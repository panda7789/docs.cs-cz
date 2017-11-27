---
title: "- (Dělení) (Entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0f215e12f9f86ee08679bdb2e2638c0c8df35ea4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="f3580-102">/ (Dělení) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="f3580-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="f3580-103">Vydělí jedno číslo jiným.</span><span class="sxs-lookup"><span data-stu-id="f3580-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3580-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3580-104">Syntax</span></span>  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="f3580-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f3580-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="f3580-106">Číselný výraz k rozdělení.</span><span class="sxs-lookup"><span data-stu-id="f3580-106">The numeric expression to divide.</span></span> <span data-ttu-id="f3580-107">`dividend`je jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="f3580-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="f3580-108">Číselný výraz k rozdělení dělenec podle.</span><span class="sxs-lookup"><span data-stu-id="f3580-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="f3580-109">`divisor`je jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="f3580-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f3580-110">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="f3580-110">Result Types</span></span>  
 <span data-ttu-id="f3580-111">Datový typ, který je výsledkem implicitní typ povýšením dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="f3580-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="f3580-112">Další informace o povýšení implicitní typ najdete v tématu [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f3580-112">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3580-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3580-113">Example</span></span>  
 <span data-ttu-id="f3580-114">Následující dotaz Entity SQL používá / aritmetické operátor rozdělit jeden kontrolních jiným.</span><span class="sxs-lookup"><span data-stu-id="f3580-114">The following Entity SQL query uses the / arithmetic operator to divide one numer by another.</span></span> <span data-ttu-id="f3580-115">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f3580-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f3580-116">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="f3580-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="f3580-117">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f3580-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="f3580-118">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="f3580-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="f3580-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3580-119">See Also</span></span>  
 [<span data-ttu-id="f3580-120">Odkaz na entitu SQL</span><span class="sxs-lookup"><span data-stu-id="f3580-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
