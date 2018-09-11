---
title: 'Postupy: Stahování souboru na pozadí'
ms.date: 03/30/2017
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
ms.openlocfilehash: 2396516a0e6c9aeb9b2d64a0bf6e3974d64a5cc5
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44369053"
---
# <a name="how-to-download-a-file-in-the-background"></a>Postupy: Stahování souboru na pozadí
Stažení souboru je běžný úkol a často je užitečné k provedení této operace může trvat delší dobu na samostatném vlákně. Použití <xref:System.ComponentModel.BackgroundWorker> komponenty, které chcete provést tuto úlohu s velmi malým množstvím kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak používat <xref:System.ComponentModel.BackgroundWorker> komponenty se načíst soubor XML z adresy URL. Pokud uživatel klikne **Stáhnout** tlačítko, <xref:System.Windows.Forms.Control.Click> volání obsluhy události <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metodu <xref:System.ComponentModel.BackgroundWorker> součásti spustit operaci stahování. Tlačítka je zakázán dobu stahování a poté povoleny po dokončení stahování. A <xref:System.Windows.Forms.MessageBox> zobrazí obsah souboru.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 **Stahování souboru**  
  
 Soubor se stáhne na <xref:System.ComponentModel.BackgroundWorker> komponenty pracovní podproces, který se spouští <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události. Toto vlákno spustí, když kód volá <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 **Čekání na BackgroundWorker – dokončení**  
  
 `downloadButton_Click` Obslužné rutiny události ukazuje postup při čekání <xref:System.ComponentModel.BackgroundWorker> součást, kterou dokončit jeho asynchronní úlohu.  
  
 Pokud pouze aplikaci reagovat na události a nechcete, aby provedete jakékoli práce v hlavním vlákně, čekají na vlákně na pozadí k dokončení právě ukončení obslužné rutiny.  
  
 Pokud chcete pokračovat v provádění práce v hlavním vlákně, použijte <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> a určí, zda <xref:System.ComponentModel.BackgroundWorker> vlákna je stále spuštěn. V tomto příkladu se aktualizuje indikátor průběhu během zpracování stahování. Nezapomeňte volat <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> metoda zachovat interaktivní uživatelské rozhraní.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 **Zobrazení výsledku**  
  
 `backgroundWorker1_RunWorkerCompleted` Metoda obslužné rutiny <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí a je volána po dokončení operace na pozadí. Tato metoda nejprve zkontroluje, <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> vlastnost. Pokud <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> je `null`, pak tato metoda zobrazí obsah souboru. Pak povolí tlačítko Stáhnout, který byl zakázán, když začalo stahování, a obnoví indikátor průběhu.  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení System.Xml, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření použijeme příklad z příkazového řádku pro visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="robust-programming"></a>Robustní programování  
 Vždy zkontrolujte <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> vlastnost v vaše <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužná rutina události, než se pokusíte o přístup k <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> vlastnost nebo jakýkoli jiný objekt, který může mít byl ovlivněn <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Postupy: Spuštění operace na pozadí](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Postupy: Implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
