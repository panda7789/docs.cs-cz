---
title: IsTrue – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 4b863eed8406a10b9a44d7139f8659ac5cb758ad
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349513"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue – operátor (Visual Basic)
Určuje, zda je výraz `True`.  
  
 Ve svém kódu nemůžete volat `IsTrue` explicitně, ale kompilátor Visual Basic ho může použít k vygenerování kódu z `OrElse` klauzulí. Definujete-li třídu nebo strukturu a poté použijete proměnnou typu v klauzuli `OrElse`, je nutné definovat `IsTrue` v této třídě nebo struktuře.  
  
 Kompilátor považuje operátory `IsTrue` a `IsFalse` za *spárovaný pár*. To znamená, že pokud definujete jeden z nich, musíte také definovat druhý.  
  
## <a name="compiler-use-of-istrue"></a>Použití kompilátoru true  
 Pokud jste definovali třídu nebo strukturu, můžete použít proměnnou daného typu v `For`, `If`, `Else If`nebo příkazu `While` nebo v klauzuli `When`. Pokud to uděláte, kompilátor vyžaduje operátor, který převede typ na `Boolean` hodnotu, aby mohl otestovat podmínku. Vyhledá vhodný operátor v následujícím pořadí:  
  
1. Rozšiřující operátor převodu z vaší třídy nebo struktury na `Boolean`.  
  
2. Rozšiřující operátor převodu z vaší třídy nebo struktury na `Boolean?`.  
  
3. Operátor `IsTrue` pro třídu nebo strukturu.  
  
4. Zužující převod na `Boolean?`, který nezahrnuje převod z `Boolean` na `Boolean?`.  
  
5. Zužující operátor převodu z vaší třídy nebo struktury na `Boolean`.  
  
 Pokud jste nedefinovali převod na `Boolean` nebo operátor `IsTrue`, kompilátor signalizuje chybu.  
  
> [!NOTE]
> Operátor `IsTrue` může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má jeho operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje obrys struktury, která obsahuje definice pro operátory `IsFalse` a `IsTrue`.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Viz také:

- [Operátor IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Postupy: Definice operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)
