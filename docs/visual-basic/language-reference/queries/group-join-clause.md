---
title: Group Join – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 094281b0afb34451ae8539e4eb967043b21d379c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="group-join-clause-visual-basic"></a>Group Join – klauzule (Visual Basic)
Kombinuje dvě kolekce do jedné hierarchické kolekce. Spojení operace je založená na odpovídající klíče.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`element`|Požadováno. Ovládací prvek proměnnou pro kolekci se připojený.|  
|`type`|Volitelné. Typ `element`. Pokud žádné `type` je zadaný typ `element` je odvozeno z `collection`.|  
|`collection`|Požadováno. Kolekce se zkombinovat s kolekcí, který je na levé straně `Group Join` operátor. A `Group Join` klauzule mohou být použity v `Join` klauzule nebo v jiném `Group Join` klauzule.|  
|`key1` `Equals` `key2`|Požadováno. Identifikuje klíče pro kolekce se připojený. Je nutné použít `Equals` operátor k porovnání klíče z kolekce se připojený. Podmínky připojení můžete kombinovat pomocí `And` operátor k identifikaci několik klíčů. `key1` Parametr musí být z kolekce na levé straně `Join` operátor. `key2` Parametr musí být z kolekce na pravé straně `Join` operátor.<br /><br /> Klíčů používaných v podmínku připojení může být výrazy, které obsahují více než jednu položku z kolekce. Každý výraz klíče však může obsahovat pouze položky z jeho příslušné kolekce.|  
|`expressionList`|Požadováno. Jeden nebo více výrazů, které určují, jak jsou agregovat skupiny elementy z kolekce. Lze zjistit název člena seskupené výsledků `Group` – klíčové slovo (`<alias> = Group`). Můžete použít také agregační funkce na aplikujete na skupinu.|  
  
## <a name="remarks"></a>Poznámky  
 `Group Join` Klauzule kombinuje dvě kolekce na základě shody se hodnoty klíče z kolekce se připojený. Výsledný kolekce může obsahovat člena, který odkazuje na kolekci elementů z druhé kolekci, která odpovídají hodnotě klíče z první kolekce. Můžete také zadat agregační funkce použít na seskupené elementy z druhé kolekci. Informace o agregační funkce najdete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Zvažte například kolekce správci a kolekce zaměstnanci. Elementy z obou kolekcí mají ManagerID vlastnost, která identifikuje zaměstnance, kteří pro konkrétní nadřízeného. Výsledek pro každou manager a zaměstnanci s odpovídající hodnotou ManagerID by obsahovat výsledky z operace spojení. Výsledky z `Group Join` operace by obsahovat úplný seznam správci. Každý výsledek manager by měla mít člena, který odkazuje seznamu zaměstnanců, které byly shoda pro konkrétní správce.  
  
 Kolekce vyplývající z `Group Join` operace může obsahovat libovolnou kombinaci hodnot z kolekce v identifikovat `From` klauzule a výrazy určené v `Into` klauzuli `Group Join` klauzule. Další informace o platné výrazy pro `Into` klauzule, najdete v části [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 A `Group Join` operace vrátí všechny výsledky z kolekce identifikovat na levé straně `Group Join` operátor. To platí i v případě, že neexistují žádné odpovídající položky v kolekci se připojený. Toto je třeba `LEFT OUTER JOIN` v systému SQL.  
  
 Můžete použít `Join` klauzule kombinování kolekcí do jedné kolekce. Jde o ekvivalent `INNER JOIN` v systému SQL.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu spojí dvě kolekce pomocí `Group Join` klauzule.  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Join](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Klauzule Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
