---
title: '* Operátor'
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
ms.openlocfilehash: f1a7653fb3006ab3c9736ec168a8c5ea028f4763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409313"
---
# <a name="-operator-visual-basic"></a>* – operátor (Visual Basic)
Vynásobí dvě čísla.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a>Součásti  
  
|Pojem|Definice|  
|---|---|  
|`number1`|Povinná hodnota. Libovolný číselný výraz.|  
|`number2`|Povinná hodnota. Libovolný číselný výraz.|  
  
## <a name="result"></a>Výsledek  
 Výsledkem je produkt `number1` a `number2` .  
  
## <a name="supported-types"></a>Podporované typy  
 Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal` .  
  
## <a name="remarks"></a>Poznámky  
 Datový typ výsledku závisí na typech operandů. Následující tabulka ukazuje, jak je určen datový typ výsledku.  
  
|Datové typy operandů|Výsledný datový typ|  
|---|---|  
|Oba výrazy jsou integrální datové typy ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger –](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ulong](../data-types/ulong-data-type.md)).|Číselný datový typ, který je vhodný pro datové typy `number1` a `number2` . Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](data-types-of-operator-results.md).|  
|Oba výrazy jsou [desítkové](../data-types/decimal-data-type.md) .|`Decimal`|  
|Oba výrazy jsou [jednoduché](../data-types/single-data-type.md)|`Single`|  
|Jeden z výrazů je datový typ s plovoucí desetinnou čárkou ( `Single` nebo [Double](../data-types/double-data-type.md)), ale ne oba `Single` (Poznámka `Decimal` není datový typ s plovoucí desetinnou čárkou).|`Double`|  
  
 Pokud je výraz vyhodnocen jako [Nothing](../nothing.md), bude považován za nulu.  
  
## <a name="overloading"></a>Přetížení  
 `*`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá `*` operátor k násobení dvou čísel. Výsledkem je součin dvou operandů.  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Viz také

- [* = – Operátor](multiplication-assignment-operator.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Aritmetické operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
