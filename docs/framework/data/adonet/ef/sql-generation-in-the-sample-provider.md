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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 58a49f7bf5d385466810a3c59bda748ef66d5840
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="cbea5-102">Generování SQL ve zprostředkovateli ukázka</span><span class="sxs-lookup"><span data-stu-id="cbea5-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="cbea5-103">[Zprostředkovatele Entity Framework ukázka](http://go.microsoft.com/fwlink/?LinkId=180616) předvádí nové komponenty zprostředkovatele dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbea5-103">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="cbea5-104">To funguje s databází systému SQL Server 2005 a je implementovaný jako obálku pro zprostředkovatele dat ADO.NET 2.0 System.Data.SqlClient.</span><span class="sxs-lookup"><span data-stu-id="cbea5-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="cbea5-105">Modul generování SQL ukázkového poskytovatele (umístěný ve složce generování SQL, s výjimkou souboru, DmlSqlGenerator.cs) trvá vstupní DbQueryCommandTree a vytvoří jeden příkazu SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="cbea5-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cbea5-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cbea5-106">In This Section</span></span>  
 <span data-ttu-id="cbea5-107">Tento oddíl obsahuje následující témata:</span><span class="sxs-lookup"><span data-stu-id="cbea5-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="cbea5-108">Architektura a návrh</span><span class="sxs-lookup"><span data-stu-id="cbea5-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="cbea5-109">Návod: Generování SQL</span><span class="sxs-lookup"><span data-stu-id="cbea5-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="cbea5-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="cbea5-110">See Also</span></span>  
 [<span data-ttu-id="cbea5-111">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="cbea5-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
