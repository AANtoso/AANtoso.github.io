---
layout: post
title:      "The Easy Access to a Medication Tracker"
date:       2019-10-14 23:31:59 +0000
permalink:  the_easy_access_to_a_medication_tracker
---


Keeping track of medications is a huge problem that many clients have these days. Especially when multiple medications for multiple disease processes are assigned to one client to take.  The more medications there are, the more confusing it can get. They may need to be taken more than once a day and at different times during the day. making an application that can help clients keep track of their medications is what I decided to accomplish.

One thing I always have to remember throughout these projects is that a strong foundation/skeleton to a project always helps. One thing that still confuses me is the process of migrating and rolling back in order to fix tables. 

One specific issue I ran into was needing to rename a column in a migration that was already created. The reason why I had to do this is because there are preset. This can cause errors when you are trying to input data.

This is what my code used to look like:

```
class CreateMedications < ActiveRecord::Migration
  def change
    create_table :medications do |t|
      t.string :medication_name
      t.string :class
      t.string :indication
      t.string :dose
      t.string :frequency
      t.integer :user_id
    end
  end
end
```

The difference is I had to rename class therapeutic_class.

In order to do so I had to create a new migration by running rake db:create_migration NAME=name_here. I named the migtation change_class_to_therapeutic_class. Then I entered the following code into the change method. 

```
class ChangeClassToTherapeuticClass < ActiveRecord::Migration
  def change
    rename_column :medications, :class, :therapeutic_class
  end
end
```

After entering this method, I ran rake db:migrate. My schema then changed.
This is what my code looks like in my schema. Class was changed to therapeutic_class.

```
create_table "medications", force: :cascade do |t|
    t.string  "medication_name"
    t.string  "therapeutic_class"
    t.string  "indication"
    t.string  "dose"
    t.string  "frequency"
    t.integer "user_id"
  end
```

