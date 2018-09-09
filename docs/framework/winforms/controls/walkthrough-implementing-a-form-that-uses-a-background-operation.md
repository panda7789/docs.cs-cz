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
ms.openlocfilehash: 81c7f21e7e331b60d41330c8239893332dbea5a1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253127"
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a>Návod: Implementace formuláře, který používá operaci na pozadí
Pokud máte operace, která bude trvat dlouhou dobu pro dokončení, a nechcete uživatelského rozhraní (UI) přestane reagovat nebo "zablokování", můžete použít <xref:System.ComponentModel.BackgroundWorker> třídy k provedení operace v jiném vlákně.  
  
 Tento návod ukazuje, jak používat <xref:System.ComponentModel.BackgroundWorker> pro provádění časově náročné výpočty "v pozadí," při stále poměrně rychle reaguje uživatelské rozhraní.  Pokud jste si prostřednictvím, budete mít aplikaci, která vypočítá Fibonacciho čísla asynchronně. Přestože výpočetní že hodně Fibonacciho může trvat určitou dobu, hlavní vlákno uživatelského rozhraní nebude možné přerušit toto zpoždění a formulář bude responzivní během výpočtu.  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření aplikace pro Windows  
  
-   Vytváření <xref:System.ComponentModel.BackgroundWorker> ve formuláři  
  
-   Přidání asynchronní obslužné rutiny  
  
-   Přidání vytváření sestav průběhu a podporu pro zrušení  
  
 Úplný seznam všech kód použitý v tomto příkladu najdete v části [postupy: implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Vytvoření projektu  
 Prvním krokem je vytvoření projektu a k nastavení tvaru.  
  
#### <a name="to-create-a-form-that-uses-a-background-operation"></a>Chcete-li vytvořit formulář, který používá operaci na pozadí  
  
1.  Vytvořte projekt aplikace pro systém Windows s názvem `BackgroundWorkerExample` (**souboru** > **nový** > **projektu**  >  **Visual C#** nebo **jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).  
  
2.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na **Form1** a vyberte **přejmenovat** z místní nabídky. Změňte název souboru, aby `FibonacciCalculator`. Klikněte na tlačítko **Ano** tlačítko, pokud budete vyzváni, pokud chcete přejmenovat všechny odkazy na prvek kódu '`Form1`".  
  
3.  Přetáhněte <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku **nástrojů** do formuláře. Nastavte <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> vlastnost `1` a <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> vlastnost `91`.  
  
4.  Přidejte dva <xref:System.Windows.Forms.Button> ovládací prvky do formuláře.  
  
5.  Přejmenování prvního <xref:System.Windows.Forms.Button> ovládací prvek `startAsyncButton` a nastavit <xref:System.Windows.Forms.Control.Text%2A> vlastnost `Start Async`. Přejmenujte druhý <xref:System.Windows.Forms.Button> ovládací prvek `cancelAsyncButton`a nastavte <xref:System.Windows.Forms.Control.Text%2A> vlastnost `Cancel Async`. Nastavte jeho <xref:System.Windows.Forms.Control.Enabled%2A> vlastnost `false`.  
  
6.  Vytvořte obslužnou rutinu události pro obě <xref:System.Windows.Forms.Button> ovládacích prvků <xref:System.Windows.Forms.Control.Click> události. Podrobnosti najdete v tématu [postupy: vytváření událostí obslužné rutiny pomocí návrháře](https://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
7.  Přetáhněte <xref:System.Windows.Forms.Label> ovládacího prvku **nástrojů** do formuláře a přejmenujte jej `resultLabel`.  
  
8.  Přetáhněte <xref:System.Windows.Forms.ProgressBar> ovládacího prvku **nástrojů** do formuláře.  
  
## <a name="creating-a-backgroundworker-in-your-form"></a>Vytváření podproces BackgroundWorker ve formuláři  
 Můžete vytvořit <xref:System.ComponentModel.BackgroundWorker> pro asynchronní operace pomocí **Windows** **Návrháře formulářů**.  
  
#### <a name="to-create-a-backgroundworker-with-the-designer"></a>Chcete-li vytvořit podproces BackgroundWorker pomocí návrháře  
  
-   Z **součásti** karty **nástrojů**, přetáhněte <xref:System.ComponentModel.BackgroundWorker> do formuláře.  
  
## <a name="adding-asynchronous-event-handlers"></a>Přidání asynchronní obslužné rutiny  
 Nyní jste připraveni pro přidání obslužné rutiny událostí pro <xref:System.ComponentModel.BackgroundWorker> asynchronní událostí komponenty. Časově náročná operace, která se spustí na pozadí, která vypočítá Fibonacciho čísla, je volána pomocí jedné z těchto obslužných rutin událostí.  
  
#### <a name="to-implement-asynchronous-event-handlers"></a>K implementaci asynchronní obslužné rutiny  
  
1.  V **vlastnosti** okně s <xref:System.ComponentModel.BackgroundWorker> stále vybranou možností komponenty, klikněte na tlačítko **události** tlačítko. Dvakrát klikněte <xref:System.ComponentModel.BackgroundWorker.DoWork> a <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí pro vytváření obslužných rutin událostí. Další informace o tom, jak používat obslužné rutiny událostí, naleznete v tématu [postupy: vytváření událostí obslužné rutiny pomocí návrháře](https://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
2.  Vytvoření nové metody, volá `ComputeFibonacci`, ve formuláři. Tato metoda provádí samotnou práci, a tok se spustí na pozadí. Tento kód ukazuje implementaci rekurzivní Fibonacciho algoritmu, který je zejména, přičemž exponenciálně delší dobu pro velké objemy. Používá se tady pro ilustraci, chcete-li zobrazit operace, která můžete zavést dlouhá zpoždění ve vaší aplikaci.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  V <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužná rutina události, přidejte volání `ComputeFibonacci` metody. Využijte první parametr `ComputeFibonacci` z <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> vlastnost <xref:System.ComponentModel.DoWorkEventArgs>. <xref:System.ComponentModel.BackgroundWorker> a <xref:System.ComponentModel.DoWorkEventArgs> parametry se později použijí pro vykazování průběhu a zrušení podporovat. Přiřadit návratovou hodnotu z `ComputeFibonacci` k <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> vlastnost <xref:System.ComponentModel.DoWorkEventArgs>. Tohoto výsledku bude k dispozici na <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužné rutiny události.  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BackgroundWorker.DoWork> Obslužná rutina události neobsahuje odkaz `backgroundWorker1` instance proměnné přímo, protože to by spárovat tuto obslužnou rutinu události pro konkrétní instanci <xref:System.ComponentModel.BackgroundWorker>. Místo toho odkaz na <xref:System.ComponentModel.BackgroundWorker> , který vyvolá tato událost se zotavilo z `sender` parametru. To je důležité při formuláři hostiteli více než jedné <xref:System.ComponentModel.BackgroundWorker>. Je také důležité, abyste manipulovat s objekty uživatelského rozhraní ve vašich <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události. Místo toho komunikovat prostřednictvím uživatelského rozhraní <xref:System.ComponentModel.BackgroundWorker> události.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  V `startAsyncButton` ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužná rutina události, přidejte kód, který spustí asynchronní operaci.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  V <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> obslužná rutina události, přiřadit výsledek výpočtu, která `resultLabel` ovládacího prvku.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## <a name="adding-progress-reporting-and-support-for-cancellation"></a>Přidání vytváření sestav průběhu a podporu pro zrušení  
 Pro asynchronní operace, které bude trvat dlouhou dobu je často žádoucí sestav průběhu pro uživatele a aby uživatel mohl zrušit operaci. <xref:System.ComponentModel.BackgroundWorker> Třída poskytuje událost, která umožňuje publikovat průběh jako vaše operace pokračuje na pozadí. Poskytuje také příznak, který umožňuje detekovat volání do kódu pracovního procesu <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> a přerušit sama sebe.  
  
#### <a name="to-implement-progress-reporting"></a>K implementaci vykazování průběhu  
  
1.  V **vlastnosti**, vyberte `backgroundWorker1`. Nastavte <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> a <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> vlastností `true`.  
  
2.  Deklarujte dvě proměnné v `FibonacciCalculator` formuláře. Ty se používají ke sledování pokroku.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  Přidat obslužnou rutinu události pro <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> událostí. V <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> obslužná rutina události, aktualizace <xref:System.Windows.Forms.ProgressBar> s <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> vlastnost <xref:System.ComponentModel.ProgressChangedEventArgs> parametru.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### <a name="to-implement-support-for-cancellation"></a>K implementaci podpory pro zrušení  
  
1.  V `cancelAsyncButton` ovládacího prvku <xref:System.Windows.Forms.Control.Click> obslužná rutina události, přidejte kód, který zruší asynchronní operaci.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  Fragmenty se od následujícího kódu `ComputeFibonacci` metoda sestavy průběh a podporu zrušení.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku můžete zkompilujete a spustíte aplikaci Fibonacciho kalkulačku.  
  
#### <a name="to-test-your-project"></a>K otestování vašeho projektu  
  
-   Stiskněte klávesu F5 ke kompilaci a spuštění aplikace.  
  
     Při výpočtu běží na pozadí, zobrazí se <xref:System.Windows.Forms.ProgressBar> zobrazení průběhu výpočtu směrem k dokončení. Můžete také zrušit čekající operace.  
  
     Pro malé čísla výpočtu by měla být velmi rychlé zpracování, ale pro větší čísla, měli byste vidět významnému zpoždění. Pokud zadáte hodnotu 30 nebo vyšší, měli byste vidět trvat několik sekund, v závislosti na rychlosti počítače. Pro hodnoty větší než 40 může trvat minuty nebo hodiny na dokončení výpočtu. Je zaneprázdněn computingu hodně Fibonacciho kalkulačky, Všimněte si, že můžete volně pohyb tvaru, minimalizovat, maximalizovat a dokonce i zavřít. Je to proto, že hlavní vlákno uživatelského rozhraní nečeká na výpočet na dokončení.  
  
## <a name="next-steps"></a>Další kroky  
 Teď, když jste implementovali formulář, který používá <xref:System.ComponentModel.BackgroundWorker> komponentu pro spuštění výpočtu na pozadí můžete prozkoumat další možnosti pro asynchronní operace:  
  
-   Použití více <xref:System.ComponentModel.BackgroundWorker> objekty pro několik souběžných operací.  
  
-   Ladění aplikace s více vlákny, naleznete v tématu [postupy: použití okna vláken](/visualstudio/debugger/how-to-use-the-threads-window).  
  
-   Implementujte vlastní komponenty, která podporuje asynchronní programovací model. Další informace najdete v tématu [založený na událostech přehled asynchronních vzorů](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
    > [!CAUTION]
    >  Pokud používáte multithreading jakéhokoli druhu, potenciálně zpřístupníte sami velmi závažných a složitých chyb. Poraďte [spravovaných vláken osvědčené postupy](../../../../docs/standard/threading/managed-threading-best-practices.md) před implementací jakéhokoli řešení, které používá multithreading.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- [Dělení na spravovaná vlákna](../../../../docs/standard/threading/index.md)
- [Doporučené postupy dělení na spravovaná vlákna](../../../../docs/standard/threading/managed-threading-best-practices.md)
- [Přehled asynchronních vzorů založených na událostech](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Postupy: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md)  
- [Návod: Spuštění operace na pozadí](walkthrough-running-an-operation-in-the-background.md)
- [Komponenta BackgroundWorker](backgroundworker-component.md)
