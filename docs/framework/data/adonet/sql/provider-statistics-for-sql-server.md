---
title: Statistiky zprostředkovatelů na SQL Serveru
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: b2b63719149c21eba493b3d8f2fc65309515bb0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646006"
---
# <a name="provider-statistics-for-sql-server"></a>Statistiky zprostředkovatelů na SQL Serveru
Od verze rozhraní .NET Framework verze 2.0, zprostředkovatele dat .NET Framework pro SQL Server podporuje běhové statistiky. Je nutné povolit statistiky tak, že nastavíte <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> objektu `True` po máte platné připojení objekt vytvořený. Po statistiky jsou povolené, můžete zkontrolovat je jako "snímku v čase" načtením <xref:System.Collections.IDictionary> odkazovat prostřednictvím <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> metodu <xref:System.Data.SqlClient.SqlConnection> objektu. Můžete zobrazit výčet prostřednictvím seznamu jako sada položek slovníku dvojice název/hodnota. Tyto páry název/hodnota Neseřazený. Kdykoli můžete volat <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> metodu <xref:System.Data.SqlClient.SqlConnection> objekt resetovat počítadla. Pokud statistiky shromažďování není povolený, výjimka se nevygeneroval. Kromě toho pokud <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> je volána bez <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> s byla nejdříve volána, jsou hodnoty získané počáteční hodnoty pro každou položku. Pokud povolíte statistiky, spusťte aplikaci na dobu a potom zakázat statistiky, hodnoty získané bude odpovídat hodnotám shromážděných až do chvíle, kdy byly zakázány statistiky. Na jednotlivá připojení jsou všechny statistické hodnoty shromážděné.  
  
## <a name="statistical-values-available"></a>Statistické hodnoty, které jsou k dispozici  
 Aktuálně nejsou k dispozici od poskytovatele serveru Microsoft SQL Server 18 různých položek. Počet položek, které jsou k dispozici je přístupná prostřednictvím **počet** vlastnost <xref:System.Collections.IDictionary> rozhraní vrácený odkaz <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>. Všechny čítače pro statistiky zprostředkovatelů používat modul common language runtime <xref:System.Int64> typ (**dlouhé** v C# a Visual Basic), což je 64 bitů široké. Maximální hodnota **int64** datový typ, podle definice **int64. Hodnota MaxValue** pole, je ((2^63)-1)). Pokud hodnoty čítačů dosáhnou této maximální hodnotu, se mají už považovat přesné. To znamená, že **int64. Hodnota MaxValue**-1((2^63)-2) je v podstatě největší platná hodnota pro všechny statistiky.  
  
> [!NOTE]
>  Slovník se používá k vrácení statistiky zprostředkovatelů, protože číslo, názvy a pořadí vrácených statistik může v budoucnu změnit. Neměli byste tedy spoléhat na určitou hodnotu se nenašel ve slovníku aplikace, ale místo toho zkontrolujte, zda hodnota je k dispozici a odpovídajícím způsobem větve.  
  
 Následující tabulka popisuje aktuální statistické hodnoty. Všimněte si, že názvy klíčů pro jednotlivé hodnoty nejsou lokalizovány do místní verze rozhraní Microsoft .NET Framework.  
  
|Název klíče|Popis|  
|--------------|-----------------|  
|`BuffersReceived`|Vrátí počet datového proudu (protokolu TDS) paketů přijatých zprostředkovatele ze systému SQL Server po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.|  
|`BuffersSent`|Vrátí počet TDS paketům odeslaným do systému SQL Server zprostředkovatelem po statistiky byly povoleny. Velké příkazů může vyžadovat více vyrovnávacích pamětí. Například, pokud velké příkaz odeslán do serveru a vyžaduje šest pakety `ServerRoundtrips` se zvýší o jedna a `BuffersSent` je zvýšen o šest.|  
|`BytesReceived`|Vrátí počet bajtů dat v paketech TDS přijatých zprostředkovatele ze systému SQL Server po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.|  
|`BytesSent`|Vrátí počet bajtů dat odeslaných k systému SQL Server v paketech TDS po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.|  
|`ConnectionTime`|Množství času (v milisekundách), které bylo připojení otevřené po statistiky byly povoleny (celková doba připojení, pokud statistiky byly povoleny před otevřením připojení).|  
|`CursorOpens`|Vrátí počet pokusů, které kurzor byl otevřen prostřednictvím připojení, jakmile aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.<br /><br /> Mějte na paměti, že – pouze pro předávání – jen pro čtení výsledky vrácené příkazy SELECT nejsou považovány za ukazatele a proto nemají vliv na tento čítač.|  
|`ExecutionTime`|Vrátí souhrnně za dobu (v milisekundách), že zprostředkovatel strávil zpracování po povolili statistiky, včetně času strávenému čekáním odpovědi ze serveru, jakož i čas strávený prováděním kódu v samotného poskytovatele.<br /><br /> Třídy, které obsahují kód časování jsou:<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Pokud chcete zachovat výkon důležité členy co nejmenší, nejsou vypršel časový limit následující členy:<br /><br /> SqlDataReader<br /><br /> Tato [] – operátor (všechna přetížení)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> Getordinal –<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|Vrátí celkový počet příkazů INSERT, odstranění a aktualizace provést přes připojení po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.|  
|`IduRows`|Vrátí celkový počet řádky ovlivněné příkazy INSERT, odstranění a aktualizace provést přes připojení po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.|  
|`NetworkServerTime`|Vrátí souhrnně za dobu (v milisekundách), který stráví poskytovateli čekání na odpovědi ze serveru po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.|  
|`PreparedExecs`|Vrátí počet připravené příkazy provést přes připojení po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.|  
|`Prepares`|Vrátí počet příkazů připravili prostřednictvím připojení po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.|  
|`SelectCount`|Vrátí počet příkazů SELECT provést přes připojení po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky. Jedná se o NAČTENÍ příkazy načíst řádky z kurzory a počet pro příkazy SELECT se aktualizuje při ukončení <xref:System.Data.SqlClient.SqlDataReader> je dosaženo.|  
|`SelectRows`|Vrátí počet řádků, které vybraná aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky. Tento čítač zobrazuje všechny řádky generované příkazy SQL, včetně těch, které nejsou ve skutečnosti používané volající. Například zavření čtecí modul dat před čtením úplná sada výsledků nebude mít vliv na počet. To zahrnuje načtených z kurzory prostřednictvím příkazů načítání řádků.|  
|`ServerRoundtrips`|Vrátí určený počet pokusů o připojení odesílat příkazy na serveru a obdržel odpověď zpět po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.|  
|`SumResultSets`|Vrátí počet výsledků sad, které již byly použity po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky. Například to bude zahrnovat všechny sadu výsledků, který je vrácen do klienta. Pro ukazatele považuje každé operace načítání nebo fetch bloku sady nezávislých výsledek.|  
|`Transactions`|Vrátí počet spuštění po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky, včetně vrácení zpět uživatelské transakce. Pokud připojení je spuštěna s režim automatického potvrzení na, každý příkaz se považuje za transakci.<br /><br /> Tento čítač zvýší počet transakcí, poté, co je proveden příkaz BEGIN TRAN, bez ohledu na to, jestli transakce potvrzena nebo vrácena zpět později.|  
|`UnpreparedExecs`|Vrátí počet neupravený příkazy provést přes připojení po aplikace byla spuštěna pomocí zprostředkovatele a má povolený statistiky.|  
  
### <a name="retrieving-a-value"></a>Načítání hodnoty  
 Následující konzolové aplikace ukazuje, jak povolit statistické údaje o připojení, načíst čtyři hodnoty jednotlivých statistiky a zapíše je v okně konzoly.  
  
> [!NOTE]
>  Následující příklad používá ukázku **AdventureWorks** databáze je součástí systému SQL Server. Připojovací řetězec k dispozici ve vzorovém kódu předpokládá, že databáze je nainstalováný a dostupný na místním počítači. Úprava připojovacího řetězce podle potřeby pro vaše prostředí.  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a>Načítání všech hodnot  
 Následující konzolové aplikace ukazuje, jak povolit statistické údaje o připojení, načíst všechny dostupné statistiky hodnoty pomocí čítače výčtu a zapisuje je do okna konzoly.  
  
> [!NOTE]
>  Následující příklad používá ukázku **AdventureWorks** databáze je součástí systému SQL Server. Připojovací řetězec k dispozici ve vzorovém kódu předpokládá, že databáze je nainstalováný a dostupný na místním počítači. Úprava připojovacího řetězce podle potřeby pro vaše prostředí.  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrive it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
