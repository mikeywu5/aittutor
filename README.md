# The Socratic Prompt Tutor

## Overview

During this workshop, we are going to build a custom "Socratic Tutor" on writing great prompts. This specialized AI
persona is designed to teach you the art of prompt engineering by actively guiding you to the answers, rather than
simply doing the work for you. In addition, this project perfectly showcases how the power of no-code AI development can
streamline workflows and build custom solutions, delivering practical, everyday value. Here are the top three reasons
why we chose this project for today:

1. Large Language Models (LLMs) already possess an exceptional grasp of writing, logic, and language mechanics. This
   allows LLM to teach you interactively how to develop and refine excellent prompts that AI can easily process and
   understand.
2. The best teacher for AI is AI. Because it excels at recognizing and producing highly effective prompts for itself,
   we can easily customize AI personas with specific rules and logic to create an optimal learning environment.
3. We will navigate through the iterative lifecycle—updating features, fixing errors, and refining logic—without
   writing any code but natural language. By relying purely on natural language, we will observe how LLMs, RAG, and
   agentic systems work in practice to significantly boost your productivity.

Before you begin, start a new GitHub Copilot Chat window for each request group:

1. Create the anatomy of a good prompt.
2. Build a Socratic Prompt Tutor agent.
3. Test the Socratic Prompt Tutor agent.
4. Develop a web app.

## Anatomy of a good prompt

To get started, we will need to set up some files. Let's get started by creating documentation. We will be using
Markdown format, as it is an easy-to-understand document format. Since we know that a good prompt must contain the
roles, tasks, context, and specific format, we will write it in this form.

> Create a `.md` tutorial worksheet for "the anatomy of a good prompt" (for example: role, task, context, and format), with fill-in sections for each step. Include examples.

Although the AI generated the content from our descriptions, we didn't like the examples because they are disjointed. Providing one example may not be enough. In this case, we want to create a working example for a business professional, a math teacher, and a vlogger. In addition, we would like to combine all these examples into a final step. So, here's a likely prompt.

> Each example provided is disjointed from the others. I want three different examples for each item (business professional, math teacher, and vlogger). The examples should all be connected. Modify the examples in this file so we have three examples for each step, and ensure each category is connected. In the final step, provide the combined prompt for each of the three examples.

To make the document more visual, we want to add graphics. Because GitHub Copilot generates text only, we can't embed raster images (JPEG, PNG). Instead, use Scalable Vector Graphics (SVG), a text-based XML format. We can add a small SVG icon for each step. For example, use this prompt:

> Include SVG graphics in the generated Markdown file. Create square SVG icons as separate files, one for each step heading, to illustrate that step. Embed each SVG beside its heading, scaled to match the heading's font size.

Further adjustments can be made. For example, if we do not like the colors, we can tell it to change the colors and the shape.

> Use a monochrome sky-blue color with rounded corners for all the SVGs generated.

We can also adjust each icon by telling it so. For example:

> For the role SVG, modify it to have a person bust (woman) inside a cogwheel.

We can also move all the images to a different location in the workspace. This also relocates the image hyperlinks within Markdown to the new location. For example,

> Move all the SVG images generated earlier to a new location at /assets. Also, relocate all references.

## Socratic Prompt Tutoring Agent

We will now create the Socratic Prompt Tutoring Agent. In VS Code's Chat panel, click "Create custom agent" (agent icon), add a new agent to the workspace, and name it "Socratic Prompt Tutor." Create a new GitHub Copilot Chat window. Then, locate the newly created agent file, move the cursor to the end of that file, and paste the prompt below into the chat box to update the agent.

> Modify only the body content in the VS Code GitHub Copilot agent Markdown so it implements a comprehensive Socratic Prompt Tutor and strictly conforms to agent Markdown policies. Treat every user input as a draft prompt to be evaluated (rather than executed). Provide concise, actionable feedback to actively teach users how to write highly effective prompts. The final output must be a single, perfectly valid agent Markdown file with the original front matter intact and no duplicated content.

Then, we may also want to update the `name`, `description`, and `argument-hint` in the heading. In addition, we may need to restrict this agent's `tools` access.

> Update the agent meta heading data's `name` to `Socratic Prompt Tutor`, set the `description` to explain that the agent helps users learn to write effective prompts through Socratic guidance, and set the `argument-hint` to indicate what to enter (for example, a prompt excerpt or the full prompt for validation). Enable only the necessary `tools` for this agent.

Let's test this agent. Create a new GitHub Copilot chat window. Select the `Socratic Prompt Tutor`. Then, type a simple prompt to see the results. For example, `Write a story.` The resulting response appears as a single block of text and is difficult to read, so we want the agent to break the feedback into clear steps. To improve this, we need logical verification of the prompt against the document we generated. So, we will attach that document in the chat box by dragging the generated "Anatomy of a good prompt" file into the chat window, and then improve the agent context.

> Using the attached document on all the necessary steps of the prompt, modify the current agent so that it will now verify prompts against the required steps. So, when a step is vague or missing, highlight the exact unclear text, identify the affected step, briefly describe what is missing, and provide a concrete example.

To make the agent more interactive, we can turn it into a wizard. We have a few options: the user can ask the agent for explanations, more examples, or hints on what to fix in the prompt excerpt. Additionally, the user can ask questions, share comments, or provide their own prompt fixes based on the provided context.

> Modify the agent context to behave like a wizard. It should output only the lowest invalid step at a time. For example, if steps 1 and 2 pass, it should provide concise comments for step 3. Then, it should present a combined prompt with the revised prompt emphasized, followed by a menu of choices: the user can ask for further explanations, clarifications, hints on what to fix, and examples relevant to the prompt. Additionally, the user can provide open-ended input, such as asking questions, sharing comments, and submitting prompt changes. The agent should also address all user concerns. If the user provides a message related to the input prompt, the agent should detect whether the message is a complete prompt or a prompt excerpt. If it is a complete prompt, the agent should reanalyze from step 1. If it is a prompt excerpt, the agent should analyze and validate based on the current step. If it passes, it should proceed to the next step.

Overall, it looks great, but the text still feels too plain. We want the AI-generated response to be more richly formatted, so we can add the following prompt to modify it.

> Modify this agent context to format the AI response using Markdown. Use a heading for each step. Enclose each example in an indented block quote (>) that follows a short heading that briefly describes the example. Emphasize all important questions you pose, and wrap placeholders in inline code like `{{placeholder}}`. Keep responses concise and compact. Include emojis to make certain parts of the response stand out.

It's possible that the original combined prompt gets lost, which can happen. If not, we can skip this step. For example, we can add:

> Modify this agent context to ensure the combined prompt is never lost and always remains in context. The combined prompt must merge the user's original input with all accepted fixes. Add a menu option that lets the user view the current stored combined prompt at any time. After any user edit or fix, update and display the combined prompt automatically. The user can also request revisions to the combined prompt.

Great, once everything is validated and successful, we can likely execute this prompt. However, we can go one step further and generate the file content into a specific folder.

> Modify this agent context so that when all steps are successful and finalized, it prompts the user to execute the final combined prompt. Ensure the agent context has file edit tools enabled. If the user chooses `run`, the agent should run the prompt and save a file under the `/results` path with a filename based on a brief 3–5 word title summary of the combined prompt. If the `/results` folder does not exist, create it before saving the file. If the file format is not specified in the prompt, use rich Markdown format (`.md`); otherwise, use the specified file extension. The user can also choose to revise by adding more prompt excerpts to the final prompt. In that case, the agent should reanalyze the combined prompt with that excerpt from the first step. The user can also request to revisit specific steps, which should present an appropriate menu of step choices.

Sometimes, when we're out of ideas, we can ask the AI to help create a topic for us to practice writing prompts. We can set this up so the AI creates a topic and the user writes a prompt based on that topic.

> Modify this agent context to allow the user to practice writing prompts. In this case, the AI must generate a short topic sentence, and the user must write a prompt based on that topic. The agent must validate the input prompt and confirm it is directly related to the topic. If the prompt is off-topic, the agent must warn the user and require a revision before continuing. If the prompt is on topic, the agent must run it against all steps. The agent must also maintain and update the overall score each time the prompt goes through each step.

If the game doesn't work, we should explicitly force the AI to fix the agent context automatically so it works correctly.

> Simulate the agent in practice mode with an off-topic prompt. If it still validates steps without warning the user, you must fix the agent context so off-topic prompts are blocked, a warning is always shown, and step validation is not allowed until the prompt is corrected.

## Web Application

Let's create a no-code website. The idea is to create a website that shows the document ("The Anatomy of a Good Prompt") we generated earlier. Once the user finishes reading the document, the user can proceed to the next page, where they will answer a few multiple-choice questions that assess their understanding of what they read. Here, we will demonstrate the following:

1. As long as we know exactly what to do, we can create an app without touching any code. However, we will still see a lot of code, and with some experience, we can let the AI read the code and fix it by itself.
2. Store the MCQ data in JSON format.
3. Write the data to CSV format in the app.
4. Generate HTML/CSS webpages easily.
5. We need to specify the web framework. A popular one used by many AI platforms is React.js, so that's what we're going to tell the AI to use.
6. Without being a designer, we can also ask the AI to change the web designs by typing in words.
7. We can let the AI fix this code automatically by having it test the code over and over again. This demonstrates iterative refinement.
8. How can we harden our web app by adding automated tests?

We will begin by converting our Markdown document into a webpage. We also need to specify the technology we are using and briefly describe the app's functionality. Note that if we do not explicitly provide a filename, the AI will automatically assign a meaningful name to each file.

> Use Node.js and React.js to build a website. The website should display all information from the "The Anatomy of a Good Prompt" Markdown document. At the bottom, there should be an input field for the user to enter their name. Next to the input field, there should be a "Check my understanding" button. When the user clicks the button, it should take the user to a set of 10 multiple-choice questions related to the document. When the user submits, it should show the next screen with the score, the incorrect questions and answers, and explanations for why they were incorrect.

We may need to apply a few fixes, depending on how your model generates the code. For example,

> Make sure the Markdown content is converted to HTML correctly. Make sure the icon images are included correctly. Make sure the blank underline placeholders are displayed correctly.

We can continue refining this web app. But let's move to the final step, where we want to store the data and show interactive statistics without writing a single line of code.

Let's save all user results to a CSV file. Let's also build a dashboard to review and navigate the results.

> After the user completes the quiz, save the user's results to a CSV file. Each row represents one user. Add the following fields to the CSV: name, completion date/time, score, total, answer choice for each question, and score for each question. Each question is worth 1 point. Also, create an interactive dashboard webpage showing quiz statistics (such as score metrics: min, max, mean, and median; per-question statistics; student scores; and a score distribution graph).

We may need to know some technical terms when fixing issues, but we are still far from writing code directly. In one of my tests, the agent said that the API server and web server were created separately, which may cause issues. So, I can either modify the original prompt to ensure the API and web server are combined (same endpoint), or I can have the agent modify it.

> Modify the code so the API and web app use the same web server endpoint.

So far, it's working, but we want to test our dashboard with a lot of data. One option is to enter the data manually, or we can ask the agent to generate the data for us. It will create a node.js script to generate the data.

> I would like to test the dashboard with a lot of data. Please populate 100 user records in the results CSV with distinct male and female first names. Scores should average around 7/10 points. Please provide a dataset that lets me see different effects in the dashboard (average, outliers, and extremes).

To retrieve the URL, you can ask:

> What are the URLs for the document and dashboard?

If a URL is not working, tell the agent to fix it.

> The URL "..." isn't working. Please fix it. `{Paste the error message}`
