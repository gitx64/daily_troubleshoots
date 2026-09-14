## Important tip for docker compose healthchecks

-> If using CMD-SHELL then it always expects single string command as the second parameter, If you used seperate strings then it will just execute the first part of the command in a single shell so it will always show unhealthy or continuously restart.
