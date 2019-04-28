---
title: Výrazy dotazů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c36f327b-e230-48d4-bbd5-78dc6478c447
ms.openlocfilehash: 5f89028b9c501dd840f1dc9445418e4757967db8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614619"
---
# <a name="query-expressions-entity-sql"></a>Výrazy dotazů (Entity SQL)
Výraz dotazu kombinuje mnoho operátorů dotazu do jednoho syntaxe. [!INCLUDE[esql](../../../../../../includes/esql-md.md)] poskytuje různé druhy výrazů, včetně následujících: [literály](../../../../../../docs/framework/data/adonet/ef/language-reference/literals-entity-sql.md), [parametry](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md), [proměnné](../../../../../../docs/framework/data/adonet/ef/language-reference/variables-entity-sql.md), operátory, [funkce](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)množinové operátory a tak dále. Další informace najdete v tématu [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md).  
  
## <a name="clauses"></a>Klauzule  
 Výraz dotazu se skládá z řady klauzule, které se vztahují na kolekci objektů následných operací. Jsou založené na stejné klauzule součástí standardní příkaz SQL select: [Vyberte](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md), [FROM](../../../../../../docs/framework/data/adonet/ef/language-reference/from-entity-sql.md), [kde](../../../../../../docs/framework/data/adonet/ef/language-reference/where-entity-sql.md), [Seskupit podle](../../../../../../docs/framework/data/adonet/ef/language-reference/group-by-entity-sql.md), [HAVING](../../../../../../docs/framework/data/adonet/ef/language-reference/having-entity-sql.md), a [ORDER](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md).  
  
## <a name="scope"></a>Rozsah  
 Názvy definované v klauzuli FROM zavedení do rozsahu od v pořadí vzhled, zleva doprava. V seznamu spojení výrazy mohou odkazovat na názvy definované výše v seznamu. Veřejné vlastnosti prvků, které jsou identifikované v klauzuli FROM nejsou přidány do rozsahu od: Musí být vždy odkazovány prostřednictvím alias kvalifikovaný název. Za normálních okolností všechny části vyberte výrazu považují v rámci oboru FROM.  
  
## <a name="see-also"></a>Viz také:

- [Reference k Entity SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
