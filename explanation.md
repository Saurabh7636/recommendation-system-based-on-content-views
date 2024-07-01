# User Recommendation System Documentation

## Introduction

This document describes the functionality of a content recommendation system developed to provide personalized recommendations for users. The system leverages user interaction data, content information, and user attributes to generate recommendations. It combines content view similarity and user attribute similarity to offer tailored content suggestions.

## Data Overview

The system uses four datasets:

1. **User Data (`users.csv`)**: Contains information about users, including their age, gender, and tags indicating interests or preferences.
2. **Content Data (`contents.csv`)**: Contains details about available content, such as titles, types, and associated portals.
3. **Content Views Data (`content_views.csv`)**: Records user interactions with content, including the number of views.
4. **User Votes Data (`user_votes.csv`)**: Logs user votes on content, capturing upvotes and downvotes.

## Data Preprocessing

**Duplicate Removal**: Duplicate entries in the content data are removed to ensure each piece of content is unique based on its global ID, entity ID, and portal name.

**Portal Name Extraction**: The system extracts the portal name from the user’s ID to link user activities with the corresponding portal's content.

**Tag Preprocessing**: User tags are processed to handle null values and invalid formats, ensuring that tags are correctly parsed and usable for similarity calculations.

**User Attributes DataFrame**: A DataFrame indexed by user IDs is created to hold user attributes, facilitating quick access and manipulation during similarity computations.

## Similarity Computation

**Tag Similarity**: The system calculates the similarity between user tags using a Jaccard index approach. It compares the intersection and union of tag sets for different users to derive a similarity score.

**User Similarity Based on Attributes**: Similarity between users is calculated based on three key attributes:
- **Age Range**
- **Gender**
- **Tags**

Each attribute contributes to an overall similarity score, with adjustable weights for fine-tuning the influence of each attribute.

## Recommendation Generation

**Content Filtering**: The system filters content and views data by the identified portal name for the user in question. This ensures recommendations are relevant to the user's portal.

**Interaction Matrix Creation**: An interaction matrix is created, mapping user IDs to the number of views for each piece of content. This matrix is then converted to a sparse matrix for efficient computation.

**Cosine Similarity Computation**: The system computes cosine similarity between users based on their content viewing patterns. This measures how similar users are in terms of their interaction with content.

**Attribute Similarity Integration**: User attribute similarity scores are combined with content view similarity scores. This integration ensures that recommendations consider both user preferences and viewing behaviors.

**Recommendation Filtering**: Content that the user has already viewed or downvoted is filtered out from the recommendations. Upvoted content by the user is given a higher priority by boosting its score.

**Score Calculation**: The final recommendation scores are calculated by combining similarity metrics and vote adjustments. These scores are used to rank content, and the top-ranked content is recommended to the user.

## Example Usage

The system can be queried to generate recommendations for a specific user by providing their user ID. The example provided in the script demonstrates how to obtain the top 4 recommendations for a user with ID `aaa1b-207`.

## Conclusion

This content recommendation system offers a comprehensive method for personalizing content suggestions based on user interactions and attributes. It balances the influence of different similarity measures to provide relevant and engaging content for users.

Adjustments can be made to the system’s parameters and weights to optimize the recommendation results for different scenarios or datasets.

>This documentation provides an overview of the recommendation system's functionality without delving into the technical details of the code implementation.