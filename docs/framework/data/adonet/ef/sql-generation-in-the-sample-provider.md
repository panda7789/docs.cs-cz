---
title: "Generování SQL ve zprostředkovateli ukázka"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7a7f95f7432fdac00a34e7d878ef979656a7af4e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="a79d7-102">Generování SQL ve zprostředkovateli ukázka</span><span class="sxs-lookup"><span data-stu-id="a79d7-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="a79d7-103">[Zprostředkovatele Entity Framework ukázka](http://go.microsoft.com/fwlink/?LinkId=180616) předvádí nové komponenty zprostředkovatele dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a79d7-103">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="a79d7-104">To funguje s databází systému SQL Server 2005 a je implementovaný jako obálku pro zprostředkovatele dat ADO.NET 2.0 System.Data.SqlClient.</span><span class="sxs-lookup"><span data-stu-id="a79d7-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="a79d7-105">Modul generování SQL ukázkového poskytovatele (umístěný ve složce generování SQL, s výjimkou souboru, DmlSqlGenerator.cs) trvá vstupní DbQueryCommandTree a vytvoří jeden příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="a79d7-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a79d7-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a79d7-106">In This Section</span></span>  
 <span data-ttu-id="a79d7-107">Tento oddíl obsahuje následující témata:</span><span class="sxs-lookup"><span data-stu-id="a79d7-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="a79d7-108">Architektura a návrh</span><span class="sxs-lookup"><span data-stu-id="a79d7-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="a79d7-109">Návod: Generování SQL</span><span class="sxs-lookup"><span data-stu-id="a79d7-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="a79d7-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a79d7-110">See Also</span></span>  
 [<span data-ttu-id="a79d7-111">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="a79d7-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
