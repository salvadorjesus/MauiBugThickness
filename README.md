# MauiBugThickness
A public repo to demonstrate a possible bug in .Net Maui when defining a thickness in XAML.

This is a small modification of the template project.

You can get exceptions at runtime when defining a thickness in a resource dictionary in XAML. Doing so as a string works in debug configuration, but the app will end raising exceptions on release. However, if you define the thickness as a Thickness object, it will work on both configurations.