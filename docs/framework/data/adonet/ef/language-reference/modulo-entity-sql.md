---
title: (Modulo) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
ms.openlocfilehash: e2d2c4cd6fd62cf5785d6b69aa399a74f8d04d30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760477"
---
# <a name="modulo-entity-sql"></a><span data-ttu-id="eaf90-102">(Modulo) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="eaf90-102">(Modulo) (Entity SQL)</span></span>
<span data-ttu-id="eaf90-103">Vrátí zbytek jeden výraz hodnotou druhého.</span><span class="sxs-lookup"><span data-stu-id="eaf90-103">Returns the remainder of one expression divided by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eaf90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eaf90-104">Syntax</span></span>  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="eaf90-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="eaf90-105">Arguments</span></span>  
 `dividend`  
 <span data-ttu-id="eaf90-106">Číselný výraz, který se má dělit.</span><span class="sxs-lookup"><span data-stu-id="eaf90-106">The numeric expression to divide.</span></span> <span data-ttu-id="eaf90-107">`dividend` je libovolný platný výraz některou z číselných datových typů.</span><span class="sxs-lookup"><span data-stu-id="eaf90-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="eaf90-108">Číselný výraz, který se má dělit dělenec.</span><span class="sxs-lookup"><span data-stu-id="eaf90-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="eaf90-109">`divisor` je libovolný platný výraz některou z číselných datových typů.</span><span class="sxs-lookup"><span data-stu-id="eaf90-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="eaf90-110">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="eaf90-110">Result Types</span></span>  
 <span data-ttu-id="eaf90-111">Edm.Int32</span><span class="sxs-lookup"><span data-stu-id="eaf90-111">Edm.Int32</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaf90-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="eaf90-112">Example</span></span>  
 <span data-ttu-id="eaf90-113">Následující dotaz Entity SQL používá aritmetického operátoru % vrátit zbývající jeden výraz hodnotou druhého.</span><span class="sxs-lookup"><span data-stu-id="eaf90-113">The following Entity SQL query uses the % arithmetic operator to return the remainder of one expression divided by another.</span></span> <span data-ttu-id="eaf90-114">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="eaf90-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="eaf90-115">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="eaf90-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="eaf90-116">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="eaf90-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="eaf90-117">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="eaf90-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a><span data-ttu-id="eaf90-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eaf90-118">See also</span></span>

- [<span data-ttu-id="eaf90-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="eaf90-119">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
