---
title: Čítače výkonu
description: Pomocí čítačů výkonu ADO.NET můžete monitorovat stav aplikace a prostředky připojení pomocí nástroje sledování výkonu systému Windows nebo prostřednictvím kódu programu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: 9dde2d7305a1176dadba3802fc5335c0c95bfbbb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286673"
---
# <a name="performance-counters-in-adonet"></a>Čítače výkonu v ADO.NET
ADO.NET 2,0 představil rozšířenou podporu pro čítače výkonu, které zahrnují podporu pro i <xref:System.Data.SqlClient> <xref:System.Data.OracleClient> . <xref:System.Data.SqlClient>Čítače výkonu dostupné v předchozích verzích ADO.NET byly zastaralé a nahrazeny novými čítači výkonu popsanými v tomto tématu. Pomocí čítačů výkonu ADO.NET můžete monitorovat stav aplikace a prostředky připojení, které používá. Čítače výkonu lze monitorovat pomocí nástroje sledování výkonu systému Windows nebo lze programově přistupovat pomocí <xref:System.Diagnostics.PerformanceCounter> třídy v <xref:System.Diagnostics> oboru názvů.  
  
## <a name="available-performance-counters"></a>Dostupné čítače výkonu  
 V současné době jsou k dispozici 14 různých čítačů výkonu pro <xref:System.Data.SqlClient> a <xref:System.Data.OracleClient> jak je popsáno v následující tabulce. Všimněte si, že názvy jednotlivých čítačů nejsou lokalizovány mezi regionální verze .NET Framework Microsoft.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|Počet připojení za sekundu, které se provádí na databázovém serveru.|  
|`HardDisconnectsPerSecond`|Počet odpojení za sekundu, které se provádí na databázovém serveru.|  
|`NumberOfActiveConnectionPoolGroups`|Počet jedinečných skupin fondu připojení, které jsou aktivní. Tento čítač je řízen počtem jedinečných připojovacích řetězců, které jsou nalezeny v doméně aplikace.|  
|`NumberOfActiveConnectionPools`|Celkový počet fondů připojení.|  
|`NumberOfActiveConnections`|Počet aktivních připojení, která jsou aktuálně používána. **Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen. Pokud chcete tento čítač výkonu povolit, přečtěte si téma [Aktivace čítačů mimo výchozí](#ActivatingOffByDefault).|  
|`NumberOfFreeConnections`|Počet připojení, která jsou k dispozici pro použití ve fondech připojení. **Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen. Pokud chcete tento čítač výkonu povolit, přečtěte si téma [Aktivace čítačů mimo výchozí](#ActivatingOffByDefault).|  
|`NumberOfInactiveConnectionPoolGroups`|Počet jedinečných skupin fondů připojení, které jsou označeny pro vyřazení. Tento čítač je řízen počtem jedinečných připojovacích řetězců, které jsou nalezeny v doméně aplikace.|  
|`NumberOfInactiveConnectionPools`|Počet neaktivních fondů připojení, které nemají žádnou poslední aktivitu a čekají na jejich vyřazení.|  
|`NumberOfNonPooledConnections`|Počet aktivních připojení, která nejsou ve fondu.|  
|`NumberOfPooledConnections`|Počet aktivních připojení, která jsou spravována infrastrukturou sdružování připojení.|  
|`NumberOfReclaimedConnections`|Počet připojení, která byla uvolněna prostřednictvím uvolňování paměti, kdy `Close` `Dispose` aplikace nevolala. Nepovedlo se explicitně uzavřít ani vyřadit připojení neuškodí výkon.|  
|`NumberOfStasisConnections`|Počet připojení, které aktuálně čekají na dokončení akce a které jsou proto nedostupné pro použití vaší aplikací.|  
|`SoftConnectsPerSecond`|Počet aktivních připojení, která jsou načítána z fondu připojení. **Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen. Pokud chcete tento čítač výkonu povolit, přečtěte si téma [Aktivace čítačů mimo výchozí](#ActivatingOffByDefault).|  
|`SoftDisconnectsPerSecond`|Počet aktivních připojení, které jsou vraceny do fondu připojení. **Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen. Pokud chcete tento čítač výkonu povolit, přečtěte si téma [Aktivace čítačů mimo výchozí](#ActivatingOffByDefault).|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>Skupiny fondu připojení a fondy připojení  
 Při použití ověřování systému Windows (integrované zabezpečení) je nutné monitorovat `NumberOfActiveConnectionPoolGroups` `NumberOfActiveConnectionPools` čítače výkonu a. Důvodem je, že se skupiny fondu připojení mapují na jedinečné připojovací řetězce. Při použití integrovaného zabezpečení se fondy připojení mapují na připojovací řetězce a navíc vytvoří samostatné fondy pro jednotlivé identity Windows. Například pokud Fred a Julie každý v rámci stejné domény AppDomain, oba používají připojovací řetězec, vytvoří se `"Data Source=MySqlServer;Integrated Security=true"` Skupina fondu připojení pro připojovací řetězec a vytvoří se dva další fondy, jeden pro Fred a druhý pro Julie. Pokud Jan a Martha používají připojovací řetězec se stejným SQL Server přihlášením, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"` vytvoří se pro identitu **lowPrivUser** jenom jeden fond.  
  
<a name="ActivatingOffByDefault"></a>
### <a name="activating-off-by-default-counters"></a>Aktivace čítačů mimo výchozí  
 Čítače výkonu `NumberOfFreeConnections` ,, `NumberOfActiveConnections` `SoftDisconnectsPerSecond` a `SoftConnectsPerSecond` jsou ve výchozím nastavení vypnuté. Do konfiguračního souboru aplikace přidejte následující informace, abyste je povolili:  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a>Načítání hodnot čítače výkonu  
 Následující aplikace konzoly ukazuje, jak načíst hodnoty čítače výkonu ve vaší aplikaci. Aby bylo možné vracet informace pro všechny čítače výkonu ADO.NET, musí být připojení otevřená a aktivní.  
  
> [!NOTE]
> V tomto příkladu se používá ukázková databáze **AdventureWorks** obsažená v SQL Server. Připojovací řetězce, které jsou uvedeny v ukázkovém kódu, předpokládají, že je databáze nainstalována a dostupná v místním počítači s názvem instance SqlExpress a že jste vytvořili SQL Server přihlašovacích údajů, které odpovídají zadaným řetězcům v připojovacích řetězcích. Pokud je server nakonfigurovaný pomocí výchozího nastavení zabezpečení, které povoluje jenom ověřování systému Windows, může být nutné povolit SQL Server přihlašovacích údajů. Upravte připojovací řetězce podle potřeby tak, aby vyhovovaly vašemu prostředí.  
  
### <a name="example"></a>Příklad  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System.Data.SqlClient  
Imports System.Diagnostics  
Imports System.Runtime.InteropServices  
  
Class Program  
  
    Private PerfCounters(9) As PerformanceCounter  
    Private connection As SqlConnection = New SqlConnection  
  
    Public Shared Sub Main()  
        Dim prog As Program = New Program  
        ' Open a connection and create the performance counters.
        prog.connection.ConnectionString = _  
           GetIntegratedSecurityConnectionString()  
        prog.SetUpPerformanceCounters()  
        Console.WriteLine("Available Performance Counters:")  
  
        ' Create the connections and display the results.  
        prog.CreateConnections()  
        Console.WriteLine("Press Enter to finish.")  
        Console.ReadLine()  
    End Sub  
  
    Private Sub CreateConnections()  
        ' List the Performance counters.  
        WritePerformanceCounters()  
  
        ' Create 4 connections and display counter information.  
        Dim connection1 As SqlConnection = New SqlConnection( _  
           GetIntegratedSecurityConnectionString)  
        connection1.Open()  
        Console.WriteLine("Opened the 1st Connection:")  
        WritePerformanceCounters()  
  
        Dim connection2 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionStringDifferent)  
        connection2.Open()  
        Console.WriteLine("Opened the 2nd Connection:")  
        WritePerformanceCounters()  
  
        Console.WriteLine("Opened the 3rd Connection:")  
        Dim connection3 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection3.Open()  
        WritePerformanceCounters()  
  
        Dim connection4 As SqlConnection = New SqlConnection( _  
           GetSqlConnectionString)  
        connection4.Open()  
        Console.WriteLine("Opened the 4th Connection:")  
        WritePerformanceCounters()  
  
        connection1.Close()  
        Console.WriteLine("Closed the 1st Connection:")  
        WritePerformanceCounters()  
  
        connection2.Close()  
        Console.WriteLine("Closed the 2nd Connection:")  
        WritePerformanceCounters()  
  
        connection3.Close()  
        Console.WriteLine("Closed the 3rd Connection:")  
        WritePerformanceCounters()  
  
        connection4.Close()  
        Console.WriteLine("Closed the 4th Connection:")  
        WritePerformanceCounters()  
    End Sub  
  
    Private Enum ADO_Net_Performance_Counters  
        NumberOfActiveConnectionPools  
        NumberOfReclaimedConnections  
        HardConnectsPerSecond  
        HardDisconnectsPerSecond  
        NumberOfActiveConnectionPoolGroups  
        NumberOfInactiveConnectionPoolGroups  
        NumberOfInactiveConnectionPools  
        NumberOfNonPooledConnections  
        NumberOfPooledConnections  
        NumberOfStasisConnections  
        ' The following performance counters are more expensive to track.  
        ' Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        '     SoftConnectsPerSecond  
        '     SoftDisconnectsPerSecond  
        '     NumberOfActiveConnections  
        '     NumberOfFreeConnections  
    End Enum  
  
    Private Sub SetUpPerformanceCounters()  
        connection.Close()  
        Me.PerfCounters(9) = New PerformanceCounter()  
  
        Dim instanceName As String = GetInstanceName()  
        Dim apc As Type = GetType(ADO_Net_Performance_Counters)  
        Dim i As Integer = 0  
        Dim s As String = ""  
        For Each s In [Enum].GetNames(apc)  
            Me.PerfCounters(i) = New PerformanceCounter()  
            Me.PerfCounters(i).CategoryName = ".NET Data Provider for SqlServer"  
            Me.PerfCounters(i).CounterName = s  
            Me.PerfCounters(i).InstanceName = instanceName  
            i = (i + 1)  
        Next  
    End Sub  
  
    Private Declare Function GetCurrentProcessId Lib "kernel32.dll" () As Integer  
  
    Private Function GetInstanceName() As String  
        'This works for Winforms apps.
        Dim instanceName As String = _  
           System.Reflection.Assembly.GetEntryAssembly.GetName.Name  
  
        ' Must replace special characters like (, ), #, /, \\
        Dim instanceName2 As String = _  
           AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
           .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        'For ASP.NET applications your instanceName will be your CurrentDomain's
        'FriendlyName. Replace the line above that sets the instanceName with this:
        'instanceName = AppDomain.CurrentDomain.FriendlyName.ToString.Replace("(", "[") _  
        '    .Replace(")", "]").Replace("#", "_").Replace("/", "_").Replace("\\", "_")  
  
        Dim pid As String = GetCurrentProcessId.ToString  
        instanceName = (instanceName + ("[" & (pid & "]")))  
        Console.WriteLine("Instance Name: {0}", instanceName)  
        Console.WriteLine("---------------------------")  
        Return instanceName  
    End Function  
  
    Private Sub WritePerformanceCounters()  
        Console.WriteLine("---------------------------")  
        For Each p As PerformanceCounter In Me.PerfCounters  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue)  
        Next  
        Console.WriteLine("---------------------------")  
    End Sub  
  
    Private Shared Function GetIntegratedSecurityConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
        Return ("Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" & _  
          "User Id=LowPriv;Password=Data!05;")  
    End Function  
End Class  
```  

```csharp  
using System;  
using System.Data.SqlClient;  
using System.Diagnostics;  
using System.Runtime.InteropServices;  
  
class Program  
{  
    PerformanceCounter[] PerfCounters = new PerformanceCounter[10];  
    SqlConnection connection = new SqlConnection();  
  
    static void Main()  
    {  
        Program prog = new Program();  
        // Open a connection and create the performance counters.  
        prog.connection.ConnectionString =  
           GetIntegratedSecurityConnectionString();  
        prog.SetUpPerformanceCounters();  
        Console.WriteLine("Available Performance Counters:");  
  
        // Create the connections and display the results.  
        prog.CreateConnections();  
        Console.WriteLine("Press Enter to finish.");  
        Console.ReadLine();  
    }  
  
    private void CreateConnections()  
    {  
        // List the Performance counters.  
        WritePerformanceCounters();  
  
        // Create 4 connections and display counter information.  
        SqlConnection connection1 = new SqlConnection(  
              GetIntegratedSecurityConnectionString());  
        connection1.Open();  
        Console.WriteLine("Opened the 1st Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection2 = new SqlConnection(  
              GetSqlConnectionStringDifferent());  
        connection2.Open();  
        Console.WriteLine("Opened the 2nd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection3 = new SqlConnection(  
              GetSqlConnectionString());  
        connection3.Open();  
        Console.WriteLine("Opened the 3rd Connection:");  
        WritePerformanceCounters();  
  
        SqlConnection connection4 = new SqlConnection(  
              GetSqlConnectionString());  
        connection4.Open();  
        Console.WriteLine("Opened the 4th Connection:");  
        WritePerformanceCounters();  
  
        connection1.Close();  
        Console.WriteLine("Closed the 1st Connection:");  
        WritePerformanceCounters();  
  
        connection2.Close();  
        Console.WriteLine("Closed the 2nd Connection:");  
        WritePerformanceCounters();  
  
        connection3.Close();  
        Console.WriteLine("Closed the 3rd Connection:");  
        WritePerformanceCounters();  
  
        connection4.Close();  
        Console.WriteLine("Closed the 4th Connection:");  
        WritePerformanceCounters();  
    }  
  
    private enum ADO_Net_Performance_Counters  
    {  
        NumberOfActiveConnectionPools,  
        NumberOfReclaimedConnections,  
        HardConnectsPerSecond,  
        HardDisconnectsPerSecond,  
        NumberOfActiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPoolGroups,  
        NumberOfInactiveConnectionPools,  
        NumberOfNonPooledConnections,  
        NumberOfPooledConnections,  
        NumberOfStasisConnections  
        // The following performance counters are more expensive to track.  
        // Enable ConnectionPoolPerformanceCounterDetail in your config file.  
        //     SoftConnectsPerSecond  
        //     SoftDisconnectsPerSecond  
        //     NumberOfActiveConnections  
        //     NumberOfFreeConnections  
    }  
  
    private void SetUpPerformanceCounters()  
    {  
        connection.Close();  
        this.PerfCounters = new PerformanceCounter[10];  
        string instanceName = GetInstanceName();  
        Type apc = typeof(ADO_Net_Performance_Counters);  
        int i = 0;  
        foreach (string s in Enum.GetNames(apc))  
        {  
            this.PerfCounters[i] = new PerformanceCounter();  
            this.PerfCounters[i].CategoryName = ".NET Data Provider for SqlServer";  
            this.PerfCounters[i].CounterName = s;  
            this.PerfCounters[i].InstanceName = instanceName;  
            i++;  
        }  
    }  
  
    [DllImport("kernel32.dll", SetLastError = true)]  
    static extern int GetCurrentProcessId();  
  
    private string GetInstanceName()  
    {  
        //This works for Winforms apps.  
        string instanceName =  
            System.Reflection.Assembly.GetEntryAssembly().GetName().Name;  
  
        // Must replace special characters like (, ), #, /, \\  
        string instanceName2 =  
            AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(', '[')  
            .Replace(')', ']').Replace('#', '_').Replace('/', '_').Replace('\\', '_');  
  
        // For ASP.NET applications your instanceName will be your CurrentDomain's
        // FriendlyName. Replace the line above that sets the instanceName with this:  
        // instanceName = AppDomain.CurrentDomain.FriendlyName.ToString().Replace('(','[')  
        // .Replace(')',']').Replace('#','_').Replace('/','_').Replace('\\','_');  
  
        string pid = GetCurrentProcessId().ToString();  
        instanceName = instanceName + "[" + pid + "]";  
        Console.WriteLine("Instance Name: {0}", instanceName);  
        Console.WriteLine("---------------------------");  
        return instanceName;  
    }  
  
    private void WritePerformanceCounters()  
    {  
        Console.WriteLine("---------------------------");  
        foreach (PerformanceCounter p in this.PerfCounters)  
        {  
            Console.WriteLine("{0} = {1}", p.CounterName, p.NextValue());  
        }  
        Console.WriteLine("---------------------------");  
    }  
  
    private static string GetIntegratedSecurityConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
          "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrieve it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  

## <a name="see-also"></a>Viz také

- [Připojení ke zdroji dat](connecting-to-a-data-source.md)
- [Sdružování připojení OLE DB, ODBC a Oracle](ole-db-odbc-and-oracle-connection-pooling.md)
- [Čítače výkonu pro ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))
- [Běhová profilace](../../debug-trace-profile/runtime-profiling.md)
- [Úvod do monitorování mezních hodnot výkonu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))
- [Přehled ADO.NET](ado-net-overview.md)
