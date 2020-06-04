---
title: 'Postupy: Vrácení hodnoty z procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 917e52b711645fbf94a132216a3fa90b0dfc15b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414321"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Postupy: Vrácení hodnoty z procedury (Visual Basic)
`Function`Procedura vrátí hodnotu volajícímu kódu buď spuštěním `Return` příkazu, nebo zjištěním `Exit Function` `End Function` příkazu or.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Vrácení hodnoty pomocí příkazu return  
  
1. Vložte `Return` příkaz do místa, kde je úkol procedury dokončen.  
  
2. Sledujte `Return` klíčové slovo s výrazem, který vrací hodnotu, kterou chcete vrátit na volající kód.  
  
3. Stejný postup může mít více než jeden `Return` příkaz.  
  
     Následující `Function` postup vypočítá nejdelší stranu (nebo přepony) pravého trojúhelníku a vrátí ji do volajícího kódu.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     Následující příklad ukazuje typické volání metody `hypotenuse` , které ukládá vrácenou hodnotu.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Vrácení hodnoty pomocí funkce Exit nebo funkce end  
  
1. V alespoň jednom místě v `Function` proceduře přiřaďte hodnotu k názvu procedury.  
  
2. Když spustíte `Exit Function` `End Function` příkaz nebo, Visual Basic vrátí hodnotu, která byla naposledy přiřazena k názvu procedury.  
  
3. Stejným postupem můžete mít více než jeden `Exit Function` příkaz a můžete kombinovat `Return` a `Exit Function` příkazy stejným postupem.  
  
4. Procedura může obsahovat jenom jeden `End Function` příkaz `Function` .  
  
     Další informace a příklad naleznete v části "návratová hodnota" v [příkazu Function](../../../language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Function – příkaz](../../../language-reference/statements/function-statement.md)
- [Return – příkaz](../../../language-reference/statements/return-statement.md)
- [Postupy: Vytvoření procedury, která vrací hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)
- [Postupy. Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
