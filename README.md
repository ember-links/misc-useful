# Misc useful Ember

* [Lazy loading images in viewport](#lazy-loading-images-in-viewport)
* [Return from Pushpayload](#return-from-pushpayload)

---

## Lazy loading images in viewport

> If you are looking for a responsive, lazy loaded artwork component that has fallback artwork and handles user monograms, take a look at the dummy-artwork component!  Also 3.5.8 released of ember-in-viewport.  I'm convinced this may be one of the more performance tuned, fully featured, battle tested viewport detection libraries out there.

[Link to test in Ember viewport github repo](https://github.com/DockYard/ember-in-viewport/blob/master/tests/dummy/app/components/dummy-artwork.js)

---

## Return from Pushpayload

> If you rely on the ds-pushpayload-return feature flag, you can use the following pattern to manually serialize the API response and push the record into the store.

**utils/push-payload.js**
```js
export function pushPayload(store, modelName, rawPayload) {
   let ModelClass = store.modelFor(modelName);
   let serializer = store.serializerFor(modelName);

   let jsonApiPayload = serializer.normalizeResponse(store, ModelClass, rawPayload, null, 'query');

  return store.push(jsonApiPayload);
}
```

```js
import { pushPayload } from '<app-name>/utils/push-payload';

...

pushPayload(this.get('store'), modelName, rawPayload);
```

[Link to official Ember blog article](https://blog.emberjs.com/2018/04/13/ember-3-1-released.html#toc_feature-flag-code-ds-pushpayload-return-code-4-of-4)
