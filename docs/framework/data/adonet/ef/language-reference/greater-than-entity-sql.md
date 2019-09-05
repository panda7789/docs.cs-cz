---
title: '> (Je větší než) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: 0b57f36681575ccbe3239220e89804c804f13f39
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250889"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="5b798-102">> (Je větší než) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5b798-102">> (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="5b798-103">Porovná dva výrazy a určí, zda má levý výraz hodnotu větší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="5b798-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b798-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b798-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5b798-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5b798-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5b798-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="5b798-106">Any valid expression.</span></span> <span data-ttu-id="5b798-107">Oba výrazy musí mít implicitně převoditelné datové typy.</span><span class="sxs-lookup"><span data-stu-id="5b798-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5b798-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="5b798-108">Result Types</span></span>  
 <span data-ttu-id="5b798-109">`true`Pokud má levý výraz hodnotu větší než pravý výraz; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="5b798-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b798-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b798-110">Example</span></span>  
 <span data-ttu-id="5b798-111">Následující Entity SQL dotaz pomocí operátoru porovnání > Porovná dva výrazy a určí, zda má levý výraz hodnotu větší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="5b798-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="5b798-112">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5b798-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5b798-113">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="5b798-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5b798-114">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="5b798-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5b798-115">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="5b798-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="5b798-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b798-116">See also</span></span>

- [<span data-ttu-id="5b798-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5b798-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
