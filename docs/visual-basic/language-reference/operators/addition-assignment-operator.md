---
title: += – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: c2ce384901a9f0207e8279a5a07a88600c875e7f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372204"
---
# <a name="-operator-visual-basic"></a>+= – operátor (Visual Basic)
Přidá hodnotu číselného výrazu do hodnoty číselné proměnné nebo vlastnosti a přiřadí výsledek proměnné nebo vlastnosti. Lze také použít ke zřetězení `String` výrazu s `String` proměnnou nebo vlastností a přiřazení výsledku k proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinná hodnota. Jakákoli číselná nebo `String` proměnná nebo vlastnost.  
  
 `expression`  
 Povinná hodnota. Libovolný číselný `String` výraz or.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `+=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).  
  
 `+=`Operátor přidá hodnotu na pravé straně k proměnné nebo vlastnosti vlevo a výsledek přiřadí proměnné nebo vlastnosti nalevo. `+=`Operátor lze také použít k zřetězení `String` výrazu na základě jeho práva na `String` proměnnou nebo vlastnost vlevo a přiřazení výsledku k proměnné nebo vlastnosti na levé straně.  
  
> [!NOTE]
> Při použití `+=` operátoru nemusí být možné určit, zda dojde k přidání nebo zřetězení řetězců. Použijte `&=` operátor pro zřetězení k eliminaci nejednoznačnosti a k poskytnutí kódu pro samoobslužné dokumenty.  
  
 Tento operátor přiřazení implicitně provádí rozšiřující, ale ne zužující převody, pokud prostředí kompilace vynutilo striktní sémantiku. Další informace o těchto převodech naleznete v tématu [rozšiřující a zúžené převody](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Další informace o striktní a opravňující sémantikě naleznete v tématu [Option Strict Statement](../statements/option-strict-statement.md).  
  
 Pokud je povolená sémantika povolující, `+=` operátor implicitně provede celou řadu řetězců a číselných převodů, které jsou stejné jako u `+` operátorů. Podrobnosti o těchto převodech naleznete v tématu [+ Operator](addition-operator.md).  
  
## <a name="overloading"></a>Přetížení  
 `+`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Přetížení `+` operátoru ovlivňuje chování `+=` operátoru. Pokud váš kód používá `+=` pro třídu nebo strukturu, která je přetížena `+` , ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `+=` operátor ke kombinování hodnoty jedné proměnné s jinou. První část používá `+=` s číselnými proměnnými k přidání jedné hodnoty do druhé. Druhá část používá `+=` s `String` proměnnými k zřetězení jedné hodnoty s jinou. V obou případech je výsledek přiřazen první proměnné.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 Hodnota `num1` je nyní 13 a hodnota `str1` je nyní "103".  
  
## <a name="see-also"></a>Viz také

- [+ – Operátor](addition-operator.md)
- [Operátory přiřazení](assignment-operators.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [Operátory řetězení](concatenation-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Příkazy](../../programming-guide/language-features/statements.md)
