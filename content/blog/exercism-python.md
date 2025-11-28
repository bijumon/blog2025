---
title: Learning python through exercises
date: 2025-05-01T23:15:46+05:30
tags: [ python, learn ]
description: "using problems from exercism.com python track"
---

["Hello, World!"](http://en.wikipedia.org/wiki/%22Hello,_world!%22_program) is the traditional first program for beginning programming in a new language or environment.

The objectives are simple:

- Write a function that returns the string "Hello, World!".
- Run the test suite and make sure that it succeeds.

``` python
def hello():
    return 'Hello, World!'
```---
title: Currency Exchange
date: 2025-05-09T22:19:29+05:30
---

``` python
''' A currency exchange calculator '''

def exchange_money(budget:float, exchange_rate:float):
    """
    calculate the value of exchanged curreny

    :param budget: float - amount of money you are planning to exchange.
    :param exchange_rate: float - unit value of the foreign currency.
    :return: float - exchanged value of the foreign currency you can receive.
    """

    return budget / exchange_rate

def get_change(budget, exchanging_value):
    """

    :param budget: float - amount of money you own.
    :param exchanging_value: float - amount of your money you want to exchange now.
    :return: float - amount left of your starting currency after exchanging.
    """

    return budget - exchanging_value


def get_value_of_bills(denomination, number_of_bills):
    """

    :param denomination: int - the value of a bill.
    :param number_of_bills: int - amount of bills you received.
    :return: int - total value of bills you now have.
    """

    return denomination * number_of_bills


def get_number_of_bills(budget, denomination):
    """

    :param budget: float - the amount of money you are planning to exchange.
    :param denomination: int - the value of a single bill.
    :return: int - number of bills after exchanging all your money.
    """

    return budget // denomination


def get_leftover_of_bills(budget, denomination):
    """

    :param budget: float - the amount of money you are planning to exchange.
    :param denomination: int - the value of a single bill.
    :return: float - the leftover amount that cannot be exchanged given the current denomination.
    """

    return budget % denomination


def exchangeable_value(budget, exchange_rate, spread, denomination):
    """

    :param budget: float - the amount of your money you are planning to exchange.
    :param exchange_rate: float - the unit value of the foreign currency.
    :param spread: int - percentage that is taken as an exchange fee.
    :param denomination: int - the value of a single bill.
    :return: int - maximum value you can get.
    """

    actual_rate = exchange_rate * (1 + spread / 100)
    value_after_exchange = exchange_money(budget,actual_rate)
    return get_value_of_bills(denomination, get_number_of_bills(value_after_exchange,denomination))

```---
title: Grains
date: 2025-06-27T18:27:39+05:30
---

``` python
"""
Calculate the number of grains of wheat on a chessboard.
"""

def square(number):
    if number > 0 and number <= 64:
        return 2 ** (number - 1)
    else:
        raise ValueError("square must be between 1 and 64")


def total():
    total_grains = 0
    for grains in range(1,65):
        total_grains += square(grains)
    return total_grains
```
---
title: Armstrong Numbers
date: 2025-06-27T18:27:39+05:30
---

``` python
"""
Determine whether a number is an Armstrong number
"""

def is_armstrong_number(number):
    digits = [int(d) for d in str(number)]

    length = len(digits)
    total = 0
    for num in digits:
        total += (num ** length)
    return number == total

```
---
title: Collatz Conjecture
date: 2025-06-27T18:27:39+05:30
---

``` python
"""
Given a positive integer, return the number of steps it takes to reach 1 according to the rules of the Collatz Conjecture.
"""

def steps(number):
    step = 0
    if number > 0:
        while number > 1:
            step += 1
            if number % 2 == 0:
                number = number / 2
            else:
                number = (number * 3) + 1
    else:
        raise ValueError("Only positive integers are allowed")
    return step

```
---
title: Square Root
date: 2025-06-27T18:28:48+05:30
---

``` python
def square_root(n):
    """
    Calculates the square root of a number using the Babylonian method.

    Args:
        n: The number to find the square root of (must be non-negative).

    Returns:
        The approximate square root of n.
    """
    if n < 0:
        return "Square root is not defined for negative numbers."
    if n == 0:
        return 0

    guess = n / 2.0
    
    tolerance = 0.00001
    while abs(guess * guess - n) > tolerance:
        guess = (guess + n / guess) / 2.0
        
    return int(guess)

```
---
title: Ghost Gobble Arcade Game
date: 2025-05-12T05:19:46+05:30
---

``` python
"""Functions for implementing the rules of the classic arcade game Pac-Man."""

def eat_ghost(power_pellet_active: bool, touching_ghost: bool):
    """Verify that Pac-Man can eat a ghost if he is empowered by a power pellet.

    :param power_pellet_active: bool - does the player have an active power pellet?
    :param touching_ghost: bool - is the player touching a ghost?
    :return: bool - can the ghost be eaten?
    """
    return power_pellet_active and touching_ghost

def score(touching_power_pellet, touching_dot):
    """Verify that Pac-Man has scored when a power pellet or dot has been eaten.

    :param touching_power_pellet: bool - is the player touching a power pellet?
    :param touching_dot: bool - is the player touching a dot?
    :return: bool - has the player scored or not?
    """
    return touching_dot or touching_power_pellet

def lose(power_pellet_active, touching_ghost):
    """Trigger the game loop to end (GAME OVER) when Pac-Man touches a ghost without his power pellet.

    :param power_pellet_active: bool - does the player have an active power pellet?
    :param touching_ghost: bool - is the player touching a ghost?
    :return: bool - has the player lost the game?
    """
    return touching_ghost and not power_pellet_active

def win(has_eaten_all_dots, power_pellet_active, touching_ghost):
    """Trigger the victory event when all dots have been eaten.

    :param has_eaten_all_dots: bool - has the player "eaten" all the dots?
    :param power_pellet_active: bool - does the player have an active power pellet?
    :param touching_ghost: bool - is the player touching a ghost?
    :return: bool - has the player won the game?
    """
    return has_eaten_all_dots and not lose(power_pellet_active,touching_ghost)
```
---
title: Leap
date: 2025-05-20T11:03:16+05:30
---

``` python
def leap_year(year):
    # if year % 4 == 0 and year % 100 == 0 and year % 400 == 0:
    #     return True
    # elif year % 4 == 0 and not year % 100 == 0:
    #     return True
    # else:
    #     return False
    
    # year - 4 - 100 - 400
    # 1974   F   F     F    not
    # 1996   T   F     F    leap
    # 1960   T   F     F    leap
    # 1900   T   T     F    not
    # 2000   T   T     T    leap

    return year % 4 ==0 and (year % 100 !=0 or year % 400 == 0)

```
---
title: Triangle
date: 2025-05-20T11:03:16+05:30
---

``` python
# Let a, b, and c be sides of the triangle. Then all three of the following expressions must be true:
#
# a + b ≥ c
# b + c ≥ a
# a + c ≥ b

def valid_triangle(sides):
    a,b,c = sides
    if (a+b >= c) and (b+c >= a) and (a+c >= b):
        return True
    else:
        return False

def equilateral(sides):
    a,b,c = sides
    if sum(sides) > 0 and valid_triangle(sides) and a == b == c:
        return True
    else:
        return False

def isosceles(sides):
    a,b,c = sides
    if sum(sides) > 0 and valid_triangle(sides) and (a == b or a == c or b == c or equilateral(sides)):
        return True
    else:
        return False

def scalene(sides):
    a,b,c = sides
    if sum(sides) > 0 and valid_triangle(sides) and (a != b and a != c and b != c):
        return True
    else:
        return False


```
---
title: Meltdown Mitigation
date: 2025-05-13T10:11:00+05:30
---

``` python
"""Functions to prevent a nuclear meltdown."""


def is_criticality_balanced(temperature, neutrons_emitted):
    """Verify criticality is balanced.

    :param temperature: int or float - temperature value in kelvin.
    :param neutrons_emitted: int or float - number of neutrons emitted per second.
    :return: bool - is criticality balanced?

    A reactor is said to be critical if it satisfies the following conditions:
    - The temperature is less than 800 K.
    - The number of neutrons emitted per second is greater than 500.
    - The product of temperature and neutrons emitted per second is less than 500000.
    """

    if temperature < 800 and neutrons_emitted > 500 and temperature*neutrons_emitted < 500000:
        return True
    else:
        return False

def reactor_efficiency(voltage, current, theoretical_max_power):
    """Assess reactor efficiency zone.

    :param voltage: int or float - voltage value.
    :param current: int or float - current value.
    :param theoretical_max_power: int or float - power that corresponds to a 100% efficiency.
    :return: str - one of ('green', 'orange', 'red', or 'black').

    Efficiency can be grouped into 4 bands:

    1. green -> efficiency of 80% or more,
    2. orange -> efficiency of less than 80% but at least 60%,
    3. red -> efficiency below 60%, but still 30% or more,
    4. black ->  less than 30% efficient.

    The percentage value is calculated as
    (generated power/ theoretical max power)*100
    where generated power = voltage * current
    """

    generated_power = voltage * current
    power_efficiency = (generated_power/theoretical_max_power)*100

    if power_efficiency >= 80:
        return 'green'
    elif power_efficiency < 80 and power_efficiency >= 60:
        return 'orange'
    elif power_efficiency < 60 and power_efficiency >= 30:
        return 'red'
    else:
        return 'black'


def fail_safe(temperature, neutrons_produced_per_second, threshold):
    """Assess and return status code for the reactor.

    :param temperature: int or float - value of the temperature in kelvin.
    :param neutrons_produced_per_second: int or float - neutron flux.
    :param threshold: int or float - threshold for category.
    :return: str - one of ('LOW', 'NORMAL', 'DANGER').

    1. 'LOW' -> `temperature * neutrons per second` < 90% of `threshold`
    2. 'NORMAL' -> `temperature * neutrons per second` +/- 10% of `threshold`
    3. 'DANGER' -> `temperature * neutrons per second` is not in the above-stated ranges
    """

    assessment = temperature * neutrons_produced_per_second

    if assessment < threshold * 90/100:
        return 'LOW'
    # lies within 90% to 110% of threshold
    elif assessment >= threshold * 90/100 and assessment <= threshold * 110/100:
        return 'NORMAL'
    else:
        return 'DANGER'

```---
title: Bob
date: 2025-06-27T18:27:39+05:30
---

``` python
"""
what will Bob reply to someone when they say something to him or ask him a question?
"""

def response(hey_bob: str):
    hey_bob = hey_bob.rstrip()
    if hey_bob.endswith("?"):
        if hey_bob.isupper():
            return "Calm down, I know what I'm doing!"
        else:
            return "Sure."
    elif hey_bob.isupper():
        return "Whoa, chill out!"
    elif hey_bob.isspace() or not hey_bob:
        return "Fine. Be that way!"
    else:
        return "Whatever."

```
---
title: Raindrops
date: 2025-05-01T22:53:09+05:30
---

``` python
""" 
Raindrops is a slightly more complex version of the FizzBuzz challenge, a classic interview question. 
Convert a number into its corresponding raindrop sounds.
"""

def convert(number):
    answer = []
    raindrops = {3:"Pling", 5:"Plang", 7:"Plong"}
    
    if number % 3 == 0:
        answer += raindrops[3]
    if number % 5 == 0:
        answer += raindrops[5]
    if number % 7 == 0:
        answer += raindrops[7]
    return ''.join(answer) or str(number)
```---
title: Pig Latin
date: 2025-07-28T20:59:16+05:30
---

``` python
"""
note: `pytest -s | --capture=no` shows print() output

start with a vowel, append "ay" at the end. 
starts with consonants, move to the end one by one until a vowel is found.
words beginning with "x" or "y" followed by a consonant, no further transformation.
keep the “u” attached to “q” when moving characters around

my -> ym -> ymay
square -> quares -> aresqu -> aresquay
yellow -> ellowy -> ellowyay
rhythm -> hythmr -> ythmrh -> ythmrhay
"""

vowels = ('a','e', 'i', 'o', 'u')


def pig_latin(word):

    # stages list stores intermediate transforms of the word
    stages = [word]
    
    while not word[0] in vowels:
        if word[0] in 'xy' and not word[1] in vowels:
            break
        word = word[1:] + word[0]
        if word[-1] == 'q' and word[0] == 'u':
            word = word[1:] + 'u'
        stages.append(word)
    
    stages.append(word+"ay")
    print(" -> ".join(stages))

    return word + 'ay'

def translate(sentence):
    return ' '.join([pig_latin(word) for word in sentence.split()])

```
---
title: Matching Brackets
date: 2025-07-30T11:51:33+05:30
---

``` python
"""
Given a string containing brackets `[]`, braces `{}`, parentheses `()`, or any combination thereof, verify that any and all pairs are matched and nested correctly
"""

def is_paired(text: str) -> bool:
    pairs = { '}':'{', ']':'[', ')':'(' }
    brackets = []
    for chr in text:
        if chr in '{[(':
            brackets.append(chr)
        elif chr in '}])':
            if not brackets or brackets.pop() != pairs[chr]:
                return False
    return not brackets
```
---
title: Little Sisters Vocab
date: 2025-05-18T14:37:31+05:30
---

``` python
"""Functions for creating, transforming, and adding prefixes to strings."""


def add_prefix_un(word):
    """Take the given word and add the 'un' prefix.

    :param word: str - containing the root word.
    :return: str - of root word prepended with 'un'.
    """

    return 'un' + word


def make_word_groups(vocab_words):
    """Transform a list containing a prefix and words into a string with the prefix followed by the words with prefix prepended.

    :param vocab_words: list - of vocabulary words with prefix in first index.
    :return: str - of prefix followed by vocabulary words with
            prefix applied.

    This function takes a `vocab_words` list and returns a string
    with the prefix and the words with prefix applied, separated
     by ' :: '.

    For example: list('en', 'close', 'joy', 'lighten'),
    produces the following string: 'en :: enclose :: enjoy :: enlighten'.
    """
    
    #prefix = vocab_words[0]
    #
    # create a list with prefix as first item,
    # append prefix to each work in list and add to list
    # words_with_prefix = [prefix + word for word in vocab_words[1:]]
    #
    # '[prefix]' is a list with only one item
    # return a string by joining '[prefix]' with list words_with_prefix
    # return ' :: '.join([prefix] + words_with_prefix)

    # above turned into a one-liner
    return ' :: '.join( [vocab_words[0]] + [vocab_words[0] + word for word in vocab_words[1:]] )



def remove_suffix_ness(word):
    """Remove the suffix from the word while keeping spelling in mind.

    :param word: str - of word to remove suffix from.
    :return: str - of word with suffix removed & spelling adjusted.

    For example: "heaviness" becomes "heavy", but "sadness" becomes "sad".
    """

    # word_root = word.split('ness')[0]
    word_root = word.removesuffix('ness')

    # if word_root[-1] == 'i':
    return word_root[:-1] + 'y' if word_root.endswith('i') else word_root
        


def adjective_to_verb(sentence, index):
    """Change the adjective within the sentence to a verb.

    :param sentence: str - that uses the word in sentence.
    :param index: int - index of the word to remove and transform.
    :return: str - word that changes the extracted adjective to a verb.

    For example, ("It got dark as the sun set.", 2) becomes "darken".
    """

    return sentence.strip('.').split()[index] + 'en'

```
---
title: Pangram
date: 2025-08-02T08:55:41+05:30
---

``` python
"""
A pangram is a sentence using every letter of the alphabet at least once.
It is case insensitive, so it doesn't matter if a letter is lower-case (e.g. `k`) or upper-case (e.g. `K`).

Is a sentence a pangram ?
"""

def is_pangram(sentence: str) -> bool:
    alphabets = list("abcdefghijklmnopqrstuvwxyz")

    for char in alphabets:
        if char not in sentence.lower():
            return False
    return True
```
---
title: Isogram
date: 2025-07-30T13:02:03+05:30
---

``` python
"""
Determine if a word or phrase is an isogram.

An isogram (also known as a "non-pattern word") is a word or phrase without a repeating letter, however spaces and hyphens are allowed to appear multiple times.

Examples of isograms:

- lumberjacks
- background
- downstream
- six-year-old

The word _isograms_, however, is not an isogram, because the s repeats.
"""

def is_isogram(text: str) -> bool:
    chars = ''.join(filter(str.isalnum, text)).lower()
    return len(chars) == len(set(chars))

```
---
title: Isbn Verifier
date: 2025-08-02T16:34:54+05:30
---

``` python
"""
check an ISBN-10 number is valid by computing a checksum, as per the ISBN-10 validation formula.
"""

def is_valid(isbn: str) -> bool:
    digits = [10 if c == 'X' and i == 9 else int(c) if c.isdigit() else None 
              for i, c in enumerate(c for c in isbn if c.isalnum())]

    if len(digits) != 10 or any(d is None for d in digits):
        return False

    result = sum(d * (10 - i) for i, d in enumerate(digits))
    return result % 11 == 0

```
---
title: Rotational Cipher
date: 2025-07-31T17:24:06+05:30
---

``` python
"""
Implement of the rotational cipher, also sometimes called the Caesar cipher.
"""

def rotate(text: str, key: int) -> str:
    chars = "abcdefghijklmnopqrstuvwxyz"

    new_chars = chars[key:] + chars[:key]
    trans_table = str.maketrans(chars + chars.upper(), new_chars + new_chars.upper())
    return text.translate(trans_table)

```
---
title: Black Jack
date: 2025-05-15T05:13:57+05:30
---

``` python
"""Functions to help play and score a game of blackjack.

How to play blackjack:    https://bicyclecards.com/how-to-play/blackjack/
"Standard" playing cards: https://en.wikipedia.org/wiki/Standard_52-card_deck
"""


def value_of_card(card):
    """Determine the scoring value of a card.

    :param card: str - given card.
    :return: int - value of a given card.  See below for values.

    1.  'J', 'Q', or 'K' (otherwise known as "face cards") = 10
    2.  'A' (ace card) = 1
    3.  '2' - '10' = numerical value.
    """

    if card in [ 'J',  'Q', 'K' ]:
        return 10
    elif card == 'A':
        return 1
    elif int(card) >= 2 or int(card) <= 10:
        return int(card)


def higher_card(card_one, card_two):
    """Determine which card has a higher value in the hand.

    :param card_one, card_two: str - cards dealt in hand.  See below for values.
    :return: str or tuple - resulting Tuple contains both cards if they are of equal value.

    1.  'J', 'Q', or 'K' (otherwise known as "face cards") = 10
    2.  'A' (ace card) = 1
    3.  '2' - '10' = numerical value.
    """

    if card_one is card_two:
        return card_one, card_two
    elif value_of_card(card_one) == value_of_card(card_two):
        return card_one, card_two
    elif value_of_card(card_one) > value_of_card(card_two):
        return card_one
    else:
        return card_two

def value_of_ace(card_one, card_two):
    """Calculate the most advantageous value for the ace card.

    :param card_one, card_two: str - card dealt. See below for values.
    :return: int - either 1 or 11 value of the upcoming ace card.

    1.  'J', 'Q', or 'K' (otherwise known as "face cards") = 10
    2.  'A' (ace card) = 11 (if already in hand)
    3.  '2' - '10' = numerical value.
    """

    if card_one == 'A' or card_two == 'A':
        return 1

    points = value_of_card(card_one) + value_of_card(card_two)
    if points <= 10:
        return 11
    else:
        return 1


def is_blackjack(card_one, card_two):
    """Determine if the hand is a 'natural' or 'blackjack'.

    :param card_one, card_two: str - card dealt. See below for values.
    :return: bool - is the hand is a blackjack (two cards worth 21).

    1.  'J', 'Q', or 'K' (otherwise known as "face cards") = 10
    2.  'A' (ace card) = 11 (if already in hand)
    3.  '2' - '10' = numerical value.
    """

    hand = card_one, card_two

    # any(iterable)
    # Return True if any element of the iterable is true. If the iterable is empty, return False.
    # https://docs.python.org/3/library/functions.html#any

    return 'A' in hand and any(card in hand for card in ('10', 'J', 'Q', 'K'))

def can_split_pairs(card_one, card_two):
    """Determine if a player can split their hand into two hands.

    :param card_one, card_two: str - cards dealt.
    :return: bool - can the hand be split into two pairs? (i.e. cards are of the same value).
    """

    return value_of_card(card_one) == value_of_card(card_two)


def can_double_down(card_one, card_two):
    """Determine if a blackjack player can place a double down bet.

    :param card_one, card_two: str - first and second cards in hand.
    :return: bool - can the hand can be doubled down? (i.e. totals 9, 10 or 11 points).
    """

    points = value_of_card(card_one) + value_of_card(card_two)

    return 9 <= points <= 11
```
---
title: Perfect Numbers
date: 2025-08-11T08:54:26+05:30
---

``` python
"""
Determine if a number is perfect, abundant, or deficient
"""

import math

def classify(number: int) -> str:
    """ A perfect number equals the sum of its positive divisors.

    :param number: int a positive integer
    :return: str the classification of the input integer
    """
    if number <= 0:
        raise ValueError("Classification is only possible for positive integers.")
    elif number is 1:
        return "deficient"

    divisors = []
    for i in range(1, math.isqrt(number)+1):
        if number % i == 0:
            divisors.append(i)
            if i != 1 and i != number // i:
                divisors.append(number // i)

    sum_divisors = sum(divisors)
    if sum_divisors == number:
        return "perfect"
    elif sum_divisors > number:
        return "abundant"
    else:
        return "deficient"

```
---
title: Sublist
date: 2025-08-06T12:14:51+05:30
---

``` python
"""
This exercise stub and the test suite contain several enumerated constants.

Enumerated constants can be done with a NAME assigned to an arbitrary,
but unique value. An integer is traditionally used because it’s memory
efficient.
It is a common practice to export both constants and functions that work with
those constants (ex. the constants in the os, subprocess and re modules).

https://en.wikipedia.org/wiki/Enumerated_type
"""

# Possible sublist categories.
# Change the values as you see fit.
SUBLIST = 1
SUPERLIST = 2
EQUAL = 3
UNEQUAL = 0

def is_sublist(A: list, B: list) -> bool:
    """True if list_one is a contiguous slice in list_two"""

    lenA, lenB = len(A), len(B)
    if lenA == 0: 
        return True
    if lenA > lenB:
        return False
    return any(B[i:i+lenA] == A for i in range(lenB - lenA + 1))

def sublist(A:list, B:list):
    """
    return - relationship between lists A and B
    relation is one of 'equal', 'sublist', 'superlist', 'unequal'.
    """
    if A == B:
        return EQUAL
    elif is_sublist(A, B):
        return SUBLIST
    elif is_sublist(B, A):
        return SUPERLIST
    return UNEQUAL

```
---
title: All Your Base
date: 2025-08-19T13:40:04+05:30
---

``` python
def rebase(input_base: int, digits: list[int], output_base: int) -> list[int]:
    """
    Convert a number from one base to another.

    input_base - The base of the input number (must be >= 2)
    digits - A list of integers representing the number in the input base
             Each digit must satisfy 0 <= digit < input_base
    output_base - The base to convert the number into (must be >= 2)

    returns - A list of integers representing the number in the output base.
        The most significant digit comes first

    raises - ValueError 
            if input_base or output_base < 2
            if any digit is out of range
    """

    if input_base < 2:
        raise ValueError("input base must be >= 2")
    if output_base < 2:
        raise ValueError("output base must be >= 2")
    
    if not digits or all(d == 0 for d in digits):
        return [0]
    
    if any(d < 0 or d >= input_base for d in digits):
        raise ValueError("all digits must satisfy 0 <= d < input base")
    
    # Convert digits to integer value
    value = 0
    for d in digits:
        value = value * input_base + d
    
    # Convert integer value to output_base
    result = []
    while value:
        value, rem = divmod(value, output_base)
        result.append(rem)
    
    return result[::-1]
```---
title: Little Sisters Essay
date: 2025-05-19T11:11:44+05:30
---

``` python
"""Functions to help edit essay homework using string manipulation."""


def capitalize_title(title):
    """Convert the first letter of each word in the title to uppercase if needed.

    :param title: str - title string that needs title casing.
    :return: str - title string in title case (first letters capitalized).
    """

    return title.title()


def check_sentence_ending(sentence):
    """Check the ending of the sentence to verify that a period is present.

    :param sentence: str - a sentence to check.
    :return: bool - return True if punctuated correctly with period, False otherwise.
    """

    return sentence.endswith('.')


def clean_up_spacing(sentence):
    """Verify that there isn't any whitespace at the start and end of the sentence.

    :param sentence: str - a sentence to clean of leading and trailing space characters.
    :return: str - a sentence that has been cleaned of leading and trailing space characters.
    """

    return sentence.strip()


def replace_word_choice(sentence, old_word, new_word):
    """Replace a word in the provided sentence with a new one.

    :param sentence: str - a sentence to replace words in.
    :param old_word: str - word to replace.
    :param new_word: str - replacement word.
    :return: str - input sentence with new words in place of old words.
    """

    return sentence.replace(old_word, new_word)


```
---
title: Rna Transcription
date: 2025-08-19T17:49:18+05:30
---

``` python
"""
Determine the RNA complement of a given DNA sequence.
"""

def to_rna(dna_strand: str) -> str:
    result = []
    for strand in dna_strand:
        match strand:
            case "G":
                result.append("C")
            case "C":
                result.append("G")
            case "T":
                result.append("A")
            case "A":
                result.append("U")
    return "".join(result)
```---
title: Atbash Cipher
date: 2025-08-22T10:03:51+05:30
---

``` python
"""
Implements Atbash cipher
"""

alphabets = "abcdefghijklmnopqrstuvwxyz"
cipher_map = str.maketrans(alphabets, alphabets[::-1])

def encode(plain_text: str) -> str:
    # Normalize and filter allowed characters
    filtered = "".join(ch.lower() for ch in plain_text if ch.isalpha() or ch.isdigit())
    
    # Translate alphabets using Atbash cipher
    translated = filtered.translate(cipher_map)
    
    # Insert spaces every 5 characters
    return " ".join(translated[i:i+5] for i in range(0, len(translated), 5))

def decode(ciphered_text):
    # Remove spaces, normalize case
    filtered = "".join(ch.lower() for ch in ciphered_text if ch.isalpha() or ch.isdigit())
    
    # Apply the Atbash mapping
    return filtered.translate(cipher_map)
```---
title: Wordy
date: 2025-08-22T10:04:16+05:30
---

``` python
"""
Parse and evaluate simple math word problems returning the answer as an integer.
"""

def answer(question: str) -> int:
    replacements = {
        "What is": "",
        "plus": "+",
        "minus": "-",
        "multiplied by": "*",
        "divided by": "/",
        "?": ""
    }

    for word, symbol in replacements.items():
        question = question.replace(word, symbol)

    tokens = question.split()
    tokens.insert(0, "(")
    tokens.insert(4, ")")

    if len(tokens) < 3:
        raise ValueError("syntax error")
    
    if any(token.isalpha() and token not in list(replacements.keys()) for token in tokens):
        raise ValueError("unknown operation")

    try:
        return eval(" ".join(tokens))
    except:
        raise ValueError("syntax error")

```---
title: Card Games
date: 2025-05-19T14:03:21+05:30
---

``` python
import math

"""Functions for tracking poker hands and assorted card tasks.

Python list documentation: https://docs.python.org/3/tutorial/datastructures.html
"""


def get_rounds(number):
    """Create a list containing the current and next two round numbers.
 
    :return: list - current round and the two that follow.
    """

    return [ number, number +1, number + 2]


def concatenate_rounds(rounds_1, rounds_2):
    """Concatenate two lists of round numbers.

    :param rounds_1: list - first rounds played.
    :param rounds_2: list - second set of rounds played.
    :return: list - all rounds played.
    """

    return rounds_1 + rounds_2


def list_contains_round(rounds, number):
    """Check if the list of rounds contains the specified number.

    :param rounds: list - rounds played.
    :param number: int - round number.
    :return: bool - was the round played?
    """

    return number in rounds


def card_average(hand):
    """Calculate and returns the average card value from the list.

    :param hand: list - cards in hand.
    :return: float - average value of the cards in the hand.
    """

    return float(sum(hand)/len(hand))


def approx_average_is_average(hand):
    """Return if the (average of first and last card values) OR ('middle' card) == calculated average.

    :param hand: list - cards in hand.
    :return: bool - does one of the approximate averages equal the `true average`?
    """

    estimate = float((hand[0] + hand[-1])/2)
    average = float(sum(hand)/len(hand))
    middle = hand[math.floor(len(hand)/2)]
    if estimate == average or middle == average:
        return True
    else:
        return False


def average_even_is_average_odd(hand):
    """Return if the (average of even indexed card values) == (average of odd indexed card values).

    :param hand: list - cards in hand.
    :return: bool - are even and odd averages equal?
    """

    evens = hand[::2]
    odds = hand[1::2]

    return sum(evens)/len(evens) == sum(odds)/len(odds)

def maybe_double_last(hand):
    """Multiply a Jack card value in the last index position by 2.

    :param hand: list - cards in hand.
    :return: list - hand with Jacks (if present) value doubled.
    """

    if hand[-1] == 11:
        hand[-1] = 22
    return hand

```
---
title: Chaitanas Colossal Coaster
date: 2025-05-22T11:07:39+05:30
---

``` python
"""Functions to manage and organize queues at Chaitana's roller coaster."""


def add_me_to_the_queue(express_queue, normal_queue, ticket_type, person_name):
    """Add a person to the 'express' or 'normal' queue depending on the ticket number.

    :param express_queue: list - names in the Fast-track queue.
    :param normal_queue: list - names in the normal queue.
    :param ticket_type: int - type of ticket. 1 = express, 0 = normal.
    :param person_name: str - name of person to add to a queue.
    :return: list - the (updated) queue the name was added to.
    """

    queue = express_queue if ticket_type == 1 else normal_queue
    queue.append(person_name)
    return queue
    


def find_my_friend(queue, friend_name):
    """Search the queue for a name and return their queue position (index).

    :param queue: list - names in the queue.
    :param friend_name: str - name of friend to find.
    :return: int - index at which the friends name was found.
    """

    return queue.index(friend_name)


def add_me_with_my_friends(queue, index, person_name):
    """Insert the late arrival's name at a specific index of the queue.

    :param queue: list - names in the queue.
    :param index: int - the index at which to add the new name.
    :param person_name: str - the name to add.
    :return: list - queue updated with new name.
    """

    queue.insert(index,person_name)
    return queue


def remove_the_mean_person(queue, person_name):
    """Remove the mean person from the queue by the provided name.

    :param queue: list - names in the queue.
    :param person_name: str - name of mean person.
    :return: list - queue update with the mean persons name removed.
    """

    queue.remove(person_name)
    return queue


def how_many_namefellows(queue, person_name):
    """Count how many times the provided name appears in the queue.

    :param queue: list - names in the queue.
    :param person_name: str - name you wish to count or track.
    :return: int - the number of times the name appears in the queue.
    """

    return queue.count(person_name)


def remove_the_last_person(queue):
    """Remove the person in the last index from the queue and return their name.

    :param queue: list - names in the queue.
    :return: str - name that has been removed from the end of the queue.
    """

    return queue.pop()


def sorted_names(queue):
    """Sort the names in the queue in alphabetical order and return the result.

    :param queue: list - names in the queue.
    :return: list - copy of the queue in alphabetical order.
    """

    return sorted(queue)


```
---
title: Making The Grade
date: 2025-05-30T12:56:14+05:30
---

``` python
"""Functions for organizing and calculating student exam scores."""


def round_scores(student_scores):
    """Round all provided student scores.

    :param student_scores: list - float or int of student exam scores.
    :return: list - student scores *rounded* to nearest integer value.
    """

    student_scores_rounded = []
    for score in student_scores:
        student_scores_rounded.append(round(score))

    return student_scores_rounded


def count_failed_students(student_scores):
    """Count the number of failing students out of the group provided.

    :param student_scores: list - containing int student scores.
    :return: int - count of student scores at or below 40.
    """

    failed_students: int = 0
    for score in student_scores:
        if score <= 40:
            failed_students += 1
    return failed_students

def above_threshold(student_scores, threshold):
    """Determine how many of the provided student scores were 'the best' based on the provided threshold.

    :param student_scores: list - of integer scores.
    :param threshold: int - threshold to cross to be the "best" score.
    :return: list - of integer scores that are at or above the "best" threshold.
    """

    scores_above_threshold = []
    for score in student_scores:
        if score >= threshold:
            scores_above_threshold.append(score)
    return scores_above_threshold


def letter_grades(highest):
    """Create a list of grade thresholds based on the provided highest grade.

    :param highest: int - value of highest exam score.
    :return: list - of lower threshold scores for each D-A letter grade interval.
            For example, where the highest score is 100, and failing is <= 40,
            The result would be [41, 56, 71, 86]:

            41 <= "D" <= 55
            56 <= "C" <= 70
            71 <= "B" <= 85
            86 <= "A" <= 100
    """

    low_score = 41
    no_grades = 4 # A B C D
    threshold_increment = round((highest - low_score)/no_grades)
    lower_threshold = []
    for index in range(no_grades):
        lower_threshold.append(low_score + (threshold_increment*index))
    return lower_threshold


def student_ranking(student_scores, student_names):
    """Organize the student's rank, name, and grade information in descending order.

    :param student_scores: list - of scores in descending order.
    :param student_names: list - of string names by exam score in descending order.
    :return: list - of strings in format ["<rank>. <student name>: <score>"].
    """

    rank_list = []
    for index, (name, score) in enumerate(zip(student_names, student_scores)):
        rank_list.append(f"{index+1}. {name}: {score}")
    return rank_list

def perfect_score(student_info):
    """Create a list that contains the name and grade of the first student to make a perfect score on the exam.

    :param student_info: list - of [<student name>, <score>] lists.
    :return: list - first `[<student name>, 100]` or `[]` if no student score of 100 is found.
    """

    for info in student_info:
        if info[1] == 100:
            return info
    return []

```
---
title: Tisbury Treasure Hunt
date: 2025-05-31T20:25:25+05:30
---

``` python
"""Functions to help Azara and Rui locate pirate treasure."""


def get_coordinate(record):
    """Return coordinate value from a tuple containing the treasure name, and treasure coordinate.

    :param record: tuple - with a (treasure, coordinate) pair.
    :return: str - the extracted map coordinate.
    """

    coordinate = record[1]
    return coordinate


def convert_coordinate(coordinate):
    """Split the given coordinate into tuple containing its individual components.

    :param coordinate: str - a string map coordinate
    :return: tuple - the string coordinate split into its individual components.
    """

    return tuple((coordinate))


def compare_records(azara_record, rui_record):
    """Compare two record types and determine if their coordinates match.

    :param azara_record: tuple - a (treasure, coordinate) pair.
    :param rui_record: tuple - a (location, tuple(coordinate_1, coordinate_2), quadrant) trio.
    :return: bool - do the coordinates match?
    """
    return tuple(azara_record[1]) == rui_record[1]

def create_record(azara_record, rui_record):
    """Combine the two record types (if possible) and create a combined record group.

    :param azara_record: tuple - a (treasure, coordinate) pair.
    :param rui_record: tuple - a (location, coordinate, quadrant) trio.
    :return: tuple or str - the combined record (if compatible), or the string "not a match" (if incompatible).
    """
    return azara_record + rui_record if compare_records(azara_record, rui_record) else "not a match"


def clean_up(combined_record_group):
    """Clean up a combined record group into a multi-line string of single records.

    :param combined_record_group: tuple - everything from both participants.
    :return: str - everything "cleaned", excess coordinates and information are removed.

    The return statement should be a multi-lined string with items separated by newlines.

    (see HINTS.md for an example).
    """

    report = ""
    for item in combined_record_group:
        if tuple(item[1]) == item[3]:
            report += f"""('{item[0]}', '{item[2]}', {item[3]}, '{item[4]}')\n"""
    return report
```
---
title: Inventory Management
date: 2025-06-24T17:51:07+05:30
---

``` python
"""Functions to keep track and alter inventory."""
from collections import Counter

def create_inventory(items):
    """Create a dict that tracks the amount (count) of each element on the `items` list.

    :param items: list - list of items to create an inventory from.
    :return: dict - the inventory dictionary.
    """

    return dict(Counter(items))


def add_items(inventory, items):
    """Add or increment items in inventory using elements from the items `list`.

    :param inventory: dict - dictionary of existing inventory.
    :param items: list - list of items to update the inventory with.
    :return: dict - the inventory updated with the new items.
    """

    for item in items:
        if item in inventory:
            inventory[item] += 1
        else:
            inventory[item] = 1
    return inventory



def decrement_items(inventory, items):
    """Decrement items in inventory using elements from the `items` list.

    :param inventory: dict - inventory dictionary.
    :param items: list - list of items to decrement from the inventory.
    :return: dict - updated inventory with items decremented.
    """

    for item in items:
        if item in inventory:
            if inventory[item] <= 1:
                inventory[item] = 0
            else:
                inventory[item] -= 1
    return inventory


def remove_item(inventory, item):
    """Remove item from inventory if it matches `item` string.

    :param inventory: dict - inventory dictionary.
    :param item: str - item to remove from the inventory.
    :return: dict - updated inventory with item removed. Current inventory if item does not match.
    """
    if item in inventory:
        inventory.pop(item)
    return inventory


def list_inventory(inventory):
    """Create a list containing only available (item_name, item_count > 0) pairs in inventory.

    :param inventory: dict - an inventory dictionary.
    :return: list of tuples - list of key, value pairs from the inventory dictionary.
    """

    item_list = []
    for key, value in inventory.items():
        if value > 0:
            item_list.append((key,value))
    return item_list


```
---
title: Cater Waiter
date: 2025-06-24T17:58:59+05:30
---

``` python
"""Functions for compiling dishes and ingredients for a catering company."""


from sets_categories_data import (VEGAN,
                                  VEGETARIAN,
                                  KETO,
                                  PALEO,
                                  OMNIVORE,
                                  ALCOHOLS,
                                  SPECIAL_INGREDIENTS)


def clean_ingredients(dish_name, dish_ingredients):
    """Remove duplicates from `dish_ingredients`.

    :param dish_name: str - containing the dish name.
    :param dish_ingredients: list - dish ingredients.
    :return: tuple - containing (dish_name, ingredient set).

    This function should return a `tuple` with the name of the dish as the first item,
    followed by the de-duped `set` of ingredients as the second item.
    """

    return (dish_name, set(dish_ingredients))


def check_drinks(drink_name, drink_ingredients):
    """Append "Cocktail" (alcohol)  or "Mocktail" (no alcohol) to `drink_name`, based on `drink_ingredients`.

    :param drink_name: str - name of the drink.
    :param drink_ingredients: list - ingredients in the drink.
    :return: str - drink_name appended with "Mocktail" or "Cocktail".

    The function should return the name of the drink followed by "Mocktail" (non-alcoholic) and drink
    name followed by "Cocktail" (includes alcohol).

    """
    
    return f"{drink_name} Mocktail" if set(drink_ingredients).isdisjoint(ALCOHOLS) else f"{drink_name} Cocktail"


def categorize_dish(dish_name, dish_ingredients):
    """Categorize `dish_name` based on `dish_ingredients`.

    :param dish_name: str - dish to be categorized.
    :param dish_ingredients: set - ingredients for the dish.
    :return: str - the dish name appended with ": <CATEGORY>".

    This function should return a string with the `dish name: <CATEGORY>` (which meal category the dish belongs to).
    `<CATEGORY>` can be any one of  (VEGAN, VEGETARIAN, PALEO, KETO, or OMNIVORE).
    All dishes will "fit" into one of the categories imported from `sets_categories_data.py`

    """

    categories= [(VEGAN, "VEGAN"),
        (VEGETARIAN,"VEGETARIAN"),
        (PALEO,"PALEO"),
        (KETO,"KETO"),
        (OMNIVORE,"OMNIVORE")]
    for category, name in categories:
        if dish_ingredients <= category:
            return f"{dish_name}: {name}"
    return f"{dish_name}: UNCLASSIFIED"

def tag_special_ingredients(dish):
    """Compare `dish` ingredients to `SPECIAL_INGREDIENTS`.

    :param dish: tuple - of (dish name, list of dish ingredients).
    :return: tuple - containing (dish name, dish special ingredients).

    Return the dish name followed by the `set` of ingredients that require a special note on the dish description.
    For the purposes of this exercise, all allergens or special ingredients that need to be tracked are in the
    SPECIAL_INGREDIENTS constant imported from `sets_categories_data.py`.
    """

    return (dish[0], set(dish[1]).intersection(SPECIAL_INGREDIENTS))


def compile_ingredients(dishes):
    """Create a master list of ingredients.

    :param dishes: list - of dish ingredient sets.
    :return: set - of ingredients compiled from `dishes`.

    This function should return a `set` of all ingredients from all listed dishes.
    """

    masterlist = set()
    for ingrediants in dishes:
        masterlist = masterlist.union(ingrediants)
    return masterlist

def separate_appetizers(dishes, appetizers):
    """Determine which `dishes` are designated `appetizers` and remove them.

    :param dishes: list - of dish names.
    :param appetizers: list - of appetizer names.
    :return: list - of dish names that do not appear on appetizer list.

    The function should return the list of dish names with appetizer names removed.
    Either list could contain duplicates and may require de-duping.
    """

    return list(set(dishes).difference(set(appetizers)))


def singleton_ingredients(dishes, intersection):
    """Determine which `dishes` have a singleton ingredient (an ingredient that only appears once across dishes).

    :param dishes: list - of ingredient sets.
    :param intersection: constant - can be one of `<CATEGORY>_INTERSECTIONS` constants imported from `sets_categories_data.py`.
    :return: set - containing singleton ingredients.

    Each dish is represented by a `set` of its ingredients.

    Each `<CATEGORY>_INTERSECTIONS` is an `intersection` of all dishes in the category. `<CATEGORY>` can be any one of:
        (VEGAN, VEGETARIAN, PALEO, KETO, or OMNIVORE).

    The function should return a `set` of ingredients that only appear in a single dish.
    """

    singleton = set()
    for ingrediants in dishes:
        singleton = singleton.symmetric_difference(set(ingrediants))
    return singleton - intersection

```
---
title: Ellens Alien Game
date: 2025-06-25T21:51:08+05:30
---

``` python
"""Solution to Ellen's Alien Game exercise."""


class Alien:
    """Create an Alien object with location x_coordinate and y_coordinate.

    Attributes
    ----------
    (class)total_aliens_created: int
    x_coordinate: int - Position on the x-axis.
    y_coordinate: int - Position on the y-axis.
    health: int - Number of health points.

    Methods
    -------
    hit(): Decrement Alien health by one point.
    is_alive(): Return a boolean for if Alien is alive (if health is > 0).
    teleport(new_x_coordinate, new_y_coordinate): Move Alien object to new coordinates.
    collision_detection(other): Implementation TBD.
    """

    total_aliens_created = 0

    def __init__(self, x_coordinate, y_coordinate):
        self.x_coordinate = x_coordinate
        self.y_coordinate = y_coordinate
        self.health = 3
        Alien.total_aliens_created += 1

    def hit(self):
        self.health -= 1
        if self.health == 0:
            self.health = 0

    def is_alive(self):
        return self.health > 0

    def teleport(self, new_x, new_y):
        self.x_coordinate = new_x
        self.y_coordinate = new_y

    def collision_detection(self, other):
        pass


#TODO:  create the new_aliens_collection() function below to call your Alien class with a list of coordinates.

def new_aliens_collection(alien_start_positions: list):
    aliens = []
    for alien in alien_start_positions:
        new_alien = Alien(alien[0], alien[1])
        aliens.append(new_alien)
    return aliens

```
---
title: Matrix
date: 2025-05-04T17:26:53+05:30
---

``` python
"""
from a matrix of numbers, return the rows and columns of that matrix
"""

class Matrix:
    def __init__(self, matrix_string):
        rowStrings = [r.split() for r in matrix_string.splitlines()]
        self.matrix = [[int(num) for num in row] for row in rowStrings]

    def row(self, index):
        return self.matrix[index - 1]

    def column(self, index):
        return [ column[index - 1] for column in self.matrix]
```
