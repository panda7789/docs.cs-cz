---
title: '- Rozdělovací (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: d4e4c1449b665e6dea22bfcc0ee2277478b4da1a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251058"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="d89bd-102">/(Dělení) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d89bd-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="d89bd-103">Vydělí jedno číslo jiným číslem.</span><span class="sxs-lookup"><span data-stu-id="d89bd-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d89bd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d89bd-104">Syntax</span></span>  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="d89bd-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d89bd-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="d89bd-106">Číselný výraz, který se má rozdělit</span><span class="sxs-lookup"><span data-stu-id="d89bd-106">The numeric expression to divide.</span></span> <span data-ttu-id="d89bd-107">`dividend`je libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="d89bd-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="d89bd-108">Číselný výraz, podle kterého se má dělenec rozdělit.</span><span class="sxs-lookup"><span data-stu-id="d89bd-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="d89bd-109">`divisor`je libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="d89bd-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d89bd-110">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="d89bd-110">Result Types</span></span>  
 <span data-ttu-id="d89bd-111">Datový typ, který je výsledkem propagace implicitního typu obou argumentů.</span><span class="sxs-lookup"><span data-stu-id="d89bd-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="d89bd-112">Další informace o implicitním typu povýšení naleznete v tématu [Type System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d89bd-112">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d89bd-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="d89bd-113">Example</span></span>  
 <span data-ttu-id="d89bd-114">Následující Entity SQL dotaz používá aritmetický operátor/k rozdělení jednoho čísla jiným.</span><span class="sxs-lookup"><span data-stu-id="d89bd-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="d89bd-115">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d89bd-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d89bd-116">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="d89bd-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="d89bd-117">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="d89bd-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="d89bd-118">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="d89bd-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DIVIDE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="d89bd-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d89bd-119">See also</span></span>

- [<span data-ttu-id="d89bd-120">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d89bd-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
