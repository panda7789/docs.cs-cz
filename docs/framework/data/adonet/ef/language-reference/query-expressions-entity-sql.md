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
# <a name="query-expressions-entity-sql"></a>Výrazy dotazů (Entity SQL)
Výraz dotazu kombinuje mnoho různých operátorů dotazu do jediné syntaxe. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]poskytuje různé druhy výrazů, včetně následujících: [literály](literals-entity-sql.md), [parametry](parameters-entity-sql.md), [proměnné](variables-entity-sql.md), operátory, [funkce](functions-entity-sql.md), nastavit operátory a tak dále. Další informace najdete v tématu [Entity SQL Reference](entity-sql-reference.md).  
  
## <a name="clauses"></a>Klauzule  
 Výraz dotazu se skládá z řady klauzulí, které používají po sobě jdoucí operace na kolekci objektů. Jsou založené na stejných klauzulích, které najdete ve standardním příkazu SQL SELECT: [Vyberte](select-entity-sql.md), [from](from-entity-sql.md), [kde](where-entity-sql.md), [Group by](group-by-entity-sql.md), [having](having-entity-sql.md)a [Order](order-by-entity-sql.md)by.  
  
## <a name="scope"></a>Scope  
 Názvy definované v klauzuli FROM jsou představeny v rozsahu od v pořadí vzhledem k pravé straně. V seznamu spojení můžou výrazy odkazovat na názvy definované dříve v seznamu. Veřejné vlastnosti prvků identifikovaných v klauzuli FROM nejsou přidány do rozsahu z: Je nutné, aby se vždy odkazovaly přes kvalifikovaný název aliasu. Za normálních okolností jsou všechny části výrazu SELECT považovány za v rozsahu od.  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](entity-sql-reference.md)
