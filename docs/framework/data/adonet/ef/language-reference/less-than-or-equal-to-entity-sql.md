---
title: '&lt;= (Je menší než nebo rovno) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: 66eb2dc5d4b23ea2f4e00888237b36c950c80602
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604025"
---
# <a name="lt-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="8bb75-102">&lt;= (Je menší než nebo rovno) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8bb75-102">&lt;= (Less Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="8bb75-103">Porovná dva výrazy k určení, zda levý výraz má hodnotu menší než nebo rovna pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="8bb75-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bb75-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bb75-104">Syntax</span></span>  
  
```  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="8bb75-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8bb75-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8bb75-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="8bb75-106">Any valid expression.</span></span> <span data-ttu-id="8bb75-107">Implicitně převést datové typy musí mít oba výrazy.</span><span class="sxs-lookup"><span data-stu-id="8bb75-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="8bb75-108">Typy výsledků</span><span class="sxs-lookup"><span data-stu-id="8bb75-108">Result Types</span></span>  
 <span data-ttu-id="8bb75-109">`true` Pokud levý výraz má hodnotu menší než nebo rovna pravý výraz; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="8bb75-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bb75-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8bb75-110">Example</span></span>  
 <span data-ttu-id="8bb75-111">Následující dotaz Entity SQL používá < = – operátor porovnání k porovnání dvou výrazů slouží k určení, zda levý výraz má hodnotu menší než nebo rovna pravý výraz.</span><span class="sxs-lookup"><span data-stu-id="8bb75-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="8bb75-112">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="8bb75-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="8bb75-113">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="8bb75-113">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="8bb75-114">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="8bb75-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="8bb75-115">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="8bb75-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="8bb75-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bb75-116">See also</span></span>
- [<span data-ttu-id="8bb75-117">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8bb75-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
