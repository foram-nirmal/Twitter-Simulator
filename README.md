# Twitter-Simulator


### PART I


The Main driver file is server.ex

Program Description:
The goal of this was to implement a Twitter-like engine.


### Input Format:

Building and Execution instructions

To Run all the test cases

Navigate into the folder Project 4/project4_1
mix test


#### Functionality
Register the users.
Randomly choose some users to be logged in and some to be logged out.
Randomly choose followers for each user.
Predefine hashtags to be randomly chosen in each tweet.

Check if the user is logged in, if yes start publishing tweets.
-->Some tweets are @another _user or without a mention.

-->Send each tweet to the main server which then forwards it to all its followers and the @mentioned user.

-->Each node keeps publishing tweets till it reaches the max number defined.

-->The main server handles all the distribution of tweets.

-->As a node receives a tweet it adds it to its own feed.

-->Each tweet received is randomly retweeted based on a probability.

-->Retweets are also sent to the appropriate feeds.

If the user was logged out it does not send any tweets nor receive them live.
Once each node has sent out the required number of tweets the program stops sending further tweets.
For users that were logged out, we use queries and build up its feed by searching the ETS tables and matching it with the user they follow. We end up building a twitter feed that the user should have received
if they were logged in.

#### Test Cases
Check report for more detail.






### PART II

The goal of this was to implement a user interface for the simulator created in project 4.1 using Phoenix that allows access to the ongoing simulation using a web browser.

#### Phoenix installation steps:
To start your Phoenix server:

  * Install dependencies with `mix deps.get`
  * Install Node.js dependencies with `cd assets && npm install`
  * Start Phoenix endpoint with `mix phx.server`

Now you can visit [`localhost:4000`](http://localhost:4000) from your browser.


#### Functionalities

Register the users -> A user needs to be registered to log in. As soon as the user gets registered, a list of existing user pops up on the screen. The user can click "Login" with the specific username to login to the system

As soon as the user logs in, following are the activities which she/he can perform:
    1. Tweet -> User can write a tweet and post using the "Post" button. This tweet will appear in her/his own feed.
                This same tweet will be visible to all the subscribers of the current user.
                
    2. Followers -> Current user can write in the followers textbox a user which it would like to be its subscriber. 
            -If the user doesn't exist, there is an alert which specifies "Invalid user"
            -If the user types his own username, there is an alert which says "Cannot follow itself"
            -If none of the above holds true, current user successfully the gets the follower
            
    3. Mentions -> A tweet may or may not have a mention.
            -Irrespective of whether the current user follows the user it's mentioning, the same tweet would appear on the        feed of the user mentioned. 
            -The tweet doesn't get added to user's feed if the mentioned user doesn't exist
            -The current user can also mention the user to which it is subscribed to.
            -The current user can search for all the mentions of a given user using the "Mentions search box"
            
    4. Hashtags -> A tweet may or may not have a hashtag
            -The current user can search for a specific hashtag using the "Hashtags search box"
            
    5. Retweets -> Every tweet appearing on user feed has the fuctionality of being retweeted.
            -If the current user retweets some tweet, tweet gets added to its own feed
            -If the retweet contains a mention, tweet gets added to the mentioned user

