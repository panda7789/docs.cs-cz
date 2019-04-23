---
title: '>= (Větší než nebo rovno) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: b5a8a834c325cca38e2c106ca3f8ee829dd699b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317139"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="67dcf-102">> = (větší než nebo rovno) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="67dcf-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="67dcf-103">Porovná dva výrazy k určení, zda levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="67dcf-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67dcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67dcf-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="67dcf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="67dcf-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="67dcf-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="67dcf-106">Any valid expression.</span></span> <span data-ttu-id="67dcf-107">Implicitně převést datové typy musí mít oba výrazy.</span><span class="sxs-lookup"><span data-stu-id="67dcf-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="67dcf-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="67dcf-108">Result Types</span></span>  
 <span data-ttu-id="67dcf-109">`true` Pokud levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="67dcf-109">`true` if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67dcf-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="67dcf-110">Example</span></span>  
 <span data-ttu-id="67dcf-111">Pomocí následujícího dotazu Entity SQL > = – operátor porovnání k porovnání dvou výrazů slouží k určení, zda levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="67dcf-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="67dcf-112">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="67dcf-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="67dcf-113">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="67dcf-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="67dcf-114">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="67dcf-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="67dcf-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="67dcf-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="67dcf-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="67dcf-116">See also</span></span>

- [<span data-ttu-id="67dcf-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="67dcf-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
