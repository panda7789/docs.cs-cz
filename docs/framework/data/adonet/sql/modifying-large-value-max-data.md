---
title: Úpravy velké hodnotu (maximální) dat v ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: ea079a0b55dde8df7b3442f3d604b2b6467ba785
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584328"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="79409-102">Úpravy velké hodnotu (maximální) dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="79409-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="79409-103">Rozsáhlého objektu (LOB) datové typy jsou ty, které překračují maximální velikost řádku 8 kilobajtů (KB).</span><span class="sxs-lookup"><span data-stu-id="79409-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="79409-104">SQL Server poskytuje `max` specifikátor pro `varchar`, `nvarchar`, a `varbinary` datové typy, aby umožňovala ukládání hodnoty větší než 2 ^ 32 bajtů.</span><span class="sxs-lookup"><span data-stu-id="79409-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="79409-105">Zadat sloupce tabulky a proměnných jazyka Transact-SQL `varchar(max)`, `nvarchar(max)`, nebo `varbinary(max)` datové typy.</span><span class="sxs-lookup"><span data-stu-id="79409-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="79409-106">V ADO.NET `max` datové typy lze načíst pomocí `DataReader`a je taky možné specifikovat jako obě hodnoty vstupní a výstupní parametr bez žádným zvláštním způsobem.</span><span class="sxs-lookup"><span data-stu-id="79409-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="79409-107">Pro velké `varchar` datové typy dat, dají se načíst a přírůstkově aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="79409-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="79409-108">`max` Datových typů lze použít pro porovnání, jako proměnné jazyka Transact-SQL a pro zřetězení.</span><span class="sxs-lookup"><span data-stu-id="79409-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="79409-109">Také je možné použít v DISTINCT, ORDER BY, klauzule GROUP BY příkazu SELECT, stejně jako v agregace, spojení a poddotazy.</span><span class="sxs-lookup"><span data-stu-id="79409-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="79409-110">Následující tabulka obsahuje odkazy na dokumentaci SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="79409-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="79409-111">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="79409-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="79409-112">Použití vysoké hodnoty datových typů</span><span class="sxs-lookup"><span data-stu-id="79409-112">Using Large-Value Data Types</span></span>](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="79409-113">Typ velké hodnoty omezení</span><span class="sxs-lookup"><span data-stu-id="79409-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="79409-114">Následující omezení platí pro `max` datové typy, které neexistují pro menší datové typy:</span><span class="sxs-lookup"><span data-stu-id="79409-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
-   <span data-ttu-id="79409-115">A `sql_variant` nemůže obsahovat velké `varchar` datového typu.</span><span class="sxs-lookup"><span data-stu-id="79409-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
-   <span data-ttu-id="79409-116">Velké `varchar` sloupců nemůže být určen jako klíčový sloupec v indexu.</span><span class="sxs-lookup"><span data-stu-id="79409-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="79409-117">Můžou v zahrnutý sloupec v neclusterovaný index.</span><span class="sxs-lookup"><span data-stu-id="79409-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
-   <span data-ttu-id="79409-118">Velké `varchar` sloupce nelze použít jako dělení klíčových sloupců.</span><span class="sxs-lookup"><span data-stu-id="79409-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="79409-119">Práce s typy velké hodnoty v jazycích Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="79409-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="79409-120">Příkazů jazyka Transact-SQL `OPENROWSET` funkce je jednorázový metoda připojování a přístup ke vzdáleným datům.</span><span class="sxs-lookup"><span data-stu-id="79409-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="79409-121">Obsahuje všechny informace o připojení, která je nezbytná pro přístup ke vzdáleným datům ze zdroje dat OLE DB.</span><span class="sxs-lookup"><span data-stu-id="79409-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="79409-122">`OPENROWSET` může být odkazováno v klauzuli FROM dotazu, jako by šlo název tabulky.</span><span class="sxs-lookup"><span data-stu-id="79409-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="79409-123">Lze také odkazovat jako cílové tabulce příkazu INSERT, UPDATE, nebo odstraňte příkaz, v souladu s možností zprostředkovatele OLE DB.</span><span class="sxs-lookup"><span data-stu-id="79409-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="79409-124">`OPENROWSET` Zahrnuje funkce `BULK` poskytovatel sady řádků, které umožňuje číst data přímo ze souboru bez načítání dat do cílové tabulky.</span><span class="sxs-lookup"><span data-stu-id="79409-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="79409-125">To umožňuje používat `OPENROWSET` v jednoduchý příkaz INSERT SELECT.</span><span class="sxs-lookup"><span data-stu-id="79409-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="79409-126">`OPENROWSET BULK` Argumenty možnost poskytnout významnou kontrolu nad tím, kam se začínají i končí čtení dat, jak zacházet s chybami a jak interpretovat data.</span><span class="sxs-lookup"><span data-stu-id="79409-126">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="79409-127">Například můžete určit, že datový soubor přečíst jako jeden řádek, jeden sloupec sady řádků typu `varbinary`, `varchar`, nebo `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="79409-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="79409-128">Pro úplnou syntaxi a možnosti najdete v tématu knihy Online SQL Server.</span><span class="sxs-lookup"><span data-stu-id="79409-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="79409-129">V následujícím příkladu vloží fotografii do ProductPhoto tabulky v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="79409-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="79409-130">Při použití `BULK OPENROWSET` poskytovatele, je nutné zadat pojmenovaný seznam sloupců, i pokud nejsou vkládání hodnot do každý sloupec.</span><span class="sxs-lookup"><span data-stu-id="79409-130">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="79409-131">Primární klíč v tomto případě je definován jako sloupec identity a může být vynechán ze seznamu sloupců.</span><span class="sxs-lookup"><span data-stu-id="79409-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="79409-132">Všimněte si, že je třeba zadat také název korelace na konci `OPENROWSET` příkazu, který v tomto případě je thumbnailphoto nastavuje.</span><span class="sxs-lookup"><span data-stu-id="79409-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="79409-133">To souvisí se sloupcem v `ProductPhoto` tabulku, do které se načítá soubor.</span><span class="sxs-lookup"><span data-stu-id="79409-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
```  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,   
    ThumbnailPhotoFilePath,   
    LargePhoto,   
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET   
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="79409-134">Aktualizace dat používání aktualizace. ZÁPIS</span><span class="sxs-lookup"><span data-stu-id="79409-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="79409-135">Příkaz jazyka Transact-SQL pro sadu VS11 má nové syntaxe zápisu pro úpravu obsahu `varchar(max)`, `nvarchar(max)`, nebo `varbinary(max)` sloupce.</span><span class="sxs-lookup"><span data-stu-id="79409-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="79409-136">To umožňuje provádět částečné aktualizace data.</span><span class="sxs-lookup"><span data-stu-id="79409-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="79409-137">AKTUALIZACE. Zápis syntaxe se tady zobrazí ve zkrácené formě:</span><span class="sxs-lookup"><span data-stu-id="79409-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="79409-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="79409-138">UPDATE</span></span>  
  
 <span data-ttu-id="79409-139">{  *\<objektu >* }</span><span class="sxs-lookup"><span data-stu-id="79409-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="79409-140">NASTAVIT</span><span class="sxs-lookup"><span data-stu-id="79409-140">SET</span></span>  
  
 <span data-ttu-id="79409-141">{ *column_name* = {. ZÁPIS ( *výraz* , @Offset , @Length )}</span><span class="sxs-lookup"><span data-stu-id="79409-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="79409-142">Metody zápisu určuje, že část hodnoty *column_name* budou upraveny.</span><span class="sxs-lookup"><span data-stu-id="79409-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="79409-143">Výraz je hodnota, kterou bude zkopírován do *column_name*, `@Offset` se počáteční bod, ve kterém se zapíše výraz, a `@Length` argument je délku části ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="79409-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="79409-144">If</span><span class="sxs-lookup"><span data-stu-id="79409-144">If</span></span>|<span data-ttu-id="79409-145">Pak...</span><span class="sxs-lookup"><span data-stu-id="79409-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="79409-146">Výraz je nastavena na hodnotu NULL</span><span class="sxs-lookup"><span data-stu-id="79409-146">The expression is set to NULL</span></span>|<span data-ttu-id="79409-147">`@Length` je ignorována a hodnotou v *column_name* zkrácen v zadaném `@Offset`.</span><span class="sxs-lookup"><span data-stu-id="79409-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="79409-148">`@Offset` je rovno hodnotě NULL</span><span class="sxs-lookup"><span data-stu-id="79409-148">`@Offset` is NULL</span></span>|<span data-ttu-id="79409-149">Operace update připojí výraz na konci existujícího *column_name* hodnotu a `@Length` se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="79409-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="79409-150">`@Offset` je větší než délka hodnoty column_name</span><span class="sxs-lookup"><span data-stu-id="79409-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="79409-151">SQL Server vrátí chybu.</span><span class="sxs-lookup"><span data-stu-id="79409-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="79409-152">`@Length` je rovno hodnotě NULL</span><span class="sxs-lookup"><span data-stu-id="79409-152">`@Length` is NULL</span></span>|<span data-ttu-id="79409-153">Operace aktualizace odebere všechna data z `@Offset` na konec objektu `column_name` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="79409-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="79409-154">Ani `@Offset` ani `@Length` může být záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="79409-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79409-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="79409-155">Example</span></span>  
 <span data-ttu-id="79409-156">V tomto příkladu příkazů jazyka Transact-SQL aktualizuje hodnotu do částečné DocumentSummary, `nvarchar(max)` sloupec v tabulce dokument v databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="79409-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="79409-157">Slovo "součástmi" se nahrazuje slovo "funkce" tak, že určíte slovo nahrazení, počáteční umístění (posun) slova, třeba nahradit stávající data a počet znaků, které mají být nahrazeny (délka).</span><span class="sxs-lookup"><span data-stu-id="79409-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="79409-158">Příklad obsahuje příkazy SELECT, před a po příkazu UPDATE k porovnání výsledků.</span><span class="sxs-lookup"><span data-stu-id="79409-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
```  
USE AdventureWorks;  
GO  
--View the existing value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety components of your bicycle.  
  
--Modify a single word in the DocumentSummary column  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
WHERE DocumentID = 3 ;  
GO   
--View the modified value.  
SELECT DocumentSummary  
FROM Production.Document  
WHERE DocumentID = 3;  
GO  
-- The first sentence of the results will be:  
-- Reflectors are vital safety features of your bicycle.  
```  
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="79409-159">Práce s typy velkých hodnot v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="79409-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="79409-160">Můžete pracovat s typů velkých hodnot v ADO.NET zadáním typů velkých hodnot jako <xref:System.Data.SqlClient.SqlParameter> objekty v <xref:System.Data.SqlClient.SqlDataReader> vrátit požadovaný výsledek, nastavení, nebo pomocí <xref:System.Data.SqlClient.SqlDataAdapter> tak, aby vyplnil `DataSet` / `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="79409-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="79409-161">Není žádný rozdíl mezi stejným způsobem jako při práci s typem velké hodnoty a jeho souvisejících, menší hodnota datového typu.</span><span class="sxs-lookup"><span data-stu-id="79409-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="79409-162">Použití GetSqlBytes k načtení dat</span><span class="sxs-lookup"><span data-stu-id="79409-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="79409-163">`GetSqlBytes` Metodu <xref:System.Data.SqlClient.SqlDataReader> slouží k načtení obsahu `varbinary(max)` sloupce.</span><span class="sxs-lookup"><span data-stu-id="79409-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="79409-164">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt s názvem `cmd` , který vybere `varbinary(max)` data z tabulky a <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` načítající data jako <xref:System.Data.SqlTypes.SqlBytes>.</span><span class="sxs-lookup"><span data-stu-id="79409-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim bytes As SqlBytes = reader.GetSqlBytes(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBytes bytes = reader.GetSqlBytes(0);  
    }  
```  
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="79409-165">Použití GetSqlChars k načtení dat</span><span class="sxs-lookup"><span data-stu-id="79409-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="79409-166">`GetSqlChars` Metodu <xref:System.Data.SqlClient.SqlDataReader> slouží k načtení obsahu `varchar(max)` nebo `nvarchar(max)` sloupce.</span><span class="sxs-lookup"><span data-stu-id="79409-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="79409-167">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt s názvem `cmd` , který vybere `nvarchar(max)` data z tabulky a <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , který načítá data.</span><span class="sxs-lookup"><span data-stu-id="79409-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim buffer As SqlChars = reader.GetSqlChars(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
{  
    SqlChars buffer = reader.GetSqlChars(0);  
}  
```  
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="79409-168">Použití GetSqlBinary k načtení dat</span><span class="sxs-lookup"><span data-stu-id="79409-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="79409-169">`GetSqlBinary` Metodu <xref:System.Data.SqlClient.SqlDataReader> slouží k načtení obsahu `varbinary(max)` sloupce.</span><span class="sxs-lookup"><span data-stu-id="79409-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="79409-170">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt s názvem `cmd` , který vybere `varbinary(max)` data z tabulky a <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` načítající data jako <xref:System.Data.SqlTypes.SqlBinary> datového proudu.</span><span class="sxs-lookup"><span data-stu-id="79409-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
```vb  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
While reader.Read()  
    Dim binaryStream As SqlBinary = reader.GetSqlBinary(0)  
End While  
```  
  
```csharp  
reader = cmd.ExecuteReader(CommandBehavior.CloseConnection);  
while (reader.Read())  
    {  
        SqlBinary binaryStream = reader.GetSqlBinary(0);  
    }  
```  
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="79409-171">Použití GetBytes k načtení dat</span><span class="sxs-lookup"><span data-stu-id="79409-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="79409-172">`GetBytes` Metodu <xref:System.Data.SqlClient.SqlDataReader> načteme posun určený sloupec datového proudu bajtů do bajtového pole začínající na posunu určeného pole.</span><span class="sxs-lookup"><span data-stu-id="79409-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="79409-173">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` bajtů, který načte do bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="79409-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="79409-174">Všimněte si, že na rozdíl od `GetSqlBytes`, `GetBytes` vyžaduje zadání velikosti pole vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="79409-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
```vb  
While reader.Read()  
    Dim buffer(4000) As Byte  
    Dim byteCount As Integer = _  
    CInt(reader.GetBytes(1, 0, buffer, 0, 4000))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    byte[] buffer = new byte[4000];  
    long byteCount = reader.GetBytes(1, 0, buffer, 0, 4000);  
}  
```  
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="79409-175">Použití GetValue k načtení dat</span><span class="sxs-lookup"><span data-stu-id="79409-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="79409-176">`GetValue` Metodu <xref:System.Data.SqlClient.SqlDataReader> přečte hodnotu do pole počínaje posunutím zadaný sloupec.</span><span class="sxs-lookup"><span data-stu-id="79409-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="79409-177">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , posun binární data načte z prvního sloupce a potom data z druhé posun sloupce řetězce.</span><span class="sxs-lookup"><span data-stu-id="79409-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
```vb  
While reader.Read()  
    ' Read the data from varbinary(max) column  
    Dim binaryData() As Byte = CByte(reader.GetValue(0))  
  
    ' Read the data from varchar(max) or nvarchar(max) column  
    Dim stringData() As String = Cstr((reader.GetValue(1))  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
    // Read the data from varbinary(max) column  
    byte[] binaryData = (byte[])reader.GetValue(0);  
  
    // Read the data from varchar(max) or nvarchar(max) column  
    String stringData = (String)reader.GetValue(1);  
}  
```  
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="79409-178">Převod z typů velkých hodnot na typy CLR</span><span class="sxs-lookup"><span data-stu-id="79409-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="79409-179">Můžete převést obsah `varchar(max)` nebo `nvarchar(max)` sloupec některou z metod pro převod řetězce, jako například `ToString`.</span><span class="sxs-lookup"><span data-stu-id="79409-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="79409-180">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , který načítá data.</span><span class="sxs-lookup"><span data-stu-id="79409-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
```vb  
While reader.Read()  
    Dim str as String = reader(0).ToString()  
    Console.WriteLine(str)  
End While  
```  
  
```csharp  
while (reader.Read())  
{  
     string str = reader[0].ToString();  
     Console.WriteLine(str);  
}  
```  
  
### <a name="example"></a><span data-ttu-id="79409-181">Příklad</span><span class="sxs-lookup"><span data-stu-id="79409-181">Example</span></span>  
 <span data-ttu-id="79409-182">Následující kód načte název a `LargePhoto` objektu z `ProductPhoto` v tabulku `AdventureWorks` databáze a uloží jej do souboru.</span><span class="sxs-lookup"><span data-stu-id="79409-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="79409-183">Sestavení musí být zkompilovány s odkazem na <xref:System.Drawing> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="79409-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="79409-184"><xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Metodu <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.SqlTypes.SqlBytes> objekt, který zpřístupňuje `Stream` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="79409-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="79409-185">Tento kód používá k vytvoření nového `Bitmap` objekt a uloží ho do Gif `ImageFormat`.</span><span class="sxs-lookup"><span data-stu-id="79409-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="79409-186">Pomocí parametrů typ velké hodnoty</span><span class="sxs-lookup"><span data-stu-id="79409-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="79409-187">Může být používáno velké hodnoty <xref:System.Data.SqlClient.SqlParameter> objekty stejným způsobem použít menší hodnotu napíše <xref:System.Data.SqlClient.SqlParameter> objekty.</span><span class="sxs-lookup"><span data-stu-id="79409-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="79409-188">Můžete načíst typy velké hodnoty jako <xref:System.Data.SqlClient.SqlParameter> hodnoty, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="79409-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="79409-189">Kód předpokládá, že následující GetDocumentSummary uložené procedury existuje v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="79409-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="79409-190">Uložené procedury přijímá vstupní parametr s názvem @DocumentID a vrátí obsah DocumentSummary sloupec v @DocumentSummary výstupní parametr.</span><span class="sxs-lookup"><span data-stu-id="79409-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
```  
CREATE PROCEDURE GetDocumentSummary   
(  
    @DocumentID int,  
    @DocumentSummary nvarchar(MAX) OUTPUT  
)  
AS  
SET NOCOUNT ON  
SELECT  @DocumentSummary=Convert(nvarchar(MAX), DocumentSummary)  
FROM    Production.Document  
WHERE   DocumentID=@DocumentID  
```  
  
### <a name="example"></a><span data-ttu-id="79409-191">Příklad</span><span class="sxs-lookup"><span data-stu-id="79409-191">Example</span></span>  
 <span data-ttu-id="79409-192">Vytvoří kód ADO.NET <xref:System.Data.SqlClient.SqlConnection> a <xref:System.Data.SqlClient.SqlCommand> objekty spuštění GetDocumentSummary uložené procedury a načíst shrnutí, dokumentů, které se ukládá jako typ velké hodnoty.</span><span class="sxs-lookup"><span data-stu-id="79409-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="79409-193">Kód předá hodnotu @DocumentID vstupní parametr a zobrazí výsledky se předat zpátky @DocumentSummary výstupní parametr v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="79409-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="79409-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="79409-194">See Also</span></span>  
 [<span data-ttu-id="79409-195">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="79409-195">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="79409-196">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="79409-196">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="79409-197">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="79409-197">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="79409-198">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="79409-198">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
