---
title: SQL Server a ADO.NET
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: f30d9d715a2d94deee788f92cfc8eed0cba706de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172767"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="38d36-102">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="38d36-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="38d36-103">Tato část popisuje funkce a chování, které jsou specifické pro zprostředkovatele dat .NET Framework pro SQL Server (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="38d36-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <xref:System.Data.SqlClient> <span data-ttu-id="38d36-104">poskytuje přístup k verzím systému SQL Server, který zapouzdřuje protokoly specifické pro databázi.</span><span class="sxs-lookup"><span data-stu-id="38d36-104">provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="38d36-105">Funkce zprostředkovatel dat slouží k podobný zprostředkovatele dat .NET Framework pro OLE DB, ODBC a Oracle.</span><span class="sxs-lookup"><span data-stu-id="38d36-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <xref:System.Data.SqlClient> <span data-ttu-id="38d36-106">zahrnuje analyzátor tabulková data služby stream (TDS) pro přímou komunikaci s SQL serverem.</span><span class="sxs-lookup"><span data-stu-id="38d36-106">includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38d36-107">Použití zprostředkovatele dat .NET Framework pro SQL Server, aplikace musí odkazovat <xref:System.Data.SqlClient> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="38d36-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38d36-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="38d36-108">In This Section</span></span>  
 [<span data-ttu-id="38d36-109">SQL Server – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="38d36-109">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="38d36-110">Poskytuje přehled funkcí zabezpečení systému SQL Server a scénáře aplikací pro vytváření zabezpečených aplikací ADO.NET, které cílí na systém SQL Server.</span><span class="sxs-lookup"><span data-stu-id="38d36-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="38d36-111">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="38d36-111">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 <span data-ttu-id="38d36-112">Popisuje, jak pracovat s datovými typy SQL serveru a jejich vzájemné interakce s datovými typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="38d36-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="38d36-113">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="38d36-113">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="38d36-114">Popisuje, jak pracovat s daty velké hodnoty v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="38d36-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="38d36-115">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="38d36-115">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 <span data-ttu-id="38d36-116">Popisuje, jak pracovat s daty v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="38d36-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="38d36-117">Obsahuje oddíly o operace hromadného kopírování, MARS, asynchronní operace a parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="38d36-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="38d36-118">Funkce SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="38d36-118">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 <span data-ttu-id="38d36-119">Popisuje funkce serveru SQL Server, které jsou užitečné pro vývojáře aplikací ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="38d36-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="38d36-120">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="38d36-120">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="38d36-121">Popisuje základní stavební bloky, procesy a postupy určené pro vytvoření LINQ na SQL aplikace.</span><span class="sxs-lookup"><span data-stu-id="38d36-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="38d36-122">Kompletní dokumentaci databázového stroje SQL serveru najdete v tématu knihy Online SQL Server pro verzi SQL serveru, který používáte.</span><span class="sxs-lookup"><span data-stu-id="38d36-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="38d36-123">SQL Server Books Online</span><span class="sxs-lookup"><span data-stu-id="38d36-123">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="38d36-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38d36-124">See also</span></span>

- [<span data-ttu-id="38d36-125">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="38d36-125">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="38d36-126">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="38d36-126">Data Type Mappings in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="38d36-127">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="38d36-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="38d36-128">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="38d36-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="38d36-129">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="38d36-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
