---
title: 'Postupy: Spuštění operace na pozadí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
ms.openlocfilehash: 7a2ce452a1e55d0b01245c4eb7f43056031b9e2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-run-an-operation-in-the-background"></a>Postupy: Spuštění operace na pozadí
Pokud máte operace, která bude trvat dlouhou dobu pro dokončení, a nechcete způsobit zpoždění v uživatelském rozhraní, můžete použít <xref:System.ComponentModel.BackgroundWorker> třídy spusťte operaci na jiné vlákno.  
  
 Následující příklad kódu ukazuje, jak spustit časově náročná operace na pozadí. Formulář má **spustit** a **zrušit** tlačítka. Klikněte **spustit** tlačítko Spustit asynchronní operace. Klikněte **zrušit** tlačítko zastavení spuštění asynchronní operaci. Výsledek každé operace se zobrazí v <xref:System.Windows.Forms.MessageBox>.  
  
 Rozsáhlá podpora pro tuto úlohu v sadě Visual Studio není k dispozici.  
  
 Viz také [návod: spuštění operace na pozadí](http://msdn.microsoft.com/library/ms233672\(v=vs.110\)).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Postupy: Implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Komponenta BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
