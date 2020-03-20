---
title: Změna dat s velkou hodnotou (max)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 00a4ae83270bb74e9703faebfc93e26b5c069478
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174274"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="14a0a-102">Úprava vysokých (maximálních) hodnot v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="14a0a-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="14a0a-103">Datové typy velkých objektů (LOB) jsou ty, které překračují maximální velikost řádku 8 kilobajtů (KB).</span><span class="sxs-lookup"><span data-stu-id="14a0a-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="14a0a-104">SQL Server `max` poskytuje specifikátor `nvarchar`pro `varbinary` `varchar`, a datové typy umožňující ukládání hodnot až 2 ^32 bajtů.</span><span class="sxs-lookup"><span data-stu-id="14a0a-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="14a0a-105">Sloupce tabulky a proměnné Transact-SQL `nvarchar(max)`mohou `varbinary(max)` určovat `varchar(max)`, nebo datové typy.</span><span class="sxs-lookup"><span data-stu-id="14a0a-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="14a0a-106">V ADO.NET `max` lze datové typy načíst `DataReader`pomocí aplikace a lze je také zadat jako hodnoty vstupních i výstupních parametrů bez zvláštního zpracování.</span><span class="sxs-lookup"><span data-stu-id="14a0a-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="14a0a-107">U `varchar` velkých datových typů lze data načítat a aktualizovat postupně.</span><span class="sxs-lookup"><span data-stu-id="14a0a-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="14a0a-108">Datové `max` typy lze použít pro porovnání, jako transact-SQL proměnné a pro zřetězení.</span><span class="sxs-lookup"><span data-stu-id="14a0a-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="14a0a-109">Mohou být také použity v DISTINCT, ORDER BY, GROUP BY klauzule select příkazu, jakož i v agregaci, spojení a poddotazy.</span><span class="sxs-lookup"><span data-stu-id="14a0a-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="14a0a-110">Následující tabulka obsahuje odkazy na dokumentaci v SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="14a0a-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="14a0a-111">**Dokumentace SQL Serveru**</span><span class="sxs-lookup"><span data-stu-id="14a0a-111">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="14a0a-112">[Použití datových typů s velkou hodnotou](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="14a0a-112">[Using Large-Value Data Types](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))</span></span>  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="14a0a-113">Omezení typu velké hodnoty</span><span class="sxs-lookup"><span data-stu-id="14a0a-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="14a0a-114">Následující omezení platí `max` pro datové typy, které neexistují pro menší datové typy:</span><span class="sxs-lookup"><span data-stu-id="14a0a-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
- <span data-ttu-id="14a0a-115">A `sql_variant` nesmí obsahovat velký `varchar` datový typ.</span><span class="sxs-lookup"><span data-stu-id="14a0a-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
- <span data-ttu-id="14a0a-116">Velké `varchar` sloupce nelze zadat jako klíčový sloupec v indexu.</span><span class="sxs-lookup"><span data-stu-id="14a0a-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="14a0a-117">Jsou povoleny v zahrnutém sloupci v indexu bez clusterů.</span><span class="sxs-lookup"><span data-stu-id="14a0a-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
- <span data-ttu-id="14a0a-118">Velké `varchar` sloupce nelze použít jako rozdělení klíčových sloupců.</span><span class="sxs-lookup"><span data-stu-id="14a0a-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="14a0a-119">Práce s typy velkých hodnot v transakt-SQL</span><span class="sxs-lookup"><span data-stu-id="14a0a-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="14a0a-120">Funkce Transact-SQL `OPENROWSET` je jednorázová metoda připojení a přístupu ke vzdáleným datům.</span><span class="sxs-lookup"><span data-stu-id="14a0a-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="14a0a-121">Obsahuje všechny informace o připojení potřebné pro přístup ke vzdáleným datům ze zdroje dat TECHNOLOGIE OLE DB.</span><span class="sxs-lookup"><span data-stu-id="14a0a-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="14a0a-122">`OPENROWSET`může být odkazováno v from klauzule dotazu, jako by to byl název tabulky.</span><span class="sxs-lookup"><span data-stu-id="14a0a-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="14a0a-123">Může být také odkazováno jako cílová tabulka insert, UPDATE nebo DELETE prohlášení, s výhradou možnosti zprostředkovatele OLE DB.</span><span class="sxs-lookup"><span data-stu-id="14a0a-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="14a0a-124">Funkce `OPENROWSET` zahrnuje `BULK` zprostředkovatele sady řádků, který umožňuje číst data přímo ze souboru bez načítání dat do cílové tabulky.</span><span class="sxs-lookup"><span data-stu-id="14a0a-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="14a0a-125">To umožňuje použít `OPENROWSET` v jednoduchém příkazu INSERT SELECT.</span><span class="sxs-lookup"><span data-stu-id="14a0a-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="14a0a-126">Argumenty `OPENROWSET BULK` možnosti poskytují významnou kontrolu nad tím, kde začít a ukončit čtení dat, jak řešit chyby a jak jsou interpretována data.</span><span class="sxs-lookup"><span data-stu-id="14a0a-126">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="14a0a-127">Můžete například určit, že datový soubor bude přečten jako jednořádková jednosloupcová sada řádků typu `varbinary`, `varchar`nebo `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="14a0a-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="14a0a-128">Úplnou syntaxi a možnosti najdete v tématu SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="14a0a-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="14a0a-129">Následující příklad vloží fotografii do tabulky ProductPhoto v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="14a0a-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="14a0a-130">Při použití `BULK OPENROWSET` zprostředkovatele je nutné zadat pojmenovaný seznam sloupců, i když nevkládáte hodnoty do každého sloupce.</span><span class="sxs-lookup"><span data-stu-id="14a0a-130">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="14a0a-131">Primární klíč v tomto případě je definován jako sloupec identity a může být vynechán ze seznamu sloupců.</span><span class="sxs-lookup"><span data-stu-id="14a0a-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="14a0a-132">Všimněte si, že musíte také zadat `OPENROWSET` název korelace na konci příkazu, což je v tomto případě ThumbnailPhoto.</span><span class="sxs-lookup"><span data-stu-id="14a0a-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="14a0a-133">To koreluje se sloupcem v tabulce, `ProductPhoto` do kterého je soubor načítán.</span><span class="sxs-lookup"><span data-stu-id="14a0a-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
```sql  
INSERT Production.ProductPhoto (  
    ThumbnailPhoto,
    ThumbnailPhotoFilePath,
    LargePhoto,
    LargePhotoFilePath)  
SELECT ThumbnailPhoto.*, null, null, N'tricycle_pink.gif'  
FROM OPENROWSET
    (BULK 'c:\images\tricycle.jpg', SINGLE_BLOB) ThumbnailPhoto  
```  
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="14a0a-134">Aktualizace dat pomocí funkce UPDATE . Zápis</span><span class="sxs-lookup"><span data-stu-id="14a0a-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="14a0a-135">Příkaz Transact-SQL UPDATE obsahuje novou syntaxi WRITE `varchar(max)` `nvarchar(max)`pro `varbinary(max)` úpravu obsahu sloupců nebo sloupců .</span><span class="sxs-lookup"><span data-stu-id="14a0a-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="14a0a-136">To umožňuje provádět částečné aktualizace dat.</span><span class="sxs-lookup"><span data-stu-id="14a0a-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="14a0a-137">Aktualizace . Syntaxe WRITE je zde zobrazena ve zkrácené podobě:</span><span class="sxs-lookup"><span data-stu-id="14a0a-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="14a0a-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="14a0a-138">UPDATE</span></span>  
  
 <span data-ttu-id="14a0a-139">{ \* \<objekt>\* }</span><span class="sxs-lookup"><span data-stu-id="14a0a-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="14a0a-140">SET</span><span class="sxs-lookup"><span data-stu-id="14a0a-140">SET</span></span>  
  
 <span data-ttu-id="14a0a-141">{ *column_name* = { . WRITE *expression* ( @Offset výraz @Length , , ) }</span><span class="sxs-lookup"><span data-stu-id="14a0a-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="14a0a-142">Metoda WRITE určuje, že část hodnoty *column_name* bude změněna.</span><span class="sxs-lookup"><span data-stu-id="14a0a-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="14a0a-143">Výraz je hodnota, která bude zkopírována do *column_name*, `@Offset` je počátečním bodem, ve kterém bude výraz zapsán, a `@Length` argumentem je délka oddílu ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="14a0a-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="14a0a-144">Pokud uživatel</span><span class="sxs-lookup"><span data-stu-id="14a0a-144">If</span></span>|<span data-ttu-id="14a0a-145">Pak...</span><span class="sxs-lookup"><span data-stu-id="14a0a-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="14a0a-146">Výraz je nastaven na hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="14a0a-146">The expression is set to NULL</span></span>|<span data-ttu-id="14a0a-147">`@Length`je ignorována a hodnota v *column_name* je zkrácena na zadaném `@Offset`.</span><span class="sxs-lookup"><span data-stu-id="14a0a-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="14a0a-148">`@Offset`je null</span><span class="sxs-lookup"><span data-stu-id="14a0a-148">`@Offset` is NULL</span></span>|<span data-ttu-id="14a0a-149">Operace aktualizace připojí výraz na konci existující *column_name* `@Length` hodnotu a je ignorována.</span><span class="sxs-lookup"><span data-stu-id="14a0a-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="14a0a-150">`@Offset`je větší než délka column_name hodnoty</span><span class="sxs-lookup"><span data-stu-id="14a0a-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="14a0a-151">SQL Server vrátí chybu.</span><span class="sxs-lookup"><span data-stu-id="14a0a-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="14a0a-152">`@Length`je null</span><span class="sxs-lookup"><span data-stu-id="14a0a-152">`@Length` is NULL</span></span>|<span data-ttu-id="14a0a-153">Operace aktualizace odebere všechna `@Offset` data z `column_name` na konec hodnoty.</span><span class="sxs-lookup"><span data-stu-id="14a0a-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="14a0a-154">Ani `@Offset` záporné `@Length` číslo.</span><span class="sxs-lookup"><span data-stu-id="14a0a-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14a0a-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="14a0a-155">Example</span></span>  
 <span data-ttu-id="14a0a-156">Tento příklad Transact-SQL aktualizuje částečnou hodnotu v DocumentSummary, `nvarchar(max)` sloupec v tabulce Dokument v databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="14a0a-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="14a0a-157">Slovo "komponenty" se nahradí slovem "prvky" zadáním náhradního slova, počátečního umístění (posunu) slova, které má být nahrazeno v existujících datech, a počtu znaků, které mají být nahrazeny (délka).</span><span class="sxs-lookup"><span data-stu-id="14a0a-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="14a0a-158">Příklad obsahuje příkazy SELECT před a za příkazem UPDATE k porovnání výsledků.</span><span class="sxs-lookup"><span data-stu-id="14a0a-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
```sql
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
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="14a0a-159">Práce s typy s velkými hodnotami v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="14a0a-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="14a0a-160">Můžete pracovat s typy velkých hodnot v ADO.NET <xref:System.Data.SqlClient.SqlParameter> zadáním <xref:System.Data.SqlClient.SqlDataReader> velkých typů hodnot jako objekty <xref:System.Data.SqlClient.SqlDataAdapter> v `DataSet` / `DataTable`vrátit sadu výsledků, nebo pomocí vyplnit .</span><span class="sxs-lookup"><span data-stu-id="14a0a-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="14a0a-161">Neexistuje žádný rozdíl mezi způsobem práce s velkým typem hodnoty a souvisejícím datovým typem s menší hodnotou.</span><span class="sxs-lookup"><span data-stu-id="14a0a-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="14a0a-162">Použití GetSqlBytes k načtení dat</span><span class="sxs-lookup"><span data-stu-id="14a0a-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="14a0a-163">Metoda `GetSqlBytes` <xref:System.Data.SqlClient.SqlDataReader> lze použít k načtení obsahu `varbinary(max)` sloupce.</span><span class="sxs-lookup"><span data-stu-id="14a0a-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="14a0a-164">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt `cmd` s `varbinary(max)` názvem, který vybírá <xref:System.Data.SqlClient.SqlDataReader> data `reader` z tabulky a <xref:System.Data.SqlTypes.SqlBytes>objekt s názvem, který načítá data jako .</span><span class="sxs-lookup"><span data-stu-id="14a0a-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="14a0a-165">Použití getsqlchars k načtení dat</span><span class="sxs-lookup"><span data-stu-id="14a0a-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="14a0a-166">Metoda `GetSqlChars` <xref:System.Data.SqlClient.SqlDataReader> lze použít k načtení obsahu `varchar(max)` nebo `nvarchar(max)` sloupce.</span><span class="sxs-lookup"><span data-stu-id="14a0a-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="14a0a-167">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt `cmd` s `nvarchar(max)` názvem, který vybírá <xref:System.Data.SqlClient.SqlDataReader> data `reader` z tabulky a objekt s názvem, který načítá data.</span><span class="sxs-lookup"><span data-stu-id="14a0a-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="14a0a-168">Použití GetSqlBinary k načtení dat</span><span class="sxs-lookup"><span data-stu-id="14a0a-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="14a0a-169">Metodu `GetSqlBinary` <xref:System.Data.SqlClient.SqlDataReader> lze použít k načtení obsahu `varbinary(max)` sloupce.</span><span class="sxs-lookup"><span data-stu-id="14a0a-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="14a0a-170">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt `cmd` s `varbinary(max)` názvem, který vybírá <xref:System.Data.SqlClient.SqlDataReader> data `reader` z tabulky a <xref:System.Data.SqlTypes.SqlBinary> objekt s názvem, který načítá data jako datový proud.</span><span class="sxs-lookup"><span data-stu-id="14a0a-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="14a0a-171">Použití GetBytes k načtení dat</span><span class="sxs-lookup"><span data-stu-id="14a0a-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="14a0a-172">Metoda `GetBytes` přečte <xref:System.Data.SqlClient.SqlDataReader> datový proud bajtů ze zadaného posunu sloupce do bajtového pole začínajícího na zadaném posunu pole.</span><span class="sxs-lookup"><span data-stu-id="14a0a-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="14a0a-173">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt `reader` s názvem, který načte bajty do bajtového pole.</span><span class="sxs-lookup"><span data-stu-id="14a0a-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="14a0a-174">Všimněte si, že na rozdíl od `GetSqlBytes`, `GetBytes` vyžaduje velikost vyrovnávací paměti pole.</span><span class="sxs-lookup"><span data-stu-id="14a0a-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="14a0a-175">Použití funkce GetValue k načtení dat</span><span class="sxs-lookup"><span data-stu-id="14a0a-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="14a0a-176">Metoda `GetValue` přečte <xref:System.Data.SqlClient.SqlDataReader> hodnotu ze zadaného posunu sloupce do pole.</span><span class="sxs-lookup"><span data-stu-id="14a0a-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="14a0a-177">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt `reader` s názvem, který načítá binární data z prvního sloupce posun a potom řetězcová data z druhého sloupce posun.</span><span class="sxs-lookup"><span data-stu-id="14a0a-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="14a0a-178">Převod z typů velkých hodnot na typy CLR</span><span class="sxs-lookup"><span data-stu-id="14a0a-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="14a0a-179">Obsah `varchar(max)` sloupce nebo `nvarchar(max)` sloupce můžete převést pomocí libovolné metody `ToString`převodu řetězce, například .</span><span class="sxs-lookup"><span data-stu-id="14a0a-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="14a0a-180">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt `reader` s názvem, který načítá data.</span><span class="sxs-lookup"><span data-stu-id="14a0a-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="14a0a-181">Příklad</span><span class="sxs-lookup"><span data-stu-id="14a0a-181">Example</span></span>  
 <span data-ttu-id="14a0a-182">Následující kód načte název `LargePhoto` a objekt `ProductPhoto` z `AdventureWorks` tabulky v databázi a uloží je do souboru.</span><span class="sxs-lookup"><span data-stu-id="14a0a-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="14a0a-183">Sestavení musí být zkompilován s <xref:System.Drawing> odkazem na obor názvů.</span><span class="sxs-lookup"><span data-stu-id="14a0a-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="14a0a-184">Metoda <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> <xref:System.Data.SqlClient.SqlDataReader> vrátí objekt, <xref:System.Data.SqlTypes.SqlBytes> který zpřístupňuje `Stream` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="14a0a-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="14a0a-185">Kód používá k vytvoření `Bitmap` nového objektu a potom jej `ImageFormat`uloží do Gif .</span><span class="sxs-lookup"><span data-stu-id="14a0a-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="14a0a-186">Použití parametrů typu velké hodnoty</span><span class="sxs-lookup"><span data-stu-id="14a0a-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="14a0a-187">Velké typy hodnot lze <xref:System.Data.SqlClient.SqlParameter> použít v objektech stejným <xref:System.Data.SqlClient.SqlParameter> způsobem, jakým používáte menší typy hodnot v objektech.</span><span class="sxs-lookup"><span data-stu-id="14a0a-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="14a0a-188">Můžete načíst velké <xref:System.Data.SqlClient.SqlParameter> typy hodnot jako hodnoty, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="14a0a-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="14a0a-189">Kód předpokládá, že následující GetDocumentSummary uložená procedura existuje v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="14a0a-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="14a0a-190">Uložená procedura převezme @DocumentID vstupní parametr s názvem a vrátí @DocumentSummary obsah sloupce DocumentSummary ve výstupním parametru.</span><span class="sxs-lookup"><span data-stu-id="14a0a-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
```sql
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
  
### <a name="example"></a><span data-ttu-id="14a0a-191">Příklad</span><span class="sxs-lookup"><span data-stu-id="14a0a-191">Example</span></span>  
 <span data-ttu-id="14a0a-192">Kód ADO.NET <xref:System.Data.SqlClient.SqlConnection> vytvoří <xref:System.Data.SqlClient.SqlCommand> a objekty ke spuštění GetDocumentSummary uloženou proceduru a načíst souhrn dokumentu, který je uložen jako velký typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="14a0a-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="14a0a-193">Kód předá hodnotu @DocumentID vstupního parametru a zobrazí @DocumentSummary výsledky předané zpět ve výstupním parametru v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="14a0a-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="14a0a-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="14a0a-194">See also</span></span>

- [<span data-ttu-id="14a0a-195">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="14a0a-195">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="14a0a-196">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="14a0a-196">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="14a0a-197">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="14a0a-197">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="14a0a-198">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="14a0a-198">ADO.NET Overview</span></span>](../ado-net-overview.md)
