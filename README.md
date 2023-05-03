# Udiddit-a-social-news-aggregator

# Introduction
Udiddit, a social news aggregation, web content rating, and discussion website, is currently using a risky and unreliable Postgres database schema to store the forum posts, discussions, and votes made by their users about different topics.

The schema allows posts to be created by registered users on certain topics, and can include a URL or a text content. It also allows registered users to cast an upvote (like) or downvote (dislike) for any forum post that has been created. In addition to this, the schema also allows registered users to add comments on create_posts.

Here is the DDL used to create the schema:

`CREATE TABLE bad_posts (
	id SERIAL PRIMARY KEY,
	topic VARCHAR(50),
	username VARCHAR(50),
	title VARCHAR(150),
	url VARCHAR(4000) DEFAULT NULL,
	text_content TEXT DEFAULT NULL,
	upvotes TEXT,
	downvotes TEXT
);`

`CREATE TABLE bad_comments (
	id SERIAL PRIMARY KEY,
	username VARCHAR(50),
	post_id BIGINT,
	text_content TEXT
);`



# Part I: Investigate the existing schema
As a first step, investigate this schema and some of the sample data in the project’s SQL workspace. Then, in your own words, outline three (3) specific things that could be improved about this schema. Don’t hesitate to outline more if you want to stand out!

1.	Data Type: Upvotes and Downvotes should not be text. They should be INT data type.
2.	Bad_posts Table: This is not normalized. There should be another table- user_info containing Users_id which, with username, will form primary keys. This User_id can be included in Bad_posts table referenced as a foreign key.
3.	Bad_comments table: Similarly, instead of username, user_id from user_info table should be included as foreign key.

# Part II: Create the DDL for your new schema
Once you’ve taken the time to think about your new schema, write the DDL for it in the space provided here:

# Part III: Migrate the provided data
Write the DML to migrate the current data in bad_posts and bad_comments to your new database schema:
