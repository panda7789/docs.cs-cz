---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 9495e5daf88326c5a682172d835c3349fe79e571
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248751"
---
# <a name="using-entity-sql"></a><span data-ttu-id="71b2f-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="71b2f-102">USING (Entity SQL)</span></span>
<span data-ttu-id="71b2f-103">Určuje obory názvů použité ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="71b2f-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71b2f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71b2f-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="71b2f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="71b2f-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="71b2f-106">Určuje kratší alias pro získání oboru názvů pomocí.</span><span class="sxs-lookup"><span data-stu-id="71b2f-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="71b2f-107">Libovolný platný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="71b2f-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71b2f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="71b2f-108">Example</span></span>  
 <span data-ttu-id="71b2f-109">Následující Entity SQL dotaz pomocí operátoru USING určí obory názvů použité ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="71b2f-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="71b2f-110">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="71b2f-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="71b2f-111">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="71b2f-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="71b2f-112">Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="71b2f-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="71b2f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71b2f-113">See also</span></span>

- [<span data-ttu-id="71b2f-114">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="71b2f-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="71b2f-115">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="71b2f-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
