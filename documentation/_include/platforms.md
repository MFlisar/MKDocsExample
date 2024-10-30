## :material-laptop: Supported Platforms

This is a **KMP (kotlin multiplatform)** library and the provided modules do support following platforms.

<table>
  <tr>
    <th>Module</th>
    <th>Android</th>
    <th>iOS</th>
    <th>JVM</th>
    <th>Info</th>
  </tr>

  {% for group in project["groups"] %}

    <tr><td colspan="5" style="background-color:var(--md-primary-fg-color--light);">{{ group["label"] }}</td></tr>

    {% for module in project["modules"] %}
      {% if module["name"] is in group["modules"] %}
          
        <tr>
            <td><code>{{ module["name"] }}</code></td>
            <td>
              {% if module["platforms"]["android"] %}✔{% else %}-{% endif %}
            </td>
            <td>
              {% if module["platforms"]["ios"] %}✔{% else %}-{% endif %}
            </td>
            <td>
              {% if module["platforms"]["jvm"] %}✔{% else %}-{% endif %}
            </td>
            <td>
              {% if module["platforms"]["info"] is not none %}
              {{ module["platforms"]["info"] }}
              {% endif %}
            </td>
        </tr>
          
      {% endif %}
    {% endfor %}

  {% endfor %}

</table>