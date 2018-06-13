---
title: 'Postupy: Volání procedury, která nevrátí hodnotu (Visual Basic).'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: cf136f1486645d6e8e4b5856c0b1baf9e99f6c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649045"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Postupy: Volání procedury, která nevrátí hodnotu (Visual Basic).
A `Sub` postup nevrátí hodnotu kód volání. Zavoláte ji explicitně příkazem samostatné volání. Nelze volat ho jednoduše pomocí jeho názvu v rámci výrazu.  
  
### <a name="to-call-a-sub-procedure"></a>K volání Sub – procedury  
  
1.  Zadejte název `Sub` postupu.  
  
2.  Použijte název procedury v závorkách uveďte seznam argumentů. Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách. Však pomocí závorek usnadňuje kódu čtení.  
  
3.  Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami. Ujistěte se, zadejte argumenty ve stejném pořadí, `Sub` postupu definuje odpovídající parametry.  
  
     V následujícím příkladu volání jazyka Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> funkce aktivovat okna aplikace. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> vezme jako jeho jedinou argument záhlaví okna. Volání kódu nevrací hodnotu. Pokud není spuštěn proces poznámkového bloku, v příkladu vyvolá <xref:System.ArgumentException>. `Shell` Postup předpokládá, že se aplikace v zadané cesty.  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [Procedury](./index.md)  
 [Procedury Sub](./sub-procedures.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Postupy: Vytvoření procedury](./how-to-create-a-procedure.md)  
 [Postupy. Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)  
 [Postupy: volání obslužné rutiny událostí v jazyce Visual Basic](./how-to-call-an-event-handler.md)
