## **Assignment No : 02**

## **Assignment Name : Designing a Library Management System Using UML**

## **Submission Date : September 30, 2024**

---

## **Theory :**
<div align="justify">
  
Unified Modeling Language (UML) is a standard visual language used to represent the design and structure of software systems. It helps in modeling the architecture, behavior, and interactions of objects within a system. UML provides a set of diagrams like class diagrams, sequence diagrams, and use case diagrams, which allow developers to visualize the system before actual coding begins. By using UML, teams can better understand and communicate the system’s functionality, making it easier to design, document, and maintain complex software projects.
</div>

## **Problem:**
Design a Library Management System using UML.

## **UML Diagram (Hand Drawing) :**
![Image1](https://github.com/user-attachments/assets/a38101f7-57c4-4c5b-b678-21beeaf357cc)

## **Discussion :**
<div align="justify">
The UML diagram represents a library management system involving several key classes: Library Management, Books, Librarian, Member, BorrowTransaction, and Fine. The relationships between these classes reflect real-world dependencies and interactions within the library environment.<br><br>

The relationship between Books and Library Management is an aggregation, as books can exist independently of the library. In contrast, both Members and Librarians are in a composition relationship with Library Management since their existence depends on the library itself.

The Librarian has an association with Books, indicating the librarian maintains book details. The BorrowTransaction and Fine classes show deeper dependencies, particularly through composition with Books and Members, reflecting that borrowing and fines are directly tied to these entities. The inheritance between Librarian and Member highlights that a librarian is also a member, and similarly, Fine is derived from BorrowTransaction, indicating that fines are a potential result of borrow transactions.

In terms of multiplicity, the diagram shows that:

A library can have one or more books and zero or more members, but only one librarian.
A book can only have one corresponding borrow transaction, while members can have multiple borrow transactions and fines.
This structure provides a clear representation of how different entities in the library system interact and depend on one another.


</div>

## **Conclusion :**
<div align="justify">
The UML diagram gives a clear picture of how a library management system works. The connections between Books, Members, Librarians, BorrowTransaction, and Fine show how everything depends on one another. The diagram also includes how many of each item can exist in the system. Each class has important details like a member's name, ID, email, or a book's title, author, and ISBN. There are also useful functions such as borrowDate(), returnDate(), addBook(), returnBook(), checkAvailability(), checkHistory(), and payFine(). This design makes it easier to manage the library, including books, borrowing, and fines.

</div>
<br>
