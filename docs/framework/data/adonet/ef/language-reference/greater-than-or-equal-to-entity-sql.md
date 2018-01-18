---
title: "&gt;= (Větší než nebo rovno) (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b176e1efdc17b58083234d0437033bd43775f604
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="gt-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="e6532-102">&gt;= (Větší než nebo rovno) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="e6532-102">&gt;= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="e6532-103">Porovná dva výrazy a určit, zda má levý výraz hodnotu větší než nebo rovna hodnotě pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="e6532-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6532-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6532-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="e6532-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e6532-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e6532-106">Jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="e6532-106">Any valid expression.</span></span> <span data-ttu-id="e6532-107">Oba výrazy musí mít implicitně převést datové typy.</span><span class="sxs-lookup"><span data-stu-id="e6532-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e6532-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="e6532-108">Result Types</span></span>  
 <span data-ttu-id="e6532-109">`true`Pokud levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="e6532-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6532-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6532-110">Example</span></span>  
 <span data-ttu-id="e6532-111">Následující dotaz Entity SQL používá > = – operátor porovnání k porovnání dvou výrazů k určení, zda levý výraz obsahuje hodnotu větší než nebo rovna hodnotě pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="e6532-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="e6532-112">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e6532-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e6532-113">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="e6532-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="e6532-114">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="e6532-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="e6532-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="e6532-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="e6532-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6532-116">See Also</span></span>  
 [<span data-ttu-id="e6532-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e6532-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
