---
title: + (Zřetězení řetězců) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: b1416649681aed7ef730e9d17c3863a6616ab37f
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903636"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="32f91-102">+ (Zřetězení řetězců) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="32f91-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="32f91-103">Spojuje dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="32f91-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32f91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32f91-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="32f91-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="32f91-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="32f91-106">Libovolný platný výraz modelu EDM. Řetězec datové typy.</span><span class="sxs-lookup"><span data-stu-id="32f91-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="32f91-107">Oba výrazy musí být stejného typu dat nebo jeden výraz musí být možné implicitně převést na datový typ jiný výraz.</span><span class="sxs-lookup"><span data-stu-id="32f91-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="32f91-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="32f91-108">Result Types</span></span>  
 <span data-ttu-id="32f91-109">Datový typ, který je výsledkem implicitních typů povýšení dvou argumentů.</span><span class="sxs-lookup"><span data-stu-id="32f91-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="32f91-110">Další informace o podpoře implicitních typů, najdete v části [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="32f91-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32f91-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="32f91-111">Example</span></span>  
 <span data-ttu-id="32f91-112">Následující dotaz Entity SQL používá + operátor spojuje dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="32f91-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="32f91-113">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="32f91-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="32f91-114">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="32f91-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="32f91-115">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="32f91-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="32f91-116">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="32f91-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="32f91-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32f91-117">See also</span></span>
- [<span data-ttu-id="32f91-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="32f91-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="32f91-119">Typy konceptuálních modelů (CSDL)</span><span class="sxs-lookup"><span data-stu-id="32f91-119">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
