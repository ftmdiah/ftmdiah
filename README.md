
/Python program that converts a decimal number to its binary equivalent using a stack

class Stack: def init(self): self.items = []

def is_empty(self):
    return self.items == []

def push(self, item):
    self.items.append(item)

def pop(self):
    if not self.is_empty():
        return self.items.pop()
    else:
        return None
def decimal_to_binary(decimal): stack = Stack()

while decimal > 0:
    remainder = decimal % 2  # Get the remainder when divided by 2
    stack.push(remainder)  # Push the remainder onto the stack
    decimal //= 2  # Update the decimal by integer division

binary = ""
while not stack.is_empty():
    binary += str(stack.pop())  # Pop elements from the stack to form the binary number

return binary if binary != "" else "0"
Example usage:
decimal_number = 25 # Replace this with your decimal number binary_result = decimal_to_binary(decimal_number) print(f"The binary equivalent of {decimal_number} is {binary_result}")

/Python implementation of a class that handles infix to postfix conversion based on the specified rules
class InfixToPostfixConverter: def init(self): self.infix = "" self.postfix = ""

def get_infix(self, expression):
    self.infix = expression

def show_infix(self):
    return f"Infix Expression: {self.infix};"

def show_postfix(self):
    return f"Postfix Expression: {self.postfix}"

def precedence(self, operator):
    precedence = {'+': 1, '-': 1, '*': 2, '/': 2}
    return precedence.get(operator, 0)

def convert_to_postfix(self):
    stack = []
    self.postfix = ""

    for symbol in self.infix:
        if symbol.isalnum():  # Operand
            self.postfix += symbol
        elif symbol == '(':
            stack.append(symbol)
        elif symbol == ')':
            while stack and stack[-1] != '(':
                self.postfix += stack.pop()
            stack.pop()  # Discard '('
        else:  # Operator
            while stack and self.precedence(stack[-1]) >= self.precedence(symbol):
                self.postfix += stack.pop()
            stack.append(symbol)

    while stack:
        self.postfix += stack.pop()
Testing the expressions
expressions = [ "A + B - C", "(A + B) * C", "(A + B) * (C - D)", "A + ((B + C) * (E - F) - G) / (H - I)", "A + B * (C + D) - E / F * G + H" ]

for expression in expressions: converter = InfixToPostfixConverter() converter.get_infix(expression) converter.convert_to_postfix() print(converter.show_infix()) print(converter.show_postfix()) print()

# /Python function that converts a binary number to its decimal equivalent by calculating the weighted sum
def binary_to_decimal(binary): decimal = 0 power = 0

# Iterating through the binary number from right to left
for digit in reversed(binary):
    if digit == '1':
        decimal += 2 ** power  # Calculating the weighted sum
    power += 1  # Incrementing the power for the next bit

return decimal
Example usage:
binary_number = "101010" # Replace this with your binary number result = binary_to_decimal(binary_number) print(f"The decimal equivalent of {binary_number} is {result}")
