---
title: Generování SQL ve zprostředkovateli ukázek
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: a59f1fecf85d63208c3388204c962b5838902ba7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854314"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="98ee6-102">Generování SQL ve zprostředkovateli ukázek</span><span class="sxs-lookup"><span data-stu-id="98ee6-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="98ee6-103">[Poskytovatel ukázkového Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) ukazuje nové komponenty zprostředkovatelů dat ADO.NET, které podporují Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="98ee6-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the Entity Framework.</span></span>  <span data-ttu-id="98ee6-104">Funguje s databází SQL Server 2005 a je implementována jako obálka pro System. data. SqlClient ADO.NET 2,0 Zprostředkovatel dat.</span><span class="sxs-lookup"><span data-stu-id="98ee6-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="98ee6-105">Modul pro generování SQL ukázkového poskytovatele (umístěný ve složce generování SQL, s výjimkou souboru DmlSqlGenerator.cs) přebírá vstupní DbQueryCommandTree a vytváří jeden příkaz SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="98ee6-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="98ee6-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="98ee6-106">In This Section</span></span>  
 <span data-ttu-id="98ee6-107">Tento oddíl obsahuje následující témata:</span><span class="sxs-lookup"><span data-stu-id="98ee6-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="98ee6-108">Architektura a návrh</span><span class="sxs-lookup"><span data-stu-id="98ee6-108">Architecture and Design</span></span>](architecture-and-design.md)  
  
 [<span data-ttu-id="98ee6-109">Návod: Generování SQL</span><span class="sxs-lookup"><span data-stu-id="98ee6-109">Walkthrough: SQL Generation</span></span>](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="98ee6-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98ee6-110">See also</span></span>

- [<span data-ttu-id="98ee6-111">Generování SQL</span><span class="sxs-lookup"><span data-stu-id="98ee6-111">SQL Generation</span></span>](sql-generation.md)
