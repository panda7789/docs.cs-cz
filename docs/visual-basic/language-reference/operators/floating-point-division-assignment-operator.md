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
ms.openlocfilehash: 48ae78630aa66ad804d539f88524c456cf805889
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371242"
---
# <a name="-operator-visual-basic"></a>/= – operátor [Visual Basic]
Vydělí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí výsledek s plovoucí desetinnou čárkou pro proměnnou nebo vlastnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinná hodnota. Jakákoli číselná proměnná nebo vlastnost.  
  
 `expression`  
 Povinná hodnota. Libovolný číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `/=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).  
  
 `/=`Operátor nejprve rozdělí hodnotu proměnné nebo vlastnosti (na levé straně operátoru) podle hodnoty výrazu (na pravé straně operátoru) (na pravé straně operátoru). Operátor potom přiřadí výsledek s plovoucí desetinnou čárkou této operace proměnné nebo vlastnosti.  
  
 Tento příkaz přiřadí `Double` hodnotu proměnné nebo vlastnosti vlevo. Pokud `Option Strict` je `On` , `variableorproperty` musí být `Double` . Pokud `Option Strict` je `Off` , Visual Basic provede implicitní převod a přiřadí výslednou hodnotu k `variableorproperty` , s možnou chybou v době běhu. Další informace naleznete v tématu [rozšiřující a zužující převody](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a [příkaz Option Strict](../statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Přetížení  
 [Operátor/(Visual Basic)](floating-point-division-operator.md) lze *přetížit, což*znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Přetížení `/` operátoru ovlivňuje chování `/=` operátoru. Pokud váš kód používá `/=` pro třídu nebo strukturu, která je přetížena `/` , ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `/=` operátor k rozdělení jedné `Integer` proměnné za sekundu a přiřazení podílu první proměnné.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Viz také

- [/– Operátor (Visual Basic)](floating-point-division-operator.md)
- [\\= – Operátor](integer-division-assignment-operator.md)
- [Operátory přiřazení](assignment-operators.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Příkazy](../../programming-guide/language-features/statements.md)
