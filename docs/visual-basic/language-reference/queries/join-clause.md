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
ms.openlocfilehash: 21432b95b30ae38ac2cbc9e55b5a3066f0bef665
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945285"
---
# <a name="join-clause-visual-basic"></a>Join – klauzule (Visual Basic)
Kombinuje dvě kolekce do jedné kolekce. Operace spojení je založená na shodujících se klíčích a používá `Equals` operátor.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>Součásti  
 `element`  
 Povinný parametr. Řídicí proměnná pro kolekci, je připojen.  
  
 `collection`  
 Povinný parametr. Kolekce, kterou chcete v kombinaci s kolekce vymezených na levé straně `Join` operátor. A `Join` klauzule může být vnořena v jiné `Join` klauzuli, nebo `Group Join` klauzuli.  
  
 `joinClause`  
 Volitelné. Jeden nebo více dalších `Join` klauzule pro další upřesnění dotazu.  
  
 `groupJoinClause`  
 Volitelné. Jeden nebo více dalších `Group Join` klauzule pro další upřesnění dotazu.  
  
 `key1` `Equals` `key2`  
 Povinný parametr. Určuje klíče pro kolekce, je připojen. Je nutné použít `Equals` operátor porovnání klíčů z kolekcí je připojen. Podmínky připojení můžete kombinovat pomocí `And` operátor k identifikaci více klíčů. `key1` musí být z kolekce na levé straně `Join` operátor. `key2` musí být z kolekce na pravé straně `Join` operátor.  
  
 Klíče používané v podmínku připojení může být výrazů, které obsahují více než jednu položku z kolekce. Každý výraz klíče však může obsahovat pouze položky z jeho příslušné kolekce.  
  
## <a name="remarks"></a>Poznámky  
 `Join` Klauzule kombinuje dvě kolekce na základě porovnání hodnoty klíče z kolekcí je připojen. Výsledný kolekce může obsahovat libovolnou kombinaci hodnot z kolekce vymezených na levé straně `Join` operátor a identifikovat v kolekci `Join` klauzuli. Dotaz vrátí pouze výsledky, pro které je podmínka určené `Equals` operátor je splněna. To je ekvivalentní `INNER JOIN` v SQL.  
  
 Lze použít více `Join` klauzule v dotazu pro připojení dvou nebo více kolekcí do jedné kolekce.  
  
 Můžete provést implicitní spojení kombinování kolekcí bez `Join` klauzuli. K tomuto účelu zahrnují více `In` ustanovení vaší `From` klauzule a zadejte `Where` klauzuli, která identifikuje klíče, které chcete použít pro připojení.  
  
 Můžete použít `Group Join` klauzule zkombinovat kolekce do jedné hierarchické kolekce. Podobá se trochu `LEFT OUTER JOIN` v SQL.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu provádí implicitní spojení do seznamu zákazníků v kombinaci s jejich objednávky.  
  
 [!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu spojení dvou kolekcí s použitím `Join` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]  
  
 Tento příklad vytvoří výstup podobný následujícímu:  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu spojení dvou kolekcí s použitím `Join` klauzule dvě klíčové sloupce.  
  
 [!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]  
  
 Tento příklad vytvoří výstup podobný následujícímu:  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a>Viz také:

- [Úvod do LINQ v JAZYKU Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
