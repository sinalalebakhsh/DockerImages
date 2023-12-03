# In this directory
#  docker build -t react-app . 
FROM node:14.16.0-alpine3.13

# for run 
# docker run -it react-app
WORKDIR /app
COPY . .
# COPY source dest
# COPY package.json README.md /app/
# COPY package*.json README.md /app/
#             |_> this star is meaning every files include package(anyThing).json
#                e.g. package.sina.json
#                e.g. package.1993.json  etc
# COPY . README.md /app/
#      |_> copy get everything from current directory right we are.


# ADD http://.../file.json destitation
# ADD http://.../file.json .

# IF use below:
# ADD file.zip . 
# Result:
#       "ADD" uncompressd is in to here directory









