---
title: + (Zřetězení řetězců) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: ef482a1206dea98cfb5a0ba5071acc130ef0cd18
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249022"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="6e0e1-102">+ (Zřetězení řetězců) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6e0e1-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="6e0e1-103">Zřetězí dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e0e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e0e1-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="6e0e1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6e0e1-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6e0e1-106">Libovolný platný výraz modelu EDM. Řetězcové datové typy.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="6e0e1-107">Oba výrazy musí být stejného datového typu nebo jeden výraz musí být možné implicitně převést na datový typ druhého výrazu.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="6e0e1-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="6e0e1-108">Result Types</span></span>  
 <span data-ttu-id="6e0e1-109">Datový typ, který je výsledkem propagace implicitního typu obou argumentů.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="6e0e1-110">Další informace o implicitním typu povýšení naleznete v tématu [Type System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6e0e1-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e0e1-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="6e0e1-111">Example</span></span>  
 <span data-ttu-id="6e0e1-112">Následující Entity SQL dotaz používá operátor + k zřetězení dvou řetězců.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="6e0e1-113">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6e0e1-114">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="6e0e1-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6e0e1-115">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="6e0e1-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="6e0e1-116">Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="6e0e1-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="6e0e1-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e0e1-117">See also</span></span>

- [<span data-ttu-id="6e0e1-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6e0e1-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="6e0e1-119">Typy konceptuálních modelů (CSDL)</span><span class="sxs-lookup"><span data-stu-id="6e0e1-119">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
