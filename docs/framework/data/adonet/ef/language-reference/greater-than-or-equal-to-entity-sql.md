---
title: '>= (Větší než nebo rovno) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 70780ac4-0123-4da8-b731-8af856daffe3
ms.openlocfilehash: b5a8a834c325cca38e2c106ca3f8ee829dd699b2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317139"
---
# <a name="-greater-than-or-equal-to-entity-sql"></a><span data-ttu-id="b07b4-102">> = (větší než nebo rovno) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b07b4-102">>= (Greater Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="b07b4-103">Porovná dva výrazy k určení, zda levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="b07b4-103">Compares two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b07b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b07b4-104">Syntax</span></span>  
  
```  
expression >= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="b07b4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b07b4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="b07b4-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="b07b4-106">Any valid expression.</span></span> <span data-ttu-id="b07b4-107">Implicitně převést datové typy musí mít oba výrazy.</span><span class="sxs-lookup"><span data-stu-id="b07b4-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="b07b4-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="b07b4-108">Result Types</span></span>  
 `true` <span data-ttu-id="b07b4-109">Pokud levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="b07b4-109">if the left expression has a value greater than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b07b4-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b07b4-110">Example</span></span>  
 <span data-ttu-id="b07b4-111">Pomocí následujícího dotazu Entity SQL > = – operátor porovnání k porovnání dvou výrazů slouží k určení, zda levý výraz má hodnotu větší než nebo rovna hodnotě pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="b07b4-111">The following Entity SQL query uses >= comparison operator to compare two expressions to determine whether the left expression has a value greater than or equal to the right expression.</span></span> <span data-ttu-id="b07b4-112">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b07b4-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b07b4-113">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="b07b4-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b07b4-114">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="b07b4-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b07b4-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="b07b4-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="b07b4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b07b4-116">See also</span></span>

- [<span data-ttu-id="b07b4-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b07b4-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
