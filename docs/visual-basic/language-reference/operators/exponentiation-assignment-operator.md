---
title: ^= – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 382e0b27c2dbf27e5acccf29f1b8d2b002cb6664
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592225"
---
# <a name="-operator-visual-basic"></a>^= – operátor (Visual Basic)
Vyvolá hodnotu proměnné nebo vlastnosti na mocninu výrazu a přiřadí výsledek zpátky proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinný parametr. Jakákoli číselná proměnná nebo vlastnost.  
  
 `expression`  
 Povinný parametr. Libovolný číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně operátoru `^=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Operátor `^=` nejprve vyvolá hodnotu proměnné nebo vlastnosti (na levé straně operátoru) na mocninu hodnoty výrazu (na pravé straně operátoru). Operátor potom přiřadí výsledek této operace zpátky k proměnné nebo vlastnosti.  
  
 Visual Basic vždy provádí umocnění v [datovém typu Double](../../../visual-basic/language-reference/data-types/double-data-type.md). Operandy jiného typu jsou převedeny na `Double` a výsledek je vždy `Double`.  
  
 Hodnota `expression` může být zlomková, záporná nebo obojí.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor ^](../../../visual-basic/language-reference/operators/exponentiation-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má operand typ této třídy nebo struktury. Přetížení operátoru `^` má vliv na chování operátoru `^=`. Pokud váš kód používá `^=` na třídě nebo struktuře, která přetěžuje `^`, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `^=` k vyvolání hodnoty jedné proměnné `Integer` na mocninu druhé proměnné a přiřazení výsledku první proměnné.  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Viz také:

- [^ – operátor](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
