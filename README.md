# Database2
Database with trigger and added comment


CREATE TABLE Analytics (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    title TEXT,
    comments_count INTEGER DEFAULT 0
);

CREATE TABLE Comment(
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    content TEXT
);


INSERT INTO Analytics (title)
VALUES ('Website analytics');


CREATE TRIGGER increment_comments 
AFTER INSERT ON Comment
BEGIN
    UPDATE Analytics 
    SET comments_count = comments_count + 1 
    WHERE Analytics.id = 1;
END

INSERT INTO Comment (content)
VALUES ('This is my first comment!');

SELECT * FROM Analytics;
