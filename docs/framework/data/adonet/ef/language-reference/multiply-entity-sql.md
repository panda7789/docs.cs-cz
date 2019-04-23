---
title: '* (Multiply) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 308df758d59a7e12a8b5a19ae72fcbee2f168490
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329723"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="f12ee-102">\* (Multiply) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f12ee-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="f12ee-103">Vynásobí dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="f12ee-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f12ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f12ee-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f12ee-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f12ee-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f12ee-106">Libovolný platný výraz některou z číselných datových typů.</span><span class="sxs-lookup"><span data-stu-id="f12ee-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f12ee-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="f12ee-107">Result Types</span></span>  
 <span data-ttu-id="f12ee-108">Datový typ, který je výsledkem implicitních typů povýšení dvou argumentů.</span><span class="sxs-lookup"><span data-stu-id="f12ee-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="f12ee-109">Další informace o podpoře implicitních typů, najdete v části [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f12ee-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f12ee-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f12ee-110">Example</span></span>  
 <span data-ttu-id="f12ee-111">Následující dotaz Entity SQL používá \* aritmetický operátor má vynásobit dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="f12ee-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="f12ee-112">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f12ee-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f12ee-113">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="f12ee-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f12ee-114">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f12ee-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f12ee-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="f12ee-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="f12ee-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f12ee-116">See also</span></span>

- [<span data-ttu-id="f12ee-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f12ee-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
