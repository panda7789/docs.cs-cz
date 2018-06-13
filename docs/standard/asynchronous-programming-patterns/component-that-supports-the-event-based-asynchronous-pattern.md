---
title: 'Návod: Implementace komponenty, která podporuje asynchronní vzor založený na událostech'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
ms.openlocfilehash: 9156a538e306fb8657855a840dd8185cef8794b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579259"
---
# <a name="walkthrough-implementing-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Návod: Implementace komponenty, která podporuje asynchronní vzor založený na událostech
Pokud píšete třídu s některé operace, které může vést k významnému zpoždění, zvažte, udělíte tím, že implementujete asynchronní funkce [na základě událostí přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Tento návod ukazuje, jak vytvořit komponenty, která implementuje asynchronní vzor založený na událostech. Je implementována pomocí pomocné třídy z <xref:System.ComponentModel?displayProperty=nameWithType> obor názvů, které zajišťuje, že součást funguje správně v rámci modelu všechny aplikace, včetně [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], konzoly a aplikace Windows Forms. Tato součást je také navrhovatelé s <xref:System.Windows.Forms.PropertyGrid> řízení a vlastní vlastní Designer.  
  
 Pokud jste prostřednictvím, budete mít aplikaci, která vypočítá prvočísel asynchronně. Vaše aplikace bude mít vlákno hlavní uživatelské rozhraní (UI) a vlákno pro každý prime číslo výpočtu. I když testování, zda je velký počet prime může trvat určitou dobu, hlavního vlákna uživatelského rozhraní nesmějí být přerušeny toto zpoždění a formulář bude přizpůsobivý během výpočty. Bude moct spustit, protože mnoho výpočty podle potřeby souběžně a selektivně zrušit probíhající výpočty.  
  
 Úkoly v tomto návodu zahrnují:  
  
-   Vytváření komponenty  
  
-   Definování veřejné asynchronní události a delegáti  
  
-   Definování privátního delegáti  
  
-   Implementace veřejné události  
  
-   Implementace metody dokončení  
  
-   Implementace metody pracovního procesu  
  
-   Implementace Start a zrušit metody  
  
 Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: implementace klienta asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Vytváření komponenty  
 Prvním krokem je vytvoření komponentou bude implementovat asynchronní vzor založený na událostech.  
  
#### <a name="to-create-the-component"></a>Chcete-li vytvořit komponentu  
  
-   Vytvoření třídy s názvem `PrimeNumberCalculator` který dědí z <xref:System.ComponentModel.Component>.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Definování veřejné asynchronní události a delegáti  
 Příslušné součásti komunikuje s klienty, kteří používají události. *MethodName *** dokončeno** upozornění na událost zahození klientům dokončení asynchronní úlohu a *MethodName *** ProgressChanged** událostí informuje klienti průběh asynchronní úlohu.  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Chcete-li definovat asynchronní události pro klienty příslušné součásti:  
  
1.  Import <xref:System.Threading?displayProperty=nameWithType> a <xref:System.Collections.Specialized?displayProperty=nameWithType> obory názvů v horní části souboru.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  Před `PrimeNumberCalculator` třídy definice deklarovat delegátů pro události, průběh a dokončení.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  V `PrimeNumberCalculator` definici třídy, deklarování událostí pro generování sestav průběh a dokončení klientům.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  Po `PrimeNumberCalculator` definici třídy, které jsou odvozeny `CalculatePrimeCompletedEventArgs` třídy pro výsledek každé výpočtu k obslužné rutině událostí klienta pro vytváření sestav `CalculatePrimeCompleted`.event. Kromě `AsyncCompletedEventArgs` vlastnosti, tato třída umožňuje určit, jaké číslo byla testována, jestli je primární a co první dělitel je, pokud není prvotní klientovi.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku můžete vytvořit komponentu.  
  
#### <a name="to-test-your-component"></a>K testování příslušné součásti  
  
-   Zkompilujte komponentu.  
  
     Zobrazí dvě upozornění kompilátoru:  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Vymaže se tato upozornění v další části.  
  
## <a name="defining-private-delegates"></a>Definování privátního delegáti  
 Asynchronní aspektů `PrimeNumberCalculator` součásti jsou implementované interně se označuje jako speciální delegátem <xref:System.Threading.SendOrPostCallback>. A <xref:System.Threading.SendOrPostCallback> představuje metody zpětného volání, které provádí na <xref:System.Threading.ThreadPool> přístup z více vláken. Metoda zpětného volání musí mít podpis, která přijímá jeden parametr typu <xref:System.Object>, což znamená, že bude nutné předat stavu mezi Delegáti v obálkovou třídu. Další informace naleznete v tématu <xref:System.Threading.SendOrPostCallback>.  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>K implementaci příslušné součásti interní asynchronní chování:  
  
1.  Deklarace a vytvořit <xref:System.Threading.SendOrPostCallback> deleguje v `PrimeNumberCalculator` třídy. Vytvořte <xref:System.Threading.SendOrPostCallback> objekty v nástroj metoda volána `InitializeDelegates`.  
  
     Budete potřebovat dva delegáti: jeden pro vytvoření sestavy průběhu klientovi a jeden pro vytváření sestav dokončení klientovi.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  Volání `InitializeDelegates` metoda v konstruktoru příslušné součásti.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  Delegáta v deklarovat `PrimeNumberCalculator` třída, která zpracovává samotnou práci provést asynchronně. Tento delegát zabalí metodu pracovního procesu, který kontroluje, zda je číslo prime. Delegát používá <xref:System.ComponentModel.AsyncOperation> parametr, který se použije ke sledování životnost asynchronní operaci.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  Vytvoření kolekce pro správu životnosti z čekajících asynchronních operací. Klient musí způsob, jak sledovat operace, jak se spustí a dokončení, a toto sledování probíhá tím, že klient předat jedinečný token nebo ID úkolu, pokud klient provede volání asynchronní metody. `PrimeNumberCalculator` Součásti musí udržovat přehled o jednotlivých volání tím, že přidružíte ID úkolu pomocí jeho odpovídající volání. Pokud klient předá ID úkolu, který není jedinečné, `PrimeNumberCalculator` součásti musí vyvolat výjimku.  
  
     `PrimeNumberCalculator` Součást uchovává informace o ID úlohy pomocí speciální kolekce třídu s názvem <xref:System.Collections.Specialized.HybridDictionary>. V definici třídy, vytvořte <xref:System.Collections.Specialized.HybridDictionary> názvem `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Implementace veřejné události  
 Součásti, které implementovat asynchronní vzor založený na událostech komunikaci s klienty, kteří používají události. Tyto události jsou vyvolány na správné vlákno pomocí <xref:System.ComponentModel.AsyncOperation> třídy.  
  
#### <a name="to-raise-events-to-your-components-clients"></a>Umožňuje aktivovat události klientům příslušné součásti:  
  
1.  Implementujte veřejné události vytváření sestav pro klienty. Budete potřebovat událost pro vytváření sestav průběh a jeden pro generování sestav dokončení.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implementace metody dokončení  
 Delegát dokončení je metoda, která základní, podprocesy asynchronní chování vyvolá při ukončení asynchronní operaci úspěšné dokončení, chyby nebo zrušení. Toto volání se odehrává na libovolný vlákno.  
  
 Tato metoda je, kde je ID úkolu klienta z interní kolekce tokenů jedinečných klientských odebrat. Tato metoda také končí životnost konkrétní asynchronní operaci voláním <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> metoda na odpovídajícím <xref:System.ComponentModel.AsyncOperation>. Toto volání vyvolává událost dokončení na vlákno, které jsou vhodné pro model aplikace. Po <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> metoda je volána, tuto instanci <xref:System.ComponentModel.AsyncOperation> již být použít, a všechny následné pokusy o použít vyvolá výjimku.  
  
 `CompletionMethod` Podpis musí obsahovat všechny stavy potřebné k popisu výsledek asynchronní operace. Zda je číslo prime a hodnotu jeho první dělitel Pokud není číslo prime drží stav pro číslo, které se testoval tato konkrétní asynchronní operace. Také drží stavu popisující žádné výjimka, ke které došlo k chybě, a <xref:System.ComponentModel.AsyncOperation> odpovídající tuto konkrétní úlohu.  
  
#### <a name="to-complete-an-asynchronous-operation"></a>K dokončení asynchronní operace:  
  
-   Implementace metody dokončení. Jak dlouho trvá šest parametry, které používá k naplnění `CalculatePrimeCompletedEventArgs` , je vrácen do klienta prostřednictvím klienta `CalculatePrimeCompletedEventHandler`. Odebere token ID úloh klienta z interní kolekce a ho ukončí asynchronní operace životního cyklu pomocí volání <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>. <xref:System.ComponentModel.AsyncOperation> Zařazuje volání vlákno nebo kontext, který je vhodný pro aplikačního modelu.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku můžete vytvořit komponentu.  
  
#### <a name="to-test-your-component"></a>K testování příslušné součásti  
  
-   Zkompilujte komponentu.  
  
     Zobrazí jednu upozornění kompilátoru:  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Toto upozornění se vyřeší v další části.  
  
## <a name="implementing-the-worker-methods"></a>Implementace metody pracovního procesu  
 Pokud jste implementovali podporující asynchronní kód `PrimeNumberCalculator` součásti. Nyní můžete implementovat kód, který ve skutečnosti provádí zpracování. Budete implementovat tři metody: `CalculateWorker`, `BuildPrimeNumberList`, a `IsPrime`. Společně `BuildPrimeNumberList` a `IsPrime` tvoří dobře známé algoritmus volat ze sít Eratosthenes, která určuje, zda je číslo prime tak, že najdete všechny prvočísel až druhou odmocninu čísla test. Pokud žádné divisors pomocí tohoto bodu, je číslo testovací prime.  
  
 Pokud tuto komponentu byly napsány pro maximální efektivity, by nezapomeňte všechny prvočísel zjištěných různé volání pro jiný testovací čísla. By také vyhledat trivial divisors jako 2, 3 nebo 5. Tohoto příkladu je cílem ukazují, jak časově náročná operace mohou být provedeny asynchronně, ale tak tyto optimalizace jsou ponechané jako cvičení za vás.  
  
 `CalculateWorker` Metoda je uzavřen do delegáta a je vyvoláno asynchronně s volání `BeginInvoke`.  
  
> [!NOTE]
>  Průběh vytváření sestav je implementována ve `BuildPrimeNumberList` metoda. V rychlé počítačích `ProgressChanged` události mohou být vyvolány rychle za sebou. Vlákno klienta, na kterém tyto události jsou vyvolány, musí být schopen zpracování této situace. Uživatelského rozhraní kódu může být přenášeny pomocí zpráv a nelze zpracovat, což vede k hanging chování. Uživatelské rozhraní příklad, který zpracovává této situaci, najdete v části [postupy: implementace klienta asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Provést asynchronně výpočtu prime číslo:  
  
1.  Implementace `TaskCanceled` metody nástrojů. To ověří kolekci úloh doba platnosti pro danou úlohu ID a vrátí `true` Pokud není nalezena ID úkolu.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  Implementace `CalculateWorker` metoda. Jak dlouho trvá dva parametry: číslo otestovat a <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  Implementace `BuildPrimeNumberList`. Jak dlouho trvá dva parametry: číslo chcete otestovat a <xref:System.ComponentModel.AsyncOperation>. Použije <xref:System.ComponentModel.AsyncOperation> sestavy průběhu a přírůstkové výsledky. To zaručuje, že obslužné rutiny událostí klienta se nazývají na správné vlákno nebo kontext pro aplikačního modelu. Když `BuildPrimeNumberList` najde-li číslo prime, oznámí toto jako výsledek přírůstkové do klienta obslužné rutiny události pro `ProgressChanged` událostí. To vyžaduje třídy odvozené od <xref:System.ComponentModel.ProgressChangedEventArgs>, volané `CalculatePrimeProgressChangedEventArgs`, který má jeden přidat vlastnost s názvem `LatestPrimeNumber`.  
  
     `BuildPrimeNumberList` Metoda také pravidelně volá `TaskCanceled` metoda a ukončí, pokud metoda vrátí `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  Implementace `IsPrime`. Jak dlouho trvá tři parametry: seznam prvočísel známé, číslo pro testování a výstupní parametr pro první dělitel nalezen. Zadaný seznam prvočísel, se určuje, zda číslo testovací prime.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  Odvození `CalculatePrimeProgressChangedEventArgs` z <xref:System.ComponentModel.ProgressChangedEventArgs>. Tato třída je nezbytné pro vytváření sestav přírůstkové výsledky do klienta obslužné rutiny události pro `ProgressChanged` událostí. Má jeden přidané vlastnost s názvem `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku můžete vytvořit komponentu.  
  
#### <a name="to-test-your-component"></a>K testování příslušné součásti  
  
-   Zkompilujte komponentu.  
  
     Všechno, co jsou zůstane k zapsání metody pro spuštění a zrušení asynchronních operací `CalculatePrimeAsync` a `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implementace Start a zrušit metody  
 Spuštění metody pracovního procesu ve vlastním vlákně voláním `BeginInvoke` na delegáta, který z nich. Chcete-li spravovat dobu životnosti konkrétní asynchronní operaci, zavolejte <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> metodu <xref:System.ComponentModel.AsyncOperationManager> pomocná třída. Vrátí <xref:System.ComponentModel.AsyncOperation>, který zařazuje volání obslužných rutin událostí klienta správné vlákno nebo kontextu.  
  
 Zrušit konkrétní nevyřízenou operaci voláním <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> na jeho odpovídající <xref:System.ComponentModel.AsyncOperation>. Tím končí tuto operaci a následných volání jeho <xref:System.ComponentModel.AsyncOperation> vyvolá výjimku.  
  
#### <a name="to-implement-start-and-cancel-functionality"></a>K implementaci úvodní a zrušit funkce:  
  
1.  Implementace `CalculatePrimeAsync` metoda. Ujistěte se, že token zadaný klienta (ID úlohy) je jedinečný s ohledem na všechny tokeny představující aktuálně úkolů čekajících na zpracování. Pokud klient předá do jedinečný tokenu, `CalculatePrimeAsync` vyvolá výjimku. Token, jinak se přidá do kolekce ID úloh.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  Implementace `CancelAsync` metoda. Pokud `taskId` v tokenu kolekci parametrů existuje, bude odebrán. Tím se zabrání zrušené úlohy, které nebyly spuštěné z spuštěná. Pokud je spuštěn úkol, `BuildPrimeNumberList` metoda ukončí, když zjistí, ID úlohy byl odebrán z kolekce životního cyklu.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku můžete vytvořit komponentu.  
  
#### <a name="to-test-your-component"></a>K testování příslušné součásti  
  
-   Zkompilujte komponentu.  
  
 `PrimeNumberCalculator` Je nyní úplný a připravené k použití.  
  
 Pro příklad klienta, který používá `PrimeNumberCalculator` součást, najdete v části [postupy: implementace klienta asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Další kroky  
 V tomto příkladu můžete vyplnit napsáním `CalculatePrime`, synchronní ekvivalent `CalculatePrimeAsync` metoda. Bude `PrimeNumberCalculator` součást plně kompatibilní s asynchronní vzor založený na událostech.  
  
 V tomto příkladu může zvýšit zachováním seznam všech prvočísel zjištěných různé volání pro jiný testovací čísla. Použití tohoto přístupu, bude každý úkol těžit z práci předchozí úlohy. Pečlivě Chraňte tento seznam s `lock` oblastech, tak přístup k seznamu podle různých vláknech serializován.  
  
 V tomto příkladu lze zvýšit rovněž testování pro trivial divisors, jako je 2, 3 nebo 5.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [NENÍ v sestavení: Více vláken v jazyce Visual Basic](https://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Vícevláknové programování s asynchronním vzorem založeným na událostech](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
