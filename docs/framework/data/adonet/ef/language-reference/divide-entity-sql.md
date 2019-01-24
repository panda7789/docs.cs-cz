---
title: '- (Dělení) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 42fc5e2a9f9f159a8a60973dbed6540b3188fba6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745231"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="462f0-102">/ (Dělení) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="462f0-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="462f0-103">Rozdělí jedno číslo jiným.</span><span class="sxs-lookup"><span data-stu-id="462f0-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="462f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="462f0-104">Syntax</span></span>  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="462f0-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="462f0-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="462f0-106">Číselný výraz, který se má dělit.</span><span class="sxs-lookup"><span data-stu-id="462f0-106">The numeric expression to divide.</span></span> <span data-ttu-id="462f0-107">`dividend` je libovolný platný výraz některou z číselných datových typů.</span><span class="sxs-lookup"><span data-stu-id="462f0-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="462f0-108">Číselný výraz, který se má dělit dělenec.</span><span class="sxs-lookup"><span data-stu-id="462f0-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="462f0-109">`divisor` je libovolný platný výraz některou z číselných datových typů.</span><span class="sxs-lookup"><span data-stu-id="462f0-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="462f0-110">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="462f0-110">Result Types</span></span>  
 <span data-ttu-id="462f0-111">Datový typ, který je výsledkem implicitních typů povýšení dvou argumentů.</span><span class="sxs-lookup"><span data-stu-id="462f0-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="462f0-112">Další informace o podpoře implicitních typů, najdete v části [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="462f0-112">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="462f0-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="462f0-113">Example</span></span>  
 <span data-ttu-id="462f0-114">Následující dotaz Entity SQL používá / aritmetický operátor dělit jednu číslici jiného.</span><span class="sxs-lookup"><span data-stu-id="462f0-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="462f0-115">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="462f0-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="462f0-116">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="462f0-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="462f0-117">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="462f0-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="462f0-118">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="462f0-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="462f0-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="462f0-119">See also</span></span>
- [<span data-ttu-id="462f0-120">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="462f0-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
