---
title: 'Postupy: Vrácení hodnoty z procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 62e8a52e488247d4dfcde2a560920447abe1c182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651831"
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
  
2.  Při spuštění `Exit Function` nebo `End Function` příkazu jazyka Visual Basic, vrátí hodnotu naposledy přiřazen název procedury.  
  
3.  Můžete mít více než jednu `Exit Function` příkaz v stejným způsobem a můžete kombinovat `Return` a `Exit Function` příkazy v stejným způsobem.  
  
4.  Může mít jen jeden `End Function` příkaz v `Function` postupu.  
  
     Další informace a příklady naleznete v tématu "Vrátí hodnotu" v [funkce příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Procedury Sub](./sub-procedures.md)  
 [Procedury vlastnosti](./property-procedures.md)  
 [Procedury operátoru](./operator-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Příkaz Return](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [Postupy: Vytvoření procedury, která vrací hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)  
 [Postupy. Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
