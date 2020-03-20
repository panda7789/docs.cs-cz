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
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="39967-102">Čítače výkonu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="39967-102">Performance Counters in ADO.NET</span></span>
<span data-ttu-id="39967-103">ADO.NET 2.0 zavedlrozšířenou podporu čítačů <xref:System.Data.SqlClient> <xref:System.Data.OracleClient>výkonu, která zahrnuje podporu pro obě a .</span><span class="sxs-lookup"><span data-stu-id="39967-103">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="39967-104">Čítače <xref:System.Data.SqlClient> výkonu dostupné v předchozích verzích ADO.NET byly zastaralé a nahrazeny novými čítači výkonu popsanými v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="39967-104">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="39967-105">Pomocí ADO.NET čítačů výkonu můžete sledovat stav aplikace a prostředků připojení, které používá.</span><span class="sxs-lookup"><span data-stu-id="39967-105">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="39967-106">Čítače výkonu lze sledovat pomocí programu Sledování výkonu systému <xref:System.Diagnostics.PerformanceCounter> Windows nebo <xref:System.Diagnostics> lze k nim přistupovat programově pomocí třídy v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="39967-106">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="39967-107">Dostupné čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="39967-107">Available Performance Counters</span></span>  
 <span data-ttu-id="39967-108">V současné době je k dispozici <xref:System.Data.SqlClient> 14 různých čítačů výkonu pro a <xref:System.Data.OracleClient> jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="39967-108">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="39967-109">Všimněte si, že názvy pro jednotlivé čítače nejsou lokalizovány v rámci místní verze rozhraní Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="39967-109">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="39967-110">Čítač výkonu</span><span class="sxs-lookup"><span data-stu-id="39967-110">Performance counter</span></span>|<span data-ttu-id="39967-111">Popis</span><span class="sxs-lookup"><span data-stu-id="39967-111">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="39967-112">Počet připojení za sekundu, které jsou prováděny na databázový server.</span><span class="sxs-lookup"><span data-stu-id="39967-112">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="39967-113">Počet odpojení za sekundu, které jsou prováděny na databázovém serveru.</span><span class="sxs-lookup"><span data-stu-id="39967-113">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="39967-114">Počet jedinečných skupin fondu připojení, které jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="39967-114">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="39967-115">Tento čítač je řízen počtem jedinečných připojovacích řetězců, které se nacházejí v AppDomain.</span><span class="sxs-lookup"><span data-stu-id="39967-115">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="39967-116">Celkový počet fondů připojení.</span><span class="sxs-lookup"><span data-stu-id="39967-116">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="39967-117">Počet aktivních připojení, která jsou aktuálně používána.</span><span class="sxs-lookup"><span data-stu-id="39967-117">The number of active connections that are currently in use.</span></span> <span data-ttu-id="39967-118">**Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen.</span><span class="sxs-lookup"><span data-stu-id="39967-118">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="39967-119">Chcete-li povolit tento čítač výkonu, [přečtěte si téma Aktivace čítačů mimo výchozí nastavení](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="39967-119">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="39967-120">Počet připojení, která jsou k dispozici pro použití ve fondech připojení.</span><span class="sxs-lookup"><span data-stu-id="39967-120">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="39967-121">**Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen.</span><span class="sxs-lookup"><span data-stu-id="39967-121">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="39967-122">Chcete-li povolit tento čítač výkonu, [přečtěte si téma Aktivace čítačů mimo výchozí nastavení](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="39967-122">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="39967-123">Počet jedinečných skupin fondu připojení, které jsou označeny pro vyřezávání.</span><span class="sxs-lookup"><span data-stu-id="39967-123">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="39967-124">Tento čítač je řízen počtem jedinečných připojovacích řetězců, které se nacházejí v AppDomain.</span><span class="sxs-lookup"><span data-stu-id="39967-124">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="39967-125">Počet neaktivních fondů připojení, které neměly žádné nedávné aktivity a čekají na vyřazení.</span><span class="sxs-lookup"><span data-stu-id="39967-125">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="39967-126">Počet aktivních připojení, které nejsou sdružené.</span><span class="sxs-lookup"><span data-stu-id="39967-126">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="39967-127">Počet aktivních připojení, které jsou spravovány infrastrukturou sdružování připojení.</span><span class="sxs-lookup"><span data-stu-id="39967-127">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="39967-128">Počet připojení, které byly uvolněny prostřednictvím `Close` `Dispose` uvolňování paměti, kde nebo nebyl volán aplikací.</span><span class="sxs-lookup"><span data-stu-id="39967-128">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="39967-129">Neexplicitní uzavření nebo likvidace spojení poškozuje výkon.</span><span class="sxs-lookup"><span data-stu-id="39967-129">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="39967-130">Počet připojení, která aktuálně čekají na dokončení akce a která proto nejsou k dispozici pro použití vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="39967-130">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="39967-131">Počet aktivních připojení, která jsou vyžádána z fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="39967-131">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="39967-132">**Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen.</span><span class="sxs-lookup"><span data-stu-id="39967-132">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="39967-133">Chcete-li povolit tento čítač výkonu, [přečtěte si téma Aktivace čítačů mimo výchozí nastavení](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="39967-133">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="39967-134">Počet aktivních připojení, která jsou právě vrácena do fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="39967-134">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="39967-135">**Poznámka:**  Tento čítač výkonu není ve výchozím nastavení povolen.</span><span class="sxs-lookup"><span data-stu-id="39967-135">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="39967-136">Chcete-li povolit tento čítač výkonu, [přečtěte si téma Aktivace čítačů mimo výchozí nastavení](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="39967-136">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="39967-137">Skupiny fondu připojení a fondy připojení</span><span class="sxs-lookup"><span data-stu-id="39967-137">Connection Pool Groups and Connection Pools</span></span>  
 <span data-ttu-id="39967-138">Při použití ověřování systému Windows (integrované `NumberOfActiveConnectionPoolGroups` `NumberOfActiveConnectionPools` zabezpečení) je nutné sledovat čítače i čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="39967-138">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="39967-139">Důvodem je, že skupiny fondu připojení mapovat na jedinečné připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="39967-139">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="39967-140">Při použití integrovaného zabezpečení se fondy připojení mapují na připojovací řetězce a navíc vytvářejí samostatné fondy pro jednotlivé identity systému Windows.</span><span class="sxs-lookup"><span data-stu-id="39967-140">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="39967-141">Například pokud Fred a Julie, každý v rámci stejné `"Data Source=MySqlServer;Integrated Security=true"`AppDomain, oba používají připojovací řetězec , je vytvořena skupina fondu připojení pro připojovací řetězec a dva další fondy jsou vytvořeny, jeden pro Fred a jeden pro Julie.</span><span class="sxs-lookup"><span data-stu-id="39967-141">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="39967-142">Pokud Jan a Martha použít připojovací `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`řetězec s identické přihlášení SQL Server , pak je vytvořen pouze jeden fond pro **lowPrivUser** identity.</span><span class="sxs-lookup"><span data-stu-id="39967-142">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>
### <a name="activating-off-by-default-counters"></a><span data-ttu-id="39967-143">Aktivace čítačů mimo výchozí nastavení</span><span class="sxs-lookup"><span data-stu-id="39967-143">Activating Off-By-Default Counters</span></span>  
 <span data-ttu-id="39967-144">Čítače `NumberOfFreeConnections` `NumberOfActiveConnections`výkonu `SoftDisconnectsPerSecond`, `SoftConnectsPerSecond` , a jsou ve výchozím nastavení vypnuty.</span><span class="sxs-lookup"><span data-stu-id="39967-144">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="39967-145">Přidejte do konfiguračního souboru aplikace následující informace, které je povolte:</span><span class="sxs-lookup"><span data-stu-id="39967-145">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="39967-146">Načítání hodnot čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="39967-146">Retrieving Performance Counter Values</span></span>  
 <span data-ttu-id="39967-147">Následující konzolová aplikace ukazuje, jak načíst hodnoty čítače výkonu ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="39967-147">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="39967-148">Připojení musí být otevřená a aktivní, aby informace byly vráceny pro všechny čítače výkonu ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="39967-148">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39967-149">Tento příklad používá ukázkovou databázi **AdventureWorks,** která je součástí serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="39967-149">This example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="39967-150">Připojovací řetězce uvedené v ukázkovém kódu předpokládají, že databáze je nainstalována a k dispozici v místním počítači s názvem instance SqlExpress a že jste vytvořili přihlášení serveru SQL Server, které odpovídají těm, které jsou součástí připojovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="39967-150">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="39967-151">Pokud je server nakonfigurován pomocí výchozího nastavení zabezpečení, které umožňuje pouze ověřování systému Windows, bude pravděpodobně nutné povolit přihlášení serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="39967-151">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="39967-152">Podle potřeby upravte připojovací řetězce tak, aby vyhovovaly vašemu prostředí.</span><span class="sxs-lookup"><span data-stu-id="39967-152">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="39967-153">Příklad</span><span class="sxs-lookup"><span data-stu-id="39967-153">Example</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="39967-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="39967-154">See also</span></span>

- [<span data-ttu-id="39967-155">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="39967-155">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="39967-156">Sdružování připojení OLE DB, ODBC a Oracle</span><span class="sxs-lookup"><span data-stu-id="39967-156">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)
- <span data-ttu-id="39967-157">[Čítače výkonu pro ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="39967-157">[Performance Counters for ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/fxk122b4(v=vs.100))</span></span>
- [<span data-ttu-id="39967-158">Běhová profilace</span><span class="sxs-lookup"><span data-stu-id="39967-158">Runtime Profiling</span></span>](../../debug-trace-profile/runtime-profiling.md)
- <span data-ttu-id="39967-159">[Úvod do sledování prahových hodnot výkonu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="39967-159">[Introduction to Monitoring Performance Thresholds](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bd20x32d(v=vs.90))</span></span>
- [<span data-ttu-id="39967-160">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="39967-160">ADO.NET Overview</span></span>](ado-net-overview.md)
