{% if project["dependencies"]["compose"] is defined %}

## Compose

|      Dependency       | Version |                     Infos                      |
|:---------------------:|:-------:|:----------------------------------------------:|
| Compose Multiplatform | `{{ project["dependencies"]["compose"]["cmp"] }}` | Uses compose `{{ project["dependencies"]["compose"]["compose"] }}` and material3 `{{ project["dependencies"]["compose"]["material3"] }}` |

{% if project["dependencies"]["compose"]["experimantal"] %}
!!! warning

    I try to use as few experimental APIs as possible, but this library does use a few experimental APIs which are still marked as experimental in material3 `1.3.0`. I will provide new versions as soon as possible if experimental APIs change or become stable.

{% endif %}

{% endif %}

## Modules

<table>
  <tr>
    <th>Module</th>
    <th>Dependency</th>
    <th>Version</th>
  </tr>

  {% for group in project["groups"] %}

    <tr><td colspan="3" style="background-color:var(--md-primary-fg-color--light);">{{ group["label"] }}</td></tr>

    {% for module in project["modules"] %}
      {% if module["name"] is in group["modules"] %}
          
        <tr>
          <td><code>{{ module["name"] }}</code></td>

          {% if module["dependencies"]|length > 0 %}
            <td>
              {% for d in module["dependencies"] %}
              <a href={{ d["link"] }} target="_blank">{{ d["name"] }}</a><br>
              {% endfor %}
            </td>
            <td>
              {% for d in module["dependencies"] %}
              <code>{{ d["version"] }}</code><br>
              {% endfor %}
            </td>
          {% else %}
            <td>-</td>
            <td></td>
          {% endif %}
        </tr>
          
      {% endif %}
    {% endfor %}

  {% endfor %}

</table>