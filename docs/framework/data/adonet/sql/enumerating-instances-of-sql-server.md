---
title: Vytváření výčtu instancí SQL Serveru (ADO.NET)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ddf1c83c-9d40-45e6-b04d-9828c6cbbfdc
ms.openlocfilehash: a723679fe18352e115df78af72975097dc28b617
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162852"
---
# <a name="enumerating-instances-of-sql-server-adonet"></a><span data-ttu-id="8f3c8-102">Vytváření výčtu instancí SQL Serveru (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8f3c8-102">Enumerating Instances of SQL Server (ADO.NET)</span></span>
<span data-ttu-id="8f3c8-103">SQL Server povoluje aplikací, aby našel instance systému SQL Server v rámci aktuální sítě.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-103">SQL Server permits applications to find SQL Server instances within the current network.</span></span> <span data-ttu-id="8f3c8-104"><xref:System.Data.Sql.SqlDataSourceEnumerator> Třída zpřístupňuje tyto informace pro vývojáře aplikací, poskytování <xref:System.Data.DataTable> obsahující informace o všech serverech viditelné.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-104">The <xref:System.Data.Sql.SqlDataSourceEnumerator> class exposes this information to the application developer, providing a <xref:System.Data.DataTable> containing information about all the visible servers.</span></span> <span data-ttu-id="8f3c8-105">To vrácena tabulka obsahuje seznam instancí serveru, dostupný v síti, která odpovídá seznamu, pokud uživatel se pokusí vytvořit nové připojení a rozbalí rozevírací seznam obsahující všechny dostupné servery na **připojení Vlastnosti** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-105">This returned table contains a list of server instances available on the network that matches the list provided when a user attempts to create a new connection, and expands the drop-down list containing all the available servers on the **Connection Properties** dialog box.</span></span> <span data-ttu-id="8f3c8-106">Výsledky zobrazené nejsou vždy úplný.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-106">The results displayed are not always complete.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f3c8-107">Stejně jako u většiny služby Windows to je vhodné spustit službu SQL Browser s nejmenšími možnými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-107">As with most Windows services, it is best to run the SQL Browser service with the least possible privileges.</span></span> <span data-ttu-id="8f3c8-108">Další informace o službu SQL Browser a jak spravovat své chování naleznete v tématu knihy Online SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-108">See SQL Server Books Online for more information on the SQL Browser service, and how to manage its behavior.</span></span>  
  
## <a name="retrieving-an-enumerator-instance"></a><span data-ttu-id="8f3c8-109">Načítání Instance výčtu</span><span class="sxs-lookup"><span data-stu-id="8f3c8-109">Retrieving an Enumerator Instance</span></span>  
 <span data-ttu-id="8f3c8-110">Aby bylo možné načíst tabulku obsahující informace o dostupných instancí systému SQL Server, musíte nejdřív načíst enumerátor pomocí sdílených/statické <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> vlastnost:</span><span class="sxs-lookup"><span data-stu-id="8f3c8-110">In order to retrieve the table containing information about the available SQL Server instances, you must first retrieve an enumerator, using the shared/static <xref:System.Data.Sql.SqlDataSourceEnumerator.Instance%2A> property:</span></span>  
  
```vb  
Dim instance As System.Data.Sql.SqlDataSourceEnumerator = _  
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
```csharp  
System.Data.Sql.SqlDataSourceEnumerator instance =   
   System.Data.Sql.SqlDataSourceEnumerator.Instance  
```  
  
 <span data-ttu-id="8f3c8-111">Po načtení statická instance volejte <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> metoda, která vrátí <xref:System.Data.DataTable> obsahující informace o dostupných serverů:</span><span class="sxs-lookup"><span data-stu-id="8f3c8-111">Once you have retrieved the static instance, you can call the <xref:System.Data.Sql.SqlDataSourceEnumerator.GetDataSources%2A> method, which returns a <xref:System.Data.DataTable> containing information about the available servers:</span></span>  
  
```vb  
Dim dataTable As System.Data.DataTable = instance.GetDataSources()  
```  
  
```csharp  
System.Data.DataTable dataTable = instance.GetDataSources();  
```  
  
 <span data-ttu-id="8f3c8-112">Tabulka vrácená z volání metody, které obsahuje následující sloupce, které obsahují `string` hodnoty:</span><span class="sxs-lookup"><span data-stu-id="8f3c8-112">The table returned from the method call contains the following columns, all of which contain `string` values:</span></span>  
  
|<span data-ttu-id="8f3c8-113">Sloupec</span><span class="sxs-lookup"><span data-stu-id="8f3c8-113">Column</span></span>|<span data-ttu-id="8f3c8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8f3c8-114">Description</span></span>|  
|------------|-----------------|  
|**<span data-ttu-id="8f3c8-115">ServerName</span><span class="sxs-lookup"><span data-stu-id="8f3c8-115">ServerName</span></span>**|<span data-ttu-id="8f3c8-116">Název serveru.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-116">Name of the server.</span></span>|  
|**<span data-ttu-id="8f3c8-117">InstanceName</span><span class="sxs-lookup"><span data-stu-id="8f3c8-117">InstanceName</span></span>**|<span data-ttu-id="8f3c8-118">Název instance serveru.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-118">Name of the server instance.</span></span> <span data-ttu-id="8f3c8-119">Prázdné, pokud je server spuštěn jako výchozí instanci.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-119">Blank if the server is running as the default instance.</span></span>|  
|**<span data-ttu-id="8f3c8-120">IsClustered</span><span class="sxs-lookup"><span data-stu-id="8f3c8-120">IsClustered</span></span>**|<span data-ttu-id="8f3c8-121">Určuje, zda je server součástí clusteru.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-121">Indicates whether the server is part of a cluster.</span></span>|  
|**<span data-ttu-id="8f3c8-122">Version</span><span class="sxs-lookup"><span data-stu-id="8f3c8-122">Version</span></span>**|<span data-ttu-id="8f3c8-123">Verze serveru.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-123">Version of the server.</span></span> <span data-ttu-id="8f3c8-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8f3c8-124">For example:</span></span><br /><br /> <span data-ttu-id="8f3c8-125">-9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span><span class="sxs-lookup"><span data-stu-id="8f3c8-125">-   9.00.x ([!INCLUDE[ssVersion2005](../../../../../includes/ssversion2005-md.md)])</span></span><br /><span data-ttu-id="8f3c8-126">-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span><span class="sxs-lookup"><span data-stu-id="8f3c8-126">-   10.0.xx ([!INCLUDE[ssKatmai](../../../../../includes/sskatmai-md.md)])</span></span><br /><span data-ttu-id="8f3c8-127">-10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span><span class="sxs-lookup"><span data-stu-id="8f3c8-127">-   10.50.x ([!INCLUDE[ssKilimanjaro](../../../../../includes/sskilimanjaro-md.md)])</span></span><br /><span data-ttu-id="8f3c8-128">-   11.0.xx (SQL Server 2012)</span><span class="sxs-lookup"><span data-stu-id="8f3c8-128">-   11.0.xx (SQL Server 2012)</span></span>|  
  
## <a name="enumeration-limitations"></a><span data-ttu-id="8f3c8-129">Výčet omezení</span><span class="sxs-lookup"><span data-stu-id="8f3c8-129">Enumeration Limitations</span></span>  
 <span data-ttu-id="8f3c8-130">Všechny dostupné servery může nebo nemusí být uvedená.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-130">All of the available servers may or may not be listed.</span></span> <span data-ttu-id="8f3c8-131">Seznam se může lišit v závislosti na faktorech, třeba vypršení časových limitů a síťové přenosy.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-131">The list can vary depending on factors such as timeouts and network traffic.</span></span> <span data-ttu-id="8f3c8-132">To může způsobit seznamem, aby se na dvě po sobě jdoucích volání lišit.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-132">This can cause the list to be different on two consecutive calls.</span></span> <span data-ttu-id="8f3c8-133">Zobrazí se pouze servery ve stejné síti.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-133">Only servers on the same network will be listed.</span></span> <span data-ttu-id="8f3c8-134">Pakety všesměrového vysílání obvykle nebudete procházet směrovače, proto nemusíte vidět serveru uvedené, ale bude stabilní napříč volání.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-134">Broadcast packets typically won't traverse routers, which is why you may not see a server listed, but it will be stable across calls.</span></span>  
  
 <span data-ttu-id="8f3c8-135">Uvedené servery může nebo nemusí mít další informace, jako `IsClustered` a verze.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-135">Listed servers may or may not have additional information such as `IsClustered` and version.</span></span> <span data-ttu-id="8f3c8-136">To závisí na způsobu získání seznamu.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-136">This is dependent on how the list was obtained.</span></span> <span data-ttu-id="8f3c8-137">Servery uvedené přes službu systému SQL Server browser budou mít informace než přes infrastrukturu Windows, který zobrazí seznam pouze název.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-137">Servers listed through the SQL Server browser service will have more details than those found through the Windows infrastructure, which will list only the name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f3c8-138">Výčet server je dostupná jenom při spouštění v režimu úplné důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-138">Server enumeration is only available when running in full-trust.</span></span> <span data-ttu-id="8f3c8-139">Spuštění v prostředí částečně důvěryhodných sestavení nebudou moct používat, i v případě, že mají <xref:System.Data.SqlClient.SqlClientPermission> oprávnění zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="8f3c8-139">Assemblies running in a partially-trusted environment will not be able to use it, even if they have the <xref:System.Data.SqlClient.SqlClientPermission> Code Access Security (CAS) permission.</span></span>  
  
 <span data-ttu-id="8f3c8-140">Obsahuje informace o systému SQL Server <xref:System.Data.Sql.SqlDataSourceEnumerator> prostřednictvím externí služby Windows s názvem SQL Browser.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-140">SQL Server provides information for the <xref:System.Data.Sql.SqlDataSourceEnumerator> through the use of an external Windows service named SQL Browser.</span></span> <span data-ttu-id="8f3c8-141">Tato služba je ve výchozím nastavení povoleno, ale správci vypnout nebo zakázat, neviditelný instance serveru k této třídě.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-141">This service is enabled by default, but administrators may turn it off or disable it, making the server instance invisible to this class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f3c8-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f3c8-142">Example</span></span>  
 <span data-ttu-id="8f3c8-143">Následující konzolové aplikace načte informace o všech viditelných instancí systému SQL Server a zobrazí informace v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="8f3c8-143">The following console application retrieves information about all of the visible SQL Server instances and displays the information in the console window.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8f3c8-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8f3c8-144">See also</span></span>

- [<span data-ttu-id="8f3c8-145">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8f3c8-145">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="8f3c8-146">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="8f3c8-146">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
