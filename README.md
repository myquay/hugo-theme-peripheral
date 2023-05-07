# Peripheral
A fast, clean, Hugo theme with minimal dependencies. 

We've called it Peripheral because it is lightweight to reduce web-bloat introduced by the theme itself.

## Example


Source code: [https://github.com/myquay/hugo-theme-peripheral-example](https://github.com/myquay/hugo-theme-peripheral-example)

Life demo: [https://myquay.github.io/hugo-theme-peripheral-example/](https://myquay.github.io/hugo-theme-peripheral-example/)

<img width="1040" alt="image" src="https://user-images.githubusercontent.com/629527/236664180-2ec38fa1-ecad-4ea5-9966-c9e2ab79ab7c.png">

## Features
The theme is designed to be lean and to celebrate the content. Infact, if you turn off Google Analytics there will be no JavaScript running.

### Minimal dependencies
No large frameworks have been used, just one custom CSS style sheet. This is to make the theme as small as possible so your blog can be reached by the people on a wide range of connection types. It's ridiculous the amount of data you need to download to read a news article these days.

### Series
Related blog posts can be linked in a table to make it easier for readers to navigate though multiple related blog posts.

Series are configured using two settings in the page FrontMatter.


    series: multi-tenant
    concludeSeries: true


All posts in the same series linked so they can be easily traversed. 

<img width="1290" alt="image" src="https://user-images.githubusercontent.com/629527/236220134-23f337c1-161f-40a1-8e27-44fd81dff601.png">

For the last post set `concludeSeries` to true to disable the next post coming soon message.

### Obsolescence 
In a fast moving industry like tech, posts can become obsolete pretty quickly. This theme includes the ability to automatically put a note on older content to give the reader a heads up that this is older content.

<img width="1109" alt="image" src="https://user-images.githubusercontent.com/629527/236219847-d1e22b9a-7ad2-4488-99ee-4629709a408c.png">

This can be disabled on a post explicitly by setting the obsolescence feature in the post FrontMatter. 

    series: multi-tenant
    concludeSeries: true

### Git Integration 
If you're hosting your blog source code publicly you can encourage others to fix content by submitting a pull request or show the current commit of the website that has been pushed live.

<img width="1043" alt="image" src="https://user-images.githubusercontent.com/629527/236219256-a51a303c-f70e-4f0a-92e3-b289f6165c96.png">

To get the latest commit information displaying you will need to update the build server to update `config.toml` with the latest commit details.
    
## Installation

Install Hugo and create a new site. See [the Hugo documentation](https://gohugo.io/getting-started/quick-start/) for details.

Add Peripheral:

    $ git submodule add https://github.com/myquay/hugo-theme-peripheral.git themes/peripheral
    
Start Hugo:

    hugo serve
    
Update config.toml to use the new theme:

    themesDir = "themes"
    theme = "hugo-theme-peripheral"
    
## Configuration

There are both configuration for standard Hugo settings and theme specific settings. These are configured in your sites `config.toml` file.

### Settings: Basic
Basic settings configuration things like the site title, if you want the Git integrated features to activate ensure GitInfo is enabled.

    baseURL = "..."
    languageCode = "..."
    title = "..."
    themesDir = "themes"
    theme = "hugo-theme-peripheral"
    googleAnalytics = "..."
    enableGitInfo = true
    DefaultContentLanguage = "en"

Code blocks can be configured with the built in Syntax Highligther. JS is not used in this template where we can help it so either enable `noClasses` or output the CSS of the theme you'd like to your sites `assets/css` folder.

    [markup]
      [markup.highlight]
        anchorLineNos = false
        codeFences = true
        guessSyntax = true
        hl_Lines = ''
        lineAnchors = ''
        lineNoStart = 1
        lineNos = false
        lineNumbersInTable = true
        noClasses = false
        style = '...'
        tabWidth = 4
        
Generating CSS:

    hugo gen chromastyles --style=monokai > syntax.css

### Theme settings
The theme has several blocks of settings for each of the extra features it enables

#### Settings: General Theme

Basic settings for the theme

* **favicon:** Location of the favicon in relation to the static folder.
* **dateFormat:** Format of outputted timestamps.
* **subtitle:** Blog subtitle in the header.
* **location:** Author location, also used in the header.

Example:

    [Params.Peripheral]
        favicon = "favicon.png"
        dateFormat = "January 2, 2006"
        subtitle = "Blog subtitle"
        location = "Auckland, New Zealand"
        
#### Settings: Git Integration
These settings control the two git integrations on the theme.

1. The `Commit XYZ` message in the header which shows the version of the blog deployed and has a link to the changes in the last release
2. The submit a pull request message at the bottom of each blog post

* **enabled:** If the GIT settings are enabled or not.
* **repository:** The repository the blog is hosted at
* **abbreviatedHash:** The short commit hash
* **hash:** The full commit hash
* **subject:** The commit message
* **branch:** The branch which is deployed

 To work propery `enableGitInfo` in the standard settings must also be enabled.
 
Example:

    [Params.Peripheral.GitInfo]
        enabled = true
        repository = "..."
        abbreviatedHash = "{{AbbreviatedHash}}"
        hash = "{{Hash}}"
        subject = "{{Subject}}"
        branch = "main" 

#### Settings: Obsolescence 
These settings control the obsolescence feature in the theme.

* **enabled:** If the feature is enabled or not
* **years:** Posts older than this in years have the message displayed
* **message:** The message to display on old posts
 
Example:

    [Params.Peripheral.Obsolescence]
        enabled = true
        years = 3
        message = "This content is more than 3 years old. Please read this keeping its age in mind."
        
#### Settings: Series
These settings control the series feature in the theme.

* **enabled:** If the feature is enabled or not
* **showToBeContinued:** Show a next post is coming message on the table
 
Example:

    [Params.Peripheral.Series]
        enabled = true
        showToBeContinued = true
        
## About

This theme has minimal dependencies, on page load the following resources are requested

* Site CSS file (all CSS resources concatenated to a single file 
* Google Analytics, and subsequent events _(if enabled)_
* favicon

## License

MIT Licensed, see [LICENSE](https://github.com/myquay/hugo-theme-peripheral/blob/main/LICENSE).
