# Social Media App

A simple social media web application that allows users to register, post updates, and comment on posts. Built with **Node.js, MySQL, and JavaScript**.

---

## Features

- User registration and login
- Create, edit, and delete posts
- Comment on posts
- Upload profile images
- Responsive design

---

## Technologies Used

- **Frontend:** HTML, CSS, JavaScript  
- **Backend:** Node.js, Express.js  
- **Database:** MySQL  

---

## Database Setup

1. Open MySQL or phpMyAdmin
2. Run the following SQL code to create the database and tables with sample data:

```sql
-- Create database
CREATE DATABASE IF NOT EXISTS social_media;
USE social_media;

-- -----------------------------
-- Table: users
-- -----------------------------
CREATE TABLE IF NOT EXISTS users (
    userId INT(11) NOT NULL AUTO_INCREMENT,
    userName VARCHAR(100) NOT NULL,
    userPassword VARCHAR(255) NOT NULL,
    userImage TEXT,
    createdAt TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (userId)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;


-- -----------------------------
-- Table: posts
-- -----------------------------
CREATE TABLE IF NOT EXISTS posts (
    postId INT(11) NOT NULL AUTO_INCREMENT,
    postedUserId INT(11) NOT NULL,
    postText TEXT,
    postImageUrl TEXT,
    postedTime TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (postId),
    FOREIGN KEY (postedUserId) REFERENCES users(userId) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;


-- -----------------------------
-- Table: comments
-- -----------------------------
CREATE TABLE IF NOT EXISTS comments (
    commentId INT(11) NOT NULL AUTO_INCREMENT,
    commentOfPostId INT(11) NOT NULL,
    commentedUserId INT(11) NOT NULL,
    commentText TEXT,
    commentTime TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (commentId),
    FOREIGN KEY (commentOfPostId) REFERENCES posts(postId) ON DELETE CASCADE,
    FOREIGN KEY (commentedUserId) REFERENCES users(userId) ON DELETE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

