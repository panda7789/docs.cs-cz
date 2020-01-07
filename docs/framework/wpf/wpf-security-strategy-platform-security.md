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
ms.openlocfilehash: b2fd923de165c0926e6f812764c71127b7c27691
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636234"
---
# <a name="wpf-security-strategy---platform-security"></a>Strategie zabezpečení WPF – zabezpečení platformy
I když Windows Presentation Foundation (WPF) poskytuje celou řadu služeb zabezpečení, využívá také funkce zabezpečení základní platformy, která zahrnuje operační systém, modul CLR a Internet Explorer. Tyto vrstvy se kombinují tak, aby poskytovaly vysoce zabezpečený model zabezpečení s vysokou ochranou, který se pokusí vyhnout jakémukoli jedinému bodu selhání, jak je znázorněno na následujícím obrázku:  
  
 ![Diagram, který zobrazuje model zabezpečení WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 Zbývající část tohoto tématu se zabývá funkcemi v každé z těchto vrstev, které se konkrétně týkají WPF.  

## <a name="operating-system-security"></a>Zabezpečení operačního systému  
Jádro systému Windows poskytuje několik funkcí zabezpečení, které tvoří základ zabezpečení pro všechny aplikace systému Windows, včetně těch, které jsou vytvořeny pomocí WPF. Toto téma popisuje širokou škálu těchto funkcí zabezpečení, které jsou důležité pro WPF, a také způsob, jakým se WPF integruje s nimi za účelem zajištění další ochrany.  
  
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>Microsoft Windows XP Service Pack 2 (SP2)  
 Kromě obecného přezkoumání a posílení systému Windows jsou k dispozici tři klíčové funkce [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)], které probereme v tomto tématu:  
  
- Kompilace/GS  
  
- Microsoft web Windows Update.  
  
#### <a name="gs-compilation"></a>Kompilace/GS  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] poskytuje ochranu tím, že znovu zkompiluje mnoho základních systémových knihoven, včetně všech závislostí WPF, jako je například CLR, které pomáhají zmírnit přetečení vyrovnávací paměti. Toho dosáhnete použitím parametru/GS s kompilátorem C/C++ Command-line. I když by se přetečení vyrovnávací paměti mělo výslovně vyhnout, kompilace/GS poskytuje příklad ochrany proti potenciálním ohrožením zabezpečení, která jsou neúmyslně nebo škodlivě vytvořená v nich.  
  
 V minulosti bylo přetečení vyrovnávací paměti příčinou mnoha vysoce ovlivněných zneužití zabezpečení. K přetečení vyrovnávací paměti dojde v případě, že útočník využívá chybu zabezpečení kódu, která umožňuje vkládání škodlivého kódu, který zapisuje za hranice vyrovnávací paměti. To pak umožňuje útočníkovi napadení procesu, ve kterém je kód spuštěn, přepsáním zpáteční adresy funkce, která způsobí spuštění kódu útočníka. Výsledkem je škodlivý kód, který spouští libovolný kód se stejnými oprávněními jako napadený proces.  
  
 Příznak kompilátoru-GS na vysoké úrovni chrání před některými potenciálními přetečeními vyrovnávací paměti vložením speciálního souboru cookie zabezpečení, který chrání zpáteční adresu funkce s místními vyrovnávacími paměťmi řetězců. Po návratu funkce se soubor cookie zabezpečení porovná s předchozí hodnotou. Pokud se hodnota změnila, může dojít k přetečení vyrovnávací paměti a proces se zastavil s chybovou podmínkou. Zastavení procesu zabrání spuštění potenciálně škodlivého kódu. Další podrobnosti najdete v tématu [-GS (kontrolní seznam zabezpečení vyrovnávací paměti)](/cpp/build/reference/gs-buffer-security-check) .  
  
 WPF je kompilována s příznakem/GS, aby bylo možné přidat další vrstvu obrany pro aplikace WPF.  
  
### <a name="windows-vista"></a>Windows Vista  
Uživatelé WPF v systému Windows Vista budou těžit z dalších vylepšení zabezpečení operačního systému, včetně přístupu uživatelů s minimálními oprávněními, kontroly integrity kódu a izolace oprávnění.  
  
#### <a name="user-account-control-uac"></a>Řízení uživatelských účtů  
 V současné době se uživatelé systému Windows spouštějí s oprávněními správce, protože mnoho aplikací vyžaduje tyto požadavky buď k instalaci, nebo k provedení. Jedním z příkladů je možnost psát výchozí nastavení aplikace do registru.  
  
 Spuštění s oprávněními správce ve skutečnosti znamená, že aplikace se spouštějí z procesů, kterým jsou udělena oprávnění správce. Dopad tohoto zabezpečení je takový, že veškerý škodlivý kód, který by napadený procesem spuštěným s oprávněními správce, automaticky zdědí tato oprávnění, včetně přístupu k důležitým systémovým prostředkům.  
  
 Jedním ze způsobů, jak chránit před touto bezpečnostní hrozbou, je spouštění aplikací s minimálním množstvím oprávnění, která jsou vyžadována. Tato funkce se označuje jako princip nejnižších oprávnění a je základní funkcí operačního systému Windows. Tato funkce se nazývá řízení uživatelských účtů (UAC) a pomocí nástroje řízení uživatelských účtů (UAC) se používá v těchto dvou klíčových způsobech:  
  
- Spuštění většiny aplikací s oprávněními nástroje řízení uživatelských účtů ve výchozím nastavení, i když je uživatel správcem; s oprávněními správce budou spuštěny pouze aplikace, které potřebují oprávnění správce. Aby bylo možné spustit s oprávněními správce, aplikace musí být explicitně označeny buď v manifestu aplikace, nebo jako položka v zásadách zabezpečení.  
  
- Pro zajištění řešení kompatibility, jako je virtualizace. Mnoho aplikací se třeba pokouší zapisovat do umístění s omezeným přístupem, jako je C:\Program Files. Pro aplikace spuštěné v nástroji Řízení uživatelských účtů existuje alternativní umístění pro jednotlivé uživatele, které pro zápis do nástroje nevyžaduje oprávnění správce. Pro aplikace, které běží v nástroji Řízení uživatelských účtů, Nástroj UAC virtualizuje C:\Program Files, takže aplikace, které jsou zapsány do této služby, jsou ve skutečnosti zapsány do alternativního umístění pro jednotlivé uživatele. Tento druh práce s kompatibilitou umožňuje operačnímu systému spouštět mnoho aplikací, které se dřív nepodařilo spustit v nástroji Řízení uživatelských účtů.  
  
#### <a name="code-integrity-checks"></a>Kontroly integrity kódu  
 Systém Windows Vista zahrnuje hlubší kontroly integrity kódu, které zabraňují v vkládání škodlivého kódu do systémových souborů nebo do jádra za běhu za běhu. To překračuje ochranu systémových souborů.  
   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Proces omezených práv pro aplikace hostované v prohlížeči  
 Aplikace WPF hostované v prohlížeči se spouštějí v karanténě zóny Internet Zone. Integrace WPF s aplikací Microsoft Internet Explorer rozšiřuje tuto ochranu o další podporu.  
  
 Vzhledem k tomu, že aplikace prohlížeče XAML (XBAP) jsou obecně izolované nastavením oprávnění zóny Internet, odebrání těchto oprávnění nepoškozuje aplikace prohlížeče XAML (XBAP) z hlediska kompatibility. Místo toho je vytvořena další vrstva důkladné obrany; Pokud aplikace izolovaného prostoru (sandbox) může zneužít jiné vrstvy a převzít proces, bude mít stále omezená oprávnění.  
  
 Viz [použití účtu uživatele s nejnižšími oprávněními](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
## <a name="common-language-runtime-security"></a>Zabezpečení společného jazykového modulu runtime  
 Modul CLR (Common Language Runtime) nabízí řadu výhod zabezpečení klíčů, které zahrnují ověřování a ověřování, zabezpečení přístupu kódu (CAS) a kritickou metodologii zabezpečení.  
    
### <a name="validation-and-verification"></a>Ověřování a ověřování  
 Pro zajištění izolace a integrity sestavení používá CLR proces ověřování. Ověřování CLR zajišťuje izolaci sestavení tím, že ověřuje jejich formát přenositelného spustitelného souboru (PE) pro adresy, které ukazují mimo sestavení. Ověřování CLR také ověřuje integritu metadat, která jsou vložena do sestavení.  
  
 Za účelem zajištění bezpečnosti typů, což umožňuje zabránit běžným problémům se zabezpečením (například přetečení vyrovnávací paměti) a povolit sandboxing prostřednictvím izolovaného procesu, zabezpečení CLR používá koncept ověřování.  
  
 Spravované aplikace jsou kompilovány do jazyka MSIL (Microsoft Intermediate Language). Když jsou spouštěny metody ve spravované aplikaci, je její jazyk MSIL zkompilován do nativního kódu prostřednictvím kompilace JIT (just-in-time). Kompilace JIT zahrnuje proces ověření, který se vztahuje na mnoho pravidel zabezpečení a odolnosti, které zajišťují, že kód:  
  
- Porušení kontraktů typu  
  
- Zavedení přetečení vyrovnávací paměti  
  
- Přístup k paměti je volně přístupný.  
  
 Spravovaný kód, který není v souladu s pravidly ověřování, není povoleno spustit, pokud se nepovažuje za důvěryhodný kód.  
  
 Výhodou ověřitelného kódu je klíčovým důvodem, proč WPF sestavuje na .NET Framework. V rozsahu, ve kterém se používá ověřitelný kód, se výrazně sníží možnost zneužití možných ohrožení zabezpečení.  
  
### <a name="code-access-security"></a>Zabezpečení přístupu kódu  
 Klientský počítač zveřejňuje širokou škálu prostředků, ke kterým může mít spravovaná aplikace přístup, včetně systému souborů, registru, tiskových služeb, uživatelského rozhraní, reflexe a proměnných prostředí. Aby mohla spravovaná aplikace přistupovat ke všem prostředkům v klientském počítači, musí mít .NET Framework oprávnění k tomu. Oprávnění v certifikačních autoritách je podtřídou <xref:System.Security.CodeAccessPermission>; CAS implementuje jednu podtřídu pro každý prostředek, ke kterému mají přístup spravované aplikace.  
  
 Sada oprávnění, ke kterým je spravovaná aplikace udělována CAS při spuštění, se označuje jako sada oprávnění a je určena legitimací poskytovanou aplikací. Pro aplikace WPF jsou poskytnuté legitimace umístění nebo zóna, ze kterých se aplikace spouští. CAS identifikuje následující zóny:  
  
- **Tento počítač**. Aplikace spouštěné z klientského počítače (plně důvěryhodné).  
  
- **Místní intranet**. Aplikace spouštěné z intranetu. (Poněkud důvěryhodné).  
  
- **Internet.** Aplikace spouštěné z Internetu (Nejméně důvěryhodné).  
  
- **Důvěryhodné servery**. Aplikace identifikované uživatelem jako důvěryhodné (Nejméně důvěryhodné).  
  
- **Nedůvěryhodné lokality**. Aplikace identifikované uživatelem jako nedůvěryhodné. (Nedůvěryhodné).  
  
 Pro každou z těchto zón poskytuje CAS sadu předdefinovaných oprávnění, která zahrnuje oprávnění, která odpovídají úrovni důvěry přidružené k jednotlivým. Zde jsou některé z nich:  
  
- **FullTrust**. Pro aplikace spouštěné ze zóny **můj počítač** . Všechna možná oprávnění jsou udělena.  
  
- **LocalIntranet**. Pro aplikace spouštěné z **místní zóny intranetu** . K poskytnutí středního přístupu k prostředkům klientského počítače, včetně izolovaného úložiště, neomezeného přístupu k uživatelskému rozhraní, neomezených dialogových oken, omezených reflexe a omezeného přístupu k proměnným prostředí, je udělená podmnožina oprávnění. Nejsou k dispozici oprávnění pro kritické prostředky, jako je registr.  
  
- **Internet.** Pro aplikace spouštěné ze zóny **Internet** nebo **Důvěryhodné servery** . K poskytnutí omezeného přístupu k prostředkům klientského počítače, včetně izolovaného úložiště, jenom otevřeného souboru a omezeného uživatelského rozhraní, se udělí podmnožina oprávnění. V podstatě Tato sada oprávnění izoluje aplikace od klientského počítače.  
  
 Aplikacím identifikovaným jako **nedůvěryhodné servery** nejsou vůbec udělena oprávnění CAS. V důsledku toho pro ně neexistuje předdefinovaná sada oprávnění.  
  
 Následující obrázek znázorňuje vztah mezi zónami, sadami oprávnění, oprávněními a prostředky:  
  
 ![Diagram, který zobrazuje sady oprávnění CAS.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 Omezení izolovaného prostoru zabezpečení zóny Internet Zone platí stejně jako jakýkoli kód, který XBAP importuje ze systémové knihovny, včetně WPF. Tím se zajistí, že je každý bit kódu uzamčený, dokonce i WPF. Aby bylo možné spustit, aplikace XBAP potřebuje spustit funkci, která vyžaduje více oprávnění než ty, které jsou povoleny v izolovaném prostoru zabezpečení Internetové zóny.  
  
 Zvažte aplikaci XBAP, která obsahuje následující stránku:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Aby bylo možné spustit tuto funkci XBAP, musí podkladový kód WPF spustit více funkcí, než je k dispozici pro volání funkce XBAP, včetně:  
  
- Vytvoření popisovače okna (HWND) pro vykreslování  
  
- Odesílání zpráv  
  
- Načítání písma Tahoma  
  
 Z hlediska zabezpečení by byl umožněn přímý přístup k libovolné z těchto operací z aplikace v izolovaném prostoru (sandbox).  
  
 Naštěstí rozhraní WPF v této situaci umožňuje provádět tyto operace se zvýšenými oprávněními jménem aplikace v izolovaném prostoru (sandbox). I když jsou všechny operace WPF zkontrolovány proti omezeným oprávněním zabezpečení zóny Internet pro doménu aplikace v XBAP, WPF (stejně jako u ostatních systémových knihoven) je udělena sada oprávnění, která obsahuje všechna možná oprávnění.
  
 K tomu je potřeba, aby WPF přijímal zvýšená oprávnění, přičemž se jim zabrání v tom, aby se tato oprávnění řídila sadou oprávnění zóny Internet v doméně hostitelské aplikace.  
  
 WPF to dělá pomocí metody **Assert** oprávnění. Následující kód ukazuje, jak se to stane.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 **Kontrolní** výraz v podstatě zabraňuje neomezenému oprávnění, které vyžaduje WPF, od omezení oprávnění pro internetovou ZÓNU v XBAP.  
  
 Z perspektivy platformy je WPF zodpovědný za správné použití **Assert** ; nesprávné použití **výrazu Assert** by mohlo povolit zvýšení oprávnění škodlivým kódem. V důsledku toho je důležité volat pouze **Assert** v případě potřeby a zajistit, aby omezení izolovaného prostoru zůstala nedotčená. Například kód v izolovaném prostoru (sandbox) nesmí otevírat náhodné soubory, ale může používat písma. WPF umožňuje aplikacím v izolovaném prostoru (sandbox) používat funkce písma voláním **Assert**a pro WPF ke čtení souborů, které obsahují tato písma jménem aplikace v izolovaném prostoru.  
  
### <a name="clickonce-deployment"></a>ClickOnce – nasazení  
 ClickOnce je komplexní technologie nasazení, která je součástí .NET Framework a integruje se se sadou Visual Studio (podrobné informace najdete v tématu [zabezpečení a nasazení ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) ). Samostatné aplikace WPF lze nasadit pomocí technologie ClickOnce, zatímco aplikace hostované v prohlížeči musí být nasazeny s ClickOnce.  
  
 Aplikacím nasazeným pomocí technologie ClickOnce je poskytnuta další vrstva zabezpečení než zabezpečení přístupu kódu (CAS); v podstatě aplikace nasazené ClickOnce požaduje oprávnění, která potřebují. Jsou jim udělena pouze ta oprávnění, pokud nepřekročí sadu oprávnění pro zónu, ze které je aplikace nasazena. Omezením sady oprávnění jenom na ty, které jsou potřeba, i když jsou menší než ta, kterou poskytuje sada oprávnění pro spouštěcí zónu. počet prostředků, ke kterým má aplikace přístup, se zkracuje na minimum. V důsledku toho, pokud dojde k narušení aplikace, je možné omezit poškození klientského počítače.  
  
### <a name="security-critical-methodology"></a>Metodika kritické pro zabezpečení  
 Kód WPF, který používá oprávnění k povolení izolovaného prostoru Internet Zone pro aplikace XBAP, je nutné uchovávat v nejvyšší možné úrovni auditu zabezpečení a řízení. Pro usnadnění tohoto požadavku .NET Framework poskytuje novou podporu pro správu kódu, který zvyšuje oprávnění. Konkrétně modul CLR vám umožňuje identifikovat kód, který zvyšuje oprávnění, a označit ho pomocí <xref:System.Security.SecurityCriticalAttribute>; kód, který není označený <xref:System.Security.SecurityCriticalAttribute>, se bude *transparentní* pomocí této metodologie. V opačném případě spravovaný kód, který není označený <xref:System.Security.SecurityCriticalAttribute>, brání oprávnění zvýšit oprávnění.  
  
 Metodologie pro kritické zabezpečení umožňuje organizaci kódu WPF, která zvyšuje oprávnění na *jádro kritické pro zabezpečení*a zbytek je transparentní. Izolování kódu, který je kritický pro zabezpečení, umožňuje technickému týmu WPF soustředit se na další analýzu zabezpečení a správu zdrojů v jádru kritickém pro zabezpečení nad rámec standardních postupů zabezpečení (viz [strategie zabezpečení WPF – Security Engineering](wpf-security-strategy-security-engineering.md)).  
  
 Všimněte si, že .NET Framework povoluje, aby důvěryhodný kód rozšířil izolovanou prostorovou mezipaměť internetové zóny XBAP tím, že umožňuje vývojářům psát spravovaná sestavení označená pomocí <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) a nasazená do globální mezipaměti sestavení (GAC) uživatele. Označení sestavení pomocí APTCA je vysoce citlivá operace zabezpečení, protože umožňuje jakémukoli volání tohoto sestavení, včetně škodlivého kódu z Internetu. Při tomto postupu se musí použít extrémní opatrnost a osvědčené postupy. aby se uživatelé museli nainstalovat, musí si vybrat, aby tento software důvěřoval.  
  
## <a name="microsoft-internet-explorer-security"></a>Microsoft Internet Explorer Security  
 Kromě snížení zabezpečení a zjednodušení konfigurace zabezpečení Microsoft Internet Explorer 6 (SP2) obsahuje několik funkcí, které vylepšení zabezpečení zvyšují zabezpečení pro uživatele aplikací prohlížeče XAML (XBAP). Pohyb těchto funkcí se snaží uživatelům větší kontrolu nad jejich možností procházení.  
  
 Před IE6 SP2 můžou uživatelé podléhat některé z následujících možností:  
  
- Náhodně otevíraná okna.  
  
- Matoucí přesměrování skriptu.  
  
- Řada dialogů zabezpečení na některých webech.  
  
 V některých případech se nedůvěryhodné weby pokusí uživatele přimět k instalaci [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] nebo opakovanému zobrazení dialogového okna instalace Microsoft ActiveX, a to i v případě, že ho uživatel mohl zrušit. Pomocí těchto postupů je možné, že velký počet uživatelů byl napadený, což vede k nedostatečným rozhodováním, což vedlo k instalaci spywarových aplikací.  
  
 IE6 SP2 obsahuje několik funkcí, které pomáhají zmírnit tyto typy problémů, které se týkají konceptu zahájení spouštění uživatelů. IE6 SP2 detekuje, kdy uživatel klikl na odkaz nebo element stránky před akcí, která se označuje jako *iniciace uživatele*, a považuje ji za odlišnou od toho, že skript na stránce aktivuje podobnou akci. Příklad: IE6 SP2 zahrnuje **blokování automaticky otevíraných oken** , které detekuje, když uživatel klikne na tlačítko před stránkou, která vytváří automaticky otevírané okno. To umožňuje, aby aplikace IE6 SP2 povolovala většinu automaticky otevíraných oken neškodného a současně zabránila automaticky otevíraná okna, která se uživatelům nedotazují ani nechtějí. Blokovaná automaticky otevíraná okna jsou zachycena v novém **informačním panelu**, který uživateli umožňuje ručně přepsat blok a zobrazit automaticky otevírané okno.  
  
 Pro **otevření**/**uložení** výzev zabezpečení se použije také stejná logika pro zahájení uživatelem. Dialogová okna pro instalaci ActiveX jsou v informačním pruhu vždy zachycena, pokud nepředstavuje upgrade z dříve nainstalovaného ovládacího prvku. Tyto míry se kombinují, aby uživatelům poskytovaly bezpečnější a lépe řízené uživatelské prostředí, protože jsou chráněné před lokalitami, které jim umožňují nainstalovat nežádoucí nebo škodlivý software.  
  
 Tyto funkce také chrání zákazníky, kteří používají aplikaci IE6 SP2 k procházení webů, které jim umožňují stahovat a instalovat aplikace WPF. To je důležité kvůli tomu, že aplikace IE6 SP2 nabízí lepší uživatelské prostředí, které uživatelům omezuje možnost instalace škodlivých nebo Devious aplikací bez ohledu na to, jaká technologie se použila k jejich sestavení, včetně WPF. WPF přidá tyto ochrany pomocí ClickOnce, aby usnadnila stahování svých aplikací přes Internet. Vzhledem k tomu, že aplikace prohlížeče XAML (XBAP) se provádějí v izolovaném prostoru zabezpečení Internetové zóny, můžou se snadno spustit. Na druhé straně samostatné aplikace WPF vyžadují ke spuštění úplný vztah důvěryhodnosti. Pro tyto aplikace ClickOnce zobrazí dialogové okno zabezpečení během procesu spuštění, aby upozornilo na použití dalších požadavků na zabezpečení aplikace. To ale musí být iniciované uživatelem, bude se řídit také logikou iniciované uživatelem a můžete ho zrušit.  
  
 Internet Explorer 7 zahrnuje a rozšiřuje možnosti zabezpečení aplikace IE6 SP2 jako součást trvalého závazku na zabezpečení.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení přístupu kódu](../misc/code-access-security.md)
- [Zabezpečení](security-wpf.md)
- [Částečné zabezpečení důvěryhodnosti WPF](wpf-partial-trust-security.md)
- [Strategie zabezpečení WPF – engineering zabezpečení](wpf-security-strategy-security-engineering.md)
