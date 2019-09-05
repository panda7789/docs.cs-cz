---
title: Existuje (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 20e18bf536f2b89eca9515b3c5dca7ca7fbd6fe5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250993"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="a635c-102">Existuje (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a635c-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="a635c-103">Určuje, zda je kolekce prázdná.</span><span class="sxs-lookup"><span data-stu-id="a635c-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a635c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a635c-104">Syntax</span></span>  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="a635c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a635c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a635c-106">Libovolný platný výraz, který vrací kolekci.</span><span class="sxs-lookup"><span data-stu-id="a635c-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="a635c-107">NOT</span><span class="sxs-lookup"><span data-stu-id="a635c-107">NOT</span></span>  
 <span data-ttu-id="a635c-108">Určuje, že výsledek EXISTS je negace.</span><span class="sxs-lookup"><span data-stu-id="a635c-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a635c-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a635c-109">Return Value</span></span>  
 <span data-ttu-id="a635c-110">`true`Pokud kolekce není prázdná; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="a635c-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a635c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a635c-111">Remarks</span></span>  
 <span data-ttu-id="a635c-112">Existuje jeden ze [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sad operátorů.</span><span class="sxs-lookup"><span data-stu-id="a635c-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="a635c-113">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="a635c-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="a635c-114">Informace o prioritách pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory naleznete v tématu [Except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a635c-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a635c-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="a635c-115">Example</span></span>  
 <span data-ttu-id="a635c-116">Následující Entity SQL dotaz používá operátor EXISTS k určení, zda je kolekce prázdná.</span><span class="sxs-lookup"><span data-stu-id="a635c-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="a635c-117">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a635c-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a635c-118">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="a635c-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a635c-119">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="a635c-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a635c-120">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="a635c-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="a635c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a635c-121">See also</span></span>

- [<span data-ttu-id="a635c-122">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a635c-122">Entity SQL Reference</span></span>](entity-sql-reference.md)
