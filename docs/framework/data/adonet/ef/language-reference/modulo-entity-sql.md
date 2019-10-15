---
title: Operace (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: 4bbdbe53403cfec2568cfac320fc7ab1ad2725b0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319600"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="73541-102">Operace (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="73541-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="73541-103">Vrátí zbytek jednoho výrazu děleného jiným.</span><span class="sxs-lookup"><span data-stu-id="73541-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73541-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73541-104">Syntax</span></span>  
  
```sql  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="73541-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="73541-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="73541-106">Číselný výraz, který se má rozdělit</span><span class="sxs-lookup"><span data-stu-id="73541-106">The numeric expression to divide.</span></span> <span data-ttu-id="73541-107">`dividend` je libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="73541-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="73541-108">Číselný výraz, podle kterého se má dělenec rozdělit.</span><span class="sxs-lookup"><span data-stu-id="73541-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="73541-109">`divisor` je libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="73541-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="73541-110">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="73541-110">Result Types</span></span>  
 <span data-ttu-id="73541-111">EDM. Int32</span><span class="sxs-lookup"><span data-stu-id="73541-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="73541-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="73541-112">Example</span></span>  
 <span data-ttu-id="73541-113">Následující Entity SQL dotaz pomocí aritmetického operátoru% vrátí zbytek jednoho výrazu děleného jiným.</span><span class="sxs-lookup"><span data-stu-id="73541-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="73541-114">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="73541-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="73541-115">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="73541-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="73541-116">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="73541-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="73541-117">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="73541-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MODULO](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="73541-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73541-118">See also</span></span>

- [<span data-ttu-id="73541-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="73541-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
