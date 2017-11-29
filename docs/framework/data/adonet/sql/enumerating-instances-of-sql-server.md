---
title: "Vytváření výčtu instancí systému SQL Server (ADO.NET)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 99111cb9e48bd5ccd4463afcee6b78bc2387cf7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="e006b-102">Vytváření výčtu instancí systému SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e006b-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="e006b-103">umožňuje aplikacím najít [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instancí v rámci aktuální sítě.</span><span class="sxs-lookup"><span data-stu-id="e006b-103"> permits applications to find [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances within the current network.</span></span> <span data-ttu-id="e006b-104"><xref:System.Data.Sql.SqlDataSourceEnumerator> Třída zpřístupňuje tyto informace pro vývojáře aplikací, zajištění <xref:System.Data.DataTable> obsahující informace o všech viditelné serverech.</span><span class="sxs-lookup"><span data-stu-id="e006b-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="e006b-105">To vrácena tabulka obsahuje seznam instancí serverů, které jsou k dispozici v síti, která odpovídá seznamu zadat, když se uživatel pokusí o vytvoření nového připojení a rozbalí rozevírací seznam obsahující všechny dostupné servery na **připojení Vlastnosti** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e006b-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="e006b-106">Výsledky zobrazí vždy nebyly dokončeny.</span><span class="sxs-lookup"><span data-stu-id="e006b-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e006b-107">Jako s většina služeb systému Windows, je vhodné spustit službu SQL Browser s nejmenšími možnými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="e006b-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="e006b-108">V tématu [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] knihy Online pro další informace o služba SQL Browser a jak spravovat své chování.</span><span class="sxs-lookup"><span data-stu-id="e006b-108">See [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="e006b-109">Načítání Instance enumerátor</span><span class="sxs-lookup"><span data-stu-id="e006b-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="e006b-110">Chcete-li načíst tabulku obsahující informace o dostupných [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instancí, musíte nejprve získat enumerátor pomocí sdílených/statické <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> vlastnost:</span><span class="sxs-lookup"><span data-stu-id="e006b-110">In order to retrieve the table containing information about the available [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="e006b-111">Po načtení statická instance, můžete zavolat <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metoda, která vrátí hodnotu <xref:System.Data.DataTable> obsahující informace o dostupných serverů:</span><span class="sxs-lookup"><span data-stu-id="e006b-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="e006b-112">Tabulka vrácená z volání metody, které obsahuje následující sloupce, které obsahují `string` hodnoty:</span><span class="sxs-lookup"><span data-stu-id="e006b-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="e006b-113">Sloupec</span><span class="sxs-lookup"><span data-stu-id="e006b-113">Column</span></span>|<span data-ttu-id="e006b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e006b-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e006b-115">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="e006b-115">**ServerName**</span></span>|<span data-ttu-id="e006b-116">Název serveru.</span><span class="sxs-lookup"><span data-stu-id="e006b-116">Name of the server.</span></span>|  
|<span data-ttu-id="e006b-117">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="e006b-117">**InstanceName**</span></span>|<span data-ttu-id="e006b-118">Název instance serveru.</span><span class="sxs-lookup"><span data-stu-id="e006b-118">Name of the server instance.</span></span> <span data-ttu-id="e006b-119">Prázdná, pokud je server spuštěn jako výchozí instanci.</span><span class="sxs-lookup"><span data-stu-id="e006b-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="e006b-120">**IsClustered**</span><span class="sxs-lookup"><span data-stu-id="e006b-120">**IsClustered**</span></span>|<span data-ttu-id="e006b-121">Určuje, zda je server součástí clusteru.</span><span class="sxs-lookup"><span data-stu-id="e006b-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="e006b-122">**Verze**</span><span class="sxs-lookup"><span data-stu-id="e006b-122">**Version**</span></span>|<span data-ttu-id="e006b-123">Verze serveru.</span><span class="sxs-lookup"><span data-stu-id="e006b-123">Version of the server.</span></span> <span data-ttu-id="e006b-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e006b-124">For example:</span></span><br /><br /> <span data-ttu-id="e006b-125">-9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span><span class="sxs-lookup"><span data-stu-id="e006b-125">-   9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span></span><br /><span data-ttu-id="e006b-126">-10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span><span class="sxs-lookup"><span data-stu-id="e006b-126">-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span></span><br /><span data-ttu-id="e006b-127">-10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span><span class="sxs-lookup"><span data-stu-id="e006b-127">-   10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span></span><br /><span data-ttu-id="e006b-128">-11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012)</span><span class="sxs-lookup"><span data-stu-id="e006b-128">-   11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="e006b-129">Omezení – výčet</span><span class="sxs-lookup"><span data-stu-id="e006b-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="e006b-130">Všechny dostupné servery může nebo nemusí být uvedena.</span><span class="sxs-lookup"><span data-stu-id="e006b-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="e006b-131">Seznam se může lišit v závislosti na faktorech, jako je například časové limity a síťový provoz.</span><span class="sxs-lookup"><span data-stu-id="e006b-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="e006b-132">To může způsobit seznamu jiné na dvě po sobě jdoucí volání.</span><span class="sxs-lookup"><span data-stu-id="e006b-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="e006b-133">Objeví se pouze servery ve stejné síti.</span><span class="sxs-lookup"><span data-stu-id="e006b-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="e006b-134">Paketů všesměrového vysílání obvykle nebude přes směrovače, proto nemusíte vidět server uvedený, ale bude stabilní napříč volání.</span><span class="sxs-lookup"><span data-stu-id="e006b-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="e006b-135">Uvedené servery může nebo nemusí mít další informace, jako `IsClustered` a verze.</span><span class="sxs-lookup"><span data-stu-id="e006b-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="e006b-136">Toto je závisí na způsobu získání seznamu.</span><span class="sxs-lookup"><span data-stu-id="e006b-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="e006b-137">Servery uvedené prostřednictvím [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] prohlížeče služba bude mít další podrobnosti, než jsou prostřednictvím infrastrukturu nástroje systému Windows, která se zobrazí seznam pouze název.</span><span class="sxs-lookup"><span data-stu-id="e006b-137">Servers listed through the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e006b-138">Výčet serveru je k dispozici pouze při spuštění v plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="e006b-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="e006b-139">Sestavení v prostředí částečně důvěryhodné nebude možné použít, i když <xref:System.Data.SqlClient.SqlClientPermission> oprávnění zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="e006b-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="e006b-140">poskytuje informace o <xref:System.Data.Sql.SqlDataSourceEnumerator> prostřednictvím externí službu systému Windows s názvem SQL Browser.</span><span class="sxs-lookup"><span data-stu-id="e006b-140"> provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="e006b-141">Tato služba je ve výchozím nastavení povoleno, ale správci vypnout nebo ji zakázat, viditelnosti instance serveru pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="e006b-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e006b-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="e006b-142">Example</span></span>  
 <span data-ttu-id="e006b-143">Následující konzolové aplikace načte informace o všech viditelných [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instance a zobrazí informace v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="e006b-143">The following console application retrieves information about all of the visible [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances and displays the information in the console window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e006b-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="e006b-144">See Also</span></span>  
 [<span data-ttu-id="e006b-145">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e006b-145">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="e006b-146">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="e006b-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
