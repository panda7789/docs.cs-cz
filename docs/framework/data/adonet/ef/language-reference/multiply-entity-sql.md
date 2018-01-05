---
title: "* (Násobení) (Entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e2dca4be3d23d6cf9171eec960335ef57de1156c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="55aa5-102">* (Násobení) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="55aa5-102">* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="55aa5-103">Vynásobí dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="55aa5-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55aa5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55aa5-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="55aa5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="55aa5-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="55aa5-106">Jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="55aa5-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="55aa5-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="55aa5-107">Result Types</span></span>  
 <span data-ttu-id="55aa5-108">Datový typ, který je výsledkem implicitní typ povýšením dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="55aa5-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="55aa5-109">Další informace o povýšení implicitní typ najdete v tématu [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="55aa5-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55aa5-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="55aa5-110">Example</span></span>  
 <span data-ttu-id="55aa5-111">Následující dotaz Entity SQL používá * aritmetického operátoru mají vynásobit dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="55aa5-111">The following Entity SQL query uses the * arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="55aa5-112">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="55aa5-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="55aa5-113">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="55aa5-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="55aa5-114">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="55aa5-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="55aa5-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="55aa5-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="55aa5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="55aa5-116">See Also</span></span>  
 [<span data-ttu-id="55aa5-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="55aa5-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
