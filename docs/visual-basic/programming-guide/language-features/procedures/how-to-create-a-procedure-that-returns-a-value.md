---
title: 'Postupy: Vytvoření procedury, která vrátí hodnotu.'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 218dbb52abc0100724d38d10be91ef24252d5226
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349725"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>Postupy: Vytvoření procedury, která vrátí hodnotu (Visual Basic).
K vrácení hodnoty na volající kód použijte `Function` proceduru.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>Vytvoření procedury, která vrátí hodnotu  
  
1. Mimo jakýkoli jiný postup použijte příkaz `Function` následovaný příkazem `End Function`.  
  
2. V příkazu `Function` použijte klíčové slovo `Function` s názvem procedury a pak seznam parametrů v závorkách.  
  
3. Pomocí závorek s klauzulí `As` určete datový typ vrácené hodnoty.  
  
4. Umístěte příkazy kódu procedury mezi příkazy `Function` a `End Function`.  
  
5. Použijte příkaz `Return` pro návrat hodnoty do kódu volajícího.  
  
     Následující `Function` postup vypočítá nejdelší stranu (neboli přepony) pravého trojúhelníku s ohledem na hodnoty ostatních dvou stran.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     Následující příklad ukazuje typické volání `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Postupy: Vrácení hodnoty z procedury](./how-to-return-a-value-from-a-procedure.md)
- [Postupy. Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
