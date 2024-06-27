# Recommendation System

## Overview
The recommendation system provides personalized content recommendations to users based on their preferences and behavior. It utilizes data from four main tables: `users`, `contents`, `views`, and `votes`.

## Dataset Description
Here's a table summarizing the dataset description:

| DataFrame            | Column Name       | Description                                                |
|----------------------|-------------------|------------------------------------------------------------|
| Users (`users`)      | portal_user_id    | Unique identifier for each user, including the portal name.|
|                      | age_range         | Age group of the user.                                     |
|                      | gender            | Gender of the user.                                        |
|                      | tags              | Interests or topics the user is interested in, represented as a list. |
| Contents (`contents`) | global_id        | Unique identifier for each piece of content (Across all portals).     |
|                      | entity_id         | Internal tracking identifier for the content (Portal Level).    |
|                      | content_type      | Type of content.                                           |
|                      | content_title     | Title of the content.                                      |
|                      | content_topic     | Main topic of the content.                                 |
|                      | portal_name       | Name of portal the content belongs to.                     |
| Content Views (`views`) | portal_user_id | Identifier of the user who viewed the content.             |
|                      | global_id         | Identifier of the content that was viewed.                 |
|                      | entity_id         | Internal tracking identifier for the content.              |
|                      | event_type        | Type of interaction with the content.                      |
|                      | num_of_views      | Number of times the content was viewed by the user.        |
| User Votes (`votes`) | portal_user_id    | Identifier of the user who voted.                          |
|                      | global_id         | Identifier of the content that was voted on.               |
|                      | vote_type         | Type of vote given to the content (like, dislike, etc.).   |

> This table provides a concise overview of the dataset, including the columns present in each table (`users`, `contents`, `views`, and `votes`) and a brief description of each column.

## Data Preprocessing
- **Tag Preprocessing**: User tags are preprocessed to handle null values and convert JSON strings into lists of tags. This ensures consistency in user tags, making it easier to compute similarities.

## Recommendation Process
1. **Filtering by Portal Name**: The system starts by identifying the portal name from the user's ID to filter relevant content.
2. **Tag Similarity Calculation**: For each user, the system calculates similarity based on the tags they are interested in.
   - The similarity is computed as the ratio of the intersection to the union of tag sets.
3. **User Similarity Computation**: The system calculates similarity between users based on age, gender, and tags.
   - **Age and Gender**: Exact matches are given a similarity score of 1.
   - **Tags**: The similarity is computed using the tags associated with users.
4. **Analyzing Content Views**: The system examines content interactions by similar users to identify content that might interest the target user.
5. **Incorporating User Votes**: Votes are used to assess the quality of content based on user preferences.
   - **Vote Type**: Votes such as likes or dislikes are factored into the recommendation to prioritize content that has been positively rated by similar users.
   - **Vote Impact**: Content with positive votes from similar users is more likely to be recommended.
6. **Generating Recommendations**: Recommendations are based on content that similar users have interacted with and positively rated but the target user has not yet seen.

## Impact of Data on Recommendations
- **User Similarity**: Age, gender, and tags are used to find similar users, enhancing the accuracy of recommendations.
- **Content Popularity**: Information on content views and user votes helps identify popular and positively rated content, which can be recommended to users.
- **Content Quality**: Votes provide a measure of content quality and user preference, ensuring that high-quality, well-rated content is prioritized in recommendations.
- **Content Relevance**: Filtering content based on portal names and user votes ensures that recommendations are relevant and of high quality, aligning with the user's interests and preferences within that portal.

## Conclusion
The recommendation system leverages user data, content data, user interactions, and voting behavior to provide personalized content recommendations, improving user engagement and satisfaction. It enhances the user experience by delivering relevant and highly rated content based on their preferences and behavior.

> Note: This documentation provides an overview of the recommendation system and how it utilizes the dataset to generate personalized recommendations for users.
