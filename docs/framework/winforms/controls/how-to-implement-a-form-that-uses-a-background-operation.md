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
ms.openlocfilehash: 8f348097223d2db4c54d9ecbba89eb8d179b6680
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404533"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a>Postupy: Implementace formuláře, který používá operaci na pozadí
Následující ukázkový program vytvoří formulář, který vypočítá Fibonacciho čísla. Výpočet běží na vlákně, které je oddělené od vlákně uživatelského rozhraní, takže uživatelské rozhraní i nadále běžel bez zpoždění při výpočtu pokračuje.  
  
 Není k dispozici rozsáhlou podporu pro tuto úlohu v sadě Visual Studio.  
  
 Viz také [návod: implementace formuláře, který používá operaci na pozadí](https://msdn.microsoft.com/library/b2zk6580\(v=vs.110\)).  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Robustní programování  
  
> [!CAUTION]
>  Pokud používáte multithreading jakéhokoli druhu, potenciálně zpřístupníte sami velmi závažných a složitých chyb. Poraďte [spravovaných vláken osvědčené postupy](../../../../docs/standard/threading/managed-threading-best-practices.md) před implementací jakéhokoli řešení, které používá multithreading.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Přehled asynchronních vzorů založených na událostech](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Doporučené postupy dělení na spravovaná vlákna](../../../../docs/standard/threading/managed-threading-best-practices.md)
