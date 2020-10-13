<h1 align="center">
  Networkism
</h1>

<p align="center">
  <img src="https://images.unsplash.com/photo-1599140782241-144735f5949a?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=900&q=80"/>
</p>

<p align="center">
  <a href="LICENSE"><img alt="License" src="https://img.shields.io/badge/License-Apache%202.0-blue.svg"></a>
  <a href="https://github.com/utsmannn/networkism/pulls"><img alt="Pull request" src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat"></a>
  <a href="https://developer.android.com/kotlin"><img alt="Fcm docs" src="https://img.shields.io/badge/Kotlin-Coroutine-orange?logo=kotlin&style=flat"></a>
  <a href="https://twitter.com/utsmannn"><img alt="Twitter" src="https://img.shields.io/twitter/follow/utsmannn"></a>
  <a href="https://github.com/utsmannn"><img alt="Github" src="https://img.shields.io/github/followers/utsmannn?label=follow&style=social"></a>
  <h3 align="center">The simple of network observer changes</h3>
</p>

### Prerequisite
```groovy
implementation 'org.jetbrains.kotlinx:kotlinx-coroutines-android:latest-version'
implementation 'androidx.lifecycle:lifecycle-runtime-ktx:latest-version'
```

### Download
```groovy
// uploading...
```

### API support
| result param | lollipop or newer | pre lollipop | value | desc |
| --- | --- | --- | --- | --- |
| `NetworkismResult.isConnected` | yes | yes | `boolean` | the value of network available |
| `NetworkismResult.Counter` | yes | no | `object` | model of Kbps counter |
| `NetworkismResult.Counter.downKbps` | yes | no | `Int` | current down stream bandwidth |
| `NetworkismResult.Counter.upKbps` | yes | no | `Int` | current up stream bandwidth |

### Usage
The Networkism use coroutine flow and cast to liveData with coroutineContext for lifecycle aware of activity or fragment

#### Simple usage
```kotlin
Networkism.observer(application, lifecycleScope).observe(this, { result
    if (result.isConnected) {
        // network available
    } else {
        // network lost
    }
})
```

#### Bind to listener
```kotlin

// extend activity/fragment to `NetworkListener`
class MainActivity : AppCompatActivity(), NetworkismListener {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // init lifecycle scope from 'androidx.lifecycle:lifecycle-runtime-ktx'
        Networkism(this).init(lifecycleScope)
    }

    override fun connectivityAvailable(counter: NetworkismResult.Counter?) {
        // view for connection available
        txt_log.text = "connect"
    }

    override fun connectivityLost() {
        // view for disconnect
        txt_log.text = "disconnect"
    }
}
```

#### Use dependencies injection
Create single instance of Networkism is **recommended**, see sample of manual dependencies

---

```
Copyright 2020 Muhammad Utsman

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

```