---
title: Čítače výkonu v technologii ADO.NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0b121b71-78f8-4ae2-9aa1-0b2e15778e57
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: a36e552392f887cd4e0f6dfac822c87f08a90af7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="performance-counters-in-adonet"></a><span data-ttu-id="7c9b8-102">Čítače výkonu v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7c9b8-102">Performance Counters in ADO.NET</span></span>
<span data-ttu-id="7c9b8-103">ADO.NET 2.0 zavedená rozšířenou podporu pro čítače výkonu, který zahrnuje podporu pro obě <xref:System.Data.SqlClient> a <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-103">ADO.NET 2.0 introduced expanded support for performance counters that includes support for both <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient>.</span></span> <span data-ttu-id="7c9b8-104"><xref:System.Data.SqlClient> Čítače výkonu, které jsou k dispozici v předchozích verzích technologie ADO.NET byly zastaralé a nahradí nové čítače výkonu, které jsou popsané v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-104">The <xref:System.Data.SqlClient> performance counters available in previous versions of ADO.NET have been deprecated and replaced with the new performance counters discussed in this topic.</span></span> <span data-ttu-id="7c9b8-105">Čítače výkonu technologie ADO.NET můžete použít k monitorování stavu aplikace a prostředky připojení, které používá.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-105">You can use ADO.NET performance counters to monitor the status of your application and the connection resources that it uses.</span></span> <span data-ttu-id="7c9b8-106">Čítače výkonu pomocí sledování výkonu systému Windows se dá sledovat nebo k němu přístup programově pomocí <xref:System.Diagnostics.PerformanceCounter> třídy v <xref:System.Diagnostics> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-106">Performance counters can be monitored by using Windows Performance Monitor or can be accessed programmatically using the <xref:System.Diagnostics.PerformanceCounter> class in the <xref:System.Diagnostics> namespace.</span></span>  
  
## <a name="available-performance-counters"></a><span data-ttu-id="7c9b8-107">Čítače výkonu k dispozici</span><span class="sxs-lookup"><span data-stu-id="7c9b8-107">Available Performance Counters</span></span>  
 <span data-ttu-id="7c9b8-108">Aktuálně nejsou 14 různých čítače k dispozici pro <xref:System.Data.SqlClient> a <xref:System.Data.OracleClient> jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-108">Currently there are 14 different performance counters available for <xref:System.Data.SqlClient> and <xref:System.Data.OracleClient> as described in the following table.</span></span> <span data-ttu-id="7c9b8-109">Všimněte si, že názvy pro jednotlivé čítače nejsou lokalizovány mezi místní verze rozhraní Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-109">Note that the names for the individual counters are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="7c9b8-110">Čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="7c9b8-110">Performance counter</span></span>|<span data-ttu-id="7c9b8-111">Popis</span><span class="sxs-lookup"><span data-stu-id="7c9b8-111">Description</span></span>|  
|-------------------------|-----------------|  
|`HardConnectsPerSecond`|<span data-ttu-id="7c9b8-112">Počet připojení za sekundu, které jsou určené k databázovému serveru.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-112">The number of connections per second that are being made to a database server.</span></span>|  
|`HardDisconnectsPerSecond`|<span data-ttu-id="7c9b8-113">Počet odpojí za sekundu, které jsou určené k databázovému serveru.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-113">The number of disconnects per second that are being made to a database server.</span></span>|  
|`NumberOfActiveConnectionPoolGroups`|<span data-ttu-id="7c9b8-114">Počet skupin fondu jedinečný připojení, které jsou aktivní.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-114">The number of unique connection pool groups that are active.</span></span> <span data-ttu-id="7c9b8-115">Tento čítač je řízena podle počtu jedinečných připojovací řetězce, které se nacházejí v domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-115">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfActiveConnectionPools`|<span data-ttu-id="7c9b8-116">Celkový počet připojení fondy.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-116">The total number of connection pools.</span></span>|  
|`NumberOfActiveConnections`|<span data-ttu-id="7c9b8-117">Počet aktivních připojení, které jsou právě používány.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-117">The number of active connections that are currently in use.</span></span> <span data-ttu-id="7c9b8-118">**Poznámka:** tento čítač výkonu není ve výchozím nastavení povolené.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-118">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="7c9b8-119">Pokud chcete povolit tento čítač výkonu, najdete v části [aktivace vypnout výchozím čítače](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="7c9b8-119">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfFreeConnections`|<span data-ttu-id="7c9b8-120">Počet připojení, které jsou k dispozici pro použití ve fondech připojení.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-120">The number of connections available for use in the connection pools.</span></span> <span data-ttu-id="7c9b8-121">**Poznámka:** tento čítač výkonu není ve výchozím nastavení povolené.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-121">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="7c9b8-122">Pokud chcete povolit tento čítač výkonu, najdete v části [aktivace vypnout výchozím čítače](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="7c9b8-122">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`NumberOfInactiveConnectionPoolGroups`|<span data-ttu-id="7c9b8-123">Počet skupin fondu jedinečný připojení, které jsou označeny k vyřazení.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-123">The number of unique connection pool groups that are marked for pruning.</span></span> <span data-ttu-id="7c9b8-124">Tento čítač je řízena podle počtu jedinečných připojovací řetězce, které se nacházejí v domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-124">This counter is controlled by the number of unique connection strings that are found in the AppDomain.</span></span>|  
|`NumberOfInactiveConnectionPools`|<span data-ttu-id="7c9b8-125">Počet neaktivních připojení fondy, které nedošlo k žádné poslední aktivitu a čekají na zlikvidován.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-125">The number of inactive connection pools that have not had any recent activity and are waiting to be disposed.</span></span>|  
|`NumberOfNonPooledConnections`|<span data-ttu-id="7c9b8-126">Počet aktivních připojení, které nejsou ve fondu.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-126">The number of active connections that are not pooled.</span></span>|  
|`NumberOfPooledConnections`|<span data-ttu-id="7c9b8-127">Počet aktivních připojení, které spravuje infrastrukturu sdružování připojení.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-127">The number of active connections that are being managed by the connection pooling infrastructure.</span></span>|  
|`NumberOfReclaimedConnections`|<span data-ttu-id="7c9b8-128">Počet připojení, které bylo uvolněno prostřednictvím uvolňování kde `Close` nebo `Dispose` nebyla volána aplikací.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-128">The number of connections that have been reclaimed through garbage collection where `Close` or `Dispose` was not called by the application.</span></span> <span data-ttu-id="7c9b8-129">Není explicitně zavírání nebo uvolnění připojení škodí jak výkonu.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-129">Not explicitly closing or disposing connections hurts performance.</span></span>|  
|`NumberOfStasisConnections`|<span data-ttu-id="7c9b8-130">Počet připojení, které jsou aktuálně čeká na dokončení akce a které proto není k dispozici pro použití aplikací.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-130">The number of connections currently awaiting completion of an action and which are therefore unavailable for use by your application.</span></span>|  
|`SoftConnectsPerSecond`|<span data-ttu-id="7c9b8-131">Počet aktivních připojení patrně fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-131">The number of active connections being pulled from the connection pool.</span></span> <span data-ttu-id="7c9b8-132">**Poznámka:** tento čítač výkonu není ve výchozím nastavení povolené.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-132">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="7c9b8-133">Pokud chcete povolit tento čítač výkonu, najdete v části [aktivace vypnout výchozím čítače](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="7c9b8-133">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
|`SoftDisconnectsPerSecond`|<span data-ttu-id="7c9b8-134">Počet aktivních připojení, které se vrací do fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-134">The number of active connections that are being returned to the connection pool.</span></span> <span data-ttu-id="7c9b8-135">**Poznámka:** tento čítač výkonu není ve výchozím nastavení povolené.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-135">**Note:**  This performance counter is not enabled by default.</span></span> <span data-ttu-id="7c9b8-136">Pokud chcete povolit tento čítač výkonu, najdete v části [aktivace vypnout výchozím čítače](#ActivatingOffByDefault).</span><span class="sxs-lookup"><span data-stu-id="7c9b8-136">To enable this performance counter, see [Activating Off-By-Default Counters](#ActivatingOffByDefault).</span></span>|  
  
### <a name="connection-pool-groups-and-connection-pools"></a><span data-ttu-id="7c9b8-137">Skupiny fondu připojení a připojení fondy</span><span class="sxs-lookup"><span data-stu-id="7c9b8-137">Connection Pool Groups and Connection Pools</span></span>  
 <span data-ttu-id="7c9b8-138">Pokud používáte ověřování systému Windows (integrované zabezpečení), je třeba sledovat i `NumberOfActiveConnectionPoolGroups` a `NumberOfActiveConnectionPools` čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-138">When using Windows Authentication (integrated security), you must monitor both the `NumberOfActiveConnectionPoolGroups` and `NumberOfActiveConnectionPools` performance counters.</span></span> <span data-ttu-id="7c9b8-139">Důvodem je, které jsou namapovány fondu skupin připojení na jedinečný připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-139">The reason is that connection pool groups map to unique connection strings.</span></span> <span data-ttu-id="7c9b8-140">Pokud se používá integrované zabezpečení, sdružení připojení mapovat připojovací řetězce a kromě vytvořit samostatné fondy pro jednotlivé Windows identity.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-140">When integrated security is used, connection pools map to connection strings and additionally create separate pools for individual Windows identities.</span></span> <span data-ttu-id="7c9b8-141">Například, pokud František a Julie, každou v rámci stejné domény aplikace, jak použít připojovací řetězec `"Data Source=MySqlServer;Integrated Security=true"`, skupinu fondu připojení se vytvoří pro připojovací řetězec a jsou vytvořeny dva další fondy, jeden pro František a jeden pro Julie.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-141">For example, if Fred and Julie, each within the same AppDomain, both use the connection string `"Data Source=MySqlServer;Integrated Security=true"`, a connection pool group is created for the connection string, and two additional pools are created, one for Fred and one for Julie.</span></span> <span data-ttu-id="7c9b8-142">Pokud Jan a Marta použijete připojovací řetězec s identické přihlášení systému SQL Server, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, pak pouze jednoho fondu se vytvoří pro **lowPrivUser** identity.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-142">If John and Martha use a connection string with an identical SQL Server login, `"Data Source=MySqlServer;User Id=lowPrivUser;Password=Strong?Password"`, then only a single pool is created for the **lowPrivUser** identity.</span></span>  
  
<a name="ActivatingOffByDefault"></a>   
### <a name="activating-off-by-default-counters"></a><span data-ttu-id="7c9b8-143">Aktivace vypnout výchozím čítače</span><span class="sxs-lookup"><span data-stu-id="7c9b8-143">Activating Off-By-Default Counters</span></span>  
 <span data-ttu-id="7c9b8-144">Čítače výkonu `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, a `SoftConnectsPerSecond` jsou ve výchozím nastavení vypnuté.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-144">The performance counters `NumberOfFreeConnections`, `NumberOfActiveConnections`, `SoftDisconnectsPerSecond`, and `SoftConnectsPerSecond` are off by default.</span></span> <span data-ttu-id="7c9b8-145">Přidejte do konfiguračního souboru aplikace a umožňuje jim následující informace:</span><span class="sxs-lookup"><span data-stu-id="7c9b8-145">Add the following information to the application's configuration file to enable them:</span></span>  
  
```xml  
<system.diagnostics>  
  <switches>  
    <add name="ConnectionPoolPerformanceCounterDetail"  
         value="4"/>  
  </switches>  
</system.diagnostics>  
```  
  
## <a name="retrieving-performance-counter-values"></a><span data-ttu-id="7c9b8-146">Načítání hodnoty čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="7c9b8-146">Retrieving Performance Counter Values</span></span>  
 <span data-ttu-id="7c9b8-147">Následující aplikace konzoly ukazuje, jak načíst hodnoty čítače výkonu ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-147">The following console application shows how to retrieve performance counter values in your application.</span></span> <span data-ttu-id="7c9b8-148">Připojení musí být otevřený a aktivní informace, které má být vrácen pro všechny čítače výkonu technologie ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-148">Connections must be open and active for information to be returned for all of the ADO.NET performance counters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c9b8-149">Tento příklad používá vzorku **AdventureWorks** databáze je součástí systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-149">This example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="7c9b8-150">Připojovací řetězce, který je součástí ukázkový kód předpokládají, že databáze je nainstalovaná a k dispozici v místním počítači s názvem instance SqlExpress a že jste vytvořili přihlášení serveru SQL, které se shodují s těmi, zadaný v připojovacích řetězcích.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-150">The connection strings provided in the sample code assume that the database is installed and available on the local computer with an instance name of SqlExpress, and that you have created SQL Server logins that match those supplied in the connection strings.</span></span> <span data-ttu-id="7c9b8-151">Budete muset povolit přihlášení serveru SQL, pokud je server nakonfigurovaný pomocí výchozích nastavení zabezpečení, která umožňuje pouze ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-151">You may need to enable SQL Server logins if your server is configured using the default security settings which allow only Windows Authentication.</span></span> <span data-ttu-id="7c9b8-152">Upravte připojovací řetězce podle potřeby, aby odpovídaly vašemu prostředí.</span><span class="sxs-lookup"><span data-stu-id="7c9b8-152">Modify the connection strings as necessary to suit your environment.</span></span>  
  
### <a name="example"></a><span data-ttu-id="7c9b8-153">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c9b8-153">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7c9b8-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c9b8-154">See Also</span></span>  
 [<span data-ttu-id="7c9b8-155">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="7c9b8-155">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="7c9b8-156">Sdružování připojení OLE DB, ODBC a Oracle</span><span class="sxs-lookup"><span data-stu-id="7c9b8-156">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 [<span data-ttu-id="7c9b8-157">Čítače výkonu pro technologii ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7c9b8-157">Performance Counters for ASP.NET</span></span>](http://msdn.microsoft.com/library/1e122fcb-05c0-4f9f-bef1-f47023fa1ac6)  
 [<span data-ttu-id="7c9b8-158">Běhová profilace</span><span class="sxs-lookup"><span data-stu-id="7c9b8-158">Runtime Profiling</span></span>](../../../../docs/framework/debug-trace-profile/runtime-profiling.md)  
 [<span data-ttu-id="7c9b8-159">Úvod do monitorování prahové hodnoty výkonu</span><span class="sxs-lookup"><span data-stu-id="7c9b8-159">Introduction to Monitoring Performance Thresholds</span></span>](http://msdn.microsoft.com/library/d40f10b9-e2b7-4ec8-a9b3-706929e5bf35)  
 [<span data-ttu-id="7c9b8-160">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="7c9b8-160">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
