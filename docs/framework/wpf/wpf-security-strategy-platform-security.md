---
title: Strategie zabezpečení WPF – zabezpečení platformy
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform security model [WPF]
- Common Language Runtime (CLR) security features
- operating system security model [WPF]
- Internet Explorer security features [WPF]
- Security-Critical method
- CLR security features [WPF]
- security model [WPF]
- security model [WPF], platform
- WPF [WPF], about security model
- Windows Presentation Foundation [WPF], about security model
- security model [WPF], operating system
ms.assetid: 2a39a054-3e2a-4659-bcb7-8bcea490ba31
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c3c1654bd63d59bf6588b1dc18593ef7a33f37c0
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="wpf-security-strategy---platform-security"></a>Strategie zabezpečení WPF – zabezpečení platformy
Při [!INCLUDE[TLA#tla_wpf](../../../includes/tlasharptla-wpf-md.md)] nabízí mnoho služeb zabezpečení, také využívá funkce zabezpečení, základní platformy, která obsahuje operační systém, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], a [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)]. Tyto vrstvy kombinovat zajistit [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] model zabezpečení silné a obrany zabezpečení, který se pokouší vyhnout žádné jediný bod selhání, jak je znázorněno na následujícím obrázku:  
  
 ![Obrázek zabezpečení WPF](../../../docs/framework/wpf/media/windowplatformsecurity.PNG "windowplatformsecurity")  
  
 Zbývající část tohoto tématu popisuje funkce v každé z těchto úrovní, které se týkají [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] konkrétně.  
  

  
<a name="Operating_System_Security"></a>   
## <a name="operating-system-security"></a>Zabezpečení operačního systému  
 Minimální úroveň operačního systému, který je požadován [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] je [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)]. Základní částí [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] poskytuje několik funkcí zabezpečení, které tvoří základ zabezpečení pro všechny aplikace systému Windows, včetně těch, které vytvořené s [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] funkce zabezpečení systému zahrnuje [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] a jejich další rozšíření. Toto téma popisuje rozšiřuje tyto funkce zabezpečení, které jsou důležité pro [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], a jak [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] se integruje se s nimi zajistit další obrany zabezpečení.  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Kromě kontrolu obecné a posilování systému Windows, jsou tři klíčové funkce z [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] , se budeme zabývat v tomto tématu:  
  
-   /GS kompilace  
  
-   [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)].  
  
#### <a name="gs-compilation"></a>/GS kompilace  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] poskytuje ochranu a nutnosti rekompilace mnoho základní systémové knihovny, včetně všech objektů [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] závislosti, jako [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], které pomáhají omezit možnost přetečení vyrovnávací paměti. Toho dosáhnete pomocí parametru /GS kompilátoru příkazového řádku jazyka C/C++. I když přetečení vyrovnávací paměti musí být explicitně vyhnout, kompilace /GS poskytuje příklad obrany zabezpečení proti potenciální chyby zabezpečení, které jsou nedopatřením nebo neúmyslně vytvořené pomocí je.  
  
 Přetečení vyrovnávací paměti se upřednostňovaly příčinu mnoho vysoce účinného bezpečnostními hrozbami. Přetečení vyrovnávací paměti nastane, když útočník využívá výhod chybu kódu, který umožňuje vkládání škodlivého kódu, který zapíše za hranice vyrovnávací paměti. To pak umožňuje útočník napadnout procesu, ve kterém je prováděna kód tak, že přepíše návratové adresy funkce způsobí spuštění kódu útočníka. Výsledkem je škodlivý kód, který se spustí libovolný kód se stejnými oprávněními jako napadenému proces.  
  
 Na vysoké úrovni příznak /GS kompilátoru chrání před některé potenciální přetečení vyrovnávací paměti vložením speciální zabezpečení souboru cookie k ochraně na návratovou adresu funkci, která má místní řetězec vyrovnávací paměti. Po návratu funkci soubor cookie zabezpečení se porovná s jejich předchozí hodnotu. Pokud hodnota změnila, pravděpodobně došlo k přetečení vyrovnávací paměti a tento proces je zastavena s chybový stav. Zastavení procesu zabrání spuštění potenciálně škodlivého kódu. V tématu [/GS (Kontrola zabezpečení vyrovnávací paměti)](http://msdn.microsoft.com/library/8dbf701c.aspx) další podrobnosti.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Kompiluje s příznakem /GS přidat ještě další vrstvu obrany [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace.  
  
#### <a name="microsoft-windows-update-enhancements"></a>Vylepšení služby Microsoft Windows Update  
 [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)] je taky vylepšené v [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] ke zjednodušení procesu pro stahování a instalace aktualizací. Tyto změny výrazně zvýšit zabezpečení pro [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] zákazníků tím, že pomáhá zajistit, že jejich systémy jsou aktuální, zejména s ohledem na aktualizace zabezpečení.  
  
<a name="Windows_Vista"></a>   
### <a name="windows-vista"></a>Windows Vista  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uživatelé na [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] bude těžit z rozšířené další zabezpečení operačního systému, včetně "Nejnižších oprávnění uživatele přístupu", kontroly integrity kódu a oprávnění izolace.  
  
#### <a name="user-account-control-uac"></a>Řízení uživatelských účtů (UAC)  
 V současné době Windows uživatelé zpravidla spustit s oprávněním správce, protože řada aplikací vyžaduje pro instalaci nebo spuštění nebo obojí. Schopnost zápis výchozí nastavení aplikace do registru je jedním z příkladů.  
  
 Spuštěn s oprávněními správce skutečně znamená aplikace, které se spouštějí z procesy, které jsou udělena oprávnění správce. Zabezpečení dopad to je, že škodlivý kód, který hijacks procesu spuštěného s oprávněními správce automaticky zdědí těchto oprávnění, včetně přístupu k důležitým systémovým prostředkům.  
  
 Jedním ze způsobů hrozbě zabezpečení je spuštění aplikace s minimem oprávnění, které jsou požadovány. To se označuje jako Princip nejnižších nutných oprávnění a je základní funkce [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] operačního systému. Tato funkce je volána řízení uživatelských účtů (UAC) a je používána [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] nástroje Řízení uživatelských účtů klíče dvěma způsoby:  
  
-   Spouštět většinu aplikací s oprávněními nástroje Řízení uživatelských účtů ve výchozím nastavení, i když uživatel je správcem; jenom aplikace, které potřebují oprávnění správce se spustí s oprávněními správce. Pokud chcete spustit s oprávněními správce, aplikace musí být explicitně označen buď jejich aplikace manifestu nebo jako položku v zásadách zabezpečení.  
  
-   K zajištění kompatibility řešení, jako je virtualizace. Mnoho aplikací se například pokusíte zapsat do umístění s omezeným přístupem, jako je C:\Program Files. Pro aplikace provádění řízení Uživatelských účtů alternativní uživatelská umístění existuje, který nevyžaduje oprávnění správce k zápisu. Pro aplikace spuštěné v rámci nástroje Řízení uživatelských účtů nástroje Řízení uživatelských účtů Virtualizuje C:\Program Files, aby aplikace, kteří myslíte, že jsou zápis do něj jsou ve skutečnosti zápis do alternativního, uživatelská umístění. Tento druh kompatibility pracovní umožňuje operačního systému spustit mnoho aplikací, které nebylo možné spustit dříve v řízení uživatelských účtů.  
  
#### <a name="code-integrity-checks"></a>Kontroly Integrity kódu  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] obsahuje podrobnější kontroly integrity kódu můžete zabránit se vložit do systému souborů nebo do jádra během zatížení nebo spustit škodlivý kód. To má význam nad rámec Ochrana systému souborů.  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Proces omezená práva pro webové aplikace  
 Hostované prohlížečem [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace provést v rámci izolovaného prostoru zónu Internetu. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Integrace s [!INCLUDE[TLA#tla_ie](../../../includes/tlasharptla-ie-md.md)] rozšiřuje tuto ochranu s další podporu.  
  
#### <a name="internet-explorer-6-service-pack-2-and-internet-explorer-7-for-xp"></a>Internet Explorer 6 Service Pack 2 a prohlížeče Internet Explorer 7 pro XP  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] využívá zabezpečení operačního systému omezením proces oprávnění pro [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] pro další ochranu. Před hostované prohlížečem [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace spuštěna, operační systém vytvoří hostitelský proces, který odebere nepotřebná oprávnění z token procesu. Mezi příklady oprávnění, které jsou odebrány patří možnost vypnout počítač uživatele, zatížení ovladače a přístup pro čtení ke všem souborům na počítači.  
  
#### <a name="internet-explorer-7-for-vista"></a>Internet Explorer 7 pro Vista  
 V [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace spouštět v chráněném režimu. Konkrétně [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] spustit s střední úrovně integrity.  
  
#### <a name="defense-in-depth-layer"></a>Obrany zabezpečení vrstvy  
 Vzhledem k tomu [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] jsou obecně v izolovaném prostoru pomocí Internetu oprávnění sada zón, odebrání těchto oprávnění nepříznivý vliv [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] z hlediska kompatibility. Místo toho je vytvořena dodatečnou vrstvu vícevrstvého do hloubky; Pokud v izolovaném prostoru aplikace je možné zneužít jiných vrstev a napadnout proces, proces bude stále pouze oprávnění omezená.  
  
 V tématu [pomocí nejméně privilegovaným uživatelského účtu](http://technet.microsoft.com/library/cc700846.aspx).  
  
<a name="Common_Language_Runtime_Security"></a>   
## <a name="common-language-runtime-security"></a>Běžné zabezpečení Runtime jazyka  
 [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] Nabízí řadu výhod zabezpečení klíčů, které zahrnují ověření a ověření, [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]a metody kritické zabezpečení.  
  
<a name="Validation_and_Verification"></a>   
### <a name="validation-and-verification"></a>Ověřování a ověřování  
 Poskytuje izolaci sestavení a integritu, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] používá proces ověření. [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] ověření zajistí, že jsou tím, že ověří jejich přenosné spustitelný soubor (PE) formát souboru pro adresy, které bod mimo sestavení izolované sestavení. [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] ověření také ověří integritu metadata, která se vloží v rámci sestavení.  
  
 Zajistit bezpečnost typů pomáhá zabránit běžné problémy se zabezpečením (např. vyrovnávací přetečení) a povolte sandboxing prostřednictvím podproces izolace [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] zabezpečení používá koncept ověření.  
  
 Spravované aplikace jsou zkompilovány do Microsoft Intermediate Language (MSIL). Po provedení metody ve spravované aplikaci jsou jeho MSIL kompiluje do nativního kódu prostřednictvím kompilace JIT (JIT). JIT – kompilace zahrnuje proces ověření, který používá mnoho zabezpečení a odolnosti pravidla, která zajišťují, že kód není:  
  
-   Porušují kontrakty typu  
  
-   Zavést přetečení vyrovnávací paměti  
  
-   Velkým přístup k paměti.  
  
 Spravovaný kód, který není v souladu s pravidel ověřování není povoleno provést, pokud bude považován za důvěryhodný kód.  
  
 Výhodou ověřitelný kód je klíče důvod, proč [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] vychází [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)]. V rozsahu, který se používá ověřitelný kód, je výrazně snížena možnost zneužitím možných ohrožení zabezpečení.  
  
<a name="Code_Access_Security"></a>   
### <a name="code-access-security"></a>Zabezpečení přístupu kódu  
 Klientský počítač zpřístupní širokou škálu prostředků, spravované aplikace můžou mít přístup k, včetně systému souborů, registru, tisk služby, uživatelské rozhraní, reflexe a proměnných prostředí. Před spravované aplikaci můžete získat přístup k žádnému z prostředků na klientský počítač, musí mít [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)] k tomu oprávnění. Oprávnění v [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] je podtřídou třídy <xref:System.Security.CodeAccessPermission>; [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] implementuje jeden podtřídami pro přístup každý prostředek, který spravované aplikace.  
  
 Sadu oprávnění, která udělují spravované aplikaci [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] po jeho spuštění, provádění se označuje jako sadu oprávnění a je dáno důkaz poskytuje aplikace. Pro [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikací, důkaz, že je k dispozici je umístění, nebo zónu, ze kterého se spuštění aplikace. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] identifikuje následující zóny:  
  
-   **Počítač**. Aplikace spustí z klientský počítač (plně důvěryhodný).  
  
-   **Místní Intranet**. Aplikace spustí z intranetu. (Poněkud důvěryhodný).  
  
-   **Internet**. Aplikace spustí z Internetu. (Nejméně důvěryhodné).  
  
-   **Důvěryhodné servery**. Aplikace identifikovaný uživatele jako důvěryhodný. (Nejméně důvěryhodné).  
  
-   **Nedůvěryhodná lokality**. Aplikace zjistí uživatelem se nedůvěryhodný. (Nedůvěryhodné).  
  
 Pro každou z těchto zón [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] poskytuje sadu předdefinovaných oprávnění, která zahrnuje oprávnění a který by odpovídal úroveň důvěryhodnosti spojené s každou. Mezi ně patří:  
  
-   **FullTrust**. Pro spuštění z aplikace **Můj počítač** zóny. Všechny možné oprávnění.  
  
-   **LocalIntranet**. Pro spuštění z aplikace **místní Intranet** zóny. Podmnožinu oprávnění jsou udělena zajistit střední přístup k prostředkům klientský počítač, včetně izolovaného úložiště, neomezený přístup k uživatelskému rozhraní, dialogová okna neomezený souboru, omezené reflexe, omezený přístup k proměnné prostředí. Oprávnění u důležitých prostředků jako registru nejsou zadány.  
  
-   **Internet**. Pro spuštění z aplikace **Internet** nebo **Důvěryhodné servery** zóny. Podmnožinu oprávnění jsou udělená zadaný omezený přístup k prostředkům, klientský počítač, včetně izolovaného úložiště soubor otevřít jenom a omezený uživatelského rozhraní. Toto oprávnění v podstatě nastaví izoluje aplikace od klientský počítač.  
  
 Označený z aplikace **umístěné na serverech** zóny jsou udělena žádná oprávnění podle [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] vůbec. Sada předdefinovaných oprávnění v důsledku toho neexistuje pro ně.  
  
 Následující obrázek ukazuje vztah mezi zóny, sady oprávnění, oprávnění a prostředky.  
  
 ![Sady oprávnění certifikační Autority](../../../docs/framework/wpf/media/caspermissionsets.png "CASPermissionSets")  
  
 Omezení Internetu zóny zabezpečení izolovaného prostoru se rovněž vztahují na všechny kód, který [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] importuje z knihovny systému, včetně [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. To zajišťuje, že každý bit kód uzamčeném dolů, i [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Bohužel, abyste mohli provést, [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] musí provést funkce, která vyžaduje další oprávnění než ty, které ve izolovaného prostoru internetové zóny zabezpečení povolené.  
  
 Vezměte v úvahu [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] aplikace, která zahrnuje následující stránka:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Chcete-li to provést [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], základní [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kód musí být spuštěn další funkce, než je k dispozici volání [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], včetně:  
  
-   Vytváření popisovač okna (hWnd) pro vykreslení  
  
-   Odeslání zprávy  
  
-   Načítání písmo Tahoma  
  
 Z zabezpečení by závažné bod pohledu, umožňuje přímý přístup k jakémukoli z těchto operací z aplikace v izolovaném prostoru.  
  
 Naštěstí [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] je určen k této situaci tím, že tyto operace provést s vyššími oprávněními jménem aplikace v izolovaném prostoru. Při všech [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] operace jsou zkontrolován omezenými oprávněními zabezpečení zóně Internet domény aplikace [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] (stejně jako u jiných knihovny system) je povolen sadu oprávnění, která zahrnuje všechny možné oprávnění  
  
 To vyžaduje, aby [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] obdrží zvýšená oprávnění při brání těchto oprávnění se řídí sada oprávnění zón Internetu hostitele domény aplikace.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] to provádí pomocí **Assert** metoda oprávnění. Následující kód ukazuje, jak se to stane.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Assert** v podstatě brání neomezená oprávnění vyžadují [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] z je omezené na základě Internetu zónu oprávnění [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)].  
  
 Z hlediska platformy [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] zodpovídá za použití **Assert** správně; nesprávné použití **Assert** může povolit škodlivý kód o zvýšení oprávnění. V důsledku toho je pak potřeba volat pouze **Assert** v případě potřeby, a zajistit, že izolovaného prostoru zůstanou beze změn omezení. Například otevřete náhodných soubory kódu v izolovaném prostoru není povoleno, ale je povoleno použít písma. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Umožňuje v izolovaném prostoru aplikacím používat funkce písma voláním **Assert**a pro [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] číst soubory, které jsou známé tak, aby obsahovala písma, která jménem aplikace v izolovaném prostoru.  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce – nasazení  
 [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] je komplexní nasazení technologie, která je součástí [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)]a integruje se službou [!INCLUDE[TLA#tla_visualstu](../../../includes/tlasharptla-visualstu-md.md)] (viz [Přehled nasazení ClickOnce](http://msdn.microsoft.com/library/142dbbz4.aspx) podrobné informace). Samostatné [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] mohou být aplikace nasazeny pomocí [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)], zatímco aplikace hostované prohlížečem musí být nasazený s [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)].  
  
 Aplikace nasazené pomocí [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)] jsou uvedeny další vrstvu zabezpečení [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]; v podstatě [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] nasazené aplikace žádostí o oprávnění, které potřebují. Mají přístup pouze ta oprávnění, pokud nepřekročí sadu oprávnění pro zónu, ve kterém je aplikace nasazená. Snížením sadu oprávnění, jenom na ty, které jsou potřeba, i když je menší než ty, které jsou zadané sadou oprávnění spuštění zóny, počet prostředků, které má aplikace přístup k snížit na úplné minimum. V důsledku toho pokud aplikace je napadeny, se snižuje potenciální škody na klientský počítač.  
  
<a name="Security_Critical_Methodology"></a>   
### <a name="security-critical-methodology"></a>Metodologie kritické pro zabezpečení  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Kód, který používá oprávnění povolit izolovaném prostoru zóně Internet [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] aplikace musí být vždy na nejvyšší možné úrovni auditu zabezpečení a řízení. Pro usnadnění tohoto požadavku [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] poskytuje nové podpory pro správu kód, který zvyšuje oprávnění. Konkrétně [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] slouží k identifikaci kódu, která zvyšuje oprávnění a označte ji s <xref:System.Security.SecurityCriticalAttribute>; žádný kód neoznačené <xref:System.Security.SecurityCriticalAttribute> stane *transparentní* použití této metody. Naopak spravovaný kód, který není označen atributem <xref:System.Security.SecurityCriticalAttribute> zabráněno zvýšená oprávnění oprávnění.  
  
 Kritický pro zabezpečení metody umožňuje uspořádání [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kód, který zvyšuje oprávnění do *kritický pro zabezpečení jádra*, se zbývajícími se transparentní. Izolování kód kritický pro zabezpečení umožňuje [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] technickému týmu soustředit se na další bezpečnostní analýzy a zdroj ovládací prvek v kritické pro zabezpečení jádra vedle postupy standardní zabezpečení (najdete v části [strategie zabezpečení WPF -Inženýrství zabezpečení](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)).  
  
 Všimněte si, že [!INCLUDE[TLA2#tla_winfx](../../../includes/tla2sharptla-winfx-md.md)] umožňuje důvěryhodný kód rozšířit [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] izolovaného prostoru zónu Internetu tím, že se vývojáři k zápisu spravovaná sestavení, které jsou označené <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) a nasadili pro uživatele globální mezipaměti sestavení (GAC). Označení sestavení s APTCA je operace vysoce citlivé a zabezpečení, protože umožňuje žádný kód k volání této položky assembly, včetně škodlivý kód z Internetu. Extrémně opatrní a osvědčené postupy musí být použit při této činnosti a uživatelé musí vybrat důvěřovat softwaru v pořadí pro jeho instalaci.  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## <a name="microsoft-internet-explorer-security"></a>Zabezpečení aplikace Microsoft Internet Explorer  
 Kromě omezení problémy se zabezpečením a zjednodušit konfiguraci zabezpečení [!INCLUDE[TLA#tla_ie6sp2](../../../includes/tlasharptla-ie6sp2-md.md)] obsahuje několik funkcí tohoto vylepšení zabezpečení, které zlepšují zabezpečení pro uživatele [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]. Těžiště tyto funkce se pokusí povolit uživatelům větší kontrolu nad jejich možnosti procházení.  
  
 Před verzí [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)], uživatelé mohou podléhat žádné z následujících:  
  
-   Náhodné místní windows.  
  
-   Matoucí skriptu přesměrování.  
  
-   Řada zabezpečení dialogová okna na některé weby.  
  
 V některých případech by weby nedůvěryhodným pokusu přimět uživatele pomocí falšování identity instalace [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] nebo opakovaně zobrazen [!INCLUDE[TLA#tla_actx](../../../includes/tlasharptla-actx-md.md)] dialogové okno instalace, i když jeho zrušením uživatele. Použití těchto postupů je možné, že máte byl nalákaní velký počet uživatelů, přijímání nízký rozhodnutí, která byla vygenerována v instalaci aplikací, spywaru.  
  
 [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] zahrnuje několik funkcí zmírnit tyto typy problémů, které se týkají koncept zahájení uživatelem. [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] zjistí, když uživatel klikne na odkaz nebo stránky element před akci, která se označuje jako *zahájení uživatelem*a jsou za jinak než při podobné akce místo aktivaci pomocí skriptu na stránce. Jako příklad [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] zahrnuje **blokování automaticky otevíraných oken** , rozpozná, když uživatel klikne na tlačítko před stránce vytvoření automaticky otevírané okno. To umožňuje [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] povolit automaticky otevíraná okna nejvíce neškodné zároveň je možné zabránit automaticky otevíraná okna, které uživatelé požádat o ani má. Blokované automaticky otevíraná okna jsou zachycena v rámci nové **informační panel**, což umožňuje uživatelům ručně přepsat blok a zobrazovat místní nabídce.  
  
 Stejné logiky, která uživatel spuštění platí také pro **otevřete**/**Uložit** výzvy zabezpečení. [!INCLUDE[TLA2#tla_actx](../../../includes/tla2sharptla-actx-md.md)] dialogová okna instalace jsou vždy zachycena v části informační panel. Pokud představují upgradu z dříve nainstalovaných ovládacího prvku. Tyto míry kombinovat uživatelům bezpečnější a více řízené uživatelské prostředí vzhledem k tomu, že byla chráněná před weby, které je pro instalaci softwaru nechtěné nebo škodlivé obtěžovat.  
  
 Tato funkce také chránit zákazníkům, kteří používají [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] a přejděte do webové stránky, které mohly stáhnout a nainstalovat [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace. Konkrétně je to proto, [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] nabízí lepší uživatelské prostředí, která snižuje riziko pro uživatele k instalaci škodlivého nebo devious aplikací bez ohledu na to, jakou technologii byl použit k vytvoření, včetně [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Přidá do tyto ochrany pomocí [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] aby se usnadnilo stahování svým aplikacím přes Internet. Vzhledem k tomu [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] provést v rámci izolovaného prostoru se Internetu zóny zabezpečení, může být spuštěn bezproblémově. Na druhé straně samostatné [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace vyžadují úplný vztah důvěryhodnosti k provedení. Pro tyto aplikace [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] se zobrazí dialogové okno zabezpečení během procesu spuštění oznámit použití aplikace dodatečné požadavky na zabezpečení. Ale to musí být spuštěna uživatelem, se řídí také logikou iniciované uživatelem a můžete zrušit.  
  
 [!INCLUDE[TLA2#tla_ie7](../../../includes/tla2sharptla-ie7-md.md)] zahrnuje a rozšiřuje možnosti zabezpečení [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] v rámci trvalé snahy o zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 [Principy zabezpečení v aplikaci Microsoft Internet Explorer 6 v systému Windows XP SP2](http://www.microsoft.com/downloads/details.aspx?FamilyId=E550F940-37A0-4541-B5E2-704AB386C3ED&displaylang=en)  
 [Principy a práci v chráněném režimu Internet Exploreru](http://msdn.microsoft.com/library/bb250462.aspx)  
 [Windows XP Service Pack 3](http://www.microsoft.com/windows/products/windowsxp/sp3/default.mspx)  
 [Průvodce zabezpečením Windows Vista](http://www.microsoft.com/downloads/details.aspx?familyid=a3d1bbed-7f35-4e72-bfb5-b84a526c1565&displaylang=en)  
 [Zabezpečení přístupu kódu](../../../docs/framework/misc/code-access-security.md)  
 [Zabezpečení](../../../docs/framework/wpf/security-wpf.md)  
 [Částečné zabezpečení důvěryhodnosti WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [Strategie zabezpečení WPF – engineering zabezpečení](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)
