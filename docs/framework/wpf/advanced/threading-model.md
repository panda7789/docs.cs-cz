---
title: "Model vláken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f598cecef2d0994692f197df09e9befc39a58723
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="threading-model"></a>Model vláken
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]slouží k uložení vývojáři z obtíže dělení na vlákna. V důsledku toho většina [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vývojáři nebudete muset psát rozhraní, které používá více než jedno vlákno. Protože programy s více vlákny složitá a obtížná k ladění, by měla při řešení jednovláknové existovat vyloučeno.  
  
 Bez ohledu na tom, jak dobře navržen, ale ne [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] framework někdy budou moci poskytuje řešení s jedním podprocesem pro každý řazení problému. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]dodává zavřít, ale jsou stále situacích, kde více vláken zvýšit [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] výkonu odezvy nebo aplikace. Tento dokument po hovoříte o některé základní informace, jsou zde popsány některé z těchto situací a je uzavřen, přičemž se zabývat některé podrobnosti nižší úrovně.  
  

  
> [!NOTE]
>  Toto téma popisuje dělení na vlákna pomocí <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metody pro asynchronní volání. Můžete také provést asynchronní volání voláním <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> metodu, která trvat <xref:System.Action> nebo <xref:System.Func%601> jako parametr.  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A> Metoda vrátí <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>, který má <xref:System.Windows.Threading.DispatcherOperation.Task%2A> vlastnost. Můžete použít `await` – klíčové slovo s buď <xref:System.Windows.Threading.DispatcherOperation> nebo s přiřazenou třídou <xref:System.Threading.Tasks.Task>. Pokud potřebujete synchronně čekat <xref:System.Threading.Tasks.Task> , je vrácen rutinou <xref:System.Windows.Threading.DispatcherOperation> nebo <xref:System.Windows.Threading.DispatcherOperation%601>, volání <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> metoda rozšíření.  Volání metody <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> bude mít za následek vzájemné zablokování. Další informace o používání <xref:System.Threading.Tasks.Task> k provedení asynchronních operací, najdete v části paralelismus.  <xref:System.Windows.Threading.Dispatcher.Invoke%2A> Metoda má také přetížení, které provést <xref:System.Action> nebo <xref:System.Func%601> jako parametr.  Můžete použít <xref:System.Windows.Threading.Dispatcher.Invoke%2A> metoda aby synchronní volání předáním v delegáta, <xref:System.Action> nebo <xref:System.Func%601>.  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>Přehled a dispečera  
 Obvykle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] spustit aplikace se dvěma vlákny: jeden pro zpracování vykreslování a druhou pro správu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Vlákno vykreslování efektivně spustí skrytě na pozadí při [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno obdrží vstup, zpracovává události, vybarví obrazovky a spouští kód aplikace. Většina aplikací používá jeden [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vláken, i když v některých případech je nejvhodnější použít několik. Probereme to na příkladu později.  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Vlákno fronty pracovní položky v rámci objektu s názvem <xref:System.Windows.Threading.Dispatcher>. <xref:System.Windows.Threading.Dispatcher> Vybere pracovních položek na základě priority a spustí každé z nich k dokončení.  Každý [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno musí mít alespoň jeden <xref:System.Windows.Threading.Dispatcher>a každou <xref:System.Windows.Threading.Dispatcher> můžete spustit pracovní položky v přesně jedno vlákno.  
  
 Základem pro vytváření aplikací reakce, uživatelsky přívětivý je maximalizovat <xref:System.Windows.Threading.Dispatcher> propustnost udržováním malé pracovní položky. Tento způsob, jak položky nikdy získat zastaralé uložený ve <xref:System.Windows.Threading.Dispatcher> fronty čekání na zpracování. Jakékoli patrná zpoždění mezi vstup a odpovědí může frustrovat uživatele.  
  
 Jak pak jsou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace by měl pro zpracování velkých operací? Co když kódu zahrnuje velké výpočtu nebo potřebuje k dotazování databáze na některé vzdáleného serveru? Obvykle je pro zpracování velkých operace v samostatné vlákno, a odpověď [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno volné zpravidla položky v <xref:System.Windows.Threading.Dispatcher> fronty. Po dokončení operace big ho může hlásit svůj výsledek zpět [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno pro zobrazení.  
  
 V minulosti [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] umožňuje [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy, aby měly přístup jenom vlákno, které byly vytvořeny. To znamená, že vlákna na pozadí starosti některé dlouho běžící úlohy nelze aktualizovat v textovém poli Po dokončení. [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]k tomu k zajištění integrity [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] součásti. Pole se seznamem může vypadat neobvyklé, pokud jeho obsah aktualizoval vlákna na pozadí během vykreslování.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]má integrovanou vzájemné vyloučení mechanismus, který vynucuje tato spolupráce. Většina tříd v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odvozena od <xref:System.Windows.Threading.DispatcherObject>. Při vytváření <xref:System.Windows.Threading.DispatcherObject> ukládá odkaz na <xref:System.Windows.Threading.Dispatcher> propojené s aktuálně spuštěných vláken. V důsledku toho <xref:System.Windows.Threading.DispatcherObject> přidruží vlákno, které ji vytvoří. Při spuštění programu <xref:System.Windows.Threading.DispatcherObject> můžete volat jeho veřejné <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> metoda. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>prozkoumá <xref:System.Windows.Threading.Dispatcher> přidružené k aktuální vlákno a porovná ho do <xref:System.Windows.Threading.Dispatcher> odkazovat na uložené během vytváření. Pokud se neshodují, <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> vyvolá výjimku. <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>je určena k volání na začátku každé metody, které patří k <xref:System.Windows.Threading.DispatcherObject>.  
  
 Pokud pouze jedno vlákno můžete upravit [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], jak vlákna na pozadí komunikovat s uživatelem? Vlákna na pozadí můžete pokládat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno k provedení určité operace jeho jménem. Dělá to tak, že zaregistrujete pracovní položky pomocí <xref:System.Windows.Threading.Dispatcher> z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken. <xref:System.Windows.Threading.Dispatcher> Třída nabízí dvě metody pro registraci pracovní položky: <xref:System.Windows.Threading.Dispatcher.Invoke%2A> a <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>. Obě metody naplánovat delegáta pro provedení. <xref:System.Windows.Threading.Dispatcher.Invoke%2A>je synchronní volání – to znamená, nevrací až [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken ve skutečnosti dokončí provádění delegát. <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>je asynchronní a vrátí okamžitě.  
  
 <xref:System.Windows.Threading.Dispatcher> Řadí elementy v příslušné fronty podle priority. Existují deset úrovně, které může být určen při přidávání se element <xref:System.Windows.Threading.Dispatcher> fronty. Tyto priority jsou zachována ve <xref:System.Windows.Threading.DispatcherPriority> výčtu. Podrobné informace o <xref:System.Windows.Threading.DispatcherPriority> úrovně lze nalézt v [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)] dokumentaci.  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>Vlákna v akci: ukázky  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>Aplikace jednovláknové s dlouho běžící výpočtu  
 Většina [!INCLUDE[TLA#tla_gui#plural](../../../../includes/tlasharptla-guisharpplural-md.md)] tráví velkou část doba pro jejich nečinnosti při čekání na události, které jsou generovány v odpovědi na akce uživatelů. Pečlivě programování s dobu nečinnosti lze konstruktivně, aniž by to ovlivnilo schopnost reagovat [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Model vláken neumožňuje vstup pro přerušení děje v operace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken. To znamená, že je nutné zajistit se vrátíte do <xref:System.Windows.Threading.Dispatcher> pravidelně do procesu čekající na vyřízení vstupních událostech předtím, než získají zastaralé.  
  
 Podívejte se na následující příklad:  
  
 ![Snímek obrazovky prvočísel](../../../../docs/framework/wpf/advanced/media/threadingprimenumberscreenshot.PNG "ThreadingPrimeNumberScreenShot")  
  
 Tato jednoduchá aplikace počty směrem nahoru ze tří, hledání prvočísel. Když uživatel klikne **spustit** tlačítko hledání začne. Když program vyhledá prime, aktualizuje uživatelské rozhraní pomocí jeho zjišťování. V libovolném bodě uživatel vyhledávání ukončit.  
  
 I když je dostatečně jednoduchá, hledání prime číslo může přejít na navždy, který představuje některé problémy.  Pokud jsme zpracovat celý hledání uvnitř obslužné rutiny události klikněte na tlačítko, jsme by nikdy poskytnout [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vláken příležitosti pro zpracování další události. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] By být schopna odpovědět na vstupu nebo proces zprávy. By se nikdy překreslit a nikdy reakce na kliknutí na tlačítko.  
  
 Jsme mohli provádět vyhledávání prime číslo v samostatných podprocesu, ale pak je potřeba řešit problémy s synchronizací. S přístupem jednovláknový jsme můžete přímo aktualizovat štítek, který uvádí největší prime nalezen.  
  
 Pokud jsme rozdělit úlohu výpočtu do spravovatelných blocích, můžeme pravidelně se vrátit <xref:System.Windows.Threading.Dispatcher> a zpracování události. Bylo možné přidělit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] příležitost překreslit a zpracovat vstup.  
  
 Nejlepší způsob, jak rozdělit doba zpracování mezi výpočtu a zpracování událostí je Správa výpočtu z <xref:System.Windows.Threading.Dispatcher>. Pomocí <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> metoda, jsme naplánovat prime číslo kontroly v stejné fronty, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] události jsou vykreslovány z. V našem příkladu jsme naplánovat pouze jedno číslo prime kontrolu najednou. Po dokončení kontroly prime číslo další kontroly jsme naplánovat okamžitě. Tato kontrola pokračuje až poté, co čekající na vyřízení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] události byly zpracovány.  
  
 ![Obrázek fronty dispečera](../../../../docs/framework/wpf/advanced/media/threadingdispatcherqueue.PNG "ThreadingDispatcherQueue")  
  
 [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)]provede kontrolu pravopisu pomocí tento mechanismus. Kontrola pravopisu probíhá na pozadí pomocí čas nečinnosti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken. Podívejme se na kód.  
  
 Následující příklad ukazuje XAML, který vytváří uživatelské rozhraní.  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 Následující příklad ukazuje modelu code-behind.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 Následující příklad ukazuje obslužné rutiny události pro <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 Kromě aktualizace textu na <xref:System.Windows.Controls.Button>, tato obslužná rutina zodpovídá za plánování první kontrola prime číslo přidáním delegátovi, aby se <xref:System.Windows.Threading.Dispatcher> fronty. Přetrvával po dokončení této obslužné rutiny události svou práci <xref:System.Windows.Threading.Dispatcher> vybere tohoto delegáta pro provedení.  
  
 Jak jsme už zmínili dřív, <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> je <xref:System.Windows.Threading.Dispatcher> člen používají k plánování delegáta pro provedení. V takovém případě vybereme možnost <xref:System.Windows.Threading.DispatcherPriority.SystemIdle> s prioritou. <xref:System.Windows.Threading.Dispatcher> Spustí jenom v případě, že neexistují žádné důležité události. ke zpracování tohoto delegáta. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]rychlost reakce je důležitější než číslo kontrola. Také jsme předání nové delegáta představující rutiny kontrola číslo.  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 Tato metoda ověří, zda je číslo liché další prime. Pokud je primární, metodu přímo aktualizací `bigPrime` <xref:System.Windows.Controls.TextBlock> tak, aby odrážela jeho zjišťování. Jsme lze provést, protože výpočet dochází ve stejném vlákně, která byla použita k vytvoření komponentou. Měli jsme vybrali možnost použít samostatné vlákno pro výpočet, nám používat složitější synchronizační mechanismus a provést aktualizaci v [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken. Tuto situaci jsme budete ukazují další.  
  
 Úplný zdrojový kód pro tuto ukázku, najdete v článku [jedno vláknové objekty aplikace s ukázkou dlouho běžící výpočtu](http://go.microsoft.com/fwlink/?LinkID=160038)  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>Zpracování blokování operaci s vlákna na pozadí  
 Zpracování blokování operace v grafické aplikace může být obtížné. Neradi volat metody blokování z obslužné rutiny událostí, protože aplikace se zobrazí na zmrazení. Můžeme použít samostatné vlákna ke zpracování těchto operací, ale když máme Hotovo, musíme synchronizovat s [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vláken, protože jsme nelze upravit přímo [!INCLUDE[TLA2#tla_gui](../../../../includes/tla2sharptla-gui-md.md)] z našich pracovní vlákno. Můžeme použít <xref:System.Windows.Threading.Dispatcher.Invoke%2A> nebo <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> vložit delegáti do <xref:System.Windows.Threading.Dispatcher> z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken. Nakonec se provede tyto delegáti oprávnění k úpravě [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementy.  
  
 V tomto příkladu jsme napodobovat vzdálené volání procedury, načte předpověď počasí. Používáme samostatné pracovní vlákno provést toto volání a jsme naplánovat metodu aktualizace v <xref:System.Windows.Threading.Dispatcher> z [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vláken, když jsme bylo dokončeno.  
  
 ![Informace o počasí snímek obrazovky uživatelského rozhraní](../../../../docs/framework/wpf/advanced/media/threadingweatheruiscreenshot.PNG "ThreadingWeatherUIScreenShot")  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 Toto jsou některé podrobnosti vhodné poznamenat.  
  
-   Vytváření obslužná rutina tlačítko  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 Při kliknutí na tlačítko jsme zobrazit kreslení hodiny a spusťte ho animace. Zakážeme tlačítko. Jsme vyvolání `FetchWeatherFromServer` metoda nové vlákno, a potom jsme návratový, což <xref:System.Windows.Threading.Dispatcher> ke zpracování událostí, když jsme čekat na shromažďování předpovědi počasí.  
  
-   Načítání počasí  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 Pro zjednodušení nemáme ve skutečnosti sítě kód v tomto příkladu. Místo toho jsme simulovat zpoždění přístup k síti umístěním naší nové vlákno do režimu spánku čtyři sekund. V tuto chvíli původní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno je stále spuštěna a reagování na události. Ukážeme vám to, že jsme jste zbývajících animace spuštěna a minimalizovat a maximalizovat tlačítka také pokračovat v práci.  
  
 Po dokončení zpoždění, a rozhodli jsme se náhodně naše předpověď počasí, je čas zprávy zpět [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken. Provedeme to pomocí naplánovaného volání `UpdateUserInterface` v [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vláken pomocí daném vláknu <xref:System.Windows.Threading.Dispatcher>. Jsme předat řetězec popisující počasí pro toto volání metody naplánované.  
  
-   Aktualizace[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 Když <xref:System.Windows.Threading.Dispatcher> v [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno má čas, se provede plánované volání `UpdateUserInterface`. Tato metoda zastaví animace hodiny a zvolí obrázek, který se popisují počasí. Zobrazí tuto bitovou kopii a obnoví tlačítko "načítání forecast".  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>Více oken, více vláken  
 Některé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace vyžadují více oken nejvyšší úrovně. Je zcela přijatelné pro jedno vlákno /<xref:System.Windows.Threading.Dispatcher> kombinace ke správě více oken, ale někdy několik vláken pracovat lépe. To platí hlavně v že případě je pravděpodobné, že jedna z windows bude monopolizovat všechny vlákno.  
  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]Průzkumník funguje tímto způsobem. Každé nové okno Průzkumníka patří do procesu původní, ale se vytvoří pod kontrolou nezávislé vlákno.  
  
 Pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame> řízení, zobrazuje se webové stránky. Jsme můžete snadno vytvořit jednoduchou [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)] nahradit. Začneme s důležitou součást: možnost otevřete nové okno Průzkumníka. Když uživatel klikne na tlačítko "nové okno" tlačítko jsme spustit kopii naše okna v samostatných podprocesu. Tímto způsobem, dlouhodobé nebo blokování operací v jednom ze systému windows nebude uzamčení všechny ostatní systémy windows.  
  
 Ve skutečnosti webové prohlížeče model má vlastní složitý model vláken. Vzhledem k tomu, že by měla být pro většinu čtečky jsme jste vybrali ho.  
  
 Následující příklad ukazuje kód.  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 Jsou následující vláken segmenty tohoto kódu nejvíce zajímavé nám v tomto kontextu:  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 Tato metoda je volána, když "nové okno" po kliknutí na tlačítko. Vytvoří nové vlákno. proto ji spustí asynchronně.  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 Tato metoda je výchozím bodem pro nové vlákno. Vytvoříme nové okno pod kontrolou tohoto podprocesu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]automaticky vytvoří nový <xref:System.Windows.Threading.Dispatcher> ke správě nové vlákno. Všechny budeme muset udělat, aby byly funkční okna je spustit <xref:System.Windows.Threading.Dispatcher>.  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>Technické podrobnosti a Stumbling body  
  
### <a name="writing-components-using-threading"></a>Zápis součásti pomocí dělení na vlákna  
 [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] – Příručka vývojáře popisuje vzor jak součást můžou zpřístupnit asynchronní chování svým klientům (najdete v části [na základě událostí přehled asynchronních vzorů](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)). Předpokládejme například, jsme chtěli balíčku `FetchWeatherFromServer` metoda do komponenty opakovaně použitelný, které nepodporují grafiku. Následující standardní [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] vzor, to by vypadat podobně jako následující.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync`by použijte jeden z technik popsaných výše, jako je například vytváření vlákna na pozadí, které udělají tuto práci asynchronně, není blokování volající vlákno.  
  
 Jedna z vašich nejdůležitějších částí tohoto vzoru volá *MethodName* `Completed` metoda ve stejném vlákně, který volá *MethodName* `Async` metodu začínat. Můžete tak učinit pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poměrně snadno uložením <xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>– ale pak komponentu které nepodporují grafiku může lze použít pouze ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, není v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] programy.  
  
 <xref:System.Windows.Threading.DispatcherSynchronizationContext> Třída adresy tohoto požadavku – jako zjednodušenou verzi <xref:System.Windows.Threading.Dispatcher> to funguje s jinými [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] také architektury.  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>Vnořené čerpání  
 Někdy není možné úplně zamčení [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken. Pojďme se podívat <xref:System.Windows.MessageBox.Show%2A> metodu <xref:System.Windows.MessageBox> třídy. <xref:System.Windows.MessageBox.Show%2A>nevrací, dokud uživatel klikne na tlačítko OK. Vytváří však okno, které musí mít smyčku zpráva, aby byla interaktivní. Když jsme čekají na uživatel kliknutím na tlačítko OK, neodpovídá původní okna aplikace na vstup uživatele. Nicméně, pokračovat ke zpracování malovat zprávy. Okno původní překreslí samotná popsaná a zjištěny.  
  
 ![MessageBox tlačítko "OK"](../../../../docs/framework/wpf/advanced/media/threadingnestedpumping.png "ThreadingNestedPumping")  
  
 Některé vlákno musí být starosti okno zprávy. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vytvořit nové vlákno jenom pro okno zprávy, ale tohoto podprocesu by nemohl malovat zakázané elementy v okně původní (Nezapomeňte starší diskuzi o vzájemné vyloučení). Místo toho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá zprávu vnořené zpracování systému. <xref:System.Windows.Threading.Dispatcher> Třída obsahuje speciální metodu s názvem <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>, která ukládá aktuální bod spuštění aplikace pak začne smyčku nové zprávy. Po dokončení vnořené zpráva smyčky provádění obnoví po původní <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> volání.  
  
 V takovém případě <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> udržuje kontextu programu na volání <xref:System.Windows.MessageBox>.<xref:System.Windows.MessageBox.Show%2A>, a zahájí cyklus nové zprávy překreslit okno pozadí a zpracovat vstup okno zprávy. Když uživatel klikne na tlačítko OK a vymaže místním okně, ukončení vnořených smyčky a řízení obnoví po volání <xref:System.Windows.MessageBox.Show%2A>.  
  
### <a name="stale-routed-events"></a>Zastaralé směrované události  
 Systém směrované události v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] upozorní celý stromy, když jsou vyvolány události.  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 Při stisknutí levé tlačítko myši nad se třemi tečkami `handler2` se spustí. Po `handler2` skončí, události se předají <xref:System.Windows.Controls.Canvas> objekt, který používá `handler1` zpracovat. K tomu dojde pouze v případě `handler2` nemá explicitně označit objekt událostí jako zpracování.  
  
 Je možné, který `handler2` bude trvat značnou část doby zpracování této události. `handler2`může použít <xref:System.Windows.Threading.Dispatcher.PushFrame%2A> zahájíte smyčku vnořené zpráv, který nevrací hodin. Pokud `handler2` neobsahuje označit událost jako zpracování, pokud je tato zpráva smyčky dokončení, událost byla předána do stromu, i když je velmi staré.  
  
### <a name="reentrancy-and-locking"></a>Vícenásobný přístup a zamykání  
 Uzamčení mechanismus [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] není chovat přesně tak, jak může jeden Představte si; jeden můžou očekávat vlákna ke zcela zastaví operaci žádosti o zámek. Ve skutečnosti vlákno nadále přijímat a zpracovávat zprávy s vysokou prioritou. To pomáhá zabránit blokování a dosáhnete rozhraní minimálně reakce, ale přináší možnost pro jemně chyby.  Velká většina času nemusíte nic vědět o tom, ale za výjimečných podmínek (obvykle zahrnující [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno zprávy nebo komponenty COM STA) to může být vhodné s jistotou.  
  
 Většina rozhraní nejsou vytvořené s nástroji zabezpečení vlákna na paměti, protože vývojáři fungovat za předpokladu, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] nikdy přistupuje více než jedno vlákno. V tomto případě, že jedno vlákno může provést změny v prostředí v neočekávanou dobu, příčinou těchto nesprávně dopad, <xref:System.Windows.Threading.DispatcherObject> mechanismus vzájemné vyloučení by měla vyřešit. Vezměte v úvahu následující pseudokódu:  
  
 ![Dělení na vlákna vícenásobný přístup diagram](../../../../docs/framework/wpf/advanced/media/threadingreentrancy.png "ThreadingReentrancy")  
  
 Ve většině případů, je správné věci, ale v určitých časech v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kde takové neočekávané vícenásobný přístup skutečně způsobit problémy. Ano, v určitých časech klíče [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] volání <xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>, pokyn zámek pro daném vláknu použít změny, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] opětovné zadání bez uzamčení, namísto obvyklého [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zámku.  
  
 Ano důvod, proč se [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] team zvolte toto chování? Ho museli dělat s objekty COM STA a finalizace vlákno. Když je objekt uvolnění z paměti, jeho `Finalize` metoda běží na vyhrazené finalizační metodu vlákno, není [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken. A v něm je problém, protože COM STA objektu, který byl vytvořen na [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno může být uvolněn pouze ve [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] přístup z více vláken. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Nemá ekvivalent <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (v takovém případě používat na Win32 `SendMessage`). Avšak v tom případě [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlákno je zaneprázdněný, vlákno finalizační metodu je zastaven a proces a objekt COM STA nelze uvolnit, vytváří závažné paměť. Proto [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] team provedené robustním volání aby zámky pracovat způsobem dělají.  
  
 Úloha [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se vyhnete neočekávané opětovné zadání bez opětovného zavedení nevrácená paměť systému, proto jsme neblokovat everywhere vícenásobný přístup.  
  
## <a name="see-also"></a>Viz také  
 [Jednovláknové aplikace s ukázkou dlouho běžící výpočtu](http://go.microsoft.com/fwlink/?LinkID=160038)
