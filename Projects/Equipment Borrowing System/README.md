A campus equipment borrowing and inventory system. Allows campus users to request permissions to borrow equipment and let maintainers approve requests, manage the inventory, maintenance, and monitor operations reports. A python project for the python course.

### Business Rules
- Users must always request for permission for equipment before being allowed to use them.
- Maintainers (admins) are to approve/reject requests from users. In addition, they are also responsible for managing inventory, equipment maintenance, and operational reports.
- The system must track every equipment borrowed and prevent duplicate borrowing from users.
- The system must also prevent data deletion and enforce only a soft delete on the data. 

### User Rules
- Admins are to have a dashboard showing different statistics like borrow rate, total amount of equipment borrowed, trend of borrows, etc. (maybe how many users are currently browsing for equipment to borrow as well)
- Admins are to generate reports.
- Admins are allowed to adjust and tweak settings.
- Admins can audit borrow requests, who borrow said equipment, timestamp when they borrowed, and a borrow purpose.
- Admins are allowed to manage users such as deactivating them to prevent sign-ins and requests from said user.
- Admins are allowed to browse users and request history.
- Admins are 

### System Rules
- Django framework
- Django auth (allowed)
- Django admin (prohibited)



### Todos
#### Admin
- [] Dashboard
	- [] Daily borrow count
	- [] Borrow trend chart
	- [] Live count of browsing users
	- [] Not returned equipment count
- [] Account management
	- [] List of users
	- [] User request history
	- [] Deactivate user (deactivation means preventing sign-ins and requests from the user)
- [] Equipment management
	- [] CRUD for categories and equipment
	- 
#### User
