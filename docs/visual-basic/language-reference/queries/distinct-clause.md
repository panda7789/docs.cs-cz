---
title: Distinct – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 5aecffbce036500d294d03a925798d51f1269af6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401391"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="fa5b7-102">Distinct – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa5b7-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="fa5b7-103">Omezuje hodnoty aktuální proměnné rozsahu tak, aby v následných klauzulích dotazu vyloučily duplicitní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa5b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fa5b7-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="fa5b7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fa5b7-105">Remarks</span></span>  
 <span data-ttu-id="fa5b7-106">Pomocí `Distinct` klauzule můžete vracet seznam jedinečných položek.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="fa5b7-107">`Distinct`Klauzule způsobí, že dotaz ignoruje výsledky duplicitních dotazů.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="fa5b7-108">`Distinct`Klauzule se vztahuje na duplicitní hodnoty všech vrácených polí určených `Select` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="fa5b7-109">Pokud `Select` není zadána žádná klauzule, `Distinct` klauzule je použita na proměnnou rozsahu pro dotaz identifikovaný v `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="fa5b7-110">Pokud proměnná rozsahu není neměnný typ, dotaz bude ignorovat výsledek dotazu pouze v případě, že všichni členové typu odpovídají existujícímu výsledku dotazu.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa5b7-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="fa5b7-111">Example</span></span>  
 <span data-ttu-id="fa5b7-112">Následující výraz dotazu spojuje seznam zákazníků a seznam objednávek zákazníků.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="fa5b7-113">`Distinct`K dispozici je klauzule, která vrátí seznam jedinečných názvů zákazníků a data objednávky.</span><span class="sxs-lookup"><span data-stu-id="fa5b7-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="fa5b7-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa5b7-114">See also</span></span>

- [<span data-ttu-id="fa5b7-115">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa5b7-115">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="fa5b7-116">Dotazy</span><span class="sxs-lookup"><span data-stu-id="fa5b7-116">Queries</span></span>](index.md)
- [<span data-ttu-id="fa5b7-117">Klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="fa5b7-117">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="fa5b7-118">Klauzule SELECT</span><span class="sxs-lookup"><span data-stu-id="fa5b7-118">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="fa5b7-119">Klauzule WHERE</span><span class="sxs-lookup"><span data-stu-id="fa5b7-119">Where Clause</span></span>](where-clause.md)
