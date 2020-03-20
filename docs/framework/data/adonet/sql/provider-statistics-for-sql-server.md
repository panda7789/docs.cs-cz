---
title: Statistiky zprostředkovatelů na SQL Serveru
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: 5e37a04ff731a99664d636e0d4175f99214c2646
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174508"
---
# <a name="provider-statistics-for-sql-server"></a>Statistiky zprostředkovatelů na SQL Serveru
Počínaje rozhraním .NET Framework verze 2.0 podporuje zprostředkovatel dat rozhraní .NET Framework pro SQL Server statistiky za běhu. Statistiku je nutné <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> povolit <xref:System.Data.SqlClient.SqlConnection> nastavením `True` vlastnosti objektu po vytvoření platného objektu připojení. Po povolení statistiky, můžete zkontrolovat jako "snímek v <xref:System.Collections.IDictionary> čase" <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> načtením <xref:System.Data.SqlClient.SqlConnection> odkazu prostřednictvím metody objektu. Můžete vytvořit výčet prostřednictvím seznamu jako sadu položek slovníku pár ů názvu/hodnoty. Tyto dvojice název/hodnota jsou neuspořádané. Kdykoli můžete volat metodu <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> objektu <xref:System.Data.SqlClient.SqlConnection> k obnovení čítačů. Pokud shromažďování statistik nebyla povolena, není generována výjimka. Kromě toho <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> pokud je <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> volána bez byly volány jako první, načtené hodnoty jsou počáteční hodnoty pro každou položku. Pokud povolíte statistiky, spusťte aplikaci na chvíli a potom zakázat statistiky, načtené hodnoty bude odrážet hodnoty shromážděné až do bodu, kde byly zakázány statistiky. Všechny shromážděné statistické hodnoty jsou pro připojení.  
  
## <a name="statistical-values-available"></a>Dostupné statistické hodnoty  
 V současné době je k dispozici 18 různých položek od poskytovatele serveru Microsoft SQL Server. Počet položek k dispozici lze přistupovat prostřednictvím <xref:System.Collections.IDictionary> **Count** vlastnost <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>odkaz rozhraní vrácené . Všechny čítače pro statistiky zprostředkovatele <xref:System.Int64> používají typ clr **(long** v jazyce C# a Visual Basic), který je 64 bitů široký. Maximální hodnota datového typu **int64,** jak je definováno **int64. MaxValue** pole, is ((2^63)-1)). Když hodnoty čítačů dosáhnou této maximální hodnoty, neměly by být již považovány za přesné. To znamená, že **int64. MaxValue**-1((2^63)-2) je skutečně největší platnou hodnotu pro všechny statistiky.  
  
> [!NOTE]
> Slovník se používá pro vrácení statistiky zprostředkovatele, protože počet, názvy a pořadí vrácené statistiky se může v budoucnu změnit. Aplikace by neměly spoléhat na konkrétní hodnotu, která se nachází ve slovníku, ale místo toho by měly zkontrolovat, zda hodnota existuje a odpovídajícím způsobem větví.  
  
 Následující tabulka popisuje aktuální dostupné statistické hodnoty. Všimněte si, že názvy klíčů pro jednotlivé hodnoty nejsou lokalizovány v místních verzích rozhraní Microsoft .NET Framework.  
  
|Název klíče|Popis|  
|--------------|-----------------|  
|`BuffersReceived`|Vrátí počet paketů tabulkového datového proudu (TDS) přijatých zprostředkovatelem ze serveru SQL Server poté, co aplikace začala používat zprostředkovatele a povolila statistiky.|  
|`BuffersSent`|Vrátí počet paketů TDS odeslaných na SQL Server zprostředkovatelem po povolení statistik. Velké příkazy mohou vyžadovat více vyrovnávacích pamětí. Například pokud velký příkaz je odeslán na server a `ServerRoundtrips` vyžaduje šest paketů, `BuffersSent` je zvýšil o jeden a je zvýšil o šest.|  
|`BytesReceived`|Vrátí počet bajtů dat v paketech TDS přijatých zprostředkovatelem ze serveru SQL Server, jakmile aplikace začne používat zprostředkovatele a povolila statistiky.|  
|`BytesSent`|Vrátí počet bajtů dat odeslaných na SQL Server v paketech TDS poté, co aplikace začala používat zprostředkovatele a povolila statistiky.|  
|`ConnectionTime`|Doba (v milisekundách), po které bylo připojení otevřeno po povolení statistik (celkový čas připojení, pokud byly před otevřením připojení povoleny statistiky).|  
|`CursorOpens`|Vrátí počet otevření kurzoru prostřednictvím připojení, jakmile aplikace začala používat zprostředkovatele a povolila statistiky.<br /><br /> Všimněte si, že jen pro čtení/předávání pouze výsledky vrácené příkazy SELECT nejsou považovány za kurzory a proto nemají vliv na tento čítač.|  
|`ExecutionTime`|Vrátí kumulativní množství času (v milisekundách), které zprostředkovatel strávil zpracováním po povolení statistiky, včetně času stráveného čekáním na odpovědi ze serveru a času stráveného prováděním kódu v samotném zprostředkovateli.<br /><br /> Třídy, které obsahují kód časování jsou:<br /><br /> Sqlconnection<br /><br /> Sqlcommand<br /><br /> Sqldatareader<br /><br /> Sqldataadapter<br /><br /> Sqltransaction<br /><br /> SqlCommandBuilder<br /><br /> Chcete-li zachovat členy kritické pro výkon co nejmenší, nejsou načasovány následující členy:<br /><br /> Sqldatareader<br /><br /> tento[] operátor (všechna přetížení)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> Doba platnosti getdate<br /><br /> Získat decimal<br /><br /> Získat dvojitou<br /><br /> GetFloat<br /><br /> GetGuid<br /><br /> ZískatInt16<br /><br /> GetInt32<br /><br /> ZískatInt64<br /><br /> GetName<br /><br /> Getordinal<br /><br /> GetSqlBinární<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> Doba aplikace GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> Isdbnull|  
|`IduCount`|Vrátí celkový počet příkazů INSERT, DELETE a UPDATE provedených prostřednictvím připojení, jakmile aplikace začne používat zprostředkovatele a povolila statistiky.|  
|`IduRows`|Vrátí celkový počet řádků ovlivněných příkazy INSERT, DELETE a UPDATE provedenými prostřednictvím připojení, jakmile aplikace začne používat zprostředkovatele a povolila statistiky.|  
|`NetworkServerTime`|Vrátí kumulativní množství času (v milisekundách), které zprostředkovatel strávil čekáním na odpovědi ze serveru, jakmile aplikace začala používat zprostředkovatele a povolila statistiky.|  
|`PreparedExecs`|Vrátí počet připravených příkazů provedených prostřednictvím připojení, jakmile aplikace začne používat zprostředkovatele a povolila statistiky.|  
|`Prepares`|Vrátí počet příkazů připravených prostřednictvím připojení, jakmile aplikace začala používat zprostředkovatele a povolila statistiky.|  
|`SelectCount`|Vrátí počet příkazů SELECT provedených prostřednictvím připojení, jakmile aplikace začne používat zprostředkovatele a povolila statistiky. To zahrnuje FETCH příkazy načíst řádky z kurzory a počet <xref:System.Data.SqlClient.SqlDataReader> select příkazy je aktualizován při dosažení konce a.|  
|`SelectRows`|Vrátí počet řádků vybraných po aplikaci začal používat zprostředkovatele a povolil statistiky. Tento čítač odráží všechny řádky generované příkazy SQL, i ty, které nebyly skutečně spotřebovány volajícím. Například zavření čtečky dat před čtením celé sady výsledků nebude mít vliv na počet. To zahrnuje řádky načtené z kurzorů prostřednictvím příkazů FETCH.|  
|`ServerRoundtrips`|Vrátí počet, kolikrát připojení odeslané příkazy na server a dostal odpověď zpět, jakmile aplikace začala používat zprostředkovatele a povolila statistiky.|  
|`SumResultSets`|Vrátí počet sad výsledků, které byly použity poté, co aplikace začala používat zprostředkovatele a povolila statistiky. Například to by zahrnovalo všechny sady výsledků vrácené klientovi. Pro kurzory každá operace načtení nebo načtení bloku je považována za nezávislou sadu výsledků.|  
|`Transactions`|Vrátí počet uživatelských transakcí spuštěných po spuštění aplikace pomocí zprostředkovatele a povolil a povolil statistiky, včetně vrácení zpět. Pokud je spuštěno připojení s automatickým potvrzením, každý příkaz je považován za transakci.<br /><br /> Tento čítač zintálí počet transakcí, jakmile begin tran příkaz je proveden, bez ohledu na to, zda je transakce potvrzena nebo vrácena zpět později.|  
|`UnpreparedExecs`|Vrátí počet nepřipravených příkazů provedených prostřednictvím připojení, jakmile aplikace začne používat zprostředkovatele a povolila statistiky.|  
  
### <a name="retrieving-a-value"></a>Načítání hodnoty  
 Následující konzolová aplikace ukazuje, jak povolit statistiky připojení, načíst čtyři jednotlivé statistické hodnoty a zapsat je do okna konzoly.  
  
> [!NOTE]
> Následující příklad používá ukázkovou databázi **AdventureWorks,** která je součástí serveru SQL Server. Připojovací řetězec uvedený v ukázkovém kódu předpokládá, že databáze je nainstalována a k dispozici v místním počítači. Podle potřeby upravte připojovací řetězec pro vaše prostředí.  
  
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
    ' you can retrieve it from a configuration file.  
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
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a>Načítání všech hodnot  
 Následující konzolová aplikace ukazuje, jak povolit statistiky připojení, načíst všechny dostupné statistické hodnoty pomocí čítače výčtu a zapsat je do okna konzoly.  
  
> [!NOTE]
> Následující příklad používá ukázkovou databázi **AdventureWorks,** která je součástí serveru SQL Server. Připojovací řetězec uvedený v ukázkovém kódu předpokládá, že databáze je nainstalována a k dispozici v místním počítači. Podle potřeby upravte připojovací řetězec pro vaše prostředí.  
  
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
    ' you can retrieve it from a configuration file.  
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
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Viz také

- [SQL Server a ADO.NET](index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
