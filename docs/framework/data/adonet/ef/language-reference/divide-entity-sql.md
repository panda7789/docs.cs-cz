---
title: '- Rozdělovací (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: 79fdbebc648daac4f695387d52d2a915383f99ca
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833889"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="16e78-102">/(Dělení) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="16e78-102">/ (Divide) (Entity SQL)</span></span>
<span data-ttu-id="16e78-103">Vydělí jedno číslo jiným číslem.</span><span class="sxs-lookup"><span data-stu-id="16e78-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16e78-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16e78-104">Syntax</span></span>  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="16e78-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="16e78-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="16e78-106">Číselný výraz, který se má rozdělit</span><span class="sxs-lookup"><span data-stu-id="16e78-106">The numeric expression to divide.</span></span> <span data-ttu-id="16e78-107">`dividend` je libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="16e78-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="16e78-108">Číselný výraz, podle kterého se má dělenec rozdělit.</span><span class="sxs-lookup"><span data-stu-id="16e78-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="16e78-109">`divisor` je libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="16e78-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="16e78-110">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="16e78-110">Result Types</span></span>  
 <span data-ttu-id="16e78-111">Datový typ, který je výsledkem propagace implicitního typu obou argumentů.</span><span class="sxs-lookup"><span data-stu-id="16e78-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="16e78-112">Další informace o implicitním typu povýšení naleznete v tématu [Type System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="16e78-112">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="16e78-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="16e78-113">Example</span></span>  
 <span data-ttu-id="16e78-114">Následující Entity SQL dotaz používá aritmetický operátor/k rozdělení jednoho čísla jiným.</span><span class="sxs-lookup"><span data-stu-id="16e78-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="16e78-115">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="16e78-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="16e78-116">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="16e78-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="16e78-117">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="16e78-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="16e78-118">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="16e78-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="16e78-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16e78-119">See also</span></span>

- [<span data-ttu-id="16e78-120">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="16e78-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
