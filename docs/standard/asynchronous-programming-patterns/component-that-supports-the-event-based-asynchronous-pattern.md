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
ms.openlocfilehash: 8213d3d980edc9c37b5f50545edbcd8959616963
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745464"
---
# <a name="how-to-implement-a-component-that-supports-the-event-based-asynchronous-pattern"></a>Postupy: Implementace komponenty, která podporuje asynchronní vzor založený na událostech
Pokud píšete třída s atributem některé operace, které případně utrpíte významnému zpoždění, zvažte jeho asynchronní funkce implementací [založený na událostech přehled asynchronních vzorů](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Tento návod ukazuje, jak vytvořit komponentu, která implementuje asynchronního vzoru založeného na událostech. Je implementována pomocí pomocné třídy z <xref:System.ComponentModel?displayProperty=nameWithType> obor názvů, který zajistí, že součást správně funguje v jakékoli aplikační model, včetně [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], konzolové aplikace a aplikace Windows Forms. Tato součást je také navrhovatelé s <xref:System.Windows.Forms.PropertyGrid> ovládacího prvku a vlastní vlastní návrháři.  
  
 Pokud jste si prostřednictvím, budete mít aplikaci, která vypočítá prvočísel asynchronně. Vaše aplikace bude mít hlavní uživatelské vlákno rozhraní (UI) a vlákno pro každý výpočet prime číslo. I když testování, zda je hodně prime může trvat určitou dobu, hlavní vlákno uživatelského rozhraní nebude dojít k přerušení kvůli tomuto zpoždění dochází a formulář bude reagovat při výpočtech. Bude moct spustit, protože mnoho výpočtů chcete současně a selektivně zrušit probíhající výpočty.  
  
 Úlohy v tomto návodu zahrnují:  
  
-   Vytvoření komponenty  
  
-   Definování veřejné asynchronní události a delegáti  
  
-   Definování privátní delegátů  
  
-   Implementace veřejné události  
  
-   Implementace metody dokončení  
  
-   Implementace metody pracovního procesu  
  
-   Implementace Start a metody Cancel  
  
 Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Implementace klienta asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="creating-the-component"></a>Vytvoření komponenty  
 Prvním krokem je vytvoření Komponenta, která bude implementovat asynchronní vzor založený na událostech.  
  
#### <a name="to-create-the-component"></a>Chcete-li vytvořit komponentu  
  
-   Vytvořte třídu s názvem `PrimeNumberCalculator` , která dědí z <xref:System.ComponentModel.Component>.  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a>Definování veřejné asynchronní události a delegáti  
 Vaše komponenta komunikuje s klienty, kteří používají události. _MethodName_**dokončeno** klientů pro dokončení asynchronní úlohu, upozornění na událost a _MethodName_**ProgressChanged**událost informuje klienty pokroku asynchronní úlohu.  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a>Chcete-li definovat asynchronní události pro klienty komponenty:  
  
1.  Import <xref:System.Threading?displayProperty=nameWithType> a <xref:System.Collections.Specialized?displayProperty=nameWithType> obory názvů v horní části souboru.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  Před `PrimeNumberCalculator` třídy definice, deklarace delegátů pro události průběh a dokončení.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  V `PrimeNumberCalculator` třídy definice, deklarace události vytváření sestav průběhu a dokončení klientům.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  Po `PrimeNumberCalculator` definici třídy, jsou odvozeny `CalculatePrimeCompletedEventArgs` třídy pro vytváření sestav výsledek klienta obslužné rutiny události pro jednotlivé výpočty `CalculatePrimeCompleted`.event. Kromě `AsyncCompletedEventArgs` vlastnosti, tato třída umožňuje klientovi určíte, jaké číslo byl testován, ať už jde o primární a co první dělitel je, pokud není primární.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku můžete vytvořit komponentu.  
  
#### <a name="to-test-your-component"></a>Chcete-li otestovat  
  
-   Zkompilujte komponentu.  
  
     Zobrazí se dvě upozornění kompilátoru:  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     Tato upozornění bude vymazáno v další části.  
  
## <a name="defining-private-delegates"></a>Definování privátní delegátů  
 Asynchronní aspektů `PrimeNumberCalculator` komponenty jsou implementována interně označované jako speciální delegátem <xref:System.Threading.SendOrPostCallback>. A <xref:System.Threading.SendOrPostCallback> představuje metodu zpětného volání, která se spustí na <xref:System.Threading.ThreadPool> vlákna. Metoda zpětného volání musí mít podpis, který přijímá jeden parametr typu <xref:System.Object>, což znamená, že bude nutné předat stav mezi Delegáti v obálkovou třídu. Další informace naleznete v tématu <xref:System.Threading.SendOrPostCallback>.  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a>K implementaci interní asynchronní chování komponenty:  
  
1.  Deklarace a vytvořit <xref:System.Threading.SendOrPostCallback> delegátů v `PrimeNumberCalculator` třídy. Vytvořte <xref:System.Threading.SendOrPostCallback> objekty v metodě nástroj nazývají `InitializeDelegates`.  
  
     Budete potřebovat dva delegáty: jeden pro vykazování průběhu klientovi a jeden pro dokončení do klienta.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  Volání `InitializeDelegates` metoda v konstruktoru komponenty.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  Deklarovat delegáta v `PrimeNumberCalculator` třídu, která zpracovává skutečná práce, která se měla provádět asynchronně. Tento delegát zabalí metodě pracovního podprocesu, který testuje, jestli je primární. Delegát používá <xref:System.ComponentModel.AsyncOperation> parametr, který se použije ke sledování životnosti asynchronní operace.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  Vytvoření kolekce pro správu životní cyklus čekajících asynchronních operací. Klient potřebuje způsob, jak sledovat operace, jako jsou spuštění a dokončení, a toto sledování provádí vyžaduje, aby klient předat jedinečný token nebo ID úkolu, když klient zadá volání asynchronní metody. `PrimeNumberCalculator` Součásti musí udržovat přehled o každé volání tím, že přidružíte ID úkolu pomocí jeho odpovídající volání. Pokud klient předá ID úkolu, který není jedinečný, `PrimeNumberCalculator` součásti musí vyvolat výjimku.  
  
     `PrimeNumberCalculator` Komponenty uchovává informace o ID úkolu pomocí speciální kolekce třídu s názvem <xref:System.Collections.Specialized.HybridDictionary>. V definici třídy, vytvořte <xref:System.Collections.Specialized.HybridDictionary> volá `userTokenToLifetime`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a>Implementace veřejné události  
 Součásti, které implementují asynchronního vzoru založeného na událostech komunikaci s klienty, kteří používají události. Tyto události jsou vyvolány na řádné vlákna ve spolupráci <xref:System.ComponentModel.AsyncOperation> třídy.  
  
#### <a name="to-raise-events-to-your-components-clients"></a>Chcete-li vyvolat události klientům komponenty:  
  
1.  Implementujte veřejné události pro hlášení klientům. Budete potřebovat události vytváření sestav průběhu a jeden pro dokončení generování sestav.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a>Implementace metody dokončení  
 Dokončení delegát je metoda, která vyvolá asynchronní chování základní, volných vláken při úspěšném dokončení, chybě nebo zrušení ukončení asynchronní operace. Toto volání se stane u libovolného vlákna.  
  
 Tato metoda je, kde ID úkolu klienta je odebrán z interní kolekce jedinečných klientských tokenů. Tato metoda také končí voláním životnost konkrétní asynchronní operaci <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> metoda u odpovídajícího <xref:System.ComponentModel.AsyncOperation>. Toto volání vyvolává událost dokončení ve vlákně, které je vhodné aplikačního modelu. Po <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> metoda je volána, tuto instanci <xref:System.ComponentModel.AsyncOperation> může již nelze použít, a všechny následné pokusy o použití vyvolá výjimku.  
  
 `CompletionMethod` Podpisu musí mít všechny stavy nezbytné k popisu výsledek asynchronní operace. Obsahuje stav pro číslo, které testoval této konkrétní asynchronní operace, zda je číslo prime a hodnota jeho první dělitel nesplnění Prvočíslo. Také obsahuje stav popisující jakoukoliv výjimku, k níž došlo, a <xref:System.ComponentModel.AsyncOperation> odpovídající této konkrétní úlohy.  
  
#### <a name="to-complete-an-asynchronous-operation"></a>K dokončení asynchronní operace:  
  
-   Implementace metody dokončení. Trvá, šest parametry, které používá k naplnění `CalculatePrimeCompletedEventArgs` , který je vrácen do klienta prostřednictvím klienta `CalculatePrimeCompletedEventHandler`. Odebere token ID úkolu klienta z vnitřní kolekce a ukončení asynchronní operace životního cyklu voláním <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>. <xref:System.ComponentModel.AsyncOperation> Zařazuje volání vlákna nebo kontextu, který je vhodný pro aplikačního modelu.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku můžete vytvořit komponentu.  
  
#### <a name="to-test-your-component"></a>Chcete-li otestovat  
  
-   Zkompilujte komponentu.  
  
     Zobrazí se jedné upozornění kompilátoru:  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     Toto upozornění se vyřeší v další části.  
  
## <a name="implementing-the-worker-methods"></a>Implementace metody pracovního procesu  
 Zatím jste implementovali podpůrné asynchronní kód `PrimeNumberCalculator` komponenty. Nyní můžete implementovat kód, který ve skutečnosti zajišťuje zpracování. Budete implementovat tři metody: `CalculateWorker`, `BuildPrimeNumberList`, a `IsPrime`. Společně `BuildPrimeNumberList` a `IsPrime` tvoří dobře známý algoritmus volá Eratosthenovo síto, která určuje, zda je číslo prime tím, že hledá všechny prvočísel až druhou odmocninu čísla testu. Pokud se nenajde žádný divisors pomocí tohoto bodu, je číslo test prime.  
  
 Pokud tuto komponentu byly napsány pro maximální účinnost mezi body, by nezapomeňte všechny prvočísel zjištěných různé volání pro různé testovací čísla. To by také zkontrolovat triviální divisors jako 2, 3 nebo 5. Záměrem tohoto příkladu je předvést způsob časově náročná operace je možné spustit asynchronně, ale tak tyto optimalizace jsou ponechané jako cvičení za vás.  
  
 `CalculateWorker` Metoda je zabalena v delegátovi a je vyvoláno asynchronně s volání `BeginInvoke`.  
  
> [!NOTE]
>  Vykazování průběhu je implementována v `BuildPrimeNumberList` metody. Rychlé počítačích `ProgressChanged` události mohou být vyvolány rychle po sobě. Vlákna klienta, na kterém jsou tyto události vyvolány, musí být schopen tuto situaci. Kód uživatelského rozhraní může být docházet zprávy a schopen čelit, což vede k předsazení chování. Uživatelské rozhraní příklad, který zpracovává této situaci, naleznete v tématu [jak: Implementace klienta asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a>Spustit asynchronně výpočtu prime číslo:  
  
1.  Implementace `TaskCanceled` metody nástrojů. To ověří kolekce dobu života úlohy pro Identifikátor dané úlohy a vrátí `true` Pokud se nenajde ID úkolu.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  Implementace `CalculateWorker` metody. Přebírá dva parametry: číslo k testování a <xref:System.ComponentModel.AsyncOperation>.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  Implementace `BuildPrimeNumberList`. Přebírá dva parametry: číslo k testování a <xref:System.ComponentModel.AsyncOperation>. Používá <xref:System.ComponentModel.AsyncOperation> sestavy průběh a výsledky přírůstkové. To zaručuje, že jsou volány obslužné rutiny událostí klienta na správné thread nebo context aplikačního modelu. Když `BuildPrimeNumberList` najde-li prime číslo, bude posílat sestavy to jako výsledek přírůstkové klienta obslužné rutiny události pro `ProgressChanged` událostí. To vyžaduje třídu odvozenou z <xref:System.ComponentModel.ProgressChangedEventArgs>, označované jako `CalculatePrimeProgressChangedEventArgs`, která je přidána jedna vlastnost s názvem `LatestPrimeNumber`.  
  
     `BuildPrimeNumberList` Také pravidelně volá metodu `TaskCanceled` metoda a ukončí, pokud metoda vrátí `true`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  Implementace `IsPrime`. Přijímá tři parametry: seznam známých prvočísel, číslo k testování a výstupní parametr pro první dělitel nalezen. Zadaný seznam prvočísel, se určuje, zda je číslo test prime.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  Odvození `CalculatePrimeProgressChangedEventArgs` z <xref:System.ComponentModel.ProgressChangedEventArgs>. Tato třída je nezbytné pro vytváření sestav přírůstkové výsledky do obslužné rutiny události klienta pro `ProgressChanged` událostí. Má jeden přidaný vlastnost s názvem `LatestPrimeNumber`.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku můžete vytvořit komponentu.  
  
#### <a name="to-test-your-component"></a>Chcete-li otestovat  
  
-   Zkompilujte komponentu.  
  
     Všechno, zůstane k zapsání jsou metody pro spuštění a zrušení asynchronní operace `CalculatePrimeAsync` a `CancelAsync`.  
  
## <a name="implementing-the-start-and-cancel-methods"></a>Implementace Start a metody Cancel  
 Spustit metodě pracovního podprocesu ve vlastním vlákně voláním `BeginInvoke` na delegáta, který zabalí jej. Chcete-li spravovat dobu života konkrétní asynchronní operace, zavolejte <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> metodu na <xref:System.ComponentModel.AsyncOperationManager> pomocná třída. Tím se vrátí <xref:System.ComponentModel.AsyncOperation>, který zařadí volání obslužných rutin událostí klienta správné thread nebo context.  
  
 Zrušit konkrétní nevyřízenou operaci voláním <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> na jeho odpovídající <xref:System.ComponentModel.AsyncOperation>. Ukončí se tato operace a následných volání jeho <xref:System.ComponentModel.AsyncOperation> vyvolá výjimku.  
  
#### <a name="to-implement-start-and-cancel-functionality"></a>K implementaci úvodní a zrušit funkce:  
  
1.  Implementace `CalculatePrimeAsync` metody. Ujistěte se, že token dodaná klientem (ID úlohy) je jedinečný s ohledem všechny tokeny, které představuje aktuálně probíhající úlohy. Pokud klient předá token nejedinečné `CalculatePrimeAsync` vyvolá výjimku. V opačném případě token se přidá do kolekce ID úkolu.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  Implementace `CancelAsync` metody. Pokud `taskId` parametr existuje v kolekci token, odebere se současně. To zabraňuje zrušené úlohy, které nebyly spuštěny spouštění. Pokud je spuštěn úkol, `BuildPrimeNumberList` metoda ukončí, když zjistí, že ID úkolu byla odebrána z kolekce životnost.  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a>CheckPoint  
 V tomto okamžiku můžete vytvořit komponentu.  
  
#### <a name="to-test-your-component"></a>Chcete-li otestovat  
  
-   Zkompilujte komponentu.  
  
 `PrimeNumberCalculator` Je nyní dokončena a připravena k použití.  
  
 Pro příklad klienta, který používá `PrimeNumberCalculator` komponenty, naleznete v tématu [jak: Implementace klienta asynchronního vzoru založeného na událostech](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).  
  
## <a name="next-steps"></a>Další kroky  
 V tomto příkladu můžete vyplnit napsáním `CalculatePrime`, synchronní ekvivalent `CalculatePrimeAsync` metody. To způsobí, že `PrimeNumberCalculator` součást plně kompatibilní s asynchronní vzor založený na událostech.  
  
 V tomto příkladu můžete zvýšit tak, že zachová seznam všech prvočísel zjištěných různé volání pro různé testovací čísla. Tento přístup se každý úkol těžit z práce provedené předchozí úlohy. Pečlivě Chraňte tento seznam s `lock` oblastí, tak přístup k seznamu podle různých vláken je serializována.  
  
 V tomto příkladu může také zvýšit testováním triviální divisors, jako je 2, 3 nebo 5.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Spuštění operace na pozadí](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
