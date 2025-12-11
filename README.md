# BMI-CALCULATOR
It is a simple BMI calculator by using python programming

  import sys
import time


calculate_bmi = lambda w, h: w / (h ** 2)


def slow_print(text, delay=0.03):
    for char in text:
        print(char, end="")
        sys.stdout.flush()
        time.sleep(delay)
    print()


def get_float_input(prompt):
    while True:
        try:
            value = float(input(prompt))
            if value <= 0:
                print("Value must be positive. Try again.")
                continue
            return value
        except ValueError:
            print("Invalid input! Enter a number.")


def bmi_category(bmi):
    if bmi < 18.5:
        return "Underweight"
    elif 18.5 <= bmi < 24.9:
        return "Normal weight"
    elif 25 <= bmi < 29.9:
        return "Overweight"
    else:
        return "Obese"


def show_result(bmi):
    slow_print(f"\nYour BMI is: {bmi:.2f}")
    slow_print(f"Category: {bmi_category(bmi)}\n")


def bmi_program():
    slow_print("--------------- BMI CALCULATOR ---------------", 0.01)

    while True:
        weight = get_float_input("Enter your weight in kilograms: ")
        height = get_float_input("Enter your height in meters: ")

        
        bmi_value = calculate_bmi(weight, height)

        show_result(bmi_value)

        
        repeat = input("Do you want to calculate again? (yes/no): ").strip().lower()
        if repeat not in ("yes", "y"):
            slow_print("\nThank you for using BMI Calculator!")
            break

bmi_program()
