---
title: Úpravy velké hodnotu (maximální) dat v ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
ms.openlocfilehash: c77d688afa19caf1d54adf93b9fb6cf8b1c4701d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493895"
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Úpravy velké hodnotu (maximální) dat v ADO.NET
Rozsáhlého objektu (LOB) datové typy jsou ty, které překračují maximální velikost řádku 8 kilobajtů (KB). SQL Server poskytuje `max` specifikátor pro `varchar`, `nvarchar`, a `varbinary` datové typy, aby umožňovala ukládání hodnoty větší než 2 ^ 32 bajtů. Zadat sloupce tabulky a proměnných jazyka Transact-SQL `varchar(max)`, `nvarchar(max)`, nebo `varbinary(max)` datové typy. V ADO.NET `max` datové typy lze načíst pomocí `DataReader`a je taky možné specifikovat jako obě hodnoty vstupní a výstupní parametr bez žádným zvláštním způsobem. Pro velké `varchar` datové typy dat, dají se načíst a přírůstkově aktualizovat.  
  
 `max` Datových typů lze použít pro porovnání, jako proměnné jazyka Transact-SQL a pro zřetězení. Také je možné použít v DISTINCT, ORDER BY, klauzule GROUP BY příkazu SELECT, stejně jako v agregace, spojení a poddotazy.  
  
 Následující tabulka obsahuje odkazy na dokumentaci SQL Server Books Online.  
  
 **SQL Server Books Online**  
  
1.  [Použití vysoké hodnoty datových typů](https://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>Typ velké hodnoty omezení  
 Následující omezení platí pro `max` datové typy, které neexistují pro menší datové typy:  
  
-   A `sql_variant` nemůže obsahovat velké `varchar` datového typu.  
  
-   Velké `varchar` sloupců nemůže být určen jako klíčový sloupec v indexu. Můžou v zahrnutý sloupec v neclusterovaný index.  
  
-   Velké `varchar` sloupce nelze použít jako dělení klíčových sloupců.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Práce s typy velké hodnoty v jazycích Transact-SQL  
 Příkazů jazyka Transact-SQL `OPENROWSET` funkce je jednorázový metoda připojování a přístup ke vzdáleným datům. Obsahuje všechny informace o připojení, která je nezbytná pro přístup ke vzdáleným datům ze zdroje dat OLE DB. `OPENROWSET` může být odkazováno v klauzuli FROM dotazu, jako by šlo název tabulky. Lze také odkazovat jako cílové tabulce příkazu INSERT, UPDATE, nebo odstraňte příkaz, v souladu s možností zprostředkovatele OLE DB.  
  
 `OPENROWSET` Zahrnuje funkce `BULK` poskytovatel sady řádků, které umožňuje číst data přímo ze souboru bez načítání dat do cílové tabulky. To umožňuje používat `OPENROWSET` v jednoduchý příkaz INSERT SELECT.  
  
 `OPENROWSET BULK` Argumenty možnost poskytnout významnou kontrolu nad tím, kam se začínají i končí čtení dat, jak zacházet s chybami a jak interpretovat data. Například můžete určit, že datový soubor přečíst jako jeden řádek, jeden sloupec sady řádků typu `varbinary`, `varchar`, nebo `nvarchar`. Pro úplnou syntaxi a možnosti najdete v tématu knihy Online SQL Server.  
  
 V následujícím příkladu vloží fotografii do ProductPhoto tabulky v ukázkové databázi AdventureWorks. Při použití `BULK OPENROWSET` poskytovatele, je nutné zadat pojmenovaný seznam sloupců, i pokud nejsou vkládání hodnot do každý sloupec. Primární klíč v tomto případě je definován jako sloupec identity a může být vynechán ze seznamu sloupců. Všimněte si, že je třeba zadat také název korelace na konci `OPENROWSET` příkazu, který v tomto případě je thumbnailphoto nastavuje. To souvisí se sloupcem v `ProductPhoto` tabulku, do které se načítá soubor.  
  
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
  
## <a name="updating-data-using-update-write"></a>Aktualizace dat používání aktualizace. ZÁPIS  
 Příkaz jazyka Transact-SQL pro sadu VS11 má nové syntaxe zápisu pro úpravu obsahu `varchar(max)`, `nvarchar(max)`, nebo `varbinary(max)` sloupce. To umožňuje provádět částečné aktualizace data. AKTUALIZACE. Zápis syntaxe se tady zobrazí ve zkrácené formě:  
  
 UPDATE  
  
 {  *\<objektu >* }  
  
 NASTAVIT  
  
 { *column_name* = {. ZÁPIS ( *výraz* , @Offset , @Length )}  
  
 Metody zápisu určuje, že část hodnoty *column_name* budou upraveny. Výraz je hodnota, kterou bude zkopírován do *column_name*, `@Offset` se počáteční bod, ve kterém se zapíše výraz, a `@Length` argument je délku části ve sloupci.  
  
|If|Pak...|  
|--------|----------|  
|Výraz je nastavena na hodnotu NULL|`@Length` je ignorována a hodnotou v *column_name* zkrácen v zadaném `@Offset`.|  
|`@Offset` je rovno hodnotě NULL|Operace update připojí výraz na konci existujícího *column_name* hodnotu a `@Length` se ignoruje.|  
|`@Offset` je větší než délka hodnoty column_name|SQL Server vrátí chybu.|  
|`@Length` je rovno hodnotě NULL|Operace aktualizace odebere všechna data z `@Offset` na konec objektu `column_name` hodnotu.|  
  
> [!NOTE]
>  Ani `@Offset` ani `@Length` může být záporné číslo.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu příkazů jazyka Transact-SQL aktualizuje hodnotu do částečné DocumentSummary, `nvarchar(max)` sloupec v tabulce dokument v databázi AdventureWorks. Slovo "součástmi" se nahrazuje slovo "funkce" tak, že určíte slovo nahrazení, počáteční umístění (posun) slova, třeba nahradit stávající data a počet znaků, které mají být nahrazeny (délka). Příklad obsahuje příkazy SELECT, před a po příkazu UPDATE k porovnání výsledků.  
  
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
 Můžete pracovat s typů velkých hodnot v ADO.NET zadáním typů velkých hodnot jako <xref:System.Data.SqlClient.SqlParameter> objekty v <xref:System.Data.SqlClient.SqlDataReader> vrátit požadovaný výsledek, nastavení, nebo pomocí <xref:System.Data.SqlClient.SqlDataAdapter> tak, aby vyplnil `DataSet` / `DataTable`. Není žádný rozdíl mezi stejným způsobem jako při práci s typem velké hodnoty a jeho souvisejících, menší hodnota datového typu.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Použití GetSqlBytes k načtení dat  
 `GetSqlBytes` Metodu <xref:System.Data.SqlClient.SqlDataReader> slouží k načtení obsahu `varbinary(max)` sloupce. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt s názvem `cmd` , který vybere `varbinary(max)` data z tabulky a <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` načítající data jako <xref:System.Data.SqlTypes.SqlBytes>.  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Použití GetSqlChars k načtení dat  
 `GetSqlChars` Metodu <xref:System.Data.SqlClient.SqlDataReader> slouží k načtení obsahu `varchar(max)` nebo `nvarchar(max)` sloupce. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt s názvem `cmd` , který vybere `nvarchar(max)` data z tabulky a <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , který načítá data.  
  
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
 `GetSqlBinary` Metodu <xref:System.Data.SqlClient.SqlDataReader> slouží k načtení obsahu `varbinary(max)` sloupce. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt s názvem `cmd` , který vybere `varbinary(max)` data z tabulky a <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` načítající data jako <xref:System.Data.SqlTypes.SqlBinary> datového proudu.  
  
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
 `GetBytes` Metodu <xref:System.Data.SqlClient.SqlDataReader> načteme posun určený sloupec datového proudu bajtů do bajtového pole začínající na posunu určeného pole. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` bajtů, který načte do bajtového pole. Všimněte si, že na rozdíl od `GetSqlBytes`, `GetBytes` vyžaduje zadání velikosti pole vyrovnávací paměti.  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a>Použití GetValue k načtení dat  
 `GetValue` Metodu <xref:System.Data.SqlClient.SqlDataReader> přečte hodnotu do pole počínaje posunutím zadaný sloupec. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , posun binární data načte z prvního sloupce a potom data z druhé posun sloupce řetězce.  
  
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
 Můžete převést obsah `varchar(max)` nebo `nvarchar(max)` sloupec některou z metod pro převod řetězce, jako například `ToString`. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , který načítá data.  
  
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
 Následující kód načte název a `LargePhoto` objektu z `ProductPhoto` v tabulku `AdventureWorks` databáze a uloží jej do souboru. Sestavení musí být zkompilovány s odkazem na <xref:System.Drawing> oboru názvů.  <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Metodu <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.SqlTypes.SqlBytes> objekt, který zpřístupňuje `Stream` vlastnost. Tento kód používá k vytvoření nového `Bitmap` objekt a uloží ho do Gif `ImageFormat`.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Pomocí parametrů typ velké hodnoty  
 Může být používáno velké hodnoty <xref:System.Data.SqlClient.SqlParameter> objekty stejným způsobem použít menší hodnotu napíše <xref:System.Data.SqlClient.SqlParameter> objekty. Můžete načíst typy velké hodnoty jako <xref:System.Data.SqlClient.SqlParameter> hodnoty, jak je znázorněno v následujícím příkladu. Kód předpokládá, že následující GetDocumentSummary uložené procedury existuje v ukázkové databázi AdventureWorks. Uložené procedury přijímá vstupní parametr s názvem @DocumentID a vrátí obsah DocumentSummary sloupec v @DocumentSummary výstupní parametr.  
  
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
 Vytvoří kód ADO.NET <xref:System.Data.SqlClient.SqlConnection> a <xref:System.Data.SqlClient.SqlCommand> objekty spuštění GetDocumentSummary uložené procedury a načíst shrnutí, dokumentů, které se ukládá jako typ velké hodnoty. Kód předá hodnotu @DocumentID vstupní parametr a zobrazí výsledky se předat zpátky @DocumentSummary výstupní parametr v okně konzoly.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Binární a vysoké hodnoty na SQL Serveru](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [Mapování datových typů SQL Serveru](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [Operace dat na SQL Serveru v ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
