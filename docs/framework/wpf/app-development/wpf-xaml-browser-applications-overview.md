---
title: Přehled aplikací Prohlížeče WPF XAML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XBAP [WPF], XAML browser application
- WPF XAML browser applications (XBAP)
- XAML browser applications (XBAP)
- browser-hosted applications [WPF]
ms.assetid: 3a7a86a8-75d5-4898-96b9-73da151e5e16
ms.openlocfilehash: 81ae93871fa5e3fc46382ee9a1810808574fb043
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320129"
---
# <a name="wpf-xaml-browser-applications-overview"></a>Přehled aplikací Prohlížeče WPF XAML
<a name="introduction"></a>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] jsou k dispozici funkce webových aplikací a aplikací plně funkčním klientovi. Stejně jako webových aplikací je možné nasadit na webový server a spustit z aplikace Internet Explorer nebo Firefox XBAP. Jako plně funkčním klientovi aplikace XBAP můžete využít možnosti WPF. Vývoj aplikace XBAP je také podobné jako vývoj plně funkčním klientovi. Toto téma poskytuje jednoduchý, podrobný Úvod do vývoje XBAP, který a popisuje, kde vývoj XBAP, který se liší od vývoje ve standardu plně funkčním klientovi.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Vytvoření nové aplikace prohlížeče XAML (XBAP)](#creating_a_new_xaml_browser_application_xbap)  
  
-   [Nasazení XBAP](#deploying_a_xbap)  
  
-   [Komunikaci s webovou stránkou hostitele](#communicating_with_the_host_web_page)  
  
-   [Aspekty zabezpečení XBAP](#xbap_security_considerations)  
  
-   [Faktory ovlivňující výkon XBAP počáteční čas](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## <a name="creating-a-new-xaml-browser-application-xbap"></a>Vytvoření nové aplikace prohlížeče XAML (XBAP)  
 Nejjednodušší způsob, jak vytvořit nového projektu XBAP, který je sadou Microsoft Visual Studio. Při vytváření nového projektu, vyberte **aplikace WPF pro prohlížeč** ze seznamu šablon. Další informace najdete v tématu [jak: Vytvoření nového projektu aplikace prohlížeče WPF](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)).  
  
 Při spuštění projektu XBAP, který se otevře v okně prohlížeče místo samostatné okna. Když ladíte XBAP ze sady Visual Studio, aplikace se spustí s oprávněním zóny Internet a vyvolá proto bezpečnostním výjimkám překročení těchto oprávnění. Další informace najdete v tématu [zabezpečení](../security-wpf.md) a [částečné zabezpečení důvěryhodnosti WPF](../wpf-partial-trust-security.md).  
  
> [!NOTE]
>  Pokud nevyvíjíte se sadou Visual Studio nebo chcete další informace o souborech projektu, přečtěte si téma [sestavení aplikace WPF](building-a-wpf-application-wpf.md).  
  
<a name="deploying_a_xbap"></a>   
## <a name="deploying-an-xbap"></a>Nasazení XBAP  
 Při sestavování XBAP výstup zahrnuje následující tři soubory:  
  
|Soubor|Popis|  
|----------|-----------------|  
|Spustitelný soubor (.exe)|To obsahuje zkompilovaný kód a má příponu .exe.|  
|Manifest aplikace (.manifest)|Toto obsahuje metadata spojená s aplikací a má příponu .manifest.|  
|Manifest nasazení (.xbap)|Tento soubor obsahuje informace, že používá k nasazení aplikace ClickOnce a příponou .xbap.|  
  
 Například nasazení aplikace XBAP na webový server, [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo novější verze. Není nutné instalovat rozhraní .NET Framework na webovém serveru, ale je nutné provést registraci [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] přípon názvů typů a souborů. Další informace najdete v tématu [konfigurace služby IIS 5.0 a IIS 6.0 pro nasazení aplikací WPF](how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).  
  
 Příprava nasazení vaše XBAP, zkopírujte .exe a přidružené manifestů na webový server. Vytvořte stránku HTML, který obsahuje hypertextový odkaz na otevření manifestu nasazení, což je soubor s příponou .xbap. Když uživatel klikne odkaz na soubor .xbap, ClickOnce automaticky zpracovává mechanismy stažení a spuštění aplikace. Následující příklad kódu ukazuje stránku HTML, který obsahuje hypertextový odkaz, který odkazuje na XBAP.  
  
```html
<html>   
    <head></head>  
    <body>   
        <a href="XbapEx.xbap">Click this link to launch the application</a>  
    </body>   
</html>  
```  
  
 Může taky hostovat XBAP, který v rámci webové stránky. Vytvořte webovou stránku s jeden nebo více snímků. Nastavte vlastnost Zdroj rámce do souboru manifestu nasazení. Pokud chcete používat předdefinovaný mechanismus pro komunikaci mezi hostování webové stránky a XBAP, třeba hostování aplikace v rámci. Následující příklad kódu ukazuje stránku HTML s dvěma snímky, že zdroje pro druhý snímek je nastavena na XBAP.  
  
```html
<html>   
    <head>
        <title>A page with frames</title>
    </head>  
    <frameset cols="50%,50%">   
        <frame src="introduction.htm">   
        <frame src="XbapEx.xbap">   
    </frameset>   
</html>  
```  
  
### <a name="clearing-cached-xbaps"></a>Vymazání mezipaměti aplikace XBAP  
 V některých situacích po znovu sestavit a spustit vaše XBAP může se stát, že starší verze XBAP, který je otevřen. Toto chování může dojít například, když vaše číslo verze sestavení XBAP, který je statická a spustit XBAP z příkazového řádku. V takovém případě protože číslo verze mezi jeho verzi v mezipaměti (verze, která byla dříve spuštěna) a nové verze se nezmění, novou verzi XBAP, který se nestáhne. Místo toho se načte verze uložené v mezipaměti.  
  
 V takových případech můžete odebrat pomocí verze uložené v mezipaměti **Mage** příkazu (instalovanou se Visual Studio nebo pomocí sady Windows SDK) na příkazovém řádku. Následující příkaz odstraní mezipaměti aplikace.  
  
 ```console
 Mage.exe -cc
 ```
  
 Tento příkaz zaručuje, že je spuštěna na nejnovější verzi vaší XBAP. Při ladění aplikace v sadě Visual Studio měly být spuštěny na nejnovější verzi vaší XBAP. Obecně platí měli byste aktualizovat číslo verze vašeho nasazení s každým sestavením. Další informace o bitové kopii, naleznete v tématu [Mage.exe (Manifest Generation and Editing Tool)](../../tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
<a name="communicating_with_the_host_web_page"></a>   
## <a name="communicating-with-the-host-web-page"></a>Komunikaci s webovou stránkou hostitele  
 Když je aplikace hostovaná v rámci HTML, může komunikovat s webovou stránku, která obsahuje XBAP. Můžete to provést pomocí načítání <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> vlastnost <xref:System.Windows.Interop.BrowserInteropHelper>. Tato vlastnost vrátí objekt skript, který představuje okno HTML. Můžete pak přístup k vlastnosti, metody a události v [objekt okna](https://go.microsoft.com/fwlink/?LinkId=160274) pomocí syntaxe regulárních tečkou. Můžete také přistupovat metody skriptů a globální proměnné. Následující příklad ukazuje, jak získat objekt skriptu a ukončete prohlížeč.  
  
 [!code-csharp[XbapBrowserInterop#10](~/samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### <a name="debugging-xbaps-that-use-hostscript"></a>Ladění aplikací XBAP, které používají HostScript  
 Pokud vaše XBAP, který používá <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> objekt ke komunikaci s oknem HTML existují dvě nastavení, které je nutné zadat ke spuštění a ladění aplikace v sadě Visual Studio. Aplikace musí mít přístup ke stránce jejího původu a aplikace musí začínat stránky HTML, který obsahuje XBAP. Následující kroky popisují, jak zkontrolovat tato dvě nastavení:  
  
1. V sadě Visual Studio otevřete vlastnosti projektu.  
  
2. Na **zabezpečení** klikněte na tlačítko **Upřesnit**.  
  
     Zobrazí se dialogové okno Upřesnit nastavení zabezpečení.  
  
3. Ujistěte se, že **udělit aplikaci přístup ke stránce jejího původu** zaškrtněte políčko a klikněte na **OK**.  
  
4. Na **ladění** kartu, vyberte **Start prohlížeč s adresou URL** možnost a zadejte adresu URL pro stránku HTML, který obsahuje XBAP.  
  
5. V aplikaci Internet Explorer, klikněte na tlačítko **nástroje** tlačítko a pak vyberte **Možnosti Internetu**.  
  
     Zobrazí se dialogové okno Možnosti Internetu.  
  
6. Klikněte na tlačítko **Upřesnit** kartu.  
  
7. V **nastavení** seznamu v části **zabezpečení**, zkontrolujte **aktivní obsah ke spuštění v souborech na tomto počítači povolit** zaškrtávací políčko.  
  
8. Klikněte na **OK**.  
  
     Změny se projeví po restartování aplikace Internet Explorer.  
  
> [!CAUTION]
>  Povolení aktivní obsah v aplikaci Internet Explorer může ohrozit váš počítač. Pokud nechcete změnit nastavení zabezpečení aplikace Internet Explorer, můžete spustit na stránce HTML ze serveru a připojit k procesu ladicího programu sady Visual Studio.  
  
<a name="xbap_security_considerations"></a>   
## <a name="xbap-security-considerations"></a>Aspekty zabezpečení XBAP  
 XBAP obvykle spustit v sandboxu částečným vztahem důvěryhodnosti zabezpečení, který je omezena na sadu oprávnění zóny Internet. V důsledku toho vaši implementaci musí podporovat na podmnožinu WPF prvky, které jsou podporovány v zóně Internet nebo musí zvýšení oprávnění aplikace. Další informace najdete v tématu [zabezpečení](../security-wpf.md).  
  
 Při použití <xref:System.Windows.Controls.WebBrowser> ovládacího prvku v aplikaci WPF interně vytvoří instanci nativní ovládací prvek WebBrowser ActiveX. Když je vaše aplikace částečným vztahem důvěryhodnosti XBAP, který v aplikaci Internet Explorer, ovládací prvek ActiveX spouští ve vyhrazeném vlákně procesu aplikace Internet Explorer. Proto platí následující omezení:  
  
-   <xref:System.Windows.Controls.WebBrowser> Ovládací prvek by měl poskytovat chování podobný hostitele prohlížeče, včetně omezení zabezpečení. Některé z těchto omezení zabezpečení se dá řídit přes nastavení zabezpečení aplikace Internet Explorer. Další informace najdete v tématu [zabezpečení](../security-wpf.md).  
  
-   Když XBAP, který je načten mezi doménami v stránku HTML, je vyvolána výjimka.  
  
-   Vstup je na samostatném vlákně z WPF <xref:System.Windows.Controls.WebBrowser>, takže nemůže dojít k jejich zachycení vstup z klávesnice a není sdílený stav editoru IME.  
  
-   Časování nebo pořadí navigace se může lišit kvůli ovládací prvek ActiveX, který běží na jiném vlákně. Například přejdete na stránku není vždy zrušil spuštění další požadavek pro navigaci.  
  
-   Vlastní ovládací prvek ActiveX mohou mít problémy s komunikací, protože aplikace WPF běží v samostatném vlákně.  
  
-   <xref:System.Windows.Interop.HwndHost.MessageHook> získat zvýšit není, protože <xref:System.Windows.Interop.HwndHost> nelze vytvořit podtřídu okno systémem v jiném procesu nebo vlákna.  
  
### <a name="creating-a-full-trust-xbap"></a>Vytváření XBAP plné důvěryhodnosti  
 Pokud vaše XBAP, který vyžaduje úplný vztah důvěryhodnosti, můžete změnit projekt tak, aby toto oprávnění zapnout. Následující kroky popisují, jak povolit úplný vztah důvěryhodnosti:  
  
1. V sadě Visual Studio otevřete vlastnosti projektu.  
  
2. Na **zabezpečení** kartu, vyberte **Toto je aplikace s úplným vztahem důvěryhodnosti** možnost.  
  
 Toto nastavení provede následující změny:  
  
-   V souboru projektu `<TargetZone>` hodnota elementu se změní na `Custom`.  
  
-   V manifestu aplikace (app.manifest) `Unrestricted="true"` přidání atributu do "<xref:System.Security.PermissionSet> elementu.  
  
    ```xml
    <PermissionSet class="System.Security.PermissionSet"   
                   version="1"   
                   ID="Custom"   
                   SameSite="site"   
                   Unrestricted="true" />  
    ```  
  
### <a name="deploying-a-full-trust-xbap"></a>Nasazení XBAP plné důvěryhodnosti  
 Když nasadíte XBAP úplného vztahu důvěryhodnosti, který nedodržuje modelu důvěryhodných nasazení ClickOnce, chování, když uživatel spustí aplikaci bude záviset na zóně zabezpečení. V některých případech se uživateli zobrazí upozornění při pokusu o jeho instalaci. Uživatel můžete rozhodnout pokračovat nebo zrušit instalaci. Následující tabulka popisuje chování aplikací pro každou zónu zabezpečení a co musíte udělat pro aplikaci pro příjem úplný vztah důvěryhodnosti.  
  
|Zóna zabezpečení|Chování|Získávání úplný vztah důvěryhodnosti|  
|-------------------|--------------|------------------------|  
|Místní počítač|Automatické úplný vztah důvěryhodnosti|Není vyžadována žádná akce.|  
|Intranet a důvěryhodných serverů|Výzva k zadání úplný vztah důvěryhodnosti|Podepište XBAP pomocí certifikátu tak, aby se uživateli zobrazí zdroj v příkazovém řádku.|  
|Internet|Selže a zobrazí se "Důvěryhodnost nebyla udělena"|Podepište XBAP s certifikátem.|  
  
> [!NOTE]
>  Chování popsané v předchozí tabulce je pro aplikace XBAP úplného vztahu důvěryhodnosti, které nepostupujte podle modelu důvěryhodných nasazení ClickOnce.  
  
 Doporučujeme vám použít model nasazení důvěryhodných ClickOnce pro nasazení XBAP úplného vztahu důvěryhodnosti. Tento model umožňuje vaší XBAP, který chcete být udělena úplná důvěryhodnost automaticky, bez ohledu na zóně zabezpečení tak, aby se uživateli nezobrazí výzva. V rámci tohoto modelu musíte podepsat aplikaci pomocí certifikátu od důvěryhodného vydavatele. Další informace najdete v tématu [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview) a [Úvod k podepisování kódu](https://go.microsoft.com/fwlink/?LinkId=166327).  
  
<a name="xbap_start_time_performance_considerations"></a>   
## <a name="xbap-start-time-performance-considerations"></a>Faktory ovlivňující výkon XBAP počáteční čas  
 Důležitou součástí výkonu XBAP, který je jeho spuštění. Pokud XBAP, který je první aplikaci WPF se načíst, *studený start* čas může být deset sekund nebo více. Je to proto, že na stránce Průběh vykreslením ve WPF, a CLR a WPF musí být studeného spouštěná a zobrazte aplikaci.  
  
 Počínaje [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], počáteční čas XBAP, který je zmírněna tím, že zobrazuje stránku nespravované průběh v rané fázi cyklus nasazení. Na stránce Průběh téměř okamžitě se zobrazí po spuštění aplikace, protože je zobrazený nativní kód hostování a zobrazena ve formátu HTML.  
  
 Kromě toho lepší souběžnosti pořadí stahování ClickOnce zlepšuje čas zahájení až deset procent. Po ClickOnce soubory ke stažení a ověří spustí aktualizovat manifesty spustí stahování aplikací a indikátor průběhu.  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace sady Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby](configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)
- [Nasazení aplikace WPF](deploying-a-wpf-application-wpf.md)
