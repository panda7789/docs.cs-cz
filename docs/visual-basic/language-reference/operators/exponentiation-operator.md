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
ms.openlocfilehash: e139becf74ae367266a23513e18d0bdbdd24cdea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371385"
---
# <a name="-operator-visual-basic"></a>^ – operátor (Visual Basic)

Umocní číslo na mocninu jiného čísla.

## <a name="syntax"></a>Syntaxe

```vb
number ^ exponent
```

## <a name="parts"></a>Součásti

`number`\
Povinná hodnota. Libovolný číselný výraz.

`exponent`\
Povinná hodnota. Libovolný číselný výraz.

## <a name="result"></a>Výsledek

Výsledek je `number` vyvolán do mocniny `exponent` , vždy jako `Double` hodnota.

## <a name="supported-types"></a>Podporované typy

`Double`. Operandy jiného typu jsou převedeny na `Double` .

## <a name="remarks"></a>Poznámky

Visual Basic vždy provádí umocnění v [datovém typu Double](../data-types/double-data-type.md).

Hodnota `exponent` může být zlomková, záporná nebo obojí.

Je-li v jednom výrazu proveden více než jeden umocnění, `^` je operátor vyhodnocen tak, jak je zjištěn zleva doprava.

> [!NOTE]
> `^`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Příklad

Následující příklad používá `^` operátor k vyvolání čísla mocninou exponentu. Výsledkem je první operand vyvolaný mocninou sekundy.

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

Předchozí příklad vytvoří následující výsledky:

`exp1`je nastavené na 4 (2 čtvercové).

`exp2`hodnota je nastavená na 19683 (3 na třetí a pak na třetí).

`exp3`je nastavená na-125 (-5 na třetí).

`exp4`je nastavené na 625 (-5 až čtvrtého výkonu).

`exp5`je nastavené na 2 (kořen datové krychle 8).

`exp6`je nastaven na 0,5 (1,0 dělený kořenem datové krychle 8).

Všimněte si důležitosti závorek ve výrazech v předchozím příkladu. Z důvodu *přednosti operátoru*Visual Basic obvykle provádí `^` operátor před jakýmkoli jiným, i unárním `–` operátorem. Pokud `exp4` a `exp6` byl vypočten bez závorek, byly vytvořeny následující výsledky:

`exp4 = -5 ^ 4`vypočítá se jako – (5 až čtvrtého výkonu), což by vedlo k-625.

`exp6 = 8 ^ -1.0 / 3.0`vypočítá se jako (8 na-1 výkon nebo 0,125) dělený 3,0, což by vedlo k 0.041666666666666666666666666666667.

## <a name="see-also"></a>Viz také

- [^ = – Operátor](exponentiation-assignment-operator.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Aritmetické operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
