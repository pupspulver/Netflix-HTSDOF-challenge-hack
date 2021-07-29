# Netflix HTSDOF challenge Hack
A Python hack for [howtohackmoritzonlinefast.com](https://www.howtohackmoritzonlinefast.com) Netflix challenge to score the perfect Time! (5s)

INFO: The challenge is over, but the game is still online.

## About the game
[howtohackmoritzonlinefast.com](https://www.howtohackmoritzonlinefast.com) is a JS game where the player has to complete 4 challenges:
1. Sorting pills into the correct order.
2. Providing answers to a series of questions.
3. Finding a password via navigating through several clues across various websites.
4. Navigating through a maze, ensuring you pass through a number of unique nodes against a timer.

Upon successfully completing all 4 challenges, the player submits its time, name and email and is asked to answer a creative question.

## How does the hack work?
The program makes requests directly to the game API endpoint (https://www.howtohackmoritzonlinefast.com/api) to solve the 4 challenges directly. The server logs the time passed between the Begin and End challenge requests. When all 4 challenges are solved, the program send the player's data to submit the game results (the server returns the total game score). 

## Getting Started
It's easy, just run `howtohackmoritz.py`.  
*Optional: if you want you can add your name and email to `dataCom` (in `class hackmoritz()`).*

## API calls and endpoints

* Start a new game, get gameID:
 
  * Method: POST
  * Endpoint: `{apiPath}/game/start`  
   
   
* Begin a challenge:
   
   * Method: POST
   * Endpoint: `{apiPath}/game/challenge/{challenge_num}/begin`    
   * Payload Data: `{"game-id": gameID}`


* End a challenge, send fake results (highest score 10):

   * Method: POST
   * Endpoint: `{apiPath}/game/challenge/{challenge_num}/result`  
   * Payload Data: `{"game-id": gameID, "score": "10", "time": unixTime}`


* Submit Game results:
   
   * Method: POST
   * Endpoint: `{apiPath}/competition`   
   * Payload Data: `{
        "game-id": gameID,
        "first-name": "your",
        "last-name": "name",
        "age-agreement": "true",
        "country": "true",
        "email": "your@email.com",
        "answer": "drugazon",
        "terms-agreement": "true"
    }`


Used Headers: 
```
headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:89.0) Gecko/20100101 Firefox/89.0",
    "Accept": "application/json, text/plain, */*",
    "Alt-Used": "www.howtohackmoritzonlinefast.com"
}
```

## Disclaimer

This repository is for education purposes only, the use of this code is your responsibility.

I take NO responsibility and/or liability for how you choose to use any of the source code available here. By using any of the files available in this repository, you understand that you are AGREEING TO USE AT YOUR OWN RISK. Once again, ALL files available here are for EDUCATION and/or RESEARCH purposes ONLY.
