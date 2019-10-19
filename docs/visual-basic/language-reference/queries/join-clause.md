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
ms.openlocfilehash: b5211d0ed3f618013dc9fe764a6d7b2db8177c26
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582298"
---
# <a name="join-clause-visual-basic"></a>Join – klauzule (Visual Basic)

Kombinuje dvě kolekce do jedné kolekce. Operace JOIN je založena na porovnávacích klíčích a používá operátor `Equals`.

## <a name="syntax"></a>Syntaxe

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a>Součásti

`element` nutné. Řídicí proměnná pro kolekci, která je připojena.

`collection`  
Požadováno. Kolekce, která se má zkombinovat s kolekcí identifikovanou na levé straně operátoru `Join` Klauzule `Join` může být vnořena v jiné klauzuli-1 `Join` nebo v klauzuli `Group Join`.

`joinClause`  
Volitelné. Jedna nebo více dalších klauzulí `Join` pro další upřesnění dotazu.

`groupJoinClause`  
Volitelné. Jedna nebo více dalších klauzulí `Group Join` pro další upřesnění dotazu.

`key1` `Equals` `key2`  
Požadováno. Identifikuje klíče pro připojené kolekce. Chcete-li porovnat klíče z kolekce, které jsou spojeny, je nutné použít operátor `Equals`. Podmínky spojení můžete kombinovat pomocí operátoru `And` k identifikaci více klíčů. `key1` musí být z kolekce na levé straně operátoru `Join`. `key2` musí být z kolekce na pravé straně operátoru `Join`.

Klíče používané v podmínce spojení mohou být výrazy, které obsahují více než jednu položku z kolekce. Každý klíčový výraz však může obsahovat pouze položky z příslušné kolekce.

## <a name="remarks"></a>Poznámky

Klauzule `Join` kombinuje dvě kolekce na základě porovnání hodnot klíčů z připojených kolekcí. Výsledná kolekce může obsahovat libovolnou kombinaci hodnot z kolekce identifikované na levé straně operátoru `Join` a kolekce identifikovaná v klauzuli `Join`. Dotaz vrátí pouze výsledky, pro které je splněna podmínka určená operátorem `Equals`. Jedná se o ekvivalent `INNER JOIN` v SQL.

V dotazu můžete použít více klauzulí `Join` a spojit dvě nebo více kolekcí do jedné kolekce.

Můžete provést implicitní spojení pro kombinování kolekcí bez klauzule `Join`. Provedete to tak, že zahrnete do klauzule `From` více klauzulí `In` a zadáte klauzuli `Where`, která identifikuje klíče, které chcete pro spojení použít.

Klauzuli `Group Join` můžete použít ke kombinování kolekcí do jedné hierarchické kolekce. Toto je jako `LEFT OUTER JOIN` v SQL.

## <a name="example"></a>Příklad

Následující příklad kódu provede implicitní spojení a kombinuje seznam zákazníků se svými objednávkami.

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a>Příklad

Následující příklad kódu spojuje dvě kolekce pomocí klauzule `Join`.

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

Tento příklad vytvoří výstup podobný následujícímu:

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a>Příklad

Následující příklad kódu spojuje dvě kolekce pomocí klauzule `Join` se dvěma klíčovými sloupci.

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

Příklad vytvoří výstup podobný následujícímu:

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](../../../visual-basic/language-reference/queries/index.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)
- [Klauzule From](../../../visual-basic/language-reference/queries/from-clause.md)
- [Klauzule Group Join](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Klauzule Where](../../../visual-basic/language-reference/queries/where-clause.md)
