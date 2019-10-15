---
title: + (Zřetězení řetězců) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 9c078e193eeecd4d331c5e3c04c66dee2c4a1daa
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319317"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="2b9b4-102">+ (Zřetězení řetězců) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2b9b4-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="2b9b4-103">Zřetězí dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="2b9b4-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b9b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b9b4-104">Syntax</span></span>  
  
```sql  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2b9b4-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2b9b4-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2b9b4-106">Libovolný platný výraz modelu EDM. Řetězcové datové typy.</span><span class="sxs-lookup"><span data-stu-id="2b9b4-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="2b9b4-107">Oba výrazy musí být stejného datového typu nebo jeden výraz musí být možné implicitně převést na datový typ druhého výrazu.</span><span class="sxs-lookup"><span data-stu-id="2b9b4-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2b9b4-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="2b9b4-108">Result Types</span></span>  
 <span data-ttu-id="2b9b4-109">Datový typ, který je výsledkem propagace implicitního typu obou argumentů.</span><span class="sxs-lookup"><span data-stu-id="2b9b4-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="2b9b4-110">Další informace o implicitním typu povýšení naleznete v tématu [Type System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="2b9b4-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b9b4-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b9b4-111">Example</span></span>  
 <span data-ttu-id="2b9b4-112">Následující Entity SQL dotaz používá operátor + k zřetězení dvou řetězců.</span><span class="sxs-lookup"><span data-stu-id="2b9b4-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="2b9b4-113">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2b9b4-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2b9b4-114">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="2b9b4-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2b9b4-115">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2b9b4-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="2b9b4-116">Předat následující dotaz jako argument metodě `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="2b9b4-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CONCAT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="2b9b4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b9b4-117">See also</span></span>

- [<span data-ttu-id="2b9b4-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2b9b4-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2b9b4-119">Typy konceptuálních modelů (CSDL)</span><span class="sxs-lookup"><span data-stu-id="2b9b4-119">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
