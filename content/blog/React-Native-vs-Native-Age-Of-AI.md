---

external: false

draft: false

title: React Native vs Native Age Of AI

description: New way of approaching mobile development in age of AI

date: 2026-01-06

---

I have been developing mobile app since 2015 as an first iOS developer and then moved from Ionic, Cordova, Adobe Air and many others. I always loved developing apps for mobile. So lately I have been developing mobile apps by using React Native with "Bare flow" then using Expo. I think Expo leverage React Native development. It made it easy to develop and deploy by using EAS.

Developing mobile apps or software engineering in general are way faster thanks to LLM coding agents. Before the biggest reason why any organisation were choosing React Native were by having the "write once deploy everywhere" mentality meaning that your React Native code can work both iOS and Android. I think for a long time that was the case and it may still is. But I would like to challenge this idea.

When Apple introduced SwiftUI in 2019 and Jetpack Compose for Android in 2021 it was quite buggy and slow. Since then both frameworks improved a lot. You can write UIs way faster then previous equivalent UIKit and Android XML.  

So with that ability in hand, I believe we may not need to develop apps with React Native as much as before unless you have huge React human resource at hand. Both Swift and Kotlin looks very similar in terms of syntax. Below you can see how to define simple view model both Swift and Kotlin;


`````kotlin
import androidx.lifecycle.ViewModel
import kotlinx.coroutines.flow.MutableStateFlow
import kotlinx.coroutines.flow.asStateFlow

class CounterViewModel : ViewModel() {
    private val _count = MutableStateFlow(0)
    val count = _count.asStateFlow()

    fun increment() {
        _count.value++
    }
}
`````

```swift
import Foundation
import Observation

@Observable
class CounterViewModel {
    var count = 0

    func increment() {
        count += 1
    }
}
```

Even though there are some differences, it is not completely different. What I'm trying to point out here is that, the effort you put in those "write once, deploy everywhere" is kinda broken promise. You always have to deal with some platform specific configurations. In my last React Native project we had to integrate Adyen as a payment solution and in that we have to enable Apple Pay from entitlements and do some configuration for drop-in implementation. That means I have to do that UI changes in generated ios folder and since Expo's [CNG](https://docs.expo.dev/workflow/continuous-native-generation/) It regenerates the code every time you call `npx expo prebuild` and you have to do it in order to make newly added package work. You can maybe make it work by creating [Expo's Native Module](https://docs.expo.dev/modules/overview/) But still that is an *extra* work. Not the mention is that most of the third party frameworks are supports native by default.

# Security

I would also like to briefly mention security. As you might know that lately NPM had a big [Supply Chain Attack](https://www.trendmicro.com/en_us/research/25/i/npm-supply-chain-attack.html) you can also read in [Gitlab official blog](https://about.gitlab.com/blog/gitlab-discovers-widespread-npm-supply-chain-attack/). By choosing "efficiency" or "fast" whatever you call it, you compromise security and maybe reputation and at the end of the day extra "development work" meaning time. There might be a solution and practicalities you can do. Meaning that you have to put extra time on that as well.

# Suggestion

Don't get me wrong. I love React and it's ecosystem and I develop apps with React and React Native but I also love **solving problems**, **bring value the project or client** that I'm working on. Frameworks, programming languages just as a **tool** for me. So my suggestion would be to use agentic coding for your benefits by using little helpers such as `CLAUDE.md` or `subagents` for specific platforms. For example you could have **`claude/ios.md`** where you define list of requirements that AI would follow when adding new things into iOS code base and same for **`claude/android`** as well. You can expand this and **`claude/shared-features.md`** where you can define certain must-haves that AI could follow when generating new code in both platforms.