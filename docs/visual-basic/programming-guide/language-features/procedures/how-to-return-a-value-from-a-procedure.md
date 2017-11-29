---
title: "Postupy: Vrácení hodnoty z procedury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ce7aa0942be413986cb010963753447ea18cdf2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Postupy: Vrácení hodnoty z procedury (Visual Basic)
A `Function` postup vrátí hodnotu volání kódu, buď spuštěním `Return` příkaz nebo zjištění `Exit Function` nebo `End Function` příkaz.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Chcete-li vrátit hodnotu pomocí příkaz Return  
  
1.  PUT `Return` příkaz v okamžiku, kdy dokončení úlohy postup.  
  
2.  Postupujte podle `Return` – klíčové slovo s výrazem, jehož výsledkem je hodnota, kterou chcete vrátit volání kódu.  
  
3.  Můžete mít více než jednu `Return` příkaz v stejným způsobem.  
  
     Následující `Function` postup vypočítá nejdelší straně nebo přepony trojúhelníku práva a vrátí ji do volající kód.  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     Následující příklad ukazuje typické volání `hypotenuse`, která ukládá vrácené hodnoty.  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Vrácení hodnoty pomocí ukončení funkce nebo funkce End  
  
1.  Nejméně jedno místo v `Function` postupu, přiřazení a hodnota, která má název procedury.  
  
2.  Při spuštění `Exit Function` nebo `End Function` příkaz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vrátí hodnotu naposledy přiřazen název procedury.  
  
3.  Můžete mít více než jednu `Exit Function` příkaz v stejným způsobem a můžete kombinovat `Return` a `Exit Function` příkazy v stejným způsobem.  
  
4.  Může mít jen jeden `End Function` příkaz v `Function` postupu.  
  
     Další informace a příklady naleznete v tématu "Vrátí hodnotu" v [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Sub – procedury](./sub-procedures.md)  
 [Procedury vlastností](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Function – příkaz](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Return – příkaz](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [Postupy: vytvoření procedury, která vrátí hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Postupy: volání procedury, která vrátí hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
