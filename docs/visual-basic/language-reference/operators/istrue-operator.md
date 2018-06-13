---
title: IsTrue – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: fc01b074d9aba245b1c55b75b841a7f195f7ec04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605144"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue – operátor (Visual Basic)
Určuje, zda je výraz `True`.  
  
 Nelze volat `IsTrue` explicitně v kódu, ale Visual Basicu kompilátoru můžete ji použít k generování kódu z `OrElse` klauzule. Pokud můžete definovat třídu nebo strukturu a potom pomocí proměnné daného typu v `OrElse` klauzule, je nutné definovat `IsTrue` na tuto třídu nebo strukturu.  
  
 Kompilátor zvažuje `IsTrue` a `IsFalse` operátory jako *odpovídá páru*. To znamená, že pokud jeden z nich definujete, je nutné také definovat jiného.  
  
## <a name="compiler-use-of-istrue"></a>IsTrue – použití kompilátoru  
 Pokud jste definovali třídu nebo strukturu, můžete použít proměnné daného typu v `For`, `If`, `Else``If`, nebo `While` prohlášení, nebo v `When` klauzule. Pokud to uděláte, vyžaduje kompilátor operátor, který převede do vašeho typu `Boolean` hodnotu, takže ho můžete otestovat podmínku. Vyhledá vhodný operátor v následujícím pořadí:  
  
1.  Rozšiřující operátora převodu z třídy nebo k strukturu `Boolean`.  
  
2.  Rozšiřující operátora převodu z třídy nebo k strukturu `Boolean?`.  
  
3.  `IsTrue` Operátor na třídu nebo strukturu.  
  
4.  Zužující převody na `Boolean?` nezahrnuje převod z `Boolean` k `Boolean?`.  
  
5.  Narrowing operátora převodu z třídy nebo k strukturu `Boolean`.  
  
 Pokud nebyly definovány žádné převod na `Boolean` nebo `IsTrue` operátor, kompilátor nevydá signál k chybě.  
  
> [!NOTE]
>  `IsTrue` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při jeho operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje obrys strukturu, která obsahuje definice pro `IsFalse` a `IsTrue` operátory.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Operátor IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [Postupy: Definice operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)
