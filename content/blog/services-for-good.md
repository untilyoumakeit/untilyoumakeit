+++
title = "Services for good"
date = 2020-10-10
[taxonomies]
categories = ["swift", "development"]
tags = []
+++		

# Services for good

There are many talks about UI in mobile apps. 
In the last few years, declarative approaches almost beat any other and becoming the major.
But what about services? 
Can an imperative approach work fine with declarative UI?

# Problem standing

There is a common pattern to split the representation of data in several views.
This could be several views on one controller or different controllers.
This creates several consumers for one logical piece that can request independently.
By moving these requests into separate service we can create an entity that will load requested data and return models.
But how to avoid duplicated requests and have a correct UI representation of the data layer?

The traditional solution is creating a callback method that will return a parsed model.
And some property to check a loading state of the service (eg `isLoading` field).
Then inside each service, we need to add additional checks and assignments for this field and move all logic related with coalition requests to the consumers.
This makes UI and service code more complicated as it would be.

# Possible solution

Can move all this complexity into a reusable entity and have a much simpler interface?
The first obvious thing that we can do is move from simple callbacks to more flexible abstraction.
Let's make Combine works for us.
Our method to load data will return a Publisher.
This is a much more powerful thing as now we can do a transformation, cancellation and many other things.

# Usage examples 
