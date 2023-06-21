# MauiBugThickness
A public repo to demonstrate a possible bug in .Net Maui when defining a thickness in XAML.

This is a small modification of the template project.

You can get exceptions at runtime when defining a thickness in a resource dictionary in XAML. Doing so as a string works in debug configuration, but the app will raise exceptions on release. However, if you define the thickness as a Thickness object, it will work on both configurations.

You can easily reproduce the error and its work around by commenting and uncommenting lines in [MainPage.xaml](https://github.com/salvadorjesus/MauiBugThickness/blob/41cc245cf733ccee2f38a97c8972c012c2216c53/Maui%20Bug%20Thickness/MainPage.xaml#L5-L16):

``` XAML
    <!--Works on release and debug:-->
    <!--<ContentPage.Resources>
        <Thickness x:Key="ButtonMargin">0,50,0,0</Thickness>
    </ContentPage.Resources>-->
    
    <!--Only works on debug.
    On release:
    Android: System.InvalidCastException: Arg_InvalidCastException [...]
    Windows: System.InvalidCastException / System.Reflection.TargetInvocationException-->
    <ContentPage.Resources>
        <x:String x:Key="ButtonMargin">0,50,0,0</x:String>
    </ContentPage.Resources>
```
