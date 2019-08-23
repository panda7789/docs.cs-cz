---
title: Vytváření výčtu instancí SQL Serveru (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: 304387197c7c6ca31d76ce429cd1516be27ba7b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938178"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="b3f6f-102">Vytváření výčtu instancí SQL Serveru (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="b3f6f-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
<span data-ttu-id="b3f6f-103">SQL Server umožňuje aplikacím najít SQL Server instance v rámci aktuální sítě.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-103">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="b3f6f-104">Třída zpřístupňuje tyto informace vývojáři aplikace a <xref:System.Data.DataTable> poskytuje informace o všech viditelných serverech. <xref:System.Data.Sql.SqlDataSourceEnumerator></span><span class="sxs-lookup"><span data-stu-id="b3f6f-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="b3f6f-105">Tato vrácená tabulka obsahuje seznam instancí serveru dostupných v síti, které se shodují se seznamem zadaným při pokusu uživatele o vytvoření nového připojení, a rozbalí rozevírací seznam obsahující všechny dostupné servery ve **vlastnostech připojení.** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="b3f6f-106">Zobrazené výsledky nejsou vždy dokončeny.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3f6f-107">Stejně jako u většiny služeb Windows je nejlepší spustit službu SQL Browser s nejmenšími možnými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="b3f6f-108">Další informace o službě SQL Browser a o tom, jak spravovat její chování, najdete v tématu SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-108">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="b3f6f-109">Načítání instance enumerátoru</span><span class="sxs-lookup"><span data-stu-id="b3f6f-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="b3f6f-110">Aby bylo možné načíst tabulku obsahující informace o dostupných instancích SQL Server, je nutné nejprve načíst enumerátor pomocí vlastnosti Shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> :</span><span class="sxs-lookup"><span data-stu-id="b3f6f-110">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="b3f6f-111">Po načtení statické instance můžete zavolat <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metodu, která <xref:System.Data.DataTable> vrátí obsahující informace o dostupných serverech:</span><span class="sxs-lookup"><span data-stu-id="b3f6f-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="b3f6f-112">Tabulka vrácená voláním metody obsahuje následující sloupce, z nichž všechny obsahují `string` hodnoty:</span><span class="sxs-lookup"><span data-stu-id="b3f6f-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="b3f6f-113">Sloupec</span><span class="sxs-lookup"><span data-stu-id="b3f6f-113">Column</span></span>|<span data-ttu-id="b3f6f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b3f6f-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="b3f6f-115">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="b3f6f-115">**ServerName**</span></span>|<span data-ttu-id="b3f6f-116">Název serveru.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-116">Name of the server.</span></span>|  
|<span data-ttu-id="b3f6f-117">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="b3f6f-117">**InstanceName**</span></span>|<span data-ttu-id="b3f6f-118">Název instance serveru.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-118">Name of the server instance.</span></span> <span data-ttu-id="b3f6f-119">Prázdné, pokud server běží jako výchozí instance.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="b3f6f-120">**Clusterované**</span><span class="sxs-lookup"><span data-stu-id="b3f6f-120">**IsClustered**</span></span>|<span data-ttu-id="b3f6f-121">Označuje, zda je Server součástí clusteru.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="b3f6f-122">**Verze**</span><span class="sxs-lookup"><span data-stu-id="b3f6f-122">**Version**</span></span>|<span data-ttu-id="b3f6f-123">Verze serveru.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-123">Version of the server.</span></span> <span data-ttu-id="b3f6f-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b3f6f-124">For example:</span></span><br /><br /> <span data-ttu-id="b3f6f-125">-9.00. x (SQL Server 2005)</span><span class="sxs-lookup"><span data-stu-id="b3f6f-125">-   9.00.x (SQL Server 2005)</span></span><br /><span data-ttu-id="b3f6f-126">-   10.0.xx (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="b3f6f-126">-   10.0.xx (SQL Server 2008)</span></span><br /><span data-ttu-id="b3f6f-127">-   10.50.x (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="b3f6f-127">-   10.50.x (SQL Server 2008 R2)</span></span><br /><span data-ttu-id="b3f6f-128">-   11.0.xx (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="b3f6f-128">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="b3f6f-129">Omezení výčtu</span><span class="sxs-lookup"><span data-stu-id="b3f6f-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="b3f6f-130">Všechny dostupné servery můžou nebo nemusí být uvedené.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="b3f6f-131">Seznam se může lišit v závislosti na faktorech, jako jsou například časové limity a síťový provoz.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="b3f6f-132">To může způsobit, že se seznam bude lišit od dvou po sobě jdoucích volání.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="b3f6f-133">Zobrazí se pouze servery ve stejné síti.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="b3f6f-134">Pakety všesměrového vysílání obvykle nebudou procházet směrovači, což znamená, že se server nemusí zobrazovat, ale bude stabilní v rámci volání.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="b3f6f-135">Uvedené servery můžou nebo nemusí mít další informace, jako je `IsClustered` verze a.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="b3f6f-136">To závisí na tom, jak byl seznam získán.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="b3f6f-137">Servery uvedené prostřednictvím služby SQL Server Browser budou mít více podrobností, než jaké jsou nalezeny prostřednictvím infrastruktury systému Windows, ve které bude uveden pouze název.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-137">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3f6f-138">Výčet serveru je k dispozici pouze při spuštění v úplném vztahu důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="b3f6f-139">Sestavení spuštěná v částečně důvěryhodném prostředí ji nebudou moct používat, i když mají <xref:System.Data.SqlClient.SqlClientPermission> oprávnění zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="b3f6f-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="b3f6f-140">SQL Server poskytuje informace pro <xref:System.Data.Sql.SqlDataSourceEnumerator> použití externí služby systému Windows s názvem SQL Browser.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-140">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="b3f6f-141">Tato služba je ve výchozím nastavení povolená, ale správci ji můžou vypnout nebo zakázat, takže instance serveru není pro tuto třídu viditelná.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3f6f-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3f6f-142">Example</span></span>  
 <span data-ttu-id="b3f6f-143">Následující aplikace konzoly načte informace o všech viditelných instancích SQL Server a zobrazí informace v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="b3f6f-143">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
```vb  
Imports System.Data.Sql  
  
Module Module1  
  Sub Main()  
    ' Retrieve the enumerator instance and then the data.  
    Dim instance As SqlDataSourceEnumerator = _  
     SqlDataSourceEnumerator.Instance  
    Dim table As System.Data.DataTable = instance.GetDataSources()  
  
    ' Display the contents of the table.  
    DisplayData(table)  
  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Sub  
  
  Private Sub DisplayData(ByVal table As DataTable)  
    For Each row As DataRow In table.Rows  
      For Each col As DataColumn In table.Columns  
        Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
      Next  
      Console.WriteLine("============================")  
    Next  
  End Sub  
End Module  
```  
  
```csharp  
using System.Data.Sql;  
  
class Program  
{  
  static void Main()  
  {  
    // Retrieve the enumerator instance and then the data.  
    SqlDataSourceEnumerator instance =  
      SqlDataSourceEnumerator.Instance;  
    System.Data.DataTable table = instance.GetDataSources();  
  
    // Display the contents of the table.  
    DisplayData(table);  
  
    Console.WriteLine("Press any key to continue.");  
    Console.ReadKey();  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
    foreach (System.Data.DataRow row in table.Rows)  
    {  
      foreach (System.Data.DataColumn col in table.Columns)  
      {  
        Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
      }  
      Console.WriteLine("============================");  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3f6f-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3f6f-144">See also</span></span>

- [<span data-ttu-id="b3f6f-145">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b3f6f-145">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="b3f6f-146">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="b3f6f-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
