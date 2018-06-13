---
title: '* Operátor (Visual Basic)'
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
ms.openlocfilehash: 4e2d1000afcf8951e8914335f7b5a278b49f6277
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603623"
---
# <a name="-operator-visual-basic"></a>* – operátor (Visual Basic)
Vynásobí dvou čísel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`number1`|Požadováno. Jakýkoli číselný výraz.|  
|`number2`|Požadováno. Jakýkoli číselný výraz.|  
  
## <a name="result"></a>Výsledek  
 Výsledkem je produkt `number1` a `number2`.  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.  
  
## <a name="remarks"></a>Poznámky  
 Datový typ výsledku závisí na typech operandy. Následující tabulka uvádí, jakým způsobem je určován datový typ výsledku.  
  
|Operand datové typy|Výsledek datový typ|  
|---|---|  
|Integrální datové typy jsou oba výrazy ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtů](../../../visual-basic/language-reference/data-types/byte-data-type.md), [krátké](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [celé číslo](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uinteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [dlouho](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|Číselný datový typ, který je vhodný pro datové typy `number1` a `number2`. Podívejte se na tabulky "Celočíselné aritmetiky" v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).|  
|Oba výrazy jsou [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|Oba výrazy jsou [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|Buď výraz je s plovoucí desetinnou čárkou datový typ (`Single` nebo [dvojité](../../../visual-basic/language-reference/data-types/double-data-type.md)), ale nikoli pro obě `Single` (Poznámka `Decimal` není typu data s plovoucí desetinnou čárkou)|`Double`|  
  
 Pokud je výsledkem výrazu [nic](../../../visual-basic/language-reference/nothing.md), je považován za nula.  
  
## <a name="overloading"></a>Přetížení  
 `*` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `*` operátor mají vynásobit dvou čísel. Výsledkem je produkt dva operandy.  
  
 [!code-vb[VbVbalrOperators#4](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [*= – operátor](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
