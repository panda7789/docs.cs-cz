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
ms.openlocfilehash: cad021c7730782d6233c60841483df7173308dc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351997"
---
# <a name="-operator-visual-basic"></a>> > = – operátor (Visual Basic)
Provede aritmetický pravý posun na hodnotu proměnné nebo vlastnosti a přiřadí výsledek zpátky proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Proměnná nebo vlastnost integrálního typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`nebo `ULong`).  
  
 `amount`  
 Požadováno. Číselný výraz datového typu, který se rozšíří na `Integer`.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně operátoru `>>=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Operátor `>>=` nejprve provede aritmetický pravý posun na hodnotu proměnné nebo vlastnosti. Operátor potom přiřadí výsledek této operace zpátky k proměnné nebo vlastnosti.  
  
 Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci. V aritmetickém pravém posunu se bity po pravém horním rohu zahodí a bit umístěný nejvíce vlevo se rozšíří do bitových pozic uvolněné vlevo. To znamená, že pokud má `variableorproperty` zápornou hodnotu, pozice uvolněné jsou nastaveny na jednu. Pokud je `variableorproperty` pozitivní, nebo pokud je jeho datový typ typu bez znaménka, pozice uvolněné jsou nastaveny na hodnotu nula.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor > >](../../../visual-basic/language-reference/operators/right-shift-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má operand typ této třídy nebo struktury. Přetížení operátoru `>>` má vliv na chování operátoru `>>=`. Pokud váš kód používá `>>=` ve třídě nebo struktuře, která přetěžuje `>>`, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `>>=` k posunutí bitového vzoru `Integer` proměnné přímo o zadanou hodnotu a přiřazení výsledku proměnné.  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Viz také:

- [>> – operátor](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operátory bitového posunu](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
