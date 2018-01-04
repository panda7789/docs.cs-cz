---
title: "Návod: Spuštění operace na pozadí"
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
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9be47fd57e49973c0f77a069c4f3371e4f63194
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-running-an-operation-in-the-background"></a>Návod: Spuštění operace na pozadí
Pokud máte operace, která bude trvat dlouhou dobu pro dokončení, a nechcete způsobit zpoždění v uživatelském rozhraní, můžete použít <xref:System.ComponentModel.BackgroundWorker> třídy spusťte operaci na jiné vlákno.  
  
 Úplný seznam všech kód v tomto příkladu používá, najdete v části [postupy: spuštění operace na pozadí](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-run-an-operation-in-the-background"></a>Spuštění operace na pozadí  
  
1.  Pomocí svého formuláře v Návrháři formulářů Windows aktivní, přetáhněte dva <xref:System.Windows.Forms.Button> z ovládací prvky **sada nástrojů** formuláře a potom nastavte `Name` a <xref:System.Windows.Forms.Control.Text%2A> vlastnosti tlačítek podle následující tabulky.  
  
    |Tlačítko|Název|Text|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|**Start**|  
    |`button2`|`cancelBtn`|**Zrušit**|  
  
2.  Otevřete **sada nástrojů**, klikněte na tlačítko **součásti** kartě a poté přetáhněte <xref:System.ComponentModel.BackgroundWorker> součásti do formuláře.  
  
     `backgroundWorker1` Součást se zobrazí v **komponent**.  
  
3.  V **vlastnosti** nastavte <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnost `true`.  
  
4.  V **vlastnosti** klikněte na **události** tlačítko a potom dvakrát klikněte na <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> události pro vytváření obslužných rutin událostí.  
  
5.  Vložit časově náročné kódu do <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.  
  
6.  Extrahování parametry požadované operace z <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> vlastnost <xref:System.ComponentModel.DoWorkEventArgs> parametr.  
  
7.  Výsledek výpočtu pro přiřazení <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> vlastnost <xref:System.ComponentModel.DoWorkEventArgs>.  
  
     Toto je bude mít k dispozici <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  Vložení kódu pro načítání výsledek vaše operace v <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. Implementace `TimeConsumingOperation` metoda.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. V Návrháři formulářů Windows, klikněte dvakrát na `startButton` vytvořit <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.  
  
11. Volání <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metoda v <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `startButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. V Návrháři formulářů Windows, klikněte dvakrát na `cancelButton` vytvořit <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.  
  
13. Volání <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> metoda v <xref:System.Windows.Forms.Control.Click> obslužné rutiny události pro `cancelButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. V horní části souboru importujte System.ComponentModel a System.Threading – obory názvů.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. Stiskněte klávesu F6 sestavte řešení a potom stiskněte klávesu CTRL + F5 a spusťte aplikaci mimo ladicí program.  
  
> [!NOTE]
>  Pokud je stisknutím klávesy F5 aplikaci spustit v ladicím programu, výjimka vyvolána v `TimeConsumingOperation` metoda zachycení a zobrazit pomocí ladicího programu. Při spuštění aplikace mimo ladicí program, <xref:System.ComponentModel.BackgroundWorker> ošetří výjimku a ukládá ho do mezipaměti <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> vlastnost <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.  
  
1.  Klikněte na tlačítko **spustit** tlačítko Spustit asynchronní operaci a potom klikněte na **zrušit** tlačítko zastavení spuštění asynchronní operaci.  
  
     Výsledek každé operace se zobrazí v <xref:System.Windows.Forms.MessageBox>.  
  
## <a name="next-steps"></a>Další kroky  
  
-   Implementace formuláře, který sestavy průběhu jako asynchronní operaci pokračuje. Další informace najdete v tématu [postupy: implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
-   Implementujte třídu, která podporuje asynchronní vzor pro součásti. Další informace najdete v tématu [implementace asynchronního vzoru založeného na událostech](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Postupy: Implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Postupy: Spuštění operace na pozadí](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Komponenta BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
