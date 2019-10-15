---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: 0bcd4a2140a04fa0ecbfa7eee450ed029f278286
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319209"
---
# <a name="using-entity-sql"></a><span data-ttu-id="af8cd-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="af8cd-102">USING (Entity SQL)</span></span>
<span data-ttu-id="af8cd-103">Určuje obory názvů použité ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="af8cd-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af8cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af8cd-104">Syntax</span></span>  
  
```sql  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="af8cd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="af8cd-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="af8cd-106">Určuje kratší alias pro získání oboru názvů pomocí.</span><span class="sxs-lookup"><span data-stu-id="af8cd-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="af8cd-107">Libovolný platný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="af8cd-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af8cd-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="af8cd-108">Example</span></span>  
 <span data-ttu-id="af8cd-109">Následující Entity SQL dotaz pomocí operátoru USING určí obory názvů použité ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="af8cd-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="af8cd-110">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="af8cd-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="af8cd-111">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="af8cd-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="af8cd-112">Předat následující dotaz jako argument metodě `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="af8cd-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```csharp
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="af8cd-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af8cd-113">See also</span></span>

- [<span data-ttu-id="af8cd-114">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="af8cd-114">Namespaces</span></span>](namespaces-entity-sql.md)
- [<span data-ttu-id="af8cd-115">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="af8cd-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
