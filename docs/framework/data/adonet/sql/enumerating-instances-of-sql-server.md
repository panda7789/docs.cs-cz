---
title: Výčet instancí serveru SQL Server
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: a707df533216613e34d9f357c7b9e035f73b9561
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148683"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="49ed6-102">Vytváření výčtu instancí SQL Serveru (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="49ed6-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
<span data-ttu-id="49ed6-103">SQL Server umožňuje aplikacím najít instance serveru SQL Server v rámci aktuální sítě.</span><span class="sxs-lookup"><span data-stu-id="49ed6-103">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="49ed6-104">Třída <xref:System.Data.Sql.SqlDataSourceEnumerator> zpřístupňuje tyto informace vývojáři <xref:System.Data.DataTable> aplikace a poskytuje informace o všech viditelných serverech.</span><span class="sxs-lookup"><span data-stu-id="49ed6-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="49ed6-105">Tato vrácená tabulka obsahuje seznam instancí serveru dostupných v síti, který odpovídá seznamu poskytnutému při pokusu uživatele o vytvoření nového připojení, a rozbalí rozevírací seznam obsahující všechny dostupné servery v dialogovém okně **Vlastnosti připojení.**</span><span class="sxs-lookup"><span data-stu-id="49ed6-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="49ed6-106">Zobrazené výsledky nejsou vždy úplné.</span><span class="sxs-lookup"><span data-stu-id="49ed6-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49ed6-107">Stejně jako u většiny služeb systému Windows je nejlepší spustit službu prohlížeče SQL s co nejmenšími oprávněními.</span><span class="sxs-lookup"><span data-stu-id="49ed6-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="49ed6-108">Další informace o službě prohlížeče SQL Browser a způsob správy jejího chování naleznete v tématu SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="49ed6-108">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="49ed6-109">Načítání instance čítače výčtu</span><span class="sxs-lookup"><span data-stu-id="49ed6-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="49ed6-110">Chcete-li načíst tabulku obsahující informace o dostupných instancích serveru SQL Server, musíte nejprve načíst čítače enumerator pomocí sdílené/statické <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="49ed6-110">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="49ed6-111">Po načtení statické instance můžete volat <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metodu, která <xref:System.Data.DataTable> vrací obsahující informace o dostupných serverech:</span><span class="sxs-lookup"><span data-stu-id="49ed6-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="49ed6-112">Tabulka vrácená z volání metody obsahuje následující sloupce, které obsahují `string` hodnoty:</span><span class="sxs-lookup"><span data-stu-id="49ed6-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="49ed6-113">Sloupec</span><span class="sxs-lookup"><span data-stu-id="49ed6-113">Column</span></span>|<span data-ttu-id="49ed6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="49ed6-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="49ed6-115">**Název_serveru**</span><span class="sxs-lookup"><span data-stu-id="49ed6-115">**ServerName**</span></span>|<span data-ttu-id="49ed6-116">Název serveru.</span><span class="sxs-lookup"><span data-stu-id="49ed6-116">Name of the server.</span></span>|  
|<span data-ttu-id="49ed6-117">**Název_instance**</span><span class="sxs-lookup"><span data-stu-id="49ed6-117">**InstanceName**</span></span>|<span data-ttu-id="49ed6-118">Název instance serveru.</span><span class="sxs-lookup"><span data-stu-id="49ed6-118">Name of the server instance.</span></span> <span data-ttu-id="49ed6-119">Pokud je server spuštěn jako výchozí instance, je prázdné.</span><span class="sxs-lookup"><span data-stu-id="49ed6-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="49ed6-120">**Jeseskupený**</span><span class="sxs-lookup"><span data-stu-id="49ed6-120">**IsClustered**</span></span>|<span data-ttu-id="49ed6-121">Označuje, zda je server součástí clusteru.</span><span class="sxs-lookup"><span data-stu-id="49ed6-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="49ed6-122">**Verze**</span><span class="sxs-lookup"><span data-stu-id="49ed6-122">**Version**</span></span>|<span data-ttu-id="49ed6-123">Verze serveru.</span><span class="sxs-lookup"><span data-stu-id="49ed6-123">Version of the server.</span></span> <span data-ttu-id="49ed6-124">Například:</span><span class="sxs-lookup"><span data-stu-id="49ed6-124">For example:</span></span><br /><br /> <span data-ttu-id="49ed6-125">- 9.00.x (SQL Server 2005)</span><span class="sxs-lookup"><span data-stu-id="49ed6-125">-   9.00.x (SQL Server 2005)</span></span><br /><span data-ttu-id="49ed6-126">- 10.0.xx (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="49ed6-126">-   10.0.xx (SQL Server 2008)</span></span><br /><span data-ttu-id="49ed6-127">- 10.50.x (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="49ed6-127">-   10.50.x (SQL Server 2008 R2)</span></span><br /><span data-ttu-id="49ed6-128">- 11.0.xx (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="49ed6-128">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="49ed6-129">Omezení výčtu</span><span class="sxs-lookup"><span data-stu-id="49ed6-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="49ed6-130">Všechny dostupné servery mohou nebo nemusí být uvedeny.</span><span class="sxs-lookup"><span data-stu-id="49ed6-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="49ed6-131">Seznam se může lišit v závislosti na faktorech, jako jsou časové osy a síťový provoz.</span><span class="sxs-lookup"><span data-stu-id="49ed6-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="49ed6-132">To může způsobit, že seznam se liší na dvě po sobě jdoucí volání.</span><span class="sxs-lookup"><span data-stu-id="49ed6-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="49ed6-133">Budou uvedeny pouze servery ve stejné síti.</span><span class="sxs-lookup"><span data-stu-id="49ed6-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="49ed6-134">Všesměrové pakety obvykle nebudou procházet směrovači, což je důvod, proč se nemusí zobrazit uvedený server, ale bude stabilní napříč voláními.</span><span class="sxs-lookup"><span data-stu-id="49ed6-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="49ed6-135">Uvedené servery mohou nebo nemusí `IsClustered` mít další informace, jako je například a verze.</span><span class="sxs-lookup"><span data-stu-id="49ed6-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="49ed6-136">To závisí na způsobu získání seznamu.</span><span class="sxs-lookup"><span data-stu-id="49ed6-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="49ed6-137">Servery uvedené prostřednictvím služby prohlížeče SQL Server budou mít více podrobností než servery nalezené prostřednictvím infrastruktury systému Windows, která bude uvádět pouze název.</span><span class="sxs-lookup"><span data-stu-id="49ed6-137">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49ed6-138">Výčet serveru je k dispozici pouze při spuštění v plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="49ed6-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="49ed6-139">Sestavení spuštěná v částečně důvěryhodném prostředí jej nebudou moci používat, <xref:System.Data.SqlClient.SqlClientPermission> a to ani v případě, že mají oprávnění CAS (Code Access Security).</span><span class="sxs-lookup"><span data-stu-id="49ed6-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="49ed6-140">SQL Server poskytuje <xref:System.Data.Sql.SqlDataSourceEnumerator> informace pro použití externí služby Windows s názvem SQL Browser.</span><span class="sxs-lookup"><span data-stu-id="49ed6-140">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="49ed6-141">Tato služba je ve výchozím nastavení povolena, ale správci ji mohou vypnout nebo zakázat, čímž se instance serveru pro tuto třídu stane neviditelnou.</span><span class="sxs-lookup"><span data-stu-id="49ed6-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49ed6-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="49ed6-142">Example</span></span>  
 <span data-ttu-id="49ed6-143">Následující konzolová aplikace načte informace o všech viditelných instancích serveru SQL Server a zobrazí informace v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="49ed6-143">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="49ed6-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="49ed6-144">See also</span></span>

- [<span data-ttu-id="49ed6-145">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="49ed6-145">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="49ed6-146">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="49ed6-146">ADO.NET Overview</span></span>](../ado-net-overview.md)
