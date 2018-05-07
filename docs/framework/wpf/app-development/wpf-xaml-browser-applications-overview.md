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
ms.openlocfilehash: a4ffe9a278aa8c73909b7f6a78cc80e78009aeba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="wpf-xaml-browser-applications-overview"></a>Přehled aplikací Prohlížeče WPF XAML
<a name="introduction"></a>
[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] kombinuje funkce webových aplikací a bohaté klientské aplikace. Aplikace XBAP můžete jako webové aplikace nasazené na webový server a spuštěné z aplikace Internet Explorer nebo Firefox. Jako plně funkčního klienta aplikace XBAP můžete využít výhod funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Vývoj aplikace XBAP je také podobná vývoj plně funkčního klienta. Toto téma poskytuje jednoduché, vysoké úrovně Úvod k XBAP vývoj a popisuje, kde XBAP vývoj se liší od standardní vývoj plně funkčního klienta.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Vytvoření nové aplikace prohlížeče XAML (XBAP)](#creating_a_new_xaml_browser_application_xbap)  
  
-   [Nasazení XBAP](#deploying_a_xbap)  
  
-   [Komunikaci s webovou stránkou hostitele](#communicating_with_the_host_web_page)  
  
-   [Aspekty zabezpečení XBAP](#xbap_security_considerations)  
  
-   [Faktory ovlivňující výkon XBAP počáteční čas](#xbap_start_time_performance_considerations)  
  
<a name="creating_a_new_xaml_browser_application_xbap"></a>   
## <a name="creating-a-new-xaml-browser-application-xbap"></a>Vytvoření nové aplikace prohlížeče XAML (XBAP)  
 Nejjednodušší způsob, jak vytvořit nový projekt XBAP je s [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]. Při vytváření nového projektu, vyberte **aplikace prohlížeče WPF** ze seznamu šablon. Další informace najdete v tématu [postupy: vytvoření nového projektu aplikace prohlížeče WPF](http://msdn.microsoft.com/library/72ef4d90-e163-42a1-8df0-ea7ccfd1901f).  
  
 Když spouštíte projekt XBAP, otevře se v okně prohlížeče namísto samostatného okna. Když ladíte XBAP z [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], aplikace spustí s oprávněním pro zónu Internetu a proto throw výjimky zabezpečení, pokud se překročí tato oprávnění. Další informace najdete v tématu [zabezpečení](../../../../docs/framework/wpf/security-wpf.md) a [WPF částečné důvěryhodnosti zabezpečení](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
> [!NOTE]
>  Pokud nevyvíjíte s [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] nebo o další informace o souborech projektu naleznete v části [vytváření aplikace WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md).  
  
<a name="deploying_a_xbap"></a>   
## <a name="deploying-an-xbap"></a>Nasazení XBAP  
 Při sestavování XBAP výstup zahrnuje následující tři soubory:  
  
|Soubor|Popis|  
|----------|-----------------|  
|Spustitelný soubor (.exe)|To obsahuje zkompilovaný kód a má příponu .exe.|  
|Manifest aplikace (manifest)|To obsahuje metadata spojená s aplikací a má příponu manifest.|  
|Manifest nasazení (.xbap)|Tento soubor obsahuje informace, [!INCLUDE[TLA#tla_clickonce](../../../../includes/tlasharptla-clickonce-md.md)] používá k nasazení aplikace a má příponu .xbap.|  
  
 Například nasadit aplikace XBAP na webový server, [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] nebo novější verze. Chcete-li nainstalovat rozhraní .NET Framework na webovém serveru nemáte, ale je nutné provést registraci [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] typy a název souboru rozšíření. Další informace najdete v tématu [konfigurace služby IIS 5.0 a IIS 6.0 do nasazení aplikace WPF](../../../../docs/framework/wpf/app-development/how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).  
  
 Při přípravě nasazení vaší XBAP, zkopírujte .exe a přidružené manifesty na webový server. Vytvořte stránku HTML, který obsahuje hypertextový odkaz otevřete manifest nasazení, který je soubor, který má příponu .xbap. Když uživatel klikne na odkaz k souboru .xbap [!INCLUDE[TLA2#tla_clickonce](../../../../includes/tla2sharptla-clickonce-md.md)] automaticky zpracovává mechanismů stažení a spuštění aplikace. Následující příklad kódu ukazuje stránku HTML, který obsahuje hypertextový odkaz, který odkazuje na XBAP.  
  
```html
<html>   
    <head></head>  
    <body>   
        <a href="XbapEx.xbap">Click this link to launch the application</a>  
    </body>   
</html>  
```  
  
 Také můžete hostovat XBAP v rámci webové stránky. Vytvořte webovou stránku s jeden nebo více snímků. Nastavte vlastnost Zdroj rámce k souboru manifestu nasazení. Pokud chcete používat pro komunikaci mezi hostování webové stránky a XBAP předdefinované mechanismus, musíte hostovat aplikaci v rámečku. Následující příklad kódu ukazuje stránku HTML se dvěma rámečky že zdroj pro druhý rámečku je nastavena na XBAP.  
  
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
  
### <a name="clearing-cached-xbaps"></a>Probíhá vymazání mezipaměti XBAP  
 V některých situacích po znovu sestavit a spustit vaší XBAP můžete zjistit, že dřívější verzi XBAP je otevřené. Toto chování může například dojít, když je vaše číslo verze sestavení XBAP statické a XBAP spustíte z příkazového řádku. V takovém případě protože číslo verze mezi verze v mezipaměti (verze, která byla dříve spuštěna) a nové verze se nezmění, není stáhnout nové verze XBAP. Místo toho je načtena v mezipaměti.  
  
 V těchto situacích můžete odebrat verze v mezipaměti pomocí **Mage** příkazu (nainstalované s Visual Studio nebo [!INCLUDE[TLA2#tla_lhsdk](../../../../includes/tla2sharptla-lhsdk-md.md)]) na příkazovém řádku. Tento příkaz vymaže mezipaměť aplikací.  
  
 ```console
 Mage.exe -cc
 ```
  
 Tento příkaz zaručuje, že nejnovější verzi vaší XBAP spuštěné. Při ladění aplikace v [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], nejnovější verzi vaší XBAP by měl být spuštěn. Obecně platí by měl aktualizovat číslo verze vašeho nasazení s každé sestavení. Další informace o Mage najdete v tématu [Mage.exe (generování manifestu a nástroj pro úpravy)](../../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
<a name="communicating_with_the_host_web_page"></a>   
## <a name="communicating-with-the-host-web-page"></a>Komunikaci s webovou stránkou hostitele  
 Pokud aplikace hostovaný v rámci HTML, může komunikovat s webovou stránku, který obsahuje XBAP. To se provádí načítání <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> vlastnost <xref:System.Windows.Interop.BrowserInteropHelper>. Tato vlastnost vrátí objekt skript, který představuje okně HTML. Potom můžete přístup k vlastnosti, metod a události na [objektu okna](http://go.microsoft.com/fwlink/?LinkId=160274) pomocí regulárních tečkové syntaxe. Můžete taky přejít metody skriptu a globální proměnné. Následující příklad ukazuje, jak získat objekt skriptu a zavřete prohlížeč.  
  
 [!code-csharp[XbapBrowserInterop#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]  
  
### <a name="debugging-xbaps-that-use-hostscript"></a>Ladění aplikace XBAP, které používají HostScript  
 Pokud vaše XBAP používá <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> objekt ke komunikaci s okně HTML existují dvě nastavení, které je nutné zadat ke spuštění a ladění aplikace v [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]. Aplikace musí mít přístup k jeho lokality původu a aplikace musí začínat stránky HTML, který obsahuje XBAP. Následující kroky popisují, jak zkontrolovat tato dvě nastavení:  
  
1.  V sadě Visual Studio otevřete vlastnosti projektu.  
  
2.  Na **zabezpečení** , klikněte na **Upřesnit**.  
  
     Zobrazí se dialogové okno Upřesnit nastavení zabezpečení.  
  
3.  Ujistěte se, že **udělit přístup k aplikaci do jeho lokality původu** je zaškrtnuté políčko a potom klikněte na **OK**.  
  
4.  Na **ladění** vyberte **spuštění prohlížeče s adresou URL** možnost a zadejte adresu URL pro stránku HTML, který obsahuje XBAP.  
  
5.  V aplikaci Internet Explorer, klikněte **nástroje** tlačítko a potom vyberte **Možnosti Internetu**.  
  
     Zobrazí se dialogové okno Možnosti Internetu.  
  
6.  Klikněte **Upřesnit** kartě.  
  
7.  V **nastavení** v rámci **zabezpečení**, zkontrolujte **povolit spuštění v souborů v tomto počítači aktivního obsahu** zaškrtávací políčko.  
  
8.  Click **OK**.  
  
     Změny se projeví po restartování aplikace Internet Explorer.  
  
> [!CAUTION]
>  Povolení aktivní obsah v aplikaci Internet Explorer může ohrozit váš počítač. Další informace najdete v tématu [funkce zabezpečení a ochrany osobních údajů v Internet Exploreru](http://go.microsoft.com/fwlink/?LinkId=179286). Pokud nechcete, chcete-li změnit nastavení zabezpečení aplikace Internet Explorer, můžete spustit stránky HTML ze serveru a připojte [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] ladicí program k procesu.  
  
<a name="xbap_security_considerations"></a>   
## <a name="xbap-security-considerations"></a>Aspekty zabezpečení XBAP  
 Aplikace XBAP obvykle v karanténě částečným vztahem důvěryhodnosti zabezpečení, který je omezen na sadě Internet zóny oprávnění spustit. V důsledku toho implementaci musí podporovat podmnožinu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky, které jsou podporovány v zóně Internet nebo vám musí zvýšení oprávnění vaší aplikace. Další informace najdete v tématu [zabezpečení](../../../../docs/framework/wpf/security-wpf.md).  
  
 Při použití <xref:System.Windows.Controls.WebBrowser> ovládací prvek v aplikaci WPF interně vytvoří nativní ovládacího prvku WebBrowser ActiveX. Pokud je aplikace částečným vztahem důvěryhodnosti XBAP v aplikaci Internet Explorer, ovládacího prvku ActiveX běží v vyhrazené vlákna procesu aplikace Internet Explorer. Proto platí následující omezení:  
  
-   <xref:System.Windows.Controls.WebBrowser> Ovládacího prvku by měl poskytovat chování podobná webový prohlížeč hostitele, včetně omezení zabezpečení. Některé z těchto omezení zabezpečení můžete řídit pomocí nastavení zabezpečení aplikace Internet Explorer. Další informace najdete v tématu [zabezpečení](../../../../docs/framework/wpf/security-wpf.md).  
  
-   Když XBAP načíst napříč doménami v stránku HTML, je vyvolána výjimka.  
  
-   Vstup je v samostatné podprocesu z WPF <xref:System.Windows.Controls.WebBrowser>, takže nemůže být zachyceny vstup z klávesnice a není sdílený stav editoru IME.  
  
-   Načasování nebo pořadí navigace se může lišit kvůli ovládací prvek ActiveX, který je spuštěn na jiné vlákno. Například přejdete na stránku není vždy zrušena spuštěním jinou žádost o navigaci.  
  
-   Vlastní ovládací prvek ActiveX může mít problémy s komunikací, protože WPF aplikace běží v samostatné vlákno.  
  
-   <xref:System.Windows.Interop.HwndHost.MessageHook> získat vyvolá není, protože <xref:System.Windows.Interop.HwndHost> nelze podtřídami okno spuštěné v jiné vlákno nebo proces.  
  
### <a name="creating-a-full-trust-xbap"></a>Vytváření XBAP plné důvěryhodnosti  
 Pokud vaše XBAP vyžaduje úplný vztah důvěryhodnosti, můžete změnit projektu pro toto oprávnění povolit. Následující kroky popisují, jak povolit úplný vztah důvěryhodnosti:  
  
1.  V sadě Visual Studio otevřete vlastnosti projektu.  
  
2.  Na **zabezpečení** vyberte **Toto je aplikace s úplným vztahem důvěryhodnosti** možnost.  
  
 Toto nastavení provede tyto změny:  
  
-   V souboru projektu `<TargetZone>` hodnota elementu se změní na `Custom`.  
  
-   V manifestu aplikace (app.manifest) `Unrestricted="true"` je do atribut `PermissionSet` elementu.  
  
    ```xml
    <PermissionSet class="System.Security.PermissionSet"   
                   version="1"   
                   ID="Custom"   
                   SameSite="site"   
                   Unrestricted="true" />  
    ```  
  
### <a name="deploying-a-full-trust-xbap"></a>Nasazení XBAP plné důvěryhodnosti  
 Když nasadíte XBAP plné důvěryhodnosti, který neodpovídá pravidlům pro model nasazení ClickOnce důvěryhodné, chování, když uživatel spustí aplikaci, bude záviset na zóny zabezpečení. V některých případech uživatel dostane upozornění při pokusu o jeho instalaci. Uživatele můžete rozhodnout pokračovat nebo zrušit instalaci. Následující tabulka popisuje chování aplikace pro každou zónu zabezpečení a co musíte udělat pro aplikace na příjem úplný vztah důvěryhodnosti.  
  
|Zóna zabezpečení|Chování|Získávání úplný vztah důvěryhodnosti|  
|-------------------|--------------|------------------------|  
|Místní počítač|Automatické úplný vztah důvěryhodnosti|Není vyžadována žádná akce.|  
|Intranetu a důvěryhodných serverů|Výzva k zadání úplný vztah důvěryhodnosti|Podpis XBAP s certifikátem uživateli se zobrazí zdroj v řádku.|  
|Internet|Nepodaří a dojde k "Vztah důvěryhodnosti není autoritou"|Zaregistrujte XBAP s certifikátem.|  
  
> [!NOTE]
>  Chování popsané v předchozí tabulce je pro aplikace XBAP plné důvěryhodnosti, které neodpovídají modelu nasazení pomocí technologie ClickOnce důvěryhodné.  
  
 Doporučuje se používat model nasazení důvěryhodných ClickOnce pro nasazení XBAP plné důvěryhodnosti. Tento model umožňuje vaší XBAP udělit oprávnění úplný vztah důvěryhodnosti automaticky, bez ohledu na to zóny zabezpečení, takže uživatel nebude vyzván k. Jako součást tohoto modelu musíte se odhlásit od důvěryhodného vydavatele aplikace s certifikátem. Další informace najdete v tématu [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview) a [Úvod k podepisování kódu](http://go.microsoft.com/fwlink/?LinkId=166327).  
  
<a name="xbap_start_time_performance_considerations"></a>   
## <a name="xbap-start-time-performance-considerations"></a>Faktory ovlivňující výkon XBAP počáteční čas  
 Důležitým aspektem XBAP výkonu je její počáteční čas. Pokud XBAP je první aplikaci WPF načíst, *studený start* čas může být deseti sekund nebo více. Je to proto, že na stránce Průběh je vykreslen metodou WPF a CLR i WPF musí být studené spuštěna zobrazení aplikace.  
  
 Počínaje [!INCLUDE[net_v35SP1_short](../../../../includes/net-v35sp1-short-md.md)], čas studený start XBAP zmírnit tím, že zobrazuje stránku nespravované průběh brzy v cyklu nasazení. Na stránce průběh, zobrazí se téměř okamžitě po spuštění aplikace, protože se zobrazí nativní kód pro hostování a vykreslena ve formátu HTML.  
  
 Kromě toho vylepšené souběžnosti z [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] stažení pořadí zlepšuje čas spuštění až deset procent. Po [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] stáhne a ověří manifesty, se aplikace spustí stažení a spuštění panelu průběhu aktualizace.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace sady Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby](../../../../docs/framework/wpf/app-development/configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)  
 [Nasazení aplikace WPF](../../../../docs/framework/wpf/app-development/deploying-a-wpf-application-wpf.md)
