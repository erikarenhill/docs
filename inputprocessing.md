## Input processing

The following details what each input processor does and what the argument requirements are.

Input processes are executed sequentially with the result being passed back for further processing by the next processor in the input processing list. This makes it possible to say: take an input called current multiply it with an other input called voltage, log it to a feed called power, convert the power variable to kWh/d data and log that to a feed called kWhddata.

---

## Log to feed

**Description:** This processor logs the input straight to a feed. Every received post is logged as a new datapoint. 

**Argument:** The argument here is the feed name that you wish to write too. If the feed does not yet exist, this will create a feed of the given name.

---

## x (scale)

**Description:** Scale input by value given. This can be useful for calibrating a particular variable on the web rather than by reprogramming hardware. Result is passed back for further processing by the next processor in the input processing list.

**Argument:** The value to scale by.

---

## + (offset)

**Description:** Offset input by value given. This can again be useful for calibrating a particular variable on the web rather than by reprogramming hardware. Result is passed back for further processing by the next processor in the input processing list.

**Argument:** The value to offset by. 

---

## Power to kWh

**Description:** Convert a power value in Watts to cumulative and ever rising kWh plot. 

**Argument:** The argument here is the feed name that you wish to write too. If the feed does not yet exist, this will create a feed of the given name.

---

## Power to kWh/d

**Description:** This is a particularly useful input processor for energy monitoring, it converts a power value in Watts to a feed that contains an entry for the total energy used each day (kWh/d).

**Argument:** The argument here is the feed name that you wish to write too. If the feed does not yet exist, this will create a feed of the given name.

---

## x input

**Description:** This multiplies the current selected input with another input of given name. Result is passed back for further processing by the next processor in the input processing list.

**Argument:** Name of input to multiply with

---

## Input on-time

**Description:** counts the amount of time that an input is high in each day and logs to a feed. Created for counting the number of hours a solar hot water pump was on each day.

**Argument:** The feed name that you wish to write too. If the feed does not yet exist, this will create a feed of the given name.

---

## kWhinc to kWh/d

**Description:** Converts kWh increment since last post data into a kWh per day feed.

**Argument:** The feed name that you wish to write too. If the feed does not yet exist, this will create a feed of the given name.

---

## kWh to kWh/d

**Description:** Some datalogging equipment may just provide total kWh used or generated data, this can be used to convert this ever accumulating kWh variable to a kWh per day feed.

**Argument:** The feed name that you wish to write too. If the feed does not yet exist, this will create a feed of the given name. 

---

## update feed @ time

**Description:** Update a feed datapoint at a given time

**Argument:** The feed name that you wish to update too. Time argument is passed by API, for example &time=TIME&json={power:200}

---

## + input

**Description:** This adds the current selected input with another input of given name. Result is passed back for further processing by the next processor in the input processing list.

**Argument:** Name of input to add 

---

## / input

**Description:** This divides the current selected input with another input of given name. Result is passed back for further processing by the next processor in the input processing list.

**Argument:** Name of input to add 

---

## phaseshift

**Description:**

**Argument:**

---

## accumulator

**Description:**

**Argument:**

---

## rate of change

**Description:** Display the rate of change for the current and last entry

**Argument:**

---

## histogram

**Description:**

**Argument:**

---

## average

**Description:** Calculates a daily average (mean) of a value 

**Argument:**
