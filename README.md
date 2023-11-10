# DSI Social Networking Platform - Graph Database Schema

## Table of Contents
- [Project Overview](#project-overview)
- [Files Required](#files-required)
- [Installation and Setup](#installation-and-setup)
- [Schema Description](#schema-description)
  - [Node Types](#node-types)
  - [Edge Types](#edge-types)
- [Potential Benefits](#potential-benefits)
- [Challenges](#challenges)

## Project Overview

This project develops a social networking platform tailored for the Data Science Institute (DSI) community. It aims to create a virtual space for DSI students and alumni to share insights, seek advice, and connect over shared interests - be they academic, career-oriented, or hobby-related.

## Files Required

To fully operate the project, ensure you have the following files in your directory:

- `neo4j_driver.ipynb`: Contains functions for connecting to and interacting with the Neo4j database. Also include the Cypher queries for populating the database with initial data.
- `docker-compose.yml`: Docker Compose configuration for setting up the Neo4j container.

## Installation and Setup

1. Install Docker and ensure it is running on your system.
2. Launch the Neo4j container with Docker Compose:`docker-compose up -d`

## Schema Description

Our database schema includes several node types (User, Post, Message, Group) and relationships (FRIENDS_WITH, POSTED, MEMBER_OF), effectively mapping the social interactions within the DSI community.

## Node Types

### User Node
- `username`: String, unique identifier for the user.
- `first_name`: String, first name for the user.
- `last_name`: String, last name for the user.
- `email`: String, user's email address for contact and notifications.
- `class`: Integer, year the user graduated from DSI.
- `company`: String, current company where the user is employed.
- `job_title`: String, user's current job title.
- `location`: String, geographic location of the user.
- `interests`: List of interests or hobbies of the user.

### Post Node
- `post_id`: Integer, unique identifier for the post.
- `author`: String, username of the user who made the post.
- `topic`: String, topic of the post.
- `timestamp`: DateTime, when the post was made.
- `content`: Text, body of the post.
- `likes_count`: Integer, number of likes received.
- `comments_count`: Integer, number of comments made.

### Message Node
- `message_id`: Integer, unique identifier for the message.
- `sender`: String, username of the user sending the message.
- `receiver`: String, username of the user receiving the message.
- `timestamp`: DateTime, when the message was sent.
- `content`: Text, body of the message.

### Group Node
- `name`: String, name of the group.
- `description`: Text, description of what the group is about.
- `members_count`: Integer, number of members in the group.
- `created_by`: String, username of the user who created the group.

## Edge Types

### FRIENDS_WITH (User to User)
- `since`: Date, when the two users became friends.

### POSTED (User to Post)
- `on_date`: Date, when the user posted the content.

### LIKES (User to Post)
- `on_date`: Date, when the user liked the post.

### COMMENTED_ON (User to Post)
- `comment`: Text, the content of the comment.
- `on_date`: Date, when the user commented on the post.

### SENT_MESSAGE (User to Message)
- `on_date`: Date, when the user sent the message.

### RECEIVED_MESSAGE (User to Message)
- `on_date`: Date, when the user received the message.

### MEMBER_OF (User to Group)
- `since`: Date, when the user joined the group.

## Potential Benefits

The platform is designed to:

- **Enhance Connectivity**: Facilitate networking among the DSI community.
- **Knowledge Sharing**: Serve as a repository for shared projects and experiences.
- **Community Engagement**: Encourage discussions and interactions among users.

## Challenges

Key challenges include:

- **Data Privacy**: Safeguarding user information while allowing social connections.
- **Scalability**: Adapting the database to accommodate growth in user activity.
- **User Participation**: Motivating users to contribute content and engage with the community.



