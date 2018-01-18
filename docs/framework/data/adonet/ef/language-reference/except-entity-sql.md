---
title: "S výjimkou (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 546503d3fc51c863779c26f363721bf81be054b9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="except-entity-sql"></a><span data-ttu-id="ed510-102">S výjimkou (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="ed510-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="ed510-103">Vrátí kolekci všech jedinečných hodnot z výrazu dotazu nalevo od operand EXCEPT nejsou také vrácená z dotazu výrazu napravo od EXCEPT operand.</span><span class="sxs-lookup"><span data-stu-id="ed510-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="ed510-104">Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="ed510-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed510-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed510-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ed510-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="ed510-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ed510-107">Libovolný platný dotaz výraz, který vrátí kolekce k porovnání s kolekcí vrácená z jiného výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="ed510-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed510-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ed510-108">Return Value</span></span>  
 <span data-ttu-id="ed510-109">Kolekce stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="ed510-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed510-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed510-110">Remarks</span></span>  
 <span data-ttu-id="ed510-111">S výjimkou je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="ed510-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="ed510-112">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="ed510-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="ed510-113">V následující tabulce jsou uvedeny prioritu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="ed510-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="ed510-114">Priorita</span><span class="sxs-lookup"><span data-stu-id="ed510-114">Precedence</span></span>|<span data-ttu-id="ed510-115">Operátory</span><span class="sxs-lookup"><span data-stu-id="ed510-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="ed510-116">Nejvyšší</span><span class="sxs-lookup"><span data-stu-id="ed510-116">Highest</span></span>|<span data-ttu-id="ed510-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="ed510-117">INTERSECT</span></span>|  
||<span data-ttu-id="ed510-118">UNION</span><span class="sxs-lookup"><span data-stu-id="ed510-118">UNION</span></span><br /><br /> <span data-ttu-id="ed510-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="ed510-119">UNION ALL</span></span>|  
||<span data-ttu-id="ed510-120">S VÝJIMKOU</span><span class="sxs-lookup"><span data-stu-id="ed510-120">EXCEPT</span></span>|  
|<span data-ttu-id="ed510-121">Nejnižší</span><span class="sxs-lookup"><span data-stu-id="ed510-121">Lowest</span></span>|<span data-ttu-id="ed510-122">EXISTUJE</span><span class="sxs-lookup"><span data-stu-id="ed510-122">EXISTS</span></span><br /><br /> <span data-ttu-id="ed510-123">PŘEKRYTÍ.</span><span class="sxs-lookup"><span data-stu-id="ed510-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="ed510-124">VYROVNÁNÍ</span><span class="sxs-lookup"><span data-stu-id="ed510-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="ed510-125">NASTAVENÍ</span><span class="sxs-lookup"><span data-stu-id="ed510-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ed510-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed510-126">Example</span></span>  
 <span data-ttu-id="ed510-127">Následující dotaz Entity SQL pomocí operátoru EXCEPT vracet kolekci všech jedinečných hodnot ze dvou výrazů dotazu.</span><span class="sxs-lookup"><span data-stu-id="ed510-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="ed510-128">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ed510-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ed510-129">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="ed510-129">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ed510-130">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ed510-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ed510-131">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="ed510-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="ed510-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed510-132">See Also</span></span>  
 [<span data-ttu-id="ed510-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ed510-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
