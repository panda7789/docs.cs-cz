---
title: Statistiky Provider pro SQL Server
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
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 87f3dfbb3af6e638207d68540217f7134b95c354
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="provider-statistics-for-sql-server"></a>Statistiky Provider pro SQL Server
Od verze rozhraní .NET Framework verze 2.0, zprostředkovatel dat .NET Framework pro SQL Server podporuje spuštění statistiky. Je nutné povolit statistiky nastavením <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> vlastnost <xref:System.Data.SqlClient.SqlConnection> do objektu `True` po máte platné připojení objekt vytvořený. Po statistiky jsou povolené, můžete zkontrolovat, je jako "snímek v čase" načtením <xref:System.Collections.IDictionary> odkazovat pomocí <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> metodu <xref:System.Data.SqlClient.SqlConnection> objektu. Pomocí seznamu pro výčet jako sada položky slovníku dvojice název hodnota. Tyto páry název/hodnota neuspořádaného. Kdykoli můžete volat <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> metodu <xref:System.Data.SqlClient.SqlConnection> objekt, který chcete reset počítadla. Pokud není povolený statistiky shromažďování, není vygeneruje výjimku. Kromě toho pokud <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> je volána bez <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> nutnosti nejprve zavolat, jsou hodnoty získané počáteční hodnoty pro každou položku. Pokud povolíte statistiky, spusťte aplikaci nějakou dobu a pak zakažte statistiky, hodnoty získané se projeví až do chvíle, kdy byly zakázány statistiky shromážděné hodnoty. Všechny statistické hodnoty získané jsou na základě jednotlivých připojení.  
  
## <a name="statistical-values-available"></a>Statistické hodnoty, které jsou k dispozici  
 Aktuálně nejsou k dispozici od zprostředkovatele Microsoft SQL Server 18 různé položky. Počet položek, které jsou k dispozici je přístupná prostřednictvím **počet** vlastnost <xref:System.Collections.IDictionary> rozhraní odkaz vrácený <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>. Všechny čítače pro zprostředkovatele statistiky použít modul common language runtime <xref:System.Int64> typu (**dlouho** v C# a Visual Basic), což je 64bitová verze široké. Maximální hodnota, která **int64** datového typu, podle definice **int64. MaxValue** pole, je ((2^63)-1)). Pokud hodnoty čítačů dosáhnou tato maximální hodnota, se již nebude považovat za přesná. To znamená, že **int64. MaxValue**-1((2^63)-2) je efektivně největší platnou hodnotu pro všechny statistiky.  
  
> [!NOTE]
>  Slovník se používá k vrácení zprostředkovatele statistiky, protože může v budoucnu změnit počet, názvy a pořadí vrácených statistiky. Aplikace neměli spoléhat na určitou hodnotu se ve slovníku nalezena, ale měli místo toho zkontrolujte, jestli hodnota je k dispozici a odpovídajícím způsobem větev.  
  
 Následující tabulka popisuje aktuální statistické hodnoty k dispozici. Všimněte si, že názvy klíčů pro jednotlivé hodnoty nejsou lokalizovány mezi místní verze rozhraní Microsoft .NET Framework.  
  
|Název klíče|Popis|  
|--------------|-----------------|  
|`BuffersReceived`|Vrátí počet tabular data stream (TDS) paketů přijatých zprostředkovatele ze systému SQL Server po aplikace bylo zahájeno pomocí zprostředkovatele a jestli má povolenou statistiky.|  
|`BuffersSent`|Vrátí počet paketů TDS odesílá do systému SQL Server zprostředkovatele poté, co byly povoleny statistiky. Velké příkazy může vyžadovat více vyrovnávací paměti. Například, pokud velké příkaz odeslán do serveru a vyžaduje šesti pakety `ServerRoundtrips` se zvýší o jeden a `BuffersSent` se zvýší o šest.|  
|`BytesReceived`|Vrátí počet bajtů dat do TDS paketů přijatých zprostředkovatele ze systému SQL Server, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.|  
|`BytesSent`|Vrátí počet bajtů dat odeslaných k systému SQL Server v paketech TDS po aplikace bylo zahájeno pomocí zprostředkovatele a jestli má povolenou statistiky.|  
|`ConnectionTime`|Množství času (v milisekundách), které bylo připojení otevřené po povolili statistiky (celková doba připojení, pokud statistiky byly povoleny před otevřením připojení).|  
|`CursorOpens`|Vrátí počet opakovaných kurzoru byla otevřena prostřednictvím připojení, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.<br /><br /> Všimněte si, že jen pro čtení jen nebo předání výsledky vrácené příkazů SELECT nejsou považovány za kurzory a proto neovlivní tento čítač.|  
|`ExecutionTime`|Vrátí kumulativní množství času (v milisekundách), že má zprostředkovatel strávený zpracováváním po povolili statistiky, včetně doby čekání pro odpovědi ze serveru, jakož i čas strávený provádění kódu ve zprostředkovateli sám sebe.<br /><br /> Třídy, které zahrnují časování kódu jsou:<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Pokud chcete zachovat výkon kritické členy co nejmenší, nejsou vypršel časový limit následující členy:<br /><br /> SqlDataReader<br /><br /> Tento [] – operátor (všechny přetížení)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> Getguid –<br /><br /> Getint16 –<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName –<br /><br /> Getordinal –<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString –<br /><br /> IsDBNull|  
|`IduCount`|Vrátí celkový počet příkazy INSERT, odstranění a aktualizaci provést prostřednictvím připojení, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.|  
|`IduRows`|Vrátí celkový počet řádků, které jsou ovlivněné příkazy INSERT, odstranění a aktualizaci provést prostřednictvím připojení, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.|  
|`NetworkServerTime`|Vrátí kumulativní množství času (v milisekundách), který zprostředkovatel stráví čekáním na odpovědi ze serveru, jakmile aplikace bylo zahájeno pomocí zprostředkovatele a jestli má povolenou statistiky.|  
|`PreparedExecs`|Vrátí počet připravené příkazů provést prostřednictvím připojení, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.|  
|`Prepares`|Vrátí počet prohlášení připravený prostřednictvím připojení, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky.|  
|`SelectCount`|Vrátí počet příkazů SELECT provést prostřednictvím připojení, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky. To zahrnuje příkazech NAČTENÍ načíst řádky z kurzory a počet příkazů SELECT se aktualizuje po konci <xref:System.Data.SqlClient.SqlDataReader> je dosaženo.|  
|`SelectRows`|Vrátí počet řádků, které jsou vybrané, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky. Tento čítač zobrazuje všechny řádky generované příkazy SQL, i ty, které nejsou ve skutečnosti uplatníte volající. Například zavření čtecí modul dat než si přečtete celou sadu výsledků neovlivní počet. To zahrnuje řádky načítají kurzory prostřednictvím příkazech NAČTENÍ.|  
|`ServerRoundtrips`|Vrátí počet připojení odeslat příkazy na server a obdržel odpověď zpět po aplikace bylo zahájeno pomocí zprostředkovatele a jestli má povolenou statistiky.|  
|`SumResultSets`|Vrátí počet výsledků sad, které již byly použity, jakmile se aplikace bylo zahájeno pomocí zprostředkovatele a povolil statistiky. Například to bude zahrnovat všechny sadu výsledků vrácen do klienta. Pro kurzory považuje za každé operace načtení nebo bloku fetch sadu nezávislé výsledek.|  
|`Transactions`|Vrátí počet spuštění po aplikace bylo zahájeno pomocí zprostředkovatele a jestli má povolenou statistické údaje, včetně odvolání uživatelské transakce. Pokud je službou potvrzení automaticky na připojení, považuje za každý příkaz transakce.<br /><br /> Tento čítač zvýší počet transakcí, jakmile se spustí příkaz BEGIN TRAN, bez ohledu na to, jestli je transakce potvrzena nebo vrátit později.|  
|`UnpreparedExecs`|Vrátí počet neupravený příkazy spustit prostřednictvím připojení, jakmile aplikace bylo zahájeno pomocí zprostředkovatele a jestli má povolenou statistiky.|  
  
### <a name="retrieving-a-value"></a>Načítání hodnoty  
 Následující aplikace konzoly ukazuje, jak povolit statistické údaje o připojení, načtěte čtyři hodnoty jednotlivých statistiky a zapisuje je do okna konzoly.  
  
> [!NOTE]
>  Následující příklad používá vzorku **AdventureWorks** databáze součástí [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. V ukázkovém kódu v zadaném připojovacím řetězci předpokládá, že databáze je nainstalovaná a k dispozici v místním počítači. Upravte připojovací řetězec v případě potřeby pro vaše prostředí.  
  
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
  
### <a name="retrieving-all-values"></a>Načítání všechny hodnoty  
 Následující aplikace konzoly ukazuje, jak povolit statistické údaje o připojení, načíst všechny hodnoty k dispozici statistiky použití enumerátor a jejich zápis do okna konzoly.  
  
> [!NOTE]
>  Následující příklad používá vzorku **AdventureWorks** databáze součástí [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]. V ukázkovém kódu v zadaném připojovacím řetězci předpokládá, že databáze je nainstalovaná a k dispozici v místním počítači. Upravte připojovací řetězec v případě potřeby pro vaše prostředí.  
  
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
  
## <a name="see-also"></a>Viz také  
 [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
