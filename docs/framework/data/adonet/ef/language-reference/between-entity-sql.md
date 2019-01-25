---
title: MEZI (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: cface8ab50e53f21293ad54ea6961c7e308080b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690689"
---
# <a name="between-entity-sql"></a><span data-ttu-id="b0a8f-102">MEZI (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b0a8f-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="b0a8f-103">Určuje, zda výraz výsledkem je hodnota v zadaném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="b0a8f-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Mezi výrazu má stejné funkce jako výraz jazyka Transact-SQL mezi.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0a8f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0a8f-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="b0a8f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="b0a8f-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b0a8f-107">Libovolný platný výraz pro testování v rozsahu definovaném touto `begin_expression` a `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="b0a8f-108">`expression` musí být stejného typu jako `begin_expression` a `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="b0a8f-109">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-109">Any valid expression.</span></span> <span data-ttu-id="b0a8f-110">`begin_expression` musí být stejného typu jako `expression` a `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="b0a8f-111">`begin_expression` by měla být menší než `end_expression`, jinak se bude negovat návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="b0a8f-112">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-112">Any valid expression.</span></span> <span data-ttu-id="b0a8f-113">`end_expression` musí být stejného typu jako `expression` a `begin_expression`.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="b0a8f-114">NOT</span><span class="sxs-lookup"><span data-stu-id="b0a8f-114">NOT</span></span>  
 <span data-ttu-id="b0a8f-115">Určuje, že bude výsledek BETWEEN negovat.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="b0a8f-116">AND</span><span class="sxs-lookup"><span data-stu-id="b0a8f-116">AND</span></span>  
 <span data-ttu-id="b0a8f-117">Slouží jako zástupný symbol, který označuje `expression` by měla spadat do rozsahu indikován `begin_expression` a `end_expression`.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0a8f-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b0a8f-118">Return Value</span></span>  
 <span data-ttu-id="b0a8f-119">`true` Pokud `expression` mezi rozsah indikovaný `begin_expression` a `end_expression`; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="b0a8f-120">`null` bude vrácen v případě `expression` je `null` nebo, pokud `begin_expression` nebo `end_expression` je `null`.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0a8f-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0a8f-121">Remarks</span></span>  
 <span data-ttu-id="b0a8f-122">Pokud chcete nastavit jako výhradní rozsah adres, použijte místo BETWEEN větší než (>) a menší než (<) operátory.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0a8f-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0a8f-123">Example</span></span>  
 <span data-ttu-id="b0a8f-124">Následující dotaz Entity SQL používá mezi operátor k určení, zda výraz výsledkem je hodnota v zadaném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="b0a8f-125">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b0a8f-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b0a8f-126">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="b0a8f-126">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b0a8f-127">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b0a8f-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="b0a8f-128">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="b0a8f-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="b0a8f-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0a8f-129">See also</span></span>
- [<span data-ttu-id="b0a8f-130">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b0a8f-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
