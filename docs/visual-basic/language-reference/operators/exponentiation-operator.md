---
title: ^ – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 8cdfbec917608211e19c39eb37bd12dbc7c4d33f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592213"
---
# <a name="-operator-visual-basic"></a>^ – operátor (Visual Basic)

Umocní číslo na mocninu jiného čísla.

## <a name="syntax"></a>Syntaxe

```vb
number ^ exponent
```

## <a name="parts"></a>Součásti

`number`\
Povinný parametr. Libovolný číselný výraz.

`exponent`\
Povinný parametr. Libovolný číselný výraz.

## <a name="result"></a>Výsledek

Výsledek je `number` umocněn na mocninu `exponent`, vždy jako hodnota `Double`.

## <a name="supported-types"></a>Podporované typy

`Double`. Operandy jiného typu jsou převedeny na `Double`.

## <a name="remarks"></a>Poznámky

Visual Basic vždy provádí umocnění v [datovém typu Double](../../../visual-basic/language-reference/data-types/double-data-type.md).

Hodnota `exponent` může být zlomková, záporná nebo obojí.

Je-li v jednom výrazu proveden více než jeden umocnění, je operátor `^` vyhodnocen tak, jak byl zjištěn zleva doprava.

> [!NOTE]
> Operátor `^` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Příklad

Následující příklad používá operátor `^` k vyvolání čísla mocninou exponentu. Výsledkem je první operand vyvolaný mocninou sekundy.

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

Předchozí příklad vytvoří následující výsledky:

`exp1` je nastavené na 4 (2 čtvercové).

hodnota `exp2` je nastavená na 19683 (3 na třetí straně a pak na třetí).

hodnota `exp3` je nastavena na-125 (-5 na třetí).

hodnota `exp4` je nastavená na 625 (-5 až čtvrtého výkonu).

hodnota `exp5` je nastavena na hodnotu 2 (kořenová hodnota datové krychle 8).

hodnota `exp6` je nastavena na 0,5 (1,0 děleno kořenem datové krychle 8).

Všimněte si důležitosti závorek ve výrazech v předchozím příkladu. Z důvodu *přednosti operátoru*Visual Basic obvykle provádí operátor `^` před všemi ostatními, a to i unární operátor `–`. Pokud byla vypočítána hodnota `exp4` a `exp6` bez závorek, byly vytvořeny následující výsledky:

`exp4 = -5 ^ 4` se vypočítá jako – (5 až čtvrtého výkonu), což by vedlo k-625.

`exp6 = 8 ^ -1.0 / 3.0` by se vypočítalo jako (8 na-1 výkon nebo 0,125) dělené 3,0, což by vedlo k 0.041666666666666666666666666666667.

## <a name="see-also"></a>Viz také:

- [^= – operátor](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
