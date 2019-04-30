---
title: Generování SQL ve zprostředkovateli ukázek
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: 88223930b65ccec9d030104c62d8b4b2e77ddbe2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879291"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="6b164-102">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="6b164-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="6b164-103">[Ukázka zprostředkovatele Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ukazuje nových komponent zprostředkovatele dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b164-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="6b164-104">Funguje s databází serveru SQL Server 2005 a je implementovaný jako obálka pro zprostředkovatele System.Data.SqlClient ADO.NET 2.0 Data.</span><span class="sxs-lookup"><span data-stu-id="6b164-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="6b164-105">Modul generování SQL zprostředkovateli ukázek (umístěný ve složce generování SQL, s výjimkou souboru DmlSqlGenerator.cs) přijímá vstupní DbQueryCommandTree a vytváří jeden příkaz SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="6b164-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b164-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6b164-106">In This Section</span></span>  
 <span data-ttu-id="6b164-107">Tento oddíl obsahuje následující témata:</span><span class="sxs-lookup"><span data-stu-id="6b164-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="6b164-108">Architektura a návrh</span><span class="sxs-lookup"><span data-stu-id="6b164-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="6b164-109">Návod: Generování SQL</span><span class="sxs-lookup"><span data-stu-id="6b164-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="6b164-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b164-110">See also</span></span>

- [<span data-ttu-id="6b164-111">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="6b164-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
