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
ms.openlocfilehash: 17eb3eddfae3cf7c818514a2fee20f646876a6ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604520"
---
# <a name="-operator-visual-basic"></a>/ – operátor (Visual Basic)
Provede podíl dvou čísel a vrátí výsledek s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a>Součásti  
 `expression1`  
 Požadováno. Jakýkoli číselný výraz.  
  
 `expression2`  
 Požadováno. Jakýkoli číselný výraz.  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je úplná podíl `expression1` dělený `expression2`, včetně všech zbytek.  
  
 [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) vrátí celočíselný koeficient, který zahodí zbytek.  
  
## <a name="remarks"></a>Poznámky  
 Datový typ výsledku závisí na typech operandy. Následující tabulka uvádí, jakým způsobem je určován datový typ výsledku.  
  
|Operand datové typy|Výsledek datový typ|  
|------------------------|----------------------|  
|Integrální datové typy jsou oba výrazy ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtů](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krátké](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [celé číslo](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [dlouho](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|Je jeden výraz [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) datový typ a druhá není [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|Je jeden výraz [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) datový typ a druhá není [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) nebo [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|Buď výraz [dvojité](../../../visual-basic/language-reference/data-types/double-data-type.md) datový typ|`Double`|  
  
 Před dělení, jsou všechny výrazy integrálních číselné rozšířit do `Double`. Chcete-li přiřadit výsledek celočíselný datový typ, se pokusí převést výsledek z jazyka Visual Basic `Double` do daného typu. To může vyvolat výjimku, pokud výsledek nevejde do typu. Konkrétně najdete v části "Se pokusil dělení podle nula" na této stránce nápovědy.  
  
 Pokud `expression1` nebo `expression2` vyhodnotí jako [nic](../../../visual-basic/language-reference/nothing.md), je považován za nula.  
  
## <a name="attempted-division-by-zero"></a>Pokus o dělení nulou  
 Pokud `expression2` vyhodnotí na hodnotu nula, `/` operátor pracuje odlišně pro různé operand datové typy. V následující tabulce jsou uvedeny možné chování.  
  
|Operand datové typy|Chování Pokud `expression2` je nulová.|  
|------------------------|---------------------------------------|  
|S plovoucí desetinnou čárkou (`Single` nebo `Double`)|Vrátí infinity (<xref:System.Double.PositiveInfinity> nebo <xref:System.Double.NegativeInfinity>), nebo <xref:System.Double.NaN> (není číslo) Pokud `expression1` je také nula.|  
|`Decimal`|Vyvolá <xref:System.DivideByZeroException>|  
|Integrální (podepsané nebo bez znaménka)|Pokus o převod zpátky do integrální typ vyvolává <xref:System.OverflowException> protože celočíselných typů nelze přijmout <xref:System.Double.PositiveInfinity>, <xref:System.Double.NegativeInfinity>, nebo <xref:System.Double.NaN>|  
  
> [!NOTE]
>  `/` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `/` operátor provést s plovoucí desetinnou čárkou dělení. Výsledkem je podíl dva operandy.  
  
 [!code-vb[VbVbalrOperators#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-operator_1.vb)]  
  
 Výrazy v předchozím příkladu návratové hodnoty 2.5 a 3.333333. Všimněte si, že výsledkem je vždy s plovoucí desetinnou čárkou (`Double`), i když jsou oba operandy konstanty typu integer.  
  
## <a name="see-also"></a>Viz také  
 [/ = – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [Datové typy výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
