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
ms.openlocfilehash: 44f98a6d7bf8358baf3b123b2d3b1d13009098a6
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133754"
---
# <a name="wpf-security-strategy---platform-security"></a>Strategie zabezpečení WPF – zabezpečení platformy
I když Windows Presentation Foundation (WPF) poskytuje celou řadu služeb zabezpečení, využívá také funkce zabezpečení základní platformy, která zahrnuje operační systém, modul CLR a Internet Explorer. Tyto vrstvy se kombinují a [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] poskytují silný a odolný model zabezpečení, který se pokusí vyhnout jakémukoli jedinému bodu selhání, jak je znázorněno na následujícím obrázku:  
  
 ![Diagram, který zobrazuje model zabezpečení WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 Zbývající část tohoto tématu se zabývá funkcemi v každé z těchto vrstev, které se týkají [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] konkrétně.  

<a name="Operating_System_Security"></a>   
## <a name="operating-system-security"></a>Zabezpečení operačního systému  
Jádro systému Windows poskytuje několik funkcí zabezpečení, které tvoří základ zabezpečení pro všechny aplikace systému Windows, včetně těch, které jsou vytvořeny pomocí WPF. Toto téma popisuje širokou škálu těchto funkcí zabezpečení, které jsou důležité pro WPF, a také způsob, jakým se WPF integruje s nimi za účelem zajištění další ochrany.  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Kromě obecného přezkoumání a posílení systému Windows existují tři klíčové funkce [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] , které se v tomto tématu podíváme na tyto položky:  
  
- Kompilace/GS  
  
- [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)].  
  
#### <a name="gs-compilation"></a>Kompilace/GS  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)]poskytuje ochranu tím, že znovu zkompiluje mnoho základních systémových knihoven, včetně všech [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] závislostí, jako je například CLR, které pomáhají zmírnit přetečení vyrovnávací paměti. Toho dosáhnete použitím parametru/GS s kompilátorem C/C++ Command-line. I když by se přetečení vyrovnávací paměti mělo výslovně vyhnout, kompilace/GS poskytuje příklad ochrany proti potenciálním ohrožením zabezpečení, která jsou neúmyslně nebo škodlivě vytvořená v nich.  
  
 V minulosti bylo přetečení vyrovnávací paměti příčinou mnoha vysoce ovlivněných zneužití zabezpečení. K přetečení vyrovnávací paměti dojde v případě, že útočník využívá chybu zabezpečení kódu, která umožňuje vkládání škodlivého kódu, který zapisuje za hranice vyrovnávací paměti. To pak umožňuje útočníkovi napadení procesu, ve kterém je kód spuštěn, přepsáním zpáteční adresy funkce, která způsobí spuštění kódu útočníka. Výsledkem je škodlivý kód, který spouští libovolný kód se stejnými oprávněními jako napadený proces.  
  
 Na vysoké úrovni příznak kompilátoru/GS chrání proti některým potenciálním přetečení vyrovnávací paměti vložením speciálního souboru cookie zabezpečení k ochraně zpáteční adresy funkce, která má místní vyrovnávací paměti řetězců. Po návratu funkce se soubor cookie zabezpečení porovná s předchozí hodnotou. Pokud se hodnota změnila, může dojít k přetečení vyrovnávací paměti a proces se zastavil s chybovou podmínkou. Zastavení procesu zabrání spuštění potenciálně škodlivého kódu. Další podrobnosti najdete v tématu [/GS (kontroly zabezpečení vyrovnávací paměti)](/cpp/build/reference/gs-buffer-security-check) .  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]je zkompilován s příznakem/GS pro přidání další vrstvy obrany do [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikací.  
  
#### <a name="microsoft-windows-update-enhancements"></a>Vylepšení Microsoft web Windows Update  
 [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)]byl také vylepšen [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] pro zjednodušení procesu stahování a instalace aktualizací. Tyto změny významně zvyšují zabezpečení pro [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] zákazníky tím, že pomáhají zajistit aktuálnost jejich systémů, zejména v souvislosti s aktualizacemi zabezpečení.  
  
<a name="Windows_Vista"></a>   
### <a name="windows-vista"></a>Windows Vista  
Uživatelé WPF v systému Windows Vista budou těžit z dalších vylepšení zabezpečení operačního systému, včetně přístupu uživatelů s minimálními oprávněními, kontroly integrity kódu a izolace oprávnění.  
  
#### <a name="user-account-control-uac"></a>Řízení uživatelských účtů (UAC)  
 V současné době se uživatelé systému Windows spouštějí s oprávněními správce, protože mnoho aplikací vyžaduje tyto požadavky buď k instalaci, nebo k provedení. Jedním z příkladů je možnost psát výchozí nastavení aplikace do registru.  
  
 Spuštění s oprávněními správce ve skutečnosti znamená, že aplikace se spouštějí z procesů, kterým jsou udělena oprávnění správce. Dopad tohoto zabezpečení je takový, že veškerý škodlivý kód, který by napadený procesem spuštěným s oprávněními správce, automaticky zdědí tato oprávnění, včetně přístupu k důležitým systémovým prostředkům.  
  
 Jedním ze způsobů, jak chránit před touto bezpečnostní hrozbou, je spouštění aplikací s minimálním množstvím oprávnění, která jsou vyžadována. Tato funkce se označuje jako princip nejnižších oprávnění a je základní funkcí operačního systému Windows. Tato funkce se nazývá řízení uživatelských účtů (UAC) a pomocí nástroje řízení uživatelských účtů (UAC) se používá v těchto dvou klíčových způsobech:  
  
- Spuštění většiny aplikací s oprávněními nástroje řízení uživatelských účtů ve výchozím nastavení, i když je uživatel správcem; s oprávněními správce budou spuštěny pouze aplikace, které potřebují oprávnění správce. Aby bylo možné spustit s oprávněními správce, aplikace musí být explicitně označeny buď v manifestu aplikace, nebo jako položka v zásadách zabezpečení.  
  
- Pro zajištění řešení kompatibility, jako je virtualizace. Mnoho aplikací se třeba pokouší zapisovat do umístění s omezeným přístupem, jako je C:\Program Files. Pro aplikace spuštěné v nástroji Řízení uživatelských účtů existuje alternativní umístění pro jednotlivé uživatele, které pro zápis do nástroje nevyžaduje oprávnění správce. Pro aplikace, které běží v nástroji Řízení uživatelských účtů, Nástroj UAC virtualizuje C:\Program Files, takže aplikace, které jsou zapsány do této služby, jsou ve skutečnosti zapsány do alternativního umístění pro jednotlivé uživatele. Tento druh práce s kompatibilitou umožňuje operačnímu systému spouštět mnoho aplikací, které se dřív nepodařilo spustit v nástroji Řízení uživatelských účtů.  
  
#### <a name="code-integrity-checks"></a>Kontroly integrity kódu  
 Systém Windows Vista zahrnuje hlubší kontroly integrity kódu, které zabraňují v vkládání škodlivého kódu do systémových souborů nebo do jádra za běhu za běhu. To překračuje ochranu systémových souborů.  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Proces omezených práv pro aplikace hostované v prohlížeči  
 Aplikace hostované [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] v prohlížeči se spouštějí v karanténě zóny Internet Zone. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]integrace s aplikací Microsoft Internet Explorer rozšiřuje tuto ochranu o další podporu.  
  
 Vzhledem [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] k tomu, že jsou obecně izolovaným prostorem sady oprávnění zóny Internet, odebrání těchto [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] oprávnění neškodí z hlediska kompatibility. Místo toho je vytvořena další vrstva důkladné obrany; Pokud aplikace izolovaného prostoru (sandbox) může zneužít jiné vrstvy a převzít proces, bude mít stále omezená oprávnění.  
  
 Viz [použití účtu uživatele](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29)s nejnižšími oprávněními.  
  
<a name="Common_Language_Runtime_Security"></a>   
## <a name="common-language-runtime-security"></a>Zabezpečení společného jazykového modulu runtime  
 Modul CLR (Common Language Runtime) nabízí řadu výhod zabezpečení klíčů, které zahrnují ověřování a ověřování, zabezpečení přístupu kódu (CAS) a kritickou metodologii zabezpečení.  
  
<a name="Validation_and_Verification"></a>   
### <a name="validation-and-verification"></a>Ověřování a ověřování  
 Pro zajištění izolace a integrity sestavení používá CLR proces ověřování. Ověřování CLR zajišťuje izolaci sestavení tím, že ověřuje jejich formát přenositelného spustitelného souboru (PE) pro adresy, které ukazují mimo sestavení. Ověřování CLR také ověřuje integritu metadat, která jsou vložena do sestavení.  
  
 Za účelem zajištění bezpečnosti typů, což umožňuje zabránit běžným problémům se zabezpečením (například přetečení vyrovnávací paměti) a povolit sandboxing prostřednictvím izolovaného procesu, zabezpečení CLR používá koncept ověřování.  
  
 Spravované aplikace jsou kompilovány do jazyka MSIL (Microsoft Intermediate Language). Když jsou spouštěny metody ve spravované aplikaci, je její jazyk MSIL zkompilován do nativního kódu prostřednictvím kompilace JIT (just-in-time). Kompilace JIT zahrnuje proces ověření, který se vztahuje na mnoho pravidel zabezpečení a odolnosti, které zajišťují, že kód:  
  
- Porušení kontraktů typu  
  
- Zavedení přetečení vyrovnávací paměti  
  
- Přístup k paměti je volně přístupný.  
  
 Spravovaný kód, který není v souladu s pravidly ověřování, není povoleno spustit, pokud se nepovažuje za důvěryhodný kód.  
  
 Výhodou ověřitelného kódu je klíčovým důvodem, proč [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] se sestavení na .NET Framework. V rozsahu, ve kterém se používá ověřitelný kód, se výrazně sníží možnost zneužití možných ohrožení zabezpečení.  
  
<a name="Code_Access_Security"></a>   
### <a name="code-access-security"></a>Zabezpečení přístupu kódu  
 Klientský počítač zveřejňuje širokou škálu prostředků, ke kterým může mít spravovaná aplikace přístup, včetně systému souborů, registru, tiskových služeb, uživatelského rozhraní, reflexe a proměnných prostředí. Aby mohla spravovaná aplikace přistupovat ke všem prostředkům v klientském počítači, musí mít .NET Framework oprávnění k tomu. Oprávnění v certifikačních autoritách je podtřídou <xref:System.Security.CodeAccessPermission>třídy; CAS implementuje jednu podtřídu pro každý prostředek, ke kterému mají přístup spravované aplikace.  
  
 Sada oprávnění, ke kterým je spravovaná aplikace udělována CAS při spuštění, se označuje jako sada oprávnění a je určena legitimací poskytovanou aplikací. Pro [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace jsou poskytnuté legitimace umístění nebo zóna, ze kterých se aplikace spouští. CAS identifikuje následující zóny:  
  
- **Tento počítač**. Aplikace spouštěné z klientského počítače (plně důvěryhodné).  
  
- **Místní intranet**. Aplikace spouštěné z intranetu. (Poněkud důvěryhodné).  
  
- **Internet**. Aplikace spouštěné z Internetu (Nejméně důvěryhodné).  
  
- **Důvěryhodné servery**. Aplikace identifikované uživatelem jako důvěryhodné (Nejméně důvěryhodné).  
  
- **Nedůvěryhodné lokality**. Aplikace identifikované uživatelem jako nedůvěryhodné. (Nedůvěryhodné).  
  
 Pro každou z těchto zón poskytuje CAS sadu předdefinovaných oprávnění, která zahrnuje oprávnění, která odpovídají úrovni důvěry přidružené k jednotlivým. Zde jsou některé z nich:  
  
- **FullTrust**. Pro aplikace spouštěné ze zóny **můj počítač** . Všechna možná oprávnění jsou udělena.  
  
- **LocalIntranet**. Pro aplikace spouštěné z **místní** zóny intranetu. K poskytnutí středního přístupu k prostředkům klientského počítače, včetně izolovaného úložiště, neomezeného přístupu k uživatelskému rozhraní, neomezených dialogových oken, omezených reflexe a omezeného přístupu k proměnným prostředí, je udělená podmnožina oprávnění. Nejsou k dispozici oprávnění pro kritické prostředky, jako je registr.  
  
- **Internet**. Pro aplikace spouštěné ze zóny **Internet** nebo **Důvěryhodné servery** . K poskytnutí omezeného přístupu k prostředkům klientského počítače, včetně izolovaného úložiště, jenom otevřeného souboru a omezeného uživatelského rozhraní, se udělí podmnožina oprávnění. V podstatě Tato sada oprávnění izoluje aplikace od klientského počítače.  
  
 Aplikacím identifikovaným jako nedůvěryhodné **servery** nejsou vůbec udělena oprávnění CAS. V důsledku toho pro ně neexistuje předdefinovaná sada oprávnění.  
  
 Následující obrázek znázorňuje vztah mezi zónami, sadami oprávnění, oprávněními a prostředky:  
  
 ![Diagram, který zobrazuje sady oprávnění CAS.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Omezení izolovaného prostoru zabezpečení zóny Internet Zone platí stejně jako jakýkoli kód, který XBAP importuje ze systémové knihovny, včetně [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Tím je zajištěno, že je každý bit kódu uzamčen, dokonce [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]i. Aby bylo možné spustit, aplikace XBAP potřebuje spustit funkci, která vyžaduje více oprávnění než ty, které jsou povoleny v izolovaném prostoru zabezpečení Internetové zóny.  
  
 Zvažte aplikaci XBAP, která obsahuje následující stránku:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Aby bylo možné spustit tuto funkci XBAP [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] , musí podkladový kód spustit více funkcí, než je k dispozici pro volání funkce XBAP, včetně:  
  
- Vytvoření popisovače okna (HWND) pro vykreslování  
  
- Odesílání zpráv  
  
- Načítání písma Tahoma  
  
 Z hlediska zabezpečení by byl umožněn přímý přístup k libovolné z těchto operací z aplikace v izolovaném prostoru (sandbox).  
  
 Naštěstí v [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] rámci této situace umožňuje, aby tyto operace byly spouštěny se zvýšenými oprávněními jménem aplikace v izolovaném prostoru (sandbox). I když [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] jsou všechny operace zkontrolovány proti omezeným oprávněním zabezpečení zóny Internet pro doménu aplikace XBAP ( [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] stejně jako ostatní systémové knihovny), je udělena sada oprávnění, která zahrnuje všechna možná oprávnění.
  
 To vyžaduje, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aby aplikace přijímala zvýšená oprávnění a zabránila tomu, aby se tato oprávnění řídila sadou oprávnění zóny Internet v doméně hostitelské aplikace.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]provede to pomocí metody **Assert** oprávnění. Následující kód ukazuje, jak se to stane.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Kontrolní** výraz v podstatě zabraňuje neomezeným oprávněním [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] , která vyžaduje omezení přístupu k internetové zóně pro XBAP.  
  
 Z perspektivy [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] platformy zodpovídá za správné použití **výrazu Assert** ; nesprávné použití **výrazu** by mohlo povolit zvýšení oprávnění pomocí škodlivého kódu. V důsledku toho je důležité volat pouze **Assert** v případě potřeby a zajistit, aby omezení izolovaného prostoru zůstala nedotčená. Například kód v izolovaném prostoru (sandbox) nesmí otevírat náhodné soubory, ale může používat písma. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]umožňuje aplikacím v izolovaném prostoru (sandbox) používatfunkce písma voláním [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Assert a pro čtení souborů známých jako tato písma jménem aplikace v izolovaném prostoru (sandbox).  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>ClickOnce – nasazení  
 ClickOnce je komplexní technologie nasazení, která je součástí .NET Framework a integruje se s [!INCLUDE[TLA#tla_visualstu](../../../includes/tlasharptla-visualstu-md.md)] (podrobné informace naleznete v tématu [zabezpečení a nasazení ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) ). Samostatné [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace lze nasadit pomocí technologie ClickOnce, zatímco aplikace hostované v prohlížeči musí být nasazeny s ClickOnce.  
  
 Aplikacím nasazeným pomocí technologie ClickOnce je poskytnuta další vrstva zabezpečení než zabezpečení přístupu kódu (CAS); v podstatě aplikace nasazené ClickOnce požaduje oprávnění, která potřebují. Jsou jim udělena pouze ta oprávnění, pokud nepřekročí sadu oprávnění pro zónu, ze které je aplikace nasazena. Omezením sady oprávnění jenom na ty, které jsou potřeba, i když jsou menší než ta, kterou poskytuje sada oprávnění pro spouštěcí zónu. počet prostředků, ke kterým má aplikace přístup, se zkracuje na minimum. V důsledku toho, pokud dojde k narušení aplikace, je možné omezit poškození klientského počítače.  
  
<a name="Security_Critical_Methodology"></a>   
### <a name="security-critical-methodology"></a>Metodika kritické pro zabezpečení  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] Kód, který používá oprávnění k povolení izolovaného prostoru Internet Zone pro aplikace XBAP, je nutné uchovávat v nejvyšší možné úrovni auditu zabezpečení a řízení. Pro usnadnění tohoto požadavku .NET Framework poskytuje novou podporu pro správu kódu, který zvyšuje oprávnění. Konkrétně modul CLR umožňuje identifikovat kód, který zvyšuje oprávnění a označí ho <xref:System.Security.SecurityCriticalAttribute>pomocí; jakýkoliv kód, který není <xref:System.Security.SecurityCriticalAttribute> označen jako, je *transparentní* pomocí této metodologie. Naopak spravovaný kód, který není označen příznakem, <xref:System.Security.SecurityCriticalAttribute> brání v oprávnění ke zvýšení oprávnění.  
  
 Metodologie pro kritické zabezpečení umožňuje organizaci [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] kódu, která zvyšuje oprávnění na *jádro kritické pro zabezpečení*a zbytek je transparentní. Izolování kódu, který je kritický pro zabezpečení [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] , umožňuje technickému týmu soustředit se na další analýzu zabezpečení a správu zdrojů v jádru kritickém pro zabezpečení nad rámec standardních postupů zabezpečení (viz [strategie zabezpečení WPF – zabezpečení Inženýr](wpf-security-strategy-security-engineering.md)).  
  
 Všimněte si, že .NET Framework povoluje, aby důvěryhodný kód rozšířil rozhraní karantény Internet Zone pro XBAP tím, že umožňuje vývojářům <xref:System.Security.AllowPartiallyTrustedCallersAttribute> psát spravovaná sestavení označená pomocí (APTCA) a nasazená do globální mezipaměti sestavení (GAC) uživatele. Označení sestavení pomocí APTCA je vysoce citlivá operace zabezpečení, protože umožňuje jakémukoli volání tohoto sestavení, včetně škodlivého kódu z Internetu. Při tomto postupu se musí použít extrémní opatrnost a osvědčené postupy. aby se uživatelé museli nainstalovat, musí si vybrat, aby tento software důvěřoval.  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## <a name="microsoft-internet-explorer-security"></a>Microsoft Internet Explorer Security  
 Kromě snížení zabezpečení a zjednodušení konfigurace zabezpečení Microsoft Internet Explorer 6 (SP2) obsahuje několik funkcí, které vylepšení zabezpečení zvyšují zabezpečení pro uživatele [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]. Pohyb těchto funkcí se snaží uživatelům větší kontrolu nad jejich možností procházení.  
  
 Před IE6 SP2 můžou uživatelé podléhat některé z následujících možností:  
  
- Náhodně otevíraná okna.  
  
- Matoucí přesměrování skriptu.  
  
- Řada dialogů zabezpečení na některých webech.  
  
 V některých případech by nedůvěryhodné weby se pokusily uživatele přimět k falšování instalace [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] nebo opakovanému zobrazení dialogového okna pro instalaci Microsoft ActiveX, i když ho uživatel mohl zrušit. Pomocí těchto postupů je možné, že velký počet uživatelů byl napadený, což vede k nedostatečným rozhodováním, což vedlo k instalaci spywarových aplikací.  
  
 IE6 SP2 obsahuje několik funkcí, které pomáhají zmírnit tyto typy problémů, které se týkají konceptu zahájení spouštění uživatelů. IE6 SP2 detekuje, kdy uživatel klikl na odkaz nebo element stránky před akcí, která se označuje jako *iniciace uživatele*, a považuje ji za odlišnou od toho, že skript na stránce aktivuje podobnou akci. Příklad: IE6 SP2 zahrnuje **blokování automaticky otevíraných oken** , které detekuje, když uživatel klikne na tlačítko před stránkou, která vytváří automaticky otevírané okno. To umožňuje, aby aplikace IE6 SP2 povolovala většinu automaticky otevíraných oken neškodného a současně zabránila automaticky otevíraná okna, která se uživatelům nedotazují ani nechtějí. Blokovaná automaticky otevíraná okna jsou zachycena v novém **informačním panelu**, který uživateli umožňuje ručně přepsat blok a zobrazit automaticky otevírané okno.  
  
 Pro **otevření**/**Uložit** výzvy zabezpečení se použije také stejná logika pro zahájení uživatelem. Dialogová okna pro instalaci ActiveX jsou v informačním pruhu vždy zachycena, pokud nepředstavuje upgrade z dříve nainstalovaného ovládacího prvku. Tyto míry se kombinují, aby uživatelům poskytovaly bezpečnější a lépe řízené uživatelské prostředí, protože jsou chráněné před lokalitami, které jim umožňují nainstalovat nežádoucí nebo škodlivý software.  
  
 Tyto funkce také chrání zákazníky, kteří používají aplikaci IE6 SP2 k procházení webů, které jim umožňují stahovat a instalovat [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace. To je důležité kvůli tomu, že aplikace IE6 SP2 nabízí lepší uživatelské prostředí, které uživatelům omezuje možnost instalovat škodlivé nebo Devious aplikace bez ohledu na to, jaká technologie se použila k jejich [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]sestavování, včetně. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]Přidá se k těmto ochranám pomocí ClickOnce, aby se usnadnilo stahování svých aplikací přes Internet. Vzhledem [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] k tomu, že se spustí v izolovaném prostoru zabezpečení zóny Internetu, můžou se snadno spustit. Na druhé straně samostatné [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplikace vyžadují úplný vztah důvěryhodnosti pro spuštění. Pro tyto aplikace ClickOnce zobrazí dialogové okno zabezpečení během procesu spuštění, aby upozornilo na použití dalších požadavků na zabezpečení aplikace. To ale musí být iniciované uživatelem, bude se řídit také logikou iniciované uživatelem a můžete ho zrušit.  
  
 Internet Explorer 7 zahrnuje a rozšiřuje možnosti zabezpečení aplikace IE6 SP2 jako součást trvalého závazku na zabezpečení.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení přístupu kódu](../misc/code-access-security.md)
- [Zabezpečení](security-wpf.md)
- [Částečné zabezpečení důvěryhodnosti WPF](wpf-partial-trust-security.md)
- [Strategie zabezpečení WPF – engineering zabezpečení](wpf-security-strategy-security-engineering.md)
