# charge-planner
An AI driven electric car charging optimizer for home assistant packaged in a docker file.

The program uses an AI model to predict solar power production based on weather forecasts, the suns altitude/azimuth, etc.
The program then combines the predicted production with tomorrows electricity rates, current car battery level, etc to 
automatically charge the car on a optimized schedule based on price to charge through home assistant.
The program communicates with home assistant through RESTfulAPI calls on port 5000.
The AI model was developed in Python using PyTorch and trained on 20k example hours.
The docker image is on docker hub under the repo name: antonzachrisson/charge_planner.

Approach 1:
Create a docker-compose.yml file and copy the following code (change mapping paths):

version: "3"

services:
  app:
    image: antonzachrisson/charge_planner:latest
    restart: always
    volumes:
      - /path/to/config_dir:/home/data
    network_mode: host

Approach 2:
Run docker image from the terminal: $ docker run --name charge_planner -d antonzachrisson/charge_planner
and map the config directory to the container.

Config:

Put config.txt in the mapped config directory, "bilEffekt" is the chargers maximum output in kW, "battCap" is the car battery capacity in kWh.

Home Assistant Integration:

GUIDE COMING SOON...

