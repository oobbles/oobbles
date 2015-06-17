---
layout: post
title:  "Dinner Club"
date:   2015-06-17 09:10:43
categories: code
---
*What was the assignment?*
Add a DinnerClub class. Each DinnerClub object represents a group of friends who go out to eat together frequently.

Dinner clubs should be able to list each member's name along with how much that person has paid during their history of membership in the club. You will use the CheckSplitter class to calculate how much each member owes for each dinner club event. Not every member goes to each event, so sometimes the check splitter is splitting a check between 4 people and sometimes it's 3 or 7 or 10 or you get the picture.

*In just a few sentences, how does your program accomplish the assignment's requirements?*
My program takes a total bill, tip, location and any number of attendees and then tracks the amount each person has spent as well as the events they have attended.

What are the attributes and behaviors of each class's objects?
What kind of data is stored in each class?
What are the parameters for methods?

I have two classes: `DinnerClub` and `CheckSplitter`.  `CheckSplitter` is a helper class that handles converting the tip and dividing up the total cost.

`DinnerClub` is the main class.  When instantiated it creates an array called outings.

This array will hold a list of hashes with hashes inside.  The main method is `update_total`.  This method takes the arguments of total bill, the tip, where the group ate at and who attended.  It then counts the number of attendees, passes that count to a new instance of `CheckSplitter` along with the total bill and the optional tip.

`CheckSplitter` divides that amount to be used later on in the method. (n.b. Everyone gets an even split at this time, there are no other options).

Next the method sets the event hash with `:location` taking the location and `:attendees` set to an empty hash that I fill by iterating through the attendees and attaching the amount value.  After the iteration, the completed hash is pushed to outings.
```ruby
  def update\ _total(total_bill, tip, location, *attendees )
    number_of_payees=attendees.length
    amount =CheckSplitter.new(total_bill, number_of_payees, tip).split

    event1={:location => location, :attendees => {}}
    attendees.each do |name|
      event1[:attendees][name] = amount
    end

    @outings.push(event1)
  end 
```
The second main method of `DinnerClub` is `get_balance`.  We give this method the name of a Dinner Club member as the argument.  Next is initializing the total variable to 0.  Now we take the outings array and loop through it to go though each event hash.  As we do that we use the `:attendees` key to unlock the value of the individual user's 'tab'.  We set that to a float, assign it to amount then add that to total.  When that is all done, it returns the total total to us. :)

Finally we get to use `app.rb` which is how we interact with the other classes.  We can make a new instance of `DinnerClub`, add events to the outing array, inspect in and also just get the balance for one member.

```ruby
require "./dinnerclub.rb"
foodie_group = DinnerClub.new

foodie\_group.update_total(55, 5, "Pizza Hut", "Lisa", "Vis")
foodie\_group.update_total(60, 5, "Arbys", "Mark", "Vis")
foodie\_group.update_total(76, 0.25, "LaMesa", "Vis", "Mira", "Lisa")

puts foodie_group.outings.inspect

puts "Here is the balance for the member Vis: $#{foodie\_group.get_balance('Vis')}"
````