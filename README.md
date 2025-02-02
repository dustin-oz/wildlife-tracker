# Wildlife Tracker
LEARN Academy challenge - 04.29.2022

### Student:
Dustin S

# The Story:
The Forest Service is considering a proposal to place in conservancy a forest of virgin Douglas fir just outside of Portland, Oregon. Before they give the go-ahead, they need to do an environmental impact study. They've asked you to build an API the rangers can use to report wildlife sightings.

#### Created my rails app
```
$ rails new wildlife_tracker -d postgresql -T
$ cd wildlife_tracker
$ rails db:create
$ bundle add rspec-rails
$ rails generate rspec:install
$ rails server
```
#### Postman
- Open Postman

#### Story: As a developer I can create an animal model in the database. An animal has the following information: common name, latin name, kingdom (mammal, insect, etc.).

- Terminal `$ rails generate resource Animal common_name:string latin_name:string kingdom:string`
- Remove the views: `$ rm -rf app/views/animals`
- Remove the stylesheet: `$ rm app/assets/stylesheets/animals.scss`
- `rails db:migrate`
- `rails c`

#### Story: As the consumer of the API I can see all the animals in the database.
- Added index method to controller
- Verified in postman

- Add some animals to the database:
  - `Animal.create common_name: 'Bald Eagle', latin_name: 'Haliaeetus leucocephalus', kingdom: 'bird'`
  - `Animal.create common_name: 'Common Yellowthroat', latin_name: 'Geothlypis trichas', kingdom: 'bird'`
  - `Animal.create common_name: 'Red Spotted Garter Snake', latin_name: 'Thamnophis sirtalis sirtalis', kingdom: 'snake'`
  - `Animal.create common_name: 'Pileated Woodpecker', latin_name: 'Dryocopus pileatus', kingdom: 'bird'`

  #### Story: As the consumer of the API I can update an animal in the database.
  - Added ` skip_before_action :verify_authenticity_token` to /app/controllers/application_controller.rb
    - Added Update method to controller
    - Verified in postman

  #### Story: As the consumer of the API I can destroy an animal in the database.
  - Added destroy method to controller
    - Verified in postman

#### Story: As the consumer of the API I can create a new animal in the database.
- Added create method to controller
    - verified in postman

#### Story: As the consumer of the API I can create a sighting of an animal with date (use the datetime datatype), a latitude, and a longitude.
Hint: An animal has_many sightings. (rails g resource Sighting animal_id:integer ...)
Hint: Datetime is written in Rails as “year-month-day hr:min:sec" (“2022-01-28 05:40:30")
- Created a new resource of Sighting to track them in the db
- `rails generate resource Sighting date:datetime latitude:integer longitude:integer animal_id:integer`
- `rm -rf app/views/sightings`
- `rails db:migrate` 
- In app/models/animal.rb => `has_many :sightings`
- In app/models/sighting.rb => `belongs_to :animal`
- Created index method in sightings controller

#### Story: As the consumer of the API I can update an animal sighting in the database.
- `animal = Animal.where(common_name: 'Bald Eagle').first`
- `animal.sightings.create date: Date.today.to_s, longitude: 31, latitude: 19`
- Created update method in sighting controller
- Verified in postman

#### Story: As the consumer of the API I can destroy an animal sighting in the database.
- Created destroy method in the sightings controller
- Verified in postman

#### Story: As the consumer of the API, when I view a specific animal, I can also see a list sightings of that animal.
Hint: Checkout the Ruby on Rails API docs on how to include associations.