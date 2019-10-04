---
title: V (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: e46db63600b6baa03697615a2f5eb9240f55d15e
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833696"
---
# <a name="in-entity-sql"></a><span data-ttu-id="a8f24-102">V (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a8f24-102">IN (Entity SQL)</span></span>
<span data-ttu-id="a8f24-103">Určuje, zda hodnota odpovídá jakékoli hodnotě v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a8f24-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8f24-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8f24-104">Syntax</span></span>  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="a8f24-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a8f24-105">Arguments</span></span>  
 `value`  
 <span data-ttu-id="a8f24-106">Libovolný platný výraz, který vrací hodnotu, která se má shodovat.</span><span class="sxs-lookup"><span data-stu-id="a8f24-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="a8f24-107">MĚNÍ</span><span class="sxs-lookup"><span data-stu-id="a8f24-107">[ NOT ]</span></span>  
 <span data-ttu-id="a8f24-108">Určuje, že výsledkem operátoru `Boolean` je negace.</span><span class="sxs-lookup"><span data-stu-id="a8f24-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="a8f24-109">Libovolný platný výraz, který vrátí kolekci pro otestování shody.</span><span class="sxs-lookup"><span data-stu-id="a8f24-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="a8f24-110">Všechny výrazy musí být stejného typu nebo společného základního nebo odvozeného typu jako `value`.</span><span class="sxs-lookup"><span data-stu-id="a8f24-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8f24-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a8f24-111">Return Value</span></span>  
 <span data-ttu-id="a8f24-112">`true`, pokud je hodnota v kolekci nalezena; hodnota null, pokud má hodnotu null nebo je kolekce null; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="a8f24-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="a8f24-113">Použití operátoru NOT v negaci výsledků v.</span><span class="sxs-lookup"><span data-stu-id="a8f24-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8f24-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8f24-114">Example</span></span>  
 <span data-ttu-id="a8f24-115">Následující Entity SQL dotaz používá operátor IN k určení, zda hodnota odpovídá jakékoli hodnotě v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a8f24-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="a8f24-116">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="a8f24-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="a8f24-117">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="a8f24-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="a8f24-118">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="a8f24-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="a8f24-119">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="a8f24-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a><span data-ttu-id="a8f24-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8f24-120">See also</span></span>

- [<span data-ttu-id="a8f24-121">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a8f24-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
