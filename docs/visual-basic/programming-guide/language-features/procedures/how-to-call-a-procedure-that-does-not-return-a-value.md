---
title: 'Postupy: Volání procedury, která nevrací hodnotu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
ms.openlocfilehash: 6e3ce2a184ca5411a6a016929a16bf3d67e669ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864231"
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>Postupy: Volání procedury, která nevrací hodnotu (Visual Basic)
A `Sub` procedury nesmí vracet hodnotu volajícímu kódu. Zavoláte ji explicitně pomocí samostatné volání příkazu. Nelze volat ho jednoduše pomocí jeho názvu ve výrazu.  
  
### <a name="to-call-a-sub-procedure"></a>Chcete-li volat proceduru Sub  
  
1. Zadejte název `Sub` postup.  
  
2. Použijte název procedury se závorkami uvést seznam argumentů. Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky. Však pomocí závorek díky váš kód lépe čitelný.  
  
3. Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami. Je nutné zadat argumenty ve stejném pořadí, které `Sub` procedura definuje odpovídající parametry.  
  
     Následující příklad volá jazyka Visual Basic <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> funkce k aktivaci okna aplikace. <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> Titulek okna přijímá jako její jediný argument. Nevrací hodnotu volajícímu kódu. Pokud není spuštěný proces Poznámkový blok, příklad vyvolá <xref:System.ArgumentException>. `Shell` Postup předpokládá, že jsou aplikace v zadaných cest.  
  
     [!code-vb[VbVbalrCatRef#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCatRef/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Interaction.Shell%2A>
- <xref:System.ArgumentException>
- [Procedury](./index.md)
- [Procedury Sub](./sub-procedures.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Příkaz Sub](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [Postupy: Vytvoření procedury](./how-to-create-a-procedure.md)
- [Postupy: Volání procedury, která vrací hodnotu](./how-to-call-a-procedure-that-returns-a-value.md)
- [Postupy: Volání obslužné rutiny událostí v jazyce Visual Basic](./how-to-call-an-event-handler.md)
