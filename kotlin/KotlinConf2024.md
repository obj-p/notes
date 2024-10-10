# KotlinConf 2024

## Pushing the limits of the Server Side UI platform with KMP | Paulina Sadowska

> [Video](https://www.youtube.com/watch?v=PQSGD9ySuM0&list=PLq1zqU_rm4fjHfRCI2-xS8TycnzkQTC_m&index=1)

### MBox

Server Side UI platform MBox circa 2019 ([allegro Tech Blog](https://blog.allegro.tech/2022/08/mbox-server-driven-ui-for-mobile-apps.html)).

Allows BE to specify page for FE.

```javascript
const OfferView = () => {
  return <FlexContainer {...} >
    <Image {...} />
    <FlexContainer {...} >
      <Badge {...} />
      <Label {...} />
    </FlexContainer>
    <Price {...} />
    <Image {...} />
    <Label {...} />
  </FlexContainer>
}
```

The above is serialized into JSON and rendered on FE.

### MBox vs. Native

| MBox                       | Native                     |
| -------------------------- | -------------------------- |
| frequently changed content | complex side-logic         |
| limited interaction        | highly interactive content |

### Improving MBox to address developer concerns

Complex client-side logic became a blocker to MBox adoption. To address they needed:

> 1. View binding
> 2. Client-side logic

They investigated JSC ([detailed trade-offs](https://youtu.be/PQSGD9ySuM0?list=PLq1zqU_rm4fjHfRCI2-xS8TycnzkQTC_m&t=736)). Eventually they decided to make a customer client-side logic engine.

What does a client-side logic engine need:

> 1. Cross-platform engine
> 2. Contract
> 3. Developer-friendly language

For 2. used [JsonLogic](https://jsonlogic.com).

```json
{
  "if": [
    {
      "<": [{ "length": { "var": "password" } }, 8]
    },
    "password is too short",
    ""
  ]
}
```

JSON isn't a great developer experience. They created a DSL to represent the above and ultimately be serialized to JSON Logic.

```javascript
password.length().get() < 8 ? "password is too short" : ""
```

Implemented 1. with KMP ([detailed discussion](https://youtu.be/PQSGD9ySuM0?list=PLq1zqU_rm4fjHfRCI2-xS8TycnzkQTC_m&t=1148)).

KMP library for JSON logic engine is [open-source](https://github.com/allegro/json-logic-kmp).
