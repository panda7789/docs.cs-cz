---
title: "KLÍČ (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: aa18efd32998f881d49d7ebd71bad0cdf8122457
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="key-entity-sql"></a><span data-ttu-id="11a6e-102">KLÍČ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="11a6e-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="11a6e-103">Extrahuje klíč odkaz nebo výraz entity.</span><span class="sxs-lookup"><span data-stu-id="11a6e-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a6e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11a6e-104">Syntax</span></span>  
  
```  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="11a6e-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11a6e-105">Remarks</span></span>  
 <span data-ttu-id="11a6e-106">Klíč entity obsahuje hodnoty klíče ve správném pořadí zadané entity nebo odkaz na entitu.</span><span class="sxs-lookup"><span data-stu-id="11a6e-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="11a6e-107">Protože několik sad entit může být založen na stejného typu, může vypadat stejným klíčem v každé sadě entit.</span><span class="sxs-lookup"><span data-stu-id="11a6e-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="11a6e-108">Chcete-li získat jedinečný odkaz, použijte `REF`.</span><span class="sxs-lookup"><span data-stu-id="11a6e-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="11a6e-109">Návratový typ operátor klíč je typ řádek, který obsahuje jedno pole pro každý klíč entity, ve stejném pořadí.</span><span class="sxs-lookup"><span data-stu-id="11a6e-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="11a6e-110">V následujícím příkladu se klíče operátor je předán odkaz na entitu BadOrder a vrátí část klíče tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="11a6e-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="11a6e-111">V takovém případě s přesně jeden pole odpovídající typ záznamu `Id` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="11a6e-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )   
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="11a6e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="11a6e-112">Example</span></span>  
 <span data-ttu-id="11a6e-113">Následující dotaz Entity SQL pomocí operátoru klíč k extrakci část výraz obsahující odkaz na typ klíče.</span><span class="sxs-lookup"><span data-stu-id="11a6e-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="11a6e-114">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="11a6e-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="11a6e-115">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="11a6e-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="11a6e-116">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="11a6e-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="11a6e-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="11a6e-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#KEY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#key)]  
  
## <a name="see-also"></a><span data-ttu-id="11a6e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="11a6e-118">See Also</span></span>  
 [<span data-ttu-id="11a6e-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="11a6e-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="11a6e-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="11a6e-120">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
 [<span data-ttu-id="11a6e-121">REF</span><span class="sxs-lookup"><span data-stu-id="11a6e-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
 [<span data-ttu-id="11a6e-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="11a6e-122">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)
