---
title: = (Rovná se) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
ms.openlocfilehash: d50ede1964f6d6b9025a7214efe90e878aa55a0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333155"
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="fd8de-102">= (Rovná se) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="fd8de-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="fd8de-103">Porovná rovnost dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="fd8de-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd8de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd8de-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="fd8de-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fd8de-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fd8de-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="fd8de-106">Any valid expression.</span></span> <span data-ttu-id="fd8de-107">Implicitně převést datové typy musí mít oba výrazy.</span><span class="sxs-lookup"><span data-stu-id="fd8de-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fd8de-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="fd8de-108">Result Types</span></span>  
 <span data-ttu-id="fd8de-109">`true` Pokud levý výraz rovná pravý výraz; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="fd8de-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd8de-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd8de-110">Remarks</span></span>  
 <span data-ttu-id="fd8de-111">== – Operátor je ekvivalentní =.</span><span class="sxs-lookup"><span data-stu-id="fd8de-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd8de-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="fd8de-112">Example</span></span>  
 <span data-ttu-id="fd8de-113">Následující dotaz Entity SQL používá = – operátor porovnání k porovnání rovnosti dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="fd8de-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="fd8de-114">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="fd8de-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fd8de-115">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="fd8de-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="fd8de-116">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="fd8de-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="fd8de-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="fd8de-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="fd8de-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd8de-118">See also</span></span>

- [<span data-ttu-id="fd8de-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fd8de-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
