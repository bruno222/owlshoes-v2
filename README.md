## Video Demo

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/Ixx6tf_SoK4/0.jpg)](https://www.youtube.com/watch?v=Ixx6tf_SoK4)


## What

The idea behind this project is to optimize the cost efficiency of your Contact Center by enabling one Agent to handle multiple calls simultaneously, assisted by Virtual Agents.

The current challenge is that the world is not yet ready for Virtual Agents to completely take control of contact centers due to GPT still experiencing [Hallucination problems](https://en.wikipedia.org/wiki/Hallucination_(artificial_intelligence)), making them potentially untrustworthy.

The solution is to **SYNERGIZE YOUR AI**. Combine the best of AI with the intellect of humans.

## Architectural Overview

The below is an overview of the various services involved as well as the order of operations.

![Basic Overview](https://raw.githubusercontent.com/bruno222/wip/main/docs/images/basic_overview.png)

## Operating at Capacity
Below is what it could look like a with a fully trained agent simultaneously supporting 5+ conversations happening with the AI Assistant.

![Operating at Capacity](https://raw.githubusercontent.com/bruno222/wip/main/docs/images/enhanced.png)


With this project, your Agents (real human beings) can:

- Monitor multiple calls in real-time between your Customers and the Virtual Agents.
- Hijack/take over a call if they observe that the Virtual Agent is not responding correctly due to Hallucination problems.
- Send hints to the Voice Bot via text message in real-time to adjust and correct the direction of the conversations with the Voice Bot.

## Built-in Scenarios

**TODO** dive into the various situations that a caller can run into:
- new user / unknown user
- known user with existing order
-

## Built-in features

**TODO** highlight the functionality this repository provides today:
- sending SMS to confirm product selection
- ability for agent to monitor live transcripts
- ability for agent to enhance and modify existing context
- ability for agent to take control off the call, relieving the AI where necessary.
- send email with order confirmation details


**Disclaimer**: This is a hackathon project built in ~4 days and is not production-ready. Use at your own risk.

## Installing

To set up the project, you need to install at least 2 out of the 4 assets:

- [**mandatory**] ngrok - CLI tool to expose your computer so Twilio can send the Media Stream to your Node.js project.

- [**mandatory**] The Node.js project (back-end) - the core of the project. This can be hosted locally or on a cloud service such as AWS EC2 or other comparable providers.

- [**optional**] The Next.js project (front-end) - only necessary if you need to modify the HTML; otherwise, the back-end has a static version of the front-end within the /front-end/out folder.

- [**optional**] The Flex Plugin - required only if you intend to use the "hijack call" option to escalate the call from the Virtual Agent to the Real Human Agent.

#### Step 1 of 4 - Installing ngrok

1. Follow the instructions from Ngrok.
2. Execute `ngrok http 3000` to run it. For the sake of these instructions, let's say your `ngrok` returned `https://abcabc.ngrok.app`.
3. In your /call-gpt/.env, edit your `SERVER` env attribute to `SERVER="abcabc.ngrok.app"`.
4. Get a new phone number within Twilio Console ([here](https://console.twilio.com/us1/develop/phone-numbers/manage/incoming)) and configure the "When a call comes in" with the URL `https://abcabc.ngrok.app/incoming`

#### Step 2 of 4 - Installing the back-end

1. Clone this repo.
2. Execute `cd ./call-gpt` to go to the folder where the back-end is.
3. Ensure you have Node v18 or higher installed by executing `node -v`.
4. Run `npm install` to install the packages into your computer.
5. Rename `.env-example` from this folder to `.env` and follow the instructions in the `.env` file; you will need an [Deepgram account](https://deepgram.com/), an [OpenAI account](https://openai.com/) and finally an [ElevenLabs account](https://elevenlabs.io/).
6. Run `npm run dev` to start the project.
7. That's it! Open your ngrok URL (`https://abcabc.ngrok.app/`) in your browser to check if it loads.

#### Step 3 of 4 - Installing the front-end

1. Execute `cd ./front-end` to go to the folder where the back-end is.
2. Run `npm install` to install the packages into your computer.
3. Run `npm run` dev to start the project.
4. That's it! Open the URL of Next.js URL in your browser (`https://localhost:3001/`) to check if it loads! It has hot-reload, so you can change the files and see the updated version automatically.
5. Once you are happy with your changes, you can execute `npm run build`, and the static HTML will be recreated in the `/front-end/out` folder. So you don't need to execute this Front-end folder every time; only if you need to change something.

#### Step 4 of 4 - Installing the Flex Plugin:

1. Execute `cd ./flex-plugin-hackathon` to go to the Plugin folder.
2. Run `npm install` to install the packages into your computer.
3. You need to have the [Twilio CLI](https://www.twilio.com/docs/twilio-cli/quickstart). Type `twilio` in your terminal to see if you have it; if not, install it now.
4. You need the [Flex Plugins CLI](https://www.twilio.com/docs/flex/developer/plugins/cli/install). Type `twilio plugins` to make sure you have it; if not, install it.
5. You need to create a new profile for your Twilio CLI; type `twilio profiles:list` to check if you are using it correctly. If not, add a new profile with the command `twilio profiles:add`.
6. Run `twilio flex:plugins:deploy --changelog deploy` to deploy this Plugin.
7. Once **step 6** is finished, it will show the next steps; you will have to run the command mentioned there (something like `twilio flex:plugins:release ... etc etc`).
8. We are done! Go to https://flex.twilio.com - You should see your `back-end` project being loaded into Panel2 of Flex (loading the URL `http://localhost:3000` which is the URL of the back-end).

Happy Hacking! We can't wait to see what you build.
