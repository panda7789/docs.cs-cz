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
ms.openlocfilehash: 31a6da163061b905b8ffddcfc4b44978f5cdd55e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350298"
---
# <a name="-operator-visual-basic"></a>+= – operátor (Visual Basic)
Přidá hodnotu číselného výrazu do hodnoty číselné proměnné nebo vlastnosti a přiřadí výsledek proměnné nebo vlastnosti. Lze také použít k zřetězení `String`ho výrazu s proměnnou nebo vlastností `String` a přiřazení výsledku proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Jakákoli číselná nebo `String`ová proměnná nebo vlastnost.  
  
 `expression`  
 Požadováno. Libovolný numerický nebo výraz `String`.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně operátoru `+=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Operátor `+=` přidá hodnotu na základě práva na proměnnou nebo vlastnost vlevo a výsledek přiřadí proměnné nebo vlastnosti nalevo. Operátor `+=` lze také použít k zřetězení výrazu `String` na základě jeho práva na `String` proměnnou nebo vlastnost na levé straně a přiřadit výsledek proměnné nebo vlastnosti na levé straně.  
  
> [!NOTE]
> Když použijete operátor `+=`, možná nebudete moci určit, zda dojde k přidání nebo zřetězení řetězců. Použijte operátor `&=` pro zřetězení k eliminaci nejednoznačnosti a k poskytnutí kódu pro osobní dokument.  
  
 Tento operátor přiřazení implicitně provádí rozšiřující, ale ne zužující převody, pokud prostředí kompilace vynutilo striktní sémantiku. Další informace o těchto převodech naleznete v tématu [rozšiřující a zúžené převody](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Další informace o striktní a opravňující sémantikě naleznete v tématu [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Pokud je povolená sémantika povolující, operátor `+=` implicitně provede celou řadu řetězcových a číselných převodů, které jsou stejné jako u operátorů `+`. Podrobnosti o těchto převodech naleznete v tématu [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Přetížení  
 Operátor `+` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Přetížení operátoru `+` má vliv na chování operátoru `+=`. Pokud váš kód používá `+=` ve třídě nebo struktuře, která přetěžuje `+`, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `+=` ke kombinování hodnoty jedné proměnné s jinou. První část používá `+=` s numerickými proměnnými k přidání jedné hodnoty do druhé. Druhá část používá `+=` s `String` proměnných k zřetězení jedné hodnoty s jinou. V obou případech je výsledek přiřazen první proměnné.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 Hodnota `num1` je nyní 13 a hodnota `str1` je nyní "103".  
  
## <a name="see-also"></a>Viz také:

- [+ – operátor](../../../visual-basic/language-reference/operators/addition-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
