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
ms.openlocfilehash: f4c0d7fa9f14868404cde6201692e26b919198be
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43803662"
---
# <a name="group-join-clause-visual-basic"></a>Group Join – klauzule (Visual Basic)
Kombinuje dvě kolekce do jedné hierarchické kolekce. Operace spojení je založená na shodujících se klíčích.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`element`|Požadováno. Řídicí proměnná pro kolekci, je připojen.|  
|`type`|Volitelné. Typ `element`. Pokud ne `type` je zadán typ `element` je odvozen z `collection`.|  
|`collection`|Požadováno. Kolekce, kterou chcete zkombinovat s kolekcí, který je na levé straně `Group Join` operátor. A `Group Join` klauzule může být vnořena v `Join` klauzule nebo v jiném `Group Join` klauzuli.|  
|`key1` `Equals` `key2`|Požadováno. Určuje klíče pro kolekce, je připojen. Je nutné použít `Equals` operátor porovnání klíčů z kolekcí je připojen. Podmínky připojení můžete kombinovat pomocí `And` operátor k identifikaci více klíčů. `key1` Parametr musí být z kolekce na levé straně `Join` operátor. `key2` Parametr musí být z kolekce na pravé straně `Join` operátor.<br /><br /> Klíče používané v podmínku připojení může být výrazů, které obsahují více než jednu položku z kolekce. Každý výraz klíče však může obsahovat pouze položky z jeho příslušné kolekce.|  
|`expressionList`|Požadováno. Jeden nebo více výrazů, které určují, jak se agregují skupiny prvků z kolekce. Chcete-li zjistit název člena pro seskupené výsledky, použijte `Group` – klíčové slovo (`<alias> = Group`). Může také obsahovat agregační funkce, které chcete aplikovat ve skupině.|  
  
## <a name="remarks"></a>Poznámky  
 `Group Join` Klauzule kombinuje dvě kolekce na základě porovnání hodnoty klíče z kolekcí je připojen. Výsledný kolekce může obsahovat člena, který odkazuje na kolekci elementů z druhé kolekce, která odpovídá hodnotě klíče z první kolekce. Můžete také zadat agregační funkce použít na seskupené prvky z druhé kolekci. Informace o agregačních funkcích naleznete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Zvažte například kolekce manažerů a kolekce zaměstnanců. Elementy z obou kolekcí mají ManagerID vlastnost, která identifikuje zaměstnance, kteří pro konkrétní nadřízeného. Výsledek pro každého správce a zaměstnanci s odpovídající hodnotou ManagerID by obsahovat výsledky z operace spojení. Výsledky z `Group Join` operace by obsahoval úplný seznam správců. Každý správce výsledek by obsahovat členy, na který odkazuje seznam zaměstnanců, která byla nalezena shoda s konkrétní správce.  
  
 Vyplývající z kolekce `Group Join` operace může obsahovat libovolnou kombinaci hodnot z kolekce identifikované v `From` klauzule a výrazy uvedené v `Into` klauzuli `Group Join` klauzuli. Další informace o zobrazení platných výrazů pro `Into` klauzule, naleznete v tématu [Aggregate – klauzule](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 A `Group Join` operace vrátí všechny výsledky z kolekce vymezených na levé straně `Group Join` operátor. To platí i v případě, že neexistují žádné odpovídající položky v kolekci je připojen. Podobá se trochu `LEFT OUTER JOIN` v SQL.  
  
 Můžete použít `Join` klauzule zkombinovat kolekce do jedné kolekce. To je ekvivalentní `INNER JOIN` v SQL.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu spojení dvou kolekcí s použitím `Group Join` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/index.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Join](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Klauzule Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
