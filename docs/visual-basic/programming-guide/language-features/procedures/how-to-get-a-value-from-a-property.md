---
title: 'Postupy: Získání hodnoty z vlastnosti'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 85512d4311d3e731a2c4e129d6a01f9b3273b333
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74339827"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Postupy: Získání hodnoty z vlastnosti (Visual Basic)
You retrieve a property's value by including the property name in an expression.  
  
 The property's `Get` procedure retrieves the value, but you do not explicitly call it by name. You use the property just as you would use a variable. Visual Basic makes the calls to the property's procedures.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>To retrieve a value from a property  
  
1. Use the property name in an expression the same way you would use a variable name. You can use a property anywhere you can use a variable or a constant.  
  
     -nebo-  
  
     Use the property name following the equal (`=`) sign in an assignment statement.  
  
     The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. If the property takes arguments, follow the property name with parentheses to enclose the argument list. If there are no arguments, you can optionally omit the parentheses.  
  
3. Place the arguments in the argument list within the parentheses, separated by commas. Be sure you supply the arguments in the same order that the property defines the corresponding parameters.  
  
 The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md)
- [Postupy: Vytvoření vlastnosti](./how-to-create-a-property.md)
- [Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Postupy: Volání procedury vlastnosti](./how-to-call-a-property-procedure.md)
- [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Postupy: Vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
