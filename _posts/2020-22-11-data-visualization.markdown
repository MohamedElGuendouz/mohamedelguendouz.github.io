---
layout: post
title: "Data Visualization"
date: 2020-22-11 14:30:00 +0000
description: "CNN, RNN, DEEP LEARNING ?"
tags: [Machine Learning,Python,Model,swift,SwiftUI,Combine,design,pattern,redux,unidirectional,data,flow,model,state,management]
comments: true
sharing: true
published: true
img: clean_swiftui_01.jpg
---
Can you imagine, UIKit is 11 years old! Ever since the release of the iOS SDK in 2008 we were building our apps with it. And throughout this time the developers were in a relentless search for the best architecture to use for their apps. It all started with **MVC**, but later we witnessed the rise of **MVP**, **MVVM**, **VIPER**, **RIBs**, and **VIP**.


**Model**: a data container

```swift
struct Country {
    let name: String
}
```

**View**: a SwiftUI view

```swift
struct CountriesList: View {
    
    @ObservedObject var viewModel: ViewModel
    
    var body: some View {
        List(viewModel.countries) { country in
            Text(country.name)
        }
        .onAppear {
            self.viewModel.loadCountries()
        }
    }
}
```

**ViewModel**: an `ObservableObject` that encapsulates the business logic and allows the `View` to observe changes of the state

Since WebRepository takes URLSession as a constructor parameter, it is very easy to test it by [mocking the networking calls](https://github.com/nalexn/clean-architecture-swiftui/blob/master/UnitTests/NetworkMocking/RequestMocking.swift) with a custom `URLProtocol`

# Final thoughts

[The demo project](https://github.com/nalexn/clean-architecture-swiftui) now has **97% test coverage**, all thanks to the Clean Architecture's "dependency rule" and segregation of the app on multiple layers.

It offers fully setup persistence layer with CoreData, deep linking from a Push Notification, and other non-trivial yet practical examples.

<div style="max-width:800px; display: block; margin-left: auto; margin-right: auto;"><img src="https://github.com/nalexn/blob_files/blob/master/images/countries_preview.png?raw=true" alt="Diagram"/></div>