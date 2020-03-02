---
layout: post
title:      "JavaScript & Rails Project"
date:       2020-03-02 04:01:04 +0000
permalink:  javascript_and_rails_project
---

​
Where to even start with writing about this project is mind boggling. For my JavaScripts & Rails project, I decided to create a medication portal. This medication portal links the patients to their medications. Many of my projects are related to medication tracking because it is a huge problem in the healthcare field.
​
As with many of my projects, I have run into errors including but not limited too:
-Typos
-Association miss-matches
-Singular and pleural switches
-Missing symbols
​
However, with this project, One of the most frustrating issues that I ran into was being able to create a medication.
Because the medications are linked to the patient, I needed a way to link the patients and the medications. I had tried several ways. After consulting with several other classmates, this is the way that ended up working for me.
Originally my migration for medications looked like this:
```
class CreateMedications < ActiveRecord::Migration[5.2]
  def change
    create_table :medications do |t|
      t.string :name 
      t.string :pharm_class
      t.string :indication
      t.string :dose
      t.string :frequency
      t.text :note
      t.timestamps
    end
  end
end
```
​
However, this was not allowing a medication to be connected to a patient. I rolled back my migrations and I changed my medications migration so that it looked like this:
```
class CreateMedications < ActiveRecord::Migration[5.2]
  def change
    create_table :medications do |t|
      t.integer :patient_id
      t.string :name 
      t.string :pharm_class
      t.string :indication
      t.string :dose
      t.string :frequency
      t.text :note
      t.timestamps
    end
  end
end
```
​
Here I included an integer for the patient id. This allowed medications to be created after a patient has already been created.
​
I feel like this process was a little bit different when doing the Ruby on Rails project. I don't remember having to add an id to the migration in order to connect the patient with the provider.
​
This project was by far the hardest one for me. JavaScript is not something I am well versed in at all. Always having a second set of eyes will get you through your project.

