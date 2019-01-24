---
title: Generování SQL ve zprostředkovateli ukázek
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: b2397570bb5f312aa6a3955a76234bde508fcc6a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505497"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="1e292-102">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="1e292-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="1e292-103">[Ukázka zprostředkovatele Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ukazuje nových komponent zprostředkovatele dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1e292-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="1e292-104">Funguje s databází serveru SQL Server 2005 a je implementovaný jako obálka pro zprostředkovatele System.Data.SqlClient ADO.NET 2.0 Data.</span><span class="sxs-lookup"><span data-stu-id="1e292-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="1e292-105">Modul generování SQL zprostředkovateli ukázek (umístěný ve složce generování SQL, s výjimkou souboru DmlSqlGenerator.cs) přijímá vstupní DbQueryCommandTree a vytváří jeden příkaz SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="1e292-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e292-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1e292-106">In This Section</span></span>  
 <span data-ttu-id="1e292-107">Tento oddíl obsahuje následující témata:</span><span class="sxs-lookup"><span data-stu-id="1e292-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="1e292-108">Architektura a návrh</span><span class="sxs-lookup"><span data-stu-id="1e292-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="1e292-109">Návod: Generování SQL</span><span class="sxs-lookup"><span data-stu-id="1e292-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="1e292-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e292-110">See also</span></span>
- [<span data-ttu-id="1e292-111">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="1e292-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
