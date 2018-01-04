---
title: MEZI (entita SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 06008847a564d91d92a596978b90b040b6c508f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="between-entity-sql"></a><span data-ttu-id="bd9c6-102">MEZI (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="bd9c6-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="bd9c6-103">Určuje, zda výraz výsledkem hodnota v zadaném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="bd9c6-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Mezi výraz má stejné funkce jako výraz jazyka Transact-SQL mezi.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd9c6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd9c6-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="bd9c6-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="bd9c6-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="bd9c6-107">Jakýkoli platný výraz pro testování v rozsahu definovaného `begin_expression` a `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="bd9c6-108">`expression`musí být stejného typu, jak `begin_expression` a `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="bd9c6-109">Jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-109">Any valid expression.</span></span> <span data-ttu-id="bd9c6-110">`begin_expression`musí být stejného typu, jak `expression` a `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="bd9c6-111">`begin_expression`musí být menší než `end_expression`, jinak bude Negované návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="bd9c6-112">Jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-112">Any valid expression.</span></span> <span data-ttu-id="bd9c6-113">`end_expression`musí být stejného typu, jak `expression` a `begin_expression`.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="bd9c6-114">NENÍ</span><span class="sxs-lookup"><span data-stu-id="bd9c6-114">NOT</span></span>  
 <span data-ttu-id="bd9c6-115">Určuje, že se Negované výsledek BETWEEN.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="bd9c6-116">AND</span><span class="sxs-lookup"><span data-stu-id="bd9c6-116">AND</span></span>  
 <span data-ttu-id="bd9c6-117">Jako zástupný znak, který označuje `expression` by měla být v rozsahu indikován `begin_expression` a `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd9c6-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bd9c6-118">Return Value</span></span>  
 <span data-ttu-id="bd9c6-119">`true`Pokud `expression` mezi rozsah indikovaný `begin_expression` a `end_expression`, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="bd9c6-120">`null`bude vrácen v případě `expression` je `null` nebo, pokud `begin_expression` nebo `end_expression` je `null`.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd9c6-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd9c6-121">Remarks</span></span>  
 <span data-ttu-id="bd9c6-122">Pokud chcete zadat rozsah vylučují, použijte místo BETWEEN větší než (>) a menší než (<) operátory.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd9c6-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd9c6-123">Example</span></span>  
 <span data-ttu-id="bd9c6-124">Následující dotaz Entity SQL používá mezi operátor k určení, zda výraz výsledkem hodnota v zadaném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="bd9c6-125">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="bd9c6-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="bd9c6-126">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="bd9c6-126">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="bd9c6-127">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="bd9c6-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="bd9c6-128">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="bd9c6-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="bd9c6-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd9c6-129">See Also</span></span>  
 [<span data-ttu-id="bd9c6-130">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="bd9c6-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
