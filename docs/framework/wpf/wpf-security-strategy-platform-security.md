---
title: Strategie zabezpečení WPF – zabezpečení platformy
ms.date: 03/30/2017
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
ms.openlocfilehash: 5b40302d93ce1bfc378b86210ed7bb54732d294b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756768"
---
# <a name="wpf-security-strategy---platform-security"></a>Strategie zabezpečení WPF – zabezpečení platformy
Windows Presentation Foundation (WPF) poskytuje širokou škálu služeb zabezpečení, také využívá podkladovou platformu, která obsahuje operační systém, funkce zabezpečení [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], a [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)]. Tyto vrstvy se dá zajistit [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] silné zabezpečení obrany v modelu, který se pokouší vyhnout jakékoli jediným bodem selhání, jak je znázorněno na následujícím obrázku:  
  
 ![Diagram zobrazující model zabezpečení WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 Zbývající část tohoto tématu jsou popsané funkce v každém z těchto úrovní, které se týkají [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] zvlášť.  

<a name="Operating_System_Security"></a>   
## <a name="operating-system-security"></a>Zabezpečení operačního systému  
 Minimální úroveň operačního systému, který vyžaduje [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] je [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)]. Jádro [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] poskytuje několik funkcí zabezpečení, které tvoří základ zabezpečení pro všechny aplikace Windows, včetně těch vytvořených pomocí [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] zahrnuje funkce zabezpečení [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] a jejich další rozšíření. Toto téma popisuje škálu tyto funkce zabezpečení, které jsou důležité pro [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], také o tom [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] integruje do nich další defense-in-depth.  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Kromě obecné kontrolu a posílení Windows, jsou k dispozici tři klíčové funkce z [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] , který se budeme zabývat v tomto tématu:  
  
- /GS kompilace  
  
- [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)].  
  
#### <a name="gs-compilation"></a>/GS kompilace  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] poskytuje ochranu opětovnou kompilací mnoho core systémových knihoven, včetně všech objektů [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] závislosti, jako [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], aby mohlo včas reagovat přetečení vyrovnávací paměti. Toho dosáhnete pomocí parametru /GS kompilátoru příkazového řádku jazyka C/C++. I když přetečení vyrovnávací paměti by měla být explicitně vyhnout, /GS kompilace poskytuje příklad v obrany proti potenciální ohrožení zabezpečení, které jsou vytvořeny neúmyslně nebo záměrně – podle nich.  
  
 Přetečení vyrovnávací paměti v minulosti byly příčinou mnoho bezpečnostními zesíleným zabezpečením. Pokud útočník využívá výhod chybu kódu, který umožňuje vkládání škodlivý kód, který zapíše za hranice vyrovnávací paměti dojde k přetečení vyrovnávací paměti. Díky tomu pak útočníka o zneužití procesu, ve kterém je kód spuštěn přepsáním návratovou adresu funkce způsobí spuštění kódu útočníka. Výsledkem je škodlivý kód, který se spustí libovolný kód se stejnými oprávněními jako napadenému proces.  
  
 Na vysoké úrovni příznak /GS kompilátoru chrání proti některé potenciální přetečení vyrovnávací paměti vložením speciální zabezpečení souboru cookie k ochraně návratovou adresu funkce s místní vyrovnávací paměti řetězců. Po vrácení funkce, soubor cookie zabezpečení je ve srovnání s původní hodnotu. Pokud hodnota změnila, pravděpodobně došlo k přetečení vyrovnávací paměti a proces se ukončí s chybovou podmínku. Zastavení procesu zabrání spouštění potenciálně škodlivého kódu. Zobrazit [/GS (Kontrola zabezpečení vyrovnávací paměti)](/cpp/build/reference/gs-buffer-security-check) další podrobnosti.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] je zkompilován s příznak /GS pro přidání další vrstvy Defense za účelem [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikací.  
  
#### <a name="microsoft-windows-update-enhancements"></a>Vylepšení aktualizace Microsoft Windows  
 [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)] také jsme vylepšili v [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] ke zjednodušení procesu pro stahování a instalaci aktualizací. Tyto změny výrazně zvýšit zabezpečení [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] zákazníků tím, že pomáhá zajistit, že jejich systémů jsou aktuální, zejména s ohledem na aktualizace zabezpečení.  
  
<a name="Windows_Vista"></a>   
### <a name="windows-vista"></a>Windows Vista  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] uživatelé na [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] bude mít prospěch z vylepšení další zabezpečení operačního systému, včetně "Nejnižších možných oprávnění uživatelského přístupu", kontroly integrity kódu a oprávnění izolace.  
  
#### <a name="user-account-control-uac"></a>Řízení uživatelských účtů (UAC)  
 V současné době Windows uživatelé mají tendenci spustit s oprávněními správce, protože řada aplikací vyžaduje pro instalaci nebo spuštění nebo obojí. Schopnost zápis výchozí nastavení aplikace do registru není jedním z příkladů.  
  
 Pomocí oprávnění správce ve skutečnosti znamená, že aplikace můžete spustit z procesů, které jsou udělena oprávnění správce. Dopad na zabezpečení tohoto je, že škodlivý kód, který napadení procesu spuštěného s oprávněními správce automaticky zdědí tato oprávnění, včetně přístupu ke důležité systémové prostředky.  
  
 Jedním ze způsobů pro ochranu před toto ohrožení zabezpečení je ke spouštění aplikací s minimem oprávnění, které jsou požadovány. To se označuje jako Princip nejnižších oprávnění a je základní funkce [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] operačního systému. Tato funkce se nazývá řízení uživatelských účtů (UAC) a používá [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] nástroje Řízení uživatelských účtů klíčů dvěma způsoby:  
  
- Spouštět většinu aplikací s oprávněními nástroje Řízení uživatelských účtů ve výchozím nastavení, i v případě, že uživatel je správcem; jenom aplikace, které je třeba oprávnění správce se spustí s oprávněními správce. Spustit s oprávněními správce, aplikace musí být explicitně označeny buď jejich aplikace manifestu nebo jako položka v zásadách zabezpečení.  
  
- Pro zajištění kompatibility řešení, jako je virtualizace. Například mnoho aplikací pokusu o zápis do umístění s omezeným přístupem, například C:\Program Files. Pro aplikace spouští v rámci nástroje Řízení uživatelských účtů existuje umístění služby alternativní na uživatele, která nevyžaduje oprávnění správce pro zápis do. Pro aplikace běžící v rámci nástroje Řízení uživatelských účtů nástroje Řízení uživatelských účtů Virtualizuje C:\Program Files tak, že aplikace, kteří myslíte, že se zápis do něj jsou ve skutečnosti zápis do alternativního, umístění jednotlivých uživatelů. Tento druh kompatibility pracovní umožňuje operačnímu systému ke spouštění mnoho aplikací, které nelze spustit dříve v nástroji Řízení uživatelských účtů.  
  
#### <a name="code-integrity-checks"></a>Kontrola Integrity kódu  
 [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] zahrnuje lepší kontroly integrity kódu zabránit se vloží do systému souborů nebo do jádra v době zatížení nebo spustit škodlivý kód. To jde nad rámec Ochrana systému souborů.  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Proces omezená práva pro aplikace hostované prohlížečem  
 Hostované v prohlížeči [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace jsou spouštěny v rámci sandboxu zóny Internet. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Integrace s [!INCLUDE[TLA#tla_ie](../../../includes/tlasharptla-ie-md.md)] rozšiřuje tuto ochranu s dodatečnou podporou.  
  
#### <a name="internet-explorer-6-service-pack-2-and-internet-explorer-7-for-xp"></a>Internet Explorer 6 Service Pack 2 a Internet Explorer 7 pro XP  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] využívá zabezpečení operačního systému tím, že omezíte oprávnění procesu pro [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] další ochranu. Před hostovaná prohlížečem [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] spuštění aplikace, operační systém vytvoří hostitelský proces, který odstraňuje nepotřebná oprávnění z tokenu procesu. Mezi příklady oprávnění, které jsou odebrány patří možnost vypnout počítač uživatele, zatížení ovladače a oprávnění ke čtení pro všechny soubory v počítači.  
  
#### <a name="internet-explorer-7-for-vista"></a>Internet Explorer 7, Vista  
 V [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace běží v chráněném režimu. Konkrétně [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] spustit s střední úrovni integrity.  
  
#### <a name="defense-in-depth-layer"></a>Vrstvy v obrany  
 Protože [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] jsou obecně v izolovaném prostoru prostřednictvím Internetu sadu oprávnění zóny, odebírání těchto oprávnění nepoškodí [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] z hlediska kompatibility. Místo toho se vytvoří další úroveň v obrany; Pokud aplikace v izolovaném prostoru je schopen zneužít jinými vrstvami a zneužití procesu, proces bude stále pouze máte omezená oprávnění.  
  
 Zobrazit [pomocí nejméně privilegovaný uživatelský účet](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
<a name="Common_Language_Runtime_Security"></a>   
## <a name="common-language-runtime-security"></a>Zabezpečení služby Common Language Runtime  
 [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] Nabízí řadu výhod zabezpečení klíče, které zahrnují ověření a ověření, [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]a důležité metody zabezpečení.  
  
<a name="Validation_and_Verification"></a>   
### <a name="validation-and-verification"></a>Ověřování a ověřování  
 Pro zajištění izolace sestavení a integritu, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] používá proces ověření. [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] ověření zajišťuje, že sestavení jsou izolované tak jejich formát souboru Portable Executable (PE) pro adresy, které odkazují mimo sestavení. [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] ověřování také ověří integritu metadat, který je vložený v rámci sestavení.  
  
 Zajistit bezpečnost typů pomáhá zabránit běžné problémy se zabezpečením (např. vyrovnávací přetečení) a povolit sandboxing prostřednictvím podproces izolace [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] security používá koncept ověření.  
  
 Spravované aplikace jsou zkompilovány do Microsoft Intermediate Language (MSIL). Při spuštění metody ve spravované aplikaci, jeho jazyka MSIL je kompilován do nativního kódu prostřednictvím kompilace za běhu (JIT). Kompilace JIT zahrnuje ověřovací proces, který používá mnoho pravidla zabezpečení a odolnosti, které zajistí, že kód není:  
  
- Porušují typ smlouvy  
  
- Zavést přetečení vyrovnávací paměti  
  
- Nečekaně přístup k paměti.  
  
 Spravovaný kód, který není v souladu s pravidly ověřování není povoleno provést, pokud bude považován za důvěryhodný kód.  
  
 Výhodou ověřitelný kód je klíče důvod proč [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] založený na rozhraní .NET Framework. V rozsahu, který se používá ověřitelný kód, je výrazně snížili možnost zneužití možných ohrožení zabezpečení.  
  
<a name="Code_Access_Security"></a>   
### <a name="code-access-security"></a>Zabezpečení přístupu kódu  
 Klientský počítač poskytuje širokou škálu prostředků, že spravovaná aplikace může mít přístup k, včetně systému souborů, registr, tiskové služby, uživatelské rozhraní, reflexe a proměnných prostředí. Spravované aplikace mohli získat přístup ke některý z prostředků v klientském počítači, musí mít oprávnění rozhraní .NET Framework. U oprávnění v [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] je podtřídou třídy <xref:System.Security.CodeAccessPermission>; [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] implementuje jednu podtřídu pro přístup k jednotlivých prostředků, které spravované aplikace.  
  
 Sadu oprávnění, která spravované aplikace je [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] po jeho spuštění, provádění se označuje jako sadu oprávnění a je určena legitimací poskytovaný aplikací. Pro [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikací, důkaz, že je k dispozici je umístění nebo oblasti, ve kterém je spuštěných aplikací. [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] identifikuje tyto oblasti:  
  
- **Tento počítač**. Aplikace spustí z klientského počítače (plně důvěryhodná).  
  
- **Místní Intranet**. Aplikace spustí z intranetu. (Částečně důvěryhodných).  
  
- **Internet**. Aplikace spustí ze sítě Internet. (Nejméně důvěryhodné).  
  
- **Důvěryhodné servery**. Aplikace identifikován jako důvěryhodný uživatel. (Nejméně důvěryhodné).  
  
- **Nedůvěryhodné weby**. Aplikace identifikovány uživatelem, jako je nedůvěryhodný. (Nedůvěryhodné).  
  
 Pro každou z těchto oblastí [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] poskytuje sadu předdefinovaných oprávnění, která zahrnuje všechna oprávnění který by odpovídal úroveň vztahu důvěryhodnosti spojené s jednotlivými. Zde jsou některé z nich:  
  
- **FullTrust**. Pro spuštění z aplikace **tento počítač** zóny. Všechny možné oprávnění jsou udělena.  
  
- **LocalIntranet**. Pro spuštění z aplikace **místní Intranet** zóny. Podmnožinu oprávnění jsou udělena a zajistit tak střední přístup k prostředkům, klientský počítač, včetně izolovaného úložiště, neomezený přístup k uživatelskému rozhraní, dialogová okna neomezený souboru, omezené reflexe, omezený přístup k proměnným prostředí. Nejsou k dispozici oprávnění u důležitých prostředků jako registru.  
  
- **Internet**. Pro spuštění z aplikace **Internet** nebo **Důvěryhodné servery** zóny. Podmnožina oprávnění jsou udělena zadaný omezený přístup k prostředkům, klientský počítač, včetně izolované úložiště souboru otevřete pouze a omezené uživatelského rozhraní. Toto oprávnění nastavena v podstatě izoluje aplikace od klientského počítače.  
  
 Označený z aplikace **nedůvěryhodné weby** zóny jsou udělena žádná oprávnění podle [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] vůbec. V důsledku toho sada předdefinovaných oprávnění neexistuje pro ně.  
  
 Následující obrázek ukazuje vztah mezi zónami, sady oprávnění, oprávnění a prostředky:  
  
 ![Diagram zobrazující průběh sady oprávnění certifikační Autority.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Omezení sandboxu zabezpečení zóně Internet stejnou měrou vztahují na jakýkoli kód, který XBAP, který importuje z knihovny systému, včetně [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Tím se zajistí, že každý bit kód je uzamčený, i [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Aby bylo možné provést, bohužel XBAP potřebuje ke spuštění funkce, které vyžadují více oprávnění než ty, které zajišťuje sandboxu zabezpečení zóně Internet.  
  
 Vezměte v úvahu aplikace XBAP, který obsahuje následující stránka:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 K provedení této XBAP, základní [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kód musí být spuštěn víc funkcí než je k dispozici k volání XBAP, včetně:  
  
- Vytváření popisovač okna (HWND) pro vykreslování  
  
- Odeslání zprávy  
  
- Načítání Tahoma písma  
  
 Z zabezpečení by katastrofickými pohledu, umožňuje přímý přístup k jakémukoli z těchto operací z aplikace v izolovaném prostoru.  
  
 Naštěstí [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] určeného tuto situaci lze vyřešit tím, že tyto operace provádět s vyššími oprávněními jménem aplikace v izolovaném prostoru. Při všech [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] operace jsou porovnávána s omezenými oprávněními zabezpečení zóně Internet domény aplikace XBAP, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] (stejně jako u jiných knihovnách system) je udělena sada oprávnění, která zahrnuje všechna oprávnění je to možné.
  
 To vyžaduje, aby [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] obdrží zvýšená oprávnění, a brání tato oprávnění se řídí sada oprávnění Internetu zóny host domény aplikace.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] to provádí pomocí **Assert** metoda oprávnění. Následující kód ukazuje, jak to probíhá.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Assert** v podstatě brání neomezená oprávnění vyžadované [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] z jsou omezené na základě Internetu zóna oprávnění XBAP.  
  
 Z hlediska platformy [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] zodpovídá za použití **Assert** správně; kvůli nesprávnému použití **Assert** může povolit škodlivý kód ke zvýšení oprávnění. V důsledku toho je pak potřeba volat pouze **Assert** v případě potřeby, a zajistit, že izolovaného prostoru omezení zůstávají beze změn. Například otevřete náhodných souborů v izolovaném prostoru kód není povoleno, ale je povoleno ji používat. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Umožňuje v izolovaném prostoru aplikacím používat funkce písmo voláním **Assert**a pro [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] číst soubory, které jsou známé tak, aby obsahovala těchto písmo jménem aplikace v izolovaném prostoru.  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce – nasazení  
 [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] je komplexní nasazení technologie, která je součástí rozhraní .NET Framework a integruje se s [!INCLUDE[TLA#tla_visualstu](../../../includes/tlasharptla-visualstu-md.md)] (viz [ClickOnce zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment) podrobné informace). Samostatné [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace můžete nasadit s využitím [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)], zatímco aplikace hostované prohlížečem musí být nasazeny s [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)].  
  
 Aplikace nasazené pomocí [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)] jsou uvedeny další vrstvu zabezpečení [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]; v podstatě [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] nasazené aplikace požádat o oprávnění, která potřebují. Jsou poskytovány pouze ta oprávnění, pokud nepřekročí sadu oprávnění pro zónu, ze kterého je aplikace nasazená. Snížením sadu oprávnění pouze na ty, které jsou potřeba, i když jsou menší než uvedené poskytnuté aplikací zóny spouštěcí oprávnění nastavit, počet prostředků, že aplikace má přístup k je omezená na úplném. V důsledku toho pokud aplikace je zachycena, se snižuje potenciál pro poškození do klientského počítače.  
  
<a name="Security_Critical_Methodology"></a>   
### <a name="security-critical-methodology"></a>Metodologie kritické pro zabezpečení  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Kód, který používá oprávnění a povolit sandboxu zóny Internetu pro aplikace XBAP, který musí uchovávat na nejvyšší možné stupeň auditování zabezpečení a řízení. Pro usnadnění tohoto požadavku, rozhraní .NET Framework poskytuje novou podporu pro správu kód, který má oprávnění. Konkrétně [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] umožňuje identifikovat kód, který má oprávnění a označte ji pomocí <xref:System.Security.SecurityCriticalAttribute>; jakýkoli kód není označené <xref:System.Security.SecurityCriticalAttribute> stane *transparentní* použití této metody. Naopak spravovaného kódu, který není označen atributem <xref:System.Security.SecurityCriticalAttribute> je zabráněno zvyšování oprávnění.  
  
 Kritické pro zabezpečení metodologie umožňuje uspořádání [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kód, který má oprávnění do *kritické pro zabezpečení jádra*, pokračujte zbývajícími je transparentní. Izolace kritické pro zabezpečení kódu umožňuje [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] inženýrský tým zaměřit další bezpečnostní analýzy a zdrojový ovládací prvek na kritické pro zabezpečení jádra nenabízející postupy standard zabezpečení (viz [strategie zabezpečení WPF – Engineering zabezpečení](wpf-security-strategy-security-engineering.md)).  
  
 Všimněte si, že rozhraní .NET Framework umožňuje důvěryhodného kódu k rozšíření izolovaného prostoru zóny Internetu XBAP, který umožňuje vývojářům umožňuje psát spravovaná sestavení, které jsou označeny <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) a nasadili pro uživatele globální mezipaměti sestavení (GAC). Označení sestavení APTCA je operace vysoce citlivé a zabezpečení, protože povoluje libovolný kód k volání tohoto sestavení, včetně škodlivý kód z Internetu. Extrémně opatrní a osvědčené postupy a musí být při tomto postupu uživatele musíte se rozhodnout důvěřovat softwaru v pořadí, aby byl nainstalován.  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## <a name="microsoft-internet-explorer-security"></a>Microsoft Internet Explorer Security  
 Nad rámec omezení problémy se zabezpečením a zjednodušení konfigurace zabezpečení [!INCLUDE[TLA#tla_ie6sp2](../../../includes/tlasharptla-ie6sp2-md.md)] obsahuje několik funkcí, které zvyšují zabezpečení pro uživatele zlepšení zabezpečení [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]. Síla tyto funkce se pokusí povolit uživatelům větší kontrolu nad komfortem při jejich procházení.  
  
 Před verzí [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)], uživatele může být v souladu s některou z následujících akcí:  
  
- Náhodné zobrazována místní okna.  
  
- Přesměrování skript matoucí.  
  
- Mnoho dialogy zabezpečení v některé webové servery.  
  
 V některých případech se nedůvěryhodné weby mistranslation: přimět uživatele pomocí zfalšování instalace [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] nebo opakovaně zobrazení [!INCLUDE[TLA#tla_actx](../../../includes/tlasharptla-actx-md.md)] instalace dialogové okno, i když je zrušena uživatelem. Pomocí následujících postupů, je možné, že mají byla nalákaní velký počet uživatelů, rozhodování o nízký, z kterých vzniklo s instalací aplikace spyware.  
  
 [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] obsahuje několik funkcí pro zmírnění těchto typů problémů, které se točí kolem koncepce zahájení uživatelem. [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] rozpozná, pokud uživatel klikne na odkaz nebo stránky prvek před akci, která se označuje jako *zahájení uživatelem*a zpracovává jinak než při podobné akce místo toho aktivaci pomocí skriptu na stránce. Jako příklad [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] zahrnuje **blokování automaticky otevíraných oken** , který detekuje, když uživatel klikne na tlačítko před stránce vytvoření automaticky otevírané okno. Díky tomu [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] povolit automaticky otevíraná okna nejvíce neškodného zároveň je možné zabránit automaticky otevíraná okna, které uživatelé požádat o ani vhodné. Blokované automaticky otevíraná okna jsou zachycena v rámci nové **informační panel**, který umožňuje uživateli ručně přepsat blok a zobrazit automaticky otevírané okno.  
  
 Stejnou logiku zahájení uživatelem platí také pro **otevřít**/**Uložit** výzvy zabezpečení. [!INCLUDE[TLA2#tla_actx](../../../includes/tla2sharptla-actx-md.md)] dialogová okna instalace jsou vždy zachycena v informačním panelu pokud představují upgradu z dřív nainstalovaného ovládacího prvku. Tyto míry se dá uživatelům a bezpečnější více řízené uživatelské prostředí vzhledem k tomu, aby byla chráněná před weby, které obtěžování je nainstalovat nežádoucí software nebo škodlivý software.  
  
 Tyto funkce také zákazníkům, kteří používají ochranu [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] a přejděte do webové stránky, které zajistí, aby stáhněte a nainstalujte [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikací. Zejména je to proto [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] nabízí lepší výkon, která organizacím snižuje riziko pro uživatele k instalaci škodlivých aktivit nebo devious aplikací bez ohledu na to, jakou technologii byl použit k sestavení, včetně [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Přidá do tyto ochrany s použitím [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] k usnadnění stahování své aplikace přes Internet. Protože [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] spustit v sandboxu Internet zóny zabezpečení, může být spuštěn bez problémů. Na druhou stranu, samostatné [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace vyžadují úplný vztah důvěryhodnosti k provedení. V případě těchto aplikací [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] se zobrazí dialogové okno zabezpečení během procesu spuštění oznámit využívání vaší aplikace dodatečné požadavky na zabezpečení. Však to musí být uživatelem iniciované, se také řídí logiky iniciované uživatelem a může být zrušen.  
  
 [!INCLUDE[TLA2#tla_ie7](../../../includes/tla2sharptla-ie7-md.md)] zahrnuje a přesahuje možnosti zabezpečení [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] jako součást dlouhodobě zaměřuje na zabezpečení.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení přístupu kódu](../misc/code-access-security.md)
- [Zabezpečení](security-wpf.md)
- [Částečné zabezpečení důvěryhodnosti WPF](wpf-partial-trust-security.md)
- [Strategie zabezpečení WPF – engineering zabezpečení](wpf-security-strategy-security-engineering.md)
