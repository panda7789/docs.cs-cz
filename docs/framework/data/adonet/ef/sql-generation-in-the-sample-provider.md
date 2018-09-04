---
title: Generování SQL ve zprostředkovateli ukázek
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: cba1cec6d7ef0fdf8d4d4cf6c8e44fb325cf6447
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556202"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="eaef7-102">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="eaef7-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="eaef7-103">[Ukázka zprostředkovatele Entity Framework](https://go.microsoft.com/fwlink/?LinkId=180616) ukazuje nových komponent zprostředkovatele dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eaef7-103">The [Entity Framework Sample Provider](https://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="eaef7-104">Funguje s databází serveru SQL Server 2005 a je implementovaný jako obálka pro zprostředkovatele System.Data.SqlClient ADO.NET 2.0 Data.</span><span class="sxs-lookup"><span data-stu-id="eaef7-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="eaef7-105">Modul generování SQL zprostředkovateli ukázek (umístěný ve složce generování SQL, s výjimkou souboru DmlSqlGenerator.cs) přijímá vstupní DbQueryCommandTree a vytváří jeden příkaz SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="eaef7-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eaef7-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="eaef7-106">In This Section</span></span>  
 <span data-ttu-id="eaef7-107">Tento oddíl obsahuje následující témata:</span><span class="sxs-lookup"><span data-stu-id="eaef7-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="eaef7-108">Architektura a návrh</span><span class="sxs-lookup"><span data-stu-id="eaef7-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="eaef7-109">Návod: Generování SQL</span><span class="sxs-lookup"><span data-stu-id="eaef7-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="eaef7-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="eaef7-110">See Also</span></span>  
 [<span data-ttu-id="eaef7-111">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="eaef7-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
