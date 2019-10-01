---
title: < < = – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: aae71069bdcb88efa5842526dd7eb47806f248d0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701111"
---
# <a name="-operator-visual-basic"></a>\< @ no__t-1 = – operátor (Visual Basic)
Provede aritmetický levý posun na hodnotu proměnné nebo vlastnosti a přiřadí výsledek zpátky proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Proměnná nebo vlastnost integrálního typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` nebo `ULong`).  
  
 `amount`  
 Požadováno. Číselný výraz datového typu, který se rozšíří na `Integer`.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně operátoru `<<=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Operátor `<<=` nejprve provede Aritmetický posun vlevo od hodnoty proměnné nebo vlastnosti. Operátor potom přiřadí výsledek této operace zpátky k této proměnné nebo vlastnosti.  
  
 Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci. V aritmetickém levém Shift se bity, které přesahují rozsah výsledných dat, zahodí a bitové pozice uvolněné na pravé straně mají nastavenou hodnotu nula.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor < <](../../../visual-basic/language-reference/operators/left-shift-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má operand typ této třídy nebo struktury. Přetížení operátoru `<<` má vliv na chování operátoru `<<=`. Pokud váš kód používá `<<=` na třídě nebo struktuře, která přetěžuje `<<`, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `<<=` k posunu bitového vzoru proměnné `Integer` vlevo o zadanou hodnotu a přiřazení výsledku proměnné.  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Viz také:

- [Operátor <<](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operátory bitového posunu](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
