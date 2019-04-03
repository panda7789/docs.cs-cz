---
title: IsTrue – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: cb8ad8cb4a1ec13611edfcc3de7f4b7eb33fc553
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829925"
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
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Viz také:

- [Operátor IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Postupy: Definovat operátor](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Operátor OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md)
