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
ms.openlocfilehash: 2652c080951823e5289785b5906d2b0f48f5d658
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950776"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech
Pokud píšete třídu s některými operacemi, které mohou znamenat znatelné prodlevy, zvažte, že je nutné poskytnout asynchronní funkce implementací [asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Tento návod ukazuje, jak vytvořit komponentu, která implementuje asynchronní vzor založený na událostech. Je implementováno pomocí pomocných tříd z <xref:System.ComponentModel?displayProperty=nameWithType> oboru názvů, který zajišťuje správné fungování komponenty v jakémkoli modelu aplikace, včetně ASP.NET, konzolových aplikací a aplikací model Windows Forms. Tato součást je také navržena s <xref:System.Windows.Forms.PropertyGrid> ovládacím prvkem a vlastními návrháři.  
  
 Pokud jste vy, budete mít aplikaci, která provede asynchronní výpočet počtu primárních čísel. Vaše aplikace bude mít vlákno hlavního uživatelského rozhraní (UI) a vlákno pro každý výpočet primárního čísla. I když otestujete, zda velký počet primárních čísel může trvat znatelné množství času, hlavní vlákno uživatelského rozhraní nebude tímto zpožděním přerušeno a formulář bude během výpočtů reagovat. Budete moct spustit libovolný počet výpočtů, jak budete mít souběžně, a selektivně zrušit probíhající výpočty.  
  
 Úlohy, které jsou znázorněné v tomto návodu, zahrnují:  
  
- Vytváření komponenty  
  
- Definování veřejných asynchronních událostí a delegátů  
  
- Definování privátních delegátů  
  
- Implementace veřejných událostí  
  
- Implementace metody dokončení  
  
- Implementace metod pracovních procesů  
  
- Implementace metod Start a Cancel  
  
 Postup kopírování kódu v tomto tématu jako jediného výpisu naleznete v [tématu How to: Implementujte klienta asynchronního vzoru](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)založeného na událostech.  
  
## <a name="creating-the-component"></a>Vytváření komponenty  
 Prvním krokem je vytvoření komponenty, která bude implementovat asynchronní vzor založený na událostech.  
  
### <a name="to-create-the-component"></a>Vytvoření komponenty  
  
- Vytvořte třídu s názvem `PrimeNumberCalculator` , ze <xref:System.ComponentModel.Component>které dědí.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Definování veřejných asynchronních událostí a delegátů  
 Vaše komponenta komunikuje s klienty pomocí událostí. _MethodName_**Dokončená** upozornění událostí klientů na dokončení asynchronní úlohy a událost _methodName_**ProgressChanged** informuje klienty o průběhu asynchronní úlohy.  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Definování asynchronních událostí pro klienty vaší komponenty:  
  
1. Importujte obory <xref:System.Collections.Specialized?displayProperty=nameWithType> názvů avhorníčástisouboru.<xref:System.Threading?displayProperty=nameWithType>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. Před definicí `PrimeNumberCalculator` třídy deklarujte delegáty pro události průběhu a dokončení.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. V definici `PrimeNumberCalculator` třídy deklarujte události pro vytváření sestav o průběhu a doplňování klientům.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. Po definici `CalculatePrimeCompletedEventArgs` `CalculatePrimeCompleted`třídy odvodíte třídu pro vykazování výsledku každého výpočtu do obslužné rutiny události klienta pro událost. `PrimeNumberCalculator` Kromě `AsyncCompletedEventArgs` vlastností umožňuje tato třída klientovi určit, jaké číslo bylo testováno, zda je primární a co je první dělitel, pokud není primární.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku můžete komponentu sestavit.  
  
### <a name="to-test-your-component"></a>Testování komponenty  
  
- Zkompilujte komponentu.  
  
     Zobrazí se dvě upozornění kompilátoru:  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Tato upozornění budou vymazána v následující části.  
  
## <a name="defining-private-delegates"></a>Definování privátních delegátů  
 Asynchronní aspekty `PrimeNumberCalculator` komponenty jsou implementovány interně pomocí speciálního delegáta známého <xref:System.Threading.SendOrPostCallback>jako. Představuje metodu zpětného volání, která se spouští <xref:System.Threading.ThreadPool> ve vlákně. <xref:System.Threading.SendOrPostCallback> Metoda zpětného volání musí mít signaturu, která přijímá jeden parametr typu <xref:System.Object>, což znamená, že budete muset předat stav mezi delegáty v obálce třídy. Další informace naleznete v tématu <xref:System.Threading.SendOrPostCallback>.  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Implementace vnitřního asynchronního chování vaší komponenty:  
  
1. Deklarovat a vytvořit <xref:System.Threading.SendOrPostCallback> delegáty `PrimeNumberCalculator` ve třídě. Vytvořte objekty v obslužné metodě, která je `InitializeDelegates`volána. <xref:System.Threading.SendOrPostCallback>  
  
     Budete potřebovat dva delegáty: jeden pro vytváření sestav o průběhu klientovi a jeden pro dokončení vytváření sestav klientovi.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. `InitializeDelegates` Volejte metodu v konstruktoru vaší komponenty.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. Deklarujete delegáta ve `PrimeNumberCalculator` třídě, která zpracovává skutečnou práci, která má být provedena asynchronně. Tento delegát zalomí metodu pracovního procesu, která testuje, zda je číslo primární. Delegát převezme <xref:System.ComponentModel.AsyncOperation> parametr, který bude použit ke sledování životnosti asynchronní operace.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. Vytvořte kolekci pro správu životností nedokončených asynchronních operací. Klient potřebuje způsob, jak sledovat operace, když jsou spouštěny a dokončeny, a toto sledování je provedeno tím, že vyžaduje, aby klient předával jedinečný token nebo ID úlohy, když klient provede volání asynchronní metody. `PrimeNumberCalculator` Komponenta musí sledovat každé volání přiřazením ID úlohy k odpovídajícímu vyvolání. Pokud klient předává ID úlohy, které není jedinečné, `PrimeNumberCalculator` komponenta musí vyvolat výjimku.  
  
     Komponenta udržuje sledování ID úlohy pomocí speciální třídy kolekce nazvané a <xref:System.Collections.Specialized.HybridDictionary>. `PrimeNumberCalculator` V definici třídy vytvořte <xref:System.Collections.Specialized.HybridDictionary> třídu s názvem. `userTokenToLifetime`  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Implementace veřejných událostí  
 Komponenty, které implementují asynchronní vzor založený na událostech, komunikují klientům pomocí událostí. Tyto události jsou vyvolány ve správném vlákně s použitím <xref:System.ComponentModel.AsyncOperation> třídy.  
  
### <a name="to-raise-events-to-your-components-clients"></a>Chcete-li vyvolat události do klientů vaší komponenty:  
  
1. Implementujte veřejné události pro vytváření sestav klientům. Budete potřebovat událost pro vykazování průběhu a jednu pro dokončení generování sestav.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implementace metody dokončení  
 Delegát pro dokončení je metoda, kterou podkladové asynchronní chování s volným vláknem vyvolá v případě, že asynchronní operace skončí po úspěšném dokončení, chybě nebo zrušení. K tomuto vyvolání dojde v libovolném vlákně.  
  
 Tato metoda je v případě, že ID úlohy klienta je odebráno z interní kolekce jedinečných tokenů klienta. Tato metoda také ukončí životnost konkrétní asynchronní operace voláním <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> metody na odpovídajícím <xref:System.ComponentModel.AsyncOperation>elementu. Toto volání vyvolá událost dokončení ve vlákně, které je vhodné pro model aplikace. Po zavolání <xref:System.ComponentModel.AsyncOperation> metody se tato instance již nebude moci použít a jakékoli následné pokusy o její použití vyvolá výjimku. <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>  
  
 `CompletionMethod` Signatura musí obsahovat všechny stavy, které jsou nezbytné pro popis výsledku asynchronní operace. Obsahuje stav pro číslo, které bylo testováno touto konkrétní asynchronní operací, bez ohledu na to, zda je číslo primární, a hodnotu jeho prvního dělitele, pokud se nejedná o prvočíslo. Obsahuje také stav popisující jakoukoli výjimku, ke které došlo, a <xref:System.ComponentModel.AsyncOperation> odpovídající konkrétní úlohu.  
  
### <a name="to-complete-an-asynchronous-operation"></a>Dokončení asynchronní operace:  
  
- Implementujte metodu dokončení. Přijímá šest parametrů, které používá k naplnění `CalculatePrimeCompletedEventArgs` objektu `CalculatePrimeCompletedEventHandler`vráceného klientovi přes klienta. Odebere token ID úlohy klienta z interní kolekce a ukončí dobu života asynchronní operace voláním metody <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>. <xref:System.ComponentModel.AsyncOperation> Zazařazuje volání do vlákna nebo kontextu, který je vhodný pro model aplikace.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku můžete komponentu sestavit.  
  
### <a name="to-test-your-component"></a>Testování komponenty  
  
- Zkompilujte komponentu.  
  
     Zobrazí se jedno upozornění kompilátoru:  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Toto upozornění bude vyřešeno v další části.  
  
## <a name="implementing-the-worker-methods"></a>Implementace metod pracovních procesů  
 Zatím jste implementovali podpůrný asynchronní kód pro `PrimeNumberCalculator` komponentu. Nyní můžete implementovat kód, který provede skutečnou práci. Budete implementovat tři metody: `CalculateWorker`, `BuildPrimeNumberList` `IsPrime`a. `BuildPrimeNumberList` Společně a `IsPrime` tvoří dobře známý algoritmus nazvaný síto Eratosthenovo, který určuje, jestli je číslo primární, hledáním všech hlavních čísel až po druhou odmocninu čísla testu. Pokud žádné dělitele nejsou tímto bodem nalezeny, číslo testu je typu primární.  
  
 Pokud byla tato součást vytvořena pro maximální efektivitu, zapamatuje se všechna prvočísla zjištěná různými voláními různých testovacích čísel. Také zkontroluje triviální dělitele jako 2, 3 a 5. Záměrem tohoto příkladu je Ukázat, jak se můžou časově náročné operace provádět asynchronně, ale tyto optimalizace jsou jako cvičení pro vás.  
  
 Metoda je zabalena do delegáta a je vyvolána asynchronně s `BeginInvoke`voláním metody. `CalculateWorker`  
  
> [!NOTE]
> Vytváření sestav o průběhu je implementováno v `BuildPrimeNumberList` metodě. V rychlých počítačích `ProgressChanged` se události dají vyvolat rychle po sobě. Vlákno klienta, na kterém jsou tyto události vyvolány, musí být schopné tuto situaci zpracovat. Kód uživatelského rozhraní může být zahlcený zprávami a nemůže být zachován. Výsledkem je neodezva. Ukázkové uživatelské rozhraní, které zpracovává tuto situaci, najdete v [tématu How to: Implementujte klienta asynchronního vzoru](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)založeného na událostech.  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>K asynchronnímu provedení výpočtu primárního čísla:  
  
1. Implementujte `TaskCanceled` metodu Utility. Tím se ověří shromažďování životnosti úloh pro dané ID úlohy a vrátí `true` se, pokud nebylo nalezeno ID úlohy.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. Implementujte `CalculateWorker` metodu. Používá dva parametry: číslo, které se má testovat, a <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. Implementujte `BuildPrimeNumberList`. Používá dva parametry: číslo, které se má testovat, a <xref:System.ComponentModel.AsyncOperation>. Používá <xref:System.ComponentModel.AsyncOperation> k nahlášení průběhu a přírůstkových výsledků. To zaručuje, že jsou obslužné rutiny událostí klienta volány ve správném vlákně nebo kontextu pro model aplikace. Když `BuildPrimeNumberList` najde hlavní číslo, nahlásí ho jako přírůstkový výsledek `ProgressChanged` pro obslužnou rutinu události klienta pro událost. To vyžaduje třídu odvozenou z <xref:System.ComponentModel.ProgressChangedEventArgs>, s `CalculatePrimeProgressChangedEventArgs`názvem, která má jednu přidanou `LatestPrimeNumber`vlastnost nazvanou.  
  
     Metoda také pravidelně `TaskCanceled` volá metodu a ukončí, pokud se metoda vrátí `true`. `BuildPrimeNumberList`  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. Implementujte `IsPrime`. Používá tři parametry: seznam známých prvočísl, číslo k otestování a výstupní parametr pro první nalezený dělitel. Seznam primárních čísel určuje, zda je číslo testu primární.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. `CalculatePrimeProgressChangedEventArgs` Odvodit <xref:System.ComponentModel.ProgressChangedEventArgs>z. Tato třída je nezbytná pro vytváření sestav přírůstkových výsledků do obslužné rutiny události klienta `ProgressChanged` pro danou událost. Obsahuje jednu přidanou vlastnost s `LatestPrimeNumber`názvem.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku můžete komponentu sestavit.  
  
### <a name="to-test-your-component"></a>Testování komponenty  
  
- Zkompilujte komponentu.  
  
     Vše, co zbývá k zápisu, jsou metody pro spuštění a zrušení asynchronních operací `CalculatePrimeAsync` a `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implementace metod Start a Cancel  
 Metodu Worker spustíte ve vlastním vlákně voláním `BeginInvoke` delegáta, který ho zabalí. Chcete-li spravovat životnost konkrétní asynchronní operace, zavolejte <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> metodu <xref:System.ComponentModel.AsyncOperationManager> na pomocnou třídu. Vrátí <xref:System.ComponentModel.AsyncOperation>, který zařazování volá do správného vlákna nebo kontextu v obslužných rutinách událostí klienta.  
  
 Zrušením příslušné nedokončené operace zavoláte <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> odpovídajícím způsobem. <xref:System.ComponentModel.AsyncOperation> Tím se ukončí Tato operace a jakékoliv následné volání do jejího <xref:System.ComponentModel.AsyncOperation> vyvolání vyvolá výjimku.  
  
### <a name="to-implement-start-and-cancel-functionality"></a>Implementace funkce spustit a zrušit:  
  
1. Implementujte `CalculatePrimeAsync` metodu. Ujistěte se, že token poskytovaný klientem (ID úlohy) je jedinečný s ohledem na všechny tokeny, které představují aktuálně probíhající úkoly. Pokud klient projde nejedinečným tokenem, `CalculatePrimeAsync` vyvolá výjimku. V opačném případě se token přidá do kolekce ID úlohy.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. Implementujte `CancelAsync` metodu. `taskId` Pokud parametr existuje v kolekci tokenů, je odebrán. Tím zabráníte zrušeným úlohám, které nebyly spuštěny. Pokud je úloha spuštěná, `BuildPrimeNumberList` metoda se ukončí, když zjistí, že ID úlohy se odebralo z kolekce životního cyklu.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku můžete komponentu sestavit.  
  
### <a name="to-test-your-component"></a>Testování komponenty  
  
- Zkompilujte komponentu.  
  
 `PrimeNumberCalculator` Komponenta je nyní dokončena a připravena k použití.  
  
 Ukázkového klienta, který používá `PrimeNumberCalculator` komponentu, najdete v tématu [How to: Implementujte klienta asynchronního vzoru](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)založeného na událostech.  
  
## <a name="next-steps"></a>Další kroky  
 Tento příklad můžete vyplnit psaním `CalculatePrime`synchronního `CalculatePrimeAsync` ekvivalentu metody. Díky tomu bude `PrimeNumberCalculator` komponenta plně kompatibilní s asynchronním vzorem založeným na událostech.  
  
 Tento příklad můžete vylepšit tak, že si zachováte seznam všech primárních čísel zjištěných různými voláními různých testovacích čísel. Při použití tohoto přístupu bude každý úkol těžit z práce provedené předchozími úkoly. Buďte opatrní při ochraně tohoto seznamu s `lock` použitím oblastí, proto je serializovaný přístup k seznamu podle různých vláken.  
  
 Můžete také vylepšit tento příklad testováním triviálních dělitelů, jako jsou 2, 3 a 5.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
