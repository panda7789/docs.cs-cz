---
title: Join – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: 2186954ab6536988271629c4feba0a40563bfc3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603909"
---
# <a name="join-clause-visual-basic"></a>Join – klauzule (Visual Basic)
Kombinuje dvě kolekce do jedné kolekce. Operace spojení je založena na odpovídající klíče a používá `Equals` operátor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>Součásti  
 `element`  
 Požadováno. Ovládací prvek proměnnou pro kolekci se připojený.  
  
 `collection`  
 Požadováno. Kolekce se zkombinovat s kolekcí identifikovat na levé straně `Join` operátor. A `Join` klauzule mohou být použity v jiné `Join` klauzuli, nebo v `Group Join` klauzule.  
  
 `joinClause`  
 Volitelné. Jeden nebo více dalších `Join` klauzule pro další upřesnění dotazu.  
  
 `groupJoinClause`  
 Volitelné. Jeden nebo více dalších `Group Join` klauzule pro další upřesnění dotazu.  
  
 `key1` `Equals` `key2`  
 Požadováno. Identifikuje klíče pro kolekce se připojený. Je nutné použít `Equals` operátor k porovnání klíče z kolekce se připojený. Podmínky připojení můžete kombinovat pomocí `And` operátor k identifikaci několik klíčů. `key1` musí být z kolekce na levé straně `Join` operátor. `key2` musí být z kolekce na pravé straně `Join` operátor.  
  
 Klíčů používaných v podmínku připojení může být výrazy, které obsahují více než jednu položku z kolekce. Každý výraz klíče však může obsahovat pouze položky z jeho příslušné kolekce.  
  
## <a name="remarks"></a>Poznámky  
 `Join` Klauzule kombinuje dvě kolekce na základě shody se hodnoty klíče z kolekce se připojený. Výsledný kolekce může obsahovat libovolnou kombinaci hodnoty z kolekce identifikovat na levé straně `Join` operátor a identifikovat v kolekci `Join` klauzule. Dotaz vrátí jenom ty výsledky, pro které podmínku určeného `Equals` splníte operátor. Jde o ekvivalent `INNER JOIN` v systému SQL.  
  
 Můžete použít více `Join` klauzule v dotazu pro připojení dvě nebo více kolekcí do jedné kolekce.  
  
 Můžete provádět na implicitní spojení kombinovat kolekce bez `Join` klauzule. Chcete-li to provést, obsahovat více `In` klauzule v vaše `From` klauzule a zadejte `Where` klauzuli, která identifikuje klíčů, které chcete použít pro spojení.  
  
 Můžete použít `Group Join` klauzule kombinování kolekcí do jedné hierarchické kolekce. Toto je třeba `LEFT OUTER JOIN` v systému SQL.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu provede na implicitní spojení kombinovat seznamu zákazníků jejich objednávky.  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu spojí dvě kolekce pomocí `Join` klauzule.  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 Tento příklad vytvoří výstup podobný následujícímu:  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu spojí dvě kolekce pomocí `Join` klauzuli with dvě klíčové sloupce.  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 Tento příklad vytvoří výstup podobný následujícímu:  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Dotazy](../../../visual-basic/language-reference/queries/queries.md)  
 [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Klauzule Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
