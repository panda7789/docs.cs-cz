---
title: "Postupy: Stahování souboru na pozadí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 875ad9a17078865c526770587d36b1db1adf378c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-download-a-file-in-the-background"></a>Postupy: Stahování souboru na pozadí
Stažení souboru je běžné úlohy a je často užitečné ke spuštění této operace může trvat delší dobu na samostatné vlákno. Použití <xref:System.ComponentModel.BackgroundWorker> součást k provedení této úlohy s kódem velmi malé.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat <xref:System.ComponentModel.BackgroundWorker> součást se načíst soubor XML z adresy URL. Když uživatel klikne **Stáhnout** tlačítko <xref:System.Windows.Forms.Control.Click> volání obslužné rutiny událostí <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metodu <xref:System.ComponentModel.BackgroundWorker> součásti spustit operaci stahování. Tlačítko je zakázána dobu stahování a povolena po dokončení stahování. A <xref:System.Windows.Forms.MessageBox> zobrazí obsah souboru.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 **Stahování souboru**  
  
 Soubor se stáhne na <xref:System.ComponentModel.BackgroundWorker> součásti pracovní vlákno, který se spouští <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události. Tento přístup z více vláken spustí, když váš kód zavolá <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metoda.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 **BackgroundWorker – ukončíte čekání**  
  
 `downloadButton_Click` Obslužné rutiny události ukazuje, jak čekat <xref:System.ComponentModel.BackgroundWorker> součást dokončení asynchronní úkolu.  
  
 Pokud má aplikace reakce na události jenom a nechcete provádět v hlavní vlákno žádné operace, a počkat na dokončení vlákně na pozadí, ukončete právě obslužná rutina.  
  
 Pokud chcete pokračovat, pracuje v hlavní vlákno, použijte <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> vlastnosti k určení zda <xref:System.ComponentModel.BackgroundWorker> vlákno je stále spuštěná. V příkladu se aktualizuje indikátor průběhu během zpracování stahování. Volejte <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metoda zachovat reagující uživatelské rozhraní.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 **Zobrazení výsledek**  
  
 `backgroundWorker1_RunWorkerCompleted` Metoda zpracovává <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí a je volána po dokončení operace na pozadí. Tato metoda nejprve zkontroluje <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> vlastnost. Pokud <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> je `null`, pak tato metoda zobrazí obsah souboru. Umožňuje klikněte na tlačítko Stáhnout, který byl zakázán, když zahájil stahování, a obnoví indikátor průběhu.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení System.Drawing System.Windows.Forms a System.Xml.  
  
 Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Robustní programování  
 Vždy zkontrolujte <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> vlastnost v vaší <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události před pokusem o přístup <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> vlastnost nebo jakýkoliv jiný objekt, který může mít byl ovlivněn <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Postupy: Spuštění operace na pozadí](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Postupy: Implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
