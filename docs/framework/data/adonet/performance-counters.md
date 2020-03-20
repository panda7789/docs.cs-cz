---
title: Čítače výkonu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: b68787980a8b64d9ee90ed8d834fab2c5c69006b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149333"
---
# <a name="performance-counters-in-adonet"></a>Čítače výkonu v ADO.NET
ADO.NET 2.0 zavedlrozšířenou podporu čítačů <xref:System.Data.SqlClient> <xref:System.Data.OracleClient>výkonu, která zahrnuje podporu pro obě a . Čítače <xref:System.Data.SqlClient> výkonu dostupné v předchozích verzích ADO.NET byly zastaralé a nahrazeny novými čítači výkonu popsanými v tomto tématu. Pomocí ADO.NET čítačů výkonu můžete sledovat stav aplikace a prostředků připojení, které používá. Čítače výkonu lze sledovat pomocí programu Sledování výkonu systému <xref:System.Diagnostics.PerformanceCounter> Windows nebo <xref:System.Diagnostics> lze k nim přistupovat programově pomocí třídy v oboru názvů.  
  
## <a name="available-performance-counters"></a>Dostupné čítače výkonu  
 V současné době je k dispozici <xref:System.Data.SqlClient> 14 různých čítačů výkonu pro a <xref:System.Data.OracleClient> jak je popsáno v následující tabulce. Všimněte si, že názvy pro jednotlivé čítače nejsou lokalizovány v rámci místní verze rozhraní Microsoft .NET Framework.  
  
|Čítač výkonu|Popis|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|Počet připojení za sekundu, které jsou prováděny na databázový server.|  
|`HardDisconnectsPerSecond`|Počet odpojení za sekundu, které jsou prováděny na databázovém serveru.|  
|`NumberOfActiveConnectionPoolGroups`|Počet jedinečných skupin fondu připojení, které jsou aktivní. Tento čítač je řízen počtem jedinečných připojovacích řetězců, které se nacházejí v AppDomain.|  
|`NumberOfActiveConnectionPools`|Celkový počet fondů připojení.|  
|`NumberOfActiveConnections`|Počet aktivních připojení, která jsou aktuálně používána. **Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen. Chcete-li povolit tento čítač výkonu, [přečtěte si téma Aktivace čítačů mimo výchozí nastavení](#ActivatingOffByDefault).|  
|`NumberOfFreeConnections`|Počet připojení, která jsou k dispozici pro použití ve fondech připojení. **Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen. Chcete-li povolit tento čítač výkonu, [přečtěte si téma Aktivace čítačů mimo výchozí nastavení](#ActivatingOffByDefault).|  
|`NumberOfInactiveConnectionPoolGroups`|Počet jedinečných skupin fondu připojení, které jsou označeny pro vyřezávání. Tento čítač je řízen počtem jedinečných připojovacích řetězců, které se nacházejí v AppDomain.|  
|`NumberOfInactiveConnectionPools`|Počet neaktivních fondů připojení, které neměly žádné nedávné aktivity a čekají na vyřazení.|  
|`NumberOfNonPooledConnections`|Počet aktivních připojení, které nejsou sdružené.|  
|`NumberOfPooledConnections`|Počet aktivních připojení, které jsou spravovány infrastrukturou sdružování připojení.|  
|`NumberOfReclaimedConnections`|Počet připojení, které byly uvolněny prostřednictvím `Close` `Dispose` uvolňování paměti, kde nebo nebyl volán aplikací. Neexplicitní uzavření nebo likvidace spojení poškozuje výkon.|  
|`NumberOfStasisConnections`|Počet připojení, která aktuálně čekají na dokončení akce a která proto nejsou k dispozici pro použití vaší aplikací.|  
|`SoftConnectsPerSecond`|Počet aktivních připojení, která jsou vyžádána z fondu připojení. **Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen. Chcete-li povolit tento čítač výkonu, [přečtěte si téma Aktivace čítačů mimo výchozí nastavení](#ActivatingOffByDefault).|  
|`SoftDisconnectsPerSecond`|Počet aktivních připojení, která jsou právě vrácena do fondu připojení. **Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen. Chcete-li povolit tento čítač výkonu, [přečtěte si téma Aktivace čítačů mimo výchozí nastavení](#ActivatingOffByDefault).|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>Skupiny fondu připojení a fondy připojení  
 Při použití ověřování systému Windows (integrované `NumberOfActiveConnectionPoolGroups` `NumberOfActiveConnectionPools` zabezpečení) je nutné sledovat čítače i čítače výkonu. Důvodem je, že skupiny fondu připojení mapovat na jedinečné připojovací řetězce. Při použití integrovaného zabezpečení se fondy připojení mapují na připojovací řetězce a navíc vytvářejí samostatné fondy pro jednotlivé identity systému Windows. Například pokud Fred a Julie, každý v rámci stejné `"Data Source=MySqlServer;Integrated Security=true"`AppDomain, oba používají připojovací řetězec , je vytvořena skupina fondu připojení pro připojovací řetězec a dva další fondy jsou vytvořeny, jeden pro Fred a jeden pro Julie. Pokud Jan a Martha použít připojovací `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`řetězec s identické přihlášení SQL Server , pak je vytvořen pouze jeden fond pro **lowPrivUser** identity.  
  
<a name="ActivatingOffByDefault"></a>
### <a name="activating-off-by-default-counters"></a>Aktivace čítačů mimo výchozí nastavení  
 Čítače `NumberOfFreeConnections` `NumberOfActiveConnections`výkonu `SoftDisconnectsPerSecond`, `SoftConnectsPerSecond` , a jsou ve výchozím nastavení vypnuty. Přidejte do konfiguračního souboru aplikace následující informace, které je povolte:  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a>Načítání hodnot čítače výkonu  
 Následující konzolová aplikace ukazuje, jak načíst hodnoty čítače výkonu ve vaší aplikaci. Připojení musí být otevřená a aktivní, aby informace byly vráceny pro všechny čítače výkonu ADO.NET.  
  
> [!NOTE]
> Tento příklad používá ukázkovou databázi **AdventureWorks,** která je součástí serveru SQL Server. Připojovací řetězce uvedené v ukázkovém kódu předpokládají, že databáze je nainstalována a k dispozici v místním počítači s názvem instance SqlExpress a že jste vytvořili přihlášení serveru SQL Server, které odpovídají těm, které jsou součástí připojovacích řetězců. Pokud je server nakonfigurován pomocí výchozího nastavení zabezpečení, které umožňuje pouze ověřování systému Windows, bude pravděpodobně nutné povolit přihlášení serveru SQL Server. Podle potřeby upravte připojovací řetězce tak, aby vyhovovaly vašemu prostředí.  
  
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
- [Úvod do sledování prahových hodnot výkonu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))
- [Přehled ADO.NET](ado-net-overview.md)
