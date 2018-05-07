---
title: IsFalse – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: e84b2162eb0763725f05bc52d5c4223d7c430b81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse – operátor (Visual Basic)
Určuje, zda je výraz `False`.  
  
 Nelze volat `IsFalse` explicitně v kódu, ale Visual Basicu kompilátoru můžete ji použít k generování kódu z `AndAlso` klauzule. Pokud můžete definovat třídu nebo strukturu a potom pomocí proměnné daného typu v `AndAlso` klauzule, je nutné definovat `IsFalse` na tuto třídu nebo strukturu.  
  
 Kompilátor zvažuje `IsFalse` a `IsTrue` operátory jako *odpovídá páru*. To znamená, že pokud jeden z nich definujete, je nutné také definovat jiného.  
  
> [!NOTE]
>  `IsFalse` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při jeho operand má typ třídy nebo struktura. Pokud váš kód používá tento operátor na takové třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje obrys strukturu, která obsahuje definice pro `IsFalse` a `IsTrue` operátory.  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Operátor IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Postupy: Definice operátoru](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [Operátor AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)
