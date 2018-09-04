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
ms.openlocfilehash: 9e8bcd4503ec840e46022a55cc08dc0610eaa60b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512463"
---
# <a name="threading-model"></a>Model vláken
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] slouží k uložení vývojáři z obtížné dělení na vlákna. V důsledku toho většina [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vývojáři nebudete muset psát rozhraní, které používá více než jedno vlákno. Protože s více vlákny jsou složité a těžko ladění, mělo by se vyhnout při existují řešení s jedním vláknem.  
  
 Bez ohledu na to jak dobře navržený, ale ne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] někdy framework budou moci poskytnout řešení s jedním vláknem pro každý druh problému. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje zavřít, ale stále existují situace, kdy více vláken zvýšit [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] výkonu rychlost odezvy nebo aplikace. Tento dokument po diskuze o některých materiálu na pozadí, zkoumá některé z těchto situací a poté dojde k závěru představíme některé podrobnosti nižší úrovně.  
  

  
> [!NOTE]
>  Toto téma popisuje práce s vlákny pomocí <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metody pro asynchronní volání. Můžete také provádět asynchronní volání voláním <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> metodu, která trvat <xref:System.Action> nebo <xref:System.Func%601> jako parametr.  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> Metoda vrátí hodnotu <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>, který má <xref:System.Windows.Threading.DispatcherOperation.Task%2A> vlastnost. Můžete použít `await` – klíčové slovo se buď <xref:System.Windows.Threading.DispatcherOperation> nebo přidružené <xref:System.Threading.Tasks.Task>. Pokud budete muset počkat synchronně <xref:System.Threading.Tasks.Task> , který je vrácen <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>, volání <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> – metoda rozšíření.  Volání <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> povede k zablokování. Další informace o používání <xref:System.Threading.Tasks.Task> k provádění asynchronních operací, najdete v článku funkční paralelismus.  <xref:System.Windows.Threading.Dispatcher.Invoke%2A> Metoda má také přetížení, která přijímají <xref:System.Action> nebo <xref:System.Func%601> jako parametr.  Můžete použít <xref:System.Windows.Threading.Dispatcher.Invoke%2A> předáním delegátu, volá metodu provádět synchronní <xref:System.Action> nebo <xref:System.Func%601>.  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>Přehled a dispečer  
 Obvykle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace začínat dvěma vlákny: jeden pro zpracování vykreslování a druhý pro správu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Vlákno vykreslování efektivně se spustí na pozadí při [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno přijímá vstup, zpracovává události, jsou vykreslovány na obrazovce a spouští kód aplikace. Většina aplikací pomocí jediné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna, i když v některých situacích je nejvhodnější použít několik. Tomu se budeme podrobněji to na příkladu později.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Front vláken pracovní položky v objektu s názvem <xref:System.Windows.Threading.Dispatcher>. <xref:System.Windows.Threading.Dispatcher> Vybere pracovních položek na základě priority a spuštění každé z nich dokončen.  Každý [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna musí mít aspoň jeden <xref:System.Windows.Threading.Dispatcher>a každý <xref:System.Windows.Threading.Dispatcher> pracovních položek můžete spustit v přesně jedno vlákno.  
  
 Trik, jak zajistit k vytváření aplikací s rychlou odezvou a uživatelsky vstřícného je maximalizace <xref:System.Windows.Threading.Dispatcher> propustnost udržováním malé pracovní položky. Tento způsob, jak položky nikdy se zastaralé chladniček na <xref:System.Windows.Threading.Dispatcher> fronty čekající na zpracování. Případné patrné zpoždění mezi vstup a odpovědi může frustrovat uživatele.  
  
 Jak jsou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace by měl zpracovávat velký objem operací? Co když kód zahrnuje velké výpočtu nebo potřebuje dotazovat databázi na některé vzdáleném serveru? Odpověď je obvykle pro zpracování velkých objemů operace v samostatném vlákně, byste museli opustit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno free mají tendenci k položkám v <xref:System.Windows.Threading.Dispatcher> fronty. Po dokončení operace velké objemy se může hlásit svůj výsledek zpět [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vláken k zobrazení.  
  
 V minulosti [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] umožňuje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvků, které mají přístup pouze vlákno, které byly vytvořeny. To znamená, že nelze vlákna na pozadí starosti některé dlouhotrvající úlohu po dokončení aktualizovat textové pole. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] To umožňuje zajistit integritu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] komponenty. Pole se seznamem vyhledat strangeová, pokud jeho obsah byly aktualizovány ve vlákně na pozadí během vykreslování.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] má integrovanou vzájemné vyloučení mechanismus, který vynucuje tato koordinace. Většina tříd v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odvozovat <xref:System.Windows.Threading.DispatcherObject>. Při konstrukci <xref:System.Windows.Threading.DispatcherObject> uchovává odkaz na <xref:System.Windows.Threading.Dispatcher> propojené s aktuálně běžícímu vláknu. V důsledku toho <xref:System.Windows.Threading.DispatcherObject> přidruží vlákno, které ji vytvoří. Při provádění programu <xref:System.Windows.Threading.DispatcherObject> můžete volat jeho veřejné <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> metoda. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> prozkoumá <xref:System.Windows.Threading.Dispatcher> spojené s aktuálním vláknem a porovná ji <xref:System.Windows.Threading.Dispatcher> odkazovat na uložené během konstrukce. Pokud se neshodují, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> vyvolá výjimku. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> je určena k volání na začátku každé metodu, která náleží <xref:System.Windows.Threading.DispatcherObject>.  
  
 Pokud pouze jedno vlákno může změnit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], jak vláken na pozadí komunikovat s uživatelem? Vlákna na pozadí můžete klást [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno pro provádění operací na jejím jménem. Dělá to tak, že zaregistrujete pracovní položka s <xref:System.Windows.Threading.Dispatcher> z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. <xref:System.Windows.Threading.Dispatcher> Třídy nabízí dvě metody pro registraci pracovních položek: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> a <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>. Obě metody naplánovat delegáta pro spuštění. <xref:System.Windows.Threading.Dispatcher.Invoke%2A> je synchronní volání – to znamená, ho nevrací až [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] podproces dokončí ve skutečnosti spouští delegáta. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> je asynchronní a vrátí hodnotu okamžitě.  
  
 <xref:System.Windows.Threading.Dispatcher> Řadí prvky podle priority v příslušné fronty. Existují deset úrovně, které může být určen při přidávání element, který má <xref:System.Windows.Threading.Dispatcher> fronty. Tyto priority jsou zachována ve <xref:System.Windows.Threading.DispatcherPriority> výčtu. Podrobné informace o <xref:System.Windows.Threading.DispatcherPriority> úrovních najdete v [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] dokumentaci.  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>Vlákna v akci: ukázky  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Aplikace s jedním vláknem s dlouhotrvající výpočtu  
 Většina [!INCLUDE[TLA#tla_gui#plural](../../../../includes/tlasharptla-guisharpplural-md.md)] výdajů velkou část svůj čas nečinnosti při čekání na události, které jsou generovány v reakci na interakci uživatele. Pečlivé programování s nečinnosti slouží konstruktivně, aniž by to mělo dopad na odezvu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Model vláken neumožňuje zadání přerušit probíhající operace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. To znamená, že musí být potřeba vrátit <xref:System.Windows.Threading.Dispatcher> pravidelně k procesu čekající události vstupu než uživatelé získají zastaralé.  
  
 Vezměte v úvahu v následujícím příkladu:  
  
 ![Snímek obrazovky prvočísel](../../../../docs/framework/wpf/advanced/media/threadingprimenumberscreenshot.PNG "ThreadingPrimeNumberScreenShot")  
  
 Tato jednoduchá aplikace počítá směrem nahoru ve třech, vyhledání prvočísel. Pokud uživatel klikne **Start** tlačítko hledání začne. Když program vyhledá prime, aktualizuje uživatelské rozhraní s jeho zjišťování. V kterékoli fázi můžete uživatele zastavit hledání.  
  
 I když je dostatečně jednoduchá, hledání prime číslo může přechod na forever, který představuje určité obtíže.  Pokud jsme zpracovat celé hledání uvnitř obslužné rutiny události kliknutí tlačítka, by nikdy poskytujeme [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna příležitost dobře se zpracování jiných událostí. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Nebudou moct reagovat na vstup nebo proces zprávy. To by nikdy repaint a nikdy reakce na kliknutí na tlačítko.  
  
 Jsme mohli provádět vyhledávání prime číslo v samostatném vlákně, ale pak budeme muset řešit problémy synchronizace. S přístupem s jedním vláknem, abychom mohli přímo aktualizovat popisek, který obsahuje seznam největší prime nalezen.  
  
 Pokud jsme rozdělte úkol výpočtu rozčlenit na zvládnutelné dávky, budeme pravidelně se vrátit na <xref:System.Windows.Threading.Dispatcher> a zpracovávat události. Můžeme poskytnout [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] příležitost repaint a zpracovat vstup.  
  
 Ke správě výpočtu z je nejlepší způsob, jak rozdělit doba zpracování mezi výpočet a zpracování událostí <xref:System.Windows.Threading.Dispatcher>. Pomocí <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metoda, jsme naplánovat kontroly prime číslo ve stejné fronty, která [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] události jsou vykreslovány vedle z. V našem příkladu jsme naplánovat jenom jedno číslo prime kontrolu najednou. Po dokončení kontroly prime číslo k další kontrole jsme naplánovat okamžitě. Tato kontrola probíhá až poté, co čekající [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] události byly zpracovány.  
  
 ![Dispečer fronty obrázek](../../../../docs/framework/wpf/advanced/media/threadingdispatcherqueue.PNG "ThreadingDispatcherQueue")  
  
 [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)] provede kontrolu pravopisu pomocí tohoto mechanismu. Kontrola pravopisu probíhá na pozadí pomocí doby nečinnosti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. Pojďme se podívat na kód.  
  
 Následující příklad ukazuje, XAML, který vytvoří uživatelské rozhraní.  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 Následující příklad ukazuje kód na pozadí.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 Následující příklad ukazuje obslužnou rutinu události pro <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 Kromě aktualizace textu na <xref:System.Windows.Controls.Button>, tato obslužná rutina zodpovídá za plánování první kontrola prime číslo tak, že přidáte delegáta, kterého <xref:System.Windows.Threading.Dispatcher> fronty. Později po této obslužné rutiny události dokončí svou práci <xref:System.Windows.Threading.Dispatcher> vybere tento delegát pro spuštění.  
  
 Jak už jsme zmínili výše, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> je <xref:System.Windows.Threading.Dispatcher> členů používají k plánování delegáta pro spuštění. V tomto případě zvolíme <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> priority. <xref:System.Windows.Threading.Dispatcher> Tento delegát se spustí, pouze v případě, že neexistují žádné důležité události ke zpracování. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] schopnost reagovat je důležitější než číslo kontrolu. Můžeme také předat nový delegát představující rutina kontrola číslo.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 Tato metoda ověří, zda je nejbližší liché číslo prime. Pokud je primární, metoda přímo aktualizuje `bigPrime` <xref:System.Windows.Controls.TextBlock> tak, aby odrážely jeho zjišťování. Můžeme to udělat, protože dochází k výpočtu ve stejném vláknu, která byla použita k vytvoření komponenty. Zvolili jsme použít pro výpočet samostatném vlákně, měli jsme pro složitější mechanismus synchronizace a provádění aktualizací v [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. Ukážeme si tuto situaci dále.  
  
 Úplný zdrojový kód pro tuto ukázku, najdete v článku [jedno vláknové objekty aplikace s ukázkou dlouhotrvající výpočtu](https://go.microsoft.com/fwlink/?LinkID=160038)  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Zpracování blokující operace s vlákna na pozadí  
 Zpracování blokující operace v Grafická aplikace může být obtížné. Nechceme volání metod blokování z obslužné rutiny událostí, protože aplikace se zobrazí zablokovat a. Používáme samostatného vlákna ke zpracování těchto operací, ale když máme Hotovo, máme pro synchronizaci se [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno, protože jsme nemůžete upravovat přímo [!INCLUDE[TLA2#tla_gui](../../../../includes/tla2sharptla-gui-md.md)] z našich pracovní vlákno. Můžeme použít <xref:System.Windows.Threading.Dispatcher.Invoke%2A> nebo <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> k vložení do delegátů <xref:System.Windows.Threading.Dispatcher> z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. Nakonec se spustí tyto delegáty s oprávněním k úpravě [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy.  
  
 V tomto příkladu jsme napodobovat vzdálené volání procedury, která načte předpověď počasí. Používáme samostatné pracovní vlákno k provedení tohoto volání a můžeme plánovat metodu aktualizace v <xref:System.Windows.Threading.Dispatcher> z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna, když jsme hotovi.  
  
 ![Snímek obrazovky uživatelského rozhraní weather](../../../../docs/framework/wpf/advanced/media/threadingweatheruiscreenshot.PNG "ThreadingWeatherUIScreenShot")  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 Následují některé podrobnosti zaznamenán.  
  
-   Vytvoření obslužné rutiny tlačítko  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 Při kliknutí na tlačítko můžeme zobrazit kreslení hodiny a spustit animaci. Tlačítko Zakážeme. Jsme vyvolat `FetchWeatherFromServer` metoda v nové vlákno a pak jsme vrácení, což <xref:System.Windows.Threading.Dispatcher> kvůli zpracování událostí, zatímco čekáme shromažďovat předpovědí počasí.  
  
-   Načítají se počasí  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 Abychom si to nekomplikovali, nemáme ve skutečnosti všechny sítě kód v tomto příkladu. Místo toho můžeme simulovat zpoždění síťového přístupu tak, že vložíte do režimu spánku čtyři sekundy naše nové vlákno. V tuto chvíli původní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna je stále spuštěná a reagovat na události. Ukážeme vám to, že jste ponechali jsme animace spuštěna a minimalizovat a maximalizovat tlačítka také fungovat dál.  
  
 Po dokončení zpoždění a náhodně jsme vybrali naše předpovědí počasí, je čas zprávy zpět [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. Provedeme to pomocí plánování volání `UpdateUserInterface` v [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vláken pomocí bylo vlákno <xref:System.Windows.Threading.Dispatcher>. Můžeme předat řetězec popisující počasí pro toto volání metody naplánované.  
  
-   Aktualizuje se [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 Když <xref:System.Windows.Threading.Dispatcher> v [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno má čas, spustí naplánované volání `UpdateUserInterface`. Tato metoda animace hodiny se zastaví a vybere bitovou kopii k popisu počasí. Zobrazí tuto bitovou kopii a obnoví na tlačítko "načítání forecast".  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>Více Windows, více vláken  
 Některé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace vyžadují více oken nejvyšší úrovně. Je to naprosto přijatelné pro jedno vlákno /<xref:System.Windows.Threading.Dispatcher> kombinaci ke správě více oken, ale někdy několik vláken dělat lépe. To je obzvláště hodnotu true, že pokud je pravděpodobné, že jedna z windows se monopolizovat všechny vlákna.  
  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] Průzkumník funguje tímto způsobem. Každé nové okno Průzkumníka patří k původní procesu, ale je vytvořené v rámci ovládacího prvku nezávislé vlákna.  
  
 Pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame> ovládacího prvku, zobrazíme webové stránky. Můžeme snadno vytvořit jednoduchý [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] nahradit. Začneme s důležitou funkcí: možnost otevřete nové okno Průzkumníka. Když uživatel klepne "nové okno" tlačítko, můžeme spustit kopii naše okna v samostatném vlákně. Tímto způsobem, dlouhotrvající nebo blokující operace v jednom ovládacím prvku windows nebudou uzamčení všech ostatních oken.  
  
 Model webového prohlížeče ve skutečnosti má svůj vlastní složité vláken model. Zvolili jsme ji vzhledem k tomu, že by mělo být známé většina čtenářů.  
  
 Následující příklad ukazuje kód.  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 Následující vláken segmenty tohoto kódu, které jsou zajímá nejvíce, nám v tomto kontextu:  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 Tato metoda je volána, když "nové okno" po kliknutí na tlačítko. Vytvoří nové vlákno a spustí asynchronně.  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 Tato metoda je výchozím bodem pro nové vlákno. Vytvoříme nové okno pod kontrolou toto vlákno. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] automaticky vytvoří nový <xref:System.Windows.Threading.Dispatcher> ke správě nového vlákna. Všechny musíme udělat, aby byly v okně funkční, je začít <xref:System.Windows.Threading.Dispatcher>.  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>Technické podrobnosti a Stumbling body  
  
### <a name="writing-components-using-threading"></a>Zápis komponent pomocí dělení na vlákna  
 Microsoft .NET Framework Developer's Guide popisuje vzor jak součásti můžete zveřejnit asynchronní chování svým klientům (viz [založený na událostech přehled asynchronních vzorů](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Například předpokládejme, že jsme chtěli balíček `FetchWeatherFromServer` metoda do komponenty opakovaně použitelné, které nepodporují grafiku. Následující standardní vzor rozhraní Microsoft .NET Framework vypadat přibližně takto.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync` by použijte jeden z technik popsaných výše, jako je například vytváření vlákna na pozadí, proveďte práci asynchronně, ne blokování volajícího vlákna.  
  
 Jednou z vašich nejdůležitějších částí tohoto modelu je volání *MethodName* `Completed` ve stejném vlákně, který volá metodu *MethodName* `Async` metoda začínat. Můžete tak učinit pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poměrně snadno uložením <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>–, ale které nepodporují grafiku komponenta může pouze použít ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, není v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] programy.  
  
 <xref:System.Windows.Threading.DispatcherSynchronizationContext> Třídy řeší tyto potřeby – ho představit jako zjednodušenou verzi <xref:System.Windows.Threading.Dispatcher> , který funguje s jinými [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] i architektury.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>Vnořené – čerpání  
 Někdy není možné úplně zamčení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. Pojďme se podívat <xref:System.Windows.MessageBox.Show%2A> metodu <xref:System.Windows.MessageBox> třídy. <xref:System.Windows.MessageBox.Show%2A> nevrací se, dokud uživatel neklikne na tlačítko OK. Ale vytváří okno, které musí mít interaktivní smyčku zpráv. Zatímco čekáme na uživatele kliknutím na tlačítko OK, neodpovídá původní okna aplikace na vstup uživatele. Nicméně, dál zpracovávat malovat zprávy. V původním okně překreslí samotná popsaná a zobrazení.  
  
 ![MessageBox tlačítko "OK"](../../../../docs/framework/wpf/advanced/media/threadingnestedpumping.png "ThreadingNestedPumping")  
  
 Některé vlákno musí mít na starost okno zprávy. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvořit nové vlákno jen pro okno zprávy, ale toto vlákno nebudou moct vykreslení zakázané prvků v okně původní (Nezapomeňte starší diskuzi o vzájemné vyloučení). Místo toho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá vnořené zprávy systému zpracování. <xref:System.Windows.Threading.Dispatcher> Třída zahrnuje zvláštní metodu nazvanou <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>, který pak ukládá aktuální bod provádění aplikace začíná nové smyčky zpráv. Po dokončení vnořené zpráva smyčky, provádění pokračuje po původním <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> volání.  
  
 V takovém případě <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> udržuje kontextu program na volání <xref:System.Windows.MessageBox>.<xref:System.Windows.MessageBox.Show%2A>, a spustí nový smyčky zpráv repaint pozadí okna a zpracovat vstup pro okno zprávy. Když uživatel klikne na tlačítko OK a vymaže v automaticky otevíraném okně, vnořené smyčku ukončí a obnoví ovládací prvek po volání <xref:System.Windows.MessageBox.Show%2A>.  
  
### <a name="stale-routed-events"></a>Zastaralé směrovaných událostí  
 Systém směrovaných událostí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] upozorní celé struktury, když jsou vyvolány události.  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 Když se stiskne levé tlačítko myši nad třemi tečkami `handler2` provádí. Po `handler2` dokončí, události se předají <xref:System.Windows.Controls.Canvas> objektu, který používá `handler1` ke zpracování. K tomu dojde pouze v případě `handler2` nemá explicitně označit objekt události jako zpracování.  
  
 Je možné, že `handler2` zabere značnou dobu zpracování této události. `handler2` použít <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> zahájíte vnořené smyčku, která nevrací hodin. Pokud `handler2` nemá značka události jako zpracované tuto smyčku zpráv po dokončení, události je předán směrem nahoru, i když je velmi staré.  
  
### <a name="reentrancy-and-locking"></a>Vícenásobný přístup a zamykání  
 Mechanismus zamykání z [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] nechová stejně jako může být jeden imagine; očekávat vlákno provádění operace zcela při žádosti o zámek. Ve skutečnosti vlákno nadále přijímat a zpracovávat zprávy s vysokou prioritou. To pomáhá zabránit zablokování a nastavte minimálně responzivní rozhraní, ale přináší možnost drobné chyby.  Většinu času není nutné nic vědět o to, ale za výjimečných okolností (obvykle zahrnující [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] zprávy okna nebo komponenty modelu COM STA) to může být vhodné vědět.  
  
 Většina rozhraní nejsou vytvořené pomocí bezpečný přístup z více vláken v úvahu vzhledem k tomu, že vývojáři pracují za předpokladu, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nikdy je nevyužili ve více než jedno vlákno. V tomto případě, že jedno vlákno může provést změny v prostředí v neočekávanou dobu, způsobí tyto nesprávně dopad, který <xref:System.Windows.Threading.DispatcherObject> mechanismus vzájemné vyloučení by měl řešit. Vezměte v úvahu následujícím pseudokódu:  
  
 ![Práce s vlákny opětovný vstup diagram](../../../../docs/framework/wpf/advanced/media/threadingreentrancy.png "ThreadingReentrancy")  
  
 Ve většině případů je správné věci, ale existují situace v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kde takové neočekávané vícenásobného přístupu může ve skutečnosti způsobovat problémy. Ano, v určitých časech klíče [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] volání <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>, instrukce zámek pro toto vlákno použít změny, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] opětovné zadání bez zámku, namísto obvyklého [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zámku.  
  
 Proč nebyla [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] týmu zvolte toto chování? To museli dělat s objekty COM STA a dokončení vlákna. Pokud objekt je uvolněna, jeho `Finalize` metoda běží na vyhrazených finalizační podproces, není [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. A v něm je problém, protože COM STA objekt, který byl vytvořen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno se dá uvolnit pouze na [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákna. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Nemá odpovídající <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (v tomto případě pomocí na Win32 `SendMessage`). Avšak v tom případě [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno je zaneprázdněný, je zastaven a proces vlákna finalizační metody a objekt modelu COM STA nelze zrušit, vytváří nevracení paměti vážné. Proto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] týmu provedené složité volání zámky pracovat způsobem, aby dělají.  
  
 Úloha pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je vyhnout se neočekávaným opětovný vstup bez opětovného zavedení nevracení paměti, což je důvod, proč nedošlo k blokování opětovný vstup všude, kde.  
  
## <a name="see-also"></a>Viz také  
 [Aplikace s jedním vláknem s ukázkou dlouhotrvající výpočtu](https://go.microsoft.com/fwlink/?LinkID=160038)
