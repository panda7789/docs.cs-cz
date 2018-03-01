---
title: "IsFalse – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d85fc51a75f82c65cf226b8239a8eee6585bd18a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [IsTrue – operátor](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [Postupy: definice operátora](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [AndAlso – operátor](../../../visual-basic/language-reference/operators/andalso-operator.md)
