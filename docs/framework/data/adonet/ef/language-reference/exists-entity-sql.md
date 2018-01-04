---
title: EXISTUJE (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d28ead43-4afb-4bdc-af64-efd2e05005d7
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0807be69419465a3d79f162e9738361a6ce8051a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="exists-entity-sql"></a><span data-ttu-id="908bd-102">EXISTUJE (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="908bd-102">EXISTS (Entity SQL)</span></span>
<span data-ttu-id="908bd-103">Určuje, zda kolekce je prázdný.</span><span class="sxs-lookup"><span data-stu-id="908bd-103">Determines if a collection is empty.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="908bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="908bd-104">Syntax</span></span>  
  
```  
[NOT] EXISTS ( expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="908bd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="908bd-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="908bd-106">Jakýkoli platný výraz, který vrátí kolekce.</span><span class="sxs-lookup"><span data-stu-id="908bd-106">Any valid expression that returns a collection.</span></span>  
  
 <span data-ttu-id="908bd-107">NENÍ</span><span class="sxs-lookup"><span data-stu-id="908bd-107">NOT</span></span>  
 <span data-ttu-id="908bd-108">Určuje, že se Negované výsledek EXISTS.</span><span class="sxs-lookup"><span data-stu-id="908bd-108">Specifies that the result of EXISTS be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="908bd-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="908bd-109">Return Value</span></span>  
 <span data-ttu-id="908bd-110">`true`Pokud kolekce není prázdná. v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="908bd-110">`true` if the collection is not empty; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="908bd-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="908bd-111">Remarks</span></span>  
 <span data-ttu-id="908bd-112">EXISTS je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="908bd-112">EXISTS is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="908bd-113">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="908bd-113">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="908bd-114">Priorita informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavení operátory najdete [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="908bd-114">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="908bd-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="908bd-115">Example</span></span>  
 <span data-ttu-id="908bd-116">Následující dotaz Entity SQL pomocí operátoru EXISTS určit, zda kolekce je prázdný.</span><span class="sxs-lookup"><span data-stu-id="908bd-116">The following Entity SQL query uses the EXISTS operator to determine whether the collection is empty.</span></span> <span data-ttu-id="908bd-117">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="908bd-117">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="908bd-118">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="908bd-118">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="908bd-119">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="908bd-119">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="908bd-120">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="908bd-120">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXISTS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#exists)]  
  
## <a name="see-also"></a><span data-ttu-id="908bd-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="908bd-121">See Also</span></span>  
 [<span data-ttu-id="908bd-122">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="908bd-122">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
