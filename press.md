---
lang: it
layout: page
title: Rassegna stampa emergenza
subtitle: Tutte le pubblicazioni che parlano di noi
permalink: /press/
---


<script src="//code.jquery.com/jquery-1.12.3.js"></script>
<script src="//cdn.datatables.net/1.10.12/js/jquery.dataTables.min.js"></script>
<script src="//cdn.datatables.net/plug-ins/1.10.12/sorting/date-eu.js"></script>

<script>
$(document).ready(function() {
  $('#press').dataTable({
    "pageLength": 300,
    "language": {
      "search": "Cerca: ",
      "info":           "Da _START_ a _END_ di un totale di _TOTAL_",
      "infoFiltered":   "(filtro su _MAX_ entità)",
      "infoEmpty":      "Nessun risultato"
    },
    "bPaginate": false,
    "bLengthChange": false,
    "order": [[ 0, "desc" ]],
    columnDefs: [
      { type: 'date-eu', targets: 0 }
    ]
  });
});
</script>


{: .table .table-striped #press}
Data            |Fonte                   |Titolo       |Link
:---------------|:-----------------------|:------------|:--------------
{% for member in site.data.press %} {{member.data | date: '%d/%m/%Y'}} | {{member.fonte}} | {{member.titolo}} | [Link]({{member.link}})
{% endfor %}


<div class="posts">
{% assign filteredposts = site.posts | where_exp: "post","post.categories contains 'press'"%}
  {% for post in filteredposts %}
      <article class="post">
        <h1><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h1>

        <div class="entry">
          {{ post.excerpt }}
        </div>

        <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Leggi Tutto</a>
      </article>
  {% endfor %}
</div>

