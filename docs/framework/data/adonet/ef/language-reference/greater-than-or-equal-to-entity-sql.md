---
title: '>= (Je větší než nebo rovno) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: fb97786687616ff92f0e4402c86aef02de2e70c9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250870"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="395b8-102">> = (je větší než nebo rovno) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="395b8-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="395b8-103">Porovná dva výrazy a určí, zda má levý výraz hodnotu větší nebo rovnu pravému výrazu.</span><span class="sxs-lookup"><span data-stu-id="395b8-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="395b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="395b8-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="395b8-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="395b8-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="395b8-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="395b8-106">Any valid expression.</span></span> <span data-ttu-id="395b8-107">Oba výrazy musí mít implicitně převoditelné datové typy.</span><span class="sxs-lookup"><span data-stu-id="395b8-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="395b8-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="395b8-108">Result Types</span></span>  
 <span data-ttu-id="395b8-109">`true`Pokud má levý výraz hodnotu větší než nebo rovna pravému výrazu; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="395b8-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="395b8-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="395b8-110">Example</span></span>  
 <span data-ttu-id="395b8-111">Následující Entity SQL dotaz pomocí operátoru > = Compare Porovná dva výrazy a určí, zda má levý výraz hodnotu větší nebo rovnu pravému výrazu.</span><span class="sxs-lookup"><span data-stu-id="395b8-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="395b8-112">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="395b8-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="395b8-113">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="395b8-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="395b8-114">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="395b8-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="395b8-115">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="395b8-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="395b8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="395b8-116">See also</span></span>

- [<span data-ttu-id="395b8-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="395b8-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
