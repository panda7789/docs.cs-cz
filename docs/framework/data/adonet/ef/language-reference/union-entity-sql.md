---
title: "SJEDNOCENÍ (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b62d874a9885ed864282c765cf428f3c2a445745
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="union-entity-sql"></a><span data-ttu-id="56ba5-102">SJEDNOCENÍ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="56ba5-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="56ba5-103">Kombinuje výsledky dvou nebo více dotazů do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="56ba5-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56ba5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56ba5-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="56ba5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="56ba5-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="56ba5-106">Libovolný platný dotaz výraz, který vrátí kolekce kombinovat s kolekce všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="56ba5-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="56ba5-107">UNION</span><span class="sxs-lookup"><span data-stu-id="56ba5-107">UNION</span></span>  
 <span data-ttu-id="56ba5-108">Určuje, že více kolekcí jsou kombinaci a vrátí jako jedinou kolekci.</span><span class="sxs-lookup"><span data-stu-id="56ba5-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="56ba5-109">VŠECHNY</span><span class="sxs-lookup"><span data-stu-id="56ba5-109">ALL</span></span>  
 <span data-ttu-id="56ba5-110">Určuje, že více kolekcí jsou kombinaci a vrátí jako jedinou kolekci, včetně duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="56ba5-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="56ba5-111">Pokud není zadaný, duplicitní položky se odeberou z kolekce výsledek.</span><span class="sxs-lookup"><span data-stu-id="56ba5-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56ba5-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="56ba5-112">Return Value</span></span>  
 <span data-ttu-id="56ba5-113">Kolekce stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="56ba5-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56ba5-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56ba5-114">Remarks</span></span>  
 <span data-ttu-id="56ba5-115">SJEDNOCENÍ je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="56ba5-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="56ba5-116">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="56ba5-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="56ba5-117">Priorita informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavení operátory najdete [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="56ba5-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56ba5-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="56ba5-118">Example</span></span>  
 <span data-ttu-id="56ba5-119">Následující dotaz Entity SQL používá operátor UNION ALL kombinovat výsledky dva dotazy do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="56ba5-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="56ba5-120">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="56ba5-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="56ba5-121">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="56ba5-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="56ba5-122">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="56ba5-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="56ba5-123">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="56ba5-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="56ba5-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="56ba5-124">See Also</span></span>  
 [<span data-ttu-id="56ba5-125">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="56ba5-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
