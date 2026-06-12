```{=html}
<div class="publications-list">
<%
  // Group items by year
  const byYear = {};
  for (const item of items) {
    const yr = item.year;
    if (!byYear[yr]) byYear[yr] = [];
    byYear[yr].push(item);
  }
  // Get years in descending order
  const years = Object.keys(byYear).sort((a, b) => b - a);
%>

<% for (const year of years) { %>
```
### <%= year %>
```{=html}
  <ul style="list-style-type: none; padding-left: 0;">
  <% for (const item of byYear[year]) { %>
    <li style="margin-bottom: 1em; padding-left: 2em; text-indent: -2em;">
      [<%= item.number %>] <%= item.authors %>, <%= item.title %>. <em><%= item.journal %></em><% if (item.volume) { %>, <%= item.volume %><% } %><% if (item.pages) { %>, <%= item.pages %><% } %><% if (item.note) { %> (<%= item.note %>)<% } %>.
      <% if (item.doi) { %><a href="https://doi.org/<%- item.doi %>">[DOI]</a><% } %>
      <% if (item.pdf) { %><a href="<%- item.pdf %>">[PDF]</a><% } %>
    </li>
  <% } %>
  </ul>
<% } %>

</div>
```
