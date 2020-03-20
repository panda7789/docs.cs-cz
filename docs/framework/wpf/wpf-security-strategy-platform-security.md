---
title: Strategie zabezpečení platformy
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
ms.openlocfilehash: 258fcd7c51ea59de03fe60a4eeb9a82dd1c7efca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174599"
---
# <a name="wpf-security-strategy---platform-security"></a>Strategie zabezpečení WPF – zabezpečení platformy
Zatímco Windows Presentation Foundation (WPF) poskytuje celou řadu služeb zabezpečení, ale také využívá funkce zabezpečení základní platformy, která zahrnuje operační systém, CLR a Internet Explorer. Tyto vrstvy se kombinují, aby wpf silný, obrana-in-hloubkový model zabezpečení, který se pokusí vyhnout se jedinému bodu selhání, jak je znázorněno na následujícím obrázku:  
  
 ![Diagram, který ukazuje model zabezpečení WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 Zbývající část tohoto tématu popisuje funkce v každé z těchto vrstev, které se konkrétně připomíjejí wpf.  

## <a name="operating-system-security"></a>Zabezpečení operačního systému  
Jádro systému Windows poskytuje několik funkcí zabezpečení, které tvoří základ zabezpečení pro všechny aplikace systému Windows, včetně těch, které jsou vytvořeny pomocí wpf. Toto téma popisuje šíři těchto funkcí zabezpečení, které jsou důležité pro WPF, stejně jako jak WPF integruje s nimi poskytnout další obranu do hloubky.  
  
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Kromě obecného přehledu a posílení systému Windows existují tři klíčové funkce z aktualizace Windows XP SP2, které budeme diskutovat v tomto tématu:  
  
- /GS kompilace  
  
- Microsoft Windows Update.  
  
#### <a name="gs-compilation"></a>Kompilace /GS  
 Aktualizace Windows XP SP2 poskytuje ochranu tím, že rekompilace mnoho základních systémových knihoven, včetně všech wpf závislostí, jako je například CLR, pomoci zmírnit přetečení vyrovnávací paměti. Toho je dosaženo pomocí parametru /GS s kompilátorem příkazového řádku C/C++. Přestože přetečení vyrovnávací paměti by mělo být explicitně zabráněno, /GS kompilace poskytuje příklad ochrany do hloubky proti potenciální chyby zabezpečení, které jsou neúmyslně nebo zlomyslně vytvořené jimi.  
  
 V minulosti byly přetečení vyrovnávací paměti příčinou mnoha zneužití zabezpečení s velkým dopadem. K přetečení vyrovnávací paměti dochází, když útočník využije chybu zabezpečení kódu, která umožňuje vložení škodlivého kódu, který zapíše za hranice vyrovnávací paměti. To pak umožňuje útočníkovi unést proces, ve kterém je kód spuštěn přepsáním zpáteční adresu funkce způsobit spuštění kódu útočníka. Výsledkem je škodlivý kód, který provádí libovolný kód se stejnými oprávněními jako neunesený proces.  
  
 Na vysoké úrovni příznak kompilátoru -GS chrání před některými potenciálními přetečeními vyrovnávací paměti vložením speciálního souboru cookie zabezpečení k ochraně zpáteční adresy funkce, která má místní vyrovnávací paměti řetězce. Po vrácení funkce je soubor cookie zabezpečení porovnán s předchozí hodnotou. Pokud se hodnota změnila, může dojít k přetečení vyrovnávací paměti a proces je zastaven s chybovým stavem. Zastavení procesu zabrání spuštění potenciálně škodlivého kódu. Viz [-GS (Buffer Security Check)](/cpp/build/reference/gs-buffer-security-check) pro více informací.  
  
 WPF je kompilován s příznakem /GS přidat další vrstvu obrany wpf aplikací.  
  
### <a name="windows-vista"></a>Windows Vista  
Uživatelé WPF v systému Windows Vista budou mít prospěch z dalších vylepšení zabezpečení operačního systému, včetně "Přístupu uživatelů s nejnižšími oprávněními", kontrol integrity kódu a izolace oprávnění.  
  
#### <a name="user-account-control-uac"></a>Řízení uživatelských účtů  
 Dnes mají uživatelé systému Windows tendenci spouštět s oprávněními správce, protože mnoho aplikací je vyžaduje pro instalaci nebo spuštění nebo obojí. Jedním z příkladů je možnost zapsat do registru výchozí nastavení aplikace.  
  
 Spuštění s oprávněními správce skutečně znamená, že aplikace se spouštějí z procesů, kterým jsou udělena oprávnění správce. Dopad na zabezpečení je, že jakýkoli škodlivý kód, který unese proces spuštěný s oprávněními správce, automaticky zdědí tato oprávnění, včetně přístupu ke kritickým systémovým prostředkům.  
  
 Jedním ze způsobů ochrany před touto hrozbou zabezpečení je spouštění aplikací s nejmenším množstvím požadovaných oprávnění. To to je známé jako princip nejmenší oprávnění a je základní funkcí operačního systému Windows. Tato funkce se nazývá Řízení uživatelských účtů (UAC) a používá se systémem Windows UAC dvěma klíčovými způsoby:  
  
- Chcete-li ve výchozím nastavení spouštět většinu aplikací s oprávněními skupiny Řízení uživatelských účtů, a to i v případě, že je uživatel správcem. S oprávněními správce budou spuštěny pouze aplikace, které potřebují oprávnění správce. Chcete-li spustit s oprávněními správce, musí být aplikace explicitně označeny v manifestu aplikace nebo jako položka v zásadách zabezpečení.  
  
- Poskytování řešení kompatibility, jako je virtualizace. Mnoho aplikací se například pokouší zapisovat do omezených umístění, jako je C:\Program Files. Pro aplikace prováděné v rámci nástroj Řízení uživatelských účtů existuje alternativní umístění pro jednotlivé uživatele, které nevyžaduje oprávnění správce k zápisu. Pro aplikace spuštěné pod nástroj Řízení uživatelských počítačů nástroj Řízení uživatelských počítačů virtualizuje c:\programové soubory tak, aby aplikace, které si myslí, že do ní zapisují, ve skutečnosti zapisují do alternativního umístění pro jednotlivé uživatele. Tento druh kompatibility práce umožňuje operačnímu systému spustit mnoho aplikací, které nemohly dříve spustit v nástroji Řízení řízení o řízení.  
  
#### <a name="code-integrity-checks"></a>Kontroly integrity kódu  
 Systém Windows Vista zahrnuje hlubší kontroly integrity kódu, aby se zabránilo vložení škodlivého kódu do systémových souborů nebo do jádra při načtení/spuštění. To přesahuje ochranu systémových souborů.  

### <a name="limited-rights-process-for-browser-hosted-applications"></a>Proces omezených práv pro aplikace hostované v prohlížeči  
 Aplikace WPF hostované v prohlížeči jsou spouštěny v izolovaném prostoru zóny Internet. Integrace WPF s aplikací Microsoft Internet Explorer rozšiřuje tuto ochranu o další podporu.  
  
 Vzhledem k tomu, že aplikace prohlížeče XAML (XBAPs) jsou obvykle v izolovaném prostoru sadou oprávnění zóny Internet, odebrání těchto oprávnění nepoškozuje aplikace prohlížeče XAML (XBAPs) z hlediska kompatibility. Místo toho je vytvořena další vrstva hloubkové ochrany; Pokud aplikace v izolovaném prostoru je schopen zneužít jiné vrstvy a unést proces, proces bude mít stále pouze omezená oprávnění.  
  
 Viz [Použití nejméně privilegovaného uživatelského účtu](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
## <a name="common-language-runtime-security"></a>Společné jazykové runtime zabezpečení  
 Clr (Common Language runtime) nabízí řadu klíčových výhod zabezpečení, které zahrnují ověření a ověření, zabezpečení přístupu ke kódu (CAS) a metodiku kritické pro zabezpečení.  

### <a name="validation-and-verification"></a>Ověření a ověření  
 Chcete-li poskytnout izolaci sestavení a integritu, CLR používá proces ověření. Ověření CLR zajišťuje, že sestavení jsou izolovány ověřením jejich portable spustitelný (PE) formát souboru pro adresy, které odkazují mimo sestavení. Ověření CLR také ověřuje integritu metadat, která je vložena do sestavení.  
  
 Chcete-li zajistit bezpečnost typů, pomoci zabránit běžným problémům se zabezpečením (např. přetečení vyrovnávací paměti) a umožnit zabalení do sandboxingu prostřednictvím izolace dílčího procesu, používá zabezpečení CLR koncept ověření.  
  
 Spravované aplikace jsou kompilovány do microsoft intermediate jazyka (MSIL). Při spuštění metod ve spravované aplikaci je jeho MSIL zkompilován do nativního kódu prostřednictvím kompilace Just-In-Time (JIT). Kompilace JIT zahrnuje ověřovací proces, který používá mnoho pravidel bezpečnosti a robustnosti, která zajišťují, že kód není:  
  
- Porušovat typové smlouvy  
  
- Zavedení přetečení vyrovnávací paměti  
  
- Divoce přístup k paměti.  
  
 Spravovaný kód, který neodpovídá ověřovacím pravidlům, není povolen, pokud není považován za důvěryhodný kód.  
  
 Výhodou ověřitelného kódu je klíčový důvod, proč WPF staví na rozhraní .NET Framework. Do té míry, že je použit ověřitelný kód, je možnost zneužití možných chyb zabezpečení výrazně snížena.  
  
### <a name="code-access-security"></a>Zabezpečení přístupu kódu  
 Klientský počítač zveřejňuje širokou škálu prostředků, ke kterým může mít spravovaná aplikace přístup, včetně systému souborů, registru, tiskových služeb, uživatelského rozhraní, reflexe a proměnných prostředí. Předtím, než spravovaná aplikace může přistupovat k některému z prostředků v klientském počítači, musí mít oprávnění rozhraní .NET Framework. Oprávnění v CAS je podtřída <xref:System.Security.CodeAccessPermission>; CAS implementuje jednu podtřídu pro každý prostředek, ke kterému mají spravované aplikace přístup.  
  
 Sada oprávnění, která je spravovaná aplikace udělena CAS při spuštění provádění se označuje jako sada oprávnění a je určena důkazy poskytnuté aplikací. Pro aplikace WPF je k dispozici důkaz umístění nebo zóny, ze kterého jsou spuštěny aplikace. CAS identifikuje následující zóny:  
  
- **Tento počítač**. Aplikace spuštěné z klientského počítače (plně důvěryhodné).  
  
- **Místní intranet**. Aplikace spuštěné z intranetu. (Poněkud důvěryhodný).  
  
- **Internet**. Aplikace spuštěné z internetu. (Nejméně důvěryhodné).  
  
- **Důvěryhodné servery**. Aplikace identifikované uživatelem jako důvěryhodné. (Nejméně důvěryhodné).  
  
- **Nedůvěryhodné weby**. Aplikace identifikované uživatelem jako nedůvěryhodné. (Nedůvěryhodný).  
  
 Pro každou z těchto zón cas poskytuje předdefinovanou sadu oprávnění, která obsahuje oprávnění, která odpovídá úrovni důvěryhodnosti spojené s každou z nich. Mezi ně patří:  
  
- **FullTrust**. Pro aplikace spuštěné ze zóny **Tento počítač.** Všechna možná oprávnění jsou udělena.  
  
- **LocalIntranet**. Pro aplikace spuštěné ze zóny **Místní intranet.** Podmnožina oprávnění jsou udělena k poskytování mírný přístup k prostředkům klientského počítače, včetně izolované úložiště, neomezený přístup k umělá úprava, neomezená dialogová okna souborů, omezený odraz, omezený přístup k proměnným prostředí. Oprávnění pro kritické prostředky, jako je registr nejsou k dispozici.  
  
- **Internet**. Pro aplikace spuštěné ze zóny **Internet** nebo **Důvěryhodné servery.** Podmnožina oprávnění jsou udělena poskytuje omezený přístup k prostředkům klientského počítače, včetně izolované úložiště, soubor otevřít pouze a omezené uI. Tato sada oprávnění v podstatě izoluje aplikace z klientského počítače.  
  
 Aplikace označené jako aplikace ze zóny **Nedůvěryhodné servery** neudělují cas žádná oprávnění. V důsledku toho pro ně neexistuje předdefinovaná sada oprávnění.  
  
 Následující obrázek znázorňuje vztah mezi zónami, sadami oprávnění, oprávněními a prostředky:  
  
 ![Diagram, který zobrazuje sady oprávnění CAS.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Omezení izolovaného prostoru zabezpečení zóny Internet platí stejně pro jakýkoli kód, který xbap importuje ze systémové knihovny, včetně WPF. Tím je zajištěno, že každý bit kódu je uzamčen, a to i WPF. Bohužel, aby bylo možné spustit, XBAP musí spustit funkce, které vyžaduje více oprávnění, než jsou povoleny v izolovaném prostoru zabezpečení zóny Internet.  
  
 Zvažte aplikaci XBAP, která obsahuje následující stránku:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Chcete-li spustit tento XBAP, základní kód WPF musí spustit více funkcí, než je k dispozici pro volající XBAP, včetně:  
  
- Vytvoření popisovače okna (HWND) pro vykreslování  
  
- Odesílání zpráv  
  
- Načítání písma Tahoma  
  
 Z hlediska zabezpečení by povolení přímého přístupu k některé z těchto operací z aplikace v izolovaném prostoru bylo katastrofální.  
  
 Naštěstí WPF zajišťuje tuto situaci tím, že umožňuje tyto operace provádět se zvýšenými oprávněními jménem aplikace v izolovaném prostoru. Zatímco všechny operace WPF jsou kontrolovány podle omezených oprávnění zabezpečení zóny Internetu v aplikační doméně XBAP, WPF (stejně jako u jiných systémových knihoven) je udělena sada oprávnění, která obsahuje všechna možná oprávnění.
  
 To vyžaduje, aby wpf obdrží zvýšená oprávnění a zároveň zabránit tato oprávnění řídí zóny Internet sada oprávnění domény hostitelské aplikace.  
  
 WPF to provádí pomocí **Assert** metoda oprávnění. Následující kód ukazuje, jak k tomu dochází.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Assert** v podstatě zabraňuje omezení oprávnění vyžadovaná WPF z omezení oprávnění zóny Internetu XBAP.  
  
 Z hlediska platformy WPF je zodpovědný za správné použití **Assert;** nesprávné použití **Assert** může umožnit škodlivý kód ke zvýšení oprávnění. V důsledku toho je důležité volat pouze **Assert** v případě potřeby a zajistit, aby omezení izolovaného prostoru zůstávají beze změny. Například kód v izolovaném prostoru není povoleno otevírat náhodné soubory, ale je povoleno používat písma. WPF umožňuje aplikacím v izolovaném prostoru používat funkci písma voláním **Assert**a wpf číst soubory, o kterých je známo, že obsahují tato písma jménem aplikace v izolovaném prostoru.  
  
### <a name="clickonce-deployment"></a>Nasazení clickonce  
 ClickOnce je komplexní technologie nasazení, která je součástí rozhraní .NET Framework a integruje se s Visual Studio (viz [ClickOnce zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment) pro podrobné informace). Samostatné wpf aplikace lze nasadit pomocí ClickOnce, zatímco aplikace hostované prohlížečem musí být nasazeny s ClickOnce.  
  
 Aplikace nasazené pomocí ClickOnce jsou uvedeny další vrstvu zabezpečení přes zabezpečení přístupu kódu (CAS); V podstatě ClickOnce nasazené aplikace vyžadují oprávnění, která potřebují. Jsou jim udělena pouze tato oprávnění, pokud nepřekročí sadu oprávnění pro zónu, ze které je aplikace nasazena. Snížením sadu oprávnění pouze ty, které jsou potřeba, i v případě, že jsou menší než ty, které poskytuje sada oprávnění spouštěcí zóny, počet prostředků, které má aplikace přístup je snížena na minimum. V důsledku toho, pokud je aplikace unesena, je snížena možnost poškození klientského počítače.  
  
### <a name="security-critical-methodology"></a>Kritická metodika  
 Kód WPF, který používá oprávnění k povolení izolovaného prostoru zóny Internet pro aplikace XBAP, musí být držen na nejvyšší možný stupeň auditu a kontroly zabezpečení. Pro usnadnění tohoto požadavku poskytuje rozhraní .NET Framework novou podporu pro správu kódu, který zvyšuje oprávnění. Konkrétně CLR umožňuje identifikovat kód, který zvyšuje oprávnění a <xref:System.Security.SecurityCriticalAttribute>označit ji ; jakýkoli kód, <xref:System.Security.SecurityCriticalAttribute> který není označen, se pomocí této metodiky stane *průhledným.* Naopak spravovaného kódu, který <xref:System.Security.SecurityCriticalAttribute> není označen, je zabráněno zvýšení oprávnění.  
  
 Kritická metodika zabezpečení umožňuje organizaci kódu WPF, který zvyšuje oprávnění na *jádro kritické pro zabezpečení*, přičemž zbytek je transparentní. Izolace kódu kritického pro zabezpečení umožňuje technickému týmu WPF zaměřit další analýzu zabezpečení a správě zdrojů na jádro kritické pro zabezpečení nad rámec standardních postupů zabezpečení (viz [WPF Security Strategy - Security Engineering](wpf-security-strategy-security-engineering.md)).  
  
 Všimněte si, že rozhraní .NET Framework umožňuje důvěryhodnému kódu rozšířit oblast působnosti zóny Internetu <xref:System.Security.AllowPartiallyTrustedCallersAttribute> XBAP tím, že umožňuje vývojářům psát spravovaná sestavení, která jsou označena (APTCA) a nasazena do globální mezipaměti sestavení uživatele (GAC). Označení sestavení pomocí APTCA je vysoce citlivá operace zabezpečení, protože umožňuje jakýkoli kód volat toto sestavení, včetně škodlivého kódu z Internetu. Při této práci je třeba použít mimořádnou opatrnost a osvědčené postupy a uživatelé se musí rozhodnout důvěřovat tomuto softwaru, aby mohl být nainstalován.  
  
## <a name="microsoft-internet-explorer-security"></a>Zabezpečení aplikace Microsoft Internet Explorer  
 Kromě snížení problémů se zabezpečením a zjednodušení konfigurace zabezpečení obsahuje aplikace Microsoft Internet Explorer 6 (SP2) několik funkcí, které zlepšují zabezpečení uživatelů aplikací prohlížeče XAML (XBAPs). Tah těchto funkcí se snaží umožnit uživatelům větší kontrolu nad jejich prohlížení.  
  
 Před iE6 SP2, uživatelé mohou být předmětem některého z následujících:  
  
- Náhodná vyskakovací okna.  
  
- Matoucí přesměrování skriptu.  
  
- Na některých webech je dialogová okna mnoha zabezpečení.  
  
 V některých případech by se nedůvěryhodné weby pokusily [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] oklamat uživatele falšováním instalace nebo opakovaným zobrazením dialogového okna instalace Microsoft ActiveX, i když jej uživatel pravděpodobně zrušil. Pomocí těchto technik, je možné, že značný počet uživatelů byly podvedeni do dělat špatná rozhodnutí, která vyústila s instalací spyware aplikací.  
  
 Aktualizace IE6 SP2 obsahuje několik funkcí ke zmírnění těchto typů problémů, které se točí kolem konceptu iniciace uživatele. Aktualizace IE6 SP2 zjistí, kdy uživatel před akcí klepne na odkaz nebo prvek stránky, který je označován jako *iniciace uživatele*, a zachází s ní jinak, než když je podobná akce místo toho spuštěna skriptem na stránce. Jako příklad obsahuje aktualizace IE6 SP2 blokování automaticky **otevíraných pan-up,** které zjistí, kdy uživatel klepne na tlačítko před vytvořením automaticky otevíraného panelu. To umožňuje iE6 SP2 povolit většinu neškodné automaticky otevíraná období a zároveň zabránit automaticky otevíraná období, která uživatelé ani požádat ani chtít. Blokovaná automaticky otevíraná okna jsou zachycena pod novým **informačním panelem**, který umožňuje uživateli ručně přepsat blok a zobrazit automaticky otevírané okno.  
  
 Stejná logika inicializace uživatele se používá také pro výzvy zabezpečení **Open**/**Save.** Dialogová okna instalace ActiveX jsou vždy zachycena pod informačním panelem, pokud nepředstavují upgrade z dříve nainstalovaného ovládacího prvku. Tato opatření se kombinují, aby uživatelům poskytla bezpečnější a kontrolovanější uživatelské prostředí, protože jsou chráněni před weby, které je obtěžují instalovat nežádoucí nebo škodlivý software.  
  
 Tyto funkce také chrání zákazníky, kteří používají aktualizaci IE6 SP2 k procházení webů, které jim umožňují stahovat a instalovat aplikace WPF. Zejména je to proto, že iE6 SP2 nabízí lepší uživatelské prostředí, které snižuje možnost pro uživatele k instalaci škodlivých nebo nevyzpytatelné aplikace bez ohledu na to, co technologie byla použita k jeho sestavení, včetně WPF. WPF přidává k těmto ochranám pomocí ClickOnce pro usnadnění stahování svých aplikací přes Internet. Vzhledem k tomu, že aplikace prohlížeče XAML (XBAPs) se spouštějí v izolovaném prostoru zabezpečení zóny Internet, lze je bez problémů spustit. Na druhou stranu samostatné wpf aplikace vyžadují úplné důvěryhodnosti ke spuštění. U těchto aplikací clickonce zobrazí dialogové okno zabezpečení během procesu spuštění upozornit použití další požadavky na zabezpečení aplikace. To však musí být iniciováno uživatelem, bude se také řídit logikou iniciotou uživatele a může být zrušeno.  
  
 Aplikace Internet Explorer 7 zahrnuje a rozšiřuje možnosti zabezpečení aktualizace IE6 SP2 jako součást trvalého závazku k zabezpečení.  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení přístupu kódu](../misc/code-access-security.md)
- [Zabezpečení](security-wpf.md)
- [WPF částečné zabezpečení důvěryhodnosti](wpf-partial-trust-security.md)
- [Strategie zabezpečení WPF – engineering zabezpečení](wpf-security-strategy-security-engineering.md)
