#### Task10 >> Simple Calculator: Write a script that acts as a simple calculator. The script should prompt the user to enter two numbers and an operator (+, -, *, /) and then display the result of the operation.

##### Bash script that acts as a simple calculator. It prompts the user to enter two numbers and an operator (+, -, *, /) and then displays the result of the operation.

### Script:

```bash
#!/bin/bash

# Function to perform the calculation
calculate() {
    local num1="$1"
    local num2="$2"
    local operator="$3"
    local result

    case "$operator" in
        +)
            result=$(echo "$num1 + $num2" | bc)
            ;;
        -)
            result=$(echo "$num1 - $num2" | bc)
            ;;
        \*)
            result=$(echo "$num1 * $num2" | bc)
            ;;
        /)
            if [ "$num2" -eq 0 ]; then
                echo "Error: Division by zero is not allowed."
                exit 1
            fi
            result=$(echo "scale=2; $num1 / $num2" | bc)
            ;;
        *)
            echo "Error: Invalid operator. Use +, -, *, or /."
            exit 1
            ;;
    esac

    echo "Result: $result"
}

# Prompt the user for input
read -p "Enter the first number: " num1
read -p "Enter the second number: " num2
read -p "Enter an operator (+, -, *, /): " operator

# Validate input
if ! [[ "$num1" =~ ^-?[0-9]+(\.[0-9]+)?$ ]] || ! [[ "$num2" =~ ^-?[0-9]+(\.[0-9]+)?$ ]]; then
    echo "Error: Invalid number format."
    exit 1
fi

# Perform the calculation
calculate "$num1" "$num2" "$operator"
```

### Output
![Alt text](Image_Output_of_the_tasks/Output_of_Task10.jpg)

### How it works:
1. **Function `calculate`**: Performs the calculation based on the operator:
   - `+` for addition
   - `-` for subtraction
   - `*` for multiplication
   - `/` for division (with zero check to prevent division by zero)
2. **Prompt User**: Asks the user to enter two numbers and an operator.
3. **Validate Input**: Checks if the numbers are in a valid format (integer or decimal).
4. **Perform Calculation**: Calls the `calculate` function to perform the operation and display the result.

### Usage:
Save the script as `simple_calculator.sh`, make it executable with `chmod +x simple_calculator.sh`, and run it with:

```bash
./simple_calculator.sh
```

Follow the prompts to enter two numbers and an operator. The script will display the result of the calculation.
