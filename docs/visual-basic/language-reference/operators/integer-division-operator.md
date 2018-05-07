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
ms.openlocfilehash: ef3946e871e1dc248b54932e16f6cae6026da08e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-visual-basic"></a>\ – operátor (Visual Basic)
Provede podíl dvou čísel a vrátí celé číslo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression1 \ expression2  
```  
  
## <a name="parts"></a>Součásti  
 `expression1`  
 Požadováno. Jakýkoli číselný výraz.  
  
 `expression2`  
 Požadováno. Jakýkoli číselný výraz.  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je celé číslo podíl `expression1` dělený `expression2`, která zruší všechny zbývající a zachová jenom ta část celé číslo. To se označuje jako *zkrácení*.  
  
 Datový typ výsledků je vhodné pro datové typy číselného typu `expression1` a `expression2`. Podívejte se na tabulky "Celočíselné aritmetiky" v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
 [/ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) vrátí úplné podílu, který uchovává zbývající v zlomkové části.  
  
## <a name="remarks"></a>Poznámky  
 Před provedením divizi, pokusí převést jakýkoli s plovoucí desetinnou čárkou číselný výraz jazyka Visual Basic `Long`. Pokud `Option Strict` je `On`, dojde k chybě kompilátoru. Pokud `Option Strict` je `Off`, <xref:System.OverflowException> je možné, pokud je hodnota mimo rozsah [dlouho datový typ](../../../visual-basic/language-reference/data-types/long-data-type.md). Převod na `Long` je také podléhají *banker je zaokrouhlení*. Další informace najdete v tématu "Zlomkové části" v [funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
  
 Pokud `expression1` nebo `expression2` vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), je považován za nula.  
  
## <a name="attempted-division-by-zero"></a>Pokus o dělení nulou  
 Pokud `expression2` vyhodnotí na hodnotu nula, `\` vyvolá operátor <xref:System.DivideByZeroException> výjimka. To platí pro všechny číselné datové typy operandy.  
  
> [!NOTE]
>  `\` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `\` operátor provést dělení celého čísla. Výsledkem je celé číslo, které představuje celé číslo podíl dva operandy zbývajícími zahozeny.  
  
 [!code-vb[VbVbalrOperators#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/integer-division-operator_1.vb)]  
  
 Výrazy v předchozím příkladu návratové hodnoty 2, 3, 33 a-22, v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [\\= – Operátor](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [/ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
