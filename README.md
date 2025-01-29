# data-sourcing-challenge1 SOURCING DATA FOR AI PROJECTS 
API , if you look at insta or anything the data that powers the app ,all the data is coming from the same sources.(API)
Web scraping ,go into websites and pull information from that page and get the data. Take massive amounts of data from internet with panda is from_html(). How I can get it directly without copy and past and put into python and convert them . Json .
So I have a link and I can save it with the help of panda in python and put it on.
Import pandas as pd
Tables = pd.read_html(url)
Tables 
len(tables)
tables[1]
Df = tables[1] , we need to clean it a little so we rename 
Df.rename(columns={“City population[2]” : “city population”,and others I wanna change}) the 2 in city population doesn’t make sense .
Del df[“image”] ,also df.dropna(“image”,how=any)
Df.reset_index(drop=true)
I wanna see all the cities that are in new south wales :
df[‘state/territory’] == ‘New South Wales’ .
How to save what you modified 
stats_df.to_csv("fifa_stats.csv", index=False)
First of all we create a list of the columns we are going to 
Remove stuff of and then we create a loop : this to remove 
For col in cols: 
df[col] = df[col].str.replace(“+”,””)
Etc same 
If we want to see if displays well stat_df.info()
To get the view of only just columns I’m interested in is df[[“names of columns I wanna see “, other name ..]].
JSON stands for java script notation , whenever you download json and put it in python it turns into dictionary .
Either we use Netflix from the phone or tv or etc everything is coming from API functions packages together .
What is important is how we make our request ? Base on the request we get a response .
http code  ,you find codes , if you go in a website that not functional it comes out 404 , if I do re.content is gone get me all the content iside that site ,normally is a list in json  
Res.json() is gone show me the info as a json so in lists.
Pyobj[1][2] is index2 
usa_2021= Pyobj[1][2]
usa_2021[‘country’][‘value’] so here I have the name of the two keys country and value . 
print(‘country’,usa_2021[‘country’][‘value’].
res=request.get(star_wars_url).json()
Res [‘results’]
Url parameters so when the code http://…com/ random?.. I know that from random etc that the thing that giving me the data back the output. The question mark is important is where the query string begin .


NOTES SELF MADE FROM YOUTUBE / vscode/ chat gpt
So we have url = “http//….”
x_df =pd.read_csv(url) put url in the pharentesis
x_df.info() it’s gone tell us that we have 180 rows of data and 8 columns then we do :
 x_df.head() to see better the data frame
If we have a weekepedia info and we want to pull it into python :
From bs4 import BeautifulSoup 
Import request
Then we have : url = ‘http…’
Page = request.get(url)
Soup = BeautifulSoup(page.text, ‘html’)
Now we specify what data we want 
To find the table we do soup.find(‘table’) 
If we don’t have the right table we need to find it so 
Soup.find_all(’table’) and we’ll have multiple tables 
Soup.find_all(’table’)[1] we have to put those numbers to see which tables we can reach then when we find the on  we want 
Tables = Soup.find_all(’table’)[1] .

What are the codes :
import pandas as pd

url = 'https://en.wikipedia.org/wiki/List_of_Australian_capital_cities'

tables = pd.read_html(url)
tables

To see what we have which is a list : type(tables)
List(is gone be the answer)

Slice off any of those data frames that we want using normal indexing : 
df = tables[1]
df
[1] says which table from the url we get , if we change number we’re gone get another table (if there is another one)

Fix column name : 
cols = list(df.columns)
cols[2] = "City population"
cols[3] = "State/territory population"
df.columns = cols
df.head()

Means cols (columns ) are = to the list containing the names in the data frame , we will call all the names in the column “ cols “. Then we specify that the cols in position 2 (we start count from 0) which is called City population[2] ,is gone be equal to “City population” which is the new name . Same for cols [3].
Then we same it and say df.columns = cols ,df.head(). So take columns form the list ,give them new names through new variable .then check 
Drop a column 
df = df.drop(['Image'], axis=1)
df.head()
Say what column you want to drop and axis =1 is because is a column .Explanation:
axis=0: Refers to operations along the rows (vertical direction).
axis=1: Refers to operations along the columns (horizontal direction).


Reset an index

In pandas, resetting the index means to revert the index of a DataFrame to its default integer-based index (i.e., 0, 1, 2, 3, …). This is typically used when you've performed operations like filtering, sorting, or grouping that might have resulted in a custom index, and you want to return to a simple sequential index.
df = df.reset_index(drop=True)
df.head()
 
If you don't want to keep the old index as a column in the DataFrame, you can use the drop=True argument
 If you want to modify the original DataFrame directly, you can set inplace=True.

df.loc[df["State/territory"]=="New South Wales"]
df.loc[...]
.loc[] is used for label-based indexing, and it allows you to filter rows based on a condition (the Boolean mask created in the previous step).
The Boolean mask inside the loc[] indexer is used to select only the rows where the condition is True.
Export DataFrame as csv
df.to_csv("australian_city_data.csv", index=False)
The argument index=False tells pandas not to include the index column in the output CSV file.
Next activity 3 :
Other data frame and other url . Dataframe is tables.
To find the right table we do tables[1] ,tables[2] and run it until we have the one we want .
Save the DataFrame : stats_df =pd.DataFrame(tables[5])
To drop the total row we put the number of the row, stats_df = stats_df.drop(24)
stats_df
Check data types
stats_df.dtypes

To remove and replace in the same operation something from names column :
columns =[ "GD","AGD"]
for column in columns:
    stats_df[column] = stats_df[column].str.replace("+","", regex = False)
    stats_df[column] = stats_df[column].str.replace("−", "-", regex=False)
stats_df

1. columns = ["GD", "AGD"]
This line creates a list of column names called columns, which contains two strings: "GD" and "AGD". These are the names of the columns in the stats_df DataFrame that you want to manipulate.
"GD" and "AGD" are assumed to be columns in the DataFrame (stats_df) that you wish to modify.
2. for column in columns:
This is a for loop that iterates over each column name in the columns list.
The loop will run twice because the columns list contains two items: "GD" and "AGD".
In the first iteration, column will be "GD".
In the second iteration, column will be "AGD".
3. stats_df[column] = stats_df[column].str.replace("+", "", regex=False)
In this line, you are applying a string operation to the values in the specified column (either "GD" or "AGD") of the stats_df DataFrame.
stats_df[column]: This selects the column (either "GD" or "AGD") from the DataFrame.
.str.replace("+", "", regex=False): The .str accessor is used to apply string methods to each element of the column (since DataFrame columns are treated as Series, you can use .str to apply string operations).
replace("+", "", regex=False): This tells pandas to replace all occurrences of the + symbol with an empty string ("") in the values of the column.
regex=False: This ensures that the + is treated as a literal character, not a regular expression. If regex=Truewere specified, the + would be interpreted as a regex special character (which means "one or more of the preceding character"), but here we just want to replace the + sign itself.
This line essentially removes the + sign from the data in the column.
4. stats_df[column] = stats_df[column].str.replace("−", "-", regex=False)
This line performs a similar operation but focuses on replacing a different character.
replace("−", "-", regex=False): Here, you are replacing the − (a minus sign) with the standard hyphen-minus (-).
This is important because the minus sign (−) is visually similar to the standard hyphen-minus (-), but they are different characters in Unicode. The minus sign (−) is used in some mathematical contexts, while the hyphen-minus (-) is the standard character used for negative numbers in text and programming.
By using this line, you're ensuring consistency, converting any instances of the Unicode minus sign into the standard hyphen-minus sign, which is often preferred in data processing and is compatible with most programming and data tools.
5. Result:
After these operations, for each of the columns ("GD" and "AGD"), the following transformations occur:
Any + sign is removed.
Any − (minus sign) is replaced with the - (hyphen-minus).
# Convert the following columns to dtype int
cols = ["Pld", "D", "GD"]

for col in cols:
    stats_df[col] = stats_df[col].astype('int')
    
# Convert the "AGD" column to dtype float
stats_df["AGD"] = stats_df["AGD"].astype('float')
stats_df

Activity 4
An API (Application Programming Interface) is a set of rules, protocols, and tools that allow different software applications to communicate with each other. It defines how software components should interact and provides a way for one application to request data or functionality from another application or service.
Methods: The operations available in an API are often based on common HTTP methods, including:
GET: Request data from the server (retrieve data).
POST: Submit data to be processed by the server (create or send data).
PUT: Update existing data on the server.
DELETE: Remove data from the server.
PATCH: Partially update existing data.
Data Formats: APIs often exchange data in standardized formats, such as:
JSON (JavaScript Object Notation): A lightweight, easy-to-read data format that is commonly used in APIs.
XML (Extensible Markup Language): Another format used for structuring data, though less common today than JSON.

import requests
url = url + "?format=json"
1. import requests:
This line imports the requests library, which is a popular Python library used to send HTTP requests (like GET, POST, PUT, DELETE, etc.) to web servers. It is often used for interacting with web APIs or fetching data from websites.
requests: Provides functions to make HTTP requests.
It simplifies the process of working with APIs, fetching data from URLs, and handling responses.
2. url = url + "?format=json":
This line modifies the variable url by appending the string "?format=json" to the existing URL.
url: This is a string variable that holds a URL, which is typically the address of an API endpoint or a webpage. In this case, it’s assumed to be a URL of an API that you want to request data from.
"?format=json": This is a query string appended to the URL. Query strings are typically used to pass parameters to the server in the URL.
The ? indicates the start of the query string in a URL (if there are no previous query parameters).
format=json specifies that the server should return the response in JSON format.
So, "?format=json" tells the server to respond with data in JSON format (JavaScript Object Notation), which is a widely-used, structured format for representing data.
<Response [200]> means that the code can run , if is 404 is error 
# Check if the request was successful (status code 200) if response.status_code == 200: # Parse the JSON response and print it data = response.json()  # This converts the JSON response to a Python dictionary print(data) else: print("Request failed with status code:", response.status_code)

200 Status Code (OK):
Meaning: Success.
Explanation: The request has been successfully processed by the server, and the server has returned the requested resource.
3xx - Redirection Codes
4xx - Client Error Codes
5xx - Server Error Codes
Summary of Some Common Status Codes:


When I need to retrieve API output by using CONTENT attribute (content refers to the body of the response—the actual data that the API or server sends back):
response_content = response_data.content
print(response_content)

So the action is : response_data.content (response_data = request.get(url) ) and then I save it in response_content (new variable ), after I print I’m gone have a list of  dictionaries.
Use json function from json library format
Let's break down each part of the code and explain what each line does, especially focusing on the json() function and the json.dumps() function.
The Goal:
In this example, you're making a request to an API, parsing the returned JSON data, and then formatting that data to be more readable (pretty-printed).
import json

# Formatting as json
data = response_data.json()

json.dumps():
The json.dumps() function is part of the built-in json library. It converts a Python object (like a dictionary or list) into a JSON-formatted string.
The indent=4 argument is used to format the output with 4 spaces of indentation, which makes it easier to read.

# Add indents to JSON and output to screen
print(json.dumps(data, indent=4))
Printing the result:
The formatted_json will now be a human-readable JSON string, nicely indented, and ready for output.

Ricapitolando : Full Flow:
Send the Request: You send a GET request to the API endpoint, requesting data.
Get the Response: The server sends back the requested data, typically in JSON format.
Parse the JSON: You convert the JSON response into a Python dictionary using .json().
Pretty-Print the JSON: You then convert that Python dictionary back into a JSON string with nice formatting using json.dumps() and indent=4. (The indent=4 parameter is commonly used in JSON serialization and deserialization to specify the number of spaces to use for indentation(rientranza) in the output JSON string. This makes the JSON output more readable by formatting it with a specified number of spaces for each indentation level.)
Output the Result: Finally, you print the formatted JSON string for human readability.

# Select country and GDP value for second row
country = data[1][1]['country']['value']
gdp_value = data[1][1]['value']

print("Country: " + country)
print("GDP Value: " + str(gdp_value))

You have multiple dictionaries in the second row (second row because is inside the list that opened another list which is the second one ) and if you count from 0 in the position 1 you’ll have country (in this one you have to get his 1 value also which counting from 0 is “value” ..check again why gap value

Select values and store as variables : # Select two values
data_variable = data['results'][0]['name']
data_variable_2 = data['results'][0]['birth_year']

Print those values : print(data_variable)
print(data_variable_2)

Is gone turn out Luke Sky and 19BBY , the name and the birthday


ACTIVITY 7
The ?count=2 or ?count=6 in a URL represents query parameters. Query parameters are used to pass additional information to the server in the URL. They are appended to the end of the URL after a question mark (?) and are typically used to filter or modify the response from the server.
Here's a breakdown:
Query Parameter Structure: The query parameters are added to the URL in the format ?key=value. Multiple parameters can be added by separating them with an ampersand (&), like ?key1=value1&key2=value2.
Example Usage: In the context of an API, ?count=2 might be used to specify that you want the server to return 2 items, and ?count=6 would request 6 items.
Activity 8 
Why do I have all those loops? : 
for x in range(5): Loop:
Purpose: To paginate through multiple pages of results from the API.
Explanation: APIs often limit the number of results returned in a single request. To get all results, you need to make multiple requests, each fetching a different subset of the data. The range(5) loop runs 5 times, simulating the fetching of 5 pages of results.
Example: If each page contains 50 results, this loop will fetch results 0-49, 50-99, 100-149, 150-199, and 200-249.
post_response = requests.get(url + "?offset=" + str(x * 50)).json():
Purpose: To make an API request for a specific page of results and parse the JSON response.
Explanation: This line constructs the URL with the appropriate offset query parameter to fetch the correct subset of results. The offset is calculated as x * 50, where x is the current iteration of the loop. The requests.get() function makes the HTTP GET request, and .json() parses the response as JSON.
Example: On the first iteration (x = 0), the URL might be https://api.example.com/posts?offset=0. On the second iteration (x = 1), the URL might be https://api.example.com/posts?offset=50.
for result in post_response["entries"]: Loop:
Purpose: To iterate through the list of entries in the current page of results and append them to a cumulative list.
Explanation: The API response is expected to contain a key entries that holds the list of results for the current page. This loop iterates over each entry in that list.
Example: If post_response["entries"] contains 50 results, this loop will run 50 times, appending each result to the response_json list.
response_json.append(result):
Purpose: To collect all entries from all pages into a single list.
Explanation: Each entry from the current page is appended to the response_json list, which accumulates results from all pages.
Example: After all iterations of the outer loop, response_json will contain all the entries from all fetched pages.
Full Example Code with Comments:

The pd.json_normalize function in the pandas library is used to normalize semi-structured JSON data into a flat table (DataFrame). This function is particularly useful when dealing with nested JSON data, as it helps to convert the nested structure into a tabular

import requests

url = "https://api.example.com/posts"
response_json = []

# Loop to paginate through multiple pages
for x in range(5):  # Fetch 5 pages of results
    # Make the API request for the current page
    post_response = requests.get(url + "?offset=" + str(x * 50)).json()
    
    # Loop through the "entries" of the current page and append them to the response_json list
    for result in post_response["entries"]:
        response_json.append(result)

# Print the collected results
print(response_json)

Summary:
for x in range(5):: Iterates to fetch multiple pages of results.
post_response = requests.get(url + "?offset=" + str(x * 50)).json(): Makes an API request for a specific page and parses the JSON response.
for result in post_response["entries"]:: Iterates through the entries in the current page.
response_json.append(result): Collects all entries into a single list.
The overall purpose is to paginate through the API results, collect all entries from multiple pages, and store them in a single list for further processing or analysis.

Let's break down the purpose of each part of the code: the for in range loop, the post_response request, and the for in loop. Purpose of Each Part: **`for x in range(5):` Loop**: - **Purpose**: To paginate through multiple pages of results from the API. - **Explanation**: APIs often limit the number of results returned in a single request. To get all results, you need to make multiple requests, each fetching a different subset of the data. The `range(5)` loop runs 5 times, simulating the fetching of 5 pages of results. - **Example**: If each page contains 50 results, this loop will fetch results 0-49, 50-99, 100-149, 150-199, and 200-249. **`post_response = requests.get(url + "?offset=" + str(x * 50)).json()`**: - **Purpose**: To make an API request for a specific page of results and parse the JSON response. - **Explanation**: This line constructs the URL with the appropriate `offset` query parameter to fetch the correct subset of results. The `offset` is calculated as `x * 50`, where `x` is the current iteration of the loop. The `requests.get()` function makes the HTTP GET request, and `.json()` parses the response as JSON. - **Example**: On the first iteration (`x = 0`), the URL might be `https://api.example.com/posts?offset=0`. On the second iteration (`x = 1`), the URL might be `https://api.example.com/posts?offset=50`. **`for result in post_response["entries"]:` Loop**: - **Purpose**: To iterate through the list of entries in the current page of results and append them to a cumulative list. - **Explanation**: The API response is expected to contain a key `entries` that holds the list of results for the current page. This loop iterates over each entry in that list. - **Example**: If `post_response["entries"]` contains 50 results, this loop will run 50 times, appending each result to the `response_json` list. **`response_json.append(result)`**: - **Purpose**: To collect all entries from all pages into a single list. - **Explanation**: Each entry from the current page is appended to the `response_json` list, which accumulates results from all pages. - **Example**: After all iterations of the outer loop, `response_json` will contain all the entries from all fetched pages. Full Example Code with Comments: import requests url = "https://api.example.com/posts" response_json = [] # Loop to paginate through multiple pages for x in range(5): # Fetch 5 pages of results # Make the API request for the current page post_response = requests.get(url + "?offset=" + str(x * 50)).json() # Loop through the "entries" of the current page and append them to the response_json list for result in post_response["entries"]: response_json.append(result) # Print the collected results print(response_json)Summary: **`for x in range(5):`**: Iterates to fetch multiple pages of results. **`post_response = requests.get(url + "?offset=" + str(x * 50)).json()`**: Makes an API request for a specific page and parses the JSON response. **`for result in post_response["entries"]:`**: Iterates through the entries in the current page. **`response_json.append(result)`**: Collects all entries into a single list. The overall purpose is to paginate through the API results, collect all entries from multiple pages, and store them in a single list for further processing or analysis.

Sourcing 2

amount=1 tells the way I want to store data , how do I know? I go through the documentarian 

Once I get the response I can see the keys and the values by texting response.keys() , and for the values response.values() ; I’m gone have a dictionary with keys or values .
If I go through the first key like resposne[‘results’]  it’s gone come out a list with all the info . Idc you want to obtain data from a dictionary you access with a key , if you want to obtain data from a list you access with an index .
So by index I have to put [0] so 
resposne[‘results’]  [0] 
If I have {} means that the first value of the list is a dictionary and to see the key inside resposne[‘results’]  [0].keys(0)
Lets say from all those key I want the “question” info 
resposne[‘results’]  [0][‘queston’] ; if I want to get the first value of that I use index [0] for the first value or [1] for the second value .

To see what kind of data would you like to search for : 
Search_option_text = str(list(search_options.keys())).replace(“[“,””).replace(“]”,””)
Question = (“What topic would you like to get trivia for :”) + search_options_text + “?\n

“?\n”
\n is a newline character. It tells the program to move to the next line after this string is printed. When you include \n, it effectively creates a line break in the output, so anything printed afterward will appear on a new line.
So in this activity we put input because we are interacting with someone in this game ,so after the question and after we made a list with that is in search_options_text , we do keys_of_options = input(question).
If the person I’m interacting with is not typing the one of the options that I have in the right way I need to fix it and I make a loop.  
 If kind_of_search.title() not in search_options : this is gone capitalize the letter Computer for example . We need to see where we can help the person .  
If the search is not in the options I’m gone to
If kind_of_search.title() not in search_options : 
print(f”Category must one of the choices {search_options_text}. Please provide correct input.”) 
Else: 
  While true :
           Difficulty = input(“What difficulty should trivia be :” + difficulty_options_text+”?]n”) difficulty has to be one of the choices easy ,med, hard cause it’s what I saved before in the info. But if is not 
If difficulty.lower() not in difficulty_options:
print(f”difficulty must be one of the choice {difficulty_options_texrt}. Pls ectc”)
 else: break   … space .. break again . Is gone print error .I did 

Response = request.get(url + “amount=1&category=“ +search_options{kind_of_search} + ‘&difficulty=‘ + difficulty.lower()).json 
DATA is costing and depends on how many time you call that data , we are going to create an API key . The key establish how many . We have to create a new file called .env and if is called like that is not gone be sharable . You can have multiple keys in there . 
To read the variables : from dotenv import load_dotenv and then “import” os ,so we can import os package .
Then load_dotenv() 
api_keys =os.getenv(‘Nasa API KEY’)
Then we do : import request , import json , import panda as pd 
I go to the website and select the url of geomagnetic storm and take the base of it ; save it as a variable base_url = “http://api.nasa.gov/DONKI/GST" 
start_date = “ 2024-04-01”
end_date = “2024-05-05”
Then I create the url 
query_url = f’{base_url}?startDate={start_date}&endDate{edn_date}&api_key={api_key}
response_data =request.get(query_url)
Data = response_data
print(json.dumps(data,indent=4))
I see that I have 18 elements in the list , I want to see the keys of the first element : data[0].keys , then I want to go deeper and get one of the keys data[0][“name oftheelement’]. Link events is a key so :data[1][‘linkevents’]
Df = pd.json_normalize(data)
df[[‘bla’,’bla,’bla’]] keeping this I’m gone have normalize the info for this .
For loop and explode() function:
Because the link events contains multiple events per row and we want to spread them individually . :
expanded_rows = [] store the data that we create 
For I in df.index:
      activityID = df.loc[I,’gstID’]
      startTime= df.loc[I, ‘startTime’]… 
# Initialize an empty list to store the expanded rows
expanded_rows = []

# Iterate over each index in the DataFrame
for i in df.index:
    activityID       = df.loc[i, 'gstID']         # Get the corresponding value from 'gstID'
    startTime        = df.loc[i, 'startTime']     # Get the corresponding value from 'startTime'    
    linkedEvents_col = df.loc[i, 'linkedEvents']  # Get the list of dictionaries in 'linkedEvents_col'
    
    # Iterate over each dictionary in the list
    for item in linkedEvents_col:
        # Create a new row with the dictionary and corresponding 'activityID' and 'startTime' value
        expanded_rows.append({'gstID': activityID, 'startTime': startTime, 'linkedEvents': item})

# Create a new DataFrame from the expanded rows
df_for_loop = pd.DataFrame(expanded_rows)

# Use the head function to show the dataframe
df_for_loop.head()

This is to get the individuals values from the lists in link events , so we’ll have more rows because the info will be individual . 
Activity 7
I create the query_url f’{url} +appid={api_keys}’ how do I know that my app id is in api_keys ? Because I checked on the website and is saying it.
So I have a list with parameters , there is units in it so I add it at the url &units={units}&q=
2 sourcing data for AI project 
API is how we communicate with other resources , api are creating those bridges so we can connect to datas and have them back the way we can read the ,with the request we need . 

Everyone is gone store data however they want :
search_options = {'Computers':'18','Mathematics': '19', 'Mythology':'20', 'Sports':'21'}

We need to go through the documentation and create the url 
response = requests.get(url + "amount=1" + '&' + 'category=' + search_options['Mathematics']).json()

If is a dictionary we can use response.keys() and I run it and I’ll see I have two keys 
I go through the first key response[‘responde_code’]
If you want to obtain data from the dictionaries you acses with a key , if you want a list you access with an index .
So now I want to go into the list so response[‘results’][0] that means that I go with the [0] index so first list to see response[‘results’][0].keys() here I see all the keys in that dictionary . 
response[‘results’][0][‘incorrec_answrr_’][0]
We are working with data , is money and private . If you have data that anyone has it there is a lot of websites you can sell it . You can have restrictions of data .you need to pay for data if you are professional. We need to create api keys and th minister is gone chose which benefits you have . You should not share your api keys because they are not free , also make sure you use them properly . Every time we are making an API  call we make a key.
In viscose we don’t save it in the file but we create a new file called : example.env so every file that have an .env are files that you are not sharing so anyone can take it cause is your key, where you save the key : nasa_api_key= “jdbhdfvdshja” example. You can have multiple keys there 
To read that variable we do :
From doting import load_dotenv
Import os
load_dotenev()
It says : True 
How I retrieve the key os.getenv(‘the name of the key you take from the hided env file ,but not the actual one just the variable )if I run it is gone come out the key .
Then we put everything in a variable .
Once you know where the data is you do the loops 
Explode : if you have a collection with a list with multiple values the code is gone put the list 
To create the file : click on unsolved and new file : command s and write down the name .
File text then is opening a page and you press command s so you can name it with .env ,nothing else.
If I want the attitude of London I go in the data dictionaries , I see is inside coordinates , inside that I have another dictionary so to find it I do weather_json[‘coord’][‘lat’] : like that I find it . Then I see weather_json.keys() and I see all the keys  ,I pick one value weather_json[‘main’][temp’] , after I put just main I see temp is there so thats why then I put temp and came out 5.56. 
weather_dictionary = { ‘city’:cities, .. 
Pd.DataFrame(weather_dictionary) , like this is gone display a nice data frame of what we found out ,of what we need.
Sometimes I can get an error 
Try:
  student[‘Maria’]
Except:
  print(“don’t know what happened , I think you had an invalid key) . So if I bring a key that I don’t have in the dictionary 
So maybe I know whats the error but I don’t want the code to break , the try except is allowing you to not break the code 
 The thing you have to learn is going trough json and navigate is not difficult is just long , you have to read the data in json and find where is it .
When you call load_dotenv(), it reads the .env file in the current directory (or from the file path you specify) and sets each key-value pair as an environment variable.
Then, you can access the variables using os.getenv(), just like accessing system environment variables.

import requests
import pandas as pd
from dotenv import load_dotenv
import os

# Load environment variables from .env file
load_dotenv()

# Retrieve API key from environment variables
api_key = os.getenv("API_KEY")

# Use the api_key to make requests or perform other operations
response = requests.get(f"https://api.example.com/data?api_key={api_key}")

# Process the response, for example, into a DataFrame
data = response.json()
df = pd.DataFrame(data)
