---
title: EXISTUJE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
ms.openlocfilehash: 72d96c5f24fcedf870370de3792680831145a454
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034200"
---
# <a name="exists-entity-sql"></a><span data-ttu-id="1f5f4-102">EXISTUJE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1f5f4-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="1f5f4-103">Určuje, zda je kolekce prázdná.</span><span class="sxs-lookup"><span data-stu-id="1f5f4-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f5f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f5f4-104">Syntax</span></span>  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="1f5f4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1f5f4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1f5f4-106">Libovolný platný výraz, který vrátí kolekci.</span><span class="sxs-lookup"><span data-stu-id="1f5f4-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="1f5f4-107">NOT</span><span class="sxs-lookup"><span data-stu-id="1f5f4-107">NOT</span></span>  
 <span data-ttu-id="1f5f4-108">Určuje, že bude výsledek EXISTS negovat.</span><span class="sxs-lookup"><span data-stu-id="1f5f4-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f5f4-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1f5f4-109">Return Value</span></span>  
 <span data-ttu-id="1f5f4-110">`true` Pokud kolekce není prázdná. v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="1f5f4-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f5f4-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f5f4-111">Remarks</span></span>  
 <span data-ttu-id="1f5f4-112">EXISTS je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="1f5f4-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="1f5f4-113">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sadu operátorů jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="1f5f4-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="1f5f4-114">Priorita informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory, naleznete v tématu [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="1f5f4-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f5f4-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f5f4-115">Example</span></span>  
 <span data-ttu-id="1f5f4-116">Následující dotaz Entity SQL používá operátor EXISTS k určení, zda kolekce je prázdná.</span><span class="sxs-lookup"><span data-stu-id="1f5f4-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="1f5f4-117">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1f5f4-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1f5f4-118">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="1f5f4-118">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1f5f4-119">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="1f5f4-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1f5f4-120">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="1f5f4-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="1f5f4-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f5f4-121">See also</span></span>

- [<span data-ttu-id="1f5f4-122">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1f5f4-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
