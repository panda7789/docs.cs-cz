---
title: / – operátor
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
ms.openlocfilehash: e9400b50a84522f87a9a2ea4cd05b479d7a4538e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371165"
---
# <a name="-operator-visual-basic"></a>/ – operátor (Visual Basic)
Vydělí dvě čísla a vrátí výsledek s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
expression1 / expression2  
```  
  
## <a name="parts"></a>Součásti  
 `expression1`  
 Povinná hodnota. Libovolný číselný výraz.  
  
 `expression2`  
 Povinná hodnota. Libovolný číselný výraz.  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal` .  
  
## <a name="result"></a>Výsledek  
 Výsledkem je celý podíl `expression1` dělený hodnotou `expression2` , včetně všech zbytků.  
  
 [Operátor \ (Visual Basic)](integer-division-operator.md) vrátí celočíselný podíl, který zbytek zruší.  
  
## <a name="remarks"></a>Poznámky  
 Datový typ výsledku závisí na typech operandů. Následující tabulka ukazuje, jak je určen datový typ výsledku.  
  
|Datové typy operandů|Výsledný datový typ|  
|------------------------|----------------------|  
|Oba výrazy jsou integrální datové typy ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger –](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ulong](../data-types/ulong-data-type.md)).|`Double`|  
|Jeden výraz je [jeden](../data-types/single-data-type.md) datový typ a druhý není typu [Double](../data-types/double-data-type.md) .|`Single`|  
|Jeden výraz je datový typ [Decimal](../data-types/decimal-data-type.md) a druhý není typu [Single](../data-types/single-data-type.md) nebo [Double](../data-types/double-data-type.md) .|`Decimal`|  
|Jeden z výrazů je datový typ [Double](../data-types/double-data-type.md) .|`Double`|  
  
 Před provedením dělení se rozšíří všechny celočíselné číselné výrazy na `Double` . Pokud přiřadíte výsledek celočíselnému datovému typu, Visual Basic se pokusí převést výsledek z `Double` na tento typ. To může vyvolat výjimku, pokud výsledek se nevejde do tohoto typu. Konkrétně naleznete na této stránce s touto stránkou "pokusy o dělení nulou".  
  
 Pokud `expression1` je nebo se `expression2` vyhodnotí jako [Nothing](../nothing.md), bude se zacházet jako nula.  
  
## <a name="attempted-division-by-zero"></a>Došlo k pokusu o dělení nulou.  
 Pokud je `expression2` hodnota vyhodnocena jako nula, `/` operátor se chová jinak pro různé datové typy operandů. V následující tabulce je uvedeno možné chování.  
  
|Datové typy operandů|Chování, pokud `expression2` je nula|  
|------------------------|---------------------------------------|  
|Plovoucí desetinná čárka ( `Single` nebo `Double` )|Vrátí nekonečno ( <xref:System.Double.PositiveInfinity> nebo <xref:System.Double.NegativeInfinity> ), nebo <xref:System.Double.NaN> (není číslo), pokud `expression1` je také nula.|  
|`Decimal`|Vyvolá<xref:System.DivideByZeroException>|  
|Celočíselný (podepsaný nebo nepodepsaný)|Pokus o převod zpět na celočíselný typ se vyvolá <xref:System.OverflowException> , protože integrální typy nemůžou přijmout <xref:System.Double.PositiveInfinity> , <xref:System.Double.NegativeInfinity> nebo.<xref:System.Double.NaN>|  
  
> [!NOTE]
> `/`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá `/` operátor k provádění dělení s plovoucí desetinnou čárkou. Výsledkem je podíl dvou operandů.  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 Výrazy v předchozím příkladu vrací hodnoty 2,5 a 3,333333. Všimněte si, že výsledek je vždy plovoucí desetinná čárka ( `Double` ), i když oba operandy jsou celočíselné konstanty.  
  
## <a name="see-also"></a>Viz také

- [/= – Operátor (Visual Basic)](floating-point-division-assignment-operator.md)
- [\ – Operátor (Visual Basic)](integer-division-operator.md)
- [Datové typy výsledků operátoru](data-types-of-operator-results.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Aritmetické operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
