---
title: '|| (NEBO) (Entita SQL)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b44934aa0db73f872f0ab27a4c36c5c615855de1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="-or-entity-sql"></a><span data-ttu-id="8bc88-102">|| (NEBO) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="8bc88-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="8bc88-103">Kombinuje dva `Boolean` výrazy.</span><span class="sxs-lookup"><span data-stu-id="8bc88-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bc88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bc88-104">Syntax</span></span>  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8bc88-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8bc88-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="8bc88-106">Jakýkoli platný výraz, který vrací `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="8bc88-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8bc88-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="8bc88-107">Return Value</span></span>  
 <span data-ttu-id="8bc88-108">`true`Pokud některá z podmínek je `true`, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="8bc88-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8bc88-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8bc88-109">Remarks</span></span>  
 <span data-ttu-id="8bc88-110">NEBO se [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logický operátor.</span><span class="sxs-lookup"><span data-stu-id="8bc88-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="8bc88-111">Umožňuje zkombinovat dvě podmínky.</span><span class="sxs-lookup"><span data-stu-id="8bc88-111">It is used to combine two conditions.</span></span> <span data-ttu-id="8bc88-112">Při více než jeden logický operátor je použít v příkazu, jsou vyhodnoceny nebo operátory a operátory.</span><span class="sxs-lookup"><span data-stu-id="8bc88-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="8bc88-113">Můžete však změnit pořadí vyhodnocování pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="8bc88-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="8bc88-114">Dvojité svislých pruhů (&#124; &#124;) mají stejnou funkci jako operátor OR.</span><span class="sxs-lookup"><span data-stu-id="8bc88-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="8bc88-115">Následující tabulka uvádí možné vstupní hodnoty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="8bc88-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="8bc88-116">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="8bc88-116">TRUE</span></span>|<span data-ttu-id="8bc88-117">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="8bc88-117">TRUE</span></span>|<span data-ttu-id="8bc88-118">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="8bc88-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="8bc88-119">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="8bc88-119">TRUE</span></span>|<span data-ttu-id="8bc88-120">FALSE</span><span class="sxs-lookup"><span data-stu-id="8bc88-120">FALSE</span></span>|<span data-ttu-id="8bc88-121">NULL</span><span class="sxs-lookup"><span data-stu-id="8bc88-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="8bc88-122">HODNOTA TRUE</span><span class="sxs-lookup"><span data-stu-id="8bc88-122">TRUE</span></span>|<span data-ttu-id="8bc88-123">NULL</span><span class="sxs-lookup"><span data-stu-id="8bc88-123">NULL</span></span>|<span data-ttu-id="8bc88-124">NULL</span><span class="sxs-lookup"><span data-stu-id="8bc88-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8bc88-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="8bc88-125">Example</span></span>  
 <span data-ttu-id="8bc88-126">Následující dotaz Entity SQL používá operátor OR kombinace obou `Boolean` výrazy.</span><span class="sxs-lookup"><span data-stu-id="8bc88-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="8bc88-127">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8bc88-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8bc88-128">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="8bc88-128">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8bc88-129">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8bc88-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="8bc88-130">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="8bc88-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a><span data-ttu-id="8bc88-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bc88-131">See Also</span></span>  
 [<span data-ttu-id="8bc88-132">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8bc88-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
