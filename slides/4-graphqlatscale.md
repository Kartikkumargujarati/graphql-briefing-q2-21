<!-- section-title: GraphQL at Scale -->

##  🚀 GraphQL at Scale

---

##### _Considerations & Best Practices_

---

## Nullability

###### _Field Nullability_

<!-- block-start: grid -->
<!-- block-start: column -->
```javascript
// schema definition 🤝
type Restaurant {
  name: String!
  rating: Int!
}

type Query {
  topRestaurant(): Restaurant
}
```
<!-- block-end -->
<!-- block-start: column -->
```javascript
// client query 👌
query {
    topRestaurant {
        name
        rating
    }
}
```
<!-- block-end -->
<!-- block-end -->

<!-- block-start: grid -->
<!-- block-start: column -->
```javascript
// all data present 👍
{
  topRestaurant: {
    name: "OneTaco",
    rating: 5
  }
}
```
<!-- block-end -->
<!-- block-start: column -->
```javascript
// no restaurant exist 👎
{ topRestaurant: null }
```
<!-- block-end -->
<!-- block-start: column -->
```javascript
// partial data 🙀
{
  "data": {
    "topRestaurant": null
  },
  "errors": [{
    "message": "Cannot return null for non-nullable field Restaurant.rating."
  }]
} 
```
<!-- block-end -->
<!-- block-end -->

---

###### _Argument Nullability_

<!-- block-start: grid -->
<!-- block-start: column -->
```javascript
// schema definition 🤝
type RestaurantFilter {
  cuisine: String
  rating: Int
}

type Query {
  topRestaurant(filter: RestaurantFilter!): Restaurant
}
```
<!-- block-end -->
<!-- block-start: column -->
```javascript
// old client query 💔
query {
    topRestaurant {
        name
        rating
    }
}
```
<!-- block-end -->
<!-- block-end -->

```javascript
// new client query 😐
query {
    topRestaurant ({rating: 5}) {
        name
        rating
    }
}
```

---

## Testing Best Practices
<div> 
    <br />
    <ul> 
        <li>
            <h7> Unit testing - Jest </h7>
        </li>
        <li>
            <h7> Integration testing - Nock </h7>
        </li>
        <li>
            <h7> E2E testing - K6</h7>
        </li>
        <li>
            <h7> Load Testing - K6 </h7>
        </li>
    </ul>
    <br />
</div>
<br />
