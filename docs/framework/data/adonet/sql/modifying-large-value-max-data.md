---
title: Úprava vysokých (maximálních) hodnot v ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: 34f0a61329667a42aa42693e93169a5b6fb0aa5e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792037"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Úprava vysokých (maximálních) hodnot v ADO.NET
Datové typy large object (LOB) překračují maximální velikost řádku 8 kilobajtů (KB). SQL Server poskytuje `max` specifikátor pro `varchar`, a `nvarchar` `varbinary` datové typy, které umožňují úložiště hodnot až do velikosti 2 ^ 32 bajtů. Sloupce tabulky a proměnné Transact-SQL mohou určovat `varchar(max)`, `nvarchar(max)`nebo `varbinary(max)` datové typy. V ADO.NET `max` lze datové typy načíst `DataReader`pomocí a a lze je také zadat jako vstupní i výstupní hodnoty parametrů bez speciálního zpracování. U velkých `varchar` datových typů lze data načíst a aktualizovat přírůstkově.  
  
 `max` Datové typy lze použít pro porovnání, jako proměnné Transact-SQL a pro zřetězení. Lze je také použít v klauzulích DISTINCT, ORDER BY, GROUP BY příkazu SELECT a také v agregacích, spojeních a poddotazech.  
  
 Následující tabulka obsahuje odkazy na dokumentaci v SQL Server Knihy online.  
  
 **SQL Server Books Online**  
  
1. [Použití datových typů s velkými hodnotami](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>Omezení typu s velkou hodnotou  
 Následující omezení platí `max` pro datové typy, které neexistují pro menší datové typy:  
  
- Objekt `sql_variant` nemůže obsahovat velký `varchar` datový typ.  
  
- Velké `varchar` sloupce nelze zadat jako klíčový sloupec v indexu. Jsou povoleny v zahrnutém sloupci v neclusterovaných indexech.  
  
- Jako `varchar` klíčové sloupce dělení na oddíly nelze použít velké sloupce.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Práce s typy velkých hodnot v jazyce Transact-SQL  
 Funkce jazyka Transact- `OPENROWSET` SQL je jednorázová metoda připojení a přístupu ke vzdáleným datům. Zahrnuje všechny informace o připojení potřebné pro přístup ke vzdáleným datům z OLE DBho zdroje dat. `OPENROWSET`může být odkazován v klauzuli FROM dotazu, jako by šlo o název tabulky. Může být také odkazován jako cílová tabulka příkazu INSERT, UPDATE nebo DELETE, který podléhá schopnostem poskytovatele OLE DB.  
  
 `OPENROWSET` Funkce obsahujeposkytovatelesadyřádků,kterýumožňuječístdatapřímozesouborubeznačtení`BULK` dat do cílové tabulky. To umožňuje použití `OPENROWSET` v jednoduchém příkazu INSERT SELECT.  
  
 Argumenty `OPENROWSET BULK` možností poskytují významnou kontrolu nad tím, kde začít a koncovým čtením dat, jak pracovat s chybami a jak se interpretují data. Můžete například určit, že se má datový soubor číst jako sada řádků s jedním řádkem, jeden sloupec typu `varbinary`, `varchar`nebo `nvarchar`. Úplnou syntaxi a možnosti naleznete v tématu SQL Server Books Online.  
  
 Následující příklad vloží fotografii do tabulky ProductPhoto v ukázkové databázi AdventureWorks. Při použití `BULK OPENROWSET` zprostředkovatele je nutné dodat pojmenovaný seznam sloupců i v případě, že do každého sloupce nevložíte hodnoty. Primární klíč v tomto případě je definován jako sloupec identity a může být vynechán ze seznamu sloupců. Všimněte si, že je nutné na konci `OPENROWSET` příkazu také uvést název korelace, který je v tomto případě thumbnailPhoto. Tím se koreluje se sloupcem v `ProductPhoto` tabulce, do které se soubor načítá.  
  
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
  
## <a name="updating-data-using-update-write"></a>Aktualizace dat pomocí aktualizace. PSAL  
 Příkaz Update jazyka Transact-SQL obsahuje novou syntaxi zápisu pro úpravu obsahu `varchar(max)`sloupců, `nvarchar(max)`nebo `varbinary(max)` . Díky tomu můžete provádět částečné aktualizace dat. AKTUALIZACE. Syntaxe zápisu se tady zobrazuje ve zkrácené podobě:  
  
 UPDATE  
  
 *{\<Object >* }  
  
 SET  
  
 { *column_name* = {. WRITE ( *výraz* , @Offset ; @Length )}  
  
 Metoda WRITE určuje, že se upraví sekce hodnoty *column_name* . Výraz je hodnota, která bude zkopírována do *column_name*, `@Offset` je počátečním bodem, ve kterém bude výraz `@Length` napsán, a argumentem je délka oddílu ve sloupci.  
  
|If|Pak...|  
|--------|----------|  
|Výraz je nastaven na hodnotu NULL.|`@Length`se ignoruje a hodnota v *column_name* se zkrátí na zadanou `@Offset`hodnotu.|  
|`@Offset`má hodnotu NULL|Operace aktualizace připojí výraz na konci existující hodnoty *column_name* a `@Length` ignoruje se.|  
|`@Offset`je větší než délka hodnoty column_name|SQL Server vrátí chybu.|  
|`@Length`má hodnotu NULL|Operace aktualizace odebere všechna data z `@Offset` na konec `column_name` hodnoty.|  
  
> [!NOTE]
> Ani `@Offset` ani`@Length` nemůže být záporné číslo.  
  
## <a name="example"></a>Příklad  
 Tento příklad Transact-SQL aktualizuje částečnou hodnotu v DocumentSummary, `nvarchar(max)` sloupec v tabulce dokumentů v databázi AdventureWorks. Slovo ' součásti ' je nahrazeno slovem ' Features ' zadáním nahrazujícího slova, počátečního umístění (posunu) slova, které má být nahrazeno existujícími daty, a počtem znaků, které mají být nahrazeny (délka). Příklad obsahuje příkazy SELECT před a za příkazem UPDATE pro porovnání výsledků.  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a>Práce s typy velkých hodnot v ADO.NET  
 Můžete pracovat s velkými typy hodnot v ADO.NET zadáním velkých hodnot typu <xref:System.Data.SqlClient.SqlParameter> jako objektů <xref:System.Data.SqlClient.SqlDataReader> v, chcete-li vrátit sadu výsledků dotazu <xref:System.Data.SqlClient.SqlDataAdapter> , nebo `DataSet` / `DataTable`pomocí a vyplnit. Neexistuje žádný rozdíl mezi způsobem, jakým pracujete s velkým typem hodnoty a jeho souvisejícím datovým typem s menší hodnotou.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Načtení dat pomocí GetSqlBytes  
 Metodu lze použít k`varbinary(max)`načteníobsahusloupce. `GetSqlBytes` <xref:System.Data.SqlClient.SqlDataReader> Následující fragment <xref:System.Data.SqlClient.SqlCommand> kódu předpokládá objekt s názvem `cmd` , který vybere `varbinary(max)` data z tabulky, a <xref:System.Data.SqlClient.SqlDataReader> objektu s názvem `reader` , který načte data jako <xref:System.Data.SqlTypes.SqlBytes>.  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Načtení dat pomocí GetSqlChars  
 Metodu lze použít `nvarchar(max)` k`varchar(max)` načtení obsahu sloupce nebo. <xref:System.Data.SqlClient.SqlDataReader> `GetSqlChars` Následující fragment <xref:System.Data.SqlClient.SqlCommand> kódu předpokládá objekt s názvem `cmd` , který vybere `nvarchar(max)` data z tabulky, a <xref:System.Data.SqlClient.SqlDataReader> objektu s názvem `reader` , který načte data.  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Načtení dat pomocí GetSqlBinary  
 Metodu lze použít k`varbinary(max)`načteníobsahusloupce. `GetSqlBinary` <xref:System.Data.SqlClient.SqlDataReader> Následující fragment <xref:System.Data.SqlClient.SqlCommand> kódu předpokládá objekt s názvem `cmd` , který vybere `varbinary(max)` data z tabulky, a <xref:System.Data.SqlClient.SqlDataReader> objektu s názvem `reader` , který načte data jako <xref:System.Data.SqlTypes.SqlBinary> datový proud.  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a>Načtení dat pomocí GetBytes  
 `GetBytes` Metoda<xref:System.Data.SqlClient.SqlDataReader> načte datový proud bajtů ze zadaného sloupce posunutý na pole bajtů začínající posunem zadaného pole. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , který načte bajty do pole bajtů. Všimněte si, že na `GetSqlBytes`rozdíl `GetBytes` od vyžaduje velikost pro vyrovnávací paměť pole.  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a>Načtení dat pomocí GetValue  
 `GetValue` Metoda<xref:System.Data.SqlClient.SqlDataReader> načte hodnotu z určeného posunutí sloupce do pole. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , který načte binární data z prvního posunutí sloupce a pak řetězcová data z druhého posunutí sloupce.  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Převod z typů s velkými hodnotami na typy CLR  
 Můžete převést obsah `varchar(max)` sloupce nebo `nvarchar(max)` pomocí libovolné metody `ToString`převodu řetězce, jako je například. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , který načte data.  
  
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
 Následující kód načte název a `LargePhoto` objekt `ProductPhoto` z tabulky v `AdventureWorks` databázi a uloží jej do souboru. Sestavení musí být zkompilováno s odkazem na <xref:System.Drawing> obor názvů.  Metoda vrátí objekt, který zpřístupňuje `Stream` vlastnost. <xref:System.Data.SqlTypes.SqlBytes> <xref:System.Data.SqlClient.SqlDataReader> <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Kód používá tuto operaci k vytvoření nového `Bitmap` objektu a poté jej uloží ve formátu GIF. `ImageFormat`  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Použití parametrů velkých hodnotových typů  
 Typy velkých hodnot lze v <xref:System.Data.SqlClient.SqlParameter> objektech použít stejným způsobem, jakým používáte menší typy hodnot v <xref:System.Data.SqlClient.SqlParameter> objektech. Můžete načíst typy velkých hodnot jako <xref:System.Data.SqlClient.SqlParameter> hodnoty, jak je znázorněno v následujícím příkladu. Kód předpokládá, že následující uložená procedura GetDocumentSummary existuje v ukázkové databázi AdventureWorks. Uložená procedura převezme vstupní parametr s názvem @DocumentID a vrátí obsah sloupce DocumentSummary @DocumentSummary ve výstupním parametru.  
  
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
  
### <a name="example"></a>Příklad  
 Kód ADO.NET vytvoří a <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient.SqlCommand> vytvoří objekty pro spuštění uložené procedury GetDocumentSummary a načte souhrn dokumentu, který je uložen jako velký typ hodnoty. Kód předá hodnotu pro @DocumentID vstupní parametr a zobrazí výsledky předané zpátky @DocumentSummary v parametru Output v okně konzoly.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Binární a vysoké hodnoty na SQL Serveru](sql-server-binary-and-large-value-data.md)
- [Mapování datových typů SQL Serveru](../sql-server-data-type-mappings.md)
- [Operace dat na SQL Serveru v ADO.NET](sql-server-data-operations.md)
- [Přehled ADO.NET](../ado-net-overview.md)
