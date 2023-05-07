# second-sight
This project collects donated prescription eyewear and unopened, unexpired contact lenses to distribute to individuals in need, with the aim of improving access to affordable vision correction.

## Pitch
Do you have old prescription eyewear that you no longer need? Don't let it go to waste - donate it to Second Sight! Our project is focused on collecting and distributing prescription eyewear to those who can't afford it or don't have access to it. By donating your old glasses or contact lenses, you can help someone in need to see more clearly and improve their quality of life. Whether your prescription has changed, you've had laser eye surgery, or a loved one has passed away, your unwanted eyewear can make a big difference in someone's life. Join our community of donors and help us provide a second chance for those in need of clear vision. Together, we can make a difference and change someone's life for the better.

## Common RX Acronyms
- OD: Oculus Dexter refers to right eye.
- OS: Oculus Sinister refers to left eye.
- SPH: Sphere corrects nearsighted or farsighted vision.
- CYL: Cylinder combined with Axis corrects astigmatism.
- PD: Pupillary Distance is the measurement of distance between the pupils.

## Database Schema Plan
* Describe the structure of your database. You may use words or a picture. A bulleted list is probably the simplest way to do this. *

Table: users
* id: INTEGER NOT NULL AUTOINCREMENT UNIQUE PRIMARY KEY
* first_name: TEXT NOT NULL
* last_name: TEXT NOT NULL
* address: TEXT NOT NULL // mailing address for shipping
* email: TEXT NOT NULL // email for contacting
* password: TEXT NOT NULL
* session: INTEGER UNIQUE // random number generated

Table: prescription
* id: INTEGER NOT NULL AUTOINCREMENT UNIQUE PRIMARY KEY
* donor: INTEGER // matches users.id
* type: TEXT NOT NULL // glasses (left lens, right lens - how to account for bifocals?) or contacts
* sphere: FLOAT NOT NULL
* cylinder: FLOAT NOT NULL
* axis: FLOAT NOT NULL
* add: TEXT NOT NULL
* prism: TEXT NOT NULL
* base: TEXT NOT NULL
* pd: TEXT NOT NULL // pupillary distance

Table: contacts
* id: INTEGER NOT NULL AUTOINCREMENT UNIQUE PRIMARY KEY
* type: TEXT NOT NULL // hard or soft
* brand: TEXT NOT NULL
* expiration: TEXT NOT NULL
* schedule: TEXT NOT NULL // daily, weekly, bi-weekly, monthly disposable lenses, or extended
* quantity: INTEGER NOT NULL // number of contacts with this prescription
* is_new: TEXT NOT NULL // verifying contacts are unused and new

Table: glasses
* id: INTEGER NOT NULL AUTOINCREMENT UNIQUE PRIMARY KEY
* type: TEXT NOT NULL // bifocals or single vision
* frame_size: TEXT NOT NULL
* lens_material: TEXT NOT NULL
* condition: TEXT NOT NULL // condition of eyewear

## Database Query Plan

// check login
* SELECT * FROM users where username = :username AND password = :password;
* Generate new session number

// check if session is active
* Make sure session key number is still valid

// logout
* Set session key to null

// create new user

// add donations
* user must be logged in

// search donations for a match
* user must be logged in

// delete donations once a listing is expired
DELETE FROM photo_tags WHERE expiration > CURRENT_DATE;

// remove listing by donor
* logged in user must be the donor

// someone has claimed the donated item

## Expanding scope
- Prescription Verification
- Incrase tolerance of prescription for close and not exact match
- Including glasses
