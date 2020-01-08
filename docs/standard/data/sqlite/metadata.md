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
# <a name="metadata"></a><span data-ttu-id="763d0-103">Metadata</span><span class="sxs-lookup"><span data-stu-id="763d0-103">Metadata</span></span>

<span data-ttu-id="763d0-104">Pro načtení metadat v ADO.NET jsou k dispozici dvě rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="763d0-104">There are two APIs for retrieving metadata in ADO.NET.</span></span> <span data-ttu-id="763d0-105">Jedna načte metadata o výsledcích dotazu.</span><span class="sxs-lookup"><span data-stu-id="763d0-105">One retrieves metadata about query results.</span></span> <span data-ttu-id="763d0-106">Druhý načte metadata o schématu databáze.</span><span class="sxs-lookup"><span data-stu-id="763d0-106">The other retrieves metadata about the database schema.</span></span>

## <a name="query-result-metadata"></a><span data-ttu-id="763d0-107">Metadata výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="763d0-107">Query result metadata</span></span>

<span data-ttu-id="763d0-108">Metadata týkající se výsledků dotazu můžete načíst pomocí metody <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> v `SqliteDataReader`.</span><span class="sxs-lookup"><span data-stu-id="763d0-108">You can retrieve metadata about the results of a query using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method on `SqliteDataReader`.</span></span> <span data-ttu-id="763d0-109">Vrácený <xref:System.Data.DataTable> obsahuje následující sloupce:</span><span class="sxs-lookup"><span data-stu-id="763d0-109">The returned <xref:System.Data.DataTable> contains the following columns:</span></span>

| <span data-ttu-id="763d0-110">Sloupec</span><span class="sxs-lookup"><span data-stu-id="763d0-110">Column</span></span>             | <span data-ttu-id="763d0-111">Type</span><span class="sxs-lookup"><span data-stu-id="763d0-111">Type</span></span>    | <span data-ttu-id="763d0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="763d0-112">Description</span></span>                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | <span data-ttu-id="763d0-113">Boolean</span><span class="sxs-lookup"><span data-stu-id="763d0-113">Boolean</span></span> | <span data-ttu-id="763d0-114">True, pokud sloupec zdroje může mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="763d0-114">True if the origin column may be NULL.</span></span>                                    |
| `BaseCatalogName`  | <span data-ttu-id="763d0-115">String</span><span class="sxs-lookup"><span data-stu-id="763d0-115">String</span></span>  | <span data-ttu-id="763d0-116">Název databáze zdrojového sloupce.</span><span class="sxs-lookup"><span data-stu-id="763d0-116">The name of the origin column's database.</span></span> <span data-ttu-id="763d0-117">Pro výrazy je vždycky NULL.</span><span class="sxs-lookup"><span data-stu-id="763d0-117">Always NULL for expressions.</span></span>    |
| `BaseColumnName`   | <span data-ttu-id="763d0-118">String</span><span class="sxs-lookup"><span data-stu-id="763d0-118">String</span></span>  | <span data-ttu-id="763d0-119">Název zdrojového sloupce, který má nealias</span><span class="sxs-lookup"><span data-stu-id="763d0-119">The unaliased name of the origin column.</span></span> <span data-ttu-id="763d0-120">Pro výrazy je vždycky NULL.</span><span class="sxs-lookup"><span data-stu-id="763d0-120">Always NULL for expressions.</span></span>    |
| `BaseSchemaName`   | <span data-ttu-id="763d0-121">String</span><span class="sxs-lookup"><span data-stu-id="763d0-121">String</span></span>  | <span data-ttu-id="763d0-122">Vždycky NULL.</span><span class="sxs-lookup"><span data-stu-id="763d0-122">Always NULL.</span></span> <span data-ttu-id="763d0-123">SQLite nepodporuje schémata.</span><span class="sxs-lookup"><span data-stu-id="763d0-123">SQLite doesn't support schemas.</span></span>                              |
| `BaseServerName`   | <span data-ttu-id="763d0-124">String</span><span class="sxs-lookup"><span data-stu-id="763d0-124">String</span></span>  | <span data-ttu-id="763d0-125">Cesta k souboru databáze zadaného v připojovacím řetězci.</span><span class="sxs-lookup"><span data-stu-id="763d0-125">The path to the database file specified in the connection string.</span></span>         |
| `BaseTableName`    | <span data-ttu-id="763d0-126">String</span><span class="sxs-lookup"><span data-stu-id="763d0-126">String</span></span>  | <span data-ttu-id="763d0-127">Název tabulky počátečního sloupce</span><span class="sxs-lookup"><span data-stu-id="763d0-127">The name of the origin column's table.</span></span> <span data-ttu-id="763d0-128">Pro výrazy je vždycky NULL.</span><span class="sxs-lookup"><span data-stu-id="763d0-128">Always NULL for expressions.</span></span>       |
| `ColumnName`       | <span data-ttu-id="763d0-129">String</span><span class="sxs-lookup"><span data-stu-id="763d0-129">String</span></span>  | <span data-ttu-id="763d0-130">Název nebo alias sloupce v sadě výsledků.</span><span class="sxs-lookup"><span data-stu-id="763d0-130">The name or alias of the column in the result set.</span></span>                        |
| `ColumnOrdinal`    | <span data-ttu-id="763d0-131">Int32</span><span class="sxs-lookup"><span data-stu-id="763d0-131">Int32</span></span>   | <span data-ttu-id="763d0-132">Pořadí sloupce v sadě výsledků.</span><span class="sxs-lookup"><span data-stu-id="763d0-132">The ordinal of the column in the result set.</span></span>                              |
| `ColumnSize`       | <span data-ttu-id="763d0-133">Int32</span><span class="sxs-lookup"><span data-stu-id="763d0-133">Int32</span></span>   | <span data-ttu-id="763d0-134">Always-1.</span><span class="sxs-lookup"><span data-stu-id="763d0-134">Always -1.</span></span> <span data-ttu-id="763d0-135">To se může v budoucích verzích `Microsoft.Data.Sqlite`změnit.</span><span class="sxs-lookup"><span data-stu-id="763d0-135">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span>   |
| `DataType`         | <span data-ttu-id="763d0-136">Type</span><span class="sxs-lookup"><span data-stu-id="763d0-136">Type</span></span>    | <span data-ttu-id="763d0-137">Výchozí datový typ .NET sloupce.</span><span class="sxs-lookup"><span data-stu-id="763d0-137">The default .NET data type of the column.</span></span>                                 |
| `DataTypeName`     | <span data-ttu-id="763d0-138">String</span><span class="sxs-lookup"><span data-stu-id="763d0-138">String</span></span>  | <span data-ttu-id="763d0-139">Datový typ SQLite sloupce</span><span class="sxs-lookup"><span data-stu-id="763d0-139">The SQLite data type of the column.</span></span>                                       |
| `IsAliased`        | <span data-ttu-id="763d0-140">Boolean</span><span class="sxs-lookup"><span data-stu-id="763d0-140">Boolean</span></span> | <span data-ttu-id="763d0-141">True, pokud je název sloupce v sadě výsledků uveden jako alias.</span><span class="sxs-lookup"><span data-stu-id="763d0-141">True if the column name is aliased in the result set.</span></span>                     |
| `IsAutoIncrement`  | <span data-ttu-id="763d0-142">Boolean</span><span class="sxs-lookup"><span data-stu-id="763d0-142">Boolean</span></span> | <span data-ttu-id="763d0-143">True, pokud byl zdrojový sloupec vytvořen pomocí klíčového slova AutoIncrement.</span><span class="sxs-lookup"><span data-stu-id="763d0-143">True if the origin column was created with the AUTOINCREMENT keyword.</span></span>     |
| `IsExpression`     | <span data-ttu-id="763d0-144">Boolean</span><span class="sxs-lookup"><span data-stu-id="763d0-144">Boolean</span></span> | <span data-ttu-id="763d0-145">True, pokud sloupec pochází z výrazu v dotazu.</span><span class="sxs-lookup"><span data-stu-id="763d0-145">True if the column originates from an expression in the query.</span></span>            |
| `IsKey`            | <span data-ttu-id="763d0-146">Boolean</span><span class="sxs-lookup"><span data-stu-id="763d0-146">Boolean</span></span> | <span data-ttu-id="763d0-147">True, pokud je zdrojový sloupec částí primárního klíče.</span><span class="sxs-lookup"><span data-stu-id="763d0-147">True if the origin column is part of the PRIMARY KEY.</span></span>                     |
| `IsUnique`         | <span data-ttu-id="763d0-148">Boolean</span><span class="sxs-lookup"><span data-stu-id="763d0-148">Boolean</span></span> | <span data-ttu-id="763d0-149">True, pokud je sloupec počátek jedinečný.</span><span class="sxs-lookup"><span data-stu-id="763d0-149">True if the origin column is UNIQUE.</span></span>                                      |
| `NumericPrecision` | <span data-ttu-id="763d0-150">Int16</span><span class="sxs-lookup"><span data-stu-id="763d0-150">Int16</span></span>   | <span data-ttu-id="763d0-151">Vždycky NULL.</span><span class="sxs-lookup"><span data-stu-id="763d0-151">Always NULL.</span></span> <span data-ttu-id="763d0-152">To se může v budoucích verzích `Microsoft.Data.Sqlite`změnit.</span><span class="sxs-lookup"><span data-stu-id="763d0-152">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |
| `NumericScale`     | <span data-ttu-id="763d0-153">Int16</span><span class="sxs-lookup"><span data-stu-id="763d0-153">Int16</span></span>   | <span data-ttu-id="763d0-154">Vždycky NULL.</span><span class="sxs-lookup"><span data-stu-id="763d0-154">Always NULL.</span></span> <span data-ttu-id="763d0-155">To se může v budoucích verzích `Microsoft.Data.Sqlite`změnit.</span><span class="sxs-lookup"><span data-stu-id="763d0-155">This may change in future versions of `Microsoft.Data.Sqlite`.</span></span> |

<span data-ttu-id="763d0-156">Následující příklad ukazuje, jak použít `GetSchemaTable` k vytvoření řetězce ladění, který zobrazuje metadata o výsledku:</span><span class="sxs-lookup"><span data-stu-id="763d0-156">The following example shows how to use `GetSchemaTable` to create a debug string that shows metadata about a result:</span></span>

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

<span data-ttu-id="763d0-157">Tento dotaz by například vytvořil následující řetězec pro ladění:</span><span class="sxs-lookup"><span data-stu-id="763d0-157">For example, this query would produce the following debug string:</span></span>

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

## <a name="schema-metadata"></a><span data-ttu-id="763d0-158">Metadata schématu</span><span class="sxs-lookup"><span data-stu-id="763d0-158">Schema metadata</span></span>

<span data-ttu-id="763d0-159">Microsoft. data. sqlite neimplementuje metodu GetSchema pro DbConnection.</span><span class="sxs-lookup"><span data-stu-id="763d0-159">Microsoft.Data.Sqlite doesn't implement the GetSchema method on DbConnection.</span></span> <span data-ttu-id="763d0-160">Místo toho se můžete dotazovat přímo na informace o schématu pomocí [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) tabulky a příkazů PRAGMA jako [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) a [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span><span class="sxs-lookup"><span data-stu-id="763d0-160">Instead, you can query directly for schema information using the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and PRAGMA statements like [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) and [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).</span></span>

<span data-ttu-id="763d0-161">Tento dotaz například načte metadata o všech sloupcích v databázi.</span><span class="sxs-lookup"><span data-stu-id="763d0-161">For example, this query will retrieve metadata about all the columns in the database.</span></span>

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a><span data-ttu-id="763d0-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="763d0-162">See also</span></span>

* [<span data-ttu-id="763d0-163">Úložiště SQL Database schématu</span><span class="sxs-lookup"><span data-stu-id="763d0-163">Storage of the SQL Database Schema</span></span>](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [<span data-ttu-id="763d0-164">PRAGMA – příkazy</span><span class="sxs-lookup"><span data-stu-id="763d0-164">PRAGMA Statements</span></span>](https://www.sqlite.org/pragma.html)
* [<span data-ttu-id="763d0-165">Datové typy</span><span class="sxs-lookup"><span data-stu-id="763d0-165">Data types</span></span>](types.md)
