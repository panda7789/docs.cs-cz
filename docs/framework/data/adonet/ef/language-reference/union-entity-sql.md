---
title: SJEDNOCENí (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: 34eac0dfd28d39ec68f084ea10dd46693f44eea3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248788"
---
# <a name="union-entity-sql"></a><span data-ttu-id="a51c9-102">SJEDNOCENí (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a51c9-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="a51c9-103">Kombinuje výsledky dvou nebo více dotazů do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="a51c9-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a51c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a51c9-104">Syntax</span></span>  
  
```  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a51c9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a51c9-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a51c9-106">Libovolný platný výraz dotazu, který vrací kolekci, která má být kombinována s kolekcí, všechny výrazy musí být stejného typu nebo typu společný základní nebo odvozený `expression`typ.</span><span class="sxs-lookup"><span data-stu-id="a51c9-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="a51c9-107">UNION</span><span class="sxs-lookup"><span data-stu-id="a51c9-107">UNION</span></span>  
 <span data-ttu-id="a51c9-108">Určuje, že vícenásobné kolekce se mají kombinovat a vracet jako jedna kolekce.</span><span class="sxs-lookup"><span data-stu-id="a51c9-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="a51c9-109">VŠEM</span><span class="sxs-lookup"><span data-stu-id="a51c9-109">ALL</span></span>  
 <span data-ttu-id="a51c9-110">Určuje, že vícenásobné kolekce se mají kombinovat a vracet jako jedna kolekce, včetně duplicitních hodnot.</span><span class="sxs-lookup"><span data-stu-id="a51c9-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="a51c9-111">Pokud není zadán, jsou duplicity z kolekce výsledků odebrány.</span><span class="sxs-lookup"><span data-stu-id="a51c9-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a51c9-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a51c9-112">Return Value</span></span>  
 <span data-ttu-id="a51c9-113">Kolekce stejného typu nebo společného základního nebo odvozeného typu jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="a51c9-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a51c9-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a51c9-114">Remarks</span></span>  
 <span data-ttu-id="a51c9-115">Union je jedním z [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinových operátorů.</span><span class="sxs-lookup"><span data-stu-id="a51c9-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="a51c9-116">Všechny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátory set jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="a51c9-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="a51c9-117">Informace o prioritách pro [!INCLUDE[esql](../../../../../../includes/esql-md.md)] množinové operátory naleznete v tématu [Except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="a51c9-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a51c9-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="a51c9-118">Example</span></span>  
 <span data-ttu-id="a51c9-119">Následující Entity SQL dotaz používá operátor UNION ALL ke kombinování výsledků dvou dotazů do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="a51c9-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="a51c9-120">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a51c9-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a51c9-121">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="a51c9-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a51c9-122">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="a51c9-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a51c9-123">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="a51c9-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#UNION](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#union)]  
  
## <a name="see-also"></a><span data-ttu-id="a51c9-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a51c9-124">See also</span></span>

- [<span data-ttu-id="a51c9-125">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a51c9-125">Entity SQL Reference</span></span>](entity-sql-reference.md)
