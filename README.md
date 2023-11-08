# A Container Issue - Hidden XMR Mining Process Case

This repository demonstrates why you should always inspect the contents of a Dockerfile, and never assume that a docker-compose file or environment variables will function as expected.
The Issue

Recently, I delved into Blockchain Development, which is an intriguing subject. To gain a better understanding of how the Proof of Work concept operates, I explored XMR, a cryptocurrency that can be mined using just a CPU.

While seeking a controlled and manageable way to experiment with XMR mining, I discovered that many proposed solutions employed Docker containers, which incurred only a 10% performance loss. It might seem promising at first; these solutions provide an easy way to mine without much effort. However, some issues arise:

    Many of these solutions provide only the docker-compose file, leaving you uncertain about what you're downloading and executing.
    You encounter environment variables for setting up your wallet address, but they don't function properly. As a result, you end up mining but donating 100% of the earnings to someone else.

# Conclusion - A Note to Myself

The ease with which a mining process or even more malicious processes can be concealed within any Docker image you deploy should be taken into account when copying or extending existing Docker images. Here are some key takeaways:

    Do not blindly trust ready-to-use docker-compose files, as mentioned above; you may not know what you're pulling and running.
    Examine Dockerfiles carefully to understand what has been added - know every line.
    Beware of fake environment variables, which can mislead you into thinking you've modified the solution's configurations when you have no real control.

# What This Repository Is About

I've attempted to replicate here an example of an application with a hidden subprocess that runs an XMR miner.

The provided code is for demonstration and study purposes only, so you can grasp the concept I mentioned. Use it at your own risk, and be aware that running this image can consume a significant portion of your CPU resources.

AI fixed my poor english, cheers.
