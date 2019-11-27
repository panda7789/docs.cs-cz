---
title: 'Postupy: Vrácení hodnoty z procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 1371e4ed0ff28f9caf56eabf2a1bb9290edbe75c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346029"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Postupy: Vrácení hodnoty z procedury (Visual Basic)
Procedura `Function` vrátí hodnotu volajícímu kódu buď spuštěním příkazu `Return` nebo navoláním příkazu `Exit Function` nebo `End Function`.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Vrácení hodnoty pomocí příkazu return  
  
1. Vložte příkaz `Return` v místě, kde je úkol procedury dokončen.  
  
2. Použijte klíčové slovo `Return` s výrazem, který vrací hodnotu, kterou chcete vrátit na volající kód.  
  
3. Stejný postup může mít více než jeden `Return` příkaz.  
  
     Následující `Function` postup vypočítá nejdelší stranu (nebo přepony) pravého trojúhelníku a vrátí ji do volajícího kódu.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     Následující příklad ukazuje typické volání `hypotenuse`, které ukládá vrácenou hodnotu.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Vrácení hodnoty pomocí funkce Exit nebo funkce end  
  
1. Alespoň na jednom místě v `Function` proceduře přiřaďte hodnotu k názvu procedury.  
  
2. Když spustíte příkaz `Exit Function` nebo `End Function`, Visual Basic vrátí hodnotu, která byla naposledy přiřazena k názvu procedury.  
  
3. Stejný postup může mít více než jeden `Exit Function` příkaz a můžete kombinovat `Return` a `Exit Function` příkazy stejným postupem.  
  
4. V postupu `Function` může být pouze jeden příkaz `End Function`.  
  
     Další informace a příklad naleznete v části "návratová hodnota" v [příkazu Function](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Return](../../../../visual-basic/language-reference/statements/return-statement.md)
- [Postupy: Vytvoření procedury, která vrací hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)
- [Postupy. Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
