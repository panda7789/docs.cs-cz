---
title: '! = (Nerovná se) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: 3f6f66d38eb9650e1adb06fa3ef5edbccf110374
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319512"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="326c1-102">! = (Nerovná se) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="326c1-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="326c1-103">Porovná dva výrazy a určí, zda se levý výraz nerovná pravému výrazu.</span><span class="sxs-lookup"><span data-stu-id="326c1-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="326c1-104">Operátor! = (není rovno) je funkčně ekvivalentní k operátoru < >.</span><span class="sxs-lookup"><span data-stu-id="326c1-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="326c1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="326c1-105">Syntax</span></span>  
  
```sql  
expression != expression  
-- or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="326c1-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="326c1-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="326c1-107">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="326c1-107">Any valid expression.</span></span> <span data-ttu-id="326c1-108">Oba výrazy musí mít implicitně převoditelné datové typy.</span><span class="sxs-lookup"><span data-stu-id="326c1-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="326c1-109">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="326c1-109">Result Types</span></span>  
 <span data-ttu-id="326c1-110">`true`, pokud se levý výraz nerovná pravému výrazu; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="326c1-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="326c1-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="326c1-111">Example</span></span>  
 <span data-ttu-id="326c1-112">Následující Entity SQL dotaz pomocí operátoru! = Porovná dva výrazy a určí, zda se levý výraz nerovná pravému výrazu.</span><span class="sxs-lookup"><span data-stu-id="326c1-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="326c1-113">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="326c1-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="326c1-114">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="326c1-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="326c1-115">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="326c1-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="326c1-116">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="326c1-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NOT_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="326c1-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="326c1-117">See also</span></span>

- [<span data-ttu-id="326c1-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="326c1-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
