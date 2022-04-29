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


#### Story: As the consumer of the API I can see all the animals in the database.
Hint: Make a few animals using Rails Console

- Terminal `$ rails generate resource Animal common_name:string latin_name:string kingdom:string`
- Remove the views: `$ rm -rf app/views/animals`
- Remove the stylesheet: `$ rm app/assets/stylesheets/animals.scss`
- `rails db:migrate`
- `rails c`

- Add some animals to the database:
  - `Animal.create common_name: 'Bald Eagle', latin_name: 'Haliaeetus leucocephalus', kingdom: 'bird'`
  - `Animal.create common_name: 'Common Yellowthroat', latin_name: 'Geothlypis trichas', kingdom: 'bird'`
  - `Animal.create common_name: 'Red Spotted Garter Snake', latin_name: 'Thamnophis sirtalis sirtalis', kingdom: 'snake'`
  - `Animal.create common_name: 'Pileated Woodpecker', latin_name: 'Dryocopus pileatus', kingdom: 'bird'`