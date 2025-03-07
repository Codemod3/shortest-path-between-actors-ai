# DFS project to find the degrees between actors

## The main goal of this project to implement DFS. Its main goal is to find how actors are releated with each other based on their movies

### Sample output <br>
$ python degrees.py large <br>
Loading data... <br>
Data loaded. <br>
Name: Emma Watson <br>
Name: Jennifer Lawrence <br>
3 degrees of separation. <br>
1: Emma Watson and Brendan Gleeson starred in Harry Potter and the Order of the Phoenix <br>
2: Brendan Gleeson and Michael Fassbender starred in Trespass Against Us <br>
3: Michael Fassbender and Jennifer Lawrence starred in X-Men: First Class <br>

### Understanding <br>
The distribution code contains two sets of CSV data files: one set in the large directory and one set in the small directory. Each contains files with the same names, and the same structure, but small is a much smaller dataset for ease of testing and experimentation. <br>

Each dataset consists of three CSV files. A CSV file, if unfamiliar, is just a way of organizing data in a text-based format: each row corresponds to one data entry, with commas in the row separating the values for that entry. <br>

Open up small/people.csv. You’ll see that each person has a unique id, corresponding with their id in IMDb’s database. They also have a name, and a birth year. <br>

Next, open up small/movies.csv. You’ll see here that each movie also has a unique id, in addition to a title and the year in which the movie was released. <br>

Now, open up small/stars.csv. This file establishes a relationship between the people in people.csv and the movies in movies.csv. Each row is a pair of a person_id value and movie_id value. The first row (ignoring the header), for example, states that the person with id 102 starred in the movie with id 104257. Checking that against people.csv and movies.csv, you’ll find that this line is saying that Kevin Bacon starred in the movie “A Few Good Men.” <br>

Next, take a look at degrees.py. At the top, several data structures are defined to store information from the CSV files. The names dictionary is a way to look up a person by their name: it maps names to a set of corresponding ids (because it’s possible that multiple actors have the same name). The people dictionary maps each person’s id to another dictionary with values for the person’s name, birth year, and the set of all the movies they have starred in. And the movies dictionary maps each movie’s id to another dictionary with values for that movie’s title, release year, and the set of all the movie’s stars. The load_data function loads data from the CSV files into these data structures. <br>

The main function in this program first loads data into memory (the directory from which the data is loaded can be specified by a command-line argument). Then, the function prompts the user to type in two names. The person_id_for_name function retrieves the id for any person (and handles prompting the user to clarify, in the event that multiple people have the same name). The function then calls the shortest_path function to compute the shortest path between the two people, and prints out the path. <br>

The shortest_path function, it can be called as the main block of code, where the logic is connected this function returns the shortest path from the person with id source to the person with the id target. <br>
The function returns a list, where each list item is the next (movie_id, person_id) pair in the path from the source to the target. Each pair is a tuple of two strings.

* If there are multiple paths of minimum length from the source to the target, THe function returns any of them.
* If there is no possible path between two actors, The function returns None.

