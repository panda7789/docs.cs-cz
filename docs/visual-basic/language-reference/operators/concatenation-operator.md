---
title: '&amp; Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 28d8cdb22974d77edf055ab9b2c6c767872e6783
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604299"
---
# <a name="amp-operator-visual-basic"></a>&amp; Operátor (Visual Basic)
Vytvoří spojení řetězců dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Všechny `String` nebo `Object` proměnné.  
  
 `expression1`  
 Požadováno. Jakýkoli výraz s datovým typem, který rozšiřuje na `String`.  
  
 `expression2`  
 Požadováno. Jakýkoli výraz s datovým typem, který rozšiřuje na `String`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud datový typ `expression1` nebo `expression2` není `String` ale rozšiřuje na `String`, jsou převedeny na `String`. Pokud některý z datové typy není rozšíří do `String`, kompilátor, vygeneruje se chyba.  
  
 Datový typ `result` je `String`. Pokud jeden nebo oba výrazy vyhodnocení [nic](../../../visual-basic/language-reference/nothing.md) nebo mít hodnotu <xref:System.DBNull.Value?displayProperty=nameWithType>, jsou považovány za řetězec s hodnotou "".  
  
> [!NOTE]
>  `&` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
>  Znak ampersand (&) dají použít také k identifikaci proměnné jako typ `Long`. Další informace najdete v tématu [– znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `&` operátor vynutit zřetězení řetězců. Výsledkem je řetězcovou hodnotu představující zřetězení operandy dva řetězce.  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [&= – operátor](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operátory řetězení v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
