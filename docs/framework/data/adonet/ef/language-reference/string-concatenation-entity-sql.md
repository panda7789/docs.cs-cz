---
title: + (Zřetězení řetězců) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: 8a1785d590c5f7fcc443856180d516bb40cfc28e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408471"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="d907f-102">+ (Zřetězení řetězců) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d907f-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="d907f-103">Spojuje dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="d907f-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d907f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d907f-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="d907f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d907f-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d907f-106">Libovolný platný výraz modelu EDM. Řetězec datové typy.</span><span class="sxs-lookup"><span data-stu-id="d907f-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="d907f-107">Oba výrazy musí být stejného typu dat nebo jeden výraz musí být možné implicitně převést na datový typ jiný výraz.</span><span class="sxs-lookup"><span data-stu-id="d907f-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d907f-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="d907f-108">Result Types</span></span>  
 <span data-ttu-id="d907f-109">Datový typ, který je výsledkem implicitních typů povýšení dvou argumentů.</span><span class="sxs-lookup"><span data-stu-id="d907f-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="d907f-110">Další informace o podpoře implicitních typů, najdete v části [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="d907f-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d907f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="d907f-111">Example</span></span>  
 <span data-ttu-id="d907f-112">Následující dotaz Entity SQL používá + operátor spojuje dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="d907f-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="d907f-113">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="d907f-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="d907f-114">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="d907f-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="d907f-115">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="d907f-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="d907f-116">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="d907f-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="d907f-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d907f-117">See Also</span></span>  
 [<span data-ttu-id="d907f-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d907f-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="d907f-119">Typy konceptuálních modelů (CSDL)</span><span class="sxs-lookup"><span data-stu-id="d907f-119">Conceptual Model Types (CSDL)</span></span>](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
