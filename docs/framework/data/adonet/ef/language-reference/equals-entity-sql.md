---
title: = (Je rovno) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: ec87ec682e1773c001c225567a35b3cedc9c5aba
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251002"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="9633b-102">= (Je rovno) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9633b-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="9633b-103">Porovná rovnost dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="9633b-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9633b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9633b-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="9633b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="9633b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="9633b-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="9633b-106">Any valid expression.</span></span> <span data-ttu-id="9633b-107">Oba výrazy musí mít implicitně převoditelné datové typy.</span><span class="sxs-lookup"><span data-stu-id="9633b-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9633b-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="9633b-108">Result Types</span></span>  
 <span data-ttu-id="9633b-109">`true`Pokud je levý výraz roven pravému výrazu; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="9633b-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9633b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9633b-110">Remarks</span></span>  
 <span data-ttu-id="9633b-111">Operátor = = je ekvivalentem =.</span><span class="sxs-lookup"><span data-stu-id="9633b-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9633b-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="9633b-112">Example</span></span>  
 <span data-ttu-id="9633b-113">Následující Entity SQL dotaz používá operátor porovnání k porovnání rovnosti dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="9633b-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="9633b-114">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="9633b-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9633b-115">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="9633b-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9633b-116">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="9633b-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9633b-117">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="9633b-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="9633b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9633b-118">See also</span></span>

- [<span data-ttu-id="9633b-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="9633b-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
