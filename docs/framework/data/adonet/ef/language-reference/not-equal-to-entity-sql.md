---
title: '! = (Nerovná se) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 3b4a02ad-ddfc-4c42-8dfa-676234461312
ms.openlocfilehash: c2ccadaa5801cac9c10241108f02ade223a8697f
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249842"
---
# <a name="-not-equal-to-entity-sql"></a><span data-ttu-id="2c537-102">! = (Nerovná se) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2c537-102">!= (Not Equal To) (Entity SQL)</span></span>
<span data-ttu-id="2c537-103">Porovná dva výrazy a určí, zda se levý výraz nerovná pravému výrazu.</span><span class="sxs-lookup"><span data-stu-id="2c537-103">Compares two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="2c537-104">Operátor! = (není rovno) je funkčně ekvivalentní k operátoru < >.</span><span class="sxs-lookup"><span data-stu-id="2c537-104">The != (Not Equal To) operator is functionally equivalent to the <> operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c537-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c537-105">Syntax</span></span>  
  
```  
expression != expression  
or  
expression <> expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2c537-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="2c537-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="2c537-107">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="2c537-107">Any valid expression.</span></span> <span data-ttu-id="2c537-108">Oba výrazy musí mít implicitně převoditelné datové typy.</span><span class="sxs-lookup"><span data-stu-id="2c537-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2c537-109">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="2c537-109">Result Types</span></span>  
 <span data-ttu-id="2c537-110">`true`Pokud levý výraz není roven pravému výrazu; v opačném případě. `false`</span><span class="sxs-lookup"><span data-stu-id="2c537-110">`true` if the left expression is not equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c537-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c537-111">Example</span></span>  
 <span data-ttu-id="2c537-112">Následující Entity SQL dotaz pomocí operátoru! = Porovná dva výrazy a určí, zda se levý výraz nerovná pravému výrazu.</span><span class="sxs-lookup"><span data-stu-id="2c537-112">The following Entity SQL query uses the != operator to compare two expressions to determine whether the left expression is not equal to the right expression.</span></span> <span data-ttu-id="2c537-113">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="2c537-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2c537-114">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="2c537-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2c537-115">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="2c537-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2c537-116">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="2c537-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NOT_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#not_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="2c537-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c537-117">See also</span></span>

- [<span data-ttu-id="2c537-118">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2c537-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
