---
title: + (Přidat)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: fcdee9388963553fef377a887d2e07161353f6c5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="-add"></a><span data-ttu-id="a4af6-102">+ (Přidat)</span><span class="sxs-lookup"><span data-stu-id="a4af6-102">+ (Add)</span></span>
<span data-ttu-id="a4af6-103">Sečte dvě čísla.</span><span class="sxs-lookup"><span data-stu-id="a4af6-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4af6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4af6-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a4af6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a4af6-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a4af6-106">Jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="a4af6-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a4af6-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="a4af6-107">Result Types</span></span>  
 <span data-ttu-id="a4af6-108">Datový typ, který je výsledkem implicitní typ povýšením dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="a4af6-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="a4af6-109">Další informace o povýšení implicitní typ najdete v tématu [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a4af6-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4af6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4af6-110">Remarks</span></span>  
 <span data-ttu-id="a4af6-111">Pro EDM. Typy řetězců, přidání je zřetězení.</span><span class="sxs-lookup"><span data-stu-id="a4af6-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4af6-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4af6-112">Example</span></span>  
 <span data-ttu-id="a4af6-113">Následující dotaz Entity SQL používá + aritmetického operátoru přidat dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="a4af6-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="a4af6-114">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a4af6-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a4af6-115">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="a4af6-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a4af6-116">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a4af6-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a4af6-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="a4af6-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="a4af6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4af6-118">See Also</span></span>  
 [<span data-ttu-id="a4af6-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a4af6-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="a4af6-120">Typy konceptuálního modelu (CSDL)</span><span class="sxs-lookup"><span data-stu-id="a4af6-120">Conceptual Model Types (CSDL)</span></span>](http://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
