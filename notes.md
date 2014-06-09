# Converting CSV File To Readable and Searchable List For Python:

First step: Find the URL and retrieve and save it to your computer.

# Import the csv and urllib libraries, retrieve the data file and save as a .csv file 
import csv
import urllib

urllib.urlretrieve("http://jonathansoma.com/lede/dogs.csv", "dogs.csv")

# Open the file in "rb" mode
dog_file = open("dogs.csv","rb")

# Create an iterator to unpack the file into delimited rows
dogcsv = csv.reader(dog_file, delimiter=',')

# Convert the iterator into a list of lists
all_dogs = list(dogcsv)


Second step save it as dogs.csv

Third step: write a code to open the dogs csv and transform it into a readable, sortable list for Python:

import urllib
import csv

urllib.urlretrieve("http://jonathansoma.com/lede/dogs.csv", "dogs.csv")

dogs = open("dogs.csv", "rb")
dogcsv = csv.reader(dogs, delimiter=',')

nycdogs_list = list(dogcsv)
rows = list(dogcsv)

Because I need to search it I save it as a list:

dogs = open("dogs.csv", "rb")
dogcsv = csv.reader(dogs, delimiter=',')

# Because I need to work with dogscsv as a list, I save it as a variable called rows. 
rows = list(dogcsv)

#How many dogs in NYC?

code to figure that out is:

rows = list(dogcsv)

len(rows) - 1 ( minus 1 because I dont need the header column in the list)
#OR

import csv
with open('dogs.csv', 'rb') as csvfile:
    dogscsv = csv.reader(csvfile, delimiter=',')
    dogs_data = list(dogscsv)
    print len(dogs_data) - 1 
    
    #OR
    
    import csv
with open('dogs.csv', 'rb') as csvfile:
    # Importing the URL and opening it as a CSV
    nyc_dogs = 0
    dogcsv = csv.reader(csvfile, delimiter=' ')
    for row in dogcsv:
        nyc_dogs = nyc_dogs + 1
    # Running a for loop to count the rows
    print nyc_dogs - 1
    
    #BEST ANSWER:
    
    len(rows[1:])
    
    #Second Question: How Many Dogs In Brooklyn:
    
    count = 0 
for row in nycdogs_list:
    if row[9] == "Brooklyn":
        count = count + 1 
print count

Brooklyn = 0 

#Next I write a simple for loop. I need a loop because I need to go thru every row in my file and check to see if the borough (column 9) is equal to Brooklyn.

# Start by going thru every row in the file, rows.
for row in rows:
    if row[9] == "Brooklyn":
        Brooklyn = Brooklyn + 1

print "The number of registered dogs in Brooklyn is:" 
print Brooklyn

#OR

brooklyn = 0 
staten_island = 0
manhattan = 0
queens = 0
bronx = 0

#Next I write a simple for loop. I need a loop because I need to go thru every row in my file and check to see if the borough (column 9) is equal to Brooklyn.

# Start by going thru every row in the file, rows.
for row in rows:
    if row[9] == "Brooklyn":
        brooklyn = brooklyn + 1
    if row[9] == "Queens":
        queens = queens + 1
    if row[9] == "Staten Island":
        staten_island = staten_island + 1
    if row[9] == "Bronx":
        bronx = bronx + 1
    if row[9] == "Manhattan":
        manhattan = manhattan + 1

print "Dogs in Brooklyn: " + str(brooklyn) 
print "Dogs in Queens: " + str(queens) 
print "Dogs in Staten Island: " + str(staten_island) 
print "Dogs in Bronx: " + str(bronx) 
print "Dogs in Manhattan: " + str(manhattan) 
# the reason you add a string is because python will not combine integers and strings, unless you identify waht it is


#question 3 how many dogs named max in brooklyn?

# Here, we count the number of dogs named Max in the three zip codes of the Lower East Side

# I used the following page to clarify the procedure: 
# http://stackoverflow.com/questions/6809190/python-multiple-if-statements-in-a-single-if-statement

import csv
with open('dogs.csv', 'rb') as csvfile:
   
    dogcsv = csv.reader(csvfile, delimiter=',')
    
    rows = list(dogcsv)
    
    row = rows[0]
    
    count = 0
    
    for row in rows:
        if row[0] == "Max" and row[10] == "10003":
            count = count + 1
        if row[0] == "Max" and row[10] == "10002":
            count = count + 1
        if row[0] == "Max" and row[10] == "10009":
            count = count + 1
    print count 
    
    #Better Answer:
    
    count = 0 
for row in nycdogs_list:
    if row[0] == 'Max':
        if row[10] == "10002" or row[10] == "10003" or row[10] == "10009":
            count = count + 1 
print count

Another WAY:

dogs = open("dogs.csv", "rb")
dogcsv = csv.reader(dogs, delimiter=',')

# Because I need to work with dogscsv as a list, I save it as a variable called rows. 
rows = list(dogcsv)

# Because the Lower East Side has a few different zip codes attached to it, I make a list that includes them as strings in a new variable.
# I make them strings because everything in my file is currently a string.

les = ["10002", "10003", "10009"]

# Now, I do the same thing as before, but I need an additional loop in order to check each item in my les list.

Max_LES = 0 

for row in rows:
    #print row[10] 
    
    # Here I loop thru every item in my list les. I guess because it's indented in the original for loop, Python knows I'm going to refer back to that bigger for loop that goes thru every row of my file.
    for les_zip in les:
        #print les_zip
        
        #Here, I say, if the 10th column in my file is equal to an item in my list, and the first row in my file is equal to the name Max, then:
        if row[10] == les_zip and row[0] == "Max":
            #print row[10]
            
            # Add a one to my initial variable.
            
            Max_LES = Max_LES + 1
            
print "The number of dogs named Max in the Lower East Side is:"
print Max_LES

```
code

``` count = 0
for dog in rows[1:]:
    if (dog[0]=="Max" and dog[10]=="10002"):
        count = count + 1 
    if (dog[0]=="Max" and dog[10]=="10003"):
        count = count + 1 
    if (dog[0]=="Max" and dog[10]=="10009"):
        count = count + 1 
    print count 
    
    #If you indent print count it will print every single row; you dont want that, you just want one row
    
    
    # Question Four: Brindle in two separate columns? How to figure out:
    
    count = 0
for dog in rows:
    if dog[4] == "BRINDLE": # I don't know why but the code only works if this is capitalized
        count = count + 1 #if the above is true, add a dog
    elif dog[5] == "BRINDLE":
        count = count + 1
print count

#another cleaner way:

```
code
```
count = 0
for dog in rows:
    # Why not dog[4:5]?
    if "BRINDLE" in dog[4:6]:
        count = count + 1
print count

#how many dogs have my name?

name = raw_input("Maureen")
count = 0 
for row in nycdogs_list:
    if row[0] == "Maureen":
        count = count + 1
print count

#or another way

```
name = raw_input('Enter your name: ') 

Dogs_with_your_name = [row for row in nycdogs_list if row[0]==name]
print len(Dogs_with_your_name)

