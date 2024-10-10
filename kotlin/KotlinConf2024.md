# KotlinConf 2024

## Pushing the limits of the Server Side UI platform with KMP | Paulina Sadowska

> [Video](https://www.youtube.com/watch?v=PQSGD9ySuM0&list=PLq1zqU_rm4fjHfRCI2-xS8TycnzkQTC_m&index=1)

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

| MBox | Native |
|-|-|
| frequently changed content | complex side-logic |
| limited interaction | highly interactive content |

Complex client-side logic became a blocker to MBox adoption. To address they needed:

> 1. View binding
> 2. Client-side logic

They investigated JSC ([detailed trade-offs](https://youtu.be/PQSGD9ySuM0?list=PLq1zqU_rm4fjHfRCI2-xS8TycnzkQTC_m&t=736)).

