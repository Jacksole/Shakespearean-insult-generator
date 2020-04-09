## What you will make

Ever been lost for words? In this resource you will write a Python script to generate insults, Elizabethan-style.

## What you will learn

By creating a Shakespearean insult generator with your Raspberry Pi you will learn:

    1. How to read and write data in CSV format using Python
    2. How to manipulate lists
    3. How to randomly choose an item from a list
    4. How to create a basic GUI (optional)


Based on the insult generator from https://projects.raspberrypi.org/en/projects/shakespearean-insult-generator

## Shakespearean insult generator

Ever been in the frustrating situation of being insulted by someone and wishing you had a bitingly funny zinger to come back with? In this resource you will rite a Python script to generate insults, Elizabethan-style.

## What is a CSV file?

A Comma Separated Values file (or CSV file as it’s commonly known) is a very basic way of storing data for use in a Python program. It’s simply a text file where the contents are in a specific format: separated by commas. For instance, this could be an example of data stored in a CSV file:

john, paul, george, ringo

Sometimes the values are encapsulated. For example, they may be encapsulated with quotes like this:

"john", "paul", "george", "ringo"

This is usually because the data itself contains commas, so we need to avoid confusion between where a comma represents a break between different data items, and where it’s simply part of the data. For example, in this CSV file encapsulation is definitely necessary:

"Tabitha, slayer of mice", "Tiddles, drinker of milk", "Tiffany, leaver of hairballs"

The most basic way of creating a CSV file is to type data into a text file in CSV format, and then save the file with the extension .csv. Alternatively, you could use a program such as LibreOffice Calc or Microsoft Excel to create and save a file in CSV format.


Putting your insults into a CSV file

You will need to find some suitable Shakespearean words to use. Make sure to only use Shakespearean words as insults - they are witty, intelligent, and unlikely to actually offend your friends! We found a big list of Shakespearean insults at https://www.theatrefolk.com/free-resources/shakespeare.

You can create your own insults CSV file by following the instruction below or download a pre-built insults.csv file.

Now open up a document in a spreadsheet editor. These instructions are for LibreOffice Calc, which is included on the latest distribution of Raspbian, but this process works in a very similar way in other spreadsheet programs such as Microsoft Excel. Copy the first column of insults from the Shakespearean insults PDF file. Now right-click on cell A1 in your spreadsheet and select Paste Special. In the pop up box which appears, make sure Unformatted text is selected before pressing OK. Then press OK again when you’re presented with the box below.

You should see your insult words displayed in the spreadsheet, with one word in each row, like this:

Repeat this for the second and third columns, pasting them into columns B and C of the spreadsheet.

Now save your file as “insults” and make sure to change the File type drop-down to Text CSV before pressing Save.

If a box pops up, choose to save the file in Text CSV format. Press OK on any further pop ups.

Once your file has been saved, you can check that the data is now in CSV format. Locate the file using the file explorer, then right-click on the file and select “Text editor” to open it up as plain text. You should see the insults you pasted in, separated by commas.

## Open and read from a file

* Open up Python 3 IDLE.

* Click File > New File and save the file as shakespeare.py.

* Add the following code to open the file (insults.csv) in read mode ("r" means read mode), read the full contents, and output the result:

    ```
```python
    with open("insults.csv", "r") as f:
        contents = f.read()
        print(contents)
			
```
				
What’s the difference between the current line of code…

```
```python3  
contents = f.read()
```
…and this line of code?
```

contents = f.readline()

```

Change the code and see if you can work out the difference betweeen read() and readline().

So far, we’re able to read the insults from the file in the order they were written, but we can’t do much with them. You may have noticed that the different columns forming the parts of the insult were different types of word. The first two columns (A and B) contain adjectives (describing words) and the final column (C) contains nouns, mostly in this case referring to a ‘thing’ the person resembles. If we could split them up, we could make insults of the form “Thou [List A] [List B] [List C]” by choosing a random word from each list. An example might be “Thou impertinent rump-fed miscreant”.


