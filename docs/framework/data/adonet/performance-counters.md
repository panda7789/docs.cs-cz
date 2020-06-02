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
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="fe3f4-103">Čítače výkonu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe3f4-103">Performance Counters in ADO.NET</span></span>
<span data-ttu-id="fe3f4-104">ADO.NET 2,0 představil rozšířenou podporu pro čítače výkonu, které zahrnují podporu pro i <xref:System.Data.SqlClient> <xref:System.Data.OracleClient> .</span><span class="sxs-lookup"><span data-stu-id="fe3f4-104">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="fe3f4-105"><xref:System.Data.SqlClient>Čítače výkonu dostupné v předchozích verzích ADO.NET byly zastaralé a nahrazeny novými čítači výkonu popsanými v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-105">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="fe3f4-106">Pomocí čítačů výkonu ADO.NET můžete monitorovat stav aplikace a prostředky připojení, které používá.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-106">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="fe3f4-107">Čítače výkonu lze monitorovat pomocí nástroje sledování výkonu systému Windows nebo lze programově přistupovat pomocí <xref:System.Diagnostics.PerformanceCounter> třídy v <xref:System.Diagnostics> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-107">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="fe3f4-108">Dostupné čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="fe3f4-108">Available Performance Counters</span></span>  
 <span data-ttu-id="fe3f4-109">V současné době jsou k dispozici 14 různých čítačů výkonu pro <xref:System.Data.SqlClient> a <xref:System.Data.OracleClient> jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-109">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="fe3f4-110">Všimněte si, že názvy jednotlivých čítačů nejsou lokalizovány mezi regionální verze .NET Framework Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-110">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="fe3f4-111">Čítač výkonu</span><span class="sxs-lookup"><span data-stu-id="fe3f4-111">Performance counter</span></span>|<span data-ttu-id="fe3f4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fe3f4-112">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="fe3f4-113">Počet připojení za sekundu, které se provádí na databázovém serveru.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-113">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="fe3f4-114">Počet odpojení za sekundu, které se provádí na databázovém serveru.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-114">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="fe3f4-115">Počet jedinečných skupin fondu připojení, které jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-115">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="fe3f4-116">Tento čítač je řízen počtem jedinečných připojovacích řetězců, které jsou nalezeny v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-116">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="fe3f4-117">Celkový počet fondů připojení.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-117">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="fe3f4-118">Počet aktivních připojení, která jsou aktuálně používána.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-118">The number of active connections that are currently in use.</span></span> <span data-ttu-id="fe3f4-119">**Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-119">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="fe3f4-120">Pokud chcete tento čítač výkonu povolit, přečtěte si téma [Aktivace čítačů mimo výchozí](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="fe3f4-120">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="fe3f4-121">Počet připojení, která jsou k dispozici pro použití ve fondech připojení.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-121">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="fe3f4-122">**Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-122">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="fe3f4-123">Pokud chcete tento čítač výkonu povolit, přečtěte si téma [Aktivace čítačů mimo výchozí](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="fe3f4-123">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="fe3f4-124">Počet jedinečných skupin fondů připojení, které jsou označeny pro vyřazení.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-124">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="fe3f4-125">Tento čítač je řízen počtem jedinečných připojovacích řetězců, které jsou nalezeny v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-125">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="fe3f4-126">Počet neaktivních fondů připojení, které nemají žádnou poslední aktivitu a čekají na jejich vyřazení.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-126">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="fe3f4-127">Počet aktivních připojení, která nejsou ve fondu.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-127">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="fe3f4-128">Počet aktivních připojení, která jsou spravována infrastrukturou sdružování připojení.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-128">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="fe3f4-129">Počet připojení, která byla uvolněna prostřednictvím uvolňování paměti, kdy `Close` `Dispose` aplikace nevolala.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-129">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="fe3f4-130">Nepovedlo se explicitně uzavřít ani vyřadit připojení neuškodí výkon.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-130">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="fe3f4-131">Počet připojení, které aktuálně čekají na dokončení akce a které jsou proto nedostupné pro použití vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-131">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="fe3f4-132">Počet aktivních připojení, která jsou načítána z fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-132">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="fe3f4-133">**Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-133">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="fe3f4-134">Pokud chcete tento čítač výkonu povolit, přečtěte si téma [Aktivace čítačů mimo výchozí](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="fe3f4-134">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="fe3f4-135">Počet aktivních připojení, které jsou vraceny do fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-135">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="fe3f4-136">**Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-136">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="fe3f4-137">Pokud chcete tento čítač výkonu povolit, přečtěte si téma [Aktivace čítačů mimo výchozí](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="fe3f4-137">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="fe3f4-138">Skupiny fondu připojení a fondy připojení</span><span class="sxs-lookup"><span data-stu-id="fe3f4-138">Connection Pool Groups and Connection Pools</span></span>  
 <span data-ttu-id="fe3f4-139">Při použití ověřování systému Windows (integrované zabezpečení) je nutné monitorovat `NumberOfActiveConnectionPoolGroups` `NumberOfActiveConnectionPools` čítače výkonu a.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-139">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="fe3f4-140">Důvodem je, že se skupiny fondu připojení mapují na jedinečné připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-140">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="fe3f4-141">Při použití integrovaného zabezpečení se fondy připojení mapují na připojovací řetězce a navíc vytvoří samostatné fondy pro jednotlivé identity Windows.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-141">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="fe3f4-142">Například pokud Fred a Julie každý v rámci stejné domény AppDomain, oba používají připojovací řetězec, vytvoří se `"Data Source=MySqlServer;Integrated Security=true"` Skupina fondu připojení pro připojovací řetězec a vytvoří se dva další fondy, jeden pro Fred a druhý pro Julie.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-142">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="fe3f4-143">Pokud Jan a Martha používají připojovací řetězec se stejným SQL Server přihlášením, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"` vytvoří se pro identitu **lowPrivUser** jenom jeden fond.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-143">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>
### <a name="activating-off-by-default-counters"></a><span data-ttu-id="fe3f4-144">Aktivace čítačů mimo výchozí</span><span class="sxs-lookup"><span data-stu-id="fe3f4-144">Activating Off-By-Default Counters</span></span>  
 <span data-ttu-id="fe3f4-145">Čítače výkonu `NumberOfFreeConnections` ,, `NumberOfActiveConnections` `SoftDisconnectsPerSecond` a `SoftConnectsPerSecond` jsou ve výchozím nastavení vypnuté.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-145">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="fe3f4-146">Do konfiguračního souboru aplikace přidejte následující informace, abyste je povolili:</span><span class="sxs-lookup"><span data-stu-id="fe3f4-146">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="fe3f4-147">Načítání hodnot čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="fe3f4-147">Retrieving Performance Counter Values</span></span>  
 <span data-ttu-id="fe3f4-148">Následující aplikace konzoly ukazuje, jak načíst hodnoty čítače výkonu ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-148">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="fe3f4-149">Aby bylo možné vracet informace pro všechny čítače výkonu ADO.NET, musí být připojení otevřená a aktivní.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-149">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe3f4-150">V tomto příkladu se používá ukázková databáze **AdventureWorks** obsažená v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-150">This example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="fe3f4-151">Připojovací řetězce, které jsou uvedeny v ukázkovém kódu, předpokládají, že je databáze nainstalována a dostupná v místním počítači s názvem instance SqlExpress a že jste vytvořili SQL Server přihlašovacích údajů, které odpovídají zadaným řetězcům v připojovacích řetězcích.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-151">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="fe3f4-152">Pokud je server nakonfigurovaný pomocí výchozího nastavení zabezpečení, které povoluje jenom ověřování systému Windows, může být nutné povolit SQL Server přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-152">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="fe3f4-153">Upravte připojovací řetězce podle potřeby tak, aby vyhovovaly vašemu prostředí.</span><span class="sxs-lookup"><span data-stu-id="fe3f4-153">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="fe3f4-154">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe3f4-154">Example</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="fe3f4-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe3f4-155">See also</span></span>

- [<span data-ttu-id="fe3f4-156">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="fe3f4-156">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="fe3f4-157">Sdružování připojení OLE DB, ODBC a Oracle</span><span class="sxs-lookup"><span data-stu-id="fe3f4-157">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- <span data-ttu-id="fe3f4-158">[Čítače výkonu pro ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fe3f4-158">[Performance Counters for ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))</span></span>
- [<span data-ttu-id="fe3f4-159">Běhová profilace</span><span class="sxs-lookup"><span data-stu-id="fe3f4-159">Runtime Profiling</span></span>](../../debug-trace-profile/runtime-profiling.md)
- <span data-ttu-id="fe3f4-160">[Úvod do monitorování mezních hodnot výkonu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fe3f4-160">[Introduction to Monitoring Performance Thresholds](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span></span>
- [<span data-ttu-id="fe3f4-161">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="fe3f4-161">ADO.NET Overview</span></span>](ado-net-overview.md)
