---
title: SJEDNOCENÍ (entita SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 52a7a332166250e8fa8084986fd0d89da6fdf42d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="union-entity-sql"></a><span data-ttu-id="0e277-102">SJEDNOCENÍ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="0e277-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="0e277-103">Kombinuje výsledky dvou nebo více dotazů do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="0e277-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e277-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e277-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0e277-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0e277-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0e277-106">Libovolný platný dotaz výraz, který vrátí kolekce kombinovat s kolekce všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="0e277-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="0e277-107">UNION</span><span class="sxs-lookup"><span data-stu-id="0e277-107">UNION</span></span>  
 <span data-ttu-id="0e277-108">Určuje, že více kolekcí jsou kombinaci a vrátí jako jedinou kolekci.</span><span class="sxs-lookup"><span data-stu-id="0e277-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="0e277-109">VŠECHNY</span><span class="sxs-lookup"><span data-stu-id="0e277-109">ALL</span></span>  
 <span data-ttu-id="0e277-110">Určuje, že více kolekcí jsou kombinaci a vrátí jako jedinou kolekci, včetně duplicitní položky.</span><span class="sxs-lookup"><span data-stu-id="0e277-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="0e277-111">Pokud není zadaný, duplicitní položky se odeberou z kolekce výsledek.</span><span class="sxs-lookup"><span data-stu-id="0e277-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e277-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0e277-112">Return Value</span></span>  
 <span data-ttu-id="0e277-113">Kolekce stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="0e277-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e277-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e277-114">Remarks</span></span>  
 <span data-ttu-id="0e277-115">SJEDNOCENÍ je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory.</span><span class="sxs-lookup"><span data-stu-id="0e277-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="0e277-116">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="0e277-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="0e277-117">Priorita informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavení operátory najdete [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0e277-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e277-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="0e277-118">Example</span></span>  
 <span data-ttu-id="0e277-119">Následující dotaz Entity SQL používá operátor UNION ALL kombinovat výsledky dva dotazy do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="0e277-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="0e277-120">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0e277-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0e277-121">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="0e277-121">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="0e277-122">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0e277-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="0e277-123">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="0e277-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="0e277-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e277-124">See Also</span></span>  
 [<span data-ttu-id="0e277-125">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0e277-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
