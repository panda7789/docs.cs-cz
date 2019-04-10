---
title: 'Postupy: Vytvořit proceduru, která vrací hodnotu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 115c1df4bd49d5848d72c4cbd0242a49a12740c7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335495"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Postupy: Vytvořit proceduru, která vrací hodnotu (Visual Basic)
Můžete použít `Function` postup, který vrací hodnotu volajícímu kódu.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Chcete-li vytvořit proceduru, která vrací hodnotu  
  
1. Mimo všechny procedury, použijte `Function` příkazu, za nímž následuje `End Function` příkazu.  
  
2. V `Function` prohlášení, postupujte `Function` – klíčové slovo s názvem podle postupu a seznam parametrů v závorkách.  
  
3. Postupujte podle závorek s `As` klauzule zadejte datový typ vrácené hodnoty.  
  
4. Umístit příkazy kódu podle postupu mezi `Function` a `End Function` příkazy.  
  
5. Použití `Return` příkazu vrátí hodnotu volajícímu kódu.  
  
     Následující `Function` postup vypočítá nejdelší strana nebo přepony pravoúhlého trojúhelníku, pro obě strany zadané hodnoty.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     Následující příklad ukazuje typické volání `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury Property](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Function – příkaz](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Postupy: Vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Postupy: Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
