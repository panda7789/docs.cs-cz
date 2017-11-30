---
title: "Postupy: Definice operátora převodu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0f9e63ba039a48226186fa4ce118d3e47b5673e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Postupy: Definice operátora převodu (Visual Basic)
Pokud jste definovali třídu nebo strukturu, můžete definovat operátor převodu typu mezi typ třídu nebo strukturu a jiný datový typ (například `Integer`, `Double`, nebo `String`).  
  
 Převod typů jako definovat [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) postup v rámci třídu nebo strukturu. Musí být všechny postupy převod `Public Shared`, a každé z nich musí být buď [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) nebo [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje operátory převodu mezi strukturu s názvem `digit` a `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 Můžete otestovat strukturu `digit` následujícím kódem.  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Procedury operátoru](./operator-procedures.md)  
 [Postupy: definice operátora](./how-to-define-an-operator.md)  
 [Postupy: volání procedury operátora](./how-to-call-an-operator-procedure.md)  
 [Postupy: použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md)  
 [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Structure – příkaz](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Postupy: definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
