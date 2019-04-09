---
title: '> (Větší než) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: 992e1b7cf4733266f606f8357c71d72722b04896
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127124"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="a6c7d-102">> (Větší) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a6c7d-102">> (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="a6c7d-103">Porovná dva výrazy k určení, zda levý výraz má hodnotu větší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="a6c7d-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6c7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6c7d-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a6c7d-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a6c7d-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="a6c7d-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="a6c7d-106">Any valid expression.</span></span> <span data-ttu-id="a6c7d-107">Implicitně převést datové typy musí mít oba výrazy.</span><span class="sxs-lookup"><span data-stu-id="a6c7d-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a6c7d-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="a6c7d-108">Result Types</span></span>  
 `true` <span data-ttu-id="a6c7d-109">Pokud levý výraz má hodnotu větší než pravý výraz; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="a6c7d-109">if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6c7d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a6c7d-110">Example</span></span>  
 <span data-ttu-id="a6c7d-111">Pomocí následujícího dotazu Entity SQL > – operátor porovnání k porovnání dvou výrazů slouží k určení, zda levý výraz má hodnotu větší než pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="a6c7d-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="a6c7d-112">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a6c7d-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a6c7d-113">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="a6c7d-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="a6c7d-114">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a6c7d-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="a6c7d-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="a6c7d-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="a6c7d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6c7d-116">See also</span></span>

- [<span data-ttu-id="a6c7d-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a6c7d-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
