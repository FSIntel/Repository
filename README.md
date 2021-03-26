<p align="center">
 <img height="120" src="https://fsin.tel/application/images/logo-v2.png">
</p>

# Repository
An example package repository for creating FSPM packages with examples of pre-installing data using FSIntel's FSPM application.
We will also cover how encryption keys can used to verify ownership, and the basic structure &amp; requirements 
to create a Repository on FSPM. **Please note:** You must be a _verified_ author by FSIntel to create
paid packages. This isn't a difficult proceedure; in fact, we've got a platform for you to get started
straight away. 

Simply create an account at [FSPM](), then follow the [Onboarding Developers &amp; Creators]() steps
to get you going. This will allow you to ready up [Repositories]() and [Product Pages]() instantly
before our team process your application. Once you've been approved, your [Product Pages]() will go
live subject to internal checks from FSIntel staff.

## Requirements
To create a package ready to push to your FSPM Repository, you must:

 1. Create a mandatory `fspm.json` file in the root of your Add-On.
 2. Ensure all Add-On files are in a subfolder named `addon`
 3. Zip your package (using `.zip` compression only) ([Filename Convention](#NamingConvention))

Your package should _only_ contain the following **file** and **directory**:

(Structure here)

## 1. [fspm.json Properties](#FSPMJsonProps)

An `fspm.json` is a file that is necessary to build package metadata &mdash; not just
for our benefit, but the benefit of reachability and exposure for you as a 
creator and author. Whilst we have mandatory properties in order to publish
Add-Ons through FSPM, there are a few that help further enrich your pakcages.

### Required Properties

Each **required** property must **only** contain lowercase letters, numbers and hyphens.
No spaces, dots, or any other symbol will be accepted.

```json5
{
    // Must match the Repository name in your FSPM account
    "name"    : "fbw-airbus-a380-liveries",
    // Must be your registered FSPM author name
    "author"  : "fsintel",
    // Must contain a valid package type
    "type"    : "liveries",
    // Semver versioning methodology: <Major.Minor.Hotfix>
    "version" : "1.0.0",
    // The Repository URL
    "repository": "fspm://@fsintel/{name}"
}
```

### Full fspm.json Property List
| Key | Description | Required |
| ---------------|----------------|----------------|
| **name** | The name of the Repository created in your FSPM account | true
| **type** | A valid Add-On type ([See Valid Types](#ValidTypes)) | true

### Additional Recognised Properties

`fspm.json`

```json5
{
    // Required
    "name"        : "fbw-airbus-a380-liveries",
    "author"      : "fsintel",
    "type"        : "liveries",
    "version"     : "1.0.0",
    "description" : "A selection of FlyByWire Airbus A380 Liveries",
    "install"     : {
        "game"    : "msfs2020",
        "version" : "latest"
    },
    
    // Recommended packages from FSPM's repository
    // If a paid add-on, it will link to the package
    // with buy options included on this package.
    // Handy way to help budding authors or even your
    // own authored packages to help boost visibility.
    // There are certain flags that you can include
    // if the package you're creating depends on another:
    //
    // [1] Required: if `true`, you can only purchase it with
    //               the recommended package.
    "requirements": {
        "@flybywire.airbus-a380" : {
            "min-version": "release", // or a specific version, i.e., `1.2.12`
            "required": true          // or `false`
        }   
    }
}
```

`fspm.config.json`


## 2. [How to Name Your Release](#NamingConvention)

For ensuring consistency, we use a simple naming convention. If you're planning to host
packages with us directly, the following naming convention is necessary. **Please** check this
thoroughly before submitting or it will get rejected _automatically_ if the `fspm.json` contents do not match
the package's filename **and** the [Repository]() values associated with it. 

We _could_ rename this ourselves based on the contents of the `fspm.json` (as asked many times),
but this process is part of our [Integrity Checklist]() (_or how we refer commonly to it as "[ICL]()"_) to ensure consistency in our [Marketplace]() and 
[FSPM App](). If you are unsure about what this means, please read our [Marketplace & Package Integrity, Intervention & Safety]() 
&mdash; something you will agree to as part of the terms during registering to become an author on FSPM and FSIntel respectively.


### Naming Requirements
**Name your packages exactly like this:**

`@<fspm-author>.<repository-type>.<repository-slug>.<package-version>`

**For example:**
1. `<author>` is your registered FSPM company/brand name, i.e., `@fsintel`
2. `<type>` is the Repository _type_, i.e., `aircraft`, etc. ([Valid Types](https://google.com))
3. `<slug>` is the Repository _slug_, i.e., `fbw-airbus-a380-liveries`
4. `<version>` is your proposed release version using SemVer ([How to Version Packages](https://google.com))

Simply:

1. No capital letters, symbols or spaces. 
2. Only lowercase, and must only use alphanumeric values.
3. You can only use hyphens to split words and fullstops between `author`, `type`, `slug` and `version`.
4. Must be in English.

Let's imagine we are releasing a hotfix for our Add-On &mdash; an Airbus A380 Selection of Liveries. The final `.zip` package name would be:

`@fsintel.liveries.fbw-airbus-a380-livery-pack.1.2.12.zip`

Which, your `fspm.json` must have like the following:

```json5
{
    "author"  : "fsintel",
    "type"    : "liveries",
    "name"    : "fbw-airbus-a380-liveries",
    "version" : "1.2.12"
}
```
