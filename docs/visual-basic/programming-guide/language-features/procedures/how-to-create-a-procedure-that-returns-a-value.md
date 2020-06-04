---
title: 'Postupy: Vytvoření procedury, která vrátí hodnotu.'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 2655aba6ce37be831d8dd4202ffd484cfd3fd5ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388346"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Postupy: Vytvoření procedury, která vrátí hodnotu (Visual Basic).
Použijte `Function` proceduru, která vrátí hodnotu volajícímu kódu.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Vytvoření procedury, která vrátí hodnotu  
  
1. Mimo jakýkoli jiný postup použijte `Function` příkaz následovaný `End Function` příkazem.  
  
2. V `Function` příkazu použijte `Function` klíčové slovo s názvem procedury a pak seznam parametrů v závorkách.  
  
3. Pomocí závorek s `As` klauzulí určete datový typ vrácené hodnoty.  
  
4. Umístěte příkazy kódu procedury mezi `Function` `End Function` příkazy a.  
  
5. Pomocí `Return` příkazu vraťte hodnotu volajícímu kódu.  
  
     Následující `Function` postup vypočítá nejdelší stranu (neboli přepony) pravého trojúhelníku s ohledem na hodnoty ostatních dvou stran.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     Následující příklad ukazuje typické volání metody `hypotenuse` .  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Function – příkaz](../../../language-reference/statements/function-statement.md)
- [Postupy: Vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Postupy. Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
