---
title: '* – Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: b5b601c7604cb7ce1afaebc98b2157634a77fda4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701095"
---
# <a name="-operator-visual-basic"></a>* – operátor (Visual Basic)
Vynásobí dvě čísla.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`number1`|Požadováno. Libovolný číselný výraz.|  
|`number2`|Požadováno. Libovolný číselný výraz.|  
  
## <a name="result"></a>Výsledek  
 Výsledkem je součin `number1` a `number2`.  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal`.  
  
## <a name="remarks"></a>Poznámky  
 Datový typ výsledku závisí na typech operandů. Následující tabulka ukazuje, jak je určen datový typ výsledku.  
  
|Datové typy operandů|Výsledný datový typ|  
|---|---|  
|Oba výrazy jsou integrální datové typy ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ulong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)).|Číselný datový typ, který je vhodný pro datové typy `number1` a `number2`. Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Oba výrazy jsou [desítkové](../../../visual-basic/language-reference/data-types/decimal-data-type.md) .|`Decimal`|  
|Oba výrazy jsou [jednoduché](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|Jeden z výrazů je datový typ s plovoucí desetinnou čárkou (`Single` nebo [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)), ale ne oba `Single` (Poznámka `Decimal` není datový typ s plovoucí desetinnou čárkou).|`Double`|  
  
 Pokud je výraz vyhodnocen jako [Nothing](../../../visual-basic/language-reference/nothing.md), bude považován za nulu.  
  
## <a name="overloading"></a>Přetížení  
 Operátor `*` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá operátor `*` pro násobení dvou čísel. Výsledkem je součin dvou operandů.  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Operátor *=](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
