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
ms.openlocfilehash: 7fdf5cd422cf2a4081372bc14e74ed7463393520
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979850"
---
# <a name="-operator-visual-basic"></a>+= – operátor (Visual Basic)
Přidá hodnotu číselného výrazu hodnotu číselného proměnnou nebo vlastnost a výsledek přiřadí proměnné nebo vlastnosti. Je také možné zřetězit `String` výraz, který se `String` proměnnou nebo vlastnost a přiřadit výsledek, který má proměnnou nebo vlastnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinný parametr. Všechny číselné nebo `String` proměnnou nebo vlastnost.  
  
 `expression`  
 Povinný parametr. Všechny číselné nebo `String` výrazu.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `+=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `+=` Operátor přidá hodnotu napravo na proměnnou nebo vlastnost na levé straně a výsledek přiřadí proměnné nebo vlastnosti na levé straně. `+=` Operátor je také možné zřetězit `String` výraz na jeho právo `String` proměnnou nebo vlastnost jeho vlevo a přiřadit výsledek, který má proměnnou nebo vlastnost na levé straně.  
  
> [!NOTE]
>  Při použití `+=` operátoru, nemusí být schopní určit, zda dojde k přidání nebo řetězec zřetězení. Použití `&=` operátoru pro zřetězení, chcete-li odstranit nejednoznačnost a k poskytování samoobslužných dokumentace kódu.  
  
 Tento operátor přiřazení implicitně provádí, ale není zužujících převodů, pokud prostředí kompilace Vynutí striktní sémantiku rozšíření. Další informace o tyto převody, naleznete v tématu [Widening a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Další informace o striktním a povolující sémantiku, naleznete v tématu [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Pokud jsou povoleny povolující sémantiku, `+=` operátor provádí implicitně různé řetězcové a číselné převody, které jsou stejné jako ty prováděné `+` operátor. Podrobnosti o tyto převody, naleznete v tématu [+ – operátor](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Přetížení  
 `+` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Přetížení `+` operátor má vliv na chování `+=` operátor. Pokud váš kód používá `+=` v třídě nebo struktuře, která přetížení `+`, je nutné pochopit jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `+=` operátor zkombinovat hodnoty jedné proměnné s jinou. První část používá `+=` s číselné proměnné přidat jednu hodnotu do jiné. Druhá část používá `+=` s `String` proměnné ke zřetězení jednu hodnotu druhou. V obou případech platí výsledek je přiřazen k první proměnné.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 Hodnota `num1` 13 a hodnota je nyní `str1` je nyní "103".  
  
## <a name="see-also"></a>Viz také:
- [+ – operátor](../../../visual-basic/language-reference/operators/addition-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
