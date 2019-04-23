---
title: UNION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 736b92f7aac89c309b37a8ac61a295c8d1495d6b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59323288"
---
# <a name="union-entity-sql"></a><span data-ttu-id="90712-102">UNION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="90712-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="90712-103">Kombinuje výsledky ze dvou nebo více dotazů do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="90712-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90712-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90712-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="90712-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="90712-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="90712-106">Libovolný výraz platný dotaz, který vrátí kolekci zkombinovat s kolekcí všechny výrazy musí být stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="90712-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="90712-107">UNION</span><span class="sxs-lookup"><span data-stu-id="90712-107">UNION</span></span>  
 <span data-ttu-id="90712-108">Určuje, že mají více kolekcí kombinovat a vrátí jako jedinou kolekci.</span><span class="sxs-lookup"><span data-stu-id="90712-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="90712-109">VŠECHNY</span><span class="sxs-lookup"><span data-stu-id="90712-109">ALL</span></span>  
 <span data-ttu-id="90712-110">Určuje, že mají více kolekcí kombinovat a vrátí jako jedinou kolekci, včetně duplicitních.</span><span class="sxs-lookup"><span data-stu-id="90712-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="90712-111">Pokud není zadán, duplicity se odeberou z kolekce výsledek.</span><span class="sxs-lookup"><span data-stu-id="90712-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90712-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="90712-112">Return Value</span></span>  
 <span data-ttu-id="90712-113">Kolekce stejného typu nebo typu běžné základní nebo odvozené jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="90712-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90712-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90712-114">Remarks</span></span>  
 <span data-ttu-id="90712-115">SJEDNOCENÍ je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory.</span><span class="sxs-lookup"><span data-stu-id="90712-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="90712-116">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] sadu operátorů jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="90712-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="90712-117">Priorita informace pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nastavit operátory, naleznete v tématu [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="90712-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90712-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="90712-118">Example</span></span>  
 <span data-ttu-id="90712-119">Následující dotaz Entity SQL používá operátor UNION ALL ke kombinaci výsledků dvou dotazů do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="90712-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="90712-120">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="90712-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="90712-121">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="90712-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="90712-122">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="90712-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="90712-123">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="90712-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="90712-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90712-124">See also</span></span>

- [<span data-ttu-id="90712-125">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="90712-125">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
