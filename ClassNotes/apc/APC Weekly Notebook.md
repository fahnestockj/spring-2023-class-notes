# Week 1 Project Notebook
Jacob Fahnestock 
5/25/22 
Professor Rawlins 

The Antikythera group met this week to discuss languages after completing assignment 1. The group decided Python fit the domain best as it is the primary language for data science. While the syntax for OOP patterns is unfamiliar for most of the group the benefits of accessible tooling and examples outweighed the downsides. Personally I'm pushing for the group to adopt Jupyter Notebooks as well to speed up development and documentation however most of the group members are unfamiliar with the tool. I set up a [Github repository](https://github.com/fahnestockj/ELEC3225AntikytheraProject) and found a [related blog post](https://medium.com/analytics-vidhya/simulating-the-solar-system-with-under-100-lines-of-python-code-5c53b3039fc6) working with some potential package options. I got an Anaconda virtual environment up and installed the related packages to test them out. Lastly I added some instructions to the repository's README on how to install Conda, set up a venv, and run the copied code. 


# Week 2 Project Notebook
Jacob Fahnestock 
6/1/22 
Professor Rawlins 

The group met this week to build some of our process model. We built a plan for the current Agile sprint. We're going to split into two teams to work on the database and base classes separately. I worked to make the repository's virtual environment accessible to windows and mac. This required making a custom `environment.yml` file to define the packages needed to create the environment. These packages unfortunately can't specify versions because some of the packages are on different versions on either platform. More configuration is required on windows to activate and manage the Anaconda virtual environment. I added instructions to edit the permissions on running scripts in a powershell terminal in order to run `conda init powershell` which sets up a terminal profile in a script that runs on startup. The instructions were confirmed and followed by another group member who got the project up and running on windows.

# Week 3 Project Notebook
Jacob Fahnestock
6/8/22
Professor Rawlins

The group put together a rough plan for the upcoming sprint on the figma board. 
![[Pasted image 20220608193401.png]]
We've split into two groups, one working on the database one working on the UI. Both groups will need to work together to agree on the format/schema of an event as it will inform what inputs get put in the system to see an output. I've been testing out the [astropy package](https://www.astropy.org/) along with [JPL's horizons System](https://ssd.jpl.nasa.gov/horizons/). Both are options for potential data sources or API integrations. Horizons can provide vectors for planets at a given time which could be used as an API integration to create our model/animation.


# Week 4 Project Notebook
Jacob Fahnestock
6/15/22
Professor Rawlins

I worked this week learning more about [JPL's horizons API](https://ssd.jpl.nasa.gov/horizons/). Using Nasa's planet IDs the location of planets and bodies in space can be fetched. Their location is in AUs which comes out 1.495978707×10^11 meters and comes with XYZ coordinates. Along with these locations the XYZ velocity vectors are also available. This informs how the system should function where initially a time is set (by the UI) and the locations and velocitys of the planets are fetched. Once these are fetched a play button can be hit triggering time to pass and the locations of the planets to change. This change in locations will need to be calculated using an acceleration equation. This acceleration equation to **start** will only be based on the sun's gravitational pull (since the sun is the strongest gravitational force in our solar system.) This equation is still being figured out as the original is coming from the [related blog post](https://medium.com/analytics-vidhya/simulating-the-solar-system-with-under-100-lines-of-python-code-5c53b3039fc6) mentioned in previous weeks. Here's some thoughts about that equation:
![[Pasted image 20220615111052.png]]
This equation highlights why the group picked Python since the vectors/points are so easy to work with especially with [NumPy](https://numpy.org/).


# Week 5 Project Notebook
Jacob Fahnestock
6/22/22
Professor Rawlins

This week was spent ironing out the acceleration equation and testing some UI views. The acceleration equation is the backbone of the simulation as it enables the system to simulate motion over time when given position and velocity initial conditions. Here's some of the steps for it's derivation:


This equation is derived from Newtons law of gravity and Newtons second law of motion.

Starting with Newtons law of gravity:

### g = G * M / r^2

Now the force equation 
### f = ma

By solving for acceleration we get 
### a = f/m

Now plug in the gravity equation for the force
### a = GM/r^2

Now we need to account that this acceleration is applied as a vector. 
For this we need the unit vector of the position

### unit vector = r / |r| 

Tack this onto the acceleration equation and we get

# a = GM/r^2 * r / |r|
Where 
* G is the gravitational Constant
* M is the mass of the sun
* r is the distance between the sun and planet (as a vector)

The UI is the next concern as fitting the full solar system on the screen at once makes it hard to follow any of the information displayed. Following a planet closer will be a challenge for Matplotlib, and will be a focus of the coming week.


# Week 6 Project Notebook
Jacob Fahnestock
6/29/22
Professor Rawlins

Most of this week was spent on improving the UI. The relative size of planets depending on the zoom problem was fixed with some point scaling changes. With this fixed more meaningful decisions about the UI can be made such as how many zoom options should we have? or should we be able to track a planet? A pause and resume button were added to pause and resume the simulation. These buttons are [MatplotLib widgets](https://matplotlib.org/stable/api/widgets_api.html) which offer a wide variety of UI options we could implement. Here's the current layout of the simulation:

![[Pasted image 20220629220044.png]]

Clearly the zoom is still a problem as not all the planet labels are visible. Work was done with the database team to demonstrate the Horizon's API and how to fetch relevant data like position and velocity. Also testing was planned to test the accuracy of the simulation against Horizon's datapoints.


# Week 7 Project Notebook
Jacob Fahnestock
7/13/22
Professor Rawlins

This week was spent on planning the upcoming database integrations, laying out what needs to be tested, and the final UI designs.  For UI some a new landing page/menu is in the works to allow users to select a time or celestial event they want to start the simulation from. For testing the team decided each database can be tested individually then the main equations like acceleration should be tested as well. These tests will act as documentation as well. The planned database integrations include a getPlanetInfo function which will fetch the stored info and position of the requested planet. Currently this should just accept a planet id and date. With these backend functions the database integrations can be worked on by the groups who wrote the database code directly speeding up development. 


# Week 8 Project Notebook
Jacob Fahnestock
7/20/22
Professor Rawlins

This week was mostly spent on UI specifically tables. The UI needs more information on the position of the planets as the simulation runs. I explored several options for potential tables starting with [Matplotlib widgets](https://matplotlib.org/stable/api/table_api.html?highlight=table#module-matplotlib.table). After a lot of hassle this table was hard to render and difficult to update after rendering. This is the most important feature for our team in a table is an easy way to update the table as the simulation runs. The first thing the documentation recomends is to use a different package called [Blume](https://github.com/swfiua/blume). Unfortunetly I trusted the documentation and gave Blume a shot without noticing the repository was barely used and had many of the same problems the original matplotlib table had. Finally I tried [Plotly](https://plotly.com/python/) which was a much more intuitive package with good documentation, but no way to integrate into the matplotlib frame where the simulation runs. Instead finally I gave up and decided to use the same text rendering I was using for planet names on the planet information. Here's the barebones table without much formatting:
![[Pasted image 20220720225736.png]]
After formatting this a bit better I'm convinced we likely won't need a full table package for the simulation.