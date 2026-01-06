## 🔴 Tarefas Atrasadas

```dataview 
TASK FROM "/"
WHERE !completed AND contains(text, "📅") AND contains(text, "20") AND date(split(split(text, "📅")[1], " ")[1]) < date(today)
SORT date(split(split(text, "📅")[1], " ")[1]) ASC
```

## 📌 Tarefas para Hoje

```dataview
TASK FROM "/"
WHERE !completed AND contains(text, "📅") AND contains(text, "20") AND date(split(split(text, "📅")[1], " ")[1]) = date(today)
SORT text
```

## 📅 Tarefas da Próxima Semana

```dataview
TASK
FROM "/"
WHERE !completed AND contains(text, "📅") AND contains(text, "20") AND date(split(split(text, "📅")[1], " ")[1]) > date(today) AND date(split(split(text, "📅")[1], " ")[1]) <= date(today) + dur(7 days)
SORT date(split(split(text, "📅")[1], " ")[1]) ASC
```

## 🗓️ Todas as Tarefas Futuras

```dataview
TASK FROM "/" WHERE !completed AND contains(text, "📅") AND contains(text, "20") AND date(split(split(text, "📅")[1], " ")[1]) > date(today) 
SORT date(split(split(text, "📅")[1], " ")[1]) ASC
```