---
title: SQL Server a ADO.NET
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: c58c6da7a6028c9167c73af820e922f59b528f15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938085"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="8a86c-102">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a86c-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="8a86c-103">Tato část popisuje funkce a chování, které jsou specifické pro .NET Framework Zprostředkovatel dat pro SQL Server (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="8a86c-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="8a86c-104"><xref:System.Data.SqlClient>poskytuje přístup k verzím SQL Server, které zapouzdřují protokoly pro konkrétní databáze.</span><span class="sxs-lookup"><span data-stu-id="8a86c-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="8a86c-105">Funkce poskytovatele dat je navržena tak, aby byla podobná poskytovateli .NET Framework dat pro OLE DB, ODBC a Oracle.</span><span class="sxs-lookup"><span data-stu-id="8a86c-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="8a86c-106"><xref:System.Data.SqlClient>zahrnuje analyzátor TDS (Tabular data Stream), který komunikuje přímo s SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8a86c-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a86c-107">Chcete-li použít Zprostředkovatel dat .NET Framework pro SQL Server, aplikace musí odkazovat na <xref:System.Data.SqlClient> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8a86c-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a86c-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8a86c-108">In This Section</span></span>  
 [<span data-ttu-id="8a86c-109">SQL Server – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8a86c-109">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="8a86c-110">Poskytuje přehled SQL Serverch funkcí zabezpečení a scénářů aplikací pro vytváření zabezpečených aplikací ADO.NET, které cílí na SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8a86c-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="8a86c-111">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a86c-111">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 <span data-ttu-id="8a86c-112">Popisuje, jak pracovat s datovými typy SQL Server a jak komunikují s datovými typy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8a86c-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="8a86c-113">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="8a86c-113">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="8a86c-114">Popisuje, jak pracovat s velkým množstvím dat v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8a86c-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="8a86c-115">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a86c-115">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 <span data-ttu-id="8a86c-116">Popisuje, jak pracovat s daty v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8a86c-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="8a86c-117">Obsahuje oddíly o operacích hromadného kopírování, MARS, asynchronních operací a parametrech s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="8a86c-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="8a86c-118">Funkce SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a86c-118">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 <span data-ttu-id="8a86c-119">Popisuje SQL Server funkce, které jsou užitečné pro vývojáře aplikací ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8a86c-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="8a86c-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8a86c-120">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="8a86c-121">V této části najdete popis základních stavebních bloků, procesů a technik potřebných pro vytváření aplikací LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="8a86c-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="8a86c-122">Úplnou dokumentaci k databázovému stroji SQL Server najdete v tématu SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="8a86c-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="8a86c-123">SQL Server Books Online</span><span class="sxs-lookup"><span data-stu-id="8a86c-123">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="8a86c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a86c-124">See also</span></span>

- [<span data-ttu-id="8a86c-125">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a86c-125">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="8a86c-126">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a86c-126">Data Type Mappings in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="8a86c-127">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="8a86c-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="8a86c-128">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a86c-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="8a86c-129">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="8a86c-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
