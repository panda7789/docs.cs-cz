---
title: IsTrue – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 780e67cf54c0bec230d5b052b877cf97a76d3f6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641119"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue – operátor (Visual Basic)
Určuje, zda je výraz `True`.  
  
 Nejde volat `IsTrue` explicitně v kódu, ale jazyka Visual Basic jej kompilátor může použít ke generování kódu z `OrElse` klauzule. Pokud definujete třídu nebo strukturu a pak použít proměnnou daného typu v `OrElse` klauzule, je nutné definovat `IsTrue` na této třídě nebo struktuře.  
  
 Kompilátor považuje `IsTrue` a `IsFalse` operátory jako *odpovídající dvojice*. To znamená, že pokud definujete jeden z nich, musíte také definovat druhé.  
  
## <a name="compiler-use-of-istrue"></a>Použití kompilátoru IsTrue  
 Po definování třídy nebo struktury, můžete použít proměnnou daného typu v `For`, `If`, `Else If`, nebo `While` příkazu, nebo `When` klauzuli. Pokud to uděláte, kompilátor, vyžaduje operátor převede typ do `Boolean` hodnoty, aby ho mohli otestovat podmínku. Vyhledá vhodný operátor v následujícím pořadí:  
  
1.  Rozšiřující operátor převodu z třídy nebo struktury `Boolean`.  
  
2.  Rozšiřující operátor převodu z třídy nebo struktury `Boolean?`.  
  
3.  `IsTrue` Operátor v třídě nebo struktuře.  
  
4.  Zužující převody na `Boolean?` , který nevyžaduje převod z `Boolean` k `Boolean?`.  
  
5.  Zužující operátor převodu z třídy nebo struktury `Boolean`.  
  
 Pokud jste nedefinovali jakýkoli převod na `Boolean` nebo `IsTrue` operátor signály kompilátor chybu.  
  
> [!NOTE]
>  `IsTrue` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při jeho operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje osnovy strukturu, která obsahuje definice pro `IsFalse` a `IsTrue` operátory.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Operátor IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Postupy: Definovat operátor](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)
