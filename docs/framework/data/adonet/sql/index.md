---
title: SQL Server a ADO.NET
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: 32fc946f46ddac63d87b7e5a3d8f7120799f7223
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423075"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="915df-102">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="915df-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="915df-103">Tato část popisuje funkce a chování, které jsou specifické pro zprostředkovatele dat .NET Framework pro SQL Server (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="915df-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="915df-104"><xref:System.Data.SqlClient> poskytuje přístup k verzím systému SQL Server, který zapouzdřuje protokoly specifické pro databázi.</span><span class="sxs-lookup"><span data-stu-id="915df-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="915df-105">Funkce zprostředkovatel dat slouží k podobný zprostředkovatele dat .NET Framework pro OLE DB, ODBC a Oracle.</span><span class="sxs-lookup"><span data-stu-id="915df-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="915df-106"><xref:System.Data.SqlClient> zahrnuje analyzátor tabulková data služby stream (TDS) pro přímou komunikaci s SQL serverem.</span><span class="sxs-lookup"><span data-stu-id="915df-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="915df-107">Použití zprostředkovatele dat .NET Framework pro SQL Server, aplikace musí odkazovat <xref:System.Data.SqlClient> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="915df-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="915df-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="915df-108">In This Section</span></span>  
 [<span data-ttu-id="915df-109">SQL Server – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="915df-109">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="915df-110">Poskytuje přehled funkcí zabezpečení systému SQL Server a scénáře aplikací pro vytváření zabezpečených aplikací ADO.NET, které cílí na systém SQL Server.</span><span class="sxs-lookup"><span data-stu-id="915df-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="915df-111">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="915df-111">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 <span data-ttu-id="915df-112">Popisuje, jak pracovat s datovými typy SQL serveru a jejich vzájemné interakce s datovými typy rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="915df-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="915df-113">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="915df-113">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="915df-114">Popisuje, jak pracovat s daty velké hodnoty v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="915df-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="915df-115">Operace dat na SQL Serveru v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="915df-115">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 <span data-ttu-id="915df-116">Popisuje, jak pracovat s daty v systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="915df-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="915df-117">Obsahuje oddíly o operace hromadného kopírování, MARS, asynchronní operace a parametry s hodnotou tabulky.</span><span class="sxs-lookup"><span data-stu-id="915df-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="915df-118">Funkce SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="915df-118">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 <span data-ttu-id="915df-119">Popisuje funkce serveru SQL Server, které jsou užitečné pro vývojáře aplikací ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="915df-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="915df-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="915df-120">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="915df-121">Popisuje základní stavební bloky, procesy a postupy určené pro vytvoření LINQ na SQL aplikace.</span><span class="sxs-lookup"><span data-stu-id="915df-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="915df-122">Kompletní dokumentaci databázového stroje SQL serveru najdete v tématu knihy Online SQL Server pro verzi SQL serveru, který používáte.</span><span class="sxs-lookup"><span data-stu-id="915df-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="915df-123">SQL Server Books Online</span><span class="sxs-lookup"><span data-stu-id="915df-123">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="915df-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="915df-124">See Also</span></span>  
 [<span data-ttu-id="915df-125">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="915df-125">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="915df-126">Mapování datového typu v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="915df-126">Data Type Mappings in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="915df-127">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="915df-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="915df-128">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="915df-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="915df-129">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="915df-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
