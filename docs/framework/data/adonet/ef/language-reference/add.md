---
title: + (Přidat)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: f095703646d5280947e67a6640d49234a4da3622
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826743"
---
# <a name="-add"></a><span data-ttu-id="e58b3-102">+ (Add)</span><span class="sxs-lookup"><span data-stu-id="e58b3-102">+ (Add)</span></span>
<span data-ttu-id="e58b3-103">Sečte dvě čísla.</span><span class="sxs-lookup"><span data-stu-id="e58b3-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e58b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e58b3-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e58b3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e58b3-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e58b3-106">Libovolný platný výraz některou z číselných datových typů.</span><span class="sxs-lookup"><span data-stu-id="e58b3-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e58b3-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="e58b3-107">Result Types</span></span>  
 <span data-ttu-id="e58b3-108">Datový typ, který je výsledkem implicitních typů povýšení dvou argumentů.</span><span class="sxs-lookup"><span data-stu-id="e58b3-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="e58b3-109">Další informace o podpoře implicitních typů, najdete v části [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="e58b3-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e58b3-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e58b3-110">Remarks</span></span>  
 <span data-ttu-id="e58b3-111">Pro EDM. Typy řetězce, sčítání je zřetězení.</span><span class="sxs-lookup"><span data-stu-id="e58b3-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e58b3-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e58b3-112">Example</span></span>  
 <span data-ttu-id="e58b3-113">Následující dotaz Entity SQL používá + aritmetického operátoru pro přidání dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="e58b3-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="e58b3-114">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e58b3-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e58b3-115">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="e58b3-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e58b3-116">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e58b3-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="e58b3-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="e58b3-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="e58b3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e58b3-118">See also</span></span>
- [<span data-ttu-id="e58b3-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e58b3-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="e58b3-120">Typy konceptuálních modelů (CSDL)</span><span class="sxs-lookup"><span data-stu-id="e58b3-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
