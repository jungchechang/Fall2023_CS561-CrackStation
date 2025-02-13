# CrackStation, a Decrypter implementation
A decrypter can decrypt any three-character(including "!?") password, which uses sha1 or sha256 to encrypt.

## Overview
This decrypter can decrypt unsalted hashes passwords of less than three characters, and it uses a large lookup table to find the password.

## Mission Statement
This library helps people know that unsalted Hash is unreliable. People can try to decrypt unsalted hash passwords which are less than three characters with this library.

## Installation
**Swift Package Manager**

The [Swift Package Manager](https://www.swift.org/package-manager/) is "a tool for managing the distribution of Swift code. It's integrated with the Swift build system to automate the process of downloading, compiling, and linking dependencies."

Once you have your Swift package set up, and add CrackStation to the list of dependencies in your in your `Package.swift` file:
```
dependencies: [
        .package(url: "git@github.com:JungCheChang/CrackStation.git", from: "1.1.7"),
    ]
```


## Usage

### The API
`init` will load the .json file for SHA1 and SHA256
```
    required public init() {
        do{
            lookupTable =  try CrackStation.loadDictionaryFromDisk()
        }
        catch{
            lookupTable = ["":""]
        }
    }
```

`decrypt` The function has one parameter, ShaHash and it will return the password corresponding to the ShaHash.
```
public func decrypt(shaHash: String) -> String?
```
### An example
```
import CrackStation
let password = CrackStation().decrypt(shaHash:  "356a192b7913b04c54574d18c28d46e6395428ab")
XCTAssertEqual("1", password)
```

## Author
Jung-Che Chang
