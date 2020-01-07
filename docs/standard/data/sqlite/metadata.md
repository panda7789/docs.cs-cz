---
title: Metadata
ms.date: 12/13/2019
description: Naučte se načítat metadata o databázi.
ms.openlocfilehash: b2f2704a748627d9943943fa2fa7b1b7e9f3007f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447193"
---
# <a name="metadata"></a>Metadata

Pro načtení metadat v ADO.NET jsou k dispozici dvě rozhraní API. Jedna načte metadata o výsledcích dotazu. Druhý načte metadata o schématu databáze.

## <a name="query-result-metadata"></a>Metadata výsledků dotazu

Metadata týkající se výsledků dotazu můžete načíst pomocí metody <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> v `SqliteDataReader`. Vrácený <xref:System.Data.DataTable> obsahuje následující sloupce:

| Sloupec             | Type    | Popis                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | Boolean | True, pokud sloupec zdroje může mít hodnotu NULL.                                    |
| `BaseCatalogName`  | String  | Název databáze zdrojového sloupce. Pro výrazy je vždycky NULL.    |
| `BaseColumnName`   | String  | Název zdrojového sloupce, který má nealias Pro výrazy je vždycky NULL.    |
| `BaseSchemaName`   | String  | Vždycky NULL. SQLite nepodporuje schémata.                              |
| `BaseServerName`   | String  | Cesta k souboru databáze zadaného v připojovacím řetězci.         |
| `BaseTableName`    | String  | Název tabulky počátečního sloupce Pro výrazy je vždycky NULL.       |
| `ColumnName`       | String  | Název nebo alias sloupce v sadě výsledků.                        |
| `ColumnOrdinal`    | Int32   | Pořadí sloupce v sadě výsledků.                              |
| `ColumnSize`       | Int32   | Always-1. To se může v budoucích verzích `Microsoft.Data.Sqlite`změnit.   |
| `DataType`         | Type    | Výchozí datový typ .NET sloupce.                                 |
| `DataTypeName`     | String  | Datový typ SQLite sloupce                                       |
| `IsAliased`        | Boolean | True, pokud je název sloupce v sadě výsledků uveden jako alias.                     |
| `IsAutoIncrement`  | Boolean | True, pokud byl zdrojový sloupec vytvořen pomocí klíčového slova AutoIncrement.     |
| `IsExpression`     | Boolean | True, pokud sloupec pochází z výrazu v dotazu.            |
| `IsKey`            | Boolean | True, pokud je zdrojový sloupec částí primárního klíče.                     |
| `IsUnique`         | Boolean | True, pokud je sloupec počátek jedinečný.                                      |
| `NumericPrecision` | Int16   | Vždycky NULL. To se může v budoucích verzích `Microsoft.Data.Sqlite`změnit. |
| `NumericScale`     | Int16   | Vždycky NULL. To se může v budoucích verzích `Microsoft.Data.Sqlite`změnit. |

Následující příklad ukazuje, jak použít `GetSchemaTable` k vytvoření řetězce ladění, který zobrazuje metadata o výsledku:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

Tento dotaz by například vytvořil následující řetězec pro ladění:

```sql
SELECT id AS post_id,
       title,
       body,
       random() AS random
FROM post
```

```output
post.id AS post_id INTEGER PRIMARY KEY AUTOINCREMENT
post.title TEXT NOT NULL UNIQUE
post.body TEXT
(expression) AS random BLOB
```

## <a name="schema-metadata"></a>Metadata schématu

Microsoft. data. sqlite neimplementuje metodu GetSchema pro DbConnection. Místo toho se můžete dotazovat přímo na informace o schématu pomocí [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) tabulky a příkazů PRAGMA jako [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) a [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).

Tento dotaz například načte metadata o všech sloupcích v databázi.

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a>Viz také:

* [Úložiště SQL Database schématu](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [PRAGMA – příkazy](https://www.sqlite.org/pragma.html)
* [Datové typy](types.md)
