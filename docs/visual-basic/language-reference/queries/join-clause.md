---
title: Join – klauzule
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
ms.openlocfilehash: b0baca9f897a00b3c6c67699629477ff385d6ef7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353267"
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
Požadováno. Kolekce, která se má zkombinovat s kolekcí identifikovanou na levé straně operátoru `Join` Klauzule `Join` může být vnořena do jiné klauzule `Join` nebo v klauzuli `Group Join`.

`joinClause`  
Volitelná. Jedna nebo více dalších klauzulí `Join` pro další upřesnění dotazu.

`groupJoinClause`  
Volitelná. Jedna nebo více dalších klauzulí `Group Join` pro další upřesnění dotazu.

`key1` `Equals` `key2`  
Požadováno. Identifikuje klíče pro připojené kolekce. K porovnání klíčů z kolekce, které jsou spojeny, je nutné použít operátor `Equals`. Podmínky spojení můžete kombinovat pomocí operátoru `And` k identifikaci více klíčů. `key1` musí být z kolekce na levé straně operátoru `Join`. `key2` musí být z kolekce na pravé straně operátoru `Join`.

Klíče používané v podmínce spojení mohou být výrazy, které obsahují více než jednu položku z kolekce. Každý klíčový výraz však může obsahovat pouze položky z příslušné kolekce.

## <a name="remarks"></a>Poznámky

Klauzule `Join` kombinuje dvě kolekce založené na porovnání hodnot klíčů od připojených kolekcí. Výsledná kolekce může obsahovat libovolnou kombinaci hodnot z kolekce identifikované na levé straně operátoru `Join` a kolekce identifikovaná v klauzuli `Join`. Dotaz vrátí pouze výsledky, pro které je splněna podmínka určená operátorem `Equals`. Jedná se o ekvivalent `INNER JOIN` v SQL.

V dotazu můžete použít více klauzulí `Join` pro spojení dvou nebo více kolekcí do jedné kolekce.

Můžete provést implicitní spojení pro kombinování kolekcí bez klauzule `Join`. Chcete-li to provést, zahrňte do klauzule `From` více klauzulí `In` a určete klauzuli `Where`, která určuje klíče, které chcete použít pro spojení.

Klauzuli `Group Join` můžete použít ke kombinování kolekcí do jedné hierarchické kolekce. Jedná se například o `LEFT OUTER JOIN` v SQL.

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
