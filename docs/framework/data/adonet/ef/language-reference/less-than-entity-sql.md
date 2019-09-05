---
title: < (Méně než) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: c1d19c9017a4b789b40332e4eca522e9758dcdf2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250457"
---
# <a name="-less-than-entity-sql"></a><span data-ttu-id="caf7b-102">\<(Menší než) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="caf7b-102">\< (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="caf7b-103">Porovná dva výrazy a určí, zda má levý výraz hodnotu menší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="caf7b-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caf7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="caf7b-104">Syntax</span></span>  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="caf7b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="caf7b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="caf7b-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="caf7b-106">Any valid expression.</span></span> <span data-ttu-id="caf7b-107">Oba výrazy musí mít implicitně převoditelné datové typy.</span><span class="sxs-lookup"><span data-stu-id="caf7b-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="caf7b-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="caf7b-108">Result Types</span></span>  
 <span data-ttu-id="caf7b-109">`true`Pokud má levý výraz hodnotu menší než pravý výraz; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="caf7b-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="caf7b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="caf7b-110">Example</span></span>  
 <span data-ttu-id="caf7b-111">Následující Entity SQL dotaz pomocí operátoru porovnání < Porovná dva výrazy a určí, zda má levý výraz hodnotu menší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="caf7b-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="caf7b-112">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="caf7b-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="caf7b-113">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="caf7b-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="caf7b-114">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="caf7b-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="caf7b-115">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="caf7b-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="caf7b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="caf7b-116">See also</span></span>

- [<span data-ttu-id="caf7b-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="caf7b-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
