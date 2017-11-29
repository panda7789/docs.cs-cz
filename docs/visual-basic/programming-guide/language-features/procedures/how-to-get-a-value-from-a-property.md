---
title: "Postupy: Získání hodnoty z vlastnosti (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cde5408ea09398a79a3da01ae9b2d0202c58eaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>Postupy: Získání hodnoty z vlastnosti (Visual Basic)
Můžete načíst vlastnosti na hodnotu tak, že včetně názvu vlastnosti ve výrazu.  
  
 Vlastnosti `Get` postup načte hodnotu, ale můžete explicitně ho nevolají podle názvu. Stejně, jako by použijete proměnnou, použijte vlastnost. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]Díky volání procedury vlastnosti.  
  
### <a name="to-retrieve-a-value-from-a-property"></a>K načtení hodnoty z vlastnosti  
  
1.  Pomocí názvu vlastnosti ve výrazu stejným způsobem, jako byste použili název proměnné. Můžete použít vlastnost kdekoli můžete proměnné nebo konstantní.  
  
     -nebo-  
  
     Použít následující rovná název vlastnosti (`=`) přihlásit příkazu přiřazení.  
  
     Následující příklad načte hodnotu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `Now` vlastnost implicitně volání jeho `Get` postupu.  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  Pokud vlastnost přijímá argumenty, postupujte podle názvu vlastnosti v závorkách uveďte seznam argumentů. Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách.  
  
3.  Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami. Ujistěte se, že zadáte argumenty ve stejném pořadí, vlastnost definuje odpovídajících parametrů.  
  
 Hodnota vlastnosti, na které se účastní výraz stejně jako proměnné Konstanta by nebo je uložené v proměnné nebo vlastnosti na levé straně příkazu přiřazení.  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Procedury vlastností](./property-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)  
 [Postupy: vytvoření vlastnosti](./how-to-create-a-property.md)  
 [Postupy: deklarace vlastnosti se smíšenými úrovněmi přístupu](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Postupy: volání procedury vlastnosti](./how-to-call-a-property-procedure.md)  
 [Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Postupy: vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)
