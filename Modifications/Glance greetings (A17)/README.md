# Feature 2 (part) — At a Glance greetings on the A17 base

A13 injected a `hint` TextView (`@string/hello_greeting`) into the
RelativeLayout smartspace cards. A17 uses ConstraintLayout templates,
so the injection is adapted: a `DoubleShadowTextView`
(`@+id/greeting`, title style) as the first child of `text_group` in
`res/layout/smartspace_base_template_card_with_date.xml`, with the
date view re-anchored below it (`Top_toBottomOf="@id/greeting"`).

## Strings

`hello_greeting` ("Hello!") and `hello_greeting_b` ("It's") in
`res/values/strings.xml`, merged into the 22 matching `values-*`
locales from the A13 mod (apostrophes escaped). Dynamic
morning/afternoon greetings came from the (removed) companion app
and need a runtime source — queued.
