---
title: 'Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech'
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
ms.openlocfilehash: 44a1019ac8169138aa95b03e2027d9539cbf8391
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71957361"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech
Pokud píšete třídu s některými operacemi, které mohou způsobit znatelné zpoždění, zvažte poskytnutí asynchronní funkce implementací [přehledu asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Tento návod ukazuje, jak vytvořit komponentu, která implementuje asynchronní vzor založený na událostech. Je implementována pomocí pomocných tříd z oboru <xref:System.ComponentModel?displayProperty=nameWithType> názvů, což zajišťuje, že komponenta pracuje správně v rámci libovolného modelu aplikace, včetně ASP.NET, konzolových aplikací a aplikací Windows Forms. Tato součást je také <xref:System.Windows.Forms.PropertyGrid> navržena s ovládacím prvkem a vlastními návrháři.  
  
 Po dokončení budete mít aplikaci, která vypočítá prvočísla asynchronně. Aplikace bude mít hlavní vlákno uživatelského rozhraní (UI) a vlákno pro každý výpočet prvočísla. Přestože testování, zda je velké množství prvočíslo, může trvat znatelné množství času, hlavní vlákno uživatelského rozhraní nebude tímto zpožděním přerušeno a formulář bude reagovat během výpočtů. Budete moci spustit tolik výpočtů, kolik chcete současně a selektivně zrušit čekající výpočty.  
  
 Mezi úkoly znázorněné v tomto návodu patří:  
  
- Vytvoření komponenty  
  
- Definování veřejných asynchronních událostí a delegátů  
  
- Definování soukromých delegátů  
  
- Implementace veřejných akcí  
  
- Implementace metody dokončení  
  
- Implementace metod pracovních procesů  
  
- Implementace metod Start a Cancel  
  
 Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, naleznete v tématu [How to: Implement an Client of the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Vytvoření komponenty  
 Prvním krokem je vytvoření komponenty, která bude implementovat asynchronní vzor založený na událostech.  
  
### <a name="to-create-the-component"></a>Vytvoření komponenty  
  
- Vytvořte třídu s `PrimeNumberCalculator` <xref:System.ComponentModel.Component>názvem dědí z .  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Definování veřejných asynchronních událostí a delegátů  
 Komponenta komunikuje s klienty pomocí událostí. Událost _MethodName_**Completed** upozorňuje klienty na dokončení asynchronní úlohy a událost _MethodName_**ProgressChanged** informuje klienty o průběhu asynchronní úlohy.  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Definování asynchronních událostí pro klienty komponenty:  
  
1. Importujte <xref:System.Threading?displayProperty=nameWithType> <xref:System.Collections.Specialized?displayProperty=nameWithType> obory názvů a v horní části souboru.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. Před `PrimeNumberCalculator` definicí třídy deklarujte delegáty pro události průběhu a dokončení.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. V `PrimeNumberCalculator` definici třídy deklarujte události pro hlášení průběhu a dokončení klientům.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. Po `PrimeNumberCalculator` definici třídy `CalculatePrimeCompletedEventArgs` odvodit třídu pro vykazování výsledku každého výpočtu obslužné rutině události klienta pro `CalculatePrimeCompleted`.event. Kromě `AsyncCompletedEventArgs` vlastností tato třída umožňuje klientovi určit, jaké číslo bylo testováno, zda je prvočíslo a jaký je první dělitel, pokud není prvočíslo.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku můžete vytvořit součást.  
  
### <a name="to-test-your-component"></a>Testování komponenty  
  
- Zkompilujte komponentu.  
  
     Zobrazí se dvě upozornění kompilátoru:  
  
    ```console  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Tato varování budou vymazána v další části.  
  
## <a name="defining-private-delegates"></a>Definování soukromých delegátů  
 Asynchronní aspekty `PrimeNumberCalculator` komponenty jsou implementovány interně se zvláštním <xref:System.Threading.SendOrPostCallback>delegátem známým jako . A <xref:System.Threading.SendOrPostCallback> představuje metodu zpětného volání, která se spustí ve vlákně. <xref:System.Threading.ThreadPool> Metoda zpětného volání musí mít podpis, který <xref:System.Object>přebírá jeden parametr typu , což znamená, že budete muset předat stav mezi delegáty ve třídě obálky. Další informace naleznete v tématu <xref:System.Threading.SendOrPostCallback>.  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Implementace interního asynchronního chování komponenty:  
  
1. Deklarovat <xref:System.Threading.SendOrPostCallback> a `PrimeNumberCalculator` vytvořit delegáty ve třídě. Vytvořte <xref:System.Threading.SendOrPostCallback> objekty v `InitializeDelegates`metodě nástroje s názvem .  
  
     Budete potřebovat dva delegáty: jeden pro hlášení průběhu klientovi a jeden pro vykazování dokončení klientovi.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. Volání `InitializeDelegates` metody v konstruktoru komponenty.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. Deklarovat `PrimeNumberCalculator` delegáta ve třídě, která zpracovává skutečnou práci, která má být provedena asynchronně. Tento delegát zalomí metodu pracovníka, která testuje, zda je číslo prvočíslo. Delegát přebírá <xref:System.ComponentModel.AsyncOperation> parametr, který bude použit ke sledování životnosti asynchronní operace.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. Vytvořte kolekci pro správu životnosti čekající chnacích asynchronních operací. Klient potřebuje způsob, jak sledovat operace, jak jsou prováděny a dokončeny, a toto sledování se provádí tím, že vyžaduje, aby klient předat jedinečný token nebo ID úlohy, když klient provede volání asynchronní metody. Součást `PrimeNumberCalculator` musí sledovat každé volání přidružováním ID úkolu s odpovídajícím vyvoláním. Pokud klient předá ID úlohy, `PrimeNumberCalculator` která není jedinečná, musí komponenta vyvolat výjimku.  
  
     Komponenta `PrimeNumberCalculator` sleduje ID úkolu pomocí speciální třídy <xref:System.Collections.Specialized.HybridDictionary>kolekce nazývané . V definici třídy <xref:System.Collections.Specialized.HybridDictionary> `userTokenToLifetime`vytvořte volaný .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Implementace veřejných akcí  
 Součásti, které implementují asynchronní vzor založený na událostech, komunikují klientům pomocí událostí. Tyto události jsou vyvolány ve správném vlákně pomocí třídy. <xref:System.ComponentModel.AsyncOperation>  
  
### <a name="to-raise-events-to-your-components-clients"></a>Chcete-li vyvolat události pro klienty komponenty:  
  
1. Implementujte veřejné události pro vytváření sestav klientům. Budete potřebovat událost pro hlášení průběhu a jeden pro hlášení dokončení.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implementace metody dokončení  
 Delegát dokončení je metoda, kterou základní asynchronní chování s volným vláknem vyvolá, když asynchronní operace skončí úspěšným dokončením, chybou nebo zrušením. Toto vyvolání se stane v libovolném vlákně.  
  
 Tato metoda je, kde id úlohy klienta je odebrána z vnitřní kolekce tokenů jedinečné klienta. Tato metoda také ukončí životnost určité asynchronní operace <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> voláním <xref:System.ComponentModel.AsyncOperation>metody na odpovídající . Toto volání vyvolá událost dokončení ve vlákně, která je vhodná pro model aplikace. Po <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> volání metody tuto instanci již <xref:System.ComponentModel.AsyncOperation> nelze použít a všechny následné pokusy o její použití vyvolá výjimku.  
  
 Podpis `CompletionMethod` musí obsahovat všechny stavy nezbytné k popisu výsledku asynchronní operace. Obsahuje stav pro číslo, které bylo testováno touto konkrétní asynchronní operací, zda je číslo prvočíslo a hodnota jeho prvního dělitela, pokud není prvočíslo. Obsahuje také stav popisující všechny výjimky, <xref:System.ComponentModel.AsyncOperation> ke kterým došlo, a odpovídající této konkrétní úkolu.  
  
### <a name="to-complete-an-asynchronous-operation"></a>Dokončení asynchronní operace:  
  
- Implementujte metodu dokončení. Trvá šest parametrů, které používá k `CalculatePrimeCompletedEventArgs` naplnění, který je vrácen `CalculatePrimeCompletedEventHandler`klientovi prostřednictvím klienta . Odebere token ID úlohy klienta z interní kolekce a ukončí životnost asynchronní operace <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>voláním . Zařazuje <xref:System.ComponentModel.AsyncOperation> volání vlákna nebo kontextu, který je vhodný pro model aplikace.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku můžete vytvořit součást.  
  
### <a name="to-test-your-component"></a>Testování komponenty  
  
- Zkompilujte komponentu.  
  
     Obdržíte jedno upozornění kompilátoru:  
  
    ```console  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Toto upozornění bude vyřešeno v další části.  
  
## <a name="implementing-the-worker-methods"></a>Implementace metod pracovních procesů  
 Dosud jste implementovali podpůrný asynchronní kód `PrimeNumberCalculator` pro komponentu. Nyní můžete implementovat kód, který provádí skutečnou práci. Implementujete tři `CalculateWorker` `BuildPrimeNumberList`metody: `IsPrime`, , a . Společně, `BuildPrimeNumberList` `IsPrime` a zahrnují známý algoritmus s názvem Sieve of Eratosthenes, který určuje, zda číslo je prvočíslo tím, že najde všechna prvočísla až do druhou odmocninu čísla testu. Pokud v tomto okamžiku nejsou nalezeny žádné dělitelé, číslo testu je prvočíslo.  
  
 Pokud by tato součást byla napsána pro maximální efektivitu, pamatovala by si všechna prvočísla zjištěná různými vyvoláními pro různá testovací čísla. To by také zkontrolovat triviální děliteees jako 2, 3 a 5. Záměrem tohoto příkladu je ukázat, jak časově náročné operace mohou být prováděny asynchronně, ale tak tyto optimalizace jsou ponechány jako cvičení pro vás.  
  
 Metoda `CalculateWorker` je zabalena v delegáta a je vyvolána asynchronně s voláním `BeginInvoke`.  
  
> [!NOTE]
> V metodě je `BuildPrimeNumberList` implementováno vykazování průběhu. Na rychlých `ProgressChanged` počítačích mohou být události vyvolány v rychlém sledu. Podproces klienta, na kterém jsou vyvolány tyto události, musí být schopen zpracovat tuto situaci. Kód uživatelského rozhraní může být zaplaven zprávami a nemůže držet krok, což vede k nereagování. Příklad uživatelského rozhraní, které zpracovává tuto situaci, naleznete v [tématu How to: Implement an Client of the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Provedení výpočtu prvočísla asynchronně:  
  
1. Implementujte `TaskCanceled` metodu nástroje. Tím zkontrolujete shromažďování životnosti úkolu pro `true` dané ID úkolu a vrátí se, pokud id úkolu není nalezeno.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. Implementujte `CalculateWorker` metodu. Trvá dva parametry: číslo k testování <xref:System.ComponentModel.AsyncOperation>a .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. Implementovat `BuildPrimeNumberList`. Trvá dva parametry: číslo k testování <xref:System.ComponentModel.AsyncOperation>a . Používá k <xref:System.ComponentModel.AsyncOperation> vykazování průběhu a přírůstkové výsledky. Tím je zajištěno, že obslužné rutiny událostí klienta jsou volány na správné vlákno nebo kontext pro model aplikace. Když `BuildPrimeNumberList` najde prvočíslo, hlásí to jako přírůstkový výsledek obslužné rutiny `ProgressChanged` události klienta pro událost. To vyžaduje třídu <xref:System.ComponentModel.ProgressChangedEventArgs>odvozenou `CalculatePrimeProgressChangedEventArgs`z , volal `LatestPrimeNumber`, který má jednu přidanou vlastnost s názvem .  
  
     Metoda `BuildPrimeNumberList` také pravidelně volá `TaskCanceled` metodu a ukončí, `true`pokud metoda vrátí .  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. Implementovat `IsPrime`. Trvá tři parametry: seznam známých prvočísel, číslo k testování a výstupní parametr pro první nalezený dělitel. Vzhledem k tomu, seznam prvočísel, určuje, zda číslo testu je prvočíslo.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. Odvodit `CalculatePrimeProgressChangedEventArgs` z <xref:System.ComponentModel.ProgressChangedEventArgs>. Tato třída je nezbytná pro vykazování přírůstkových výsledků obslužné rutině `ProgressChanged` události klienta pro událost. Má jednu přidanou vlastnost nazvanou `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku můžete vytvořit součást.  
  
### <a name="to-test-your-component"></a>Testování komponenty  
  
- Zkompilujte komponentu.  
  
     Vše, co zbývá zapsat, jsou metody pro spuštění `CalculatePrimeAsync` a `CancelAsync`zrušení asynchronních operací a .  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implementace metod Start a Cancel  
 Spustíte metodu worker ve vlastním `BeginInvoke` vlákně voláním delegáta, který ji zabalí. Chcete-li spravovat životnost konkrétní asynchronní operace, <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> volání <xref:System.ComponentModel.AsyncOperationManager> metody na pomocné třídy. To vrátí <xref:System.ComponentModel.AsyncOperation>, který zařazuje volání obslužné rutiny událostí klienta do správnévlákno nebo kontextu.  
  
 Určitou čekající operaci zrušíte voláním <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> na odpovídající <xref:System.ComponentModel.AsyncOperation>. Tím ukončíte tuto operaci a <xref:System.ComponentModel.AsyncOperation> všechna následná volání jeho vyvolá výjimku.  
  
### <a name="to-implement-start-and-cancel-functionality"></a>Implementace funkce Start a Cancel:  
  
1. Implementujte `CalculatePrimeAsync` metodu. Ujistěte se, že token dodaný klientem (ID úlohy) je jedinečný vzhledem ke všem tokenům představujícím aktuálně čekající úkoly. Pokud klient předá v nejedinečný `CalculatePrimeAsync` token, vyvolá výjimku. V opačném případě je token přidán do kolekce ID úlohy.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. Implementujte `CancelAsync` metodu. Pokud `taskId` parametr existuje v kolekci tokenů, je odebrán. Tím zabráníte spuštění zrušených úloh, které nebyly spuštěny. Pokud je úloha `BuildPrimeNumberList` spuštěna, metoda ukončí, když zjistí, že ID úlohy byla odebrána z kolekce životnosti.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku můžete vytvořit součást.  
  
### <a name="to-test-your-component"></a>Testování komponenty  
  
- Zkompilujte komponentu.  
  
 Součást `PrimeNumberCalculator` je nyní dokončena a připravena k použití.  
  
 Příklad klienta, který `PrimeNumberCalculator` používá komponentu, naleznete v [tématu How to: Implement an Client of the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Další kroky  
 Tento příklad můžete vyplnit `CalculatePrime`zápisem , synchronní `CalculatePrimeAsync` ekvivalent metody. Díky součástplně `PrimeNumberCalculator` kompatibilní s událostmi asynchronní vzor.  
  
 Tento příklad můžete vylepšit zachováním seznamu všech prvočísel zjištěných různými vyvoláními pro různá testovací čísla. Pomocí tohoto přístupu bude každý úkol těžit z práce provedené předchozími úkoly. Buďte opatrní chránit tento `lock` seznam s oblastmi, takže přístup k seznamu různými vlákny je serializován.  
  
 Tento příklad můžete také vylepšit testováním triviálních dělitelů, jako jsou 2, 3 a 5.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
