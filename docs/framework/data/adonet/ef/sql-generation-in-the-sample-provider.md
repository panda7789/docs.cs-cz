---
title: Generování SQL ve zprostředkovateli ukázek
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: d0e058cdc4dd3f7a1a04ab6eea5acf4d3deabb89
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248510"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="b0dc4-102">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="b0dc4-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="b0dc4-103">[Poskytovatel ukázkového Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ukazuje nové komponenty zprostředkovatelů dat ADO.NET, které podporují [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b0dc4-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="b0dc4-104">Funguje s databází SQL Server 2005 a je implementována jako obálka pro System. data. SqlClient ADO.NET 2,0 Zprostředkovatel dat.</span><span class="sxs-lookup"><span data-stu-id="b0dc4-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="b0dc4-105">Modul pro generování SQL ukázkového poskytovatele (umístěný ve složce generování SQL, s výjimkou souboru DmlSqlGenerator.cs) přebírá vstupní DbQueryCommandTree a vytváří jeden příkaz SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="b0dc4-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0dc4-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b0dc4-106">In This Section</span></span>  
 <span data-ttu-id="b0dc4-107">Tento oddíl obsahuje následující témata:</span><span class="sxs-lookup"><span data-stu-id="b0dc4-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="b0dc4-108">Architektura a návrh</span><span class="sxs-lookup"><span data-stu-id="b0dc4-108">Architecture and Design</span></span>](architecture-and-design.md)  
  
 [<span data-ttu-id="b0dc4-109">Návod: Generování SQL</span><span class="sxs-lookup"><span data-stu-id="b0dc4-109">Walkthrough: SQL Generation</span></span>](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="b0dc4-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0dc4-110">See also</span></span>

- [<span data-ttu-id="b0dc4-111">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="b0dc4-111">SQL Generation</span></span>](sql-generation.md)
