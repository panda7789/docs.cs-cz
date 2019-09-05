---
title: '* Hodnotou (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 19fb73d327f91303de938a5f49866339413b9698
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250050"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="f3d80-102">\* (Multiply) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f3d80-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="f3d80-103">Vynásobí dva výrazy.</span><span class="sxs-lookup"><span data-stu-id="f3d80-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3d80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3d80-104">Syntax</span></span>  
  
```  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f3d80-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f3d80-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f3d80-106">Libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="f3d80-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f3d80-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="f3d80-107">Result Types</span></span>  
 <span data-ttu-id="f3d80-108">Datový typ, který je výsledkem propagace implicitního typu obou argumentů.</span><span class="sxs-lookup"><span data-stu-id="f3d80-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="f3d80-109">Další informace o implicitním typu povýšení naleznete v tématu [Type System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="f3d80-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3d80-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3d80-110">Example</span></span>  
 <span data-ttu-id="f3d80-111">Následující Entity SQL dotaz používá aritmetický operátor \* k vynásobení dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="f3d80-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="f3d80-112">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f3d80-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f3d80-113">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="f3d80-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f3d80-114">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="f3d80-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f3d80-115">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="f3d80-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTIPLY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="f3d80-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3d80-116">See also</span></span>

- [<span data-ttu-id="f3d80-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f3d80-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
