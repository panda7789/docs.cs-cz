---
title: '&lt;= (Je menší než nebo rovno) (entita SQL)'
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: dd861bf3490794a7a54a09719ae4ae377d0e2861
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32761867"
---
# <a name="lt-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="ad6c2-102">&lt;= (Je menší než nebo rovno) (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="ad6c2-102">&lt;= (Less Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="ad6c2-103">Porovná dva výrazy a určit, zda levý výraz má hodnotu menší než nebo rovna pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="ad6c2-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad6c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad6c2-104">Syntax</span></span>  
  
```  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ad6c2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ad6c2-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ad6c2-106">Jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="ad6c2-106">Any valid expression.</span></span> <span data-ttu-id="ad6c2-107">Oba výrazy musí mít implicitně převést datové typy.</span><span class="sxs-lookup"><span data-stu-id="ad6c2-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="ad6c2-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="ad6c2-108">Result Types</span></span>  
 <span data-ttu-id="ad6c2-109">`true` Pokud levý výraz má hodnotu menší než nebo rovna pravý výraz; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="ad6c2-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad6c2-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="ad6c2-110">Example</span></span>  
 <span data-ttu-id="ad6c2-111">Následující dotaz Entity SQL používá < = – operátor porovnání k porovnání dvou výrazů k určení, zda levý výraz má hodnotu menší než nebo rovna pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="ad6c2-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="ad6c2-112">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ad6c2-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ad6c2-113">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="ad6c2-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ad6c2-114">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="ad6c2-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ad6c2-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="ad6c2-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="ad6c2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad6c2-116">See Also</span></span>  
 [<span data-ttu-id="ad6c2-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ad6c2-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
