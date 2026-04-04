# Vibe AI init Prompt

When I start working with AI code assist on a new project or an existing project I like to set up a few gard rails.  Instructions for the ai to follow always. 

1. Workflow.md  -  Instructs the ai on background info things i like it to follow how commit messages are writen, unit tests are required to run before commiting ..
2. gemini.md - This is the file that gemini cli uses for its internal memory. When you tell it to [save memory](https://geminicli.com/docs/tools/memory/) this is where the data goes.  The prompt itself is the gard rails I hope. How I ensure that it does exactly what I want to do.  This makes it so I dont have to ask everytime, and ensures that it always fucntions as I sexpect no matter what project.
3. change_complete.md - This file has a prompt that I use when the AI says its done and Im not sure it is.  It forces it to review its changes and verfy that everthing is as I expect it to be.
4. handoff.md - This is where I have it stor information about what it did in this session so that it has a place to start the next session. IMO this is just a way to give the AI a lot of context in the project so that it wont have to do a full scan everytime we start. 

You can just paste it in but what i like to do is 

[ProjectFolder]\.gemini\workflow.md
%USERPROFILE%\.gemini\gemini.md

Note if you ask gemini cli to [save memory](https://geminicli.com/docs/tools/memory/) it stores it in  %USERPROFILE%\.gemini\gemini.md  so you may want to merge mine with yours rather then over writing what ever you currently have there. 


Example of saving memory:
```
Can you save to your memory you will always use Conventional Commits and prefix all commits with [AI]
```
