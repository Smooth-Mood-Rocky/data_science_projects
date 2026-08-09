# Step 1: Use the pre-configured publishing image (includes RStudio, tidyverse, and TeX Live)
FROM rocker/verse:4.6.1

# Step 2: Install basic system dependencies required by typical R packages
RUN apt-get update && apt-get install -y \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    && rm -rf /var/lib/apt/lists/*

# Step 3: Set working directory inside the container
WORKDIR /home/rstudio/my_project

# Step 4: Copy your local project files into the container
COPY . /home/rstudio/my_project

# Step 5: Install R package dependencies with the correct CRAN repository link
RUN R -e "install.packages('renv', repos='https://cloud.r-project.org/')"
RUN R -e "renv::restore()"
