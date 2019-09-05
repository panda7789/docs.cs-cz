---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: d00fdeed01de80e441d28e2bcd5da084571b0361
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251035"
---
# <a name="except-entity-sql"></a><span data-ttu-id="1051c-102">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1051c-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="1051c-103">Vrátí kolekci všech jedinečných hodnot z výrazu dotazu nalevo od operandu EXCEPT, který není také vrácen z výrazu dotazu napravo od operandu EXCEPT.</span><span class="sxs-lookup"><span data-stu-id="1051c-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="1051c-104">Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="1051c-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1051c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1051c-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="1051c-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="1051c-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1051c-107">Libovolný platný výraz dotazu, který vrátí kolekci pro porovnání s kolekcí vrácenou z jiného výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="1051c-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1051c-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1051c-108">Return Value</span></span>  
 <span data-ttu-id="1051c-109">Kolekce stejného typu nebo společného základního nebo odvozeného typu jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="1051c-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1051c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1051c-110">Remarks</span></span>  
 <span data-ttu-id="1051c-111">Výjimkou je jeden z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinových operátorů.</span><span class="sxs-lookup"><span data-stu-id="1051c-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="1051c-112">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="1051c-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="1051c-113">V následující tabulce je uvedena priorita [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátorů set.</span><span class="sxs-lookup"><span data-stu-id="1051c-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="1051c-114">Priorita</span><span class="sxs-lookup"><span data-stu-id="1051c-114">Precedence</span></span>|<span data-ttu-id="1051c-115">Operátory</span><span class="sxs-lookup"><span data-stu-id="1051c-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="1051c-116">Lineárně</span><span class="sxs-lookup"><span data-stu-id="1051c-116">Highest</span></span>|<span data-ttu-id="1051c-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="1051c-117">INTERSECT</span></span>|  
||<span data-ttu-id="1051c-118">UNION</span><span class="sxs-lookup"><span data-stu-id="1051c-118">UNION</span></span><br /><br /> <span data-ttu-id="1051c-119">SJEDNOTIT VŠE</span><span class="sxs-lookup"><span data-stu-id="1051c-119">UNION ALL</span></span>|  
||<span data-ttu-id="1051c-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="1051c-120">EXCEPT</span></span>|  
|<span data-ttu-id="1051c-121">Menší</span><span class="sxs-lookup"><span data-stu-id="1051c-121">Lowest</span></span>|<span data-ttu-id="1051c-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="1051c-122">EXISTS</span></span><br /><br /> <span data-ttu-id="1051c-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="1051c-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="1051c-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="1051c-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="1051c-125">SET</span><span class="sxs-lookup"><span data-stu-id="1051c-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1051c-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="1051c-126">Example</span></span>  
 <span data-ttu-id="1051c-127">Následující Entity SQL dotaz používá operátor EXCEPT k vrácení kolekce libovolných různých hodnot ze dvou výrazů dotazu.</span><span class="sxs-lookup"><span data-stu-id="1051c-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="1051c-128">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1051c-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1051c-129">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="1051c-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1051c-130">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="1051c-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1051c-131">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="1051c-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="1051c-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1051c-132">See also</span></span>

- [<span data-ttu-id="1051c-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1051c-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
