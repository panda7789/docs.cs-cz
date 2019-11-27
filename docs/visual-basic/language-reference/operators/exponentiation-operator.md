---
title: ^ – operátor
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
ms.openlocfilehash: b9860b7b6e076fc9c0288818aa9e4f2c0fc4c356
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331110"
---
# <a name="-operator-visual-basic"></a>^ – operátor (Visual Basic)

Umocní číslo na mocninu jiného čísla.

## <a name="syntax"></a>Syntaxe

```vb
number ^ exponent
```

## <a name="parts"></a>Součásti

`number`\
Požadováno. Libovolný číselný výraz.

`exponent`\
Požadováno. Libovolný číselný výraz.

## <a name="result"></a>Výsledek

Výsledek je `number` umocněn na mocninu `exponent`, vždy jako `Double` hodnota.

## <a name="supported-types"></a>Podporované typy

`Double`. Operandy jiného typu jsou převedeny na `Double`.

## <a name="remarks"></a>Poznámky

Visual Basic vždy provádí umocnění v [datovém typu Double](../../../visual-basic/language-reference/data-types/double-data-type.md).

Hodnota `exponent` může být zlomková, záporná nebo obojí.

Je-li v jednom výrazu prováděno více než jeden umocnění, vyhodnotí se operátor `^`, protože je zjištěn zleva doprava.

> [!NOTE]
> Operátor `^` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Příklad

Následující příklad používá operátor `^` k vyvolání čísla mocninou exponentu. Výsledkem je první operand vyvolaný mocninou sekundy.

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

Předchozí příklad vytvoří následující výsledky:

`exp1` je nastavené na 4 (2 čtvercové).

`exp2` je nastavená na 19683 (3 na třetí a pak tato hodnota je třetí).

`exp3` je nastavené na-125 (-5 na třetí).

`exp4` je nastavené na 625 (-5 až čtvrtého výkonu).

`exp5` je nastavené na 2 (kořenová složka datové krychle 8).

`exp6` je nastavená na 0,5 (1,0 děleno kořenem datové krychle 8).

Všimněte si důležitosti závorek ve výrazech v předchozím příkladu. Z důvodu *přednosti operátoru*Visual Basic obvykle provádí operátor `^` před jakýmkoli jiným, a to i unární operátor `–`. Pokud byla `exp4` a `exp6` vypočítána bez závorek, byly vytvořeny následující výsledky:

`exp4 = -5 ^ 4` by se vypočítala jako – (5 až čtvrtého výkonu), což by vedlo k 625.

`exp6 = 8 ^ -1.0 / 3.0` by se vypočítala jako (8 s-1 výkonem nebo 0,125) dělenou 3,0, což by vedlo k 0.041666666666666666666666666666667.

## <a name="see-also"></a>Viz také:

- [^= – operátor](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
