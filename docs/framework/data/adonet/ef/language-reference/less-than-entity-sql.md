---
title: '&lt; (Méně než) (Entita SQL)'
ms.date: 03/30/2017
ms.assetid: 1fc2a039-3ad6-4b3c-b41d-09932e803f86
ms.openlocfilehash: e11f28fd05cb49524b5a0ff854f951385603602f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760970"
---
# <a name="lt-less-than-entity-sql"></a><span data-ttu-id="5857c-102">&lt; (Méně než) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="5857c-102">&lt; (Less Than) (Entity SQL)</span></span>
<span data-ttu-id="5857c-103">Porovná dva výrazy a určit, zda má hodnotu menší, než pravý výraz levý výraz.</span><span class="sxs-lookup"><span data-stu-id="5857c-103">Compares two expressions to determine whether the left expression has a value less than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5857c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5857c-104">Syntax</span></span>  
  
```  
expression < expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5857c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5857c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5857c-106">Jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="5857c-106">Any valid expression.</span></span> <span data-ttu-id="5857c-107">Oba výrazy musí mít implicitně převést datové typy.</span><span class="sxs-lookup"><span data-stu-id="5857c-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5857c-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="5857c-108">Result Types</span></span>  
 <span data-ttu-id="5857c-109">`true` Pokud levý výraz má hodnotu menší, než pravý výraz; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="5857c-109">`true` if the left expression has a value less than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5857c-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5857c-110">Example</span></span>  
 <span data-ttu-id="5857c-111">Následující dotaz Entity SQL používá < – operátor porovnání k porovnání dvou výrazů k určení, zda má hodnotu menší, než pravý výraz levý výraz.</span><span class="sxs-lookup"><span data-stu-id="5857c-111">The following Entity SQL query uses < comparison operator to compare two expressions to determine whether the left expression has a value less than the right expression.</span></span> <span data-ttu-id="5857c-112">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5857c-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5857c-113">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="5857c-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="5857c-114">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="5857c-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="5857c-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="5857c-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less)]  
  
## <a name="see-also"></a><span data-ttu-id="5857c-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5857c-116">See Also</span></span>  
 [<span data-ttu-id="5857c-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5857c-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
