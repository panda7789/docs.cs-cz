---
title: + (Zřetězení řetězců) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 580130fa-6c7c-4f76-a47d-d22c27ccadf6
ms.openlocfilehash: e53bd0a2607deb67d45edc44e51cf4ad283b21c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633919"
---
# <a name="-string-concatenation-entity-sql"></a><span data-ttu-id="65e7e-102">+ (Zřetězení řetězců) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="65e7e-102">+ (String Concatenation) (Entity SQL)</span></span>
<span data-ttu-id="65e7e-103">Spojuje dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="65e7e-103">Concatenates two strings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65e7e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65e7e-104">Syntax</span></span>  
  
```  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="65e7e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="65e7e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="65e7e-106">Libovolný platný výraz modelu EDM. Řetězec datové typy.</span><span class="sxs-lookup"><span data-stu-id="65e7e-106">Any valid expression of the EDM.String data types.</span></span> <span data-ttu-id="65e7e-107">Oba výrazy musí být stejného typu dat nebo jeden výraz musí být možné implicitně převést na datový typ jiný výraz.</span><span class="sxs-lookup"><span data-stu-id="65e7e-107">Both expressions must be of the same data type, or one expression must be able to be implicitly converted to the data type of the other expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="65e7e-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="65e7e-108">Result Types</span></span>  
 <span data-ttu-id="65e7e-109">Datový typ, který je výsledkem implicitních typů povýšení dvou argumentů.</span><span class="sxs-lookup"><span data-stu-id="65e7e-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="65e7e-110">Další informace o podpoře implicitních typů, najdete v části [systém typů](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="65e7e-110">For more information about implicit type promotion, see [Type System](../../../../../../docs/framework/data/adonet/ef/language-reference/type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="65e7e-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="65e7e-111">Example</span></span>  
 <span data-ttu-id="65e7e-112">Následující dotaz Entity SQL používá + operátor spojuje dva řetězce.</span><span class="sxs-lookup"><span data-stu-id="65e7e-112">The following Entity SQL query uses the + operator to concatenates two strings.</span></span> <span data-ttu-id="65e7e-113">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="65e7e-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="65e7e-114">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="65e7e-114">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="65e7e-115">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="65e7e-115">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="65e7e-116">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="65e7e-116">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CONCAT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#concat)]  
  
## <a name="see-also"></a><span data-ttu-id="65e7e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65e7e-117">See also</span></span>
- [<span data-ttu-id="65e7e-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="65e7e-118">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="65e7e-119">Typy konceptuálních modelů (CSDL)</span><span class="sxs-lookup"><span data-stu-id="65e7e-119">Conceptual Model Types (CSDL)</span></span>](https://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4)
