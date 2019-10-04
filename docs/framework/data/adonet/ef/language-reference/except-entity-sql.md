---
title: S VÝJIMKou (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: c4df8c2b72ee60a425c98c64a13a1e2d43d4506e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833859"
---
# <a name="except-entity-sql"></a><span data-ttu-id="95a86-102">S VÝJIMKou (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="95a86-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="95a86-103">Vrátí kolekci všech jedinečných hodnot z výrazu dotazu nalevo od operandu EXCEPT, který není také vrácen z výrazu dotazu napravo od operandu EXCEPT.</span><span class="sxs-lookup"><span data-stu-id="95a86-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="95a86-104">Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="95a86-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a86-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95a86-105">Syntax</span></span>  
  
```sql  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="95a86-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="95a86-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="95a86-107">Libovolný platný výraz dotazu, který vrátí kolekci pro porovnání s kolekcí vrácenou z jiného výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="95a86-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95a86-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="95a86-108">Return Value</span></span>  
 <span data-ttu-id="95a86-109">Kolekce stejného typu nebo společného základního nebo odvozeného typu jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="95a86-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95a86-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95a86-110">Remarks</span></span>  
 <span data-ttu-id="95a86-111">VÝJIMKou je jeden z operátorů množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95a86-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="95a86-112">Všechny operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="95a86-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="95a86-113">Následující tabulka ukazuje prioritu operátorů množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="95a86-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="95a86-114">Priorita</span><span class="sxs-lookup"><span data-stu-id="95a86-114">Precedence</span></span>|<span data-ttu-id="95a86-115">Operátory</span><span class="sxs-lookup"><span data-stu-id="95a86-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="95a86-116">Lineárně</span><span class="sxs-lookup"><span data-stu-id="95a86-116">Highest</span></span>|<span data-ttu-id="95a86-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="95a86-117">INTERSECT</span></span>|  
||<span data-ttu-id="95a86-118">UNION</span><span class="sxs-lookup"><span data-stu-id="95a86-118">UNION</span></span><br /><br /> <span data-ttu-id="95a86-119">SJEDNOTIT VŠE</span><span class="sxs-lookup"><span data-stu-id="95a86-119">UNION ALL</span></span>|  
||<span data-ttu-id="95a86-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="95a86-120">EXCEPT</span></span>|  
|<span data-ttu-id="95a86-121">Menší</span><span class="sxs-lookup"><span data-stu-id="95a86-121">Lowest</span></span>|<span data-ttu-id="95a86-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="95a86-122">EXISTS</span></span><br /><br /> <span data-ttu-id="95a86-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="95a86-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="95a86-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="95a86-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="95a86-125">SET</span><span class="sxs-lookup"><span data-stu-id="95a86-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="95a86-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="95a86-126">Example</span></span>  
 <span data-ttu-id="95a86-127">Následující Entity SQL dotaz používá operátor EXCEPT k vrácení kolekce libovolných různých hodnot ze dvou výrazů dotazu.</span><span class="sxs-lookup"><span data-stu-id="95a86-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="95a86-128">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="95a86-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="95a86-129">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="95a86-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="95a86-130">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="95a86-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="95a86-131">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="95a86-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#EXCEPT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#except)]  
  
## <a name="see-also"></a><span data-ttu-id="95a86-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="95a86-132">See also</span></span>

- [<span data-ttu-id="95a86-133">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="95a86-133">Entity SQL Reference</span></span>](entity-sql-reference.md)
