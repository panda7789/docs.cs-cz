---
title: '! = (Nerovná se) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: f5fdbbf2892781ce44dfe73e8cd80fbe0f74cf1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760334"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="201c8-102">! = (Nerovná se) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="201c8-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="201c8-103">Porovná dva výrazy k určení, zda levý výraz není roven pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="201c8-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="201c8-104">! = – Operátor (není rovno) je funkčně srovnatelný s <> operátor.</span><span class="sxs-lookup"><span data-stu-id="201c8-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="201c8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="201c8-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="201c8-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="201c8-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="201c8-107">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="201c8-107">Any valid expression.</span></span> <span data-ttu-id="201c8-108">Implicitně převést datové typy musí mít oba výrazy.</span><span class="sxs-lookup"><span data-stu-id="201c8-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="201c8-109">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="201c8-109">Result Types</span></span>  
 <span data-ttu-id="201c8-110">`true` Pokud levý výraz není roven pravý výraz; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="201c8-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="201c8-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="201c8-111">Example</span></span>  
 <span data-ttu-id="201c8-112">Následující dotaz Entity SQL používá! = – operátor porovnání dvou výrazů k určení, zda levý výraz není roven pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="201c8-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="201c8-113">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="201c8-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="201c8-114">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="201c8-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="201c8-115">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="201c8-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="201c8-116">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="201c8-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="201c8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="201c8-117">See also</span></span>

- [<span data-ttu-id="201c8-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="201c8-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
