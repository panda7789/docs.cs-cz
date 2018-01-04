---
title: "= (Rovná) (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 948eb588-7080-4046-bb48-633b007393bf
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: c6b258bd06fd3e7e348e190b0897d66036006873
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="-equals-entity-sql"></a><span data-ttu-id="a9779-102">= (Rovná) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="a9779-102">= (Equals) (Entity SQL)</span></span>
<span data-ttu-id="a9779-103">Porovnání rovnosti dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="a9779-103">Compares the equality of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9779-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9779-104">Syntax</span></span>  
  
```  
expression = expression  
or   
expression == expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a9779-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a9779-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a9779-106">Jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="a9779-106">Any valid expression.</span></span> <span data-ttu-id="a9779-107">Oba výrazy musí mít implicitně převést datové typy.</span><span class="sxs-lookup"><span data-stu-id="a9779-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a9779-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="a9779-108">Result Types</span></span>  
 <span data-ttu-id="a9779-109">`true`Pokud levý výraz rovná pravý výraz; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="a9779-109">`true` if the left expression is equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9779-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9779-110">Remarks</span></span>  
 <span data-ttu-id="a9779-111">== Operátor je ekvivalentní =.</span><span class="sxs-lookup"><span data-stu-id="a9779-111">The == operator is equivalent to =.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9779-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9779-112">Example</span></span>  
 <span data-ttu-id="a9779-113">Následující dotaz Entity SQL používá = – operátor porovnání k porovnání rovnosti dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="a9779-113">The following Entity SQL query uses = comparison operator to compare the equality of two expressions.</span></span> <span data-ttu-id="a9779-114">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a9779-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a9779-115">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="a9779-115">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a9779-116">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a9779-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a9779-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="a9779-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#equals)]  
  
## <a name="see-also"></a><span data-ttu-id="a9779-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9779-118">See Also</span></span>  
 [<span data-ttu-id="a9779-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a9779-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
