---
title: "- (Odečtena) (Entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc4327f9-09c0-438f-a008-927c5c478040
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5ca2bc8cb34d99421962289930c26de84eaa68e2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="--subtract-entity-sql"></a><span data-ttu-id="94d46-102">-(Odečtena) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="94d46-102">- (Subtract) (Entity SQL)</span></span>
<span data-ttu-id="94d46-103">Odečítá od dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="94d46-103">Subtracts two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d46-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94d46-104">Syntax</span></span>  
  
```  
expression - expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="94d46-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="94d46-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="94d46-106">Jakýkoli platný výraz některého číselné datové typy.</span><span class="sxs-lookup"><span data-stu-id="94d46-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="94d46-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="94d46-107">Result Types</span></span>  
 <span data-ttu-id="94d46-108">Datový typ, který je výsledkem implicitní typ povýšením dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="94d46-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="94d46-109">Další informace o povýšení implicitní typ najdete v tématu [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="94d46-109">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94d46-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="94d46-110">Example</span></span>  
 <span data-ttu-id="94d46-111">Pomocí následujícího dotazu Entity SQL-aritmetického operátoru má odečíst dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="94d46-111">The following Entity SQL query uses the - arithmetic operator to subtract two numbers.</span></span> <span data-ttu-id="94d46-112">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="94d46-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="94d46-113">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="94d46-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="94d46-114">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="94d46-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="94d46-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="94d46-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#SUBTRACT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#subtract)]  
  
## <a name="see-also"></a><span data-ttu-id="94d46-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="94d46-116">See Also</span></span>  
 [<span data-ttu-id="94d46-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="94d46-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
