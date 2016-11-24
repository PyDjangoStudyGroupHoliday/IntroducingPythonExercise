# Introducing Python Exercise

## chapter 2
2.1 How many seconds are in an hour? Use the interactive interpreter as a calculator and multiply the number of seconds in a minute (60) by the number of minutes in an hour (also 60).  

2.2 Assign the result from the previous task (seconds in an hour) to a variable called seconds_per_hour.  

2.3 How many seconds are in a day? Use your seconds_per_hour variable.  

2.4 Calculate seconds per day again, but this time save the result in a variable called
seconds_per_day.  

2.5 Divide seconds_per_day by seconds_per_hour. Use floating-point (/) division.  

2.6 Divide seconds_per_day by seconds_per_hour, using integer (//) division. Did this number agree with the floating-point value from the previous question, aside from the final .0?  

## chapter 3
3.1. Create a list called years_list, starting with the year of your birth, and each year thereafter until the year of your fifth birthday. For example, if you were born in 1980. the list would be years_list = [1980, 1981, 1982, 1983, 1984, 1985].
If you’re less than five years old and reading this book, I don’t know what to tell you.  

3.2. In which year in years_list was your third birthday? Remember, you were 0 years of age for your first year.  

3.3. In which year in years_list were you the oldest?  

3.4. Make a list called things with these three strings as elements: "mozzarella", "cin
derella", "salmonella".  

3.5. Capitalize the element in things that refers to a person and then print the list. Did
it change the element in the list?  

3.6. Make the cheesy element of things all uppercase and then print the list.  

3.7. Delete the disease element from things, collect your Nobel Prize, and print the list.  

3.8. Create a list called surprise with the elements "Groucho", "Chico", and "Harpo".  

3.9. Lowercase the last element of the surprise list, reverse it, and then capitalize it.  

3.10. Make an English-to-French dictionary called e2f and print it. Here are your starter words: dog is chien, cat is chat, and walrus is morse.  

3.11. Using your three-word dictionary e2f, print the French word for walrus.  

3.12. Make a French-to-English dictionary called f2e from e2f. Use the items method. 3.13. Using f2e, print the English equivalent of the French word chien.  

3.14. Make and print a set of English words from the keys in e2f.  

3.15. Make a multilevel dictionary called life. Use these strings for the topmost keys: 'animals', 'plants', and 'other'. Make the 'animals' key refer to another dictionary with the keys 'cats', 'octopi', and 'emus'. Make the 'cats' key refer to a list of strings with the values 'Henri', 'Grumpy', and 'Lucy'. Make all the other keys refer to empty dictionaries.  

3.16. Print the top-level keys of life.  

3.17. Print the keys for life['animals'].  

3.18. Print the values for life['animals']['cats'].  

## chapter 4

4.1 Assign the value 7 to the variable guess_me. Then, write the conditional tests (if, else, and elif) to print the string 'too low' if guess_me is less than 7, 'too high' if greater than 7, and 'just right' if equal to 7.  

4.2 Assign the value 7 to the variable guess_me and the value 1 to the variable start. Write a while loop that compares start with guess_me. Print too low if start is less than guess me. If start equals guess_me, print 'found it!' and exit the loop. If start is greater than guess_me, print 'oops' and exit the loop. Increment start at the end of the loop.  

4.3 Use a for loop to print the values of the list [3, 2, 1, 0].  

4.4 Use a list comprehension to make a list of the even numbers in range(10).  

4.5 Use a dictionary comprehension to create the dictionary squares. Use range(10) to return the keys, and use the square of each key as its value.  

4.6 Use a set comprehension to create the set odd from the odd numbers in range(10).  

4.7 Use a generator comprehension to return the string 'Got ' and a number for the numbers in range(10). Iterate through this by using a for loop.  

4.8 Define a function called good that returns the list ['Harry', 'Ron', 'Hermione'].  

4.9 Define a generator function called get_odds that returns the odd numbers from range(10). Use a for loop to find and print the third value returned.  

4.10 Define a decorator called test that prints 'start' when a function is called and 'end' when it finishes.  

4.11 Define an exception called OopsException. Raise this exception to see what hap‐ pens. Then write the code to catch this exception and print 'Caught an oops'.  

4.12 Use zip() to make a dictionary called movies that pairs these lists: titles = ['Creature of Habit', 'Crewel Fate'] and plots = ['A nun turns into a mon ster', 'A haunted yarn shop'].  

## chapter 5

5.1. Create a file called zoo.py. In it, define a function called hours() that prints the string 'Open 9-5 daily'. Then, use the interactive interpreter to import the zoo module and call its hours() function.  

5.2. In the interactive interpreter, import the zoo module as menagerie and call its hours() function.  

5.3. Staying in the interpreter, import the hours() function from zoo directly and call it.  

5.4. Import the hours() function as info and call it.  

5.5. Make a dictionary called plain with the key-value pairs 'a': 1, 'b': 2, and 'c':
3, and then print it.  

5.6. Make an OrderedDict called fancy from the same pairs listed in 5.5 and print it.
Did it print in the same order as plain?  

5.7. Make a defaultdict called dict_of_lists and pass it the argument list. Make the list dict_of_lists['a'] and append the value 'something for a' to it in one assignment. Print dict_of_lists['a'].  

## chapter 6
6.1. Make a class called Thing with no contents and print it. Then, create an object called example from this class and also print it. Are the printed values the same or different?  

6.2. Make a new class called Thing2 and assign the value 'abc' to a class attribute called letters. Print letters.  

6.3. Make yet another class called, of course, Thing3. This time, assign the value 'xyz' to an instance (object) attribute called letters. Print letters. Do you need to make an object from the class to do this?  

6.4. Make a class called Element, with instance attributes name, symbol, and number. Create an object of this class with the values 'Hydrogen', 'H', and 1.  

6.5. Make a dictionary with these keys and values: 'name': 'Hydrogen', 'symbol': 'H', 'number': 1. Then, create an object called hydrogen from class Element using this dictionary.  

6.6. For the Element class, define a method called dump() that prints the values of the object’s attributes (name, symbol, and number). Create the hydrogen object from this new definition and use dump() to print its attributes.  

6.7. Call print(hydrogen). In the definition of Element, change the name of method dump to __str__, create a new hydrogen object, and call print(hydrogen) again.  

6.8. Modify Element to make the attributes name, symbol, and number private. Define a getter property for each to return its value.  

6.9. Define three classes: Bear, Rabbit, and Octothorpe. For each, define only one method: eats(). This should return 'berries' (Bear), 'clover' (Rabbit), or 'campers' (Octothorpe). Create one object from each and print what it eats.  

6.10. Define these classes: Laser, Claw, and SmartPhone. Each has only one method: does(). This returns 'disintegrate' (Laser), 'crush' (Claw), or 'ring' (Smart Phone). Then, define the class Robot that has one instance (object) of each of these. Define a does() method for the Robot that prints what its component objects do.  


## Markdown語法
可以參考 http://markdown.tw

### 1.換行
斷行處案兩下空白，執行enter
## Program: 
可以放 .py or jupyter 

## Member list:
1. whale176
2. ekman
3. seiching


