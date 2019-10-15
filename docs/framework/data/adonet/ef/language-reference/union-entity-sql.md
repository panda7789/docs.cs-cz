---
title: SJEDNOCENí (Entity SQL)
ms.date: 03/30/2017
ms.assetid: df98a4db-b00d-4c8b-bd74-0d285f27e1df
ms.openlocfilehash: a5a20beb0ab55dcbaf2dbbb75801b50ab9ef6722
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319221"
---
# <a name="union-entity-sql"></a><span data-ttu-id="da905-102">SJEDNOCENí (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="da905-102">UNION (Entity SQL)</span></span>
<span data-ttu-id="da905-103">Kombinuje výsledky dvou nebo více dotazů do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="da905-103">Combines the results of two or more queries into a single collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da905-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da905-104">Syntax</span></span>  
  
```sql  
expression  
UNION [ ALL ]  
expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="da905-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="da905-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="da905-106">Libovolný platný výraz dotazu, který vrátí kolekci, která se má zkombinovat s kolekcí, musí být stejného typu nebo ze společného základního nebo odvozeného typu jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="da905-106">Any valid query expression that returns a collection to combine with the collection All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
 <span data-ttu-id="da905-107">UNION</span><span class="sxs-lookup"><span data-stu-id="da905-107">UNION</span></span>  
 <span data-ttu-id="da905-108">Určuje, že vícenásobné kolekce se mají kombinovat a vracet jako jedna kolekce.</span><span class="sxs-lookup"><span data-stu-id="da905-108">Specifies that multiple collections are to be combined and returned as a single collection.</span></span>  
  
 <span data-ttu-id="da905-109">VŠEM</span><span class="sxs-lookup"><span data-stu-id="da905-109">ALL</span></span>  
 <span data-ttu-id="da905-110">Určuje, že vícenásobné kolekce se mají kombinovat a vracet jako jedna kolekce, včetně duplicitních hodnot.</span><span class="sxs-lookup"><span data-stu-id="da905-110">Specifies that multiple collections are to be combined and returned as a single collection, including duplicates.</span></span> <span data-ttu-id="da905-111">Pokud není zadán, jsou duplicity z kolekce výsledků odebrány.</span><span class="sxs-lookup"><span data-stu-id="da905-111">If not specified, duplicates are removed from the result collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da905-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="da905-112">Return Value</span></span>  
 <span data-ttu-id="da905-113">Kolekce stejného typu nebo společného základního nebo odvozeného typu jako `expression`.</span><span class="sxs-lookup"><span data-stu-id="da905-113">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da905-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da905-114">Remarks</span></span>  
 <span data-ttu-id="da905-115">UNION je jednou z operátorů množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da905-115">UNION is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="da905-116">Všechny operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jsou vyhodnocovány zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="da905-116">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="da905-117">Informace o prioritách pro operátory množiny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] naleznete v tématu [Except](except-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="da905-117">For precedence information for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators, see [EXCEPT](except-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="da905-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="da905-118">Example</span></span>  
 <span data-ttu-id="da905-119">Následující Entity SQL dotaz používá operátor UNION ALL ke kombinování výsledků dvou dotazů do jedné kolekce.</span><span class="sxs-lookup"><span data-stu-id="da905-119">The following Entity SQL query uses the UNION ALL operator to combine the results of two queries into a single collection.</span></span> <span data-ttu-id="da905-120">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="da905-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="da905-121">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="da905-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="da905-122">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="da905-122">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="da905-123">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="da905-123">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#UNION](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#union)]  
  
## <a name="see-also"></a><span data-ttu-id="da905-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da905-124">See also</span></span>

- [<span data-ttu-id="da905-125">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="da905-125">Entity SQL Reference</span></span>](entity-sql-reference.md)
