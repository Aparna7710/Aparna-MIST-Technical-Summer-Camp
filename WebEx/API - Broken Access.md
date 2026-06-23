# Web Server 

## API - Broken Access
This challenge gave us a site and asked us to inspect its security. 

### Solution
1. Firstly I tried creating multiple users and I realised that the user ids are assigned sequentially and that user id: 1 has been reserved for the root user.
2. I also noticed that the user id was stored as a path which made think that it shld be possible to access other users including the root user.
3. I tried changing the normal url itself to "http://api-broken-access.challenge01.root-me.org/#/default/get_api_user?userid=1" and other possible versions but that led nowhere.
4. Inspecting the site didn't give me much clues either.
5. I then opened burpsuite, and with intercept off I created a new user.
6. Then I went to HTTP history and started looking at the response and request of the GET user commands.
7. Since I was not fully familiar with burpsuite and was not sure exactly how to intercept the request, I took to google to help to try and understand.
8. From there I understood about sending the request to the repeater and inspecting that way.
9. On inspecting from the repeater, I noticed "GET /api/user HTTP/1.1" and knew I had to modify this somehow to access the root user.
10. After several syntax attempts like, "GET /api/user?id=1 HTTP/1.1", I finally landed on "GET /api/user/1 HTTP/1.1" which gave me access to the root user id.


### Flag
> RM{E4sy_1d0r_0n_API}

### Resources
Google, BurpSuite
