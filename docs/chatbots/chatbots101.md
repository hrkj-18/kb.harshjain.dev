# Building Chatbots in Python 

### EchoBot I 

```python
bot_template = "BOT : {0}"
user_template = "USER : {0}"

# Define a function that responds to a user's message: respond
def respond(message):
    # Concatenate the user's message to the end of a standard bot respone
    bot_message = "I can hear you! You said: " + message
    # Return the result
    return bot_message

# Test function
print(respond("hello!"))
```
>>I can hear you! You said: hello!

### EchoBot II
```python
# Create templates
bot_template = "BOT : {0}"
user_template = "USER : {0}"

# Define a function that sends a message to the bot: send_message
def send_message(message):
    # Print user_template including the user_message
    print(user_template.format(message))
    # Get the bot's response to the message
    response = respond(message)
    # Print the bot template including the bot's response.
    print(bot_template.format(response))

# Send a message to the bot
send_message("hello")
```
>>USER : hello <br>
>>BOT : I can hear you! You said: hello

### Creating a personality

### ChitChat

```python
# Define variables
name = "Greg"
weather = "cloudy"

# Define a dictionary with the predefined responses
responses = {
  "what's your name?": "my name is {0}".format(name),
  "what's today's weather?": "the weather is {0}".format(weather),
  "default": "default message"
}

# Return the matching response if there is one, default otherwise
def respond(message):
    # Check if the message is in the responses
    if message in responses:
        # Return the matching message
        bot_message = responses[message]
    else:
        # Return the "default" message
        bot_message = responses["default"]
    return bot_message
```
In [1]: send_message("what's today's weather?")
>>USER : what's today's weather? <br>
>>BOT : the weather is cloudy

In [2]: send_message("what's your name?")
>>USER : what's your name? <br>
>>BOT : my name is Greg

In [3]: send_message("what's your favorite color?")
>>USER : what's your favorite color? <br>
>>BOT : default message

### Adding variety

```python
# Import the random module
import random

name = "Greg"
weather = "cloudy"

# Define a dictionary containing a list of responses for each message
responses = {
  "what's your name?": [
      "my name is {0}".format(name),
      "they call me {0}".format(name),
      "I go by {0}".format(name)
   ],
  "what's today's weather?": [
      "the weather is {0}".format(weather),
      "it's {0} today".format(weather)
    ],
  "default": ["default message"]
}

# Use random.choice() to choose a matching response
def respond(message):
    if message in responses:
        bot_message = random.choice(responses[message])
    else:
        bot_message = random.choice(responses["default"])
    return bot_message
```

In [1]: send_message("what's your name?")
>>USER : what's your name? <br>
>>BOT : my name is Greg

In [2]: send_message("what's your name?")
>>USER : what's your name?<br>
>>BOT : I go by Greg

In [3]: send_message("what's your name?")
>>USER : what's your name?<br>
>>BOT : they call me Greg

### ELIZA I: asking questions

```python
import random

# Create a responses dictionary
responses = {'statement': ['tell me more!', 
                            'why do you think that?', 
                            'how long have you felt this way?',
                            'I find that extremely interesting',
                            'can you back that up?',
                            'oh wow!', ':)'
                          ], 
             'question':  ["I don't know :(", 
                            'you tell me!'
                          ]
            }

def respond(message):
    # Check for a question mark
    if message.endswith("?"):
        # Return a random question
        return random.choice(responses["question"])
    # Return a random statement
    return random.choice(responses["statement"])


# Send messages ending in a question mark
send_message("what's today's weather?")
send_message("what's today's weather?")

# Send messages which don't end with a question mark
send_message("I love building chatbots")
send_message("I love building chatbots")
```
>>USER : what's today's weather? <br>
>>BOT : you tell me! <br>
>>USER : what's today's weather? <br>
>>BOT : I don't know :( <br>
>>USER : I love building chatbots <br>
>>BOT : can you back that up? <br> 
>>USER : I love building chatbots  <br>
>>BOT : oh wow!

### ELIZA II: Extracting key phrases
```python

rules={'I want (.*)': ['What would it mean if you got {0}',
                       'Why do you want {0}',
                       "What's stopping you from getting {0}"
                      ],
       'do you remember (.*)': ['Did you think I would forget {0}',
                                "Why haven't you been able to forget {0}",
                                'What about {0}',
                                'Yes .. and?'
                               ],
       'do you think (.*)': ['if {0}? Absolutely.', 
                             'No chance'
                            ],
       'if (.*)': ["Do you really think it's likely that {0}",
                   'Do you wish that {0}',
                   'What do you think about {0}',
                   'Really--if {0}'
                  ]
      }
  
# Define match_rule()
def match_rule(rules, message):
    response, phrase = "default", None
    
    # Iterate over the rules dictionary
    for pattern, responses in rules.items():
        # Create a match object
        match = re.search(pattern, message)
        if match is not None:
            # Choose a random response
            response = random.choice(responses)
            if '{0}' in response:
                phrase = match.group(1)
    # Return the response and phrase
    return response.format(phrase)

# Test match_rule
print(match_rule(rules, "do you remember your last birthday"))
```
>>Did you think I would forget your last birthday

### ELIZA III: Pronouns

```python
# Define replace_pronouns()
def replace_pronouns(message):

    message = message.lower()
    if 'me' in message:
        # Replace 'me' with 'you'
        return re.sub("me", "you", message)
    if 'my' in message:
        # Replace 'my' with 'your'
        return re.sub("my", "your", message)
    if 'your' in message:
        # Replace 'your' with 'my'
        return re.sub("your", "my", message)
    if 'you' in message:
        # Replace 'you' with 'me'
        return re.sub("you", "me", message)

    return message

print(replace_pronouns("my last birthday"))
print(replace_pronouns("when you went to Florida"))
print(replace_pronouns("I had my own castle"))
```
>>your last birthday <br>
>>when me went to florida <br>
>>i had your own castle

### ELIZA IV: Putting it all together

```python
# Define respond()
def respond(message):
    # Call match_rule
    response, phrase = match_rule(rules, message)
    if '{0}' in response:
        # Replace the pronouns in the phrase
        phrase = replace_pronouns(phrase)
        # Include the phrase in the response
        response = response.format(phrase)
    return response

# Send the messages
send_message("do you remember your last birthday")
send_message("do you think humans should be worried about AI")
send_message("I want a robot friend")
send_message("what if you could be anything you wanted")
```
>>USER : do you remember your last birthday <br>
>>BOT : What about my last birthday <br>
>>USER : do you think humans should be worried about AI <br>
>>BOT : if humans should be worried about ai? Absolutely. <br>
>>USER : I want a robot friend <br>
>>BOT : What's stopping you from getting a robot friend <br>
>>USER : what if you could be anything you wanted <br>
>>BOT : Really--if me could be anything me wanted
