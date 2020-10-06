# Layout Options

PlantUML uses [Graphviz](https://www.graphviz.org/) for its graph visualization. Thus the rendering itself is done automatically for you - that it one of the biggest advantages of using PlantUML.

...and also sometimes one of the biggest disadvantages, if the rendering is not what the user intended.

For this reason, C4-PlantUML also comes with some layout options.

## LAYOUT_TOP_DOWN() or LAYOUT_LEFT_RIGHT()

With the two macros `LAYOUT_TOP_DOWN()` and `LAYOUT_LEFT_RIGHT()` it is possible to easily change the flow visualization of the diagram. `LAYOUT_TOP_DOWN()` is the default.

```csharp
@startuml LAYOUT_TOP_DOWN Sample
!include https://raw.githubusercontent.com/scarrier/C4-PlantUML/latest/C4_Container.puml

/' Not needed because this is the default '/
LAYOUT_TOP_DOWN()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![LAYOUT_TOP_DOWN Sample](https://www.plantuml.com/plantuml/png/NO_BpjCm48NtVegXB99A9L4HArOD0S6YbuYaLAmYnvbIIxvOzaHHXNXtfcgXltvlZZnpvimtcqGoqcGDRAkVXsFNTuUc_tmuxQ6LDXWKRxHJPXeHBaGXVIpBAEVYbwRBD4m9e_AEq56Xl2sJaZ5gZ6NzuLrZfAFZRbiQIPY8IttDLgaTnYBmFY7A3FQUm26EECA0Id8Wq4Kdq8aLOSIpd0n1LefNTFbIY0PZyYwNezLk1OlgfZfHbEJZOYdQQoAq_IS_kL76QwxMAyZkHsLB-2s0tt-aVCQXbo5mpWa7g48mMadItYsuLBzTGTKsnVvBnoCHuNsnXjsF-jQhZF5p0aQF3Er1UHiaMoo3Qzu5tQo9C09fYuPt9MRxyw3BwTxad8UDc-8xcdzNFR6EYITPltLTqxABJK_ePynNfCHVlCavUljoP8DkdApv2m00 "LAYOUT_TOP_DOWN Sample")

Using `LAYOUT_LEFT_RIGHT`

```csharp
@startuml LAYOUT_LEFT_RIGHT Sample
!include https://raw.githubusercontent.com/scarrier/C4-PlantUML/latest/C4_Container.puml

LAYOUT_LEFT_RIGHT()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![LAYOUT_LEFT_RIGHT Sample](https://www.plantuml.com/plantuml/png/PKzDQzj04BtlhvYw1ylWIhZqr9DLuTe5knMMt92JM4kJU64_bjqHmeJyzuomOmUobs7dlNaVoqWoK6yqRFF7VuUwsQv-ryt-ptfJGoMDroY-ADlglaCu4VduCyk27D9dHQV-s4SChRE4bjBMcIosCWI58Ij-V2krj7JORJCj2IFngYcOAfN5a7fs5EAJPJ8JeiGGdKraPvITmoGVfueK9BamcOdg70bDyylrjfFXdBIBEKmlIQSpU170x-QJ37XifFUiyu17oBtNgfMad9tmglWwXxmgqx-hcay2mlTq0Rl_nOZbMhiXmbWm0ZdWTbuonVIQ57j1FIWY343Ae6QloDbUh-aIke2iSwKnAFQetrlTOnqYN_BSr7LPCMiatT2xp1efyXV7yHIS-NYoHDlrHhy1 "LAYOUT_LEFT_RIGHT Sample")

## LAYOUT_WITH_LEGEND()

Colors can help to add additional information or simply to make the diagram more aesthetically pleasing.
It can also help to save some space.

All of that is the reason, C4-PlantUML uses colors and prefer also to enable a layout without `<<stereotypes>>` and with a legend.
This can be enabled with `LAYOUT_WITH_LEGEND()`.

```csharp
@startuml LAYOUT_WITH_LEGEND Sample
!include https://raw.githubusercontent.com/scarrier/C4-PlantUML/latest/C4_Container.puml

LAYOUT_WITH_LEGEND()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![LAYOUT_WITH_LEGEND Sample](https://www.plantuml.com/plantuml/png/PKzDZzem4BtxLqpfWI3HH5GzzKIQ8gW4D6f2KK-HIQQB9NzOzaGHMkr_tubWOQNrPUHvRzx7Cf8Cr1iDs_pVxqFT77_LcsQxMg_sFw6InciKdvHjTTyXd8by_9vbGGxfaw9pV-eZXjPPGajfwqmMMnc2mf0LtxwKMbewxBQPbeIHUDKKJ9NAOaWzMmhnqJEP2L5YYCuciZFApc6IZrD52f9ScCn4TOc4fldXUjl9S4dQnHocrwZJ6JmBu7StIWOyDT9xrZdY2NBljMebAMSdl2e-po6lodI_glaa87nD5x3xMunOhhKR8emD8v03hkSbKqolIR4Nr8CYmW2a36hsYfpjvPOkeIl8EZSQW-8FwhTMZrY7o9SyDtLTLimQINVq8RD6Ylp5SVmFphm_MQBjUgDV0G00 "LAYOUT_WITH_LEGEND Sample")


## LAYOUT_AS_SKETCH()

C4-PlantUML can be especially helpful during up-front design sessions.
One thing which is often ignored is the fact, that these software architecture sketches are just sketches.

Without any proof

* if they are technically possible
* if they can fullfil all requirements
* if they keep what they promise

More often these sketches are used by many people as facts and are manifested into their documentations.
With `LAYOUT_AS_SKETCH()` you can make a difference.

```csharp
@startuml LAYOUT_AS_SKETCH Sample
!include https://raw.githubusercontent.com/scarrier/C4-PlantUML/latest/C4_Container.puml

LAYOUT_AS_SKETCH()

Person(admin, "Administrator")
System_Boundary(c1, 'Sample') {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![LAYOUT_WITH_LEGEND Sample](https://www.plantuml.com/plantuml/png/NKzDQ-Cm4BthLync3t4WQvDbJtkAQq83JLfJEoqz6SMUDW9z26cC2QN_lMEI9gMw39htvdqi8yb0lT6moLyUTdMJLqrrjwgBDLJIU8tYbxAjxZk40v6F_xCio25zKtJeztt4q3fBQ2bjdSbYAqDG6BBYtvzIIqkxxIRJaZ0Ihvg2gL9P3AbdGo5-EYOp8KeCqTb4TaRPEKpoSQf8GP8BavceZf7GD3UkjvqCnwHTp65w2ZgTmRi0VXURPC1z8xrddMVSG-wzLgqavUo4LyNlEUHLcTwlQZu927_J1MoVYX7BjNP3XB5V17B0vRnaYkarAVQ2Ub14682KGSrUaRDzdDCbT09PvqnZK3oY_cfrZRMBVCbpNTTbnQoHT46lChT8aRyuZjVWpFUJ9TgkD_eJ "LAYOUT_WITH_LEGEND Sample")
