---
title: '- (Odečte) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: 2e4c08788ea57000e189c8371f0494641931184b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59316684"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="f11ae-102">-(Odečte) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f11ae-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="f11ae-103">Odečte dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="f11ae-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f11ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f11ae-104">Syntax</span></span>  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f11ae-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f11ae-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f11ae-106">Libovolný platný výraz některou z číselných datových typů.</span><span class="sxs-lookup"><span data-stu-id="f11ae-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f11ae-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="f11ae-107">Result Types</span></span>  
 <span data-ttu-id="f11ae-108">Datový typ, který je výsledkem implicitních typů povýšení dvou argumentů.</span><span class="sxs-lookup"><span data-stu-id="f11ae-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="f11ae-109">Další informace o podpoře implicitních typů, najdete v části [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f11ae-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f11ae-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f11ae-110">Example</span></span>  
 <span data-ttu-id="f11ae-111">Pomocí následujícího dotazu Entity SQL-aritmetický operátor má odečíst dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="f11ae-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="f11ae-112">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f11ae-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f11ae-113">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="f11ae-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f11ae-114">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f11ae-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f11ae-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="f11ae-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="f11ae-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f11ae-116">See also</span></span>

- [<span data-ttu-id="f11ae-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f11ae-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
