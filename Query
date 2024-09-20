-- Create the database
CREATE DATABASE library;

-- Use the database
USE library;

-- Create the Branch table
CREATE TABLE Branch (
    Branch_no INT PRIMARY KEY,
    Manager_Id INT,
    Branch_address VARCHAR(255),
    Contact_no VARCHAR(15)
);

-- Create the Employee table
CREATE TABLE Employee (
    Emp_Id INT PRIMARY KEY,
    Emp_name VARCHAR(255),
    Position VARCHAR(50),
    Salary DECIMAL(10, 2),
    Branch_no INT,
    FOREIGN KEY (Branch_no) REFERENCES Branch(Branch_no)
);

-- Create the Books table
CREATE TABLE Books (
    ISBN VARCHAR(13) PRIMARY KEY,
    Book_title VARCHAR(255),
    Category VARCHAR(50),
    Rental_Price DECIMAL(10, 2),
    Status VARCHAR(3) CHECK (Status IN ('yes', 'no')),
    Author VARCHAR(255),
    Publisher VARCHAR(255)
);

-- Create the Customer table
CREATE TABLE Customer (
    Customer_Id INT PRIMARY KEY,
    Customer_name VARCHAR(255),
    Customer_address VARCHAR(255),
    Reg_date DATE
);

-- Create the IssueStatus table
CREATE TABLE IssueStatus (
    Issue_Id INT PRIMARY KEY,
    Issued_cust_id INT,
    Issued_book_name VARCHAR(255),
    Issue_date DATE,
    Isbn_book VARCHAR(13),
    FOREIGN KEY (Issued_cust_id) REFERENCES Customer(Customer_Id),
    FOREIGN KEY (Isbn_book) REFERENCES Books(ISBN)
);

-- Create the ReturnStatus table
CREATE TABLE ReturnStatus (
    Return_Id INT PRIMARY KEY,
    Return_cust INT,
    Return_book_name VARCHAR(255),
    Return_date DATE,
    Isbn_book2 VARCHAR(13),
    FOREIGN KEY (Return_cust) REFERENCES Customer(Customer_Id),
    FOREIGN KEY (Isbn_book2) REFERENCES Books(ISBN)
);
-- INSTERING VALUES INTO TABLES--

INSERT INTO Branch ( Branch_no,Manager_Id,Branch_address,Contact_no)
VALUES
(1,10,"Mechanical Department",101),
(2,20,"Civil Department",201),
(3,30,"Chemistry Department",301),
(4,40,"Physics Department",401),
(5,50,"Electrical Department",501),
(6,60,"Elecctronics Department",601),
(7,70,"Computer Department",701),
(8,80,"Biology Department",801),
(9,90,"History Department",901),
(10,100,"Civics Department",111);
SELECT * FROM Branch;
INSERT INTO Employee(Emp_Id,Emp_name,Position,Salary,Branch_no)
VALUES (1902,"Abin","ADMIN",55000,1),
(1732,"Jincy","Professor",12000,4),
(1533,"Ethan","Student",55000,5),
(1984,"Johan","Professor",15000,7),
(1235,"Jeevan","Student",45000,9);
SELECT * FROM Employee;
INSERT INTO Books (ISBN, Book_title, Category, Rental_Price, Status, Author, Publisher) 
VALUES
('978031488', 'The Name of the Wind', 'Fiction', 12.99, 'yes', 'Harper Lee', 'DAW Books'),
('978006084', 'It', 'Fiction', 10.50, 'yes', 'George Orwell', 'Viking'),
('978673319', 'The Green Mile', 'Fiction', 9.99, 'yes', 'F. Scott Fitzgerald', 'Signet Books'),
('978437209', 'Dune', 'Fiction', 11.25, 'yes', 'Herman Melville', 'Chilton Books'),
('978073565', 'The Hobbit', 'Fiction', 8.75, 'yes', 'J.D. Salinger', 'George Allen & Unwin'),
('978014350', 'A Wise Mans Fear', 'Nonfiction', 15.99, 'yes', 'Yuval Noah Harari', 'DAW Books'),
('978073592', 'Becoming', 'Biography', 14.50, 'yes', 'Michelle Obama', 'Crown Publishing Group'),
('978006097', 'Fight Club', 'Young Adult', 7.99, 'yes', 'Suzanne Collins', 'W.W.Norton'),
('978140655', 'The Kite Runner', 'Fiction', 13.50, 'yes', 'Khaled Hosseini', 'Riverhead Books'),
('978159003', 'The Giving Tree', 'Fiction', 10.99, 'yes', 'Cormac McCarthy', 'Harper and Row');
SELECT * FROM BOOKS;
INSERT INTO Customer (Customer_Id, Customer_name, Customer_address, Reg_date) VALUES
		('233','Joe Smith','1321 4th Street, New York, NY 10014','2023-01-15'),
		('456','Jane Smith','1321 4th Street, New York, NY 10014','2022-12-05'),
		('786','Tom Li','981 Main Street, Ann Arbor, MI 48104','2023-02-20'),
		('223','Angela Thompson','2212 Green Avenue, Ann Arbor, MI 48104','2023-03-10'),
		('363','Harry Emnace','121 Park Drive, Ann Arbor, MI 48104','2022-11-18'),
		('464','Tom Haverford','23 75th Street, New York, NY 10014','2023-04-25'),
		('342','Haley Jackson','231 52nd Avenue New York, NY 10014','2023-01-02'),
		('765','Michael Horford','653 Glen Avenue, Ann Arbor, MI 48104','2022-10-30');
SELECT * FROM Customer;
INSERT INTO IssueStatus (Issue_Id, Issued_cust_id, Issued_book_name, Issue_date, Isbn_book) VALUES
		(1, 456, 'The Name of the Wind', '2023-01-20', '978031488'),
		(2, 464, 'Becoming', '2023-02-05', '978073592'),
		(3, 233, 'The Giving Tree', '2023-02-10', '978159003'),
		(4, 765, 'Dune', '2023-03-15', '978437209'),
		(5, 342, 'It', '2023-03-20', '978006084'),
		(6, 786, 'A Wise Mans Fear', '2023-05-15', '978014350');
SELECT * FROM IssueStatus;
INSERT INTO ReturnStatus (Return_Id, Return_cust, Return_book_name, Return_date, Isbn_book2) VALUES
(1, 233, 'The Giving Tree', '2023-02-15', '978159003'),
(2, 342, 'It', '2023-03-30', '978006084'),
(3, 456, 'The Name of the Wind', '2023-04-15', '978031488'),
(4, 464, 'Becoming', '2023-05-20', '978073592'),
(5, 765, 'Dune', '2023-06-25', '978437209'),
(6, 786, 'A Wise Mans Fear', '2023-07-10', '978014350');
SELECT * FROM ReturnStatus;

-- Retrieve the book title, category, and rental price of all available books. --
SELECT Book_title, Category, Rental_Price
FROM Books
WHERE Status = 'yes';

-- List the employee names and their respective salaries in descending order of salary--
SELECT Emp_name, Salary
FROM Employee
ORDER BY Salary DESC;

-- Retrieve the book titles and the corresponding customers who have issued those books--

SELECT Books.Book_title, Customer.Customer_name
FROM IssueStatus
JOIN Books ON IssueStatus.Isbn_book = Books.ISBN
JOIN Customer ON IssueStatus.Issued_cust_id = Customer.Customer_Id;

-- Display the total count of books in each category:--
SELECT Category, COUNT(*) AS Total_Books
FROM Books
GROUP BY Category;

-- Display the branch numbers and the total count of employees in each branch:--

SELECT Branch_no, COUNT(*) AS Total_Employees
FROM Employee
GROUP BY Branch_no;


-- Display the names of customers who have issued books in the month of June 2023:--

SELECT Customer.Customer_name
FROM IssueStatus
JOIN Customer ON IssueStatus.Issued_cust_id = Customer.Customer_Id
WHERE Issue_date BETWEEN '2023-06-01' AND '2023-06-30';

-- Retrieve book_title from book table containing history:--
SELECT Book_title
FROM Books
WHERE Book_title LIKE '%history%';

-- Retrieve the branch numbers along with the count of employees for branches having more than 5 employees:--

SELECT Branch_no, COUNT(*) AS Total_Employees
FROM Employee
GROUP BY Branch_no
HAVING COUNT(*) > 5;

-- Display the names of customers who have issued books with a rental price higher than Rs. 25.--

SELECT Customer.Customer_name
FROM IssueStatus
JOIN Books ON IssueStatus.Isbn_book = Books.ISBN
JOIN Customer ON IssueStatus.Issued_cust_id = Customer.Customer_Id
WHERE Books.Rental_Price > 25;
