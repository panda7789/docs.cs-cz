---
title: V (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: 5a07ee79d5452da4341d391fae7c997c33b603a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250664"
---
# <a name="in-entity-sql"></a><span data-ttu-id="b4c7f-102">V (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b4c7f-102">IN (Entity SQL)</span></span>
<span data-ttu-id="b4c7f-103">Určuje, zda hodnota odpovídá jakékoli hodnotě v kolekci.</span><span class="sxs-lookup"><span data-stu-id="b4c7f-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4c7f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4c7f-104">Syntax</span></span>  
  
```  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="b4c7f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="b4c7f-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="b4c7f-106">Libovolný platný výraz, který vrací hodnotu, která se má shodovat.</span><span class="sxs-lookup"><span data-stu-id="b4c7f-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="b4c7f-107">MĚNÍ</span><span class="sxs-lookup"><span data-stu-id="b4c7f-107">[ NOT ]</span></span>  
 <span data-ttu-id="b4c7f-108">Určuje, že `Boolean` výsledek z má být negace.</span><span class="sxs-lookup"><span data-stu-id="b4c7f-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="b4c7f-109">Libovolný platný výraz, který vrátí kolekci pro otestování shody.</span><span class="sxs-lookup"><span data-stu-id="b4c7f-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="b4c7f-110">Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `value`.</span><span class="sxs-lookup"><span data-stu-id="b4c7f-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4c7f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b4c7f-111">Return Value</span></span>  
 <span data-ttu-id="b4c7f-112">`true`Pokud je hodnota v kolekci nalezena; hodnota null, pokud má hodnotu null nebo je kolekce null; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="b4c7f-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="b4c7f-113">Použití operátoru NOT v negaci výsledků v.</span><span class="sxs-lookup"><span data-stu-id="b4c7f-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4c7f-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4c7f-114">Example</span></span>  
 <span data-ttu-id="b4c7f-115">Následující Entity SQL dotaz používá operátor IN k určení, zda hodnota odpovídá jakékoli hodnotě v kolekci.</span><span class="sxs-lookup"><span data-stu-id="b4c7f-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="b4c7f-116">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="b4c7f-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="b4c7f-117">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="b4c7f-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="b4c7f-118">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="b4c7f-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="b4c7f-119">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="b4c7f-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#IN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#in)]  
  
## <a name="see-also"></a><span data-ttu-id="b4c7f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4c7f-120">See also</span></span>

- [<span data-ttu-id="b4c7f-121">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b4c7f-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
