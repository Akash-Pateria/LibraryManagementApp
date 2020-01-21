# Library Management Application

[Requirement Specification Document](https://github.ncsu.edu/apateri/517-Program-2-Rails#cscece-517---object-oriented-design-and-development)

# Credentials

Role | Email            | Password | Notes            |
-----|------------------|----------|------------------|
Admin| admin@system.com | password | Cannot be deleted|

# Local Deployment
To run the app locally, follow these steps:

- Clone the repository on your local machine.
~~~
git clone https://github.com/Akash-Pateria/LibraryManagementApp/edit/master/README.md
~~~
    
- Go to the directory of the project where it is cloned using terminal
~~~
cd ~/LibraryManagementApp
~~~
    
- Install gems
~~~
bundle install
~~~
- Complete Database Migrations
~~~
rake db:migrate
~~~
- Add pre-configured users and data
~~~
rake db:seed
~~~
- Run server
~~~
rails server
~~~
Your app will run on http://localhost:3000

# Features

## Admin

- Log in with an email and password
- Edit profile
- Create/Modify Librarian or Student accounts
- Create/Modify/Delete Libraries and Books.
- View the list of users (students and librarians) and their profile details (except password)
- View the list of books, along with detailed information.
- View the list of book hold requests.
- View the list of Checked out books.
- View the list of students with books overdue (along with overdue fines).
- View the borrowing history of each book.
- Delete Student/Book/Librarian from the system

## Librarian

- Log in with email and password.
- Edit their own profile to choose an existing library. Each librarian can only work for one library.
- Edit library attributes.
- Add/Remove books to/from a library.
- View & Edit book information.
- View all books.
- View hold requests for any book in the library he/she works in.
- For books in the special collection, accept or deny book hold request.
- View list of all the books that are checked out from their library.
- View the borrowing history of the books from their library.
- View the list of students with overdue books from their library along with overdue fine.

## Student

- View the list of all the libraries
- Edit profile to modify email, name and password only.
- View all books
- Check out/Request/Return a book from any library associated with their University.
- Delete a reservation request, which has not been approved yet (pending).
- View/Edit their account attributes (including changing their password).
- Search through the books
  - Search by title
  - Search by author
  - Search by publication date
  - Search by subject
- Bookmark a book they are interested in and view their bookmarked books.
- At any given time, a student can borrow a max of 'N' number of books based on their educational level.
- View the overdue fines for his/her account.
- Receive an email when any of their book request is successful.

## Book Hold Request

- If the book is available, proceed to check out:
  - If the book is in Special Collection list, add this to Librarian's approval list and wait.
  - Otherwise, add the book to student's checked out list
- If the book is unavailable or the student has checked out N books already,
  - Inform the student that the book is unavailable or max limit reached.
  - Create a book hold request if the student wants to continue requesting.
- Number of hold requests for a book should be visible to every user.

## Book Return

- If there is no hold request for a book, return and increase the available count of the book
- If there is a pending hold request,
  - Approve the hold request and add the book to the checked out list of the requested student
  - Send a mail to the student that the book is checked out.
