---
title: IsFalse – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 9f25c406038486224c2c4708c86ef86889c44c15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013540"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse – operátor (Visual Basic)
Určuje, zda je výraz `False`.  
  
 Nejde volat `IsFalse` explicitně v kódu, ale jazyka Visual Basic jej kompilátor může použít ke generování kódu z `AndAlso` klauzule. Pokud definujete třídu nebo strukturu a pak použít proměnnou daného typu v `AndAlso` klauzule, je nutné definovat `IsFalse` na této třídě nebo struktuře.  
  
 Kompilátor považuje `IsFalse` a `IsTrue` operátory jako *odpovídající dvojice*. To znamená, že pokud definujete jeden z nich, musíte také definovat druhé.  
  
> [!NOTE]
>  `IsFalse` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při jeho operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu definuje osnovy strukturu, která obsahuje definice pro `IsFalse` a `IsTrue` operátory.  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Viz také:

- [Operátor IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Postupy: Definovat operátor](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [Operátor AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md)
