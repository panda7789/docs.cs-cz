---
title: "Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels [Visual Basic], properties
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- mixed access levels
- Visual Basic code, properties
- properties [Visual Basic], access levels
- Property statement [Visual Basic], declaring mixed access levels
ms.assetid: fdbb2d97-279a-4956-b26c-cbdfbc34915a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90fe20303f6f2ed692e54e44ee8cc65897531543
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-a-property-with-mixed-access-levels-visual-basic"></a>Postupy: Deklarace vlastnosti se smíšenými úrovněmi přístupu (Visual Basic)
Pokud chcete `Get` a `Set` postupů na vlastnost, která má mít různé úrovně přístupu, můžete použít na úrovni mírnější `Property` prohlášení a více omezující úroveň buď `Get` nebo `Set` příkaz. Pokud chcete, aby určité části kódu, abyste mohli získat hodnotu vlastnosti a některé další části kódu, abyste mohli změnit hodnotu použijete u vlastnosti smíšenými úrovněmi přístupu.  
  
 Další informace o úrovních přístupu najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
### <a name="to-declare-a-property-with-mixed-access-levels"></a>Deklarace vlastnosti se smíšenými úrovněmi přístupu  
  
1.  Deklarovat vlastnost běžným způsobem a zadejte méně omezující úroveň přístupu (například `Public`) v `Property` příkaz.  
  
2.  Deklarovat buď `Get` nebo `Set` postup zadání více omezující úroveň přístupu (například `Friend`).  
  
3.  Nezadávejte procesu další úroveň přístupu. Úroveň přístupu, které jsou deklarované v předpokládá `Property` příkaz. Můžete omezit přístup jenom jeden z postupů vlastnost.  
  
     [!code-vb[VbVbcnProcedures#10](./codesnippet/VisualBasic/how-to-declare-a-property-with-mixed-access-levels_1.vb)]  
  
     V předchozím příkladu `Get` procedura nemá stejný `Protected` přístup jako vlastnost samostatně, při `Set` procedura nemá `Private` přístup. Třída odvozená z `employee` můžete přečíst `salary` hodnotu, ale jenom `employee` ho může nastavit třídy.  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Procedury vlastností](./property-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Property – příkaz](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Rozdíly mezi vlastnostmi a proměnnými v jazyce Visual Basic](./differences-between-properties-and-variables.md)  
 [Postupy: vytvoření vlastnosti](./how-to-create-a-property.md)  
 [Postupy: volání procedury vlastnosti](./how-to-call-a-property-procedure.md)  
 [Postupy: deklarace a volání výchozí vlastnosti v jazyce Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Postupy: vložení hodnoty do vlastnosti](./how-to-put-a-value-in-a-property.md)  
 [Postupy: získání hodnoty z vlastnosti](./how-to-get-a-value-from-a-property.md)
