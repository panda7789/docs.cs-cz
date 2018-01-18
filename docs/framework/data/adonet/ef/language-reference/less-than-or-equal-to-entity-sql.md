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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c6ad4e03a2221491276ae64cf292df8ce3ccd53d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="lt-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="66b52-102">&lt;= (Je menší než nebo rovno) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="66b52-102">&lt;= (Less Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="66b52-103">Porovná dva výrazy a určit, zda levý výraz má hodnotu menší než nebo rovna pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="66b52-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66b52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66b52-104">Syntax</span></span>  
  
```  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="66b52-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="66b52-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="66b52-106">Jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="66b52-106">Any valid expression.</span></span> <span data-ttu-id="66b52-107">Oba výrazy musí mít implicitně převést datové typy.</span><span class="sxs-lookup"><span data-stu-id="66b52-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="66b52-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="66b52-108">Result Types</span></span>  
 <span data-ttu-id="66b52-109">`true`Pokud levý výraz má hodnotu menší než nebo rovna pravý výraz; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="66b52-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66b52-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="66b52-110">Example</span></span>  
 <span data-ttu-id="66b52-111">Následující dotaz Entity SQL používá < = – operátor porovnání k porovnání dvou výrazů k určení, zda levý výraz má hodnotu menší než nebo rovna pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="66b52-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="66b52-112">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="66b52-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="66b52-113">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="66b52-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="66b52-114">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="66b52-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="66b52-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="66b52-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="66b52-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="66b52-116">See Also</span></span>  
 [<span data-ttu-id="66b52-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="66b52-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
