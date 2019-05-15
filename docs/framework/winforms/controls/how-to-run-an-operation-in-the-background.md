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
ms.openlocfilehash: 77f75a7eb1d7cc536df7110ef55727fbdf789f23
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591612"
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
  
- Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [Postupy: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md)
- [Komponenta BackgroundWorker](backgroundworker-component.md)
