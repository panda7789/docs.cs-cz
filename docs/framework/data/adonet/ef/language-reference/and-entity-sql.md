---
title: '&amp;&amp;(A) (Entita SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7d24213-471d-4807-b85e-570375df89b5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 098f9a09ba4fe114a3ad63f6d98efcd6bb090ac4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ampamp-and-entity-sql"></a><span data-ttu-id="b5d9f-102">&amp;&amp;(A) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="b5d9f-102">&amp;&amp; (AND) (Entity SQL)</span></span>
<span data-ttu-id="b5d9f-103">Vrátí `true` Pokud jsou oba výrazy `true`, jinak hodnota `false` nebo `NULL`.</span><span class="sxs-lookup"><span data-stu-id="b5d9f-103">Returns `true` if both expressions are `true`; otherwise, `false` or `NULL`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5d9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5d9f-104">Syntax</span></span>  
  
```  
boolean_expression AND boolean_expression  
or  
boolean_expression && boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="b5d9f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b5d9f-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="b5d9f-106">Jakýkoli platný výraz, který vrací logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b5d9f-106">Any valid expression that returns a Boolean.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5d9f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5d9f-107">Remarks</span></span>  
 <span data-ttu-id="b5d9f-108">Dvojité ampersandy (& &) mají stejnou funkci jako operátor AND.</span><span class="sxs-lookup"><span data-stu-id="b5d9f-108">Double ampersands (&&) have the same functionality as the AND operator.</span></span>  
  
 <span data-ttu-id="b5d9f-109">Následující tabulka uvádí možné vstupní hodnoty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="b5d9f-109">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="b5d9f-110">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="b5d9f-110">TRUE</span></span>|<span data-ttu-id="b5d9f-111">FALSE</span><span class="sxs-lookup"><span data-stu-id="b5d9f-111">FALSE</span></span>|<span data-ttu-id="b5d9f-112">NULL</span><span class="sxs-lookup"><span data-stu-id="b5d9f-112">NULL</span></span>|  
|`FALSE`|<span data-ttu-id="b5d9f-113">FALSE</span><span class="sxs-lookup"><span data-stu-id="b5d9f-113">FALSE</span></span>|<span data-ttu-id="b5d9f-114">FALSE</span><span class="sxs-lookup"><span data-stu-id="b5d9f-114">FALSE</span></span>|<span data-ttu-id="b5d9f-115">FALSE</span><span class="sxs-lookup"><span data-stu-id="b5d9f-115">FALSE</span></span>|  
|`NULL`|<span data-ttu-id="b5d9f-116">NULL</span><span class="sxs-lookup"><span data-stu-id="b5d9f-116">NULL</span></span>|<span data-ttu-id="b5d9f-117">FALSE</span><span class="sxs-lookup"><span data-stu-id="b5d9f-117">FALSE</span></span>|<span data-ttu-id="b5d9f-118">NULL</span><span class="sxs-lookup"><span data-stu-id="b5d9f-118">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b5d9f-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5d9f-119">Example</span></span>  
 <span data-ttu-id="b5d9f-120">Následující dotaz Entity SQL demonstruje použití operátoru AND.</span><span class="sxs-lookup"><span data-stu-id="b5d9f-120">The following Entity SQL query demonstrates how to use the AND operator.</span></span> <span data-ttu-id="b5d9f-121">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b5d9f-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b5d9f-122">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="b5d9f-122">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b5d9f-123">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b5d9f-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="b5d9f-124">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="b5d9f-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#AND](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#and)]  
  
## <a name="see-also"></a><span data-ttu-id="b5d9f-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5d9f-125">See Also</span></span>  
 [<span data-ttu-id="b5d9f-126">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="b5d9f-126">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
