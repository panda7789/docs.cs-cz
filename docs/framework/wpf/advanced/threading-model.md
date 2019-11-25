---
title: Model vláken
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text on buttons [WPF], updating
- message processing [WPF], nested
- blocking operations [WPF]
- Common Language Runtime (CLR), locking mechanism
- locking mechanism of Common Language Runtime (CLR)
- threading model [WPF]
- Word [WPF], spelling checking
- button text [WPF], updating
- spelling checking in Word [WPF]
- asynchronous behavior [WPF], exposing
- nested message processing [WPF]
- reentrancy [WPF]
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
ms.openlocfilehash: ae120311e7e58b34437de987e9f9a18e917043c0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974079"
---
# <a name="threading-model"></a>Model vláken
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je navržená tak, aby ukládala vývojáře z potíží s vlákny. V důsledku toho většina [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vývojáři nebude muset psát rozhraní, které používá více než jedno vlákno. Vzhledem k tomu, že programy s více vlákny jsou složité a obtížné je ladit, měli byste se jim vyhnout v případě existence řešení s jedním vláknem.

 Bez ohledu na to, jak to bylo navrženo, ale žádné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Framework nebude někdy moci poskytnout řešení s jedním vláknem pro každý problém. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se zavře, ale stále existují situace, kdy více vláken vylepšit [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] odezvy nebo výkon aplikace. Po prozkoumání některých materiálů se v tomto dokumentu prozkoumá některé z těchto situací a pak se dokončí diskuzí o některých podrobnostech nižší úrovně.

> [!NOTE]
> Toto téma popisuje dělení na vlákna pomocí metody <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> pro asynchronní volání. Můžete také provést asynchronní volání voláním metody <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, která jako parametr přijímá <xref:System.Action> nebo <xref:System.Func%601>.  Metoda <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> vrátí <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>, která má vlastnost <xref:System.Windows.Threading.DispatcherOperation.Task%2A>. Klíčové slovo `await` lze použít buď s <xref:System.Windows.Threading.DispatcherOperation>, nebo s přidruženým <xref:System.Threading.Tasks.Task>. Pokud potřebujete počkat synchronně pro <xref:System.Threading.Tasks.Task>, která je vrácena <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>, zavolejte metodu rozšíření <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A>.  Volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> způsobí zablokování. Další informace o použití <xref:System.Threading.Tasks.Task> k provádění asynchronních operací naleznete v tématu Task paralelismus.  Metoda <xref:System.Windows.Threading.Dispatcher.Invoke%2A> má také přetížení, které jako parametr přebírají <xref:System.Action> nebo <xref:System.Func%601>.  Pomocí metody <xref:System.Windows.Threading.Dispatcher.Invoke%2A> můžete provádět synchronní volání předáním delegáta, <xref:System.Action> nebo <xref:System.Func%601>.

<a name="threading_overview"></a>
## <a name="overview-and-the-dispatcher"></a>Přehled a dispečer
 Obvykle aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] začínají dvěma vlákny: jeden pro zpracování vykreslování a další pro správu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Vykreslování vlákna efektivně běží na pozadí, zatímco [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno přijímá vstup, zpracovává události, vykreslí obrazovku a spouští kód aplikace. Většina aplikací používá jedno vlákno [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], i když v některých situacích je nejlepší použít několik. Budeme s tímto příkladem pojednávat později.

 Vlákna [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zařadí do fronty pracovní položky v rámci objektu s názvem <xref:System.Windows.Threading.Dispatcher>. <xref:System.Windows.Threading.Dispatcher> vybere pracovní položky na základě priority a každý z nich provede dokončení.  Každé [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno musí mít alespoň jeden <xref:System.Windows.Threading.Dispatcher>a každý <xref:System.Windows.Threading.Dispatcher> může provádět pracovní položky v přesně jednom vlákně.

 Zdvih pro vytváření reagovat, uživatelsky přívětivých aplikací maximalizuje <xref:System.Windows.Threading.Dispatcher> propustnost tím, že udržuje pracovní položky malé. Tímto způsobem se položky nikdy nestarují do fronty <xref:System.Windows.Threading.Dispatcher> čekající na zpracování. Jakékoli vnímané zpoždění mezi vstupem a odpovědí může frustrovat uživatele.

 Jak pak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace za účelem zpracování velkých objemů operací? Co když váš kód zahrnuje velký výpočet nebo potřebuje dotaz na databázi na některém vzdáleném serveru? Obvykle je odpověď zpracovávat velkou operaci v samostatném vlákně, ale [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno je volné, aby bylo možné do položek ve frontě <xref:System.Windows.Threading.Dispatcher> zadarmo. Po dokončení operace se vrátí výsledek zpět do vlákna [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro zobrazení.

 V minulosti Windows umožňuje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvků, které jsou k dispozici pouze v vlákně, které je vytvořilo. To znamená, že vlákno na pozadí za určitou dlouhodobě běžící úlohu nemůže po dokončení aktualizovat textové pole. Systém Windows To zajistí, aby se zajistila integrita [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] komponent. Seznam by mohl vypadat neobvyklý, pokud jeho obsah byl během Malování aktualizován vláknem na pozadí.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má integrovaný mechanismus vzájemného vyloučení, který tuto koordinaci vynutil. Většina tříd v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odvozena od <xref:System.Windows.Threading.DispatcherObject>. V konstrukci <xref:System.Windows.Threading.DispatcherObject> ukládá odkaz na <xref:System.Windows.Threading.Dispatcher> propojený s aktuálně spuštěným vláknem. V důsledku toho <xref:System.Windows.Threading.DispatcherObject> přidruží k vláknu, které ho vytvoří. Během provádění programu může <xref:System.Windows.Threading.DispatcherObject> volat svou veřejnou <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> metodu. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> prověřuje <xref:System.Windows.Threading.Dispatcher> přidružené k aktuálnímu vláknu a porovná ho s odkazem na <xref:System.Windows.Threading.Dispatcher> uloženým během konstrukce. Pokud se neshodují, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> vyvolá výjimku. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> mají být volány na začátku každé metody, která patří do <xref:System.Windows.Threading.DispatcherObject>.

 Pokud [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]může změnit pouze jedno vlákno, jak se budou vlákna na pozadí pracovat s uživatelem? Vlákno na pozadí může položit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vláknu za účelem provedení operace za jeho jménem. Provede to registrací pracovní položky pomocí <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. Třída <xref:System.Windows.Threading.Dispatcher> poskytuje dvě metody pro registraci pracovních položek: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> a <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>. Obě metody naplánují delegáta pro spuštění. <xref:System.Windows.Threading.Dispatcher.Invoke%2A> je synchronní volání – to znamená, že se nevrátí, dokud vlákno [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] skutečně nedokončí provádění delegáta. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> je asynchronní a vrátí se hned.

 <xref:System.Windows.Threading.Dispatcher> řadí prvky ve své frontě podle priority. Při přidávání elementu do fronty <xref:System.Windows.Threading.Dispatcher> lze zadat deset úrovní. Tyto priority se udržují v <xref:System.Windows.Threading.DispatcherPriority> výčtu. Podrobné informace o úrovních <xref:System.Windows.Threading.DispatcherPriority> najdete v dokumentaci k Windows SDK.

<a name="samples"></a>
## <a name="threads-in-action-the-samples"></a>Vlákna v akci: ukázky

<a name="prime_number"></a>
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Aplikace s jedním vláknem s dlouhodobou kalkulací
 Většina grafických uživatelských rozhraní (GUI) stráví velkou část času nečinnosti při čekání na události, které jsou vygenerovány v reakci na interakci uživatele. S pečlivým programováním je možné tento čas nečinnosti použít, aniž by to ovlivnilo odezvu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Model vláken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nepovoluje vstup k přerušení operace, která probíhají ve vlákně [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. To znamená, že musíte mít jistotu, že se do <xref:System.Windows.Threading.Dispatcher> pravidelně dostanou nedokončené vstupní události před tím, než se zastarou.

 Vezměte v úvahu následující příklad:

 ![Snímek obrazovky, který zobrazuje vlákna z primárních čísel.](./media/threading-model/threading-prime-numbers.png)

 Tato jednoduchá aplikace se počítá směrem nahoru od tří, hledá se čísla na apostrofech. Když uživatel klikne na tlačítko **Start** , hledání začne. Když program najde primární, aktualizuje uživatelské rozhraní jeho zjišťováním. V jakémkoli okamžiku může uživatel hledání zastavit.

 I když je dostatek jednoduchého, hledání na základě prvotních čísel by mohlo jít trvale, což představuje některé problémy.  Pokud jsme celé vyhledávání poznamenali v obslužné rutině události Click tlačítka, nikdy neposkytneme [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vláknu možnost zpracovávat jiné události. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] by nebylo možné reagovat na vstupní nebo procesní zprávy. Nikdy nepřekreslí a nikdy nereaguje na kliknutí na tlačítko.

 Hledání na primárním čísle můžeme provést v samostatném vlákně, ale musíme řešit problémy s synchronizací. S přístupem s jedním vláknem můžeme přímo aktualizovat popisek, který uvádí největší nalezené apostrofy.

 Pokud budeme úlohu výpočtu narušit na spravovatelné bloky dat, můžeme se pravidelně vracet do <xref:System.Windows.Threading.Dispatcher> a zpracovávat události. Můžeme [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] příležitost předat a zpracovat vstup.

 Nejlepším způsobem, jak rozdělit dobu zpracování mezi výpočtem a zpracováním událostí, je spravovat výpočet z <xref:System.Windows.Threading.Dispatcher>. Pomocí metody <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> můžeme naplánovat kontroly prvotních čísel ve stejné frontě, ze které se [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] události vykreslí. V našem příkladu plánujeme vždy jenom jednu kontrolu primárního čísla. Po dokončení kontroly prvotního čísla naplánujeme další kontrolu hned. Tato kontrolu pokračuje až po zpracování nevyřízených [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] událostí.

 ![Snímek obrazovky, který zobrazuje frontu dispečera.](./media/threading-model/threading-dispatcher-queue.png)

 Microsoft Word provádí kontrolu pravopisu pomocí tohoto mechanismu. Kontrola pravopisu se provádí na pozadí s použitím času nečinnosti vlákna [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Pojďme se podívat na kód.

 Následující příklad ukazuje kód XAML, který vytváří uživatelské rozhraní.

 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]

 Následující příklad ukazuje kód na pozadí.

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]

 Následující příklad ukazuje obslužnou rutinu události pro <xref:System.Windows.Controls.Button>.

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]

 Kromě aktualizace textu na <xref:System.Windows.Controls.Button>je tato obslužná rutina odpovědná za plánování prvotní kontroly prvotních čísel přidáním delegáta do fronty <xref:System.Windows.Threading.Dispatcher>. Po dokončení této obslužné rutiny události po dokončení této obslužné rutiny bude <xref:System.Windows.Threading.Dispatcher> tento delegát vybrat k provedení.

 Jak jsme uvedli dřív, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> je <xref:System.Windows.Threading.Dispatcher> člen, který se používá k naplánování delegáta pro spuštění. V tomto případě zvolíme prioritu <xref:System.Windows.Threading.DispatcherPriority.SystemIdle>. <xref:System.Windows.Threading.Dispatcher> spustí tohoto delegáta pouze v případě, že neexistují žádné důležité události ke zpracování. odezva [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] je důležitější než kontrola počtu. Také předáte novému delegátovi, který představuje rutinu pro kontrolu čísel.

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]

 Tato metoda kontroluje, zda je následující liché číslo primární. Pokud je primární, metoda přímo aktualizuje `bigPrime`<xref:System.Windows.Controls.TextBlock> tak, aby odrážela jeho zjišťování. To můžeme udělat, protože výpočet se vyskytuje ve stejném vlákně, které jste použili k vytvoření komponenty. Zvolili jsme použití samostatného vlákna pro výpočet, musíme použít složitější synchronizační mechanismus a spustit aktualizaci ve vlákně [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Tuto situaci si ukážeme dál.

 Úplný zdrojový kód pro tuto ukázku najdete v tématu [aplikace s jedním vláknem s ukázkou dlouho běžícího výpočtu](https://go.microsoft.com/fwlink/?LinkID=160038) .

<a name="weather_sim"></a>
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Zpracování blokující operace s vláknem na pozadí
 Manipulace s blokujícími operacemi v grafické aplikaci může být obtížné. Nechceme volat metody blokování z obslužných rutin událostí, protože se zdá, že se aplikace zablokuje. Pro zpracování těchto operací můžeme použít samostatné vlákno, ale po dokončení musíme synchronizaci s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vláknem, protože nemůžeme přímo změnit grafické uživatelské rozhraní z našeho pracovního vlákna. K vkládání delegátů do <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna můžeme použít <xref:System.Windows.Threading.Dispatcher.Invoke%2A> nebo <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>. Nakonec se tyto delegáty spustí s oprávněním pro úpravu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvků.

 V tomto příkladu Napodobme vzdálené volání procedur, které načte předpověď počasí. K provedení tohoto volání používáme samostatné pracovní vlákno a při dokončení naplánujeme metodu aktualizace v <xref:System.Windows.Threading.Dispatcher> vlákna [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].

 ![Snímek obrazovky zobrazující uživatelské rozhraní počasí](./media/threading-model/threading-weather-ui.png)

 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]

 Níže jsou uvedeny některé podrobnosti.

- Vytvoření obslužné rutiny tlačítka

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]

 Po kliknutí na tlačítko zobrazíme vykreslování hodin a začnete ho animovat. Zakážeme toto tlačítko. Vyvoláme metodu `FetchWeatherFromServer` v novém vlákně a potom se vrátíme, což umožňuje, aby <xref:System.Windows.Threading.Dispatcher> zpracovávat události během čekání na shromáždění předpovědi počasí.

- Načítají se počasí.

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]

 V tomto příkladu nemáme v tomto příkladu žádný kód sítě. Místo toho simulujeme zpoždění přístupu k síti tím, že jsme nové vlákno umístili do režimu spánku po dobu čtyř sekund. V tuto chvíli je původní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno stále spuštěno a reaguje na události. Pokud to chcete zobrazit, opustili jsme animaci spuštěnou a tlačítky minimalizovat a maximalizovat i nadále fungují.

 Až se zpoždění dokončí a my jsme náhodně vybrali naši předpověď počasí, je čas na to, aby se nahlásil zpět do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ého vlákna. Provedeme to naplánováním volání `UpdateUserInterface` ve vlákně [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pomocí <xref:System.Windows.Threading.Dispatcher>tohoto vlákna. Předáte řetězec popisující počasí k tomuto plánovanému volání metody.

- Aktualizace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]

 Pokud <xref:System.Windows.Threading.Dispatcher> v vlákně [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] má čas, spustí plánované volání `UpdateUserInterface`. Tato metoda zastaví animaci hodin a vybere obrázek pro popis počasí. Zobrazuje tento obrázek a obnoví tlačítko "vyhodnotit předpověď".

<a name="multi_browser"></a>
### <a name="multiple-windows-multiple-threads"></a>Více oken, více vláken
 Některé aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vyžadují více oken nejvyšší úrovně. Je zcela přijatelné pro jednu kombinaci vláken/<xref:System.Windows.Threading.Dispatcher> pro správu více oken, ale někdy se může stát, že několik vláken vylepší úlohu. To platí zejména v případě, že existuje možnost, že jedno z oken bude monopolizovat vlákno.

 Průzkumník Windows funguje tímto způsobem. Každé nové okno Průzkumníka patří původnímu procesu, ale je vytvořeno pod kontrolou nezávislého vlákna.

 Pomocí ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Frame> můžeme zobrazit webové stránky. Snadno se dá vytvořit jednoduchá náhrada z Internet Exploreru. Začneme s důležitou funkcí: možnost otevřít nové okno Průzkumníka. Když uživatel klikne na tlačítko "nové okno", spustíme kopii našeho okna v samostatném vlákně. Tímto způsobem dlouho běžící nebo blokující operace v jednom z oken nezamkne všechna ostatní okna.

 Ve skutečnosti má model webového prohlížeče svůj vlastní složitý model vláken. Zvolili jsme to proto, že by měl být známý pro většinu čtenářů.

 Následující příklad ukazuje kód.

 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]

 Následující segmenty vlákna tohoto kódu jsou pro nás v tomto kontextu nejzajímavější:

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]

 Tato metoda je volána při kliknutí na tlačítko "nové okno". Vytvoří nové vlákno a spustí asynchronně.

 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]

 Tato metoda je výchozím bodem pro nové vlákno. Pod kontrolou tohoto vlákna vytvoříme nové okno. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] automaticky vytvoří novou <xref:System.Windows.Threading.Dispatcher> ke správě nového vlákna. K tomu, aby bylo okno funkční, je nutné začít <xref:System.Windows.Threading.Dispatcher>.

<a name="stumbling_points"></a>
## <a name="technical-details-and-stumbling-points"></a>Technické podrobnosti a body Stumbling

### <a name="writing-components-using-threading"></a>Zápis komponent pomocí dělení na vlákna
 Příručka pro vývojáře Microsoft .NET Framework popisuje vzor, jak může komponenta vystavovat asynchronní chování svým klientům (viz [Přehled asynchronních vzorů založených na událostech](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Předpokládejme například, že jsme chtěli zabalit metodu `FetchWeatherFromServer` do opakovaně použitelné, negrafické komponenty. Po standardním vzoru Microsoft .NET Framework by to vypadalo podobně jako v následujícím.

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]

 `GetWeatherAsync` by používal jeden z výše popsaných postupů, jako je například vytvoření vlákna na pozadí, pro asynchronní práci bez blokování volajícího vlákna.

 Jednou z nejdůležitějších částí tohoto modelu je volání metody *MethodName*`Completed` ve stejném vlákně, které volalo metodu *methodName*`Async`, která začíná na. To lze provést [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poměrně snadno, protože uložíte <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>, ale negrafickou komponentu lze použít pouze v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ch aplikacích, nikoli v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo ASP.NET programech.

 Třída <xref:System.Windows.Threading.DispatcherSynchronizationContext> řeší tuto potřebu – považuje se za zjednodušenou verzi <xref:System.Windows.Threading.Dispatcher>, která funguje i v jiných [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ch architekturách.

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]

### <a name="nested-pumping"></a>Vnořená pumpa
 V některých případech není možné zcela uzamknout [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno. Pojďme vzít v úvahu metodu <xref:System.Windows.MessageBox.Show%2A> třídy <xref:System.Windows.MessageBox>. <xref:System.Windows.MessageBox.Show%2A> nevrátí, dokud uživatel neklikne na tlačítko OK. Ale vytvoří okno, které musí mít smyčku zpráv, aby mohla být interaktivní. Čekáme na to, až uživatel klikne na tlačítko OK, původní okno aplikace nereaguje na vstup uživatele. Ale i nadále zpracovává zprávy o malování. Původní okno se překreslí samostatně, pokud je zahrnuto a odhaleno.

 ![Snímek obrazovky, který zobrazuje MessageBox s tlačítkem OK](./media/threading-model/threading-message-loop.png)

 U některých vláken se musí nacházet okno se zprávou. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] může vytvořit nové vlákno pouze pro okno se zprávou, ale toto vlákno by nemohlo vykreslit zakázané prvky do původního okna (zapamatuje si předchozí diskuzi o vzájemném vyloučení). Místo toho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá vnořený systém zpracování zpráv. Třída <xref:System.Windows.Threading.Dispatcher> obsahuje speciální metodu nazvanou <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>, která ukládá aktuální bod spuštění aplikace a potom zahájí novou smyčku zpráv. Po dokončení vnořené smyčky zpráv se provádění pokračuje po volání původního <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>.

 V tomto případě <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> udržuje kontext programu při volání <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType>a spustí novou smyčku zpráv pro překreslení okna na pozadí a zpracování vstupu do okna se zprávou. Když uživatel klikne na tlačítko OK a smaže automaticky otevírané okno, vnořená smyčka skončí a řízení pokračuje po volání <xref:System.Windows.MessageBox.Show%2A>.

### <a name="stale-routed-events"></a>Zastaralé směrované události
 Systém směrovanéch událostí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] upozorní celé stromy na vyvolání událostí.

 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]

 Když se na elipsě stiskne levé tlačítko myši, `handler2` se spustí. Po dokončení `handler2` je událost předána do objektu <xref:System.Windows.Controls.Canvas>, který používá `handler1` k jeho zpracování. K tomu dojde pouze v případě, že `handler2` explicitně neoznačí objekt události jako zpracovávaný.

 Je možné, že `handler2` bude trvat velkou dobu zpracování této události. `handler2` může používat <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> k zahájení vnořené smyčky zpráv, která se nevrátí na hodiny. Pokud `handler2` neoznačí událost jako zpracovanou, když je tato smyčka dokončená, událost se projde do stromu, i když je moc stará.

### <a name="reentrancy-and-locking"></a>Vícenásobný přístup a uzamykání
 Blokovací mechanizmus modulu CLR (Common Language Runtime) se chová přesně tak, jak je možné ho představit. může se stát, že vlákno ukončí operaci kompletně při požadavku na zámek. Ve skutečnosti vlákno nadále přijímá a zpracovává zprávy s vysokou prioritou. To pomáhá zabránit zablokování a dávat rozhraní s minimální odezvou, ale zavádí možnost drobných chyb.  Velká většina času, o které nepotřebujete nic vědět, ale za výjimečných okolností (obvykle zahrnující [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zprávy okna nebo součásti modelu COM STA) to může být velmi důležité.

 Většina rozhraní není sestavena s ohledem na bezpečnost vlákna, protože vývojáři pracují s předpokladem, že k [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nikdy nemá přístup více než jedno vlákno. V takovém případě může toto jediné vlákno provádět změny v prostředí v neočekávaných časech, což způsobuje, že by se mělo vyřešit tyto nenáročné účinky <xref:System.Windows.Threading.DispatcherObject> mechanismu vzájemného vyloučení. Vezměte v úvahu následující pseudokódu:

 ![Diagram, který zobrazuje Vícenásobný přístup zřetězení.](./media/threading-model/threading-reentrancy.png "ThreadingReentrancy")

 Ve většině času to je správné, ale v některých případech se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], kde takové neočekávané Vícenásobný přístup můžou způsobovat problémy. Takže v některých případech [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] volá <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>, které změní instrukci zámku pro toto vlákno na použití zámku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vícenásobný přístup-Free namísto obvyklého zámku CLR.

 Proč tým CLR zvolí toto chování? Musela se provádět s objekty modelu COM STA a s dokončovacím vláknem. Když je objekt uvolněn z paměti, je jeho `Finalize` metoda spuštěna ve vyhrazeném vlákně finalizační metody, nikoli v vlákně [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. V takovém případě se jedná o problém, protože objekt COM STA, který byl vytvořen ve vlákně [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], lze odstranit pouze ve vlákně [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. CLR odpovídá <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (v tomto případě použití `SendMessage`Win32's). Pokud je však vlákno [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] zaneprázdněno, vlákno finalizační metody je zastaveno a objekt COM STA nelze uvolnit, což způsobí vážnou nevracení paměti. Proto tým CLR provedl obtížné volání, aby zámky pracovaly způsobem, jakým dělají.

 Úkolem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je vyhnout se neočekávaným Vícenásobný přístup bez opětovného zavedení nevracení paměti, což znamená, že Vícenásobný přístup všude neblokujeme.

## <a name="see-also"></a>Viz také:

- [Vícevláknová aplikace s ukázkou dlouhotrvajícího výpočtu](https://go.microsoft.com/fwlink/?LinkID=160038)
