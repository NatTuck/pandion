---
layout: post
title:  "RStudio on Debian Buster"
---

Rstudio hasn't been built property for Debian 10 (buster), so here's some hacks
to get it to work.

# Problem 1: Get the RStudio Package

Grab the Debian 9 installer from here:
<https://www.rstudio.com/products/rstudio/download>

Install it with

```
sudo dpkg -i <package>
```

# Problem 2: Missing libssl

Grab the old libssl package from Debian Stretch

(This is bad form and could potentially lead to security issues in the future,
but is probably OK in practice in this case.)

Download the AMD64 package, and install with dpkg.

Package is at <https://packages.debian.org/stretch/amd64/libssl1.0.2/download>


# Problem 3: Might as well install the external R repo

(Reference: <https://cran.r-project.org/bin/linux/debian/#debian-buster-testing>)

```
sudo apt-key adv --keyserver keys.gnupg.net --recv-key 'E19F5F87128899B192B1A2C2AD5F960A256A04AF'
sudo nano /etc/apt/sources.list
```

Add this line to the bottom:

```
deb http://mirror.las.iastate.edu/CRAN/bin/linux/debian buster-cran35/
```

# Fix deps and Install R

```
sudo apt-get -f install
sudo apt update
sudo apt install r-recommended
```

Now Rstudio works?

```
rstudio
```


