## Data Storage and efficient access

From the blog: [Speeding up emoncms feed data requests](http://openenergymonitor.blogspot.co.uk/2012/04/speeding-up-emoncms-feed-data-requests.html)

If you log 5 second data you quickly amass a huge number of datapoints (about 6 million a year). If you then tried to visualise a years data by loading all 6 million datapoints you would be waiting a long time. The most we would want to load is the same number of datapoints as the pixel width of the visualisation, lets say around 1000 datapoints. So we need some way of picking out of our 6 million datapoints 1000 datapoints at equal interval.

When I first wrote emoncms I searched for mysql queries that could pick out table rows at given intervals and came across the following query that does this:

    SELECT * FROM (SELECT @row := @row +1 AS rownum, time,data FROM 
    ( SELECT @row :=0) r, $feedname) ranked WHERE (rownum % $resolution = 1) 
    AND (time>'$start' AND time<'$end') order by time Desc

It seem to work really well. Fast forward 5 months my feed tables are approaching 2.5 million rows  and I'm starting to notice query times getting really quite long. After a bit of searching again, I came across a suggestion to a similar problem suggesting the use of an index. So I tried adding an index and creating a php for-loop to request a single row at given intervals:

    $range = $end - $start;
    $interval = $range / 1000;
    
    for ($i=0; $i<1000; $i++)
    {
      $qtime = $start + $i * $interval;
      $result = db_query("SELECT * FROM $feedname WHERE `time` >$qtime LIMIT 1");
      if($result){
        $row = db_fetch_array($result);
        $data[] = array($row['time'] * 1000, $row['data']);     
      }
    }

The following table shows the typical times for requesting data from both the indexed and non indexed tables and the different methods. At the same time I also tested whether request times where affected by the data type that time is stored as: mysql datetime or a unix timestamp stored as an unsigned int.

[![](files/queryspeeddata.png)][0]

  
So it looks like the optimum configuration is primarily the addition of an index and use of the php data request method and then to reduce disk space use, switching to unix timestamp.

This is the current implementation of data storage in emoncms.

[0]: http://2.bp.blogspot.com/-mLgSqKaw8Ng/T4cQ9I1n-XI/AAAAAAAACZw/1zFfpAL2ZPo/s1600/queryspeeddata.png
