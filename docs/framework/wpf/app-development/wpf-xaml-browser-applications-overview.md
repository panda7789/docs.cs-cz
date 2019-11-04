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
ms.openlocfilehash: fb7ad54f61d9dcfe94379aef14930a0395da5291
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424593"
---
# <a name="wpf-xaml-browser-applications-overview"></a>Přehled aplikací Prohlížeče WPF XAML
<a name="introduction"></a>Aplikace prohlížeče XAML (XBAP) spojují funkce webových aplikací a aplikací s bohatou funkční verzí. Podobně jako webové aplikace mohou být aplikace XBAP nasazeny na webový server a spouštěny z aplikace Internet Explorer nebo Firefox. Podobně jako aplikace s bohatou platností můžou aplikace XBAP využívat možnosti WPF. Vývoj aplikací XBAP je také podobný vývoji s bohatou podporou klientů. Toto téma poskytuje jednoduchý, vysoce základní Úvod k vývoji XBAP a popisuje, kde se vývoj v XBAP liší od standardního vysoce výkonného vývoje klienta.

 Toto téma obsahuje následující oddíly:

- [Vytvoření nové aplikace prohlížeče XAML (XBAP)](#creating_a_new_xaml_browser_application_xbap)

- [Nasazení aplikace XBAP](#deploying_a_xbap)

- [Komunikace s hostitelskou webovou stránkou](#communicating_with_the_host_web_page)

- [Problematika zabezpečení XBAP](#xbap_security_considerations)

- [Požadavky na výkon při zahájení XBAP](#xbap_start_time_performance_considerations)

<a name="creating_a_new_xaml_browser_application_xbap"></a>
## <a name="creating-a-new-xaml-browser-application-xbap"></a>Vytvoření nové aplikace prohlížeče XAML (XBAP)
 Nejjednodušší způsob, jak vytvořit nový projekt XBAP, je Visual Studio. Při vytváření nového projektu vyberte v seznamu šablon položku **aplikace z prohlížeče WPF** . Další informace najdete v tématu [Postup: vytvoření nového projektu aplikace WPF Browser](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb628663(v=vs.100)).

 Když spustíte projekt XBAP, otevře se v okně prohlížeče namísto samostatného okna. Když ladíte aplikaci XBAP ze sady Visual Studio, aplikace se spustí s oprávněním pro internetovou zónu a bude proto generovat výjimky zabezpečení, pokud jsou tato oprávnění překročena. Další informace najdete v tématu zabezpečení s [částečnou důvěryhodností](../wpf-partial-trust-security.md) [zabezpečení](../security-wpf.md) a WPF.

> [!NOTE]
> Pokud nevyvíjíte pomocí sady Visual Studio nebo chcete získat další informace o souborech projektu, přečtěte si téma [Vytvoření aplikace WPF](building-a-wpf-application-wpf.md).

<a name="deploying_a_xbap"></a>
## <a name="deploying-an-xbap"></a>Nasazení aplikace XBAP
 Při sestavování aplikace XBAP obsahuje výstup následující tři soubory:

|Soubor|Popis|
|----------|-----------------|
|Spustitelný soubor (. exe)|Obsahuje zkompilovaný kód a má příponu. exe.|
|Manifest aplikace (. manifest)|Obsahuje metadata přidružená k aplikaci a má příponu. manifest.|
|Manifest nasazení (. XBAP)|Tento soubor obsahuje informace, které ClickOnce používá k nasazení aplikace a má příponu. XBAP.|

 Nasadíte aplikace XBAP na webový server, například Microsoft Internetová informační služba (IIS) 5,0 nebo novější verze. Nemusíte instalovat .NET Framework na webový server, ale musíte registrovat [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] typy MIME (Multipurpose Internet Mail Extensions) a přípony názvů souborů. Další informace najdete v tématu [Konfigurace iis 5,0 a iis 6,0 pro nasazení aplikací WPF](how-to-configure-iis-5-0-and-iis-6-0-to-deploy-wpf-applications.md).

 Pro přípravu XBAP pro nasazení zkopírujte do webového serveru soubor. exe a přidružené manifesty. Vytvořte stránku HTML obsahující hypertextový odkaz pro otevření manifestu nasazení, což je soubor s příponou. XBAP. Když uživatel klikne na odkaz na soubor. XBAP, ClickOnce automaticky zpracuje mechanismus stažení a spuštění aplikace. Následující příklad kódu ukazuje stránku HTML obsahující hypertextový odkaz, který odkazuje na XBAP.

```html
<html>
    <head></head>
    <body>
        <a href="XbapEx.xbap">Click this link to launch the application</a>
    </body>
</html>
```

 Můžete také hostovat XBAP v rámci webové stránky. Vytvořte webovou stránku s jedním nebo více snímky. Nastavte vlastnost source rámce na soubor manifestu nasazení. Pokud chcete použít vestavěný mechanizmus ke komunikaci mezi hostující webovou stránkou a XBAP, musíte aplikaci hostovat v rámci. Následující příklad kódu ukazuje stránku HTML se dvěma snímky, zdroj pro druhý rámec je nastaven na XBAP.

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

### <a name="clearing-cached-xbaps"></a>Mazání v mezipaměti – XBAP
 V některých situacích po nové sestavování a spouštění aplikace XBAP můžete zjistit, že je otevřená starší verze aplikace XBAP. K tomuto chování může dojít například v případě, že číslo verze sestavení XBAP je statické a vy spustíte aplikaci XBAP z příkazového řádku. V takovém případě, protože číslo verze mezi verzí uloženou v mezipaměti (verze, která byla dříve spuštěna) a novou verzí zůstane stejné, není stažena nová verze aplikace XBAP. Místo toho je načtena verze uložená v mezipaměti.

 V těchto situacích můžete odebrat verzi uloženou v mezipaměti pomocí příkazu **Mage** (nainstalovaného se sadou Visual Studio nebo Windows SDK) na příkazovém řádku. Následující příkaz vymaže mezipaměť aplikace.

 ```console
 Mage.exe -cc
 ```

 Tento příkaz zajistí, že se spustí nejnovější verze aplikace XBAP. Při ladění aplikace v aplikaci Visual Studio by měla být spuštěna nejnovější verze aplikace XBAP. Obecně byste měli aktualizovat číslo verze nasazení u každého sestavení. Další informace o Mage naleznete v tématu [Mage. exe (Manifest Generation and Editing Tool)](../../tools/mage-exe-manifest-generation-and-editing-tool.md).

<a name="communicating_with_the_host_web_page"></a>
## <a name="communicating-with-the-host-web-page"></a>Komunikace s hostitelskou webovou stránkou
 Když je aplikace hostována v rámci bloku HTML, můžete komunikovat s webovou stránkou, která obsahuje aplikaci XBAP. To provedete načtením vlastnosti <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> <xref:System.Windows.Interop.BrowserInteropHelper>. Tato vlastnost vrátí objekt skriptu, který představuje okno HTML. Pak můžete přistupovat k vlastnostem, metodám a událostem [objektu window](https://go.microsoft.com/fwlink/?LinkId=160274) pomocí syntaxe regulárních teček. Můžete také získat přístup k metodám skriptu a globálním proměnným. Následující příklad ukazuje, jak načíst objekt skriptu a Zavřít prohlížeč.

 [!code-csharp[XbapBrowserInterop#10](~/samples/snippets/csharp/VS_Snippets_Wpf/xbapbrowserinterop/cs/page1.xaml.cs#10)]
 [!code-vb[XbapBrowserInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/xbapbrowserinterop/vb/page1.xaml.vb#10)]

### <a name="debugging-xbaps-that-use-hostscript"></a>Ladění aplikací XBAP, které používají HostScript
 Pokud XBAP používá objekt <xref:System.Windows.Interop.BrowserInteropHelper.HostScript%2A> ke komunikaci s oknem HTML, existují dvě nastavení, která je nutné zadat pro spuštění a ladění aplikace v aplikaci Visual Studio. Aplikace musí mít přístup k jejímu umístění původu a musíte ji spustit se stránkou HTML, která obsahuje aplikaci XBAP. Následující postup popisuje, jak tato dvě nastavení kontrolovat:

1. V aplikaci Visual Studio otevřete vlastnosti projektu.

2. Na kartě **zabezpečení** klikněte na **Upřesnit**.

     Zobrazí se dialogové okno Upřesnit nastavení zabezpečení.

3. Ujistěte se, že je zaškrtnuté políčko **udělit aplikaci přístup ke svému webu** , a pak klikněte na **OK**.

4. Na kartě **ladění** vyberte možnost **spustit prohlížeč s adresou URL** a zadejte adresu URL pro stránku HTML, která obsahuje XBAP.

5. V Internet Exploreru klikněte na tlačítko **nástroje** a pak vyberte **Možnosti Internetu**.

     Zobrazí se dialogové okno Možnosti Internetu.

6. Klikněte na kartu **Upřesnit** .

7. V seznamu **Nastavení** v části **zabezpečení**zaškrtněte políčko **povolený aktivní obsah, který se má v souborech v mém počítači spustit** .

8. Klikněte na tlačítko **OK**.

     Změny se projeví po restartování aplikace Internet Explorer.

> [!CAUTION]
> Povolení aktivního obsahu v aplikaci Internet Explorer může ohrozit váš počítač. Pokud nechcete změnit nastavení zabezpečení aplikace Internet Explorer, můžete spustit stránku HTML ze serveru a připojit k procesu ladicí program sady Visual Studio.

<a name="xbap_security_considerations"></a>
## <a name="xbap-security-considerations"></a>Problematika zabezpečení XBAP
 XBAP obvykle provádějí v izolovaném prostoru zabezpečení s částečnou důvěryhodností, který je omezen na sadu oprávnění zóny Internet. V důsledku toho vaše implementace musí podporovat podmnožinu prvků WPF, které jsou podporovány v zóně Internet, nebo musíte zvýšit oprávnění aplikace. Další informace najdete v tématu [zabezpečení](../security-wpf.md).

 Při použití ovládacího prvku <xref:System.Windows.Controls.WebBrowser> v aplikaci WPF interně vytvoří instanci ovládacího prvku ActiveX Native WebBrowser. Pokud je vaše aplikace s aplikací s částečnou důvěryhodností spuštěnou v aplikaci Internet Explorer, ovládací prvek ActiveX se spouští ve vyhrazeném vlákně procesu aplikace Internet Explorer. Proto platí následující omezení:

- Ovládací prvek <xref:System.Windows.Controls.WebBrowser> by měl poskytovat podobné chování jako prohlížeč hostitele, včetně omezení zabezpečení. Některá z těchto omezení zabezpečení lze ovládat prostřednictvím nastavení zabezpečení aplikace Internet Explorer. Další informace najdete v tématu [zabezpečení](../security-wpf.md).

- Výjimka je vyvolána, když je aplikace XBAP načtena mezi doménami na stránce HTML.

- Vstup je na samostatném vlákně z <xref:System.Windows.Controls.WebBrowser>WPF, takže vstup z klávesnice nejde zachytit a stav IME není sdílený.

- Časování nebo pořadí navigace může být odlišné vzhledem k ovládacímu prvku ActiveX spuštěnému v jiném vlákně. Například navigace na stránku není vždy zrušena spuštěním další žádosti o navigaci.

- Vlastní ovládací prvek ActiveX může mít problémy s komunikací, protože aplikace WPF běží v samostatném vlákně.

- <xref:System.Windows.Interop.HwndHost.MessageHook> není vyvolána, protože <xref:System.Windows.Interop.HwndHost> nemůže podtřídit okno spuštěné v jiném vlákně nebo procesu.

### <a name="creating-a-full-trust-xbap"></a>Vytvoření plně důvěryhodného XBAP
 Pokud vaše XBAP vyžaduje úplný vztah důvěryhodnosti, můžete změnit projekt a povolit toto oprávnění. Následující postup popisuje, jak povolit úplný vztah důvěryhodnosti:

1. V aplikaci Visual Studio otevřete vlastnosti projektu.

2. Na kartě **zabezpečení** vyberte možnost **aplikace s úplným vztahem důvěryhodnosti** .

 Toto nastavení provede následující změny:

- V souboru projektu je hodnota prvku `<TargetZone>` změněna na `Custom`.

- V manifestu aplikace (App. manifest) je atribut `Unrestricted="true"` přidán do prvku<xref:System.Security.PermissionSet>.

    ```xml
    <PermissionSet class="System.Security.PermissionSet"
                   version="1"
                   ID="Custom"
                   SameSite="site"
                   Unrestricted="true" />
    ```

### <a name="deploying-a-full-trust-xbap"></a>Nasazení plně důvěryhodného XBAP
 Při nasazení plně důvěryhodného prostředí XBAP, které nedodržuje model důvěryhodného nasazení ClickOnce, bude chování při spuštění aplikace uživatelem záviset na zóně zabezpečení. V některých případech se uživateli při pokusu o instalaci zobrazí upozornění. Uživatel může zvolit pokračování nebo instalaci zrušit. Následující tabulka popisuje chování aplikace pro každou zónu zabezpečení a to, co je třeba udělat, aby aplikace přijímala úplný vztah důvěryhodnosti.

|Zóna zabezpečení|Předvídatelně|Získání úplné důvěryhodnosti|
|-------------------|--------------|------------------------|
|Místní počítač|Automatický úplný vztah důvěryhodnosti|Není nutné provádět žádnou akci.|
|Intranetové a důvěryhodné weby|Dotázat se na úplný vztah důvěryhodnosti|Přihlaste se k aplikaci XBAP pomocí certifikátu, aby se uživateli zobrazila výzva ke zdroji v příkazovém řádku.|
|Internet|Neúspěch s "důvěryhodným neuděleným"|Podepište aplikaci XBAP pomocí certifikátu.|

> [!NOTE]
> Chování popsané v předchozí tabulce je pro plně důvěryhodná aplikace XBAP, které nedodržují model důvěryhodného nasazení ClickOnce.

 Doporučuje se použít model důvěryhodného nasazení ClickOnce pro nasazení plně důvěryhodného prostředí XBAP. Tento model umožňuje, aby se XBAP automaticky udělila Plná důvěra bez ohledu na zónu zabezpečení, takže se uživateli nezobrazí výzva. V rámci tohoto modelu musíte aplikaci podepsat pomocí certifikátu od důvěryhodného vydavatele. Další informace naleznete v tématu [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview) a [Úvod do podepisování kódu](https://go.microsoft.com/fwlink/?LinkId=166327).

<a name="xbap_start_time_performance_considerations"></a>
## <a name="xbap-start-time-performance-considerations"></a>Požadavky na výkon při zahájení XBAP
 Důležitým aspektem výkonu XBAP je čas svého spuštění. Pokud je XBAP první aplikaci WPF, která se má načíst, může *počáteční čas začít* být deset sekund nebo více. Důvodem je to, že stránka s průběhem je vykreslena pomocí WPF a modul CLR i WPF musí být pro zobrazení aplikace studeny.

 Od verze .NET Framework 3,5 SP1 je čas studeného startu v XBAP na začátku omezen zobrazením nespravované stránky průběh na začátku v cyklu nasazení. Stránka Průběh se zobrazí téměř ihned po spuštění aplikace, protože je zobrazena nativním hostujícím kódem a vykreslena ve formátu HTML.

 Vylepšená souběžnost sekvence stahování ClickOnce vylepšuje čas zahájení až o deset procent. Jakmile ClickOnce stáhne a ověří manifesty, spustí se stahování aplikace a indikátor průběhu se začne aktualizovat.

## <a name="see-also"></a>Viz také:

- [Konfigurace sady Visual Studio pro ladění aplikace Prohlížeče XAML za účelem volání webové služby](configure-vs-to-debug-a-xaml-browser-to-call-a-web-service.md)
- [Nasazení aplikace WPF](deploying-a-wpf-application-wpf.md)
