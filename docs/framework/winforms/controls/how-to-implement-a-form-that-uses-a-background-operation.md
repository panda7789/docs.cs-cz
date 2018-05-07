---
title: 'Postupy: Implementace formuláře, který používá operaci na pozadí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: 5923895e1e6cf86f8de30405dbfdb0a603d708d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>Postupy: Implementace formuláře, který používá operaci na pozadí
V následujícím příkladu programu vytvoří formulář, který vypočítá Fibonacciho čísla. Výpočet běží na vlákno, která je oddělená od vlákna uživatelského rozhraní, tak uživatelské rozhraní i nadále spustit bez zpoždění, protože výpočet pokračuje.  
  
 Rozsáhlá podpora pro tuto úlohu v sadě Visual Studio není k dispozici.  
  
 Viz také [návod: implementace formuláře, který používá operaci na pozadí](http://msdn.microsoft.com/library/b2zk6580\(v=vs.110\)).  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Robustní programování  
  
> [!CAUTION]
>  Při použití jakékoli více vláken, potenciálně vystavit sami na velmi závažnou a komplexní chyby. Obrátit [spravované dělení na vlákna osvědčené postupy](../../../../docs/standard/threading/managed-threading-best-practices.md) před implementací řešení, která používá více vláken.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Přehled asynchronních vzorů založených na událostech](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Doporučené postupy dělení na spravovaná vlákna](../../../../docs/standard/threading/managed-threading-best-practices.md)
