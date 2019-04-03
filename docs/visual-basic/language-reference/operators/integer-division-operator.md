---
title: '\ – operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: 1753199e2ecf3f156b90d8c0a5cacd672397260d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828693"
---
# <a name="-operator-visual-basic"></a>\ – operátor (Visual Basic)
Provede podíl dvou čísel a vrátí celé číslo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Součásti  
 `expression1`  
 Povinný parametr. Jakýkoli číselný výraz.  
  
 `expression2`  
 Povinný parametr. Jakýkoli číselný výraz.  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typů bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je celé číslo podíl `expression1` dělený `expression2`, který zruší všechny zbývající a zachová jenom část celého čísla. To se označuje jako *zkrácení*.  
  
 Datový typ výsledku je vhodný pro datové typy číselného typu `expression1` a `expression2`. Viz "Celočíselné aritmetiky" tabulky v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
 [/ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) vrátí úplné podíl, která si zachovává zbytek v zlomkové části.  
  
## <a name="remarks"></a>Poznámky  
 Před provedením rozdělení se pokusí převést libovolný s plovoucí desetinnou čárkou číselný výraz do jazyka Visual Basic `Long`. Pokud `Option Strict` je `On`, dojde k chybě kompilátoru. Pokud `Option Strict` je `Off`, <xref:System.OverflowException> je možné, pokud je hodnota mimo rozsah [dlouhý datový typ](../../../visual-basic/language-reference/data-types/long-data-type.md). Převod na `Long` se také vztahuje *je bankovní zaokrouhlení*. Další informace najdete v tématu "Zlomkové části" [funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Pokud `expression1` nebo `expression2` vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), je považován za nulu.  
  
## <a name="attempted-division-by-zero"></a>Pokus o dělení nulou  
 Pokud `expression2` vyhodnocen jako nula, `\` vyvolá operátor <xref:System.DivideByZeroException> výjimky. To platí pro všechny číselné datové typy operandů.  
  
> [!NOTE]
>  `\` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `\` operátor dělení celého čísla. Výsledkem je celé číslo, které představuje celočíselnou podílu dvou operandů s zbytek zahodí.  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 Výrazy uvedené v předchozím příkladu vrátí hodnoty 2, 3, 33 a-22, v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [\\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [/ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
