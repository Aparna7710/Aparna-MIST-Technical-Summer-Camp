# Web Server Module

## GraphQL - Introspection
This challenge aimed to introduce us to the concept of GraphQL schema and introspection.

### Solution
1. I started with the video about GraphQL from the suggested playlist since I was completely clueless about this concept.
2. I then opened the site through burpsuite to try and find the get and post requests and the exact GraphQL queries.
3. Here, I found the base query "query":"{ rockets(country: \"Europe\") { name, country, is_active } }" and to explore all possible hidden values I changed the query to "{ __schema { queryType { fields { name } } } }"
4. From here, I found the type "IAmNotHere" and so I changed the query to "{"query":"{ __type(name:\"IAmNotHere\") { fields { name } } }}"", to inspect further.
5. There, I found the fields very_long_id and very_long_value and modified the query accordingly but I got an error indicating something about an int value.
6. So, I went back a few steps and used the query "{"query":"{ __schema { queryType { fields { name args { name type { name kind ofType { name } } } } } } }}"" to try and inspect the type IAmNotHere a bit more thoroughly.
7. Now I was finally able to understand the required query syntax and started going on giving the query, "{"query":"{ IAmNotHere(very_long_id:1) { very_long_id very_long_value } }}"" and as I kept changing the numbers I started getting more and more letters. 
8. By number 14 I ended up with the message "nothing here lol"
9. I kept going and by number 17 I got the required flag.


### Flag
> RM{1ntr0sp3ct1On_1s_us3ful}

### Resources
Youtube, BurpSuite, Help from mentor
