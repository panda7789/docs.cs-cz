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
ms.openlocfilehash: e723667b6397fe758ae2f33babe27c0e41887aab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641171"
---
# <a name="-operator-visual-basic"></a>* – operátor (Visual Basic)
Vynásobí dvě čísla.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`number1`|Povinný parametr. Jakýkoli číselný výraz.|  
|`number2`|Povinný parametr. Jakýkoli číselný výraz.|  
  
## <a name="result"></a>Výsledek  
 Výsledkem je produkt `number1` a `number2`.  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typů bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.  
  
## <a name="remarks"></a>Poznámky  
 Datový typ výsledku závisí na typy operandů. Následující tabulka ukazuje, jak je určen datový typ výsledku.  
  
|Operand datové typy|Datový typ výsledku|  
|---|---|  
|Integrální datové typy jsou oba výrazy ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtů](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krátký](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [celé číslo](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [dlouhé](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|Číselný datový typ, který je vhodný pro datové typy `number1` a `number2`. Viz "Celočíselné aritmetiky" tabulky v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Jsou oba výrazy [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|Jsou oba výrazy [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|Buď výraz je typu s plovoucí desetinnou čárkou data (`Single` nebo [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)), ale ne obojí `Single` (Poznámka: `Decimal` se nejedná o typ s plovoucí desetinnou čárkou data)|`Double`|  
  
 Pokud je výraz vyhodnocen jako [nic](../../../visual-basic/language-reference/nothing.md), je považován za nulu.  
  
## <a name="overloading"></a>Přetížení  
 `*` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `*` operátor násobení dvou čísel. Výsledkem je součin dvou operandů.  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [*= – operátor](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
