---
title: /= – operátor
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: a8a031e968df90496a4e263ae78d47045ccdc923
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331037"
---
# <a name="-operator-visual-basic"></a>/= – operátor [Visual Basic]
Vydělí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí výsledek s plovoucí desetinnou čárkou pro proměnnou nebo vlastnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Jakákoli číselná proměnná nebo vlastnost.  
  
 `expression`  
 Požadováno. Libovolný číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně operátoru `/=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Operátor `/=` nejprve vydělí hodnotu proměnné nebo vlastnosti (na levé straně operátoru) hodnotou výrazu (na pravé straně operátoru) (na pravé straně operátoru). Operátor potom přiřadí výsledek s plovoucí desetinnou čárkou této operace proměnné nebo vlastnosti.  
  
 Tento příkaz přiřadí hodnotu `Double` pro proměnnou nebo vlastnost vlevo. Pokud je `Option Strict` `On`, `variableorproperty` musí být `Double`. Pokud je `Option Strict` `Off`, Visual Basic provede implicitní převod a přiřadí výslednou hodnotu `variableorproperty`, s možnou chybou v době běhu. Další informace naleznete v tématu [rozšiřující a zužující převody](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a [příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Přetížení  
 [Operátor/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) lze *přetížit, což*znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Přetížení operátoru `/` má vliv na chování operátoru `/=`. Pokud váš kód používá `/=` ve třídě nebo struktuře, která přetěžuje `/`, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `/=` k rozdělení jedné `Integer` proměnné za sekundu a přiřazení podílu první proměnné.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Viz také:

- [/– Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\= – operátor](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
