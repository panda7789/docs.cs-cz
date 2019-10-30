---
title: + (Sečíst)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: 62bb4782f135309eed8efa7e182fd8b75f92e126
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040296"
---
# <a name="-add"></a><span data-ttu-id="fa348-102">+ (Přidat)</span><span class="sxs-lookup"><span data-stu-id="fa348-102">+ (Add)</span></span>
<span data-ttu-id="fa348-103">Přidá dvě čísla.</span><span class="sxs-lookup"><span data-stu-id="fa348-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa348-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa348-104">Syntax</span></span>  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="fa348-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="fa348-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="fa348-106">Libovolný platný výraz libovolného číselného datového typu.</span><span class="sxs-lookup"><span data-stu-id="fa348-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fa348-107">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="fa348-107">Result Types</span></span>  
 <span data-ttu-id="fa348-108">Datový typ, který je výsledkem propagace implicitního typu obou argumentů.</span><span class="sxs-lookup"><span data-stu-id="fa348-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="fa348-109">Další informace o implicitním typu povýšení naleznete v tématu [Type System](type-system-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fa348-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa348-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa348-110">Remarks</span></span>  
 <span data-ttu-id="fa348-111">Pro EDM. Řetězcové typy, sčítání jsou zřetězené.</span><span class="sxs-lookup"><span data-stu-id="fa348-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa348-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa348-112">Example</span></span>  
 <span data-ttu-id="fa348-113">Následující Entity SQL dotaz pomocí operátoru + aritmetické přidají dvě čísla.</span><span class="sxs-lookup"><span data-stu-id="fa348-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="fa348-114">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="fa348-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="fa348-115">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="fa348-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="fa348-116">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="fa348-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="fa348-117">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="fa348-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="fa348-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa348-118">See also</span></span>

- [<span data-ttu-id="fa348-119">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fa348-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="fa348-120">Typy konceptuálních modelů (CSDL)</span><span class="sxs-lookup"><span data-stu-id="fa348-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
