---
title: SQL Server a ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: 6e88c35936de72f0d426c23493bbe5a08e707ee1
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979973"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="17189-102">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17189-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="17189-103">Tato část popisuje funkce a chování, které jsou specifické pro .NET Framework Zprostředkovatel dat pro SQL Server (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="17189-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="17189-104"><xref:System.Data.SqlClient> poskytuje přístup k verzím SQL Server, které zapouzdřují protokoly pro konkrétní databáze.</span><span class="sxs-lookup"><span data-stu-id="17189-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="17189-105">Funkce poskytovatele dat je navržena tak, aby byla podobná poskytovateli .NET Framework dat pro OLE DB, ODBC a Oracle.</span><span class="sxs-lookup"><span data-stu-id="17189-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="17189-106"><xref:System.Data.SqlClient> obsahuje analyzátor TDS (Tabular data Stream), který komunikuje přímo s SQL Server.</span><span class="sxs-lookup"><span data-stu-id="17189-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17189-107">Chcete-li použít Zprostředkovatel dat .NET Framework pro SQL Server, musí aplikace odkazovat na obor názvů <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="17189-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17189-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="17189-108">In This Section</span></span>  
 [<span data-ttu-id="17189-109">SQL Server – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="17189-109">SQL Server Security</span></span>](sql-server-security.md)  
 <span data-ttu-id="17189-110">Poskytuje přehled SQL Serverch funkcí zabezpečení a scénářů aplikací pro vytváření zabezpečených aplikací ADO.NET, které cílí na SQL Server.</span><span class="sxs-lookup"><span data-stu-id="17189-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="17189-111">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17189-111">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)  
 <span data-ttu-id="17189-112">Popisuje, jak pracovat s datovými typy SQL Server a jak komunikují s datovými typy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="17189-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="17189-113">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="17189-113">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="17189-114">Popisuje, jak pracovat s velkým množstvím dat v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="17189-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="17189-115">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17189-115">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)  
 <span data-ttu-id="17189-116">Popisuje, jak pracovat s daty v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="17189-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="17189-117">Obsahuje oddíly o operacích hromadného kopírování, MARS, asynchronních operací a parametrech s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="17189-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="17189-118">Funkce SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17189-118">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)  
 <span data-ttu-id="17189-119">Popisuje SQL Server funkce, které jsou užitečné pro vývojáře aplikací ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="17189-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="17189-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="17189-120">LINQ to SQL</span></span>](./linq/index.md)  
 <span data-ttu-id="17189-121">V této části najdete popis základních stavebních bloků, procesů a technik potřebných pro vytváření aplikací LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="17189-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="17189-122">Úplnou dokumentaci k databázovému stroji SQL Server najdete v tématu SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="17189-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="17189-123">SQL Server Books Online</span><span class="sxs-lookup"><span data-stu-id="17189-123">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="17189-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17189-124">See also</span></span>

- [<span data-ttu-id="17189-125">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17189-125">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="17189-126">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17189-126">Data Type Mappings in ADO.NET</span></span>](../data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="17189-127">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="17189-127">DataSets, DataTables, and DataViews</span></span>](../dataset-datatable-dataview/index.md)
- [<span data-ttu-id="17189-128">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17189-128">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="17189-129">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="17189-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
