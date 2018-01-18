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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7b0a81fd9b92e626b52c5a74c65798ddedbd94a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="4e8dd-102">Vytváření výčtu instancí systému SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="4e8dd-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="4e8dd-103">umožňuje aplikacím najít [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instancí v rámci aktuální sítě.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-103"> permits applications to find [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances within the current network.</span></span> <span data-ttu-id="4e8dd-104"><xref:System.Data.Sql.SqlDataSourceEnumerator> Třída zpřístupňuje tyto informace pro vývojáře aplikací, zajištění <xref:System.Data.DataTable> obsahující informace o všech viditelné serverech.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="4e8dd-105">To vrácena tabulka obsahuje seznam instancí serverů, které jsou k dispozici v síti, která odpovídá seznamu zadat, když se uživatel pokusí o vytvoření nového připojení a rozbalí rozevírací seznam obsahující všechny dostupné servery na **připojení Vlastnosti** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="4e8dd-106">Výsledky zobrazí vždy nebyly dokončeny.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e8dd-107">Jako s většina služeb systému Windows, je vhodné spustit službu SQL Browser s nejmenšími možnými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="4e8dd-108">V tématu [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] knihy Online pro další informace o služba SQL Browser a jak spravovat své chování.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-108">See [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="4e8dd-109">Načítání Instance enumerátor</span><span class="sxs-lookup"><span data-stu-id="4e8dd-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="4e8dd-110">Chcete-li načíst tabulku obsahující informace o dostupných [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instancí, musíte nejprve získat enumerátor pomocí sdílených/statické <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> vlastnost:</span><span class="sxs-lookup"><span data-stu-id="4e8dd-110">In order to retrieve the table containing information about the available [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="4e8dd-111">Po načtení statická instance, můžete zavolat <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metoda, která vrátí hodnotu <xref:System.Data.DataTable> obsahující informace o dostupných serverů:</span><span class="sxs-lookup"><span data-stu-id="4e8dd-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="4e8dd-112">Tabulka vrácená z volání metody, které obsahuje následující sloupce, které obsahují `string` hodnoty:</span><span class="sxs-lookup"><span data-stu-id="4e8dd-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="4e8dd-113">Sloupec</span><span class="sxs-lookup"><span data-stu-id="4e8dd-113">Column</span></span>|<span data-ttu-id="4e8dd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4e8dd-114">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4e8dd-115">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="4e8dd-115">**ServerName**</span></span>|<span data-ttu-id="4e8dd-116">Název serveru.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-116">Name of the server.</span></span>|  
|<span data-ttu-id="4e8dd-117">**InstanceName**</span><span class="sxs-lookup"><span data-stu-id="4e8dd-117">**InstanceName**</span></span>|<span data-ttu-id="4e8dd-118">Název instance serveru.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-118">Name of the server instance.</span></span> <span data-ttu-id="4e8dd-119">Prázdná, pokud je server spuštěn jako výchozí instanci.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-119">Blank if the server is running as the default instance.</span></span>|  
|<span data-ttu-id="4e8dd-120">**IsClustered**</span><span class="sxs-lookup"><span data-stu-id="4e8dd-120">**IsClustered**</span></span>|<span data-ttu-id="4e8dd-121">Určuje, zda je server součástí clusteru.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-121">Indicates whether the server is part of a cluster.</span></span>|  
|<span data-ttu-id="4e8dd-122">**Verze**</span><span class="sxs-lookup"><span data-stu-id="4e8dd-122">**Version**</span></span>|<span data-ttu-id="4e8dd-123">Verze serveru.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-123">Version of the server.</span></span> <span data-ttu-id="4e8dd-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4e8dd-124">For example:</span></span><br /><br /> <span data-ttu-id="4e8dd-125">-9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span><span class="sxs-lookup"><span data-stu-id="4e8dd-125">-   9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span></span><br /><span data-ttu-id="4e8dd-126">-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span><span class="sxs-lookup"><span data-stu-id="4e8dd-126">-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span></span><br /><span data-ttu-id="4e8dd-127">-10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span><span class="sxs-lookup"><span data-stu-id="4e8dd-127">-   10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span></span><br /><span data-ttu-id="4e8dd-128">-   11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012)</span><span class="sxs-lookup"><span data-stu-id="4e8dd-128">-   11.0.xx ([!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="4e8dd-129">Omezení – výčet</span><span class="sxs-lookup"><span data-stu-id="4e8dd-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="4e8dd-130">Všechny dostupné servery může nebo nemusí být uvedena.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="4e8dd-131">Seznam se může lišit v závislosti na faktorech, jako je například časové limity a síťový provoz.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="4e8dd-132">To může způsobit seznamu jiné na dvě po sobě jdoucí volání.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="4e8dd-133">Objeví se pouze servery ve stejné síti.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="4e8dd-134">Paketů všesměrového vysílání obvykle nebude přes směrovače, proto nemusíte vidět server uvedený, ale bude stabilní napříč volání.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="4e8dd-135">Uvedené servery může nebo nemusí mít další informace, jako `IsClustered` a verze.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="4e8dd-136">Toto je závisí na způsobu získání seznamu.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="4e8dd-137">Servery uvedené prostřednictvím [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] prohlížeče služba bude mít další podrobnosti, než jsou prostřednictvím infrastrukturu nástroje systému Windows, která se zobrazí seznam pouze název.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-137">Servers listed through the [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e8dd-138">Výčet serveru je k dispozici pouze při spuštění v plné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="4e8dd-139">Sestavení v prostředí částečně důvěryhodné nebude možné použít, i když <xref:System.Data.SqlClient.SqlClientPermission> oprávnění zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="4e8dd-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="4e8dd-140">poskytuje informace o <xref:System.Data.Sql.SqlDataSourceEnumerator> prostřednictvím externí službu systému Windows s názvem SQL Browser.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-140"> provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="4e8dd-141">Tato služba je ve výchozím nastavení povoleno, ale správci vypnout nebo ji zakázat, viditelnosti instance serveru pro tuto třídu.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e8dd-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e8dd-142">Example</span></span>  
 <span data-ttu-id="4e8dd-143">Následující konzolové aplikace načte informace o všech viditelných [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instance a zobrazí informace v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="4e8dd-143">The following console application retrieves information about all of the visible [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instances and displays the information in the console window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e8dd-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e8dd-144">See Also</span></span>  
 [<span data-ttu-id="4e8dd-145">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4e8dd-145">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="4e8dd-146">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="4e8dd-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
