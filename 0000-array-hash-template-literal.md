- Start Date: 2019-06-05
- Relevant Team(s): Ember.js
- RFC PR: (after opening the RFC PR, update this with a link to it and update the file name)
- Tracking: (leave this empty)

# Introduce template syntax for array and hash literals

## Summary

> One paragraph explanation of the feature.

### Array literal

```handlebars
<LinkTo @route="post" @models={{[@post.id @post.comments]}} />
```

```handlebars
{{#let [
    @post.id
    @post.comments
] as |models|}}
<LinkTo @route="post" @models={{models}} />
```

### Hash literal

```handlebars
<LinkTo @route="post" @model={{@post.id}} @query={{[showComments=false]}} />
```

```handlebars
{{#let [
        @post.id
        @post.comments
    ]
    [
        showComments=false
    ]
     as |models query|
}}
<LinkTo @route="post" @models={{models}} @query={{query}} />
```

## Motivation

> Why are we doing this? What use cases does it support? What is the expected
outcome?

## Detailed design

> This is the bulk of the RFC.

> Explain the design in enough detail for somebody
familiar with the framework to understand, and for somebody familiar with the
implementation to implement. This should get into specifics and corner-cases,
and include examples of how the feature is used. Any new terminology should be
defined here.

```handlebars
{{["this" "is" "an" "array"]}}
```

```handlebars
{{ ["this" "is" "an" "array" ["inside" "an" "array"]] }}
```

```handlebars
{{ [one="this" two="is" three="a" four="pojo"] }}
```

```handlebars
{{
    [
        one="this"
        two="is"
        three="a"
        four="pojo" 
        [one="inside" two="a" three="pojo"] 
    ] 
}}
```

```handlebars
{{
    [
        name="Katie Gengler"
        teams=["cli" "framework" "steering"]
    ]
}}
```

## How we teach this

> What names and terminology work best for these concepts and why? How is this
idea best presented? As a continuation of existing Ember patterns, or as a
wholly new one?

> Would the acceptance of this proposal mean the Ember guides must be
re-organized or altered? Does it change how Ember is taught to new users
at any level?

> How should this feature be introduced and taught to existing Ember
users?

## Drawbacks

> Why should we *not* do this? Please consider the impact on teaching Ember,
on the integration of this feature with other existing and planned features,
on the impact of the API churn on existing apps, etc.

> There are tradeoffs to choosing any path, please attempt to identify them here.

## Alternatives

> What other designs have been considered? What is the impact of not doing this?

> This section could also include prior art, that is, how other frameworks in the same domain have solved this problem.

## Unresolved questions

> Optional, but suggested for first drafts. What parts of the design are still
TBD?
