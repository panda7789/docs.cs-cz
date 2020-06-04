---
title: '\= – operátor'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: a546d8b0c9b3852386970f80d3da96794da2351c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370944"
---
# <a name="-operator"></a>\\= – Operátor
Vydělí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí celočíselný výsledek proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinná hodnota. Jakákoli číselná proměnná nebo vlastnost.  
  
 `expression`  
 Povinná hodnota. Libovolný číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `\=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).  
  
 `\=`Operátor rozdělí hodnotu proměnné nebo vlastnosti na levé straně hodnotou vpravo a přiřadí celočíselný výsledek proměnné nebo vlastnosti na levé straně.  
  
 Další informace o celočíselném dělení naleznete v tématu [operátor \ (Visual Basic)](integer-division-operator.md).  
  
## <a name="overloading"></a>Přetížení  
 `\`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Přetížení `\` operátoru ovlivňuje chování `\=` operátoru. Pokud váš kód používá `\=` pro třídu nebo strukturu, která je přetížena `\` , ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `\=` operátor k rozdělení jedné `Integer` proměnné za sekundu a přiřazení celého výsledku k první proměnné.  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Viz také

- [\ – Operátor (Visual Basic)](integer-division-operator.md)
- [/= – Operátor (Visual Basic)](floating-point-division-assignment-operator.md)
- [Operátory přiřazení](assignment-operators.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Příkazy](../../programming-guide/language-features/statements.md)
