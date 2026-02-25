## 🔴 Delayed tasks

```dataview 
TASK FROM "/"
WHERE !completed AND contains(text, "📅") AND contains(text, "20") AND date(split(split(text, "📅")[1], " ")[1]) < date(today)
SORT date(split(split(text, "📅")[1], " ")[1]) ASC
```

## 📌 Today tasks

```dataview
TASK FROM "/"
WHERE !completed AND contains(text, "📅") AND contains(text, "20") AND date(split(split(text, "📅")[1], " ")[1]) = date(today)
SORT text
```

## 📅 Next week tasks

```dataview
TASK
FROM "/"
WHERE !completed AND contains(text, "📅") AND contains(text, "20") AND date(split(split(text, "📅")[1], " ")[1]) > date(today) AND date(split(split(text, "📅")[1], " ")[1]) <= date(today) + dur(7 days)
SORT date(split(split(text, "📅")[1], " ")[1]) ASC
```

## 🗓️ All future tasks

```dataview
TASK FROM "/" WHERE !completed AND contains(text, "📅") AND contains(text, "20") AND date(split(split(text, "📅")[1], " ")[1]) > date(today) 
SORT date(split(split(text, "📅")[1], " ")[1]) ASC
```