# Exhaustiveness checks in TypeScript

Talk about this use case, similar use cases, and type-driven development tips:

```typescript
/**
 * See usage in `availabilityRequestCreateInputOmittedFields`.
 *
 * The arguments passed to `Record` here ensure the exhaustiveness of this
 * object. Try removing one of the keys, and you'll see TypeScript complain
 * about a missing field.
 *
 * Using an object here is done merely to take advantage of TypeScript's
 * exhaustiveness check on the fields, since arrays aren't checked for
 * exhaustiveness (they're of dynamic length) and I don't know how to refine
 * the types we have into a tuple.
 */
const availabilityRequestAndCreateInputDiff: Record<
  Exclude<keyof AvailabilityRequestFragment, keyof AvailabilityRequestCreateInput>,
  unknown
> = {
  __typename: true,
  id: true,
  aasmState: true,
  createdAt: true,
  documents: true,
  eventConceptDocument: true,
  inventoryIntendedUsage: true,
  priceComponents: true,
  selectedSpaceBookingIntervals: true,
  suggestion: true,
  totalPrice: true,
}

/**
 * We populate the AReq creation input with the fields from the existing
 * availability request. This means we need to filter out the fields that don't
 * fit in a creation input but are nevertheless in the AReq.
 */
const availabilityRequestCreateInputOmittedFields = Object.keys(
  availabilityRequestAndCreateInputDiff,
)
```
