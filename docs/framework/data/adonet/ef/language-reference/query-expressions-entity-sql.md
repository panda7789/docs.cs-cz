---
title: Výrazy dotazů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 4428286890f41573a02daf31a4593d0c8f9ad34b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249277"
---
# <a name="query-expressions-entity-sql"></a><span data-ttu-id="5ebbd-102">Výrazy dotazů (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5ebbd-102">Query Expressions (Entity SQL)</span></span>
<span data-ttu-id="5ebbd-103">Výraz dotazu kombinuje mnoho různých operátorů dotazu do jediné syntaxe.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-103">A query expression combines many different query operators into a single syntax.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5ebbd-104">poskytuje různé druhy výrazů, včetně následujících: [literály](literals-entity-sql.md), [parametry](parameters-entity-sql.md), [proměnné](variables-entity-sql.md), operátory, [funkce](functions-entity-sql.md), nastavit operátory a tak dále.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-104">provides various kinds of expressions, including the following: [literals](literals-entity-sql.md), [parameters](parameters-entity-sql.md), [variables](variables-entity-sql.md), operators, [functions](functions-entity-sql.md), set operators, and so on.</span></span> <span data-ttu-id="5ebbd-105">Další informace najdete v tématu [Entity SQL Reference](entity-sql-reference.md).</span><span class="sxs-lookup"><span data-stu-id="5ebbd-105">For more information, see [Entity SQL Reference](entity-sql-reference.md).</span></span>  
  
## <a name="clauses"></a><span data-ttu-id="5ebbd-106">Klauzule</span><span class="sxs-lookup"><span data-stu-id="5ebbd-106">Clauses</span></span>  
 <span data-ttu-id="5ebbd-107">Výraz dotazu se skládá z řady klauzulí, které používají po sobě jdoucí operace na kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-107">A query expression is composed of a series of clauses that apply successive operations to a collection of objects.</span></span> <span data-ttu-id="5ebbd-108">Jsou založené na stejných klauzulích, které najdete ve standardním příkazu SQL SELECT: [Vyberte](select-entity-sql.md), [from](from-entity-sql.md), [kde](where-entity-sql.md), [Group by](group-by-entity-sql.md), [having](having-entity-sql.md)a [Order](order-by-entity-sql.md)by.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-108">They are based on the same clauses found in standard a SQL select statement: [SELECT](select-entity-sql.md), [FROM](from-entity-sql.md), [WHERE](where-entity-sql.md), [GROUP BY](group-by-entity-sql.md), [HAVING](having-entity-sql.md), and [ORDER BY](order-by-entity-sql.md).</span></span>  
  
## <a name="scope"></a><span data-ttu-id="5ebbd-109">Scope</span><span class="sxs-lookup"><span data-stu-id="5ebbd-109">Scope</span></span>  
 <span data-ttu-id="5ebbd-110">Názvy definované v klauzuli FROM jsou představeny v rozsahu od v pořadí vzhledem k pravé straně.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-110">Names defined in the FROM clause are introduced into the FROM scope in order of appearance, left to right.</span></span> <span data-ttu-id="5ebbd-111">V seznamu spojení můžou výrazy odkazovat na názvy definované dříve v seznamu.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-111">In the JOIN list, expressions can refer to names defined earlier in the list.</span></span> <span data-ttu-id="5ebbd-112">Veřejné vlastnosti prvků identifikovaných v klauzuli FROM nejsou přidány do rozsahu z: Je nutné, aby se vždy odkazovaly přes kvalifikovaný název aliasu.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-112">Public properties of elements identified in the FROM clause are not added to the FROM scope: They must be always referenced through the alias-qualified name.</span></span> <span data-ttu-id="5ebbd-113">Za normálních okolností jsou všechny části výrazu SELECT považovány za v rozsahu od.</span><span class="sxs-lookup"><span data-stu-id="5ebbd-113">Normally, all parts of the select expression are considered within the FROM scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ebbd-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ebbd-114">See also</span></span>

- [<span data-ttu-id="5ebbd-115">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="5ebbd-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
