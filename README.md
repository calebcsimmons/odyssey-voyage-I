# Building a Federated Supergraph in GraphQL

## How to use this repo

### Backend

There are three main folders:

- `router`
- `subgraph-locations`
- `subgraph-reviews`

### Frontend

- `client` - frontend for the FlyBy app.

To run the client:

1. Open a new terminal window, and navigate to the `client` folder.
1. Run `npm install & npm start`. This will install all packages in the client and start the application in `localhost:3000`.

### Queries

1. Get all locations for the homepage.

   ```graphql
   query getAllLocations {
     locations {
       id
       name
       photo
       description
       overallRating
     }
   }
   ```

1. Get the latest reviews for the homepage.

   ```graphql
   query LatestReviews {
     latestReviews {
       comment
       rating
       location {
         name
         description
       }
     }
   }
   ```

1. Get details for a specific location.

   ```graphql
   query getLocationDetails {
     location(id: "loc-1") {
       id
       name
       description
       photo
       overallRating
       reviews {
         comment
         rating
       }
     }
   }
   ```

1. Submit a review for a location.
   ```graphql
   mutation submitReview {
     submitReview(review: { comment: "Wow, such a great planet!", rating: 5, locationId: "1" }) {
       code
       success
       message
       review {
         id
         comment
         rating
       }
     }
   }
   ```
