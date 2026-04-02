# Vibe AI init Prompt

When I start working with AI code assist on a new project or an existing project I like to set up a few gard rails.  Instructions for the ai to follow always. 

1. Workflow.  Instructs the ai on background info things i like it to follow how commit messages are writen, unit tests are required to run before commiting ..
2. Prompt.   THe prompt itself is the gard rails I hope. How i ensure that it does exactly what i want to do.  This prevents me having to ask everytime, and ensures that it always fucntions as i sexpect no matter what project.

You can just paste it in but what i like to do is 

[ProjectFolder]\.gemini\workflow.md
%USERPROFILE%\.gemini\gemini.md


Note if you ask gemini cli to save memory it stores it in  %USERPROFILE%\.gemini\gemini.md  so you may want to merge mine with yours rather then over writing it if you have alrady instructed gemini how to function. 

