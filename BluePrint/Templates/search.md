---
banner: "[[<%tp.file.title%>]]"
content-start: 150
banner-display: cover
banner-height: 1500
banner-fade: -500
cssclasses:
  - cards
  - cards-2-3
  - cards-cover
  - table-max
tags:
  - <%tp.file.title%>
limit: "100"
title: "1"
---

<hr>

```dataviewjs
const tags = dv.current().tags;
const limit = dv.current().limit || 10;
const showTitle = dv.current().title == 1;

if (tags && tags.length > 0) {
    const tagQuery = tags.map(tag => `#${tag}`).join(" and ") + ' and -"Templates" and -"/Search"';
    const results = dv.pages(tagQuery).slice(0, limit);

    const headers = showTitle ? ["Poster", "Title", "Status"] : ["Poster"];
    const rows = results.map(p => {
        const trimmedTitle = p.file.name.length > 20 ? p.file.name.slice(0, 17) + "..." : p.file.name;
        return showTitle ? [p.poster, `[[${p.file.path}|${trimmedTitle}]]`, p.status] : [p.poster];
    });

    dv.table(headers, rows);
}
```