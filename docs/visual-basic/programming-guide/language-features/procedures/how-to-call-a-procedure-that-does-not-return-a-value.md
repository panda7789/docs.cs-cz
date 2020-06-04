---
title: 'Postupy: Volání procedury, která nevrátí hodnotu.'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 514d6e576b9b782387840ae04dcefa00de876aa9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388735"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Postupy: Volání procedury, která nevrátí hodnotu (Visual Basic).
`Sub`Procedura nevrací hodnotu volajícímu kódu. Zavoláte ji explicitně pomocí příkazu samostatného volání. Nemůžete ji volat jednoduše pomocí jejího názvu v rámci výrazu.  
  
### <a name="to-call-a-sub-procedure"></a>Volání procedury Sub  
  
1. Zadejte název `Sub` procedury.  
  
2. Chcete-li uzavřít seznam argumentů, použijte název procedury s závorkami. Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky. Použití závorek však usnadňuje čtení kódu.  
  
3. Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami. Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém `Sub` procedura definuje odpovídající parametry.  
  
     Následující příklad volá <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> funkci Visual Basic pro aktivaci okna aplikace. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>vezme název okna jako jediný argument. Nevrací hodnotu volajícímu kódu. Pokud není proces poznámkového bloku spuštěný, příklad vyvolá <xref:System.ArgumentException> . `Shell`Procedura předpokládá, že jsou aplikace v zadaných cestách.  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Sub – příkaz](../../../language-reference/statements/sub-statement.md)
- [Postupy: Vytvoření procedury](./how-to-create-a-procedure.md)
- [Postupy. Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
- [Postupy: Volání obslužné rutiny události (Visual Basic)](./how-to-call-an-event-handler.md)
