# Agent Server

Write a simpler version in flask server, to create a public web service for an internet of thing for a backend agent. It has a public URL for the post API.

The post request body is:

```

{"agent": "agent name", "action": "action name", prompt:"", expire: int}

```


On the server side, it store the action in a db in format of a queue, push it by time order. The agents can connect to server, listen to the agent name, if it is calling this agent, pop the request from queue DB, do the requested action.

If the request expires in given "int" seconds without any agents pop it, delete that request.

It has a queue for two topics, one for "show example video" agent, the other for "do a dance" agent.

Add debuging log
Add port and debug and threaded to arg from config

Implement a simple Auth check the API key in header, give a random key, http Auth Type is basic
Use this sample key "YWdlbnQ6eW91cl9hcGlfa2V5X2hlcmU=" in the code, make the code cleaner and simpler. 

# Agent Client

Write a client for "show_example_video" agent in python to use "browser use" tool. It polls the request from given url, which is given from arg. integration the for loop polling with the following code, replace the "task" part with request from the action get from app.py. keep loop polling until ctr-c by user. Don't do multi-threads, do one action per time.

## Show sample video agent
When user close the opened chromun broswer, force to stop the "browser use" instance, and continue the action polling.
Use the following system prompt

"""
1. Open YouTube (www.youtube.com).
2. Search for videos about "{task}".
3. Filter the search results to show videos with a duration of under 10 minutes.
4. From the filtered results, prioritize and select a video that is ideally around 5 minutes in length and appears to be a clear and concise lesson on the topic.
5. Click on the selected video to play it.
6. Wait for 5 mins for the video playing.
7. Close the browser and end task after 5mins."
"""

## Robot dance agent
Use this github project https://github.com/noamraph/mindstorms
To make a do_a_dance agent.
The robot has four motor: two motors in port A, C are legs, two motors on port B, D are arms.
Can also use beep, and flash hub light as well.

Make each dance around 10 seconds.
Have all above var in head of the files, e.g. port, 10 seconds.


