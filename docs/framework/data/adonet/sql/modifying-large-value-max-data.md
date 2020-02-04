---
title: Úprava dat s velkou hodnotou (max.)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: cb37fdb85d323d4f0816a3667a4624da8ec75e65
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979843"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Úprava vysokých (maximálních) hodnot v ADO.NET
Datové typy large object (LOB) překračují maximální velikost řádku 8 kilobajtů (KB). SQL Server poskytuje `max` specifikátor pro datové typy `varchar`, `nvarchar`a `varbinary`, aby bylo možné úložiště hodnot větší než 2 ^ 32 bajtů. Sloupce tabulky a proměnné Transact-SQL mohou určovat datové typy `varchar(max)`, `nvarchar(max)`nebo `varbinary(max)`. V ADO.NET lze datové typy `max` načíst pomocí `DataReader`a lze je také zadat jako vstupní i výstupní hodnoty parametrů bez speciálního zpracování. U velkých `varchar` datových typů lze data načíst a aktualizovat přírůstkově.  
  
 Datové typy `max` lze použít pro porovnání, jako proměnné Transact-SQL a pro zřetězení. Lze je také použít v klauzulích DISTINCT, ORDER BY, GROUP BY příkazu SELECT a také v agregacích, spojeních a poddotazech.  
  
 Následující tabulka obsahuje odkazy na dokumentaci v SQL Server Knihy online.  
  
 **SQL Server Books Online**  
  
1. [Použití datových typů s velkými hodnotami](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>Omezení typu s velkou hodnotou  
 Následující omezení platí pro `max` datové typy, které pro menší datové typy neexistují:  
  
- `sql_variant` nemůže obsahovat velký `varchar` datový typ.  
  
- Velké `varchar` sloupce nelze zadat jako klíčový sloupec v indexu. Jsou povoleny v zahrnutém sloupci v neclusterovaných indexech.  
  
- Sloupce s velkými `varchar` nelze použít jako oddíly klíčových sloupců.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Práce s typy velkých hodnot v jazyce Transact-SQL  
 Funkce Transact-SQL `OPENROWSET` je jednorázovou metodou připojení a přístupu ke vzdáleným datům. Zahrnuje všechny informace o připojení potřebné pro přístup ke vzdáleným datům z OLE DBho zdroje dat. na `OPENROWSET` lze odkazovat v klauzuli FROM dotazu, jako by se jednalo o název tabulky. Může být také odkazován jako cílová tabulka příkazu INSERT, UPDATE nebo DELETE, který podléhá schopnostem poskytovatele OLE DB.  
  
 Funkce `OPENROWSET` obsahuje `BULK` poskytovatele sady řádků, který umožňuje číst data přímo ze souboru bez načtení dat do cílové tabulky. To umožňuje použít `OPENROWSET` v jednoduchém příkazu INSERT SELECT.  
  
 Argumenty možností `OPENROWSET BULK` poskytují významnou kontrolu nad tím, kde začít a koncovým čtením dat, jak pracovat s chybami a jak se interpretují data. Můžete například určit, že datový soubor bude čten jako jeden řádek, sada řádků s jedním sloupcem typu `varbinary`, `varchar`nebo `nvarchar`. Úplnou syntaxi a možnosti naleznete v tématu SQL Server Books Online.  
  
 Následující příklad vloží fotografii do tabulky ProductPhoto v ukázkové databázi AdventureWorks. Pokud používáte poskytovatele `BULK OPENROWSET`, je nutné dodat pojmenovaný seznam sloupců, i když do každého sloupce nevložíte hodnoty. Primární klíč v tomto případě je definován jako sloupec identity a může být vynechán ze seznamu sloupců. Všimněte si, že musíte také uvést název korelace na konci příkazu `OPENROWSET`, který je v tomto případě ThumbnailPhoto. To koreluje se sloupcem v tabulce `ProductPhoto`, do které se soubor načítá.  
  
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
  
## <a name="updating-data-using-update-write"></a>Aktualizace dat pomocí aktualizace. PSAL  
 Příkaz UPDATE jazyka Transact-SQL obsahuje novou syntaxi zápisu pro úpravu obsahu `varchar(max)`, `nvarchar(max)`nebo `varbinary(max)` sloupců. Díky tomu můžete provádět částečné aktualizace dat. AKTUALIZACE. Syntaxe zápisu se tady zobrazuje ve zkrácené podobě:  
  
 AKTUALIZOVAT  
  
 { *\<objekt >* }  
  
 SET  
  
 { *column_name* = {. WRITE ( *výraz* , @Offset, @Length)}  
  
 Metoda WRITE určuje, že se upraví sekce hodnoty *column_name* . Výraz je hodnota, která bude zkopírována do *column_name*, `@Offset` je počátečním bodem, ve kterém bude výraz napsán, a argument `@Length` je délka oddílu ve sloupci.  
  
|If|Potom si|  
|--------|----------|  
|Výraz je nastaven na hodnotu NULL.|`@Length` se ignoruje a hodnota v *column_name* se na zadaném `@Offset`zkrátí.|  
|`@Offset` je NULL.|Operace aktualizace připojí výraz na konci existující hodnoty *column_name* a `@Length` je ignorována.|  
|`@Offset` je větší než délka column_name hodnoty.|SQL Server vrátí chybu.|  
|`@Length` je NULL.|Operace aktualizace odebere všechna data z `@Offset` na konec `column_name` hodnoty.|  
  
> [!NOTE]
> Ani `@Offset` ani `@Length` nesmí být záporné číslo.  
  
## <a name="example"></a>Příklad  
 Tento příklad Transact-SQL aktualizuje částečnou hodnotu v `nvarchar(max)` DocumentSummary sloupci v tabulce dokumentů v databázi AdventureWorks. Slovo ' součásti ' je nahrazeno slovem ' Features ' zadáním nahrazujícího slova, počátečního umístění (posunu) slova, které má být nahrazeno existujícími daty, a počtem znaků, které mají být nahrazeny (délka). Příklad obsahuje příkazy SELECT před a za příkazem UPDATE pro porovnání výsledků.  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a>Práce s typy velkých hodnot v ADO.NET  
 Můžete pracovat s velkými typy hodnot v ADO.NET zadáním velkých hodnot jako <xref:System.Data.SqlClient.SqlParameter> objektů v <xref:System.Data.SqlClient.SqlDataReader> pro vrácení sady výsledků dotazu nebo pomocí <xref:System.Data.SqlClient.SqlDataAdapter> k vyplnění `DataSet`/`DataTable`. Neexistuje žádný rozdíl mezi způsobem, jakým pracujete s velkým typem hodnoty a jeho souvisejícím datovým typem s menší hodnotou.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Načtení dat pomocí GetSqlBytes  
 Metodu `GetSqlBytes` <xref:System.Data.SqlClient.SqlDataReader> lze použít k načtení obsahu `varbinary(max)`ho sloupce. Následující fragment kódu předpokládá objekt <xref:System.Data.SqlClient.SqlCommand> s názvem `cmd`, který vybere `varbinary(max)` data z tabulky a objekt <xref:System.Data.SqlClient.SqlDataReader> s názvem `reader`, který načte data jako <xref:System.Data.SqlTypes.SqlBytes>.  
  
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
 Metodu `GetSqlChars` <xref:System.Data.SqlClient.SqlDataReader> lze použít k načtení obsahu `varchar(max)` nebo `nvarchar(max)` sloupce. Následující fragment kódu předpokládá objekt <xref:System.Data.SqlClient.SqlCommand> s názvem `cmd`, který vybere `nvarchar(max)` data z tabulky a objekt <xref:System.Data.SqlClient.SqlDataReader> s názvem `reader`, který načte data.  
  
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
 Metodu `GetSqlBinary` <xref:System.Data.SqlClient.SqlDataReader> lze použít k načtení obsahu `varbinary(max)`ho sloupce. Následující fragment kódu předpokládá objekt <xref:System.Data.SqlClient.SqlCommand> s názvem `cmd`, který vybere `varbinary(max)` data z tabulky a objekt <xref:System.Data.SqlClient.SqlDataReader> s názvem `reader`, který načte data jako datový proud <xref:System.Data.SqlTypes.SqlBinary>.  
  
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
 Metoda `GetBytes` <xref:System.Data.SqlClient.SqlDataReader> čte datový proud bajtů ze zadaného posunutí sloupce do pole bajtů začínající posunem zadaného pole. Následující fragment kódu předpokládá objekt <xref:System.Data.SqlClient.SqlDataReader> s názvem `reader`, který načte bajty do pole bajtů. Všimněte si, že na rozdíl od `GetSqlBytes``GetBytes` vyžaduje velikost pro vyrovnávací paměť pole.  
  
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
 Metoda `GetValue` <xref:System.Data.SqlClient.SqlDataReader> přečte hodnotu ze zadaného posunutí sloupce do pole. Následující fragment kódu předpokládá objekt <xref:System.Data.SqlClient.SqlDataReader> s názvem `reader`, který načte binární data z prvního posunutí sloupce a pak řetězcová data z druhého posunutí sloupce.  
  
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
 Můžete převést obsah `varchar(max)` nebo `nvarchar(max)` sloupce pomocí kterékoli metody převodu řetězce, jako je například `ToString`. Následující fragment kódu předpokládá objekt <xref:System.Data.SqlClient.SqlDataReader> s názvem `reader`, který načte data.  
  
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
 Následující kód načte název a objekt `LargePhoto` z tabulky `ProductPhoto` v databázi `AdventureWorks` a uloží je do souboru. Sestavení musí být zkompilováno s odkazem na obor názvů <xref:System.Drawing>.  Metoda <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> <xref:System.Data.SqlClient.SqlDataReader> vrací objekt <xref:System.Data.SqlTypes.SqlBytes>, který zpřístupňuje vlastnost `Stream`. Kód používá tuto operaci k vytvoření nového objektu `Bitmap` a uloží jej do `ImageFormat`GIF.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Použití parametrů velkých hodnotových typů  
 Typy velkých hodnot lze použít v <xref:System.Data.SqlClient.SqlParameter> objekty stejným způsobem jako menší typy hodnot v objektech <xref:System.Data.SqlClient.SqlParameter>. Můžete načíst typy velkých hodnot jako <xref:System.Data.SqlClient.SqlParameter> hodnoty, jak je znázorněno v následujícím příkladu. Kód předpokládá, že následující uložená procedura GetDocumentSummary existuje v ukázkové databázi AdventureWorks. Uložená procedura převezme vstupní parametr s názvem @DocumentID a vrátí obsah sloupce DocumentSummary v parametru @DocumentSummary Output.  
  
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
 Kód ADO.NET vytvoří objekty <xref:System.Data.SqlClient.SqlConnection> a <xref:System.Data.SqlClient.SqlCommand> pro spuštění uložené procedury GetDocumentSummary a načte souhrn dokumentu, který je uložen jako velký typ hodnoty. Kód předá hodnotu pro vstupní parametr @DocumentID a zobrazí výsledky předané zpět v parametru @DocumentSummary Output v okně konzoly.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Binární a vysoké hodnoty na SQL Serveru](sql-server-binary-and-large-value-data.md)
- [Mapování datových typů SQL Serveru](../sql-server-data-type-mappings.md)
- [Operace dat na SQL Serveru v ADO.NET](sql-server-data-operations.md)
- [Přehled ADO.NET](../ado-net-overview.md)
