---
title: "Úprava dat (max) velké hodnoty v technologii ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8aca5f00-d80e-4320-81b3-016d0466f7ee
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e42ff73cda8fc63d9b8ae6061cfbdb9749a0a864
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="modifying-large-value-max-data-in-adonet"></a>Úprava dat (max) velké hodnoty v technologii ADO.NET
Datové typy velkého objektu (LOB) jsou ty, které překračují maximální velikost řádku 8 kilobajtů (KB). SQL Server poskytuje `max` – specifikátor pro `varchar`, `nvarchar`, a `varbinary` datové typy umožňující úložiště hodnoty větší než 2 ^ 32 bajtů. Proměnných Transact-SQL a sloupců tabulky můžou určovat `varchar(max)`, `nvarchar(max)`, nebo `varbinary(max)` datové typy. V technologii ADO.NET `max` datové typy můžete načíst pomocí `DataReader`a dá se zadat taky jako obě hodnoty vstupní a výstupní parametr bez žádným zvláštním způsobem. Pro velké `varchar` datové typy dat můžete načíst a aktualizovat postupně.  
  
 `max` Datové typy lze použít pro porovnání, jako proměnné jazyka Transact-SQL a zřetězení. Také je možné použít v DISTINCT, ORDER BY, klauzule GROUP BY příkazu SELECT, a také agreguje, spojení a poddotazy.  
  
 Následující tabulka obsahuje odkazy na dokumentaci SQL Server Books Online.  
  
 **SQL Server Books Online**  
  
1.  [Použití velké hodnoty datových typů](http://go.microsoft.com/fwlink/?LinkId=120498)  
  
## <a name="large-value-type-restrictions"></a>Omezení typu velké hodnoty.  
 Následující omezení se použijí na `max` datové typy, které nejsou k dispozici pro menší datové typy:  
  
-   A `sql_variant` nemůže obsahovat velké `varchar` datového typu.  
  
-   Velké `varchar` sloupce nelze zadat jako klíčový sloupec v indexu. Mohou v zahrnutý sloupec v neclusterovaný index.  
  
-   Velké `varchar` sloupce nelze použít jako dělení klíčové sloupce.  
  
## <a name="working-with-large-value-types-in-transact-sql"></a>Práce s typy velké hodnoty v Transact-SQL  
 Transact-SQL `OPENROWSET` jednorázové metoda připojení a přístup vzdálených dat je funkce. Obsahuje všechny informace o připojení, která je nezbytná k přístupu vzdálených dat ze zdroje dat OLE DB. `OPENROWSET`může být odkazováno v klauzuli FROM dotazu, jako by byl název tabulky. Ho lze také odkazovat jako cílová tabulka INSERT, UPDATE, nebo odstranit příkaz závisejí na možnostech zprostředkovatele OLE DB.  
  
 `OPENROWSET` Zahrnuje funkce `BULK` poskytovatel sady řádků, které umožňuje číst data přímo ze souboru bez načítání dat do cílové tabulky. To umožňuje používat `OPENROWSET` v jednoduchý příkaz INSERT SELECT.  
  
 `OPENROWSET``BULK` Možnost argumenty poskytují významné kontrolu nad kde začínat a končit čtení dat, jak nakládat s chybami a jak interpretovat data. Například můžete zadat, že datový soubor přečíst jako jeden řádek, jeden sloupec sady řádků typu `varbinary`, `varchar`, nebo `nvarchar`. Pro dokončení syntaxe a parametry najdete v části SQL Server Books Online.  
  
 Následující příklad vloží do tabulky Fotografievýrobku v ukázkové databázi AdventureWorks fotografie. Při použití `BULK``OPENROWSET` poskytovatele, je nutné zadat pojmenovaný seznam sloupců, i pokud nejsou vložení hodnoty do každý sloupec. Primární klíč v takovém případě je definován jako sloupec identity a může být vynechán ze seznamu sloupců. Všimněte si, že je třeba zadat také název korelace na konci `OPENROWSET` příkaz, který v tomto případě je ThumbnailPhoto. To se sloupci v korelaci `ProductPhoto` tabulky do které je právě načítán soubor.  
  
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
  
## <a name="updating-data-using-update-write"></a>Aktualizace dat pomocí aktualizace. ZÁPIS  
 Příkaz Transact-SQL aktualizace má nové syntaxe zápisu úpravy obsah `varchar(max)`, `nvarchar(max)`, nebo `varbinary(max)` sloupce. To umožňuje provádět částečné aktualizace dat. AKTUALIZACE. ZAPSAT syntaxe je tady uvedené v zkrácené formě:  
  
 UPDATE  
  
 { *\<object>* }  
  
 NASTAVENÍ  
  
 { *column_name* = {. ZÁPIS ( *výraz* , @Offset , @Length )}  
  
 Metody zápisu určuje, že část hodnoty *column_name* budou upraveny. Výraz je hodnota, která se zkopírují na *column_name*, `@Offset` je počáteční bod, ve kterém se zapíšou výraz, a `@Length` argument je délka části ve sloupci.  
  
|If|Pak...|  
|--------|----------|  
|Výraz je nastaven na hodnotu NULL|`@Length`je ignorován a hodnotou v *column_name* se zkrátí v zadaném `@Offset`.|  
|`@Offset`má hodnotu NULL.|Operace aktualizace připojí výraz na konci existující *column_name* hodnotu a `@Length` je ignorována.|  
|`@Offset`je větší než délka hodnoty column_name|SQL Server vrátí chybu.|  
|`@Length`má hodnotu NULL.|Operace aktualizace odeberete všechna data z `@Offset` na konec `column_name` hodnotu.|  
  
> [!NOTE]
>  Ani `@Offset` ani `@Length` může být záporné číslo.  
  
## <a name="example"></a>Příklad  
 Tento příklad Transact-SQL aktualizace částečné hodnoty v DocumentSummary, `nvarchar(max)` sloupec v dokumentu tabulky v databázi AdventureWorks. Slovo "součástmi" je nahrazena slovo "funkce" tak, že zadáte word nahrazení, od umístění (posun) aplikace word ve stávající data a počet znaků, který má být nahrazené (délka) mají být nahrazeny. Příklad obsahuje příkazy SELECT před a po příkazu aktualizace můžete porovnat výsledky.  
  
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
  
## <a name="working-with-large-value-types-in-adonet"></a>Práce s typy velké hodnoty v technologii ADO.NET  
 Můžete pracovat s typy velké hodnoty v ADO.NET zadáním velké hodnoty typy jako <xref:System.Data.SqlClient.SqlParameter> objekty v <xref:System.Data.SqlClient.SqlDataReader> vrácení výsledku nastaveny, nebo pomocí <xref:System.Data.SqlClient.SqlDataAdapter> k vyplnění `DataSet` / `DataTable`. Není žádný rozdíl mezi způsobu práce s typem velké hodnoty a jeho souvisejících, menší hodnota datového typu.  
  
### <a name="using-getsqlbytes-to-retrieve-data"></a>Pomocí GetSqlBytes k načtení dat  
 `GetSqlBytes` Metodu <xref:System.Data.SqlClient.SqlDataReader> slouží k načtení obsahu `varbinary(max)` sloupce. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt s názvem `cmd` , vybere `varbinary(max)` data z tabulky a <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , načte data jako <xref:System.Data.SqlTypes.SqlBytes>.  
  
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
  
### <a name="using-getsqlchars-to-retrieve-data"></a>Pomocí GetSqlChars k načtení dat  
 `GetSqlChars` Metodu <xref:System.Data.SqlClient.SqlDataReader> slouží k načtení obsahu `varchar(max)` nebo `nvarchar(max)` sloupce. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt s názvem `cmd` , vybere `nvarchar(max)` data z tabulky a <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , načte data.  
  
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
  
### <a name="using-getsqlbinary-to-retrieve-data"></a>Pomocí GetSqlBinary k načtení dat  
 `GetSqlBinary` Metodu <xref:System.Data.SqlClient.SqlDataReader> slouží k načtení obsahu `varbinary(max)` sloupce. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlCommand> objekt s názvem `cmd` , vybere `varbinary(max)` data z tabulky a <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , načte data jako <xref:System.Data.SqlTypes.SqlBinary> datového proudu.  
  
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
  
### <a name="using-getbytes-to-retrieve-data"></a>Pomocí GetBytes k načtení dat  
 `GetBytes` Metodu <xref:System.Data.SqlClient.SqlDataReader> čte datového proudu bajtů z posun zadané sloupce do bajtového pole začínající na posunu zadané pole. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , načte bajtů do bajtového pole. Všimněte si, že na rozdíl od `GetSqlBytes`, `GetBytes` vyžaduje velikost vyrovnávací paměti pole.  
  
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
  
### <a name="using-getvalue-to-retrieve-data"></a>Pomocí GetValue k načtení dat  
 `GetValue` Metodu <xref:System.Data.SqlClient.SqlDataReader> načte hodnotu z posun zadané sloupce do pole. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , načte binární data z prvního sloupce posun a pak řetězcová data z druhé posun sloupce.  
  
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
  
## <a name="converting-from-large-value-types-to-clr-types"></a>Převod z typů velkých hodnot pro typy CLR  
 Můžete převést obsah `varchar(max)` nebo `nvarchar(max)` sloupce pomocí některé z metod pro převod řetězce, například `ToString`. Následující fragment kódu předpokládá <xref:System.Data.SqlClient.SqlDataReader> objekt s názvem `reader` , načte data.  
  
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
 Následující kód načte název a `LargePhoto` objektu z `ProductPhoto` tabulky v `AdventureWorks` databáze a uloží do souboru. Sestavení musí být zkompilovány s odkazem na <xref:System.Drawing> oboru názvů.  <xref:System.Data.SqlClient.SqlDataReader.GetSqlBytes%2A> Metodu <xref:System.Data.SqlClient.SqlDataReader> vrátí <xref:System.Data.SqlTypes.SqlBytes> objekt, který zveřejňuje `Stream` vlastnost. Tento kód používá k vytvoření nové `Bitmap` objekt a uloží ho do Gif `ImageFormat`.  
  
 [!code-csharp[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Photo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Photo/VB/source.vb#1)]  
  
## <a name="using-large-value-type-parameters"></a>Pomocí parametrů typu velké hodnoty  
 Typy velké hodnoty mohou být používány <xref:System.Data.SqlClient.SqlParameter> objekty stejným způsobem jako menší hodnotu typy v <xref:System.Data.SqlClient.SqlParameter> objekty. Můžete načíst typy velké hodnoty jako <xref:System.Data.SqlClient.SqlParameter> hodnoty, jak je znázorněno v následujícím příkladu. Kód předpokládá, že následující postup GetDocumentSummary uložené existuje v ukázkové databázi AdventureWorks. Uložená procedura používá vstupní parametr s názvem @DocumentID a vrátí obsah DocumentSummary sloupce v @DocumentSummary výstupní parametr.  
  
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
 Vytvoří kód ADO.NET <xref:System.Data.SqlClient.SqlConnection> a <xref:System.Data.SqlClient.SqlCommand> objektů spuštění GetDocumentSummary uložené procedury a načtení dokumentu souhrn, které je uložený jako typ velké hodnoty. Kód předá hodnotu @DocumentID vstupní parametr a zobrazí výsledky předaný zpět @DocumentSummary výstupní parametr v okně konzoly.  
  
 [!code-csharp[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/CS/source.cs#1)]
 [!code-vb[DataWorks LargeValueType.Param#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks LargeValueType.Param/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Binární a vysoké hodnoty na SQL Serveru](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [Mapování datových typů SQL Serveru](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [Operace dat na SQL Serveru v ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
