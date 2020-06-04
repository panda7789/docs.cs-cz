---
title: '>>= – operátor'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: c3afe2bcc4b9732b5afd34df1b83eaebe707b3f5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409293"
---
# <a name="-operator-visual-basic"></a>>>= – operátor (Visual Basic)
Provede aritmetický pravý posun na hodnotu proměnné nebo vlastnosti a přiřadí výsledek zpátky proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinná hodnota. Proměnná nebo vlastnost integrálního typu ( `SByte` , `Byte` , `Short` , `UShort` , `Integer` , `UInteger` , `Long` , nebo `ULong` ).  
  
 `amount`  
 Povinná hodnota. Číselný výraz datového typu, který se rozšiřuje na `Integer` .  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `>>=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).  
  
 `>>=`Operátor nejprve provede aritmetický pravý posun na hodnotu proměnné nebo vlastnosti. Operátor potom přiřadí výsledek této operace zpátky k proměnné nebo vlastnosti.  
  
 Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci. V aritmetickém pravém posunu se bity po pravém horním rohu zahodí a bit umístěný nejvíce vlevo se rozšíří do bitových pozic uvolněné vlevo. To znamená, že pokud `variableorproperty` má zápornou hodnotu, pozice uvolněné jsou nastaveny na jednu. Pokud `variableorproperty` je kladné, nebo pokud je jeho datový typ typu bez znaménka, pozice uvolněné jsou nastaveny na hodnotu nula.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor>> ](right-shift-operator.md) lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Přetížení `>>` operátoru ovlivňuje chování `>>=` operátoru. Pokud váš kód používá `>>=` pro třídu nebo strukturu, která je přetížena `>>` , ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `>>=` operátor k posunu bitového vzoru `Integer` proměnné přímo o zadanou hodnotu a k proměnné přiřadí výsledek.  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Viz také

- [Operátor>> ](right-shift-operator.md)
- [Operátory přiřazení](assignment-operators.md)
- [Operátory bitového posunu](bit-shift-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Příkazy](../../programming-guide/language-features/statements.md)
