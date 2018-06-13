---
title: += – operátor (Visual Basic)
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
ms.openlocfilehash: f12a0560d984f871110c02f1df2c2ec42b68809b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604013"
---
# <a name="-operator-visual-basic"></a>+= – operátor (Visual Basic)
Přidá hodnotu číselného výrazu na hodnotu číselného proměnné nebo vlastnosti a výsledek přiřadí proměnné nebo vlastnosti. Můžete také použít ke zřetězení `String` výraz, který se `String` proměnné nebo vlastnost a přiřadit výsledek, který má proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Všechny číselné nebo `String` proměnné nebo vlastnosti.  
  
 `expression`  
 Požadováno. Všechny číselné nebo `String` výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `+=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole. Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `+=` Operátor přidá hodnotu jeho vpravo proměnné nebo vlastnosti na levé straně a výsledek přiřadí proměnné nebo vlastnosti na levé straně. `+=` Operátor můžete také použít ke zřetězení `String` výraz jeho vpravo `String` proměnnou nebo na jeho levé straně a přiřadit výsledek, který má proměnná, nebo vlastností na levé straně.  
  
> [!NOTE]
>  Při použití `+=` operátor, nemusí být schopní určit, zda dojde k přidání nebo řetězec zřetězení. Použití `&=` operátor řetězení odstranit nejednoznačnost a k poskytování samoobslužných dokumentů kódu.  
  
 Tento operátor přiřazení implicitně provádí, ale není zužující převody Pokud prostředí kompilace vynucuje přísné sémantiku rozšíření. Další informace o těchto převody najdete v tématu [Widening a zužující převody](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Další informace o striktní a projektovou sémantiku, najdete v části [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Pokud sémantiku projektovou jsou povoleny, `+=` operátor implicitně provádí řadu řetězec a číselné převody stejné jako ty provádí `+` operátor. Informace o těchto převody v [+ – operátor](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Přetížení  
 `+` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Přetížení `+` operátor má vliv na chování `+=` operátor. Pokud váš kód používá `+=` na třídu nebo strukturu, která přetížení `+`, ujistěte se, pochopit jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `+=` operátor kombinovat s jinou hodnotu jednu proměnnou. První část používá `+=` s číselné proměnné, které chcete přidat jednu hodnotu do jiné. Druhá část používá `+=` s `String` proměnné, které chcete zřetězit jednu hodnotu druhou. V obou případech je výsledek přiřazen první proměnné.  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 Hodnota `num1` je nyní 13 a hodnotu `str1` je nyní "103".  
  
## <a name="see-also"></a>Viz také  
 [+ – operátor](../../../visual-basic/language-reference/operators/addition-operator.md)  
 [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
