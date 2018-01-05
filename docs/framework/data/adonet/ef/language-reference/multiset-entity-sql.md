---
title: "MULTIMNOŽINA (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 2dff0e0ac2d9d0e705cdd6eedcf32f7919164b89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="multiset-entity-sql"></a><span data-ttu-id="3f6f2-102">MULTIMNOŽINA (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="3f6f2-102">MULTISET (Entity SQL)</span></span>
<span data-ttu-id="3f6f2-103">Vytvoří instanci multimnožina ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="3f6f2-103">Creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="3f6f2-104">Všechny hodnoty ve MULTISET konstruktor musí být kompatibilní typu `T`.</span><span class="sxs-lookup"><span data-stu-id="3f6f2-104">All the values in the MULTISET constructor must be of a compatible type `T`.</span></span> <span data-ttu-id="3f6f2-105">Prázdný multiset konstruktory nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="3f6f2-105">Empty multiset constructors are not allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f6f2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f6f2-106">Syntax</span></span>  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a><span data-ttu-id="3f6f2-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="3f6f2-107">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="3f6f2-108">Žádný platný seznam hodnot.</span><span class="sxs-lookup"><span data-stu-id="3f6f2-108">Any valid list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f6f2-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3f6f2-109">Return Value</span></span>  
 <span data-ttu-id="3f6f2-110">Kolekci typu MULTIMNOŽINA\<T >.</span><span class="sxs-lookup"><span data-stu-id="3f6f2-110">A collection of type MULTISET\<T>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f6f2-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f6f2-111">Remarks</span></span>  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="3f6f2-112">poskytuje tři druhy konstruktory: řádek konstruktory, objekt konstruktorů a konstruktorů multiset (nebo kolekce).</span><span class="sxs-lookup"><span data-stu-id="3f6f2-112"> provides three kinds of constructors: row constructors, object constructors, and multiset (or collection) constructors.</span></span> <span data-ttu-id="3f6f2-113">Další informace najdete v tématu [vytváření typů](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3f6f2-113">For more information, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
 <span data-ttu-id="3f6f2-114">Multimnožinové konstruktoru vytvoří instanci multimnožina ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="3f6f2-114">The multiset constructor creates an instance of a multiset from a list of values.</span></span> <span data-ttu-id="3f6f2-115">Všechny hodnoty v konstruktoru musí být kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="3f6f2-115">All the values in the constructor must be of a compatible type.</span></span>  
  
 <span data-ttu-id="3f6f2-116">Například následující výraz vytvoří multimnožina celých čísel.</span><span class="sxs-lookup"><span data-stu-id="3f6f2-116">For example, the following expression creates a multiset of integers.</span></span>  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
>  <span data-ttu-id="3f6f2-117">Vnořené multiset literály jsou podporována pouze v případě mutiset zabalení má jeden prvek multiset; například `{{1, 2, 3}}`.</span><span class="sxs-lookup"><span data-stu-id="3f6f2-117">Nested multiset literals are only supported when a wrapping mutiset has a single multiset element; for example, `{{1, 2, 3}}`.</span></span> <span data-ttu-id="3f6f2-118">Když multimnožina zabalení má více elementů multiset (například `{{1, 2}, {3, 4}}`), nejsou podporovány literály vnořené multiset.</span><span class="sxs-lookup"><span data-stu-id="3f6f2-118">When the wrapping multiset has multiple multiset elements (for example, `{{1, 2}, {3, 4}}`), nested multiset literals are not supported.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f6f2-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f6f2-119">Example</span></span>  
 <span data-ttu-id="3f6f2-120">Následující dotaz Entity SQL pomocí operátoru MULTIMNOŽINA vytvořit instanci multimnožina ze seznamu hodnot.</span><span class="sxs-lookup"><span data-stu-id="3f6f2-120">The following Entity SQL query uses the MULTISET operator to create an instance of a multiset from a list of values.</span></span> <span data-ttu-id="3f6f2-121">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3f6f2-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3f6f2-122">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="3f6f2-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3f6f2-123">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3f6f2-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="3f6f2-124">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="3f6f2-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a><span data-ttu-id="3f6f2-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f6f2-125">See Also</span></span>  
 [<span data-ttu-id="3f6f2-126">Vytváření typů</span><span class="sxs-lookup"><span data-stu-id="3f6f2-126">Constructing Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)  
 [<span data-ttu-id="3f6f2-127">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3f6f2-127">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
