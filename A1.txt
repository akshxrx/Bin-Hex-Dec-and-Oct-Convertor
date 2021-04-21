# Akshara Debnath (Binary, Oct, Decimal Convertor)
# My program converts binary, decimal, octa-decimal or hex-decimal to a desired base.
# This was done through creating different, intertwined function where,
# it performed the performed the conversions. There are comments throughout
# to further explain the code! :)

invitation = input('''Hello, welcome a python convertor! (>u<)
You can convert from decimal, binary, octa-decimal and hex-decimal! (O.o)
Type yes or yep to continue >>>>   ''')

# The convertor function allows the user to indicate the base of the value and a value.
# By using these information it converts the value to a desired base.


def convertor():
    enter_number = input('\nPlease, enter a number you would like to convert: ')
    indicator = int(input('Please, indicate the current base of number: [1]Decimal [2]Binary [3]Octa-decimal [4]Hex-decimal >     '))
    convert = int(input('What base do you want to convert to? [1]Decimal [2]Binary [3]Octa-decimal [4]Hex-decimal >     '))

    # The decimal function understands all inputted value are base 10 and converts the value
    # to a different base using built in function in python.

    def decimal():
        if indicator == 1 and convert == 1:                                 # Decimal to Decimal
            final_conversion = int(enter_number)                        # The program compares to confirm the bases.
            return final_conversion                                     # This is repeated through out, in each function
        elif indicator == 1 and convert == 2:                               # Decimal to Binary
            final_conversion = str(bin(int(enter_number)))              # These are the built in function used to
            final_conversion = final_conversion.replace("0b", "")       # convert multiple time through out the program.
            return final_conversion
        elif indicator == 1 and convert == 3:                               # Decimal to Octal
            final_conversion = oct(int(enter_number))
            final_conversion = final_conversion.replace("0o", "")
            return final_conversion
        elif indicator == 1 and convert == 4:                               # Decimal to Hex-decimal
            final_conversion = hex(int(enter_number))
            final_conversion = final_conversion.replace("0x", "")
            return final_conversion.upper()

    # Similar to the decimal function, the binary function understands all inputted value are base 2.
    # Then converts the value to a different base using built in primitive data types, loop and if-statements.

    def binary():
        if indicator == 2 and convert == 1:                              # Binary to Decimal
            final_conversion = int(0)
            n = 0
            for num in reversed(enter_number):                      # It takes all the singular digit from the inputted
                if num.isdigit:                                     # in reverse order and multiplies by the base with a
                    final_conversion += (int(num) * (2 ** n))       # power, decreasing as the digit increases (Part 1).
                    n += 1
            return final_conversion
        elif indicator == 2 and convert == 2:                           # Binary to Binary
            final_conversion = int(enter_number)                    # Reprints entered number
            return final_conversion
        elif indicator == 2 and convert == 3:                           # Binary to Octal
            final_conversion = int(0)
            n = 0
            for num in reversed(enter_number):
                if num.isdigit:
                    final_conversion += (int(num) * (2 ** n))       # It repeats the process of part 1 to convert binary
                    n += 1                                          # to integer then, uses the built in oct function
            final = str(oct(int(final_conversion)))                 # to convert integer to octa-decimal (Part 2).
            final = final.replace("0o", "")
            return final
        elif indicator == 2 and convert == 4:                           # Binary to Hex-decimal
            final_conversion = int(0)
            n = 0
            for num in reversed(enter_number):
                if num.isdigit:
                    final_conversion += (int(num) * (2 ** n))
                    n += 1

            final1 = str(hex(int(final_conversion)))
            return (final1.replace('0x', '')).upper()

    # Like others, the oct_decimal function understands all inputted value are base 8. Then converts the value
    # to a different base using built in primitive data types, loop, if-statements and built in function.

    def octa_decimal():
        if indicator == 3 and convert == 1:                             # Octal to Decimal
            final_conversion = int(0)
            n = 0
            for num in reversed(enter_number):
                if num.isdigit:                                    # It reuses the process from part 1 or part 2 but
                    final_conversion += (int(num) * (8 ** n))      # instead of multiplying by 2, it multiplies by 8
                    n += 1
            return final_conversion
        elif indicator == 3 and convert == 2:                           # Octal to Binary
            final_conversion = 0
            final = ''
            n = 0
            for num in reversed(enter_number):                          # Converts octal number to decimal
                if num.isdigit():
                    final_conversion += (int(num) * (8 ** n))
                    n += 1
            for num in reversed(enter_number):
                if num.isdigit():
                    if int(num) > 7:                                    # It checks to see if the number contain 8.
                        final = str(f'The {enter_number} is invalid!')  # If it doesn't it uses built in function to convert.
                        return final                                    # If it does, it prints a value to,
                        break                                           # show the number is invalid
                    else:
                        final = bin(final_conversion)                   # Here we convert the decimal value to binary
                        final2 = f'The conversion of {enter_number} is {final.replace("0b", "")}'
                        return final2
                        break                                           # using built in functions.

        elif indicator == 3 and convert == 3:                           # Octal to Octal
            for num in enter_number:
                if num.isdigit():
                    if int(num) > 7:                                        # It checks to see if the number contain 8.
                        final_conversion = str('The number is invalid!')    # If it does, it prints a value to
                        return final_conversion                             # show the number is invalid.
                        exit(0)
                    else:
                        final2 = f'The conversion of {enter_number} is {enter_number}'     # If it doesn't,
            return final2                                                                  # it reprints entered value.

        elif indicator == 3 and convert == 4:                           # Octal to Hex
            final_conversion = int(0)
            n = 0
            for num in reversed(enter_number):
                if num.isdigit:
                    final_conversion += (int(num) * (8 ** n))
                    n += 1
            for num in reversed(enter_number):
                if int(num) > 7:
                    final1 = str(f'The {enter_number} is invalid!')
                    return final1
                    break
                else:
                    final1 = hex(int(final_conversion))
                    return f'The conversion of {enter_number} is {(final1.replace("0x", "")).upper()}'
                    break

    # Finally, the hex_decimal function understands all inputted value are base 16.
    # Then converts the value to a different base using built in function.

    def hex_decimal():
        if indicator == 4 and convert == 1:                     # Hex to Decimal
            final_conversion = int(enter_number, 16)
            return final_conversion
        elif indicator == 4 and convert == 2:                   # Hex to Binary
            final_conversion = int(enter_number, 16)        # Uses function to convert to decimal.
            final1 = bin(final_conversion)                  # Then uses built in function
            return final1.replace('0b', '')                 # to convert to other bases.
        elif indicator == 4 and convert == 3:                   # Hex to Octal
            final_conversion = int(enter_number, 16)
            final1 = oct(final_conversion)
            return final1.replace('0o', '')
        elif indicator == 4 and convert == 4:                   # Hex to Hex
            return enter_number.upper()

# This is part of the convertor function where it finally confirms the entered base
# and preferred base. Then it prints the returned value, converted from past functions.

    if indicator == 1 and (convert == 1 or convert == 2 or convert == 3 or convert == 4):
        print(f'\nThe conversion of {enter_number} is {decimal()}')
    elif indicator == 2 and (convert == 1 or convert == 2 or convert == 3 or convert == 4):
        print(f'\nThe conversion of {enter_number} is {binary()}')
    elif indicator == 3 and convert == 1:
        print(f'\nThe conversion of {enter_number} is {octa_decimal()}')
    elif indicator == 3 and convert == 2:
        print(f'\n{octa_decimal()}')
    elif indicator == 3 and convert == 3:
        print(f'\n{octa_decimal()}')
    elif indicator == 3 and convert == 4:
        print(f'\n{octa_decimal()}')
    elif indicator == 4 and (convert == 1 or convert == 2 or convert == 3 or convert == 4):
        print(f'\nThe conversion of {enter_number} is {hex_decimal()}')
# This final part loops until the user specifies they want to stop converting.


if invitation == 'yes' or invitation == 'Yes' or invitation == 'yep' or invitation == 'Yep':
    convertor()
    again = int(input('\nWould you like to convert again? [1]Yes [2]No >    '))
    # Does the user want to convert again?
    if again == 1:
        while again == 1:                                                                   # If yes the loop continues,
            convertor()                                                                     # until it is specified
            again = int(input('\nWould you like to convert again? [1]Yes [2]No >     '))    # again to discontinue.
            if again == 2:
                print('\nGood luck with all the numbers and remember you can always "count" on us! :D')
                exit(0)
                # Good-bye statement.
    elif again == 2:
        print('\nGood luck with all the numbers and remember you can always "count" on us! :D')
        exit(0)
        # If the user does not want to convert again, it just print a good-bye statement.
else:
    exit(0)


# This is the end of my convertor! Hope you enjoyed your journey :D
