---
title: '* (Násobení) (Entita SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: ecb0a55e403dddc5f7e69947035c8aa1fe7560ad
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32762543"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="73566-102">\* (Násobení) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="73566-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="73566-103">Vynásobí dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="73566-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73566-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73566-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="73566-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="73566-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="73566-106">Jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="73566-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="73566-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="73566-107">Result Types</span></span>  
 <span data-ttu-id="73566-108">Datový typ, který je výsledkem implicitní typ povýšením dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="73566-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="73566-109">Další informace o povýšení implicitní typ najdete v tématu [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="73566-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73566-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="73566-110">Example</span></span>  
 <span data-ttu-id="73566-111">Následující dotaz Entity SQL používá \* aritmetického operátoru mají vynásobit dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="73566-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="73566-112">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="73566-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="73566-113">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="73566-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="73566-114">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="73566-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="73566-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="73566-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="73566-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="73566-116">See Also</span></span>  
 [<span data-ttu-id="73566-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="73566-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
