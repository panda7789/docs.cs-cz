---
title: '&amp; – operátor'
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
ms.openlocfilehash: d778c0c99d6d074fe8b73aaf3660074643e7e136
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371606"
---
# <a name="amp-operator-visual-basic"></a>&amp;– Operátor (Visual Basic)
Generuje řetězení řetězců dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinná hodnota. Jakékoli `String` `Object` proměnné nebo.  
  
 `expression1`  
 Povinná hodnota. Libovolný výraz s datovým typem, který se rozšiřuje na `String` .  
  
 `expression2`  
 Povinná hodnota. Libovolný výraz s datovým typem, který se rozšiřuje na `String` .  
  
## <a name="remarks"></a>Poznámky  
 Pokud datový typ nebo není `expression1` `expression2` `String` , ale rozšiřuje se na `String` , je převeden na `String` . Pokud se některý z datových typů nerozšíří na `String` , kompilátor vygeneruje chybu.  
  
 Datový typ `result` je `String` . Pokud se jeden nebo oba výrazy vyhodnotí jako [Nothing](../nothing.md) nebo pokud mají hodnotu <xref:System.DBNull.Value?displayProperty=nameWithType> , považují se za řetězec s hodnotou "".  
  
> [!NOTE]
> `&`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> Znak ampersand (&) lze také použít k identifikaci proměnných jako typu `Long` . Další informace naleznete v tématu [Type Characters](../../programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá `&` operátor k vynucení zřetězení řetězců. Výsledkem je řetězcová hodnota představující zřetězení dvou řetězcových operandů.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [&= – operátor](and-assignment-operator.md)
- [Operátory řetězení](concatenation-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Operátory řetězení v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
