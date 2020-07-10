+++
author = "Hocine BEKKOUCHE"
date = 2020-04-01
title = "SSH Passwordless Login"
series = "Operations"
thumbnail = "/images/01-ssh-passwordless.jpg"
thumbnail_bg_color = "#b39cd0"
dark_thumbnail = true
tags = ["ssh","devops","operations"]
+++
## Introduction
In this article, 
we will try to setup password-less login using ssh keys to connect to remote Linux servers 
without entering a password.

open your preferred terminal and follow the steps:
## Generate Authentication Keys on local machine
{{< highlight bash>}}
ssh-keygen -t rsa
{{< / highlight >}}
## Create .ssh Directory on remote machine
{{< highlight bash >}}
ssh <user>@<remote-ip-adress> mkdir -p .ssh
{{< / highlight >}}
## Upload Generated Public Keys to remote machine
{{< highlight bash >}}
cat .ssh/id_rsa.pub | ssh <user>@<remote-ip-adress> 'cat >> ~/.ssh/authorized_keys'
{{< / highlight >}}
## Login to remote machine
{{< highlight bash >}}
ssh <user>@<remote-ip-adress>
{{< / highlight >}}
