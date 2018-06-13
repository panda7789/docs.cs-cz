---
title: Výrazy dotazů (entita SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: d721f54486845847ec86253356e7a605f882722b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763550"
---
# <a name="query-expressions-entity-sql"></a>Výrazy dotazů (entita SQL)
Výraz dotazu kombinuje operátory mnoho různých dotazu do jednoho syntaxe. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje různé druhy výrazů, včetně následujících: [literály](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parametry](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [proměnné](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operátory, [funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md), nastavte operátory a tak dále. Další informace najdete v tématu [odkaz na entitu SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).  
  
## <a name="clauses"></a>Klauzule  
 Výraz dotazu se skládá z řady klauzule, která se týkají po sobě jdoucích operací na kolekci objektů. Jsou založené na stejné klauzule nalezena ve verzi standard vyberte příkaz SQL: [vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [kde](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [GROUP BY](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [s](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), a [řadit podle](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  
  
## <a name="scope"></a>Rozsah  
 Názvy definované v klauzuli FROM vydávají do oboru FROM v pořadí podle vzhled, zleva doprava. V seznamu připojení výrazy mohou odkazovat na názvy definované výše v seznamu. Veřejné vlastnosti elementů určené v klauzuli FROM nejsou přidány do oboru FROM: musí být vždy odkazuje prostřednictvím alias kvalifikovaný název. Za normálních okolností jsou považovány všechny části vyberte výrazu za v rámci oboru FROM.  
  
## <a name="see-also"></a>Viz také  
 [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
