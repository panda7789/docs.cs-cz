---
title: 'Postupy: Zabránění připojení podřízené úlohy ke své nadřazené úloze'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7506a57e29b7942bd06141baa2d2b048ed998214
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937433"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Postupy: Zabránění připojení podřízené úlohy ke své nadřazené úloze
Tento dokument ukazuje, jak zabránit podřízené úloze v připojení k nadřazené úloze. Zabránění podřízené úloze, mohla připojit k nadřazené je užitečné, když voláte komponentu, která je vytvořená systémem třetích stran a také používající úlohy. Například komponenty třetích stran, která se používá <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost vytvořit <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601> objekt může způsobit problémy v kódu, pokud je dlouho běžící nebo dojde k neošetřené výjimce.  
  
## <a name="example"></a>Příklad  
 Následující příklad porovnává důsledky použití výchozích možností účinkům zabránit podřízené úloze v připojení k nadřazené. V příkladu se vytvoří <xref:System.Threading.Tasks.Task> objekt, který volá knihovnu třetí strany, který také používá <xref:System.Threading.Tasks.Task> objektu. Používá knihovnu třetí strany <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost vytvořit <xref:System.Threading.Tasks.Task> objektu. Aplikace používá <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> můžete vytvořit nadřazené úloze. Tato možnost dá pokyn modulu runtime pro odebrání <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specifikace v podřízených úloh.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Protože nadřazenou úlohu nedokončí až do dokončení všech podřízených úloh, může způsobit dlouhotrvající podřízená úloha celkové aplikace nízký výkon. V tomto příkladu Pokud aplikace používá výchozí možnosti pro vytvoření nadřazené úlohy, podřízená úloha musí dokončit předtím, než nadřazená úloha dokončí. Pokud aplikace používá <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost podřízené není připojena k nadřazené. Aplikace proto můžete provést další práce po dokončení nadřazených úloh, a předtím, než je třeba počkat na dokončení úloh podřízené.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `DenyChildAttach.cs` (`DenyChildAttach.vb` v jazyce Visual Basic), a pak spuštěním následujícího příkazu na příkazovém řádku pro vývojáře pro Visual Studio okno.  
  
 Visual C#  
  
 **csc.exe DenyChildAttach.cs**  
  
 Visual Basic  
  
 **vbc.exe DenyChildAttach.vb**  
  
## <a name="robust-programming"></a>Robustní programování  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
