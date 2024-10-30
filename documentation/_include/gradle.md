This library is distributed via [maven central](https://central.sonatype.com/){:target="_blank"}.

Add dependencies like following to use this library inside your project.

=== "Dependencies"

    Simply add the dependencies inside your `build.gradle.kts` file.

    ```kotlin title="build.gradle.kts"

    val {{ project["library"]["name"] | lower }} = "<LATEST-VERSION>"
    {% for group in project["groups"] %}
    // {{ group["gradle-comment" ]}}
    {% for module in group["modules"] -%}
    implementation("{{ project["library"]["maven"] }}:{{ module }}:$lumberjack")
    {% endfor %}
    {%- endfor -%}
    ```

=== "Version Catalog"

    Define the dependencies inside your `libs.versions.toml` file.

    ```toml title="libs.versions.toml"
    [versions]

    {{ project["library"]["name"] | lower }} = "<LATEST-VERSION>"
    
    {%- set l1 = project["library"]["name"] | length -%}
    {%- set ns = namespace(maxLength=0) -%}
    {%- for group in project["groups"] -%}
      {%- for module in group["modules"] -%}   
        {%- set l2 = module | length -%}
        {%- if l2 > ns.maxLength -%}
          {%- set ns.maxLength = l2 -%}
        {%- endif -%}
      {%- endfor -%}
    {%- endfor -%}

    {%- set padding = ns.maxLength + l1 + 3 -%}
    {%- set padding2 = ns.maxLength + 4 + project["library"]["maven"] | length %}

    [libraries]
    {% for group in project["groups"] %}
    # {{ group["gradle-comment" ]}}
    {% for module in group["modules"] -%}
      {%- set name = project["library"]["name"] | lower ~ "-" ~ module ~ " =" -%}
      {%- set module2 = "\"" ~ project["library"]["maven"] ~ ":" ~ module ~ "\"," -%}
    {{ name.ljust(padding) }} { module = {{ module2.ljust(padding2) }} version.ref = "{{ project["library"]["name"] | lower }}" }
    {% endfor %}
    {%- endfor -%}
    ```

    And then use the definitions in your projects like following:

    ```kotlin title="build.gradle.kts"
    {% for group in project["groups"] %}
    # {{ group["gradle-comment" ]}}
    {% for module in group["modules"] -%}
    implementation(libs.{{ project["library"]["name"] | lower }}.{{ module | replace("-", ".") }})
    {% endfor %}
    {%- endfor -%}
    
    ```

    !!! info
        
        Of course you can define the dependencies in any `.toml` file if you want but then you have to add it to your project and adjust the `libs.` accodingly.