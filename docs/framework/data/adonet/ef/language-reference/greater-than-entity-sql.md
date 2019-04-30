---
title: '> (Větší než) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: e1d13fa863eb79982d239f4e2dc298f7fcd1346f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879486"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="75a02-102">> (Větší) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="75a02-102">> (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="75a02-103">Porovná dva výrazy k určení, zda levý výraz má hodnotu větší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="75a02-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75a02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75a02-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="75a02-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="75a02-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="75a02-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="75a02-106">Any valid expression.</span></span> <span data-ttu-id="75a02-107">Implicitně převést datové typy musí mít oba výrazy.</span><span class="sxs-lookup"><span data-stu-id="75a02-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="75a02-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="75a02-108">Result Types</span></span>  
 <span data-ttu-id="75a02-109">`true` Pokud levý výraz má hodnotu větší než pravý výraz; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="75a02-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75a02-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="75a02-110">Example</span></span>  
 <span data-ttu-id="75a02-111">Pomocí následujícího dotazu Entity SQL > – operátor porovnání k porovnání dvou výrazů slouží k určení, zda levý výraz má hodnotu větší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="75a02-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="75a02-112">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="75a02-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="75a02-113">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="75a02-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="75a02-114">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="75a02-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="75a02-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="75a02-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="75a02-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75a02-116">See also</span></span>

- [<span data-ttu-id="75a02-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="75a02-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
