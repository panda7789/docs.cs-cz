---
title: '- Odečten (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
ms.openlocfilehash: fe9152100bddac86f3fb7fae1ab3c0b81ae58418
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319332"
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="925b4-102">-(Odečíst) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="925b4-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="925b4-103">Odečte dvě čísla.</span><span class="sxs-lookup"><span data-stu-id="925b4-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="925b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="925b4-104">Syntax</span></span>  
  
```sql  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="925b4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="925b4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="925b4-106">Libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="925b4-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="925b4-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="925b4-107">Result Types</span></span>  
 <span data-ttu-id="925b4-108">Datový typ, který je výsledkem propagace implicitního typu obou argumentů.</span><span class="sxs-lookup"><span data-stu-id="925b4-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="925b4-109">Další informace o implicitním typu povýšení naleznete v tématu [Type System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="925b4-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="925b4-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="925b4-110">Example</span></span>  
 <span data-ttu-id="925b4-111">Následující Entity SQL dotaz pomocí operátoru-aritmetické operace odečtou dvě čísla.</span><span class="sxs-lookup"><span data-stu-id="925b4-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="925b4-112">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="925b4-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="925b4-113">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="925b4-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="925b4-114">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="925b4-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="925b4-115">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="925b4-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#SUBTRACT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="925b4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="925b4-116">See also</span></span>

- [<span data-ttu-id="925b4-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="925b4-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
