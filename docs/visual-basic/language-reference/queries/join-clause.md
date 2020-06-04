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
ms.openlocfilehash: f73dc31bbbb9014a8a1a315de406c53fa58d1c65
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359771"
---
# <a name="join-clause-visual-basic"></a>Join – klauzule (Visual Basic)

Kombinuje dvě kolekce do jedné kolekce. Operace JOIN je založena na porovnávacích klíčích a používá `Equals` operátor.

## <a name="syntax"></a>Syntaxe

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a>Součásti

`element`Požadovanou. Řídicí proměnná pro kolekci, která je připojena.

`collection`  
Povinná hodnota. Kolekce, která se má zkombinovat s kolekcí identifikovanou na levé straně `Join` operátoru. `Join`Klauzule může být vnořena do jiné `Join` klauzule nebo v `Group Join` klauzuli.

`joinClause`  
Nepovinný parametr. Jedna nebo více dalších `Join` klauzulí pro další upřesnění dotazu.

`groupJoinClause`  
Nepovinný parametr. Jedna nebo více dalších `Group Join` klauzulí pro další upřesnění dotazu.

`key1` `Equals` `key2`  
Povinná hodnota. Identifikuje klíče pro připojené kolekce. `Equals`K porovnání klíčů z kolekcí, které jsou spojeny, je nutné použít operátor. Podmínky spojení můžete kombinovat pomocí `And` operátora k identifikaci více klíčů. `key1`musí být z kolekce na levé straně `Join` operátoru. `key2`musí být z kolekce na pravé straně `Join` operátoru.

Klíče používané v podmínce spojení mohou být výrazy, které obsahují více než jednu položku z kolekce. Každý klíčový výraz však může obsahovat pouze položky z příslušné kolekce.

## <a name="remarks"></a>Poznámky

`Join`Klauzule kombinuje dvě kolekce na základě porovnání hodnot klíčů z připojených kolekcí. Výsledná kolekce může obsahovat libovolnou kombinaci hodnot z kolekce identifikované na levé straně `Join` operátoru a kolekce identifikované v `Join` klauzuli. Dotaz vrátí pouze výsledky, pro které `Equals` je splněna podmínka určená operátorem. To je ekvivalentem `INNER JOIN` v SQL.

V dotazu můžete použít více `Join` klauzulí k propojení dvou nebo více kolekcí do jedné kolekce.

Můžete provést implicitní spojení pro kombinování kolekcí bez `Join` klauzule. Provedete to tak, `In` že zahrnete do své klauzule více klauzulí `From` a zadáte `Where` klauzuli, která identifikuje klíče, které chcete použít pro spojení.

Klauzuli můžete použít `Group Join` ke kombinování kolekcí do jedné hierarchické kolekce. To se podobá `LEFT OUTER JOIN` v SQL.

## <a name="example"></a>Příklad

Následující příklad kódu provede implicitní spojení a kombinuje seznam zákazníků se svými objednávkami.

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a>Příklad

Následující příklad kódu spojuje dvě kolekce pomocí `Join` klauzule.

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

Tento příklad vytvoří výstup podobný následujícímu:

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a>Příklad

Následující příklad kódu spojuje dvě kolekce pomocí `Join` klauzule se dvěma klíčovými sloupci.

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

Příklad vytvoří výstup podobný následujícímu:

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a>Viz také

- [Představení technologie LINQ v jazyce Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Dotazy](index.md)
- [Klauzule SELECT](select-clause.md)
- [Klauzule FROM](from-clause.md)
- [Group Join – klauzule](group-join-clause.md)
- [Klauzule WHERE](where-clause.md)
