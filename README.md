# hack-level2
Naan Mudhalvan hackathon level2
WORKBENCH GENERATED ER DIAGRAM:

 
3. Queries for Data Management
3.1 Insert Sample Data 
INSERT INTO Books (Title, Author, Genre, PublicationYear, CopiesAvailable)
VALUES 
('1984', 'George Orwell', 'Dystopian', 1949, 5),
('To Kill a Mockingbird', 'Harper Lee', 'Fiction', 1960, 3),
('The Great Gatsby', 'F. Scott Fitzgerald', 'Classics', 1925, 4),
('A Brief History of Time', 'Stephen Hawking', 'Science', 1988, 2),
('The Catcher in the Rye', 'J.D. Salinger', 'Fiction', 1951, 6);
3.2 Retrieval Queries
1. Fetch Books by Genre
SELECT Title, Author, PublicationYear, CopiesAvailable
FROM Books
WHERE Genre = 'Fiction';
2. Get Overdue Books
SELECT u.Name AS UserName, b.Title AS BookTitle, l.DueDate
FROM Loans l
JOIN Users u ON l.UserID = u.UserID
JOIN Books b ON l.BookID = b.BookID
WHERE l.DueDate < CURDATE() AND l.ReturnDate IS NULL;
3. List All Available Books
SELECT Title, Author, Genre, CopiesAvailable
FROM Books
WHERE CopiesAvailable > 0;
4. Track Loans by a Specific User
SELECT b.Title, l.LoanDate, l.DueDate
FROM Loans l
JOIN Books b ON l.BookID = b.BookID
WHERE l.UserID = 1 AND l.ReturnDate IS NULL;
5. Count Total Books by Genre
SELECT Genre, COUNT(*) AS TotalBooks
FROM Books
GROUP BY Genre;
6. List Users with Active Loans
SELECT DISTINCT u.Name, u.Email
FROM Loans l
JOIN Users u ON l.UserID = u.UserID
WHERE l.ReturnDate IS NULL;
7. Get Most Borrowed Books
SELECT b.Title, COUNT(l.LoanID) AS BorrowCount
FROM Loans l
JOIN Books b ON l.BookID = b.BookID
GROUP BY b.BookID
ORDER BY BorrowCount DESC
LIMIT 5;






4. IMPLEMENTATION & RESULTS 
4.1 Execution Environment:
For the Execution Environment, you can specify the tools and platforms used to implement your Library Management System (LMS). Here's an example of how you might describe it:
1.	Database Management Tool: MySQL Workbench (or Oracle SQL Developer)
o	Used for creating the database schema, inserting sample data, and executing SQL queries.
o	Enabled visualization of relationships and generation of the ER diagram.
2.	SQL Version: MySQL 8.0 (or Oracle SQL if applicable)
o	Provided a robust platform for developing, testing, and managing the database.
3.	Operating System: Windows 11
o	Served as the primary platform for running MySQL Workbench (or Oracle SQL Developer).
4.	Hardware:
o	Processor: Intel Core i5 or equivalent
o	RAM: 8 GB (minimum recommended for smooth execution)
5.	Additional Tools (if applicable):
o	A front-end application for connecting to the database (e.g., Python Flask/Django for testing or JavaScript with Node.js).









4.2 Screenshots of Execution Results
    







  

