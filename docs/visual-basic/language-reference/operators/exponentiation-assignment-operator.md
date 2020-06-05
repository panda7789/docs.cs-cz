---
title: ^= – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: e631cc9a484b56ee059449ca1fbd9fc69405333d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371398"
---
# <a name="-operator-visual-basic"></a>^= – operátor (Visual Basic)
Vyvolá hodnotu proměnné nebo vlastnosti na mocninu výrazu a přiřadí výsledek zpátky proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinná hodnota. Jakákoli číselná proměnná nebo vlastnost.  
  
 `expression`  
 Povinná hodnota. Libovolný číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `^=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).  
  
 `^=`Operátor nejprve vyvolá hodnotu proměnné nebo vlastnosti (na levé straně operátoru) na mocninu hodnoty výrazu (na pravé straně operátoru). Operátor potom přiřadí výsledek této operace zpátky k proměnné nebo vlastnosti.  
  
 Visual Basic vždy provádí umocnění v [datovém typu Double](../data-types/double-data-type.md). Operandy jiného typu jsou převedeny na `Double` a výsledek je vždy `Double` .  
  
 Hodnota `expression` může být zlomková, záporná nebo obojí.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor ^](exponentiation-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má operand typ této třídy nebo struktury. Přetížení `^` operátoru ovlivňuje chování `^=` operátoru. Pokud váš kód používá `^=` pro třídu nebo strukturu, která je přetížena `^` , ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `^=` operátor k vyvolání hodnoty jedné `Integer` proměnné mocninou druhé proměnné a přiřazení výsledku první proměnné.  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Viz také

- [^ – Operátor](exponentiation-operator.md)
- [Operátory přiřazení](assignment-operators.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Příkazy](../../programming-guide/language-features/statements.md)
