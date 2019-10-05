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
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957361"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech
Pokud píšete třídu s některými operacemi, které mohou znamenat znatelné prodlevy, zvažte, že je nutné poskytnout asynchronní funkce implementací [asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Tento návod ukazuje, jak vytvořit komponentu, která implementuje asynchronní vzor založený na událostech. Je implementováno pomocí pomocných tříd z oboru názvů <xref:System.ComponentModel?displayProperty=nameWithType>, který zajišťuje správné fungování komponenty v jakémkoli modelu aplikace, včetně ASP.NET, konzolových aplikací a model Windows Formsch aplikací. Tato součást je také navržena s ovládacím prvkem @no__t 0 a vlastními návrháři.  
  
 Pokud jste vy, budete mít aplikaci, která provede asynchronní výpočet počtu primárních čísel. Vaše aplikace bude mít vlákno hlavního uživatelského rozhraní (UI) a vlákno pro každý výpočet primárního čísla. I když otestujete, zda velký počet primárních čísel může trvat znatelné množství času, hlavní vlákno uživatelského rozhraní nebude tímto zpožděním přerušeno a formulář bude během výpočtů reagovat. Budete moct spustit libovolný počet výpočtů, jak budete mít souběžně, a selektivně zrušit probíhající výpočty.  
  
 Úlohy, které jsou znázorněné v tomto návodu, zahrnují:  
  
- Vytváření komponenty  
  
- Definování veřejných asynchronních událostí a delegátů  
  
- Definování privátních delegátů  
  
- Implementace veřejných událostí  
  
- Implementace metody dokončení  
  
- Implementace metod pracovních procesů  
  
- Implementace metod Start a Cancel  
  
 Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, přečtěte si téma [How to: Implementace klienta asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Vytváření komponenty  
 Prvním krokem je vytvoření komponenty, která bude implementovat asynchronní vzor založený na událostech.  
  
### <a name="to-create-the-component"></a>Vytvoření komponenty  
  
- Vytvořte třídu s názvem `PrimeNumberCalculator`, která dědí z <xref:System.ComponentModel.Component>.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Definování veřejných asynchronních událostí a delegátů  
 Vaše komponenta komunikuje s klienty pomocí událostí. _MethodName_**Dokončená** upozornění událostí klientů na dokončení asynchronní úlohy a událost _methodName_**ProgressChanged** informuje klienty o průběhu asynchronní úlohy.  
  
### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Definování asynchronních událostí pro klienty vaší komponenty:  
  
1. Importujte obory názvů <xref:System.Threading?displayProperty=nameWithType> a <xref:System.Collections.Specialized?displayProperty=nameWithType> v horní části souboru.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2. Před definicí třídy `PrimeNumberCalculator` deklarujte delegáty pro události průběhu a dokončení.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3. V definici třídy `PrimeNumberCalculator` deklarujte události pro vytváření sestav o průběhu a doplňování klientům.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4. Po definici třídy `PrimeNumberCalculator` odvodit třídu `CalculatePrimeCompletedEventArgs` pro vykazování výsledku každého výpočtu do obslužné rutiny události klienta pro @no__t -2. Event. Kromě vlastností `AsyncCompletedEventArgs` Tato třída umožňuje klientovi určit, jaké číslo bylo testováno, zda se jedná o primární a co je první dělitel, pokud není primární.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku můžete komponentu sestavit.  
  
### <a name="to-test-your-component"></a>Testování komponenty  
  
- Zkompilujte komponentu.  
  
     Zobrazí se dvě upozornění kompilátoru:  
  
    ```console  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Tato upozornění budou vymazána v následující části.  
  
## <a name="defining-private-delegates"></a>Definování privátních delegátů  
 Asynchronní aspekty součásti `PrimeNumberCalculator` jsou implementovány interně se speciálním delegátem známým jako <xref:System.Threading.SendOrPostCallback>. @No__t-0 představuje metodu zpětného volání, která se spouští na vlákně <xref:System.Threading.ThreadPool>. Metoda zpětného volání musí mít signaturu, která přijímá jeden parametr typu <xref:System.Object>, což znamená, že budete muset předat stav mezi delegáty v obálce třídy. Další informace najdete v tématu <xref:System.Threading.SendOrPostCallback>.  
  
### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>Implementace vnitřního asynchronního chování vaší komponenty:  
  
1. Deklaruje a vytvoří delegáty <xref:System.Threading.SendOrPostCallback> ve třídě `PrimeNumberCalculator`. Vytvořte objekty <xref:System.Threading.SendOrPostCallback> v metodě Utility nazvané `InitializeDelegates`.  
  
     Budete potřebovat dva delegáty: jeden pro vytváření sestav o průběhu klientovi a jeden pro dokončení vytváření sestav klientovi.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2. Volejte metodu `InitializeDelegates` v konstruktoru vaší komponenty.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3. Deklarujete delegáta ve třídě `PrimeNumberCalculator`, která zpracovává skutečnou práci, která má být provedena asynchronně. Tento delegát zalomí metodu pracovního procesu, která testuje, zda je číslo primární. Delegát přebírá parametr <xref:System.ComponentModel.AsyncOperation>, který bude použit ke sledování životnosti asynchronní operace.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4. Vytvořte kolekci pro správu životností nedokončených asynchronních operací. Klient potřebuje způsob, jak sledovat operace, když jsou spouštěny a dokončeny, a toto sledování je provedeno tím, že vyžaduje, aby klient předával jedinečný token nebo ID úlohy, když klient provede volání asynchronní metody. Komponenta `PrimeNumberCalculator` musí sledovat každé volání přiřazením ID úkolu k odpovídajícímu vyvolání. Pokud klient předává ID úlohy, které není jedinečné, komponenta `PrimeNumberCalculator` musí vyvolat výjimku.  
  
     Komponenta `PrimeNumberCalculator` udržuje přehled o ID úlohy pomocí speciální třídy kolekce nazvané <xref:System.Collections.Specialized.HybridDictionary>. V definici třídy vytvořte <xref:System.Collections.Specialized.HybridDictionary> s názvem `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Implementace veřejných událostí  
 Komponenty, které implementují asynchronní vzor založený na událostech, komunikují klientům pomocí událostí. Tyto události jsou vyvolány ve správném vlákně s použitím třídy <xref:System.ComponentModel.AsyncOperation>.  
  
### <a name="to-raise-events-to-your-components-clients"></a>Chcete-li vyvolat události do klientů vaší komponenty:  
  
1. Implementujte veřejné události pro vytváření sestav klientům. Budete potřebovat událost pro vykazování průběhu a jednu pro dokončení generování sestav.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implementace metody dokončení  
 Delegát pro dokončení je metoda, kterou podkladové asynchronní chování s volným vláknem vyvolá v případě, že asynchronní operace skončí po úspěšném dokončení, chybě nebo zrušení. K tomuto vyvolání dojde v libovolném vlákně.  
  
 Tato metoda je v případě, že ID úlohy klienta je odebráno z interní kolekce jedinečných tokenů klienta. Tato metoda také ukončí životnost konkrétní asynchronní operace voláním metody <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> na odpovídající <xref:System.ComponentModel.AsyncOperation>. Toto volání vyvolá událost dokončení ve vlákně, které je vhodné pro model aplikace. Po volání metody <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> již nelze tuto instanci <xref:System.ComponentModel.AsyncOperation> použít a jakékoli následné pokusy o její použití budou vyvolat výjimku.  
  
 Podpis `CompletionMethod` musí obsahovat všechny stavy, které jsou nezbytné pro popis výsledku asynchronní operace. Obsahuje stav pro číslo, které bylo testováno touto konkrétní asynchronní operací, bez ohledu na to, zda je číslo primární, a hodnotu jeho prvního dělitele, pokud se nejedná o prvočíslo. Obsahuje také stav popisující jakoukoli výjimku, ke které došlo, a <xref:System.ComponentModel.AsyncOperation> odpovídající tomuto konkrétnímu úkolu.  
  
### <a name="to-complete-an-asynchronous-operation"></a>Dokončení asynchronní operace:  
  
- Implementujte metodu dokončení. Přijímá šest parametrů, které používá k naplnění `CalculatePrimeCompletedEventArgs` vráceného klientovi prostřednictvím `CalculatePrimeCompletedEventHandler` klienta. Odebere token ID úlohy klienta z interní kolekce a ukončí dobu života asynchronní operace se voláním <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>. @No__t-0 zařazování volání do vlákna nebo kontextu, který je vhodný pro model aplikace.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku můžete komponentu sestavit.  
  
### <a name="to-test-your-component"></a>Testování komponenty  
  
- Zkompilujte komponentu.  
  
     Zobrazí se jedno upozornění kompilátoru:  
  
    ```console  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Toto upozornění bude vyřešeno v další části.  
  
## <a name="implementing-the-worker-methods"></a>Implementace metod pracovních procesů  
 Zatím jste implementovali podpůrný asynchronní kód pro komponentu `PrimeNumberCalculator`. Nyní můžete implementovat kód, který provede skutečnou práci. Budete implementovat tři metody: `CalculateWorker`, `BuildPrimeNumberList` a `IsPrime`. Společně `BuildPrimeNumberList` a `IsPrime` tvoří dobře známý algoritmus nazvaný síto Eratosthenovo, který určuje, jestli je číslo primárním adresářem, a to tak, že najde všechna prvočísla až do druhé odmocniny zkušebního čísla. Pokud žádné dělitele nejsou tímto bodem nalezeny, číslo testu je typu primární.  
  
 Pokud byla tato součást vytvořena pro maximální efektivitu, zapamatuje se všechna prvočísla zjištěná různými voláními různých testovacích čísel. Také zkontroluje triviální dělitele jako 2, 3 a 5. Záměrem tohoto příkladu je Ukázat, jak se můžou časově náročné operace provádět asynchronně, ale tyto optimalizace jsou jako cvičení pro vás.  
  
 Metoda `CalculateWorker` je zabalena v delegátu a je vyvolána asynchronně s voláním `BeginInvoke`.  
  
> [!NOTE]
> Vytváření sestav průběhu je implementováno v metodě `BuildPrimeNumberList`. V rychlých počítačích se události `ProgressChanged` dají v rychlém úspěchu vyvolat. Vlákno klienta, na kterém jsou tyto události vyvolány, musí být schopné tuto situaci zpracovat. Kód uživatelského rozhraní může být zahlcený zprávami a nemůže být zachován. Výsledkem je neodezva. Ukázkové uživatelské rozhraní, které zpracovává tuto situaci, naleznete v tématu [How to: Implementing Client of a Asynchronous vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>K asynchronnímu provedení výpočtu primárního čísla:  
  
1. Implementujte metodu nástroje `TaskCanceled`. Tato kontrola vyhledá kolekci životního cyklu úlohy pro dané ID úlohy a vrátí hodnotu `true`, pokud ID úlohy nebylo nalezeno.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2. Implementujte metodu `CalculateWorker`. Používá dva parametry: číslo, které se má testovat, a <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3. Implementujte `BuildPrimeNumberList`. Používá dva parametry: číslo, které se má testovat, a <xref:System.ComponentModel.AsyncOperation>. K hlášení průběhu a přírůstkových výsledků používá <xref:System.ComponentModel.AsyncOperation>. To zaručuje, že jsou obslužné rutiny událostí klienta volány ve správném vlákně nebo kontextu pro model aplikace. Když `BuildPrimeNumberList` najde hlavní číslo, oznámí to jako přírůstkový výsledek obslužné rutině události klienta pro událost `ProgressChanged`. To vyžaduje třídu odvozenou od <xref:System.ComponentModel.ProgressChangedEventArgs>, která se nazývá `CalculatePrimeProgressChangedEventArgs` s jednou přidanou vlastností nazvanou `LatestPrimeNumber`.  
  
     Metoda `BuildPrimeNumberList` také pravidelně volá metodu `TaskCanceled` a ukončí, pokud metoda vrátí `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4. Implementujte `IsPrime`. Používá tři parametry: seznam známých prvočísl, číslo k otestování a výstupní parametr pro první nalezený dělitel. Seznam primárních čísel určuje, zda je číslo testu primární.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5. Odvodit `CalculatePrimeProgressChangedEventArgs` od <xref:System.ComponentModel.ProgressChangedEventArgs>. Tato třída je nezbytná pro vytváření sestav přírůstkových výsledků do obslužné rutiny události klienta pro událost `ProgressChanged`. Má jednu přidanou vlastnost nazvanou `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku můžete komponentu sestavit.  
  
### <a name="to-test-your-component"></a>Testování komponenty  
  
- Zkompilujte komponentu.  
  
     Vše, co zbývá k zápisu, jsou metody pro spuštění a zrušení asynchronních operací, `CalculatePrimeAsync` a `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implementace metod Start a Cancel  
 Metodu Worker spustíte ve vlastním vlákně voláním `BeginInvoke` u delegáta, který ho zabalí. Chcete-li spravovat životnost určité asynchronní operace, zavolejte metodu <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> na pomocnou třídu <xref:System.ComponentModel.AsyncOperationManager>. Vrátí <xref:System.ComponentModel.AsyncOperation>, který zařazování volá do správného vlákna nebo kontextu v obslužných rutinách událostí klienta.  
  
 Zrušením konkrétní nevyřízenou operaci zrušíte volání <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> na odpovídající <xref:System.ComponentModel.AsyncOperation>. Tím se ukončí Tato operace a jakékoliv následné volání na jeho <xref:System.ComponentModel.AsyncOperation> vyvolá výjimku.  
  
### <a name="to-implement-start-and-cancel-functionality"></a>Implementace funkce spustit a zrušit:  
  
1. Implementujte metodu `CalculatePrimeAsync`. Ujistěte se, že token poskytovaný klientem (ID úlohy) je jedinečný s ohledem na všechny tokeny, které představují aktuálně probíhající úkoly. Pokud klient projde nejedinečným tokenem, `CalculatePrimeAsync` vyvolá výjimku. V opačném případě se token přidá do kolekce ID úlohy.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2. Implementujte metodu `CancelAsync`. Pokud v kolekci tokenů existuje parametr `taskId`, je odebrán. Tím zabráníte zrušeným úlohám, které nebyly spuštěny. Pokud je úloha spuštěná, metoda `BuildPrimeNumberList` se ukončí, když zjistí, že ID úlohy se odebralo z kolekce životního cyklu.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>Kontrolní bod  
 V tomto okamžiku můžete komponentu sestavit.  
  
### <a name="to-test-your-component"></a>Testování komponenty  
  
- Zkompilujte komponentu.  
  
 Komponenta `PrimeNumberCalculator` je nyní dokončena a připravena k použití.  
  
 Příklad klienta, který používá komponentu `PrimeNumberCalculator`, naleznete v tématu [How to: Implementing Client of a Asynchronous vzor založený na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Další kroky  
 Tento příklad můžete vyplnit tak, že napíšete `CalculatePrime`, synchronní ekvivalent metody `CalculatePrimeAsync`. Tím dojde k tomu, že komponenta `PrimeNumberCalculator` bude plně kompatibilní s asynchronním vzorem založeným na událostech.  
  
 Tento příklad můžete vylepšit tak, že si zachováte seznam všech primárních čísel zjištěných různými voláními různých testovacích čísel. Při použití tohoto přístupu bude každý úkol těžit z práce provedené předchozími úkoly. Buďte opatrní při ochraně tohoto seznamu s @no__tmi oblastmi, takže je serializovaný přístup k seznamu podle různých vláken.  
  
 Můžete také vylepšit tento příklad testováním triviálních dělitelů, jako jsou 2, 3 a 5.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
