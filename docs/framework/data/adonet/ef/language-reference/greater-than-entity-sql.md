---
title: "&gt;(Větší než) (Entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 05673a8d24bccf798f654a73220411d41dba17d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="gt-greater-than-entity-sql"></a><span data-ttu-id="0faa7-102">&gt;(Větší než) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="0faa7-102">&gt; (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="0faa7-103">Porovná dva výrazy a určit, zda má levý výraz hodnotu větší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="0faa7-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0faa7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0faa7-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0faa7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0faa7-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="0faa7-106">Jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="0faa7-106">Any valid expression.</span></span> <span data-ttu-id="0faa7-107">Oba výrazy musí mít implicitně převést datové typy.</span><span class="sxs-lookup"><span data-stu-id="0faa7-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0faa7-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="0faa7-108">Result Types</span></span>  
 <span data-ttu-id="0faa7-109">`true`Pokud levý výraz obsahuje hodnotu větší než pravý výraz; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="0faa7-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0faa7-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="0faa7-110">Example</span></span>  
 <span data-ttu-id="0faa7-111">Následující dotaz Entity SQL používá > – operátor porovnání k porovnání dvou výrazů k určení, zda levý výraz obsahuje hodnotu větší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="0faa7-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="0faa7-112">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0faa7-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0faa7-113">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="0faa7-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="0faa7-114">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0faa7-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="0faa7-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="0faa7-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="0faa7-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0faa7-116">See Also</span></span>  
 [<span data-ttu-id="0faa7-117">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="0faa7-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
