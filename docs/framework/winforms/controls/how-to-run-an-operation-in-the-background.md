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
ms.openlocfilehash: 5ccbb6e4c09f5417f6c2766824ec7ed9722eed52
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217988"
---
# <a name="how-to-run-an-operation-in-the-background"></a>Postupy: Spuštění operace na pozadí
Pokud máte operace, která bude trvat dlouhou dobu pro dokončení, a nechcete způsobit prodlevy v uživatelském rozhraní, můžete použít <xref:System.ComponentModel.BackgroundWorker> má třída spustit operaci v jiném vlákně.  
  
 Následující příklad kódu ukazuje, jak spustit časově náročná operace na pozadí. Formulář obsahuje **Start** a **zrušit** tlačítka. Klikněte na tlačítko **Start** tlačítko Spustit asynchronní operace. Klikněte na tlačítko **zrušit** tlačítko Zastavit spuštěné asynchronní operaci. Se zobrazí výsledek každé operace <xref:System.Windows.Forms.MessageBox>.  
  
 Není k dispozici rozsáhlou podporu pro tuto úlohu v sadě Visual Studio.  
  
 Viz také [názorný postup: Spuštění operace na pozadí](walkthrough-running-an-operation-in-the-background.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Postupy: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Komponenta BackgroundWorker](backgroundworker-component.md)
