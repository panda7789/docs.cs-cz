---
title: / – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: af2316f92e2904eee1e8c046b34b8147e40cb513
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825063"
---
# <a name="-operator-visual-basic"></a>/ – operátor (Visual Basic)
Provede podíl dvou čísel a vrátí výsledek, s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a>Součásti  
 `expression1`  
 Povinný parametr. Jakýkoli číselný výraz.  
  
 `expression2`  
 Povinný parametr. Jakýkoli číselný výraz.  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typů bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je úplné podíl `expression1` dělený `expression2`, včetně všech zbytek.  
  
 [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) vrátí podíl celé číslo, které zbytek zahodí.  
  
## <a name="remarks"></a>Poznámky  
 Datový typ výsledku závisí na typy operandů. Následující tabulka ukazuje, jak je určen datový typ výsledku.  
  
|Operand datové typy|Datový typ výsledku|  
|------------------------|----------------------|  
|Integrální datové typy jsou oba výrazy ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtů](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krátký](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [celé číslo](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [dlouhé](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Je jeden výraz [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) datový typ a druhý není [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Je jeden výraz [desetinné](../../../visual-basic/language-reference/data-types/decimal-data-type.md) datový typ a druhý není [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) nebo [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|Buď výraz [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) datový typ|`Double`|  
  
 Před provedením rozdělení libovolný integrální číselné výrazy jsou rozšířeny na `Double`. Pokud přiřadíte výsledek celočíselný datový typ, se pokusí převést výsledek z jazyka Visual Basic `Double` k danému typu. To může vyvolat výjimku, pokud výsledek nevejde do tohoto typu. Zejména naleznete v tématu "K pokusu o dělení nulou" na tuto stránku nápovědy.  
  
 Pokud `expression1` nebo `expression2` vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), je považován za nulu.  
  
## <a name="attempted-division-by-zero"></a>Pokus o dělení nulou  
 Pokud `expression2` vyhodnocen jako nula, `/` operátor chová odlišně pro různé operand datové typy. V následující tabulce jsou uvedeny možné chování.  
  
|Operand datové typy|Chování Pokud `expression2` je nula|  
|------------------------|---------------------------------------|  
|S plovoucí desetinnou čárkou (`Single` nebo `Double`)|Vrátí nekonečno (<xref:System.Double.PositiveInfinity> nebo <xref:System.Double.NegativeInfinity>), nebo <xref:System.Double.NaN> (není číslo) Pokud `expression1` je také nula|  
|`Decimal`|Vyvolá výjimku <xref:System.DivideByZeroException>|  
|Celé číslo (podepsaný nebo nepodepsaný řetězec)|Pokus o převod zpátky na celočíselný typ vyvolá <xref:System.OverflowException> protože celočíselných typů nemůže přijmout <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, nebo <xref:System.Double.NaN>|  
  
> [!NOTE]
>  `/` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `/` operátor dělení s pohyblivou čárkou. Výsledkem je podíl dvou operandů.  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 Výrazy uvedené v předchozím příkladu vrátí hodnoty 2.5 a 3.333333. Všimněte si, že výsledek je vždy s plovoucí desetinnou čárkou (`Double`), i když jsou oba operandy konstanty typu integer.  
  
## <a name="see-also"></a>Viz také:

- [/ = – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [Datové typy výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
