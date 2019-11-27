---
title: Group Join – klauzule
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
ms.openlocfilehash: 0546c86322663ce6c56a89e63311d0f02f88cfe4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346844"
---
# <a name="group-join-clause-visual-basic"></a>Group Join – klauzule (Visual Basic)
Kombinuje dvě kolekce do jedné hierarchické kolekce. Operace JOIN je založena na spárovaných klíčích.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`element`|Požadováno. Řídicí proměnná pro kolekci, která je připojena.|  
|`type`|Volitelná. Typ připojení `element`. Pokud není zadán žádný `type`, typ `element` je odvozen z `collection`.|  
|`collection`|Požadováno. Kolekce, která se má zkombinovat s kolekcí, která je na levé straně operátoru `Group Join` Klauzule `Group Join` může být vnořena do klauzule `Join` nebo do jiné klauzule `Group Join`.|  
|`key1` `Equals` `key2`|Požadováno. Identifikuje klíče pro připojené kolekce. K porovnání klíčů z kolekce, které jsou spojeny, je nutné použít operátor `Equals`. Podmínky spojení můžete kombinovat pomocí operátoru `And` k identifikaci více klíčů. Parametr `key1` musí být z kolekce na levé straně operátoru `Join`. Parametr `key2` musí být z kolekce na pravé straně operátoru `Join`.<br /><br /> Klíče používané v podmínce spojení mohou být výrazy, které obsahují více než jednu položku z kolekce. Každý klíčový výraz však může obsahovat pouze položky z příslušné kolekce.|  
|`expressionList`|Požadováno. Jeden nebo více výrazů, které určují, jak jsou agregovány skupiny prvků z kolekce. Chcete-li identifikovat název člena pro seskupené výsledky, použijte klíčové slovo `Group` (`<alias> = Group`). Můžete také zahrnout agregační funkce, které se mají použít pro skupinu.|  
  
## <a name="remarks"></a>Poznámky  
 Klauzule `Group Join` kombinuje dvě kolekce založené na porovnání hodnot klíčů od připojených kolekcí. Výsledná kolekce může obsahovat člena, který odkazuje na kolekci prvků z druhé kolekce, která odpovídá hodnotě klíče z první kolekce. Můžete také zadat agregační funkce, které mají být použity pro seskupené prvky z druhé kolekce. Informace o agregačních funkcích naleznete v tématu [klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Vezměte v úvahu například kolekci manažerů a kolekci zaměstnanců. Prvky z obou kolekcí mají vlastnost ManagerID, která identifikuje zaměstnance, kteří nahlásí konkrétnímu manažerovi. Výsledky operace join by obsahovaly výsledek pro každého manažera a zaměstnance s vyhovující hodnotou ManagerID. Výsledky operace `Group Join` by obsahovaly úplný seznam manažerů. Každý výsledek správce by měl člena, který odkazoval na seznam zaměstnanců, kteří byli shodou pro konkrétního manažera.  
  
 Kolekce, která je výsledkem operace `Group Join` může obsahovat libovolnou kombinaci hodnot z kolekce identifikované v klauzuli `From` a výrazy identifikované v klauzuli `Into` klauzule `Group Join`. Další informace o platných výrazech pro klauzuli `Into` naleznete v tématu [klauzule Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Operace `Group Join` vrátí všechny výsledky z kolekce identifikované na levé straně operátoru `Group Join`. To platí i v případě, že se v kolekci nevztahují žádné shody. Jedná se například o `LEFT OUTER JOIN` v SQL.  
  
 Klauzuli `Join` lze použít ke kombinování kolekcí do jedné kolekce. Jedná se o ekvivalent `INNER JOIN` v SQL.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu spojuje dvě kolekce pomocí klauzule `Group Join`.  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Join](../../../visual-basic/language-reference/queries/join-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
- [Klauzule Group By](../../../visual-basic/language-reference/queries/group-by-clause.md)
