---
layout: post
title:      "Rails Project (Medication Tracker)"
date:       2019-12-16 17:08:01 +0000
permalink:  rails_project_medication_tracker
---


This project was definitely the hardest one for me by far. I am still shaky and my overall understand of the material is still a work in progress. However, it will definitely improve overtime. There is a lot that is involved when building a Rails app. Although there were some similarities to Sinatra, there was definitely a lot more information to remember, more steps to take, and more pieces to link in order to have a fully functioning application.

For this I created a Medication Tracker. It is am application that allows patient to track their prescriptions as well as the providers who are prescribing them medications. This is important because it creates a simple way for a patient to manage their health and keep up to date prescription records.

In the beginning, I was going ot use 4 models. One for Patients (the users), Providers, Medications, and Prescriptions. I started my projects with all 4 of these models. However, after I built the models out, and started to decide how everything was going to relate to each other, it became a bit more complicated than I would have wanted it to be and the model relationships didn't turn out the way I wanted them to. So I removed the Medication model and everything fit together much better after this.

The most challenging part of this project for me was definitely implementing the scope method. Grasping this concept was definitely the most difficult for me. I knew that I wanted to put it in my Prescription model, but learning how to write the code and implementing it into my project was a struggle for me. There are three places where I had to add code in order to implement it:

My Prescription Model:
```
class Prescription < ApplicationRecord

    belongs_to :patient
    belongs_to :provider
    accepts_nested_attributes_for :provider
    
   ** scope :called_in, -> {where(called_in: true)}**
    
    def provider_attributes=(provider)
        self.provider = Provider.find_or_create_by(name: provider[:name])
        self.provider.update(provider)
    end
end
```

I then had to create a new views file under Prescriptions and name is called_in.html.erb because I wanted to display the medications that were called in to the patient. Here is the code for that:

```
<h2>Your Called-In Prescriptions:</h2>

    <% @prescriptions.each do |p|%>
    <li><%= link_to p.medication_id, prescription_path(p.id) %>
		</li>
    <% end %>
```

Then I had to add a method (displayed below) in my Prescriptions_Controller so that I could call it.

```
def called_in
        @prescriptions = Prescription.called_in
end
```

Lastly, I had to add a route in my routes.rb file under config so that the page can be accessed. Code:

```
get '/prescriptions/called_in', to: 'prescriptions#called_in'
```

I am going to work on styling and making the app more presentable before my review. But I am definitely proud that I was able to complete this project meeting project requirements and expectations. Now the challenge will be presenting and fully grasping the knowledge and concepts (which will come over time). 
This course is definitely a learning experience and I wouldn't be able to do it without the help of wonderful peers and instructors.
Looking forward to my future coding endeavors!

