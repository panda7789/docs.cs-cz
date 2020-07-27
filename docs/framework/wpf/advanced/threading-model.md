---
title: Model vláken
description: Přečtěte si o situacích, kdy budete možná potřebovat více vláken v aplikaci Windows Presentation Foundation. Jsou upřednostňována řešení s jedním vláknem.
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
ms.openlocfilehash: 9b67b6ea2896e9e6fec57dee8d1013d54fab03fc
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166384"
---
# <a name="threading-model"></a>Model vláken
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]je navržena pro ukládání vývojářů z potíží s vlákny. V důsledku toho většina [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vývojářů nebude muset psát rozhraní, které používá více než jedno vlákno. Vzhledem k tomu, že programy s více vlákny jsou složité a obtížné je ladit, měli byste se jim vyhnout v případě existence řešení s jedním vláknem.

 Bez ohledu na to, jak to bylo navrženo, ale žádné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] rozhraní nikdy nebude moci poskytnout řešení s jedním vláknem pro každý problém. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]je blízko, ale stále existují situace, kdy více vláken vylepšuje [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] odezvu nebo výkon aplikace. Po prozkoumání některých materiálů se v tomto dokumentu prozkoumá některé z těchto situací a pak se dokončí diskuzí o některých podrobnostech nižší úrovně.

> [!NOTE]
> Toto téma popisuje dělení na vlákna pomocí <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metody pro asynchronní volání. Můžete také provést asynchronní volání voláním <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> metody, která přijímá <xref:System.Action> nebo <xref:System.Func%601> jako parametr.  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>Metoda vrátí <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601> , která má <xref:System.Windows.Threading.DispatcherOperation.Task%2A> vlastnost. Klíčové slovo lze použít `await` buď s <xref:System.Windows.Threading.DispatcherOperation> přidruženým, nebo <xref:System.Threading.Tasks.Task> . Pokud potřebujete počkat synchronně pro <xref:System.Threading.Tasks.Task> , který je vrácený <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601> , zavolejte <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> metodu rozšíření.  Volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> způsobí zablokování. Další informace o použití nástroje <xref:System.Threading.Tasks.Task> k provedení asynchronních operací naleznete v tématu Task paralelismus.  <xref:System.Windows.Threading.Dispatcher.Invoke%2A>Metoda má také přetížení, která přijímají <xref:System.Action> nebo <xref:System.Func%601> jako parametr.  Metodu lze použít <xref:System.Windows.Threading.Dispatcher.Invoke%2A> k provádění synchronních volání předáním delegáta <xref:System.Action> nebo <xref:System.Func%601> .

<a name="threading_overview"></a>
## <a name="overview-and-the-dispatcher"></a>Přehled a dispečer
 Obvykle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace začínají dvěma vlákny: jeden pro zpracování vykreslování a další pro správu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Vykreslování vlákna efektivně běží na pozadí, zatímco [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno přijímá vstup, zpracovává události, vykreslí obrazovku a spouští kód aplikace. Většina aplikací používá jedno [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno, i když v některých případech je nejvhodnější použít několik. Budeme s tímto příkladem pojednávat později.

 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]Vlákno vyřadí pracovní položky do fronty v rámci objektu s názvem <xref:System.Windows.Threading.Dispatcher> . <xref:System.Windows.Threading.Dispatcher>Vybere pracovní položky na základě priority a každý z nich provede dokončení.  Každé [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno musí mít alespoň jeden <xref:System.Windows.Threading.Dispatcher> a každý z nich <xref:System.Windows.Threading.Dispatcher> může spouštět pracovní položky v přesně jednom vlákně.

 Schopnost vytvářet reakce na uživatelsky přívětivé aplikace je maximalizovat <xref:System.Windows.Threading.Dispatcher> propustnost tím, že se pracovní položky podrží malými. Tímto způsobem se položky nikdy nevrátí do fronty, která <xref:System.Windows.Threading.Dispatcher> čeká na zpracování. Jakékoli vnímané zpoždění mezi vstupem a odpovědí může frustrovat uživatele.

 Jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace by pak měly zpracovávat velké operace? Co když váš kód zahrnuje velký výpočet nebo potřebuje dotaz na databázi na některém vzdáleném serveru? Obvykle je odpověď zpracovávat velkou operaci v samostatném vlákně, ale vlákno je volné, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aby bylo možné položky ve <xref:System.Windows.Threading.Dispatcher> frontě. Po dokončení velké operace může hlásit svůj výsledek zpátky do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna pro zobrazení.

 V historickém režimu umožňuje systému Windows [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] přístup k elementům pouze pomocí vlákna, které je vytvořilo. To znamená, že vlákno na pozadí za určitou dlouhodobě běžící úlohu nemůže po dokončení aktualizovat textové pole. Systém Windows To zajistí, aby se zajistila integrita [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] komponent. Seznam by mohl vypadat neobvyklý, pokud jeho obsah byl během Malování aktualizován vláknem na pozadí.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]má vestavěný mechanismus vzájemného vyloučení, který tuto koordinaci vynutil. Většina tříd [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je odvozena z <xref:System.Windows.Threading.DispatcherObject> . V konstrukci <xref:System.Windows.Threading.DispatcherObject> ukládá odkaz na <xref:System.Windows.Threading.Dispatcher> vazbu k aktuálně běžícímu vláknu. V důsledku toho <xref:System.Windows.Threading.DispatcherObject> přidruží ke vláknu, který ho vytvořil. Během provádění programu <xref:System.Windows.Threading.DispatcherObject> může zavolat jeho veřejnou <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> metodu. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>prověřuje <xref:System.Windows.Threading.Dispatcher> přidružení k aktuálnímu vláknu a porovná ho s <xref:System.Windows.Threading.Dispatcher> odkazem uloženým během konstrukce. Pokud se neshodují, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> vyvolá výjimku. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>má být volána na začátku každé metody patřící do <xref:System.Windows.Threading.DispatcherObject> .

 Pokud může upravit pouze jedno vlákno [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , jak vlákna na pozadí pracují s uživatelem? Vlákno na pozadí může požádat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno o provedení operace za jeho jménem. Provede to registrací pracovní položky s <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vláknem. <xref:System.Windows.Threading.Dispatcher>Třída poskytuje dvě metody pro registraci pracovních položek: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> a <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> . Obě metody naplánují delegáta pro spuštění. <xref:System.Windows.Threading.Dispatcher.Invoke%2A>je synchronní volání – to znamená, že se nevrátí, dokud [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno dokončí provádění delegáta. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>je asynchronní a vrátí se okamžitě.

 <xref:System.Windows.Threading.Dispatcher>Seřadí prvky ve své frontě podle priority. Při přidávání elementu do fronty je možné zadat deset úrovní <xref:System.Windows.Threading.Dispatcher> . Tyto priority se udržují ve <xref:System.Windows.Threading.DispatcherPriority> výčtu. Podrobné informace o <xref:System.Windows.Threading.DispatcherPriority> úrovních najdete v dokumentaci k Windows SDK.

<a name="samples"></a>
## <a name="threads-in-action-the-samples"></a>Vlákna v akci: ukázky

<a name="prime_number"></a>
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Aplikace s jedním vláknem s dlouhodobou kalkulací
 Většina grafických uživatelských rozhraní (GUI) stráví velkou část času nečinnosti při čekání na události, které jsou vygenerovány v reakci na interakci uživatele. S pečlivým programováním je možné tento čas nečinnosti použít, aniž by to ovlivnilo odezvu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Model vláken nepovoluje vstup k přerušení operace, která se odehrává ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákně. To znamená, že musíte mít jistotu, že se budete muset <xref:System.Windows.Threading.Dispatcher> pravidelně vracet do procesu probíhajících vstupních událostí.

 Uvažujte následující příklad:

 ![Snímek obrazovky, který zobrazuje vlákna z primárních čísel.](./media/threading-model/threading-prime-numbers.png)

 Tato jednoduchá aplikace se počítá směrem nahoru od tří, hledá se čísla na apostrofech. Když uživatel klikne na tlačítko **Start** , hledání začne. Když program najde primární, aktualizuje uživatelské rozhraní jeho zjišťováním. V jakémkoli okamžiku může uživatel hledání zastavit.

 I když je dostatek jednoduchého, hledání na základě prvotních čísel by mohlo jít trvale, což představuje některé problémy.  Pokud jsme celé vyhledávání poznamenali v obslužné rutině události Click tlačítka, nikdy neposkytneme [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno možnost zpracovávat jiné události. By nebylo možné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] reagovat na vstupní nebo procesní zprávy. Nikdy nepřekreslí a nikdy nereaguje na kliknutí na tlačítko.

 Hledání na primárním čísle můžeme provést v samostatném vlákně, ale musíme řešit problémy s synchronizací. S přístupem s jedním vláknem můžeme přímo aktualizovat popisek, který uvádí největší nalezené apostrofy.

 V případě, že úlohu výpočtu rozdělíte na spravovatelné bloky dat, můžeme se pravidelně vracet do <xref:System.Windows.Threading.Dispatcher> procesů a zpracovávat události. Můžeme předat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] možnost překreslit a zpracovat vstup.

 Nejlepším způsobem, jak rozdělit dobu zpracování mezi výpočtem a zpracováním událostí, je spravovat výpočet z <xref:System.Windows.Threading.Dispatcher> . Pomocí <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metody můžeme naplánovat kontroly prvotních čísel ve stejné frontě, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] z níž se události vykreslí. V našem příkladu plánujeme vždy jenom jednu kontrolu primárního čísla. Po dokončení kontroly prvotního čísla naplánujeme další kontrolu hned. Tato kontrolu pokračuje až po zpracování nevyřízených [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] událostí.

 ![Snímek obrazovky, který zobrazuje frontu dispečera.](./media/threading-model/threading-dispatcher-queue.png)

 Microsoft Word provádí kontrolu pravopisu pomocí tohoto mechanismu. Kontrola pravopisu se provádí na pozadí s použitím času nečinnosti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. Pojďme se podívat na kód.

 Následující příklad ukazuje kód XAML, který vytváří uživatelské rozhraní.

 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]

 Následující příklad ukazuje kód na pozadí.

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]

 Následující příklad ukazuje obslužnou rutinu události pro <xref:System.Windows.Controls.Button> .

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]

 Kromě aktualizace textu na <xref:System.Windows.Controls.Button> , je tato obslužná rutina zodpovědná za plánování prvotní kontroly prvotních čísel přidáním delegáta do <xref:System.Windows.Threading.Dispatcher> fronty. Po dokončení této obslužné rutiny události <xref:System.Windows.Threading.Dispatcher> bude tento delegát vybrán pro spuštění.

 Jak jsme se už dozvěděli dřív, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> je <xref:System.Windows.Threading.Dispatcher> člen použitý k naplánování delegáta pro provádění. V tomto případě zvolíme <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> prioritu. Spustí <xref:System.Windows.Threading.Dispatcher> tohoto delegáta pouze v případě, že neexistují žádné důležité události ke zpracování. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]odezva je důležitější než Kontrola čísla. Také předáte novému delegátovi, který představuje rutinu pro kontrolu čísel.

 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]

 Tato metoda kontroluje, zda je následující liché číslo primární. Pokud je primární, metoda přímo aktualizuje rozhraní tak, `bigPrime` <xref:System.Windows.Controls.TextBlock> aby odráželo jeho zjišťování. To můžeme udělat, protože výpočet se vyskytuje ve stejném vlákně, které jste použili k vytvoření komponenty. Zvolili jsme použití samostatného vlákna pro výpočet, musíme použít složitější synchronizační mechanismus a spustit aktualizaci ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákně. Tuto situaci si ukážeme dál.

 Úplný zdrojový kód pro tuto ukázku najdete v tématu [aplikace s jedním vláknem s ukázkou dlouho běžícího výpočtu](https://github.com/Microsoft/WPF-Samples/tree/master/Threading/SingleThreadedApplication) .

<a name="weather_sim"></a>
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Zpracování blokující operace s vláknem na pozadí
 Manipulace s blokujícími operacemi v grafické aplikaci může být obtížné. Nechceme volat metody blokování z obslužných rutin událostí, protože se zdá, že se aplikace zablokuje. Pro zpracování těchto operací můžeme použít samostatné vlákno, ale po dokončení musíme synchronizaci s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vláknem, protože nemůžeme přímo změnit grafické uživatelské rozhraní z našeho pracovního vlákna. Můžeme použít <xref:System.Windows.Threading.Dispatcher.Invoke%2A> nebo <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> pro vkládání delegátů do <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. Nakonec se tyto delegáty spustí s oprávněním pro úpravu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvků.

 V tomto příkladu Napodobme vzdálené volání procedur, které načte předpověď počasí. K provedení tohoto volání používáme samostatné pracovní vlákno a při dokončení naplánujeme metodu aktualizace ve <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákně.

 ![Snímek obrazovky zobrazující uživatelské rozhraní počasí](./media/threading-model/threading-weather-ui.png)

 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]

 Níže jsou uvedeny některé podrobnosti.

- Vytvoření obslužné rutiny tlačítka

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]

 Po kliknutí na tlačítko zobrazíme vykreslování hodin a začnete ho animovat. Zakážeme toto tlačítko. `FetchWeatherFromServer`Metodu vyvolá v novém vlákně a potom se vrátíme a umožníme <xref:System.Windows.Threading.Dispatcher> zpracování událostí během čekání na shromáždění předpovědi počasí.

- Načítají se počasí.

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]

 V tomto příkladu nemáme v tomto příkladu žádný kód sítě. Místo toho simulujeme zpoždění přístupu k síti tím, že jsme nové vlákno umístili do režimu spánku po dobu čtyř sekund. V tuto chvíli [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] je původní vlákno pořád spuštěné a reaguje na události. Pokud to chcete zobrazit, opustili jsme animaci spuštěnou a tlačítky minimalizovat a maximalizovat i nadále fungují.

 Až se zpoždění dokončí a my jsme náhodně vybrali naši předpověď počasí, je čas nahlásit zpět do [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. Provedeme to naplánováním volání `UpdateUserInterface` ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákně pomocí tohoto vlákna <xref:System.Windows.Threading.Dispatcher> . Předáte řetězec popisující počasí k tomuto plánovanému volání metody.

- Aktualizuje se[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]

     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]

 Pokud <xref:System.Windows.Threading.Dispatcher> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] má vlákno ve vlákně čas, spustí plánované volání `UpdateUserInterface` . Tato metoda zastaví animaci hodin a vybere obrázek pro popis počasí. Zobrazuje tento obrázek a obnoví tlačítko "vyhodnotit předpověď".

<a name="multi_browser"></a>
### <a name="multiple-windows-multiple-threads"></a>Více oken, více vláken
 Některé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace vyžadují více oken nejvyšší úrovně. Je zcela přijatelné pro jedno vlákno nebo <xref:System.Windows.Threading.Dispatcher> kombinaci ke správě více oken, ale někdy několik vláken má lepší úlohu. To platí zejména v případě, že existuje možnost, že jedno z oken bude monopolizovat vlákno.

 Průzkumník Windows funguje tímto způsobem. Každé nové okno Průzkumníka patří původnímu procesu, ale je vytvořeno pod kontrolou nezávislého vlákna.

 Pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame> ovládacího prvku můžeme zobrazit webové stránky. Snadno se dá vytvořit jednoduchá náhrada z Internet Exploreru. Začneme s důležitou funkcí: možnost otevřít nové okno Průzkumníka. Když uživatel klikne na tlačítko "nové okno", spustíme kopii našeho okna v samostatném vlákně. Tímto způsobem dlouho běžící nebo blokující operace v jednom z oken nezamkne všechna ostatní okna.

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

 Tato metoda je výchozím bodem pro nové vlákno. Pod kontrolou tohoto vlákna vytvoříme nové okno. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]automaticky vytvoří nový <xref:System.Windows.Threading.Dispatcher> pro správu nového vlákna. K tomu, aby bylo okno funkční, je třeba spustit <xref:System.Windows.Threading.Dispatcher> .

<a name="stumbling_points"></a>
## <a name="technical-details-and-stumbling-points"></a>Technické podrobnosti a body Stumbling

### <a name="writing-components-using-threading"></a>Zápis komponent pomocí dělení na vlákna
 Příručka pro vývojáře Microsoft .NET Framework popisuje vzor, jak může komponenta vystavovat asynchronní chování svým klientům (viz [Přehled asynchronních vzorů založených na událostech](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Předpokládejme například, že jsme chtěli zabalit `FetchWeatherFromServer` metodu do opakovaně použitelné, negrafované komponenty. Po standardním vzoru Microsoft .NET Framework by to vypadalo podobně jako v následujícím.

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]

 `GetWeatherAsync`použije jeden z výše popsaných postupů, jako je například vytvoření vlákna na pozadí pro asynchronní práci bez blokování volajícího vlákna.

 Jednou z nejdůležitějších částí tohoto modelu je volání metody *methodName* `Completed` ve stejném vlákně, které volalo metodu *methodName* , `Async` která začíná na. To lze provést [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poměrně snadno, protože je uložíte <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A> , ale negrafickou komponentu lze použít pouze v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacích, nikoli v model Windows Forms nebo ASP.NETch programech.

 <xref:System.Windows.Threading.DispatcherSynchronizationContext>Třída tuto potřebu řeší – považuje se za zjednodušenou verzi nástroje <xref:System.Windows.Threading.Dispatcher> , která funguje i v jiných [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] architekturách.

 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]

### <a name="nested-pumping"></a>Vnořená pumpa
 V některých případech není možné vlákno kompletně Uzamknout [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] . Pojďme vzít v úvahu <xref:System.Windows.MessageBox.Show%2A> metodu <xref:System.Windows.MessageBox> třídy. <xref:System.Windows.MessageBox.Show%2A>nevrátí se, dokud uživatel neklikne na tlačítko OK. Ale vytvoří okno, které musí mít smyčku zpráv, aby mohla být interaktivní. Čekáme na to, až uživatel klikne na tlačítko OK, původní okno aplikace nereaguje na vstup uživatele. Ale i nadále zpracovává zprávy o malování. Původní okno se překreslí samostatně, pokud je zahrnuto a odhaleno.

 ![Snímek obrazovky, který zobrazuje MessageBox s tlačítkem OK](./media/threading-model/threading-message-loop.png)

 U některých vláken se musí nacházet okno se zprávou. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]může vytvořit nové vlákno pouze pro okno se zprávou, ale toto vlákno nebude moci vykreslit zakázané prvky do původního okna (zapamatujte si předchozí diskuzi na vzájemné vyloučení). Místo toho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá vnořený systém zpracování zpráv. <xref:System.Windows.Threading.Dispatcher>Třída obsahuje speciální metodu s názvem <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> , která ukládá aktuální bod spuštění aplikace a následně zahájí novou smyčku zpráv. Po dokončení vnořené smyčky zpráv bude spuštění pokračovat po původním <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> volání.

 V tomto případě <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> udržuje kontext programu při volání <xref:System.Windows.MessageBox.Show%2A?displayProperty=nameWithType> a spustí novou smyčku zpráv pro překreslení okna na pozadí a zpracování vstupu do okna se zprávou. Když uživatel klikne na tlačítko OK a vymaže automaticky otevírané okno, vnořená smyčka skončí a řízení pokračuje po volání <xref:System.Windows.MessageBox.Show%2A> .

### <a name="stale-routed-events"></a>Zastaralé směrované události
 Systém směrovaného Event v nástroji [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] upozorní celé stromy na vyvolání událostí.

 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]

 Po stisknutí levého tlačítka myši na elipsu se `handler2` spustí. Po `handler2` dokončení se událost předává spolu s <xref:System.Windows.Controls.Canvas> objektem, který používá `handler1` ke zpracování. K tomu dojde pouze v případě, že `handler2` objekt události explicitně neoznačí jako zpracovávaný.

 Je možné, že `handler2` bude trvat značnou dobu zpracování této události. `handler2`může použít <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> k zahájení vnořené smyčky zpráv, která se nevrátí na hodiny. Pokud `handler2` aplikace neoznačí událost jako zpracovanou, když je tato smyčka dokončená, událost se předá do stromu, i když je to hodně staré.

### <a name="reentrancy-and-locking"></a>Vícenásobný přístup a uzamykání
 Blokovací mechanizmus modulu CLR (Common Language Runtime) se chová přesně tak, jak je možné ho představit. může se stát, že vlákno ukončí operaci kompletně při požadavku na zámek. Ve skutečnosti vlákno nadále přijímá a zpracovává zprávy s vysokou prioritou. To pomáhá zabránit zablokování a dávat rozhraní s minimální odezvou, ale zavádí možnost drobných chyb.  Velká většina času, o které nepotřebujete nic vědět, ale za výjimečných okolností (obvykle se týká zpráv oken Win32 nebo komponent modelu COM STA), se může jednat o znalost.

 Většina rozhraní není sestavena s ohledem na bezpečnost vlákna, protože vývojáři pracují s předpokladem, že k [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] přístupu nikdy nemá přístup více než jedno vlákno. V takovém případě může toto jediné vlákno provádět změny v prostředí v neočekávaných časech, což způsobuje, že by se <xref:System.Windows.Threading.DispatcherObject> měl vyřešit mechanismus vzájemného vyloučení. Vezměte v úvahu následující pseudokódu:

 ![Diagram, který zobrazuje Vícenásobný přístup zřetězení.](./media/threading-model/threading-reentrancy.png "ThreadingReentrancy")

 Ve většině času to je správné, ale v některých případech se může stát, že by [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] takové neočekávané vícenásobný přístupy skutečně způsobily problémy. Takže v určitých klíčových časech [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] volání <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A> , která mění instrukci zámku pro toto vlákno, aby používala [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Zámek Vícenásobný přístup bez normálního zámku CLR.

 Proč tým CLR zvolí toto chování? Musela se provádět s objekty modelu COM STA a s dokončovacím vláknem. Když je objekt uvolněn z paměti, `Finalize` je jeho metoda spuštěna ve vyhrazeném vlákně finalizační metody, nikoli v [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákně. V tomto případě se jedná o problém, protože objekt COM STA, který byl vytvořen ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákně, lze odstranit pouze ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákně. CLR odpovídá <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (v tomto případě použití Win32's `SendMessage` ). Pokud je ale [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno zaneprázdněno, vlákno finalizační metody je zastaveno a objekt COM STA nelze uvolnit, což způsobí závažnou nevracení paměti. Proto tým CLR provedl obtížné volání, aby zámky pracovaly způsobem, jakým dělají.

 Úkolem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je zabránit neočekávanému Vícenásobný přístup, aniž byste museli znovu zavádět nevrácenou paměť, což znamená, že nebudeme zablokovat Vícenásobný přístup všude.

## <a name="see-also"></a>Viz také

- [Vícevláknová aplikace s ukázkou dlouhotrvajícího výpočtu](https://github.com/Microsoft/WPF-Samples/tree/master/Threading/SingleThreadedApplication)
