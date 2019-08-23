---
title: Statistiky zprostředkovatelů na SQL Serveru
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: e13c4df87909629a45830e3b7950551434ed5ab1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946577"
---
# <a name="provider-statistics-for-sql-server"></a>Statistiky zprostředkovatelů na SQL Serveru
Počínaje verzí 2,0 .NET Framework .NET Framework Zprostředkovatel dat pro SQL Server podporuje statistiku runtime. Chcete-li vytvořit platný objekt připojení <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> , je nutné <xref:System.Data.SqlClient.SqlConnection> povolit statistiku nastavením vlastnosti objektu na `True` hodnotu. Po povolení statistik je můžete zkontrolovat jako "snímek v čase" načtením <xref:System.Collections.IDictionary> odkazu <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> prostřednictvím metody <xref:System.Data.SqlClient.SqlConnection> objektu. Seznam můžete zobrazit jako sadu položek slovníku dvojice název/hodnota. Tyto páry název/hodnota jsou neseřazené. V každém okamžiku můžete zavolat <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> metodu <xref:System.Data.SqlClient.SqlConnection> objektu pro resetování čítačů. Pokud není shromažďování statistických údajů povolené, výjimka se nevygeneruje. Kromě toho, pokud <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> je volána, <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> aniž by byla volána jako první, jsou načtené hodnoty počátečními hodnotami pro každou položku. Pokud povolíte statistiku, spusťte aplikaci za chvíli a pak zakažte statistiku. načtené hodnoty budou odpovídat hodnotám shromážděným do okamžiku, kdy byly statistiky zakázány. Všechny shromážděné statistické hodnoty jsou založené na jednotlivých připojeních.  
  
## <a name="statistical-values-available"></a>Statistické hodnoty k dispozici  
 V současné době je od poskytovatele Microsoft SQL Server k dispozici 18 různých položek. K dostupnému počtu položek lze získat přístup prostřednictvím <xref:System.Collections.IDictionary> vlastnosti **Count** odkazu <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>rozhraní, který vrátil. Všechny čítače pro statistiku poskytovatele používají <xref:System.Int64> typ modulu CLR (**Long** in C# a Visual Basic), což je 64 bitů ve světě. Maximální hodnota datového typu **Int64** , jak je definována hodnotou **Int64. Pole MaxValue** , je ((2 ^ 63)-1)). Pokud hodnoty pro čítače dosáhnou této maximální hodnoty, neměly by se již považovat za přesné. To znamená, že **Int64. MaxValue**-1 ((2 ^ 63)-2) je nejvýhodnější největší platná hodnota pro všechny statistiky.  
  
> [!NOTE]
> Slovník se používá pro vracení statistik poskytovatele, protože počet, názvy a pořadí vrácených statistik se může v budoucnu změnit. Aplikace by neměly spoléhat na konkrétní hodnotu nalezenou ve slovníku, ale měla by se místo toho kontrolovat, zda je tato hodnota a odpovídajícím způsobem větev.  
  
 Následující tabulka popisuje aktuální statistické hodnoty k dispozici. Všimněte si, že názvy klíčů pro jednotlivé hodnoty nejsou lokalizovány mezi regionální verze .NET Framework Microsoft.  
  
|Název klíče|Popis|  
|--------------|-----------------|  
|`BuffersReceived`|Vrátí počet paketů protokolu TDS (Tabular data Stream) přijatých zprostředkovatelem od SQL Server poté, co aplikace začne používat zprostředkovatele a povolila statistiku.|  
|`BuffersSent`|Vrátí počet paketů TDS odeslaných do SQL Server zprostředkovatelem po povolení statistiky. Velké příkazy mohou vyžadovat více vyrovnávacích pamětí. Například pokud je na server odeslán velký příkaz a vyžaduje šest paketů, `ServerRoundtrips` je zvýšen o 1 a `BuffersSent` zvýšen o šest.|  
|`BytesReceived`|Vrátí počet bajtů dat v paketech TDS přijatých poskytovatelem z SQL Server, jakmile aplikace začne používat zprostředkovatele a má povolené statistiky.|  
|`BytesSent`|Vrátí počet bajtů dat odeslaných do SQL Server v paketech TDS po spuštění aplikace pomocí poskytovatele a povolených statistik.|  
|`ConnectionTime`|Množství času (v milisekundách), po které bylo připojení otevřeno po povolení statistiky (celková doba připojení, pokud byla statistika povolena před otevřením připojení).|  
|`CursorOpens`|Vrátí počet otevření kurzoru prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a povolila statistiku.<br /><br /> Všimněte si, že pouze výsledky jen pro čtení nebo dopředné pomocí příkazu SELECT nejsou považovány za kurzory, a proto nemají vliv na tento čítač.|  
|`ExecutionTime`|Vrátí kumulativní množství času (v milisekundách), které poskytovatel strávil zpracováním po povolení statistik, včetně času stráveného čekáním na odpovědi ze serveru a času stráveného prováděním kódu v samotném zprostředkovateli.<br /><br /> Třídy, které obsahují kód časování, jsou:<br /><br /> SqlConnection<br /><br /> SqlCommand<br /><br /> SqlDataReader<br /><br /> SqlDataAdapter<br /><br /> SqlTransaction<br /><br /> SqlCommandBuilder<br /><br /> Chcete-li udržet co nejzávažnější členy co nejmenší, nevypršela platnost následujících členů:<br /><br /> SqlDataReader<br /><br /> Tento operátor [] (všechna přetížení)<br /><br /> GetBoolean<br /><br /> GetChar<br /><br /> GetDateTime<br /><br /> GetDecimal<br /><br /> GetDouble<br /><br /> GetFloat<br /><br /> GetGUID –<br /><br /> GetInt16<br /><br /> GetInt32<br /><br /> GetInt64<br /><br /> GetName<br /><br /> GetOrdinal<br /><br /> GetSqlBinary<br /><br /> GetSqlBoolean<br /><br /> GetSqlByte<br /><br /> GetSqlDateTime<br /><br /> GetSqlDecimal<br /><br /> GetSqlDouble<br /><br /> GetSqlGuid<br /><br /> GetSqlInt16<br /><br /> GetSqlInt32<br /><br /> GetSqlInt64<br /><br /> GetSqlMoney<br /><br /> GetSqlSingle<br /><br /> GetSqlString<br /><br /> GetString<br /><br /> IsDBNull|  
|`IduCount`|Vrátí celkový počet příkazů INSERT, DELETE a UPDATE provedených prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a povolila statistiku.|  
|`IduRows`|Vrátí celkový počet řádků ovlivněných příkazy INSERT, DELETE a UPDATE prováděné prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a má povolené statistiky.|  
|`NetworkServerTime`|Vrátí kumulativní množství času (v milisekundách), které poskytovatel stráví čekáním na odpovědi ze serveru, jakmile aplikace začne používat poskytovatele a má povolené statistiky.|  
|`PreparedExecs`|Vrátí počet připravených příkazů provedených prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a povolila statistiku.|  
|`Prepares`|Vrátí počet příkazů připravených prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a povolila statistiku.|  
|`SelectCount`|Vrátí počet příkazů SELECT provedených prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a povolila statistiku. To zahrnuje příkazy Fetch pro načtení řádků z kurzorů a počet příkazů SELECT je aktualizován po dosažení konce <xref:System.Data.SqlClient.SqlDataReader> .|  
|`SelectRows`|Vrátí počet řádků vybraných po zahájení aplikace pomocí poskytovatele a povolených statistik. Tento čítač odráží všechny řádky vygenerované příkazy SQL, a to i ty, které volající skutečně nevyužil. Například zavření čtecího modulu dat před čtením celé sady výsledků by neovlivnilo počet. To zahrnuje řádky načtené z kurzorů prostřednictvím příkazů FETCH.|  
|`ServerRoundtrips`|Vrátí počet pokusů o připojení odeslaných příkazů serveru a odeslání odpovědi zpět, jakmile aplikace začne používat poskytovatele a povolila statistiku.|  
|`SumResultSets`|Vrátí počet sad výsledků, které byly použity poté, co aplikace začala používat poskytovatele a má povolené statistiky. Například by obsahovala sadu výsledků vrácenou klientovi. Pro kurzory se každá operace Fetch nebo Block-Fetch považuje za nezávislou sadu výsledků.|  
|`Transactions`|Vrátí počet uživatelských transakcí spuštěných po zahájení aplikace pomocí poskytovatele a povolených statistik, včetně vrácení zpět. Pokud je připojení spuštěné s automatickým potvrzením, každý příkaz se považuje za transakci.<br /><br /> Tento čítač zvyšuje počet transakcí hned po provedení příkazu BEGIN TRAN, bez ohledu na to, zda je transakce potvrzena nebo vrácena zpět později.|  
|`UnpreparedExecs`|Vrátí počet nepřipravených příkazů provedených prostřednictvím připojení, jakmile aplikace začne používat poskytovatele a povolila statistiku.|  
  
### <a name="retrieving-a-value"></a>Načítání hodnoty  
 Následující aplikace konzoly ukazuje, jak povolit statistiku připojení, načíst čtyři jednotlivé statistické hodnoty a zapsat je do okna konzoly.  
  
> [!NOTE]
> Následující příklad používá ukázkovou databázi **AdventureWorks** , která je součástí SQL Server. Připojovací řetězec uvedený v ukázkovém kódu předpokládá, že je databáze nainstalovaná a dostupná v místním počítači. Upravte připojovací řetězec podle potřeby pro vaše prostředí.  
  
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
 Následující aplikace konzoly ukazuje, jak povolit statistiku připojení, načíst všechny dostupné statistické hodnoty pomocí enumerátoru a zapsat je do okna konzoly.  
  
> [!NOTE]
> Následující příklad používá ukázkovou databázi **AdventureWorks** , která je součástí SQL Server. Připojovací řetězec uvedený v ukázkovém kódu předpokládá, že je databáze nainstalovaná a dostupná v místním počítači. Upravte připojovací řetězec podle potřeby pro vaše prostředí.  
  
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
  
## <a name="see-also"></a>Viz také:

- [SQL Server a ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
