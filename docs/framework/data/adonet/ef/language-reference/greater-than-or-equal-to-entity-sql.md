---
title: '&gt;= (Větší než nebo rovno) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: 34326072f4772e74a45e0ffb6ea1e35f1596b206
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54697140"
---
# <a name="gt-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="46e91-102">&gt;= (Větší než nebo rovno) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="46e91-102">&gt;= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="46e91-103">Porovná dva výrazy k určení, zda levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="46e91-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46e91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46e91-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="46e91-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="46e91-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="46e91-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="46e91-106">Any valid expression.</span></span> <span data-ttu-id="46e91-107">Implicitně převést datové typy musí mít oba výrazy.</span><span class="sxs-lookup"><span data-stu-id="46e91-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="46e91-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="46e91-108">Result Types</span></span>  
 <span data-ttu-id="46e91-109">`true` Pokud levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="46e91-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46e91-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="46e91-110">Example</span></span>  
 <span data-ttu-id="46e91-111">Pomocí následujícího dotazu Entity SQL > = – operátor porovnání k porovnání dvou výrazů slouží k určení, zda levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="46e91-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="46e91-112">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="46e91-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="46e91-113">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="46e91-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="46e91-114">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="46e91-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="46e91-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="46e91-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="46e91-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46e91-116">See also</span></span>
- [<span data-ttu-id="46e91-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="46e91-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
