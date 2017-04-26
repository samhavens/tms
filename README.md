# TMS
Topanga Mountain School is a beautiful thing, but the teachers and staff spend too much time on activities that should be automated! This respository aims to fix that. Hopefully, this will also be useful to other schools and organizations - but one step at a time.

### Basic idea

A responsive webapp that uses messaging (when it makes sense) to automate as many of the low-value tasks of TMS staff as possible.

### Objects the system has to be aware of aka db tables

Students
Administrators
Teachers
Courses
Schedules
Grades
Narratives
Parents
Parent Volunteer Opportunities


### Tasks

#### Grouping

`n, Constraints -> Groups (n)`

Automatically generate groups of students, constrained on reasonable dimensions. For example, "James and Iggy can't be in the same group; definitely put Sky and Gabby together; A, B, and C need to be in separate groups (ran out of plausible student names))" would be a reasonable constraint, and then the system would be told how many groups to generate, and it would generate a random set of groups that met the criteria. 

- Students can be moved between groups.
- Groups can be regenerated.
- Groups can be renamed.
- Groups are easily exportable/printable.

#### Easily create a flexible schedule

The schedule changes frequently and is very unconstrained. If you map this to an RDB, whatever your schema is, it will probably make assumptions about this schedule that the real life schedule will want to violate.

Try to let this schedule do whatever it wants. The application should not attempt to validate the schedule as much as possible. It will just be used to read from, to know when to contact staff.

#### Automate email to students who miss class

This one is a no-brainer. Teachers manually sending emails to students who missed class? Two solutions:

1) Move teachers to blogs. This way, students pull missing info, rather than teachers pushing.
2) Teachers take attendance via the application (possibly messaging), then the teacher has to enter what information they need to send out, and it automatically gets sent to missing students.

hmmm, actually

#### Attendance

A way for teachers to easily take attendance via the application. It has to be SO EASY.

##### Dream

Seating chart -> take a picture of the class -> upload -> attendance done (except for absent students who become tardy)

#### Grades

A way to enter all assignments, or just overall grades.

#### Daily check in

TMS teachers have to do trimester-ly reports (Narratives) on students. This would be easier if they could remember the entire arc of each student over each class. How can we give them that?

My current best idea is to synch with the schedule, then check in with teachers at breaks, either between classes or recess/lunch/after school. Then ask them "anything noteworth happen in SCIENCE 2:15-3:15?"

A typical response might be "Julie was still very quiet... hoping to get her out of her shell." Then later, "Julie participated in a discussion, which was really good, but Angus got frustrated and left the room agian." Another day might mention "Julie is really sharing a lot!"

This response should be stored, and correlated with the class and teacher. Ideally, it would also be able to reference the student records mentioned. That way a narrative for each student (that gets mentioned), in each class, gets created. Then, come report card time, all those notes can show up on the appopriate student's report card template. For Julie, in our examples above, there would be the outline of a clear narrative about participating and engaging more in class.

Once this data is collected and stored appropriately, it also has to be displayed...

### Report card templating

The report card generation process is a nightmare. Across the whole school, we are talking about tens or even hundreds of wasted hours.

Teachers should be able to enter their course description in the app. They should also be able to work on student Narratives (it may make sense to make Google Docs the storage system for Narratives to take advantage of the versioning, and it lets teachers use a nice editing tool without building one). When writing Course Descriptions and Narratives, there should be NO NEED to think about formatting.

- Word count has to be enforced.
- There needs to be an editing process for administrators to edit Narratives.
- There needs to be a template report card that gets filled in with Course Descriptions, Grades, and Narratives for each student.
- The system should automatically resize font to fit the Narratives and Course Description to a page.
- The system should output HTML and PDF. HTML versions should be hosted and stored behind a login, PDFs should be emailable after they are reviewed.

#### Parent volunteering

System to automatically encourage parents to volunteer. Once they have signed up, the system needs to automatically send them reminders.

### Notes

I spent a year doing everything on the computer, and I went back to the green gradebook. Opening a laptop to take attendance is too big an ask. Teachers are already slammed, this needs to be easy as hell.

### TODO

Prioritize

#### Teacher client

- A web interface is good, but an app may be required. If so, if (jsonette)[http://jasonette.com/] suffices, let's go with that.
- Usine natural language input whenever possible
