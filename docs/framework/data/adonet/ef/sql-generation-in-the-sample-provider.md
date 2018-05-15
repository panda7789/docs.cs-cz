---
title: Generování SQL ve zprostředkovateli ukázka
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: 7275a67927d7692dc943e2555d65d1f7d6e4ba5a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="1b517-102">Generování SQL ve zprostředkovateli ukázka</span><span class="sxs-lookup"><span data-stu-id="1b517-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="1b517-103">[Zprostředkovatele Entity Framework ukázka](http://go.microsoft.com/fwlink/?LinkId=180616) předvádí nové komponenty zprostředkovatele dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1b517-103">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="1b517-104">To funguje s databází systému SQL Server 2005 a je implementovaný jako obálku pro zprostředkovatele dat ADO.NET 2.0 System.Data.SqlClient.</span><span class="sxs-lookup"><span data-stu-id="1b517-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="1b517-105">Modul generování SQL ukázkového poskytovatele (umístěný ve složce generování SQL, s výjimkou souboru, DmlSqlGenerator.cs) trvá vstupní DbQueryCommandTree a vytvoří jeden příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="1b517-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1b517-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1b517-106">In This Section</span></span>  
 <span data-ttu-id="1b517-107">Tento oddíl obsahuje následující témata:</span><span class="sxs-lookup"><span data-stu-id="1b517-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="1b517-108">Architektura a návrh</span><span class="sxs-lookup"><span data-stu-id="1b517-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="1b517-109">Návod: Generování SQL</span><span class="sxs-lookup"><span data-stu-id="1b517-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="1b517-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b517-110">See Also</span></span>  
 [<span data-ttu-id="1b517-111">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="1b517-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
