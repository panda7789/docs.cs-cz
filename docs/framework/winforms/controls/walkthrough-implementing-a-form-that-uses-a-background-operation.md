---
title: 'Návod: Implementace formuláře, který používá operaci na pozadí'
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
- threading [Windows Forms], walkthroughs
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
ms.openlocfilehash: 28b1ac924fb9b6b8cbc09db62ee33c6780bee820
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542077"
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a>Návod: Implementace formuláře, který používá operaci na pozadí
Pokud máte operace, která bude trvat dlouhou dobu pro dokončení, a nechcete vaše uživatelské rozhraní (UI) přestane reagovat nebo "zablokování", můžete použít <xref:System.ComponentModel.BackgroundWorker> třída k provedení operace na jiné vlákno.  
  
 Tento návod ukazuje, jak používat <xref:System.ComponentModel.BackgroundWorker> třída provést časově náročné výpočty "v pozadí," při současném zachování reagující uživatelské rozhraní.  Pokud jste prostřednictvím, budete mít aplikaci, která vypočítá Fibonacciho čísla asynchronně. I když computing velký počet Fibonacciho může trvat, než znatelné množství času, tato prodleva nebude možné přerušit hlavního vlákna uživatelského rozhraní a formuláře budou přizpůsobivý během výpočtu.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytvoření aplikace systému Windows  
  
-   Vytváření <xref:System.ComponentModel.BackgroundWorker> do formuláře  
  
-   Přidání obslužných rutin událostí asynchronní  
  
-   Přidání sestav průběh a podpora pro zrušení  
  
 Úplný seznam všech kód v tomto příkladu používá, najdete v části [postupy: implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a nastavte formulář.  
  
#### <a name="to-create-a-form-that-uses-a-background-operation"></a>Chcete-li vytvořit formulář, který používá operaci na pozadí  
  
1.  Vytvořte projekt aplikace pro systém Windows s názvem `BackgroundWorkerExample`. Podrobnosti najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na **Form1** a vyberte **přejmenovat** z místní nabídky. Změňte název souboru `FibonacciCalculator`. Klikněte **Ano** tlačítko po zobrazení dotazu, pokud chcete přejmenovat všechny odkazy na tento element kódu '`Form1`'.  
  
3.  Přetáhněte <xref:System.Windows.Forms.NumericUpDown> řídit z **sada nástrojů** do formuláře. Nastavte <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> vlastnost `1` a <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> vlastnost `91`.  
  
4.  Přidejte dva <xref:System.Windows.Forms.Button> ovládacích prvků formuláře.  
  
5.  Přejmenujte první <xref:System.Windows.Forms.Button> řízení `startAsyncButton` a nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost `Start Async`. Přejmenujte druhý <xref:System.Windows.Forms.Button> řízení `cancelAsyncButton`a nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost `Cancel Async`. Nastavte její <xref:System.Windows.Forms.Control.Enabled%2A> vlastnost `false`.  
  
6.  Vytvoření obslužné rutiny události pro obě <xref:System.Windows.Forms.Button> ovládací prvky se <xref:System.Windows.Forms.Control.Click> události. Podrobnosti najdete v tématu [postupy: vytvoření události obslužné rutiny pomocí návrháře](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
7.  Přetáhněte <xref:System.Windows.Forms.Label> řídit z **sada nástrojů** do formuláře a přejmenujte ji `resultLabel`.  
  
8.  Přetáhněte <xref:System.Windows.Forms.ProgressBar> řídit z **sada nástrojů** do formuláře.  
  
## <a name="creating-a-backgroundworker-in-your-form"></a>Vytváření BackgroundWorker do formuláře  
 Můžete vytvořit <xref:System.ComponentModel.BackgroundWorker> pro asynchronní operace s použitím **Windows** **Návrhář formulářů**.  
  
#### <a name="to-create-a-backgroundworker-with-the-designer"></a>Chcete-li vytvořit BackgroundWorker pomocí návrháře  
  
-   Z **součásti** kartě **sada nástrojů**, přetáhněte ji <xref:System.ComponentModel.BackgroundWorker> do formuláře.  
  
## <a name="adding-asynchronous-event-handlers"></a>Přidání obslužných rutin událostí asynchronní  
 Nyní jste připraveni pro přidání obslužné rutiny události pro <xref:System.ComponentModel.BackgroundWorker> asynchronní události komponenty. Časově náročná operace, které poběží na pozadí, která vypočítá Fibonacciho čísla, nazývá pomocí jedné z těchto obslužných rutin událostí.  
  
#### <a name="to-implement-asynchronous-event-handlers"></a>Chcete-li implementovat asynchronní obslužné rutiny  
  
1.  V **vlastnosti** okně s <xref:System.ComponentModel.BackgroundWorker> komponentu vybranou, klikněte na tlačítko **události** tlačítko. Dvakrát klikněte <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> události pro vytváření obslužných rutin událostí. Další informace o tom, jak používat obslužné rutiny událostí najdete v tématu [postupy: vytvoření události obslužné rutiny pomocí návrháře](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
2.  Vytvoření nové metody, názvem `ComputeFibonacci`, do formuláře. Tato metoda nepodporuje samotnou práci a poběží na pozadí. Tento kód ukazuje implementaci rekurzivní algoritmus Fibonacciho, což je zejména neefektivní, pro větší počty trvá exponenciálnímu delší dobu pro dokončení. Použije se zde pro ilustraci, chcete-li zobrazit operace, která můžou vést k prodlevám v aplikaci.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  V <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události, přidejte volání `ComputeFibonacci` metoda. První parametr trvat, než `ComputeFibonacci` z <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> vlastnost <xref:System.ComponentModel.DoWorkEventArgs>. <xref:System.ComponentModel.BackgroundWorker> a <xref:System.ComponentModel.DoWorkEventArgs> parametry se později použije pro vytváření sestav průběh a zrušení podporují. Přiřadit návratovou hodnotou z `ComputeFibonacci` k <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> vlastnost <xref:System.ComponentModel.DoWorkEventArgs>. Bude k dispozici pro tento výsledek <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události.  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BackgroundWorker.DoWork> Obslužné rutiny události neodkazuje `backgroundWorker1` instance proměnné přímo, protože to by spojte této obslužné rutiny události pro konkrétní instanci <xref:System.ComponentModel.BackgroundWorker>. Místo toho odkaz na <xref:System.ComponentModel.BackgroundWorker> , vyvolá tato událost se zotavil z `sender` parametr. To je důležité při formuláře hostitelem více než jeden <xref:System.ComponentModel.BackgroundWorker>. Je také důležité není k manipulaci s všechny objekty uživatelského rozhraní vašeho <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události. Místo toho komunikovat s uživatelským rozhraním prostřednictvím <xref:System.ComponentModel.BackgroundWorker> události.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  V `startAsyncButton` ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události, přidat kód, který spustí asynchronní operaci.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  V <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události, přiřaďte výsledek výpočtu, která `resultLabel` ovládacího prvku.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## <a name="adding-progress-reporting-and-support-for-cancellation"></a>Přidání sestav průběh a podpora pro zrušení  
 Pro asynchronní operace, které bude trvat dlouhou dobu je často žádoucí, aby sestavy průběhu pro uživatele a uživatelům na tlačítko Storno. <xref:System.ComponentModel.BackgroundWorker> Třída poskytuje událost, která umožňuje pokládat průběh jako vaše bude pokračovat operace pozadí. Poskytuje také příznak, který umožňuje pracovní kódu ke zjištění volání <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> a přerušení sám sebe.  
  
#### <a name="to-implement-progress-reporting"></a>K implementaci průběh vytváření sestav  
  
1.  V **vlastnosti**, vyberte `backgroundWorker1`. Nastavte <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastnosti, které chcete `true`.  
  
2.  Deklarujte dvě proměnné v `FibonacciCalculator` formuláře. Ty se použije ke sledování průběhu.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  Přidání obslužné rutiny události pro <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí. V <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> obslužné rutiny události, aktualizovat <xref:System.Windows.Forms.ProgressBar> s <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> vlastnost <xref:System.ComponentModel.ProgressChangedEventArgs> parametr.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### <a name="to-implement-support-for-cancellation"></a>Jak implementovat podporu pro zrušení  
  
1.  V `cancelAsyncButton` ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události, přidat kód, který zruší asynchronní operaci.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  Následující kód fragmenty v `ComputeFibonacci` metoda sestavy průběhu a podporu zrušení.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku můžete zkompilování a spuštění aplikace Kalkulačka Fibonacciho.  
  
#### <a name="to-test-your-project"></a>K testování projektu  
  
-   Stisknutím klávesy F5 zkompilování a spuštění aplikace.  
  
     Při výpočtu běží na pozadí, zobrazí se <xref:System.Windows.Forms.ProgressBar> zobrazování průběhu výpočtu směrem k dokončení. Můžete také zrušit čekající operace.  
  
     Pro malé čísla výpočet by měl být velmi rychlé, ale pro větší čísla, měli byste vidět významnému zpoždění. Pokud zadáte hodnotu 30 nebo větší, měli byste vidět zpoždění několik sekund, v závislosti na rychlosti počítače. Hodnoty je větší než 40 může trvat minut nebo hodin výpočtu. Sice zaneprázdněn computing velký počet Fibonacciho kalkulačky, Všimněte si, že můžete volně pohyb formuláře, minimalizovat, maximalizovat a ani ji zrušit. To je proto hlavního vlákna uživatelského rozhraní nečeká na výpočtu ukončíte.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když jste implementovali formuláře, který používá <xref:System.ComponentModel.BackgroundWorker> součást provést výpočet na pozadí, můžete hledat další možnosti pro asynchronní operace:  
  
-   Použití více <xref:System.ComponentModel.BackgroundWorker> objekty pro několik souběžných operací.  
  
-   Ladění vícevláknové aplikace, najdete v tématu [postupy: použití okna vláken](/visualstudio/debugger/how-to-use-the-threads-window).  
  
-   Implementujte vlastní komponenty, která podporuje asynchronní programovací model. Další informace najdete v tématu [na základě událostí přehled asynchronních vzorů](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
    > [!CAUTION]
    >  Při použití jakékoli více vláken, potenciálně vystavit sami na velmi závažnou a komplexní chyby. Obrátit [spravované dělení na vlákna osvědčené postupy](../../../../docs/standard/threading/managed-threading-best-practices.md) před implementací řešení, která používá více vláken.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Doporučené postupy dělení na spravovaná vlákna](../../../../docs/standard/threading/managed-threading-best-practices.md)  
 [Více vláken v součásti](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [NENÍ v sestavení: Více vláken v jazyce Visual Basic](http://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Postupy: Implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Návod: Spuštění operace na pozadí](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 [Komponenta BackgroundWorker](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
