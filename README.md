
<!-- README.md is generated from README.Rmd. Please edit that file -->
chradle
=======

WORK IN PROGRESS

A simple test harness for Chromium/Chrome, drive-able from R using a websocket connection.

It started out as an R6 class but all the asyc/promise craziness got to be too hard in that context, so now it's just a library of functions.

Installation
------------

``` r
devtools::install_github("milesmcbain/chradle")
```

Example
-------

``` r

session_state <-
  callr::r(function(){
  library(chradle)
  test_session <-
    chr_init(url = "http://localhost:8080",
             debug_port = 9222,
             bin = "chromium-browser"
             )

  session_state <-
    test_session %>%
    chr_call(get_attributes(id = "#block",
                            attribute = "material"))
  session_state
  })

session_state
```
