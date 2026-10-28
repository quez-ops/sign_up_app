# signup_app

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Learn Flutter](https://docs.flutter.dev/get-started/learn-flutter)
- [Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Flutter learning resources](https://docs.flutter.dev/reference/learning-resources)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.



Critical thinking questions:


Trace the local tip feature from button tap to displayed text. Which widget/state changes during the simulated loading state, and how does the user recover from the local error case?

Hitting the refresh button flips _isLoadingTip to true, swapping out the tip text for "Loading tip..." right inside the box. After a 900ms delay, the state turns loading back to false and puts the tip into _tipDisplay. If an error hits, tapping that same refresh button just reruns the function normally with triggerError: false so the tip can load properly.

Why must the app keep form validation local even when it can ask an AI for a tip?

Validation has to stay on the device so password checks and empty-field warnings work instantly every time, even offline. Relying on an outside service for basic rules just adds lag and creates points of failure where signups could break.

Give one example of a bad decision if AI were allowed to approve signup.

It could easily let a user create an account with two passwords that don't match or accept something insecure like "123456" just because the prompt sounded convincing.

Which fixed local category selects the tip, and what form information does the feature deliberately ignore? Why?

It pulls strictly from a fixed password help list. It ignores the name, email, and password controllers on purpose so plain-text passwords and personal info never get touched or exposed just to give generic advice.

Which local test case changed what you implemented? Describe what you observed.

Testing the simulated error case forced a change in the logic. At first, using index math caused an error right on the very first click since the index started at zero. Setting up an explicit error trigger fixed it so regular tip loading and the error demonstration could both be tested reliably on demand.