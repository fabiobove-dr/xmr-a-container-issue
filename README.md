# A Container Issue - Hidden XMR Mining Process Case
A repo that shows you why you should always look what's inside a Dockerfile, and never trust a docker-compose file or take for granted that any env variables actually works.
<br>
# The Issue
Recently i got into Blockchain Development, it's an intresting topic, and to better understand how the concept of Prof of Work works i got over XMR, which is a crypto that can be mined with just a CPU.
<br>
As i was looking for a controlled and manageble way to do XMR mining, just to study, i found that many solutions proposed used docker containers that could run whith only a 10% performance loss. Nice you'd say, the developers of those solutions are so genereous that they give you the perfect tool to mine, and it takes zero effort, but here come the problems:
1. Many give you only the docker-compose file, you actually don't know what you're pulling and then running
2. You see env variables, to set up your wallet_address for example, but they don't work - you're mining but donating 100% to them.
<br>
# Conclusion, a note to self
The simplicity of how a mining process, or other more malicious subprocesses, can be hidden into every single docker-image that you deploy, needs to be considered when copying or exending existing docker-images.
<br>
1. Don't trust docker-compose files that are ready to use - as above - you actually don't know what you're pulling and then running.
2. Look into Dockerfiles, it's better what's been added - know every line
3. Fake environment variables can be misleading, you thing you've changed the configurations of the soulution you've adapted but you have no control.
<br>
# What this Repo is about
I've tryied to replicate here what can be an example of an application with an hidden subrocess that runs a xmr-miner.
It's to demonstration and study purpose only, so you can get an idea of what i was talking about and save yourself some troubles.


Cheers.



