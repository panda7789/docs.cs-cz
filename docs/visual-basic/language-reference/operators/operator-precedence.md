---
title: Priorita operátorů
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: eef6314f5fc1f5a7fffa7997559f697130f6f755
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401443"
---
# <a name="operator-precedence-in-visual-basic"></a>Priorita operátorů v jazyce Visual Basic
Když ve výrazu dojde k několika operacím, každá část je vyhodnocena a vyřešena v předem určeném pořadí s názvem *Priorita operátora*.

## <a name="precedence-rules"></a>Pravidla priorit
 Když výrazy obsahují operátory z více než jedné kategorie, vyhodnotí se podle následujících pravidel:

- Operátory aritmetické a zřetězení mají pořadí priority popsané v následující části a všechny mají větší prioritu než porovnání, logické a bitové operátory.

- Všechny operátory porovnání mají stejnou přednost a všechny mají větší prioritu než logické a bitové operátory, ale nižší prioritu než operátory aritmetické a zřetězení.

- Logické a bitové operátory mají pořadí priority popsané v následující části a všechny mají nižší prioritu než aritmetické operátory, zřetězení a porovnání.

- Operátory s stejnou prioritou jsou vyhodnocovány zleva doprava v pořadí, ve kterém jsou uvedeny ve výrazu.

## <a name="precedence-order"></a>Pořadí priority
 Operátory jsou vyhodnocovány v následujícím pořadí podle priority:

### <a name="await-operator"></a>Await – operátor
 Await

### <a name="arithmetic-and-concatenation-operators"></a>Operátory aritmetického operátoru and zřetězení
 Umocnění ( `^` )

 Unární identita a negace ( `+` , `–` )

 Násobení a dělení plovoucí desetinné čárky ( `*` , `/` )

 Celočíselné dělení ( `\` )

 Modulární aritmetická operace ( `Mod` )

 Sčítání a odčítání ( `+` , `–` )

 Zřetězení řetězců ( `&` )

 Aritmetický přenosový posun ( `<<` , `>>` )

### <a name="comparison-operators"></a>Operátory porovnání
 Všechny operátory porovnání ( `=` , `<>` , `<` , `<=` , `>` , `>=` , `Is` , `IsNot` , `Like` , `TypeOf` ... `Is` )

### <a name="logical-and-bitwise-operators"></a>Logické a bitové operátory
 Negace ( `Not` )

 Spojení ( `And` , `AndAlso` )

 Celková odvýšení ( `Or` , `OrElse` )

 Exkluzivní disjunkení ( `Xor` )

### <a name="comments"></a>Komentáře
 `=`Operátor je pouze operátor porovnání rovnosti, nikoli operátor přiřazení.

 Operátor zřetězení řetězce ( `&` ) není aritmetickým operátorem, ale v prioritě je seskupen s aritmetickými operátory.

 `Is`Operátory a `IsNot` jsou operátory porovnání odkazů na objekty. Nerovnávají hodnoty dvou objektů; kontrolují pouze k určení, zda dvě proměnné objektu odkazují na stejnou instanci objektu.

## <a name="associativity"></a>Asociativita
 Pokud se operátory stejné priority zobrazí společně ve výrazu, například násobení a dělení, kompilátor vyhodnotí každou operaci jako v případě, že ji narazí zleva doprava. Toto dokládá následující příklad.

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 První výraz vyhodnotí divizi 96/8 (což má za následek 12) a potom rozdělením 12/4, které má za následek tři. Vzhledem k tomu, že kompilátor vyhodnocuje operace `n1` od zleva doprava, je vyhodnocení stejné, pokud je pořadí explicitně určeno pro `n2` . `n1`A `n2` mají výsledek tři. Naproti tomu `n3` má výsledek 48, protože kulaté závorky vynutí, aby kompilátor vyhodnotil 8/4 jako první.

 Z důvodu tohoto chování jsou operátory označeny jako *asociativní* v Visual Basic.

## <a name="overriding-precedence-and-associativity"></a>Přepsání priority a asociativita
 Pomocí závorek můžete vynutit, aby některé části výrazu byly vyhodnoceny před jinými. To může přepsat pořadí priorit i levou asociativita. Visual Basic vždy provádí operace, které jsou uzavřeny v závorkách před těmito objekty mimo. V závorkách však udržuje běžnou prioritu a asociativita, pokud v závorkách nepoužíváte závorky. Toto dokládá následující příklad.

```vb
Dim a, b, c, d, e, f, g As Double
a = 8.0
b = 3.0
c = 4.0
d = 2.0
e = 1.0
f = a - b + c / d * e
' The preceding line sets f to 7.0. Because of natural operator
' precedence and associativity, it is exactly equivalent to the
' following line.
f = (a - b) + ((c / d) * e)
' The following line overrides the natural operator precedence
' and left associativity.
g = (a - (b + c)) / (d * e)
' The preceding line sets g to 0.5.
```

## <a name="see-also"></a>Viz také

- [= – Operátor](assignment-operator.md)
- [Is – operátor](is-operator.md)
- [IsNot – operátor](isnot-operator.md)
- [Like – operátor](like-operator.md)
- [TypeOf – operátor](typeof-operator.md)
- [Await – operátor](await-operator.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Operátory a výrazy](../../programming-guide/language-features/operators-and-expressions/index.md)
