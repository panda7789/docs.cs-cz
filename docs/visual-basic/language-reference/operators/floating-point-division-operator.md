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
ms.openlocfilehash: d30d871d48bc87e050a072cd01a38065be20616c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933263"
---
# <a name="-operator-visual-basic"></a>/ – operátor (Visual Basic)
Vydělí dvě čísla a vrátí výsledek s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a>Součásti  
 `expression1`  
 Povinný parametr. Libovolný číselný výraz.  
  
 `expression2`  
 Povinný parametr. Libovolný číselný výraz.  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal`.  
  
## <a name="result"></a>Výsledek  
 Výsledkem je celý podíl `expression1` dělený hodnotou `expression2`, včetně všech zbytků.  
  
 [Operátor \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) vrátí celočíselný podíl, který zbytek zruší.  
  
## <a name="remarks"></a>Poznámky  
 Datový typ výsledku závisí na typech operandů. Následující tabulka ukazuje, jak je určen datový typ výsledku.  
  
|Datové typy operandů|Výsledný datový typ|  
|------------------------|----------------------|  
|Oba výrazy jsou integrální datové typy ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ulong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)).|`Double`|  
|Jeden výraz je [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) datový typ a druhý není typu [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) .|`Single`|  
|Jeden výraz je datový typ [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) a druhý není typu [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) nebo [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) .|`Decimal`|  
|Jeden z výrazů je datový typ [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) .|`Double`|  
  
 Před provedením dělení se rozšíří všechny celočíselné číselné výrazy na `Double`. Pokud přiřadíte výsledek celočíselnému datovému typu, Visual Basic se pokusí převést výsledek z `Double` na tento typ. To může vyvolat výjimku, pokud výsledek se nevejde do tohoto typu. Konkrétně naleznete na této stránce s touto stránkou "pokusy o dělení nulou".  
  
 Pokud `expression1` je `expression2` nebo se vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md), bude se zacházet jako nula.  
  
## <a name="attempted-division-by-zero"></a>Došlo k pokusu o dělení nulou.  
 Pokud `expression2` je hodnota vyhodnocena jako `/` nula, operátor se chová jinak pro různé datové typy operandů. V následující tabulce je uvedeno možné chování.  
  
|Datové typy operandů|Chování, `expression2` Pokud je nula|  
|------------------------|---------------------------------------|  
|Plovoucí desetinná čárka `Double`(`Single` nebo)|Vrátí nekonečno <xref:System.Double.NegativeInfinity>(<xref:System.Double.PositiveInfinity> nebo) <xref:System.Double.NaN> , nebo (není číslo) `expression1` , pokud je také nula.|  
|`Decimal`|Vyvolá<xref:System.DivideByZeroException>|  
|Celočíselný (podepsaný nebo nepodepsaný)|Pokus o převod zpět na celočíselný typ <xref:System.OverflowException> se vyvolá, protože integrální <xref:System.Double.PositiveInfinity>typy <xref:System.Double.NegativeInfinity>nemůžou přijmout, nebo.<xref:System.Double.NaN>|  
  
> [!NOTE]
> Operátor může být přetížen, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. `/` Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se `/` používá operátor k provádění dělení s plovoucí desetinnou čárkou. Výsledkem je podíl dvou operandů.  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 Výrazy v předchozím příkladu vrací hodnoty 2,5 a 3,333333. Všimněte si, že výsledek je vždy plovoucí desetinná`Double`čárka (), i když oba operandy jsou celočíselné konstanty.  
  
## <a name="see-also"></a>Viz také:

- [/= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [Datové typy výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
