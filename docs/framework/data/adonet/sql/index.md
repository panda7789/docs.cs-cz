---
title: SQL Server a ADO.NET
description: Přečtěte si o funkcích a chování .NET Framework Zprostředkovatel dat pro SQL Server, které zapouzdřují protokoly pro konkrétní databáze.
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: eeb0ab69a68dfc2fc0faa1b4e833f80b307fffe5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286440"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="90ea5-103">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90ea5-103">SQL Server and ADO.NET</span></span>
<span data-ttu-id="90ea5-104">Tato část popisuje funkce a chování, které jsou specifické pro .NET Framework Zprostředkovatel dat pro SQL Server ( <xref:System.Data.SqlClient> ).</span><span class="sxs-lookup"><span data-stu-id="90ea5-104">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="90ea5-105"><xref:System.Data.SqlClient>poskytuje přístup k verzím SQL Server, které zapouzdřují protokoly pro konkrétní databáze.</span><span class="sxs-lookup"><span data-stu-id="90ea5-105"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="90ea5-106">Funkce poskytovatele dat je navržena tak, aby byla podobná poskytovateli .NET Framework dat pro OLE DB, ODBC a Oracle.</span><span class="sxs-lookup"><span data-stu-id="90ea5-106">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="90ea5-107"><xref:System.Data.SqlClient>zahrnuje analyzátor TDS (Tabular data Stream), který komunikuje přímo s SQL Server.</span><span class="sxs-lookup"><span data-stu-id="90ea5-107"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90ea5-108">Chcete-li použít Zprostředkovatel dat .NET Framework pro SQL Server, aplikace musí odkazovat na <xref:System.Data.SqlClient> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="90ea5-108">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90ea5-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="90ea5-109">In This Section</span></span>  
 [<span data-ttu-id="90ea5-110">SQL Server – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="90ea5-110">SQL Server Security</span></span>](sql-server-security.md)  
 <span data-ttu-id="90ea5-111">Poskytuje přehled SQL Serverch funkcí zabezpečení a scénářů aplikací pro vytváření zabezpečených aplikací ADO.NET, které cílí na SQL Server.</span><span class="sxs-lookup"><span data-stu-id="90ea5-111">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="90ea5-112">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90ea5-112">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)  
 <span data-ttu-id="90ea5-113">Popisuje, jak pracovat s datovými typy SQL Server a jak komunikují s datovými typy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="90ea5-113">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="90ea5-114">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="90ea5-114">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="90ea5-115">Popisuje, jak pracovat s velkým množstvím dat v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="90ea5-115">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="90ea5-116">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90ea5-116">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)  
 <span data-ttu-id="90ea5-117">Popisuje, jak pracovat s daty v SQL Server.</span><span class="sxs-lookup"><span data-stu-id="90ea5-117">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="90ea5-118">Obsahuje oddíly o operacích hromadného kopírování, MARS, asynchronních operací a parametrech s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="90ea5-118">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="90ea5-119">Funkce SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90ea5-119">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)  
 <span data-ttu-id="90ea5-120">Popisuje SQL Server funkce, které jsou užitečné pro vývojáře aplikací ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="90ea5-120">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="90ea5-121">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="90ea5-121">LINQ to SQL</span></span>](./linq/index.md)  
 <span data-ttu-id="90ea5-122">V této části najdete popis základních stavebních bloků, procesů a technik potřebných pro vytváření aplikací LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="90ea5-122">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="90ea5-123">Úplnou dokumentaci k databázovému stroji SQL Server najdete v tématu SQL Server Knihy online pro verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="90ea5-123">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="90ea5-124">SQL Server Knihy online</span><span class="sxs-lookup"><span data-stu-id="90ea5-124">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="90ea5-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="90ea5-125">See also</span></span>

- [<span data-ttu-id="90ea5-126">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90ea5-126">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="90ea5-127">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90ea5-127">Data Type Mappings in ADO.NET</span></span>](../data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="90ea5-128">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="90ea5-128">DataSets, DataTables, and DataViews</span></span>](../dataset-datatable-dataview/index.md)
- [<span data-ttu-id="90ea5-129">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90ea5-129">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="90ea5-130">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="90ea5-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
