---
title: Čítače výkonu v technologii ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
ms.openlocfilehash: 8696bf567d8f32fc3bc3f78e127631f488c551aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365113"
---
# <a name="performance-counters-in-adonet"></a>Čítače výkonu v technologii ADO.NET
ADO.NET 2.0 zavedená rozšířenou podporu pro čítače výkonu, který zahrnuje podporu pro obě <xref:System.Data.SqlClient> a <xref:System.Data.OracleClient>. <xref:System.Data.SqlClient> Čítače výkonu, které jsou k dispozici v předchozích verzích technologie ADO.NET byly zastaralé a nahradí nové čítače výkonu, které jsou popsané v tomto tématu. Čítače výkonu technologie ADO.NET můžete použít k monitorování stavu aplikace a prostředky připojení, které používá. Čítače výkonu pomocí sledování výkonu systému Windows se dá sledovat nebo k němu přístup programově pomocí <xref:System.Diagnostics.PerformanceCounter> třídy v <xref:System.Diagnostics> oboru názvů.  
  
## <a name="available-performance-counters"></a>Čítače výkonu k dispozici  
 Aktuálně nejsou 14 různých čítače k dispozici pro <xref:System.Data.SqlClient> a <xref:System.Data.OracleClient> jak je popsáno v následující tabulce. Všimněte si, že názvy pro jednotlivé čítače nejsou lokalizovány mezi místní verze rozhraní Microsoft .NET Framework.  
  
|Čítače výkonu|Popis|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|Počet připojení za sekundu, které jsou určené k databázovému serveru.|  
|`HardDisconnectsPerSecond`|Počet odpojí za sekundu, které jsou určené k databázovému serveru.|  
|`NumberOfActiveConnectionPoolGroups`|Počet skupin fondu jedinečný připojení, které jsou aktivní. Tento čítač je řízena podle počtu jedinečných připojovací řetězce, které se nacházejí v domény aplikace.|  
|`NumberOfActiveConnectionPools`|Celkový počet připojení fondy.|  
|`NumberOfActiveConnections`|Počet aktivních připojení, které jsou právě používány. **Poznámka:** tento čítač výkonu není ve výchozím nastavení povolené. Pokud chcete povolit tento čítač výkonu, najdete v části [aktivace vypnout výchozím čítače](#ActivatingOffByDefault).|  
|`NumberOfFreeConnections`|Počet připojení, které jsou k dispozici pro použití ve fondech připojení. **Poznámka:** tento čítač výkonu není ve výchozím nastavení povolené. Pokud chcete povolit tento čítač výkonu, najdete v části [aktivace vypnout výchozím čítače](#ActivatingOffByDefault).|  
|`NumberOfInactiveConnectionPoolGroups`|Počet skupin fondu jedinečný připojení, které jsou označeny k vyřazení. Tento čítač je řízena podle počtu jedinečných připojovací řetězce, které se nacházejí v domény aplikace.|  
|`NumberOfInactiveConnectionPools`|Počet neaktivních připojení fondy, které nedošlo k žádné poslední aktivitu a čekají na zlikvidován.|  
|`NumberOfNonPooledConnections`|Počet aktivních připojení, které nejsou ve fondu.|  
|`NumberOfPooledConnections`|Počet aktivních připojení, které spravuje infrastrukturu sdružování připojení.|  
|`NumberOfReclaimedConnections`|Počet připojení, které bylo uvolněno prostřednictvím uvolňování kde `Close` nebo `Dispose` nebyla volána aplikací. Není explicitně zavírání nebo uvolnění připojení škodí jak výkonu.|  
|`NumberOfStasisConnections`|Počet připojení, které jsou aktuálně čeká na dokončení akce a které proto není k dispozici pro použití aplikací.|  
|`SoftConnectsPerSecond`|Počet aktivních připojení patrně fondu připojení. **Poznámka:** tento čítač výkonu není ve výchozím nastavení povolené. Pokud chcete povolit tento čítač výkonu, najdete v části [aktivace vypnout výchozím čítače](#ActivatingOffByDefault).|  
|`SoftDisconnectsPerSecond`|Počet aktivních připojení, které se vrací do fondu připojení. **Poznámka:** tento čítač výkonu není ve výchozím nastavení povolené. Pokud chcete povolit tento čítač výkonu, najdete v části [aktivace vypnout výchozím čítače](#ActivatingOffByDefault).|  
  
### <a name="connection-pool-groups-and-connection-pools"></a>Skupiny fondu připojení a připojení fondy  
 Pokud používáte ověřování systému Windows (integrované zabezpečení), je třeba sledovat i `NumberOfActiveConnectionPoolGroups` a `NumberOfActiveConnectionPools` čítače výkonu. Důvodem je, které jsou namapovány fondu skupin připojení na jedinečný připojovací řetězce. Pokud se používá integrované zabezpečení, sdružení připojení mapovat připojovací řetězce a kromě vytvořit samostatné fondy pro jednotlivé Windows identity. Například, pokud František a Julie, každou v rámci stejné domény aplikace, jak použít připojovací řetězec `"Data Source=MySqlServer;Integrated Security=true"`, skupinu fondu připojení se vytvoří pro připojovací řetězec a jsou vytvořeny dva další fondy, jeden pro František a jeden pro Julie. Pokud Jan a Marta použijete připojovací řetězec s identické přihlášení systému SQL Server, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, pak pouze jednoho fondu se vytvoří pro **lowPrivUser** identity.  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a>Aktivace vypnout výchozím čítače  
 Čítače výkonu `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, a `SoftConnectsPerSecond` jsou ve výchozím nastavení vypnuté. Přidejte do konfiguračního souboru aplikace a umožňuje jim následující informace:  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a>Načítání hodnoty čítače výkonu  
 Následující aplikace konzoly ukazuje, jak načíst hodnoty čítače výkonu ve vaší aplikaci. Připojení musí být otevřený a aktivní informace, které má být vrácen pro všechny čítače výkonu technologie ADO.NET.  
  
> [!NOTE]
>  Tento příklad používá vzorku **AdventureWorks** databáze je součástí systému SQL Server. Připojovací řetězce, který je součástí ukázkový kód předpokládají, že databáze je nainstalovaná a k dispozici v místním počítači s názvem instance SqlExpress a že jste vytvořili přihlášení serveru SQL, které se shodují s těmi, zadaný v připojovacích řetězcích. Budete muset povolit přihlášení serveru SQL, pokud je server nakonfigurovaný pomocí výchozích nastavení zabezpečení, která umožňuje pouze ověřování systému Windows. Upravte připojovací řetězce podle potřeby, aby odpovídaly vašemu prostředí.  
  
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
        ' you can retrive it from a configuration file.   
        Return ("Data Source=.\SqlExpress;Integrated Security=True;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionString() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
        Return ("Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" &   
          "Initial Catalog=AdventureWorks")  
    End Function  
  
    Private Shared Function GetSqlConnectionStringDifferent() As String  
        ' To avoid storing the connection string in your code,   
        ' you can retrive it from a configuration file.   
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
        // you can retrive it from a configuration file.  
        return @"Data Source=.\SqlExpress;Integrated Security=True;" +  
          "Initial Catalog=AdventureWorks";  
    }  
    private static string GetSqlConnectionString()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Data Source=.\SqlExpress;User Id=LowPriv;Password=Data!05;" +  
        //  "Initial Catalog=AdventureWorks";  
    }  
  
    private static string GetSqlConnectionStringDifferent()  
    {  
        // To avoid storing the connection string in your code,  
        // you can retrive it from a configuration file.  
        return @"Initial Catalog=AdventureWorks;Data Source=.\SqlExpress;" +  
          "User Id=LowPriv;Password=Data!05;";  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Připojení ke zdroji dat](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Sdružování připojení OLE DB, ODBC a Oracle](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [Čítače výkonu pro technologii ASP.NET](http://msdn.microsoft.com/library/1e122fcb-05c0-4f9f-bef1-f47023fa1ac6)  
 [Běhová profilace](../../../../docs/framework/debug-trace-profile/runtime-profiling.md)  
 [Úvod do monitorování prahové hodnoty výkonu](http://msdn.microsoft.com/library/d40f10b9-e2b7-4ec8-a9b3-706929e5bf35)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
