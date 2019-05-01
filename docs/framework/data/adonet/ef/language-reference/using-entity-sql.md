---
title: USING (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 20f58b8f-6070-4456-b7e8-5ff3d6269273
ms.openlocfilehash: e14b7857a65898683939647c872c48d0b3fe458a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034089"
---
# <a name="using-entity-sql"></a><span data-ttu-id="ce5a8-102">USING (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ce5a8-102">USING (Entity SQL)</span></span>
<span data-ttu-id="ce5a8-103">Určuje obor názvů použít ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-103">Specifies namespaces used in a query expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce5a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce5a8-104">Syntax</span></span>  
  
```  
USING [ alias = ] namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="ce5a8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ce5a8-105">Arguments</span></span>  
 `alias`  
 <span data-ttu-id="ce5a8-106">Určuje kratší alias k určení oboru názvů s.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-106">Specifies a shorter alias to qualify a namespace with.</span></span>  
  
 `namespace`  
 <span data-ttu-id="ce5a8-107">Libovolný platný obor názvů.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-107">Any valid namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce5a8-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce5a8-108">Example</span></span>  
 <span data-ttu-id="ce5a8-109">Následující dotaz Entity SQL používá operátor použití k zadávání oborů názvů použít ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="ce5a8-109">The following Entity SQL query uses the USING operator to specify namespaces used in a query expression.</span></span> <span data-ttu-id="ce5a8-110">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="ce5a8-110">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ce5a8-111">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ce5a8-111">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="ce5a8-112">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="ce5a8-112">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
```  
using SqlServer; RAND()  
```  
  
## <a name="see-also"></a><span data-ttu-id="ce5a8-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce5a8-113">See also</span></span>

- [<span data-ttu-id="ce5a8-114">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="ce5a8-114">Namespaces</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/namespaces-entity-sql.md)
- [<span data-ttu-id="ce5a8-115">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ce5a8-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
