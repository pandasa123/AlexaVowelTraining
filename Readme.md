# Word Trainer

![Architecture](https://gitlab.eecs.umich.edu/pandasa/AlexaVowelTraining/raw/master/Images/Architecture.jpg)

## Inspiration / What it does

Using Abstract Relational Concept, children can learn how to identify vowels and consonants through the juxtaposition of two words with a `distance == 1`. More on the Development of Relational Concepts and Word Definition in Literature section below

## How I built it

The entire concept revolves around finding words that are `distance == 1` apart. To do that, I built a Levenshtein script that takes in a `dictionary.txt` and outputs the necessary juxtapositions. The question bank is prepared using these juxtapositions and 3 random answer choices. 

To test, I recommend following the instructions in the repository: https://gitlab.eecs.umich.edu/pandasa/AlexaVowelTraining

## Challenges I ran into

I unfortunately started late and had a lot of coursework so I couldn't spend enough time on this but I would like to return to this and improve it in the following ways (next section) 

## What's next for Identifying Vowels and Consonants by Comparisons
* Change response type
* Possible extend quiz format: "What consonants are in 'cat'? What consonants are in 'car'? What consonants are in 'cat' but not 'car'?" 
* Integrate a proper dictionary to search definitions 

## Link to Skill in Store

https://www.amazon.com/dp/B078X83GQD/ref=sr_1_1?s=digital-skills&ie=UTF8&qid=1515607690&sr=1-1&keywords=word+trainer

### Usage

```text
Alexa, tell Word Trainer to start a game
	>> Welcome to Word Trainer. I will ask you multiple choice questions...

Alexa, start Word Trainer
```

### Repository Contents
* `/.ask`	- [ASK CLI (Command Line Interface) Configuration](https://developer.amazon.com/docs/smapi/ask-cli-intro.html)	 
* `/lambda/custom` - Back-End Logic for the Alexa Skill hosted on [AWS Lambda](https://aws.amazon.com/lambda/)
* `/models` - Voice User Interface and Language Specific Interaction Models
* `skill.json`	- [Skill Manifest](https://developer.amazon.com/docs/smapi/skill-manifest.html)
* `Word Finder.py` - Using a Levenshtein Distance Algorithm, find words that are `distance = 1` apart

## Setup w/ ASK CLI

### Pre-requisites

* Node.js (> v4.3)
* Register for an [AWS Account](https://aws.amazon.com/)
* Register for an [Amazon Developer Account](https://developer.amazon.com/)
* Install and Setup [ASK CLI](https://developer.amazon.com/docs/smapi/quick-start-alexa-skills-kit-command-line-interface.html)

### Installation
1. Clone the repository.

	```bash
	$ git clone https://github.com/alexa/skill-sample-nodejs-trivia/
	```

2. Initiatialize the [ASK CLI](https://developer.amazon.com/docs/smapi/quick-start-alexa-skills-kit-command-line-interface.html) by Navigating into the repository and running npm command: `ask init`. Follow the prompts.

	```bash
	$ cd skill-sample-nodejs-trivia
	$ ask init
	```

3. Install npm dependencies by navigating into the `/lambda/custom` directory and running the npm command: `npm install`

	```bash
	$ cd lambda/custom
	$ npm install
	```


### Deployment

ASK CLI will create the skill and the lambda function for you. The Lambda function will be created in ```us-east-1 (Northern Virginia)``` by default.

1. Deploy the skill and the lambda function in one step by running the following command:

	```bash
	$ ask deploy
	```

### Testing

1. To test, you need to login to Alexa Developer Console, and enable the "Test" switch on your skill from the "Test" Tab.

2. Simulate verbal interaction with your skill through the command line using the following example:

	```bash
	 $ ask simulate -l en-GB -t "start Word Trainer"

	 ✓ Simulation created for simulation id: 4a7a9ed8-94b2-40c0-b3bd-fb63d9887fa7
	◡ Waiting for simulation response{
	  "status": "SUCCESSFUL",
	  ...
	 ```
Here's how a sample response looks![Interaction](https://gitlab.eecs.umich.edu/pandasa/AlexaVowelTraining/raw/master/Images/Interaction.png)
	 
And here's a demo video: https://youtu.be/xlEj4wOH-O8

3. Once the "Test" switch is enabled, your skill can be tested on devices associated with the developer account as well. Speak to Alexa from any enabled device, from your browser at [echosim.io](https://echosim.io/welcome), or through your Amazon Mobile App and say :

	```text
	Alexa, start Word Trainer
	```
	
	
## Literature

Navarro, Gonzalo. "A Guided Tour to Approximate String Matching". Blanco Enchilada 2120 Santiago, Chile. http://repositorio.uchile.cl/bitstream/handle/2250/126168/Navarro_Gonzalo_Guided_tour.pdf

Swartz, Karyl, and Alfred E. Hall. “Development of Relational Concepts and Word Definition in Children Five Through Eleven.” Child Development, vol. 43, no. 1, 1972, pp. 239–244. JSTOR, JSTOR, www.jstor.org/stable/1127887.
