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
# <a name="modifying-large-value-max-data-in-adonet"></a>Úprava vysokých (maximálních) hodnot v ADO.NET
Datové typy velkých objektů (LOB) jsou ty, které překračují maximální velikost řádku 8 kilobajtů (KB). SQL Server `max` poskytuje specifikátor `nvarchar`pro `varbinary` `varchar`, a datové typy umožňující ukládání hodnot až 2 ^32 bajtů. Sloupce tabulky a proměnné Transact-SQL `nvarchar(max)`mohou `varbinary(max)` určovat `varchar(max)`, nebo datové typy. V ADO.NET `max` lze datové typy načíst `DataReader`pomocí aplikace a lze je také zadat jako hodnoty vstupních i výstupních parametrů bez zvláštního zpracování. U `varchar` velkých datových typů lze data načítat a aktualizovat postupně.  
  
 Datové `max` typy lze použít pro porovnání, jako transact-SQL proměnné a pro zřetězení. Mohou být také použity v DISTINCT, ORDER BY, GROUP BY klauzule select příkazu, jakož i v agregaci, spojení a poddotazy.  
  
 Následující tabulka obsahuje odkazy na dokumentaci v SQL Server Books Online.  
  
 **Dokumentace SQL Serveru**  
  
1. [Použití datových typů s velkou hodnotou](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms178158(v=sql.100))  
  
## <a name="large-value-type-restrictions"></a>Omezení typu velké hodnoty  
 Následující omezení platí `max` pro datové typy, které neexistují pro menší datové typy:  
  
- A `sql_variant` nesmí obsahovat velký `varchar` datový typ.  
  
- Velké `varchar` sloupce nelze zadat jako klíčový sloupec v indexu. Jsou povoleny v zahrnutém sloupci v indexu bez clusterů.  
  
- Velké `varchar` sloupce nelze použít jako rozdělení klíčových sloupců.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Práce s typy velkých hodnot v transakt-SQL  
 Funkce Transact-SQL `OPENROWSET` je jednorázová metoda připojení a přístupu ke vzdáleným datům. Obsahuje všechny informace o připojení potřebné pro přístup ke vzdáleným datům ze zdroje dat TECHNOLOGIE OLE DB. `OPENROWSET`může být odkazováno v from klauzule dotazu, jako by to byl název tabulky. Může být také odkazováno jako cílová tabulka insert, UPDATE nebo DELETE prohlášení, s výhradou možnosti zprostředkovatele OLE DB.  
  
 Funkce `OPENROWSET` zahrnuje `BULK` zprostředkovatele sady řádků, který umožňuje číst data přímo ze souboru bez načítání dat do cílové tabulky. To umožňuje použít `OPENROWSET` v jednoduchém příkazu INSERT SELECT.  
  
 Argumenty `OPENROWSET BULK` možnosti poskytují významnou kontrolu nad tím, kde začít a ukončit čtení dat, jak řešit chyby a jak jsou interpretována data. Můžete například určit, že datový soubor bude přečten jako jednořádková jednosloupcová sada řádků typu `varbinary`, `varchar`nebo `nvarchar`. Úplnou syntaxi a možnosti najdete v tématu SQL Server Books Online.  
  
 Následující příklad vloží fotografii do tabulky ProductPhoto v ukázkové databázi AdventureWorks. Při použití `BULK OPENROWSET` zprostředkovatele je nutné zadat pojmenovaný seznam sloupců, i když nevkládáte hodnoty do každého sloupce. Primární klíč v tomto případě je definován jako sloupec identity a může být vynechán ze seznamu sloupců. Všimněte si, že musíte také zadat `OPENROWSET` název korelace na konci příkazu, což je v tomto případě ThumbnailPhoto. To koreluje se sloupcem v tabulce, `ProductPhoto` do kterého je soubor načítán.  
  
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
  
## <a name="updating-data-using-update-write"></a>Aktualizace dat pomocí funkce UPDATE . Zápis  
 Příkaz Transact-SQL UPDATE obsahuje novou syntaxi WRITE `varchar(max)` `nvarchar(max)`pro `varbinary(max)` úpravu obsahu sloupců nebo sloupců . To umožňuje provádět částečné aktualizace dat. Aktualizace . Syntaxe WRITE je zde zobrazena ve zkrácené podobě:  
  
 UPDATE  
  
 { * \<objekt>* }  
  
 SET  
  
 { *column_name* = { . WRITE *expression* ( @Offset výraz @Length , , ) }  
  
 Metoda WRITE určuje, že část hodnoty *column_name* bude změněna. Výraz je hodnota, která bude zkopírována do *column_name*, `@Offset` je počátečním bodem, ve kterém bude výraz zapsán, a `@Length` argumentem je délka oddílu ve sloupci.  
  
|Pokud uživatel|Pak...|  
|--------|----------|  
|Výraz je nastaven na hodnotu NULL.|`@Length`je ignorována a hodnota v *column_name* je zkrácena na zadaném `@Offset`.|  
|`@Offset`je null|Operace aktualizace připojí výraz na konci existující *column_name* `@Length` hodnotu a je ignorována.|  
|`@Offset`je větší než délka column_name hodnoty|SQL Server vrátí chybu.|  
|`@Length`je null|Operace aktualizace odebere všechna `@Offset` data z `column_name` na konec hodnoty.|  
  
> [!NOTE]
> Ani `@Offset` záporné `@Length` číslo.  
  
## <a name="example"></a>Příklad  
 Tento příklad Transact-SQL aktualizuje částečnou hodnotu v DocumentSummary, `nvarchar(max)` sloupec v tabulce Dokument v databázi AdventureWorks. Slovo "komponenty" se nahradí slovem "prvky" zadáním náhradního slova, počátečního umístění (posunu) slova, které má být nahrazeno v existujících datech, a počtu znaků, které mají být nahrazeny (délka). Příklad obsahuje příkazy SELECT před a za příkazem UPDATE k porovnání výsledků.  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a>Práce s typy s velkými hodnotami v ADO.NET  
 Můžete pracovat s typy velkých hodnot v ADO.NET <xref:System.Data.SqlClient.SqlParameter> zadáním <xref:System.Data.SqlClient.SqlDataReader> velkých typů hodnot jako objekty <xref:System.Data.SqlClient.SqlDataAdapter> v `DataSet` / `DataTable`vrátit sadu výsledků, nebo pomocí vyplnit . Neexistuje žádný rozdíl mezi způsobem práce s velkým typem hodnoty a souvisejícím datovým typem s menší hodnotou.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Použití GetSqlBytes k načtení dat  
 Metoda `GetSqlBytes` <xref:System.Data.SqlClient.SqlDataReader> lze použít k načtení obsahu `varbinary(max)` sloupce. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt `cmd` s `varbinary(max)` názvem, který vybírá <xref:System.Data.SqlClient.SqlDataReader> data `reader` z tabulky a <xref:System.Data.SqlTypes.SqlBytes>objekt s názvem, který načítá data jako .  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Použití getsqlchars k načtení dat  
 Metoda `GetSqlChars` <xref:System.Data.SqlClient.SqlDataReader> lze použít k načtení obsahu `varchar(max)` nebo `nvarchar(max)` sloupce. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt `cmd` s `nvarchar(max)` názvem, který vybírá <xref:System.Data.SqlClient.SqlDataReader> data `reader` z tabulky a objekt s názvem, který načítá data.  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Použití GetSqlBinary k načtení dat  
 Metodu `GetSqlBinary` <xref:System.Data.SqlClient.SqlDataReader> lze použít k načtení obsahu `varbinary(max)` sloupce. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt `cmd` s `varbinary(max)` názvem, který vybírá <xref:System.Data.SqlClient.SqlDataReader> data `reader` z tabulky a <xref:System.Data.SqlTypes.SqlBinary> objekt s názvem, který načítá data jako datový proud.  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a>Použití GetBytes k načtení dat  
 Metoda `GetBytes` přečte <xref:System.Data.SqlClient.SqlDataReader> datový proud bajtů ze zadaného posunu sloupce do bajtového pole začínajícího na zadaném posunu pole. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt `reader` s názvem, který načte bajty do bajtového pole. Všimněte si, že na rozdíl od `GetSqlBytes`, `GetBytes` vyžaduje velikost vyrovnávací paměti pole.  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a>Použití funkce GetValue k načtení dat  
 Metoda `GetValue` přečte <xref:System.Data.SqlClient.SqlDataReader> hodnotu ze zadaného posunu sloupce do pole. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt `reader` s názvem, který načítá binární data z prvního sloupce posun a potom řetězcová data z druhého sloupce posun.  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Převod z typů velkých hodnot na typy CLR  
 Obsah `varchar(max)` sloupce nebo `nvarchar(max)` sloupce můžete převést pomocí libovolné metody `ToString`převodu řetězce, například . Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt `reader` s názvem, který načítá data.  
  
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
  
### <a name="example"></a>Příklad  
 Následující kód načte název `LargePhoto` a objekt `ProductPhoto` z `AdventureWorks` tabulky v databázi a uloží je do souboru. Sestavení musí být zkompilován s <xref:System.Drawing> odkazem na obor názvů.  Metoda <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> <xref:System.Data.SqlClient.SqlDataReader> vrátí objekt, <xref:System.Data.SqlTypes.SqlBytes> který zpřístupňuje `Stream` vlastnost. Kód používá k vytvoření `Bitmap` nového objektu a potom jej `ImageFormat`uloží do Gif .  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Použití parametrů typu velké hodnoty  
 Velké typy hodnot lze <xref:System.Data.SqlClient.SqlParameter> použít v objektech stejným <xref:System.Data.SqlClient.SqlParameter> způsobem, jakým používáte menší typy hodnot v objektech. Můžete načíst velké <xref:System.Data.SqlClient.SqlParameter> typy hodnot jako hodnoty, jak je znázorněno v následujícím příkladu. Kód předpokládá, že následující GetDocumentSummary uložená procedura existuje v ukázkové databázi AdventureWorks. Uložená procedura převezme @DocumentID vstupní parametr s názvem a vrátí @DocumentSummary obsah sloupce DocumentSummary ve výstupním parametru.  
  
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
  
### <a name="example"></a>Příklad  
 Kód ADO.NET <xref:System.Data.SqlClient.SqlConnection> vytvoří <xref:System.Data.SqlClient.SqlCommand> a objekty ke spuštění GetDocumentSummary uloženou proceduru a načíst souhrn dokumentu, který je uložen jako velký typ hodnoty. Kód předá hodnotu @DocumentID vstupního parametru a zobrazí @DocumentSummary výsledky předané zpět ve výstupním parametru v okně konzoly.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Binární a vysoké hodnoty na SQL Serveru](sql-server-binary-and-large-value-data.md)
- [Mapování datových typů SQL Serveru](../sql-server-data-type-mappings.md)
- [Operace dat na SQL Serveru v ADO.NET](sql-server-data-operations.md)
- [Přehled ADO.NET](../ado-net-overview.md)
