---
title: 'Postupy: Vrácení hodnoty z procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 8b53df1634d2b9971bc44c968a17db81cac3924f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307883"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>Postupy: Vrácení hodnoty z procedury (Visual Basic)
A `Function` postup vrací hodnotu volajícímu kódu, buď pomocí provádí `Return` příkaz nebo zjištění `Exit Function` nebo `End Function` příkazu.  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Pro navrácení hodnoty návratový příkaz using  
  
1. Vložit `Return` příkaz v místě, kde se dokončí úkol podle postupu.  
  
2. Postupujte podle `Return` – klíčové slovo výrazem, který vrací hodnotu, kterou chcete vrátit na volajícím kódu.  
  
3. Můžete mít více než jeden `Return` příkaz ve stejné proceduře.  
  
     Následující `Function` postup vypočítá nejdelší strana nebo přepony pravoúhlého trojúhelníku a vrátí volajícímu kódu.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     Následující příklad ukazuje typické volání `hypotenuse`, která ukládá vrácené hodnoty.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Vrátit hodnotu pomocí Exit Function nebo End Function  
  
1. V nejméně jednom místě `Function` postupu přiřadit hodnotu pro název procedury.  
  
2. Při spuštění `Exit Function` nebo `End Function` příkazu jazyka Visual Basic vrátí hodnotu naposledy přiřazeno název procedury.  
  
3. Můžete mít více než jeden `Exit Function` příkaz v stejným způsobem a můžete kombinovat `Return` a `Exit Function` příkazy ve stejné proceduře.  
  
4. Může mít pouze jeden `End Function` výroky `Function` postup.  
  
     Další informace a příklad naleznete v části "Vrácení hodnoty" v [Function – příkaz](../../../../visual-basic/language-reference/statements/function-statement.md).  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Procedury vlastnosti](./property-procedures.md)
- [Procedury operátoru](./operator-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Function](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Return](../../../../visual-basic/language-reference/statements/return-statement.md)
- [Postupy: Vytvořit proceduru, která vrací hodnotu](./how-to-create-a-procedure-that-returns-a-value.md)
- [Postupy: Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
