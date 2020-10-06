# C4-PlantUML


![Container diagram for Internet Banking System](https://www.plantuml.com/plantuml/png/bLJ1RkCs4BtxAwRfeLv0YL6qfvxMiOqcMpjHLqwpFGaZQYmJIv42ITanYlvxXueYHiu2wTwaqSnxZsyUzT5vjBwjrUG7gOLgIuAzzutxRJQpUBogfD-tHUl82gCzQNybJ3rp0gsLP6UBNozJXTe_RDOpXPwSvrA-u5QKcknL4u1_WbRpLCtJuFS4EwEKEKfTWU8cG5t2wBEqZfyCC2ie8r2f4sCCyjuIyDVr_E_xXss-lK_pvVtZtVH3hCspFFjZjLtSSB4lFTvkR_BrwlVLtPAB4o-z8XX0ePHOMQnPg8LRxSbgyd2D-clGd9sSfteoISawewUYTTxKP1DO34yNStWfWzbrXofuEe4ZkmbDDuYggm4AOLhjtGNhU8REhxbGeZrDnS-CTIxWuWFyCm60g7Twf2B7fk7cHofWtZHA2lJIw0ikVS839f0rDeZV_BK8jIKfUM0PdJJdkLT0lz-mZguyy1Ol1q_dB7BCx1fak8m_AxfCiQB0_iAQ2IiRdy1SLwr26ygfDGTPaWDKwjiiEyvAa8vA-bD8WMWx8nqS98OHQO7F2uKrHqVsZQBQ559HRyScl0oQ5Zycy0LhP2V6Ma39MdegmRM58yyx-z_Qt1jnpmAWf8CKT2vlMKnBz5YWex26_Z6eoVvSm-ZT6ylQmiq3IvLqtY9JWzISohhRRW9xTAmQMqwLi5IIzXALIqAeo3bGfk8NykBgZKq5Yg-aI_P9Xhocjz-EpT9mcurp8z_UyITOmi1C_UyGxL_IATKeLUwwTqPRNMxulRzL0NxBpjDJG4O56ociSMRdOVKazgWhWkT9HkqXLqz-sWk8g8ofTnPhEhksqTakWVsY1HU6Gxmo6B0mhOzRJeRRce2tg1rsnuqUJpwJUlL7YFVomP4Bt3VRRPfnuxZFDVXkJv_h2DVJvNSagtrXub-WWujtl4VgYgEj3uJeJbeay2cxlvkz9e-KtpcPNtDt51OJFqRvJ5Wws5bJTp-TevMU77WJa7lWvVM28GVCLtwSnIXZM0Tq6QeTHXHobhYnXl5SwpW1aJxRR5C66hay6X_dBXhJpSzwTxvireCv7tcqhTL_ "Container diagram for Internet Banking System")

C4-PlantUML combines the benefits of [PlantUML](http://en.plantuml.com/) and the [C4 model](https://c4model.com/) for providing a simple way of describing and communicate software architectures - especially during up-front design sessions - with an intuitive language using open source and platform independent tools.

C4-PlantUML includes macros, stereotypes, and other goodies (like VSCode Snippets) for creating C4 diagrams with PlantUML.

* [Getting Started](#getting-started)
* [Supported Diagram Types](#supported-diagram-types)
* [Snippets for Visual Studio Code](#snippets-for-visual-studio-code)
* [Layout Options](#layout-options)
* [Samples](#advanced-samples)
* [Background](#background)
* [License](#license)

## Getting Started

At the top of your C4 PlantUML `.puml` file, you need to include the `C4_Context.puml`, `C4_Container.puml` or `C4_Component.puml` file found in the `root` of this repo.

To be independent of any internet connectifity, you can also download the files found in the `root` and reference it locally with

```c#
!include path/to/C4.puml
!include path/to/C4_Context.puml
!include path/to/C4_Container.puml
!include path/to/C4_Component.puml
```

Just remember to change the `!include` statements inside the top of the files.

If you want to use the always up-to-date version in this repo, use the following:

```c#
!include https://raw.githubusercontent.com/scarrier/C4-PlantUML/latest/C4_Container.puml
```

Now let's create a C4 Container diagram:

After you have included `C4_Container.puml` you can use the defined macro definitions for the C4 elements: `Person`, `Person_Ext`, `System`, `System_Ext`, `System_3P`, `Container`, `Relationship`, `Boundary`, and `System_Boundary`

```csharp
@startuml C4_Elements
!include https://raw.githubusercontent.com/scarrier/C4-PlantUML/latest/C4_Container.puml

Person(personAlias, "Label", "Optional Description")
Container(containerAlias, "Label", "Technology", "Optional Description")
System(systemAlias, "Label", "Optional Description")

Rel(personAlias, containerAlias, "Label", "Optional Technology")
@enduml
```

![C4_Elements](https://www.plantuml.com/plantuml/png/ZOu_ImD14CNx_HJhLHVGsoQLLUIqYnZyKyjaC-GMPcUNcLaatzxZmA28akgzAURtVXir46kP_BX-Vo3CoARkAd6aTa0_cLMz3K7WOpWcczg-AKeiRCWsn9A3HX19A65St-m8sDuUju70K2tCoB6mGMAKeSuZpkrGj71VbxYZ17hjkotiaRgvF5LBXO7yFMgKj5pTofqXVVnglrvVCKvSg1nF_u1UJcgOUrtYqdNtZFHJ-6-BC-ARpifja0yjqoS0 "C4_Elements")

In addition to this, it is also possible to define a system or component boundary.

Take a look a look at the following sample of a C4 Container Diagram:

```csharp
@startuml Basic Sample
!include https://raw.githubusercontent.com/scarrier/C4-PlantUML/latest/C4_Container.puml

LAYOUT_WITH_LEGEND()

Person(admin, "Administrator")
System_Boundary(c1, "Sample System") {
    Container(web_app, "Web Application", "C#, ASP.NET Core 2.1 MVC", "Allows users to compare multiple Twitter timelines")
}
System_3P(twitter, "Twitter")

Rel(admin, web_app, "Uses", "HTTPS")
Rel(web_app, twitter, "Gets tweets from", "HTTPS")
@enduml
```

![Basic Sample](https://www.plantuml.com/plantuml/png/JOzFIyD04CNl-HHZlAHG4wgUF3KDeWShmQHwBDjaj0lxPzcP48hutPrGsxgNOUVzPkQz9R6AF5W3AqMwWqRPO32vqgupGu-mPmxqK1HHZVcNvlsm6mXZvnsZuxppjg1EnQWn5jNzJMsKuytwfJ2AaLXQsqfGfHt6FCYL9AanadUPwgrsSqZBgMhYgDZ7T9Oq1sAqsvKVNA_Y8UiM0XrDmL5BP_2TWBppvcp4tLQ58EG7xg0CmUXEiVOkbLPrFOUogVFNnrP68i9jle3rUpLffJ5-99WY4R07oHEK87OmhAUJxQYPCG9hYqPkaLZyEPcygpC-whBgZnGzUKDpodTnjY4PblhSjdKZr0ITrSkQ9sIIBqxbCthxVsI9hX-i-GK0 "Basic Sample")

## Supported Diagram Types

* System Context & System Landscape diagrams
  * Import: `!include https://raw.githubusercontent.com/scarrier/C4-PlantUML/latest/C4_Context.puml`
  * Macros: `Person`, `Person_Ext`, `System`, `System_Ext`, `System_3P`, `SystemDb`, `SystemDb_Ext`, `Boundary`, `System_Boundary`, `Enterprise_Boundary`
* Container diagram
  * Import: `!include https://raw.githubusercontent.com/scarrier/C4-PlantUML/latest/C4_Container.puml`
  * Additional Macros: `Container`, `ContainerDb`, `Container_Boundary`
* Component diagram
  * Import: `!include https://raw.githubusercontent.com/scarrier/C4-PlantUML/latest/C4_Component.puml`
  * Additional Macros: `Component`, `ComponentDb`
* Dynamic diagram
  * Import: `!include https://raw.githubusercontent.com/scarrier/C4-PlantUML/latest/C4_Dynamic.puml`
  * Additional Macros: `RelIndex`, `increment`, `setIndex`
* Deployment diagram
  * Import: `!include https://raw.githubusercontent.com/scarrier/C4-PlantUML/latest/C4_Deployment.puml`
  * Additional Macros: `Deployment_Node`

Take a look at each of the [C4 Model Diagram Samples](samples/C4CoreDiagrams.md).

## Snippets for Visual Studio Code

Because the PlantUML support inside of Visual Studio Code is excellent with the [PlantUML extension](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml), you can also find VS Code snippets for C4-PlantUML at [.vscode/C4.code-snippets](.vscode/C4.code-snippets).

![C4-PlantUML Snippets Video](images/vscode_c4plantuml_snippets.gif)

## Layout Options

C4-PlantUML also comes with some layout options to make it easy and reuseable to create nice and useful diagrams:

* [LAYOUT_TOP_DOWN() or LAYOUT_LEFT_RIGHT()](LayoutOptions.md#layout_top_down-or-layout_left_right)
* [LAYOUT_WITH_LEGEND()](LayoutOptions.md#layout_with_legend)
* [LAYOUT_AS_SKETCH()](LayoutOptions.md#layout_as_sketch)

## Advanced Samples

The following advanced samples are reproductions with C4-PlantUML from official [C4 model samples](https://c4model.com/#examples) created by [Simon Brown](http://simonbrown.je/).

The core diagram samples from [c4model.com](https://c4model.com/#coreDiagrams) are available [here](samples/C4CoreDiagrams.md).

### techtribes.js

Source: [C4_Container Diagram Sample - techtribesjs.puml](samples/C4_Container%20Diagram%20Sample%20-%20techtribesjs.puml)

![techtribesjs](https://www.plantuml.com/plantuml/png/ZLHDS-964BthLtIuBAvIODVEnbKvBJQElHly4Kk4oaaraXenpcX6cHaPKwdyz_ICX91CgbWEI7I_xdwlF_XYBDEsBWMCB6ORgtcAviMCWX-up4IT8soihSmlqwbcsqd1xQPEQuCwKzAYj9DCbLEJCQqvwkdrJpy-2IRjydun5SoYiMHAhWdAk4GzgQXEy05gIL4bHOFT8AoL46hBPG62GC1a3WCtruRU551L42fZGkmeHqVlk42mcFtvk8oJ-F4fcJ-k7iPdmOVMD8kIwBUR-FgERArfzJM-InOtjpSFSp86mHDgesHoysR7J2gvArLj4gSuXD5iRu0b6KPdBNZCYa9ZGOBp3jbPtaFpaajkh6QMAzd11zPzI13jZCKokLArp9dUZRDFONzC4vhJsJy1qCT_TNqORp5DM5KHUeKfpAfAyCod7f7f6tjb8KILTZs__-CwX5YLv8RBoPlppzmy33XgnZN-bUCMAbILm12QoY6qymy1N-b1XXULqZVQR09hhKgQNJikS8H3o3aj3nD-lbzZC9XPvKGEcS_JiKQHv2dnU4RXELFGd5cMCeEEtlqk-dq1doUV6xOHfK5pnCy_eSGo9HKRNf65YR_CUxufomi7l-Nshav1OwLQ5KVKncikqFY9KDbVwGSqyncvdxFuuhn7no3JsGQupF4DpV_9bChyBIZWGP4SBn1yh9UePA7cLt0-EH-8z8rzZgBfpDBB6Z4tC4w5Ae1eMtFccsktYDOSqw-hd5c_RSlcRRyBSEbGHWbqcpBg0DHKhRpei4qwx9Ehjjy3K18Oc6o3UIqm1neMTnp-xPRO7PJTSjjGY9itGlJSpRyBUPigGwUJQSXtHK-lBg3zE3hHm-BJ3HcdvIwEdoB24tfufwVXmriz6U9ZEdTlZLdUZiurRAkvQwrLBfH6F_qslw8Jh9IsS77nyMTADCWpsBf3hlSmlqv3H6-HjboZcwPLcH9jiVFBZvykMzh9ibkFKyG9nKwnxwSRy5zruezmNi29Tdsld4FMmyRTekqM6hXSArtwiVPknbVjJtIGwh2T11rcI5LjeQfJmJF8L8xDVN2hDCSJMVThxP9snrGRBWjtw9vST-p3L4xhWksIv-uVyz1gSdr1cTUb-0y0 "techtribesjs")


### Message Bus and Microservices

Source: [C4_Container Diagram Sample - message bus.puml](samples/C4_Container%20Diagram%20Sample%20-%20message%20bus.puml)

![messagebus](https://www.plantuml.com/plantuml/png/bLHVRzis47_NfxXv3qs1D6wBFUsfZcqixPpOjHm4Un9ErDacIf44IJbpXttt7ILRfHSLQFCGYQVZxy_zyGSVq8McLZ2goNlSKTduKVQBr48r5S4-1Ej_7uyTFj_iPDWt_9cSC3gG3ZV2r6Clq3b9RZpzxSrAeGwFzuknma0-SAYOSYfAJUx6Cals2XhDjsg-3M5Fi3LAcMUfTw0u2L1NSF5PEizl1fWLb16er94nUdal2JB_HMgB3cjuTcYVP1NsyFxjsoHUuz_tdTTSVgNsOxQO_BLyt1IRvQgOBPyUhbvdhqwXILxaVyutqpkEdK9F7pTtnMB-n_nXni4iMv7pHb-9nWTJaxk6QVysci0vFEBK_EW3rSMjQNI5xdWbtd7AEHi-wgrnDGPfzEWr_9Dbm7-zlokqDisUMAkawB8v_WaFw8MJDbp3HEyQXIw69x6-lXVXOp5hr6m-5bWwiCvifI9MTqdNsoaykOCKb7BdNUZCUmsvTR69jyQ46Dpi2QoHEe3P0Wf1tWDxwsM0JAo-O3vDOi6pnbYdNi5juoFq6ijIXllFBOr3xQrneGNdTAaZ4nr81_yIrr7CPPs9fVKvbdfQD-KnFgUEuY23ZbgLz5H1XG5RjXuCREEiyJH0Y4qbGq8sYUUKQFhh-EPXleclAsSEic8outQefMzhy-QPGn1XMgOj2gduTO1hLdvhM5MclPfXm19zoxTqA1J1k_SYdl9W7FaVQmhZzuuZGLgvbE7-c7zU9E1uBjvNgk10pZDuEnHAzGtxLbIiO6_4pzIMMPBAnbCad_C4zCTUI-8Fi3HDE4qAX3q6sEE1-9-rfAbYld-pR4qgsUfk_nwZ6dxURJQhdDDYKh7kbdDWPHujc_jEaI7wtqKmz4Sjhk5JldmONm0l1jQmqv6Jhdnlm4IK9ofp8xvGuDkjge7BoMxr8BssfXMRWBOu0oZ9gFNbxReekn-ZsUtqPE5ocmTMy0T5f33THlmKH8inmDw71grqrFzZIoUllz5nTNUo1HwBzH3R1H8dVc3TJQt-0m00 "messagebus")

## Background

[PlantUML](http://en.plantuml.com/) is an open source project that allows you to create UML diagrams.
Diagrams are defined using a simple and intuitive language.
Images can be generated in PNG, in SVG or in LaTeX format.

PlantUML was created to allow the drawing of UML diagrams, using a simple and human readable text description.
Because it does not prevent you from drawing inconsistent diagrams, it is a drawing tool and not a modeling tool.
It is the most used text-based diagram drawing tool with [extensive support into wikis and forums, text editors and IDEs, use by different programming languages and documentation generators](http://en.plantuml.com/running).

The [C4 model](https://c4model.com/) for software architecture is an "abstraction-first" approach to diagramming, based upon abstractions that reflect how software architects and developers think about and build software.
The small set of abstractions and diagram types makes the C4 model easy to learn and use.
C4 stands for context, containers, components, and code — a set of hierarchical diagrams that you can use to describe your software architecture at different zoom levels, each useful for different audiences.

The C4 model was created as a way to help software development teams describe and communicate software architecture, both during up-front design sessions and when retrospectively documenting an existing codebase.

More information can be found here:

* [The C4 model for software architecture](https://c4model.com/)
* [REAL WORLD PlantUML - Sample Gallery](https://real-world-plantuml.com/)
* [Visualising and documenting software architecture cheat sheets](http://www.codingthearchitecture.com/2017/04/27/visualising_and_documenting_software_architecture_cheat_sheets.html)
* [PlantUML and Structurizr - Create models not diagrams](http://www.codingthearchitecture.com/2016/12/08/plantuml_and_structurizr.html)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details