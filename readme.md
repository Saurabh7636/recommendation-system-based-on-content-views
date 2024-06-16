# Recommendation System

## Overview
The recommendation system is designed to provide personalized content recommendations to users based on their preferences and behavior. It uses a dataset consisting of three main tables: `users`, `contents`, and `views`. 

## Dataset Description
Sure, here's a table summarizing the dataset description:

| DataFrame     | Column Name      | Description                                       |
|----------------|------------------|---------------------------------------------------|
| Users (`users`) | portal_user_id   | Unique identifier for each user, including the portal name. |
|                | age_range        | Age group of the user.                            |
|                | gender           | Gender of the user.                               |
|                | tags             | Interests or topics the user is interested in, represented as a list. |
| Contents (`contents`) | global_id   | Unique identifier for each piece of content (Across all portals).     |
|                        | entity_id  | Internal tracking identifier for the content (Portal Level).    |
|                        | content_type | Type of content.                               |
|                        | content_title | Title of the content.                           |
|                        | content_topic | Main topic of the content.             |
|                        | portal_name   | Name of portal the content belongs to.  |
| Content Views (`views`) | portal_user_id | Identifier of the user who viewed the content. |
|                          | global_id       | Identifier of the content that was viewed.    |
|                          | entity_id       | Internal tracking identifier for the content. |
|                          | event_type      | Type of interaction with the content.         |
|                          | num_of_views    | Number of times the content was viewed by the user. |

> This table provides a concise overview of the dataset, including the columns present in each table (`users`, `contents`, and `views`) and a brief description of each column.

## Recommendation Process
1. **Filtering by Portal Name:** The system starts by identifying the portal name from the user's ID to filter relevant content.

2. **Finding Similar Users:** Based on age, gender, and tags, the system identifies similar users to the target user.

3. **Analyzing Content Views:** The system examines what content similar users have interacted with and how frequently.

4. **Generating Recommendations:** Recommendations are made based on the content that similar users have enjoyed but the target user has not yet seen.

## Impact of Data on Recommendations
- **User Similarity:** Age, gender, and tags are used to find similar users, enhancing the accuracy of recommendations.
- **Content Popularity:** Information on content views helps identify popular content, which can be recommended to users.
- **Content Relevance:** Filtering content based on portal names ensures that recommendations are relevant to the user's interests within that portal.

## Conclusion
The recommendation system leverages user data, content data, and user interactions to provide personalized content recommendations, improving user engagement and satisfaction. It enhances the user experience by delivering relevant content based on their preferences and behavior.

> Note : This documentation provides an overview of the recommendation system and how it utilizes the dataset to generate personalized recommendations for users.