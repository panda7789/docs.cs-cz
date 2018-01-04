---
title: "&lt;= (Je menší než nebo rovno) (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ca900cde1845083e515fa4e8e884b57f8ae689a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lt-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="b5e3a-102">&lt;= (Je menší než nebo rovno) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="b5e3a-102">&lt;= (Less Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="b5e3a-103">Porovná dva výrazy a určit, zda levý výraz má hodnotu menší než nebo rovna pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="b5e3a-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5e3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5e3a-104">Syntax</span></span>  
  
```  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="b5e3a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b5e3a-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b5e3a-106">Jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="b5e3a-106">Any valid expression.</span></span> <span data-ttu-id="b5e3a-107">Oba výrazy musí mít implicitně převést datové typy.</span><span class="sxs-lookup"><span data-stu-id="b5e3a-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="b5e3a-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="b5e3a-108">Result Types</span></span>  
 <span data-ttu-id="b5e3a-109">`true`Pokud levý výraz má hodnotu menší než nebo rovna pravý výraz; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="b5e3a-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5e3a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5e3a-110">Example</span></span>  
 <span data-ttu-id="b5e3a-111">Následující dotaz Entity SQL používá < = – operátor porovnání k porovnání dvou výrazů k určení, zda levý výraz má hodnotu menší než nebo rovna pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="b5e3a-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="b5e3a-112">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b5e3a-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b5e3a-113">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="b5e3a-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="b5e3a-114">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b5e3a-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="b5e3a-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="b5e3a-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="b5e3a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5e3a-116">See Also</span></span>  
 [<span data-ttu-id="b5e3a-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b5e3a-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
