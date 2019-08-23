---
title: Úprava vysokých (maximálních) hodnot v ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 19d0c78221f35bd36edce85a60a4a7a2f985bc38
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947012"
---
# <a name="modifying-large-value-max-data-in-adonet"></a><span data-ttu-id="a5ea4-102">Úprava vysokých (maximálních) hodnot v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a5ea4-102">Modifying Large-Value (max) Data in ADO.NET</span></span>
<span data-ttu-id="a5ea4-103">Datové typy large object (LOB) překračují maximální velikost řádku 8 kilobajtů (KB).</span><span class="sxs-lookup"><span data-stu-id="a5ea4-103">Large object (LOB) data types are those that exceed the maximum row size of 8 kilobytes (KB).</span></span> <span data-ttu-id="a5ea4-104">SQL Server poskytuje `max` specifikátor pro `varchar`, a `nvarchar` `varbinary` datové typy, které umožňují úložiště hodnot až do velikosti 2 ^ 32 bajtů.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-104">SQL Server provides a `max` specifier for `varchar`, `nvarchar`, and `varbinary` data types to allow storage of values as large as 2^32 bytes.</span></span> <span data-ttu-id="a5ea4-105">Sloupce tabulky a proměnné Transact-SQL mohou určovat `varchar(max)`, `nvarchar(max)`nebo `varbinary(max)` datové typy.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-105">Table columns and Transact-SQL variables may specify `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` data types.</span></span> <span data-ttu-id="a5ea4-106">V ADO.NET `max` lze datové typy načíst `DataReader`pomocí a a lze je také zadat jako vstupní i výstupní hodnoty parametrů bez speciálního zpracování.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-106">In ADO.NET, the `max` data types can be fetched by a `DataReader`, and can also be specified as both input and output parameter values without any special handling.</span></span> <span data-ttu-id="a5ea4-107">U velkých `varchar` datových typů lze data načíst a aktualizovat přírůstkově.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-107">For large `varchar` data types, data can be retrieved and updated incrementally.</span></span>  
  
 <span data-ttu-id="a5ea4-108">`max` Datové typy lze použít pro porovnání, jako proměnné Transact-SQL a pro zřetězení.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-108">The `max` data types can be used for comparisons, as Transact-SQL variables, and for concatenation.</span></span> <span data-ttu-id="a5ea4-109">Lze je také použít v klauzulích DISTINCT, ORDER BY, GROUP BY příkazu SELECT a také v agregacích, spojeních a poddotazech.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-109">They can also be used in the DISTINCT, ORDER BY, GROUP BY clauses of a SELECT statement as well as in aggregates, joins, and subqueries.</span></span>  
  
 <span data-ttu-id="a5ea4-110">Následující tabulka obsahuje odkazy na dokumentaci v SQL Server Knihy online.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-110">The following table provides links to the documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="a5ea4-111">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="a5ea4-111">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="a5ea4-112">Použití datových typů s velkými hodnotami</span><span class="sxs-lookup"><span data-stu-id="a5ea4-112">Using Large-Value Data Types</span></span>](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a><span data-ttu-id="a5ea4-113">Omezení typu s velkou hodnotou</span><span class="sxs-lookup"><span data-stu-id="a5ea4-113">Large-Value Type Restrictions</span></span>  
 <span data-ttu-id="a5ea4-114">Následující omezení platí `max` pro datové typy, které neexistují pro menší datové typy:</span><span class="sxs-lookup"><span data-stu-id="a5ea4-114">The following restrictions apply to the `max` data types, which do not exist for smaller data types:</span></span>  
  
- <span data-ttu-id="a5ea4-115">Objekt `sql_variant` nemůže obsahovat velký `varchar` datový typ.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-115">A `sql_variant` cannot contain a large `varchar` data type.</span></span>  
  
- <span data-ttu-id="a5ea4-116">Velké `varchar` sloupce nelze zadat jako klíčový sloupec v indexu.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-116">Large `varchar` columns cannot be specified as a key column in an index.</span></span> <span data-ttu-id="a5ea4-117">Jsou povoleny v zahrnutém sloupci v neclusterovaných indexech.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-117">They are allowed in an included column in a non-clustered index.</span></span>  
  
- <span data-ttu-id="a5ea4-118">Jako `varchar` klíčové sloupce dělení na oddíly nelze použít velké sloupce.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-118">Large `varchar` columns cannot be used as partitioning key columns.</span></span>  
  
## <a name="working-with-large-value-types-in-transact-sql"></a><span data-ttu-id="a5ea4-119">Práce s typy velkých hodnot v jazyce Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a5ea4-119">Working with Large-Value Types in Transact-SQL</span></span>  
 <span data-ttu-id="a5ea4-120">Funkce jazyka Transact- `OPENROWSET` SQL je jednorázová metoda připojení a přístupu ke vzdáleným datům.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-120">The Transact-SQL `OPENROWSET` function is a one-time method of connecting and accessing remote data.</span></span> <span data-ttu-id="a5ea4-121">Zahrnuje všechny informace o připojení potřebné pro přístup ke vzdáleným datům z OLE DBho zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-121">It includes all of the connection information necessary to access remote data from an OLE DB data source.</span></span> <span data-ttu-id="a5ea4-122">`OPENROWSET`může být odkazován v klauzuli FROM dotazu, jako by šlo o název tabulky.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-122">`OPENROWSET` can be referenced in the FROM clause of a query as though it were a table name.</span></span> <span data-ttu-id="a5ea4-123">Může být také odkazován jako cílová tabulka příkazu INSERT, UPDATE nebo DELETE, který podléhá schopnostem poskytovatele OLE DB.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-123">It can also be referenced as the target table of an INSERT, UPDATE, or DELETE statement, subject to the capabilities of the OLE DB provider.</span></span>  
  
 <span data-ttu-id="a5ea4-124">`OPENROWSET` Funkce obsahujeposkytovatelesadyřádků,kterýumožňuječístdatapřímozesouborubeznačtení`BULK` dat do cílové tabulky.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-124">The `OPENROWSET` function includes the `BULK` rowset provider, which allows you to read data directly from a file without loading the data into a target table.</span></span> <span data-ttu-id="a5ea4-125">To umožňuje použití `OPENROWSET` v jednoduchém příkazu INSERT SELECT.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-125">This enables you to use `OPENROWSET` in a simple INSERT SELECT statement.</span></span>  
  
 <span data-ttu-id="a5ea4-126">Argumenty `OPENROWSET BULK` možností poskytují významnou kontrolu nad tím, kde začít a koncovým čtením dat, jak pracovat s chybami a jak se interpretují data.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-126">The `OPENROWSET BULK` option arguments provide significant control over where to begin and end reading data, how to deal with errors, and how data is interpreted.</span></span> <span data-ttu-id="a5ea4-127">Můžete například určit, že se má datový soubor číst jako sada řádků s jedním řádkem, jeden sloupec typu `varbinary`, `varchar`nebo `nvarchar`.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-127">For example, you can specify that the data file be read as a single-row, single-column rowset of type `varbinary`, `varchar`, or `nvarchar`.</span></span> <span data-ttu-id="a5ea4-128">Úplnou syntaxi a možnosti naleznete v tématu SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-128">For the complete syntax and options, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="a5ea4-129">Následující příklad vloží fotografii do tabulky ProductPhoto v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-129">The following example inserts a photo into the ProductPhoto table in the AdventureWorks sample database.</span></span> <span data-ttu-id="a5ea4-130">Při použití `BULK OPENROWSET` zprostředkovatele je nutné dodat pojmenovaný seznam sloupců i v případě, že do každého sloupce nevložíte hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-130">When using the `BULK OPENROWSET` provider, you must supply the named list of columns even if you aren't inserting values into every column.</span></span> <span data-ttu-id="a5ea4-131">Primární klíč v tomto případě je definován jako sloupec identity a může být vynechán ze seznamu sloupců.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-131">The primary key in this case is defined as an identity column, and may be omitted from the column list.</span></span> <span data-ttu-id="a5ea4-132">Všimněte si, že je nutné na konci `OPENROWSET` příkazu také uvést název korelace, který je v tomto případě thumbnailPhoto.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-132">Note that you must also supply a correlation name at the end of the `OPENROWSET` statement, which in this case is ThumbnailPhoto.</span></span> <span data-ttu-id="a5ea4-133">Tím se koreluje se sloupcem v `ProductPhoto` tabulce, do které se soubor načítá.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-133">This correlates with the column in the `ProductPhoto` table into which the file is being loaded.</span></span>  
  
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
  
## <a name="updating-data-using-update-write"></a><span data-ttu-id="a5ea4-134">Aktualizace dat pomocí aktualizace. PSAL</span><span class="sxs-lookup"><span data-stu-id="a5ea4-134">Updating Data Using UPDATE .WRITE</span></span>  
 <span data-ttu-id="a5ea4-135">Příkaz Update jazyka Transact-SQL obsahuje novou syntaxi zápisu pro úpravu obsahu `varchar(max)`sloupců, `nvarchar(max)`nebo `varbinary(max)` .</span><span class="sxs-lookup"><span data-stu-id="a5ea4-135">The Transact-SQL UPDATE statement has new WRITE syntax for modifying the contents of `varchar(max)`, `nvarchar(max)`, or `varbinary(max)` columns.</span></span> <span data-ttu-id="a5ea4-136">Díky tomu můžete provádět částečné aktualizace dat.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-136">This allows you to perform partial updates of the data.</span></span> <span data-ttu-id="a5ea4-137">AKTUALIZACE. Syntaxe zápisu se tady zobrazuje ve zkrácené podobě:</span><span class="sxs-lookup"><span data-stu-id="a5ea4-137">The UPDATE .WRITE syntax is shown here in abbreviated form:</span></span>  
  
 <span data-ttu-id="a5ea4-138">UPDATE</span><span class="sxs-lookup"><span data-stu-id="a5ea4-138">UPDATE</span></span>  
  
 <span data-ttu-id="a5ea4-139">*{\<Object >* }</span><span class="sxs-lookup"><span data-stu-id="a5ea4-139">{ *\<object>* }</span></span>  
  
 <span data-ttu-id="a5ea4-140">SET</span><span class="sxs-lookup"><span data-stu-id="a5ea4-140">SET</span></span>  
  
 <span data-ttu-id="a5ea4-141">{ *column_name* = {. WRITE ( *výraz* , @Offset ; @Length )}</span><span class="sxs-lookup"><span data-stu-id="a5ea4-141">{ *column_name* = { .WRITE ( *expression* , @Offset , @Length ) }</span></span>  
  
 <span data-ttu-id="a5ea4-142">Metoda WRITE určuje, že se upraví sekce hodnoty *column_name* .</span><span class="sxs-lookup"><span data-stu-id="a5ea4-142">The WRITE method specifies that a section of the value of the *column_name* will be modified.</span></span> <span data-ttu-id="a5ea4-143">Výraz je hodnota, která bude zkopírována do *column_name*, `@Offset` je počátečním bodem, ve kterém bude výraz `@Length` napsán, a argumentem je délka oddílu ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-143">The expression is the value that will be copied to the *column_name*, the `@Offset` is the beginning point at which the expression will be written, and the `@Length` argument is the length of the section in the column.</span></span>  
  
|<span data-ttu-id="a5ea4-144">If</span><span class="sxs-lookup"><span data-stu-id="a5ea4-144">If</span></span>|<span data-ttu-id="a5ea4-145">Pak...</span><span class="sxs-lookup"><span data-stu-id="a5ea4-145">Then</span></span>|  
|--------|----------|  
|<span data-ttu-id="a5ea4-146">Výraz je nastaven na hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-146">The expression is set to NULL</span></span>|<span data-ttu-id="a5ea4-147">`@Length`se ignoruje a hodnota v *column_name* se zkrátí na zadanou `@Offset`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-147">`@Length` is ignored and the value in *column_name* is truncated at the specified `@Offset`.</span></span>|  
|<span data-ttu-id="a5ea4-148">`@Offset`má hodnotu NULL</span><span class="sxs-lookup"><span data-stu-id="a5ea4-148">`@Offset` is NULL</span></span>|<span data-ttu-id="a5ea4-149">Operace aktualizace připojí výraz na konci existující hodnoty *column_name* a `@Length` ignoruje se.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-149">The update operation appends the expression at the end of the existing *column_name* value and `@Length` is ignored.</span></span>|  
|<span data-ttu-id="a5ea4-150">`@Offset`je větší než délka hodnoty column_name</span><span class="sxs-lookup"><span data-stu-id="a5ea4-150">`@Offset` is greater than the length of the column_name value</span></span>|<span data-ttu-id="a5ea4-151">SQL Server vrátí chybu.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-151">SQL Server returns an error.</span></span>|  
|<span data-ttu-id="a5ea4-152">`@Length`má hodnotu NULL</span><span class="sxs-lookup"><span data-stu-id="a5ea4-152">`@Length` is NULL</span></span>|<span data-ttu-id="a5ea4-153">Operace aktualizace odebere všechna data z `@Offset` na konec `column_name` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-153">The update operation removes all data from `@Offset` to the end of the `column_name` value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="a5ea4-154">Ani `@Offset` ani`@Length` nemůže být záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-154">Neither `@Offset` nor `@Length` can be a negative number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5ea4-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5ea4-155">Example</span></span>  
 <span data-ttu-id="a5ea4-156">Tento příklad Transact-SQL aktualizuje částečnou hodnotu v DocumentSummary, `nvarchar(max)` sloupec v tabulce dokumentů v databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-156">This Transact-SQL example updates a partial value in DocumentSummary, an `nvarchar(max)` column in the Document table in the AdventureWorks database.</span></span> <span data-ttu-id="a5ea4-157">Slovo ' součásti ' je nahrazeno slovem ' Features ' zadáním nahrazujícího slova, počátečního umístění (posunu) slova, které má být nahrazeno existujícími daty, a počtem znaků, které mají být nahrazeny (délka).</span><span class="sxs-lookup"><span data-stu-id="a5ea4-157">The word 'components' is replaced by the word 'features' by specifying the replacement word, the beginning location (offset) of the word to be replaced in the existing data, and the number of characters to be replaced (length).</span></span> <span data-ttu-id="a5ea4-158">Příklad obsahuje příkazy SELECT před a za příkazem UPDATE pro porovnání výsledků.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-158">The example includes SELECT statements before and after the UPDATE statement to compare results.</span></span>  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a><span data-ttu-id="a5ea4-159">Práce s typy velkých hodnot v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a5ea4-159">Working with Large-Value Types in ADO.NET</span></span>  
 <span data-ttu-id="a5ea4-160">Můžete pracovat s velkými typy hodnot v ADO.NET zadáním velkých hodnot typu <xref:System.Data.SqlClient.SqlParameter> jako objektů <xref:System.Data.SqlClient.SqlDataReader> v, chcete-li vrátit sadu výsledků dotazu <xref:System.Data.SqlClient.SqlDataAdapter> , nebo `DataSet` / `DataTable`pomocí a vyplnit.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-160">You can work with large value types in ADO.NET by specifying large value types as <xref:System.Data.SqlClient.SqlParameter> objects in a <xref:System.Data.SqlClient.SqlDataReader> to return a result set, or by using a <xref:System.Data.SqlClient.SqlDataAdapter> to fill a `DataSet`/`DataTable`.</span></span> <span data-ttu-id="a5ea4-161">Neexistuje žádný rozdíl mezi způsobem, jakým pracujete s velkým typem hodnoty a jeho souvisejícím datovým typem s menší hodnotou.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-161">There is no difference between the way you work with a large value type and its related, smaller value data type.</span></span>  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a><span data-ttu-id="a5ea4-162">Načtení dat pomocí GetSqlBytes</span><span class="sxs-lookup"><span data-stu-id="a5ea4-162">Using GetSqlBytes to Retrieve Data</span></span>  
 <span data-ttu-id="a5ea4-163">Metodu lze použít k`varbinary(max)`načteníobsahusloupce. `GetSqlBytes` <xref:System.Data.SqlClient.SqlDataReader></span><span class="sxs-lookup"><span data-stu-id="a5ea4-163">The `GetSqlBytes` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="a5ea4-164">Následující fragment <xref:System.Data.SqlClient.SqlCommand> kódu předpokládá objekt s názvem `cmd` , který vybere `varbinary(max)` data z tabulky, a <xref:System.Data.SqlClient.SqlDataReader> objektu s názvem `reader` , který načte data jako <xref:System.Data.SqlTypes.SqlBytes>.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-164">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as <xref:System.Data.SqlTypes.SqlBytes>.</span></span>  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a><span data-ttu-id="a5ea4-165">Načtení dat pomocí GetSqlChars</span><span class="sxs-lookup"><span data-stu-id="a5ea4-165">Using GetSqlChars to Retrieve Data</span></span>  
 <span data-ttu-id="a5ea4-166">Metodu lze použít `nvarchar(max)` k`varchar(max)` načtení obsahu sloupce nebo. <xref:System.Data.SqlClient.SqlDataReader> `GetSqlChars`</span><span class="sxs-lookup"><span data-stu-id="a5ea4-166">The `GetSqlChars` method of the <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varchar(max)` or `nvarchar(max)` column.</span></span> <span data-ttu-id="a5ea4-167">Následující fragment <xref:System.Data.SqlClient.SqlCommand> kódu předpokládá objekt s názvem `cmd` , který vybere `nvarchar(max)` data z tabulky, a <xref:System.Data.SqlClient.SqlDataReader> objektu s názvem `reader` , který načte data.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-167">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `nvarchar(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a><span data-ttu-id="a5ea4-168">Načtení dat pomocí GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="a5ea4-168">Using GetSqlBinary to Retrieve Data</span></span>  
 <span data-ttu-id="a5ea4-169">Metodu lze použít k`varbinary(max)`načteníobsahusloupce. `GetSqlBinary` <xref:System.Data.SqlClient.SqlDataReader></span><span class="sxs-lookup"><span data-stu-id="a5ea4-169">The `GetSqlBinary` method of a <xref:System.Data.SqlClient.SqlDataReader> can be used to retrieve the contents of a `varbinary(max)` column.</span></span> <span data-ttu-id="a5ea4-170">Následující fragment <xref:System.Data.SqlClient.SqlCommand> kódu předpokládá objekt s názvem `cmd` , který vybere `varbinary(max)` data z tabulky, a <xref:System.Data.SqlClient.SqlDataReader> objektu s názvem `reader` , který načte data jako <xref:System.Data.SqlTypes.SqlBinary> datový proud.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-170">The following code fragment assumes a <xref:System.Data.SqlClient.SqlCommand> object named `cmd` that selects `varbinary(max)` data from a table and a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data as a <xref:System.Data.SqlTypes.SqlBinary> stream.</span></span>  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a><span data-ttu-id="a5ea4-171">Načtení dat pomocí GetBytes</span><span class="sxs-lookup"><span data-stu-id="a5ea4-171">Using GetBytes to Retrieve Data</span></span>  
 <span data-ttu-id="a5ea4-172">`GetBytes` Metoda<xref:System.Data.SqlClient.SqlDataReader> načte datový proud bajtů ze zadaného sloupce posunutý na pole bajtů začínající posunem zadaného pole.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-172">The `GetBytes` method of a <xref:System.Data.SqlClient.SqlDataReader> reads a stream of bytes from the specified column offset into a byte array starting at the specified array offset.</span></span> <span data-ttu-id="a5ea4-173">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , který načte bajty do pole bajtů.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-173">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves bytes into a byte array.</span></span> <span data-ttu-id="a5ea4-174">Všimněte si, že na `GetSqlBytes`rozdíl `GetBytes` od vyžaduje velikost pro vyrovnávací paměť pole.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-174">Note that, unlike `GetSqlBytes`, `GetBytes` requires a size for the array buffer.</span></span>  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a><span data-ttu-id="a5ea4-175">Načtení dat pomocí GetValue</span><span class="sxs-lookup"><span data-stu-id="a5ea4-175">Using GetValue to Retrieve Data</span></span>  
 <span data-ttu-id="a5ea4-176">`GetValue` Metoda<xref:System.Data.SqlClient.SqlDataReader> načte hodnotu z určeného posunutí sloupce do pole.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-176">The `GetValue` method of a <xref:System.Data.SqlClient.SqlDataReader> reads the value from the specified column offset into an array.</span></span> <span data-ttu-id="a5ea4-177">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , který načte binární data z prvního posunutí sloupce a pak řetězcová data z druhého posunutí sloupce.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-177">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves binary data from the first column offset, and then string data from the second column offset.</span></span>  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a><span data-ttu-id="a5ea4-178">Převod z typů s velkými hodnotami na typy CLR</span><span class="sxs-lookup"><span data-stu-id="a5ea4-178">Converting from Large Value Types to CLR Types</span></span>  
 <span data-ttu-id="a5ea4-179">Můžete převést obsah `varchar(max)` sloupce nebo `nvarchar(max)` pomocí libovolné metody `ToString`převodu řetězce, jako je například.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-179">You can convert the contents of a `varchar(max)` or `nvarchar(max)` column using any of the string conversion methods, such as `ToString`.</span></span> <span data-ttu-id="a5ea4-180">Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , který načte data.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-180">The following code fragment assumes a <xref:System.Data.SqlClient.SqlDataReader> object named `reader` that retrieves the data.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="a5ea4-181">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5ea4-181">Example</span></span>  
 <span data-ttu-id="a5ea4-182">Následující kód načte název a `LargePhoto` objekt `ProductPhoto` z tabulky v `AdventureWorks` databázi a uloží jej do souboru.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-182">The following code retrieves the name and the `LargePhoto` object from the `ProductPhoto` table in the `AdventureWorks` database and saves it to a file.</span></span> <span data-ttu-id="a5ea4-183">Sestavení musí být zkompilováno s odkazem na <xref:System.Drawing> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-183">The assembly needs to be compiled with a reference to the <xref:System.Drawing> namespace.</span></span>  <span data-ttu-id="a5ea4-184">Metoda vrátí objekt, který zpřístupňuje `Stream` vlastnost. <xref:System.Data.SqlTypes.SqlBytes> <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A></span><span class="sxs-lookup"><span data-stu-id="a5ea4-184">The <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> method of the <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.SqlTypes.SqlBytes> object that exposes a `Stream` property.</span></span> <span data-ttu-id="a5ea4-185">Kód používá tuto operaci k vytvoření nového `Bitmap` objektu a poté jej uloží ve formátu GIF. `ImageFormat`</span><span class="sxs-lookup"><span data-stu-id="a5ea4-185">The code uses this to create a new `Bitmap` object, and then saves it in the Gif `ImageFormat`.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a><span data-ttu-id="a5ea4-186">Použití parametrů velkých hodnotových typů</span><span class="sxs-lookup"><span data-stu-id="a5ea4-186">Using Large Value Type Parameters</span></span>  
 <span data-ttu-id="a5ea4-187">Typy velkých hodnot lze v <xref:System.Data.SqlClient.SqlParameter> objektech použít stejným způsobem, jakým používáte menší typy hodnot v <xref:System.Data.SqlClient.SqlParameter> objektech.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-187">Large value types can be used in <xref:System.Data.SqlClient.SqlParameter> objects the same way you use smaller value types in <xref:System.Data.SqlClient.SqlParameter> objects.</span></span> <span data-ttu-id="a5ea4-188">Můžete načíst typy velkých hodnot jako <xref:System.Data.SqlClient.SqlParameter> hodnoty, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-188">You can retrieve large value types as <xref:System.Data.SqlClient.SqlParameter> values, as shown in the following example.</span></span> <span data-ttu-id="a5ea4-189">Kód předpokládá, že následující uložená procedura GetDocumentSummary existuje v ukázkové databázi AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-189">The code assumes that the following GetDocumentSummary stored procedure exists in the AdventureWorks sample database.</span></span> <span data-ttu-id="a5ea4-190">Uložená procedura převezme vstupní parametr s názvem @DocumentID a vrátí obsah sloupce DocumentSummary @DocumentSummary ve výstupním parametru.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-190">The stored procedure takes an input parameter named @DocumentID and returns the contents of the DocumentSummary column in the @DocumentSummary output parameter.</span></span>  
  
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
  
### <a name="example"></a><span data-ttu-id="a5ea4-191">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5ea4-191">Example</span></span>  
 <span data-ttu-id="a5ea4-192">Kód ADO.NET vytvoří a <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient.SqlCommand> vytvoří objekty pro spuštění uložené procedury GetDocumentSummary a načte souhrn dokumentu, který je uložen jako velký typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-192">The ADO.NET code creates <xref:System.Data.SqlClient.SqlConnection> and <xref:System.Data.SqlClient.SqlCommand> objects to execute the GetDocumentSummary stored procedure and retrieve the document summary, which is stored as a large value type.</span></span> <span data-ttu-id="a5ea4-193">Kód předá hodnotu pro @DocumentID vstupní parametr a zobrazí výsledky předané zpátky @DocumentSummary v parametru Output v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="a5ea4-193">The code passes a value for the @DocumentID input parameter, and displays the results passed back in the @DocumentSummary output parameter in the Console window.</span></span>  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a5ea4-194">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5ea4-194">See also</span></span>

- [<span data-ttu-id="a5ea4-195">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="a5ea4-195">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="a5ea4-196">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="a5ea4-196">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [<span data-ttu-id="a5ea4-197">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a5ea4-197">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [<span data-ttu-id="a5ea4-198">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="a5ea4-198">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
