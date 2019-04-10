---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 32b5148e43a38e5cf8dcce0ae16260d7a6b6a018
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341215"
---
# <a name="except-entity-sql"></a><span data-ttu-id="59b82-102">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="59b82-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="59b82-103">Vrátí kolekci všech jedinečných hodnot z výrazu dotazu k levému operandu EXCEPT, která nejsou také vrácen z výrazu dotazu napravo od EXCEPT operand.</span><span class="sxs-lookup"><span data-stu-id="59b82-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="59b82-104">Všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="59b82-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59b82-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59b82-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="59b82-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="59b82-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="59b82-107">Libovolný výraz platný dotaz, který vrátí kolekce k porovnání s kolekci vrácené z jiného výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="59b82-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59b82-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="59b82-108">Return Value</span></span>  
 <span data-ttu-id="59b82-109">Kolekce stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="59b82-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59b82-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59b82-110">Remarks</span></span>  
 <span data-ttu-id="59b82-111">S výjimkou je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="59b82-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="59b82-112">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sadu operátorů jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="59b82-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="59b82-113">V následující tabulce jsou uvedeny prioritu [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="59b82-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="59b82-114">Priorita</span><span class="sxs-lookup"><span data-stu-id="59b82-114">Precedence</span></span>|<span data-ttu-id="59b82-115">Operátory</span><span class="sxs-lookup"><span data-stu-id="59b82-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="59b82-116">Nejvyšší</span><span class="sxs-lookup"><span data-stu-id="59b82-116">Highest</span></span>|<span data-ttu-id="59b82-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="59b82-117">INTERSECT</span></span>|  
||<span data-ttu-id="59b82-118">UNION</span><span class="sxs-lookup"><span data-stu-id="59b82-118">UNION</span></span><br /><br /> <span data-ttu-id="59b82-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="59b82-119">UNION ALL</span></span>|  
||<span data-ttu-id="59b82-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="59b82-120">EXCEPT</span></span>|  
|<span data-ttu-id="59b82-121">Nejnižší</span><span class="sxs-lookup"><span data-stu-id="59b82-121">Lowest</span></span>|<span data-ttu-id="59b82-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="59b82-122">EXISTS</span></span><br /><br /> <span data-ttu-id="59b82-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="59b82-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="59b82-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="59b82-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="59b82-125">SET</span><span class="sxs-lookup"><span data-stu-id="59b82-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="59b82-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="59b82-126">Example</span></span>  
 <span data-ttu-id="59b82-127">Následující dotaz SQL entit vrátí kolekci všech jedinečných hodnot ze dvou výrazů dotazů pomocí operátoru EXCEPT.</span><span class="sxs-lookup"><span data-stu-id="59b82-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="59b82-128">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="59b82-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="59b82-129">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="59b82-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="59b82-130">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="59b82-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="59b82-131">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="59b82-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="59b82-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59b82-132">See also</span></span>

- [<span data-ttu-id="59b82-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="59b82-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
