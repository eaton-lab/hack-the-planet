---
image: /assets/images/hackers-panel.png
title: "project-planning-1"
layout: default
---

<style>
h3 {
    margin-top: 30px
}
pre {
    line-height: 1.5em;
}
pre code {
    font-size: 0.9em;
}
</style>



## Project proposal planning I

Planning a project can be difficult, especially as a beginning developer when
you have only been exposed to a small range of scientific programs, and 
have not yet learned about all of the possibilities made available 
through existing packages and libraries. Our goal in this tutorial is to 
begin exploring this world of possibilities. We will do this in several ways, 
first by looking at the documentation of several relatively simple Python
packages, then by looking at their GitHub repos, and finally by breaking
down the steps involved with developing large packages, and thinking of 
how to build upon existing tools rather than start from scratch. This process
of planning and exploring will stretch over the next several class sessions.

Most of the example programs we have developed thus far, such as the 
darwinday package, have been fairly silly. How can we come up with 
better ideas for a useful package? 

One way is to focus your ideas around a particular type of `data`. Let's 
consider for example that we wanted to develop a program for analyzing 
weather data. We need to consider: Where will the data come from? 
What type of format will it be in? What are we going to do with the data? 
How will users interact with my program?
Remember, not every program must focus on <i>analysis</i>, many
useful programs can act simply as aggregators of data, or for 
visualization. 

So what might be a useful weather analysis program? Well, we obviously know
that there are tons of resources already for checking the current weather,
so maybe instead we will focus on historical weather data. In our next class
session we will learn about `REST API` frameworks as a resource for accessing
publicly available data online. A quick google search for "weather rest API" 
shows me several results. Great, so I have a type of data in mind. Let's 
now walk through our planning questions one at a time.

### Where will the data come from?
Historical weather data will be accessed from a weather API (online).

### What format will the data be?
It will depend on which API I end up choosing. From looking at the documentation
of one example I see that it will likely be JSON format, something like the 
following:

```console
{
    "request": {
        "type": "City",
        "query": "New York, United States of America",
        "language": "en",
        "unit": "m"
    },
    "location": {
        "name": "New York",
        "country": "United States of America",
        "region": "New York",
        "lat": "40.714",
        "lon": "-74.006",
        "timezone_id": "America/New_York",
        "localtime": "2019-09-07 10:05",
        "localtime_epoch": 1567850700,
        "utc_offset": "-4.0"
    },
    "current": {
        "observation_time": "02:05 PM",
        "temperature": 15,
        "weather_code": 113,
        "weather_icons": [
            "https://assets.weatherstack.com/images/wsymbols01_png_64/wsymbol_0001_sunny.png"
        ],
        "weather_descriptions": [
            "Sunny"
        ],
        "wind_speed": 0,
        "wind_degree": 0,
        "wind_dir": "N",
        "pressure": 1011,
        "precip": 0,
        "humidity": 78,
        "cloudcover": 0,
        "feelslike": 15,
        "uv_index": 5,
        "visibility": 16
    },
    "historical": {
        "2008-07-01": {
            "date": "2008-07-01",
            "date_epoch": 1214870400,
            "astro": {
                "sunrise": "05:29 AM",
                "sunset": "08:31 PM",
                "moonrise": "03:24 AM",
                "moonset": "07:37 PM",
                "moon_phase": "Waning Crescent",
                "moon_illumination": 4
            },
            "mintemp": 0,
            "maxtemp": 0,
            "avgtemp": 19,
            "totalsnow": 0,
            "sunhour": 14.5,
            "uv_index": 4,
            "hourly": [
                {
                    "time": "0",
                    "temperature": 27,
                    "wind_speed": 7,
                    "wind_degree": 201,
                    "wind_dir": "SSW",
                    "weather_code": 113,
                    "weather_icons": [
                        "https://assets.weatherstack.com/images/wsymbols01_png_64/wsymbol_0001_sunny.png"
                    ],
                    "weather_descriptions": [
                        "Sunny"
                    ],
                    "precip": 1.8,
                    "humidity": 80,
                    "visibility": 9,
                    "pressure": 1011,
                    "cloudcover": 15,
                    "heatindex": 25,
                    "dewpoint": 20,
                    "windchill": 24,
                    "windgust": 11,
                    "feelslike": 25,
                    "chanceofrain": 0,
                    "chanceofremdry": 0,
                    "chanceofwindy": 0,
                    "chanceofovercast": 0,
                    "chanceofsunshine": 0,
                    "chanceoffrost": 0,
                    "chanceofhightemp": 0,
                    "chanceoffog": 0,
                    "chanceofsnow": 0,
                    "chanceofthunder": 0,
                    "uv_index": 6
                },
                {   "time": "300", ...   },
                {   "time": "600", ...   },
                // 6 more items
            ]
        }
    }
}
```

### What am I going to do with the data?
That depends. First I'll take some time and examine the data above. What
type of information is available? It looks like there is numeric values 
for many measured weather variables, so I could imagine creating a plot
of hourly, daily, or weekly means. This could be done with pandas and 
matplotlib. I also see that there are location options, which list
latitude and longitude coordinates, so I might consider showing results
for different regions -- maybe this is an option the user could toggle. 
Or maybe I could plot values on a map. There are many possibilities.


### How will users interact with my program?
We have several options here. You could create a Python package that acts
as a dedicated wrapper for accessing this specific database. Your tool could
become *the* default way that people access weather data in Python, and 
thus your package may be incorporated into many other peoples programs in 
the future as a dependency. Or, maybe you will develop the program as a 
command line tool, something that can be called from a terminal to quickly
access some interesting historical weather information. Or, you could 
develop a webapp (something we'll learn more about in the future). Your 
program can be run on a server and accessed through a website where users
enter their arguments and information such as plots are displayed as a 
response. The latter is similar to what you would find on many professional
weather websites, which access public weather data in this same way by using
public APIs. 


### Expanding on this example
Not every dataset of interest will be available through a REST API. So what
should you do? There are several options. 

If the dataset is small then you could include it directly in your package. 
But generally this is not a good practice. Instead you might want to consider
writing your program so that it is more general, and can analyze any dataset
provided by a user as long as it meets a certain formatting (e.g., CSV file
with column labeled samples and another labeled values, etc.). 

If the input data to your program is likely to be different for every user,
since they generate the data themselves (e.g., trait data measured on 
organisms, or genomic data from individuals), then you will want to find
an example dataset that you can use while designing and testing your software.
And you will want to write a method for reading and parsing the user input
data, and checking that it is appropriately formatted.

If the dataset is very large, like the example here, where we used 
programmatic access to download only a subset of the giant historical 
weather data using a REST API, then you might consider creating the REST API
yourself if it does not yet exist, and then writing a package to access 
it programmatically.

Finally, your program may not use any real empirical data at all. This
tutorial introduces the idea that you *can* plan your project around a 
specific type of data, but that is not the *only* way to develop programs.
For example, you might develop something like a game, which would take 
interactive user input, but not data in the strict sense.


### Conclusions
Coming up with an interesting and useful project idea can be challenging. 
One way to jumpstart your ideas is to begin exploring *data* as a motivating
subject to center your plans around (though this is not the only way). 
Explore some the links below to learn more about large online 
public data sets. We'll learn more about REST API type datasets in the 
next session.


- https://www.dataquest.io/blog/free-datasets-for-projects/
- https://www.data.gov/
- https://github.com/awesomedata/awesome-public-datasets



