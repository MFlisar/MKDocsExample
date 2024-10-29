# Docs for Code Blocks

## Manual Code Block

```kotlin linenums="1"
val x = 0
```

## Manual Code Block with file name / title

```kotlin title="File.kt" linenums="1"
val x = 0
```

## File via embedding

``` title="library/Demo.kt" linenums="1"
--8<-- "library/Demo.kt"
```

## Lines from file via embedding

Only including lines 4-6:

``` title="library/Demo.kt" linenums="4"
--8<-- "library/Demo.kt:4:6"
```