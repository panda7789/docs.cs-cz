---
title: SQL Server a ADO.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ab519f7881dd20c3fd9e2e08fef14591477d94a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="19e22-102">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19e22-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="19e22-103">Tato část popisuje funkce a chování, které jsou specifické pro zprostředkovatele dat .NET Framework pro SQL Server (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="19e22-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="19e22-104"><xref:System.Data.SqlClient>poskytuje přístup k verzím systému SQL Server, který zapouzdřuje protokoly specifické pro databázi.</span><span class="sxs-lookup"><span data-stu-id="19e22-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="19e22-105">Funkce zprostředkovatele dat je navržený jako podobná zprostředkovatele dat .NET Framework pro OLE DB, rozhraní ODBC a Oracle.</span><span class="sxs-lookup"><span data-stu-id="19e22-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="19e22-106"><xref:System.Data.SqlClient>zahrnuje analyzátor tabular data stream (TDS) komunikovat přímo se serverem SQL Server.</span><span class="sxs-lookup"><span data-stu-id="19e22-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19e22-107">Použití zprostředkovatele dat .NET Framework pro SQL Server, aplikace musí odkazovat <xref:System.Data.SqlClient> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="19e22-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19e22-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="19e22-108">In This Section</span></span>  
 [<span data-ttu-id="19e22-109">Zabezpečení SQL serveru</span><span class="sxs-lookup"><span data-stu-id="19e22-109">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="19e22-110">Poskytuje přehled funkcí zabezpečení systému SQL Server a scénáře aplikací pro vytváření aplikací pro zabezpečené ADO.NET cílených systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="19e22-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="19e22-111">Data serveru SQL typy a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19e22-111">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 <span data-ttu-id="19e22-112">Popisuje, jak pracovat s datovými typy systému SQL Server a způsob, jakým interagují s datovými typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="19e22-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="19e22-113">Binární a velké hodnoty dat systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="19e22-113">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="19e22-114">Popisuje, jak pracovat s daty velké hodnoty v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="19e22-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="19e22-115">Operace dat serveru SQL v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19e22-115">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 <span data-ttu-id="19e22-116">Popisuje, jak pracovat s daty v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="19e22-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="19e22-117">Obsahuje oddíly o operace hromadného kopírování, MARS, asynchronních operací a parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="19e22-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="19e22-118">Funkce SQL serveru a technologie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19e22-118">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 <span data-ttu-id="19e22-119">Popisuje funkce serveru SQL, které jsou užitečné pro vývojáře aplikací ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="19e22-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="19e22-120">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="19e22-120">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="19e22-121">Popisuje základní stavební bloky, procesy a techniky, které jsou požadované pro tvorbu LINQ SQL aplikací.</span><span class="sxs-lookup"><span data-stu-id="19e22-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="19e22-122">Úplnou dokumentaci k databázového stroje SQL Server najdete v části SQL Server Books Online pro verzi systému SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="19e22-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="19e22-123">SQL Server Books Online</span><span class="sxs-lookup"><span data-stu-id="19e22-123">SQL Server Books Online</span></span>](http://msdn.microsoft.com/library/ms130214.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="19e22-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="19e22-124">See Also</span></span>  
 [<span data-ttu-id="19e22-125">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19e22-125">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="19e22-126">Mapování datového typu v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19e22-126">Data Type Mappings in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="19e22-127">Datové sady, DataTables a DataView</span><span class="sxs-lookup"><span data-stu-id="19e22-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="19e22-128">Načítání a upravovat Data v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19e22-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="19e22-129">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="19e22-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
