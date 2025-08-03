# 0x03-shell_variables_expansions

## Task 0: `<o>`

**Script Name:** `0-alias`

**Description:**
This script creates a shell alias that redefines the `ls` command to execute `rm *` instead. When the script is sourced, any call to `ls` will delete all files in the current directory.

**Usage:**

```bash
source ./0-alias
ls  # This will now run `rm *` instead of listing files
```

## Task 1: Hello you

**Script Name:** `1-hello_you`

**Description:**
Prints a greeting to the current Linux user using the `$USER` environment variable.

**Example Output:**

```bash
hello julien
```

## Task 2: The path to success is to take massive, determined action

**Script Name:** `2-path`

**Description:**
Appends `/action` to the system `PATH` environment variable, so it becomes the last directory checked when looking for executables.

**Command Used:**

```bash
export PATH="$PATH:/action"
```

**Example usage**

```bash
 # before
echo $PATH
/home/julien/bin:/home/julien/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

# after
source ./2-path
echo $PATH
/home/julien/bin:/home/julien/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/action

# /action should now appear at the end

```

## Task 3: If the path be beautiful, let us not ask where it leads

**Script Name:** `3-paths`

**Description:**
Counts how many valid (non-empty) directories are in the `$PATH` variable. It handles cases where `$PATH` contains empty entries (`:::`).

**Command Used:**

```bash
echo "$PATH" | tr ':' '\n' | grep -v '^$' | wc -l
```

**Example usage**

```bash
. ./3-paths
# Output: e.g., 11
```

## Task 4: Global variables

**Script Name:** `4-global_variables`

**Description:**
Lists all global (environment) variables currently available in the shell session using `printenv`.

**Command Used:**

```bash
printenv
```

**Example usage**

```bash
source ./4-global_variables
# Output: list of environment variables
```

## Task 5: Local variables

**Script Name:** `5-local_variables`

**Description:**
Displays all local variables, environment variables, and shell functions currently defined in the session using the `set` command.

**Command Used:**

```bash
set
```

**Example usage**

```bash
source ./5-local_variables
# Output: list of local variables
```

## Task 6: Local variable

**Script Name:** `6-create_local_variable`

**Description:**
Creates a local shell variable named `BEST` and sets its value to `School`.

**Command Used:**

```bash
BEST="School"
```

**Example usage**

```bash
source ./6-create_local_variable
echo $BEST
# Output: School
```

## Task 7: Create a global variable

**Script Name:** `7-create_global_variable`

**Description:**
Creates a global environment variable named `BEST` with the value `School`. This variable is exported so it is available to child processes.

**Command Used:**

```bash
export BEST="School"
```

**Example usage**

```bash
source ./7-create_global_variable
printenv BEST
# Output: School
```

## Task 8: Every addition to true knowledge is an addition to human power

**Script Name:** `8-true_knowledge`

**Description:**
Prints the result of adding 128 to the value stored in the `TRUEKNOWLEDGE` environment variable.

**Command Used:**

```bash
echo $((128 + TRUEKNOWLEDGE))
```

**Example usage**

```bash
export TRUEKNOWLEDGE=1209
./8-true_knowledge
# Output: 1337
```

## Task 9: Divide and rule

**Script Name:** `9-divide_and_rule`

**Description:**
Divides the value of the `POWER` environment variable by the value of the `DIVIDE` environment variable and prints the result.

**Command Used:**

```bash
echo $((POWER / DIVIDE))
```

**Example usage**

```bash
export POWER=42784
export DIVIDE=32
./9-divide_and_rule
# Output: 1337
```

## Task 10: Love is anterior to life, posterior to death, initial of creation, and the exponent of breath

**Script Name:** `10-love_exponent_breath`

**Description:**
Displays the result of raising the value of the `BREATH` environment variable to the power of `LOVE`.

**Command Used:**

```bash
echo $((BREATH ** LOVE))
```

**Example usage**

```bash
export BREATH=4
export LOVE=3
./10-love_exponent_breath
# Output: 64
```

## Task 11: There are 10 types of people in the world...

**Script Name:** `11-binary_to_decimal`

**Description:**
Converts a binary number (from the `BINARY` environment variable) to its decimal form and prints it.

**Command Used:**

```bash
echo "$((2#$BINARY))"
```

**Example usage**

```bash
export BINARY=10100111001
./11-binary_to_decimal
# Output: 1337
```

## Task 12: Combination

**Script Name:** `12-combinations`

**Description:**
Prints all lowercase two-letter combinations (aa–zz), skipping `oo`. Alphabetically ordered. One per line.

**Constraints:**

- Max 64 characters in script
- Must skip `oo`

```bash
echo {a..z}{a..z} | tr ' ' '\n' | grep -v 'oo'
```

**Example usage**

```bash
./12-combinations | wc -l    # Should be 675
./12-combinations | grep oo  # Should return nothing

#Sample Output:

aa
ab
ac
...
on
op
oq
...
zz
```

## Task 13: Floats

**Script Name:** `13-print_float`

**Description:**
Prints the number stored in the environment variable `NUM`, formatted to **two decimal places**.

**Examples:**

```bash
NUM=0               → 0.00
NUM=98              → 98.00
NUM=3.14159265359   → 3.14
```

## Task 14: Decimal to Hexadecimal

**Script Name:** `100-decimal_to_hexadecimal`

**Description:**
Converts a number from base 10 (stored in `$DECIMAL`) to base 16 and prints the result in lowercase.

**Examples:**

```bash
DECIMAL=16   → 10
DECIMAL=1337 → 539
DECIMAL=15   → f
```

## Task 15: Encode and decode text using the rot13 encryption

**Script Name:** `101-rot13`

**Description:**
This script encodes and decodes input text using the ROT13 cipher.
ROT13 is a simple letter substitution cipher that replaces a letter with the letter 13 letters after it in the alphabet.

**Examples:**

given a file

```bash
"Everyone is a proponent of strong encryption."
- Dorothy E. Denning
```

```bash
./101-rot13 < quote
# output:
"Rirelbar vf n cebcbarag bs fgebat rapelcgvba."
- Qbebgul R. Qraavat

```
