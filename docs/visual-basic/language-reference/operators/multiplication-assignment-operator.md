---
title: '*= – operátor'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: b06ebcb4f4100a0621f52a769543c0fb24fbb4bf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401495"
---
# <a name="-operator-visual-basic"></a>*= – operátor (Visual Basic)
Vynásobí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí výsledek proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinná hodnota. Jakákoli číselná proměnná nebo vlastnost.  
  
 `expression`  
 Povinná hodnota. Libovolný číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `*=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).  
  
 `*=`Operátor nejprve vynásobí hodnotu výrazu (na pravé straně operátoru) hodnotou proměnné nebo vlastnosti (na levé straně operátoru). Operátor potom přiřadí výsledek této operace proměnné nebo vlastnosti.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor *](multiplication-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má operand typ této třídy nebo struktury. Přetížení `*` operátoru ovlivňuje chování `*=` operátoru. Pokud váš kód používá `*=` pro třídu nebo strukturu, která je přetížena `*` , ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `*=` operátor k násobení jedné `Integer` proměnné za sekundu a přiřazení výsledku první proměnné.  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Viz také

- [* – Operátor](multiplication-operator.md)
- [Operátory přiřazení](assignment-operators.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Příkazy](../../programming-guide/language-features/statements.md)
