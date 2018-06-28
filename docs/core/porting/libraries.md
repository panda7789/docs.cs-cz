---
title: Portování do .NET Core - knihovny
description: Zjistěte, jak k portu projektů knihovny z rozhraní .NET Framework na .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 07/14/2017
ms.openlocfilehash: 0f1d79623b4ece836732010e76a3c93fbbf8099f
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028042"
---
# <a name="porting-to-net-core---libraries"></a>Portování do .NET Core - knihovny

Tento článek popisuje přenosem kód knihovna pro .NET Core tak, aby běžel napříč platformami.

## <a name="prerequisites"></a>Požadavky

Tento článek předpokládá, že jste:

- Používáte Visual Studio 2017 nebo novější.
  - .NET core není podporována v dřívějších verzích sady Visual Studio
- Pochopení [doporučená portování proces](index.md).
- Byly vyřešeny problémy s [třetích stran závislosti](third-party-deps.md).

Měli byste si také se seznámit s obsahem v následujících tématech:

[Standardní rozhraní .NET](~/docs/standard/net-standard.md)   
Toto téma popisuje formální specifikaci rozhraní API .NET, která by měla být k dispozici na všech implementace rozhraní .NET.

[Balíčky, Metapackages a architektury](~/docs/core/packages.md)   
Tento článek popisuje, jak .NET Core definuje a používá balíčky, a jak balíčky podporují kód spuštěný na více implementace rozhraní .NET.

[Vývoj knihovny s křížové nástrojů platformy](~/docs/core/tutorials/libraries.md)   
Toto téma vysvětluje, jak napsat knihovny pro rozhraní .NET pomocí nástrojů příkazového řádku pro různé platformy.

[Doplňky *csproj* formát pro .NET Core](~/docs/core/tools/csproj.md)   
Tento článek popisuje změny, které byly přidány do souboru projektu v rámci přechodu *csproj* a MSBuild.

[Portování do .NET Core - analýza strany závislostmi třetích stran](~/docs/core/porting/third-party-deps.md)   
Toto téma popisuje přenositelnost závislostí třetích stran a co dělat, když závislost balíčku NuGet nefunguje v .NET Core.

## <a name="net-framework-technologies-unavailable-on-net-core"></a>Rozhraní .NET framework technologie, které jsou k dispozici na .NET Core

Několik technologií, které jsou k dispozici pro rozhraní .NET Framework knihovny nejsou k dispozici pro použití s .NET Core, například domén, vzdálenou komunikaci, zabezpečení přístupu kódu (CAS) a transparentnost zabezpečení. Pokud se knihovnách spoléhají na jeden nebo více z těchto technologií, zvažte alternativní přístupy uvedených níže. Další informace o kompatibilitě rozhraní API týmem CoreFX udržuje [seznam chování změny/compat zalomení a zastaralé nebo starší verze rozhraní API](https://github.com/dotnet/corefx/wiki/ApiCompat) v Githubu.

Právě, protože rozhraní API nebo technologie není implementována aktuálně nepodporuje neznamená, že má záměrně nepodporovaný. Problém v souboru [dotnet/corefx úložiště problémy](https://github.com/dotnet/corefx/issues) v Githubu a požádejte o konkrétní rozhraní API a technologie. [Portování požadavků v problémy](https://github.com/dotnet/corefx/labels/port-to-core) jsou označené `port-to-core` popisek.

### <a name="appdomains"></a>AppDomains

Domén izolace aplikace od sebe navzájem. Domén vyžaduje podporu runtime a jsou obecně dost drahé. Nejsou implementované v .NET Core. Plánujeme není na přidání této funkci v budoucnosti. Pro izolaci kódu, doporučujeme samostatné procesy nebo použití kontejnerů jako alternativu. Pro dynamické načítání sestavení, doporučujeme nové <xref:System.Runtime.Loader.AssemblyLoadContext> třídy.

Usnadnění kód migrace z rozhraní .NET Framework, jsme jste některé zveřejněné <xref:System.AppDomain> plochy rozhraní API v .NET Core. Některé z rozhraní API pracuje normálně (například <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), nic nestane. některé členy (například <xref:System.AppDomain.SetCachePath%2A>), a některá z nich výjimku <xref:System.PlatformNotSupportedException> (například <xref:System.AppDomain.CreateDomain%2A>). Zkontrolujte typy použijete proti [ `System.AppDomain` odkaz na zdroj](https://github.com/dotnet/corefx/blob/master/src/System.Runtime.Extensions/src/System/AppDomain.cs) v [úložiště GitHub dotnet/corefx](https://github.com/dotnet/corefx) a zkontrolujte, zda vyberte větev, který odpovídá vaší verzi implementovaná.

### <a name="remoting"></a>Vzdálená komunikace

.NET remoting byla identifikována jako problematické architektura. Používá se pro komunikaci mezi AppDomain, který již není podporována. Vzdálená komunikace také vyžaduje podporu runtime, která je nákladná, chcete-li zachovat. Z těchto důvodů .NET Remoting není podporována na .NET Core a nemáte plánujeme týkající se přidání podpory pro něj v budoucnu.

Pro komunikaci mezi procesy, zvažte mechanismy meziprocesová komunikace (IPC) jako alternativu k vzdálenou komunikaci, například <xref:System.IO.Pipes> nebo <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> třídy.

V počítačích použijte jako alternativu řešení založené na síti. Pokud možno použijte nízkou režii prostého textu protokolu, jako je například HTTP. [Kestrel webový server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), webový server používá ASP.NET Core, je možnost sem. Také zvažte použití <xref:System.Net.Sockets> pro scénáře založené na síti, mezi počítači. Další možnosti najdete v tématu [.NET otevřete zdroj vývojáře projekty: zasílání zpráv](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

### <a name="code-access-security-cas"></a>Zabezpečení přístupu kódu (CAS)

Sandboxing, který se spoléhat na modulu runtime nebo framework omezit které prostředky na spravované aplikace nebo knihovnu používá, nebo běží, [nepodporuje rozhraní .NET Framework](~/docs/framework/misc/code-access-security.md) a proto se také nepodporuje na .NET Core. Věříme, že jsou příliš mnoho případy v rozhraní .NET Framework a prostředí runtime vyskytl zvýšení oprávnění, chcete-li pokračovat, považuje certifikační Autority jako hranice zabezpečení. Kromě toho certifikační Autority umožňuje implementace složitější a často má důsledky správnost výkonu pro aplikace, které nemáte v úmyslu použít.

Použijte hranice zabezpečení poskytované operačního systému, například virtualizace, kontejnery nebo uživatelské účty pro spouštění procesů nejmenší sadu oprávnění.

### <a name="security-transparency"></a>Průhlednost zabezpečení

Podobně jako u certifikační Autority, transparentnost zabezpečení umožňuje oddělení kódu v izolovaném prostoru z kód kritický pro zabezpečení deklarativní způsobem, ale je [již nejsou podporovány jako hranice zabezpečení](~/docs/framework/misc/security-transparent-code.md). Tato funkce slouží výraznou program Silverlight. 

Použijte hranice zabezpečení poskytované operačního systému, například virtualizace, kontejnery nebo uživatelské účty pro spouštění procesů nejmenší sadu oprávnění.

## <a name="converting-a-pcl-project"></a>Převedení projektu PCL

Cíle projektu PCL můžete převést na rozhraní .NET standardní načítání knihovny v nástroji Visual Studio 2017 a provedením následujících kroků:

1. Klikněte pravým tlačítkem na soubor projektu a vyberte **vlastnosti**.
1. V části **knihovny**, vyberte **Standard platformy cíl .NET**.

Pokud vaše balíčky podporují NuGet 3.0, retargets projektu na .NET standardní.

Pokud vaše balíčky nepodporují NuGet 3.0, zobrazí se dialogové okno ze sady Visual Studio s výzvou k odinstalaci vaše aktuální balíčků. Pokud se zobrazí toto upozornění, proveďte následující kroky:

1. Klikněte pravým tlačítkem na projekt, vyberte **spravovat balíčky NuGet**.
1. Poznamenejte si projektu balíčků.
1. Odinstalaci balíčků jeden po druhém.
1. Možná budete muset restartovat Visual Studio, dokončete proces odinstalace. Pokud ano, **restartujte** se zobrazí tlačítko pro vás v **Správce balíčků NuGet** okno.
1. Pokud projekt znovu načte, cíle .NET Standard. Přidání balíčků, které bylo potřeba odinstalovat.

## <a name="retargeting-your-net-framework-code-to-net-framework-462"></a>Změna orientace kódu rozhraní .NET Framework pro rozhraní .NET Framework 4.6.2

Pokud váš kód není cílení na rozhraní .NET Framework 4.6.2, doporučujeme změnit cílový rozhraní .NET Framework 4.6.2. Tím zajistíte dostupnost nejnovější alternativy rozhraní API pro případy, kdy .NET Standard nepodporuje stávajících rozhraní API.

Pro každou z vašich projektů v sadě Visual Studio, které chcete portu, proveďte následující kroky:

1. Klikněte pravým tlačítkem na projekt a vyberte vlastnosti.
1. V **cílové rozhraní** rozevíracího seznamu vyberte **rozhraní .NET Framework 4.6.2**.
1. Znovu zkompiluje vašich projektů.

Protože projekty nyní cílí na rozhraní .NET Framework 4.6.2, použijte tuto verzi rozhraní .NET Framework jako vaše základní pro přenos kódu.

## <a name="determining-the-portability-of-your-code"></a>Určení přenositelnost kódu

Dalším krokem je spustit Analyzátor přenositelnost rozhraní API (ApiPort) k vygenerování sestavy přenositelnost pro analýzu.

Musíte rozumět [analyzátor přenositelnost rozhraní API (ApiPort)](../../standard/analyzers/portability-analyzer.md) a generování sestav přenositelnost pro cílení na .NET Core. Jak se tento pravděpodobně se může lišit podle vašich potřeb a osobní chutí. Jaké způsobem jsou několik různý přístup. Můžete zjistit sami kombinování kroky těmito dvěma způsoby v závislosti na tom, jak je strukturovaná kódu.

### <a name="dealing-primarily-with-the-compiler"></a>Především zabývají kompilátoru

Tento přístup může být nejvhodnější pro malé projekty nebo projekty, které nepoužívají mnoho rozhraní API technologie .NET Framework. Přístup je jednoduchý:

1. Volitelně můžete spustit ApiPort v projektu. Pokud spustíte ApiPort, získají informace ze sestavy na problémy, které budete potřebovat adresu.
1. Kopírovat veškerý kód přes do nového projektu .NET Core.
1. Při odkazování na sestavu přenositelnost (Pokud vygenerovaný), vyřešíte chyby kompilátoru, dokud plně zkompiluje projektu.

I když tento přístup nestrukturovaných, přístup zaměřené na kód často vede k řešení potíží se rychle a může být nejlepším řešením pro menší projekty nebo knihovny. Projekt, který obsahuje pouze datové modely může být ideální volbou pro tuto metodu.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>Zachování na rozhraní .NET Framework, dokud se nevyřeší problémy s přenositelností

Tento přístup může být nejvhodnější, pokud chcete, aby kód, který se zkompiluje během celého procesu. Přístup je následující:

1. Spusťte ApiPort na projektu.
1. Vyřešte problémy s pomocí jiné rozhraní API, které jsou přenosné.
1. Poznamenejte si všechny oblasti, kde vám zabrání v přístupu přímé alternativní.
1. Opakujte předchozí kroky pro všechny projekty, které jste portování, dokud si nejste jisti, že každý je připravena ke kopírování přes do nového projektu .NET Core.
1. Zkopírujte kód do nového projektu .NET Core.
1. Práce se všechny problémy, které jste si poznamenali, přímé alternativní neexistuje.

Tento přístup pozor, je více strukturovanými než jednoduše práce si chyby kompilátoru, ale je stále poměrně zaměřené na kód a výhodou je, že vždy kód, který se zkompiluje. Způsob řešení některých problémů, které nelze řešit pouze pomocí jiného rozhraní API se výrazně liší. Možná budete muset vyvíjet další komplexní plán pro určité projekty, které je zahrnuté jako další přístup.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Vývoj komplexní plán útoku

Tento přístup může být výhodné pro větší a složitější projekty, kde změnu struktury kódu nebo zcela přepisování určité oblasti kód může být nezbytné pro podporu .NET Core. Přístup je následující:

1. Spusťte ApiPort na projektu.
1. Porozumět, kde se používá každý typ přenosný počítač a jak, které ovlivní celkové přenositelnost.
   - Pochopení povahy těchto typů. Budou malý počet ale použít často? Budou velký počet ale použít zřídka? Zaměřena jejich používání, nebo se šíří prostřednictvím vašeho kódu?
   - Je snadno izolovat kód, který není přenosné tak, aby efektivněji nakládat s ní?
   - Je třeba Refaktorovat kódu?
   - Pro tyto typy, které nejsou přenosné existují alternativní rozhraní API, která provést stejný úkol? Například pokud používáte <xref:System.Net.WebClient> třídy, je možné použít <xref:System.Net.Http.HttpClient> třídy místo.
   - Existují různé přenosné rozhraní API k dispozici pro provádění různých úloh, i když není náhrada drop-in? Například pokud používáte <xref:System.Xml.Schema.XmlSchema> k analyzovat soubor XML, ale nevyžadují XML schéma zjišťování, můžete použít <xref:System.Xml.Linq> rozhraní API a implementujte analýza sami oproti spoléhat na rozhraní API.
1. Pokud máte sestavení, které je obtížné portu, je vhodné ponechat je v rozhraní .NET Framework pro nyní? Zde jsou některé věci vzít v úvahu:
   - V knihovně, který je nekompatibilní s .NET Core, protože je příliš výraznou závislé na funkce rozhraní .NET Framework nebo specifické pro systém Windows může mít některé funkce. Je vhodné ponechat tato funkcionalita chvíli a vydání verze .NET Core knihovny s méně funkcí dočasně dokud prostředky jsou k dispozici k portu funkce?
   - Pomohou refactor?
1. Je možné logicky zapsat implementace není k dispozici .NET Framework API?
   Zvažte kopírování, úpravy a pomocí kódu z [zdroje referenční dokumentace rozhraní .NET Framework](https://github.com/Microsoft/referencesource). Je licencován zdrojového kódu odkaz [licencí MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), takže budete mít významné volnost používat zdroj jako základ pro vlastní kód. Jenom nezapomeňte správně atribut Microsoft ve vašem kódu.
1. Tento postup opakujte podle potřeby pro různé projekty.
 
Z analytické fáze může trvat nějakou dobu v závislosti na velikosti vaší základu kódu. Výdaje čas v této fázi důkladně pochopit oboru potřebné změny a při vytváření plánu obvykle uloží je čas dlouhodobě, zejména v případě, že máte komplexní základu kódu.

Váš plán může zahrnovat provedení významných změn do vaší základu kódu při stále cílení na rozhraní .NET Framework 4.6.2, provedení to více strukturovanými verzi předchozí postup. Jak přejdete o provádění váš plán je závislá na vaše základu kódu.

### <a name="mixing-approaches"></a>Kombinování přístupy

Je pravděpodobné, že budete kombinovat výše uvedených přístupů na jednotlivých projektů. Měli byste udělat, co je nejvhodnější pro vás a vaši základu kódu.

## <a name="porting-your-tests"></a>Portování testů

Nejlepší způsob, jak zkontrolujte, zda že vše funguje, když jste přenést kód je k testování kódu, jako je port pro .NET Core. K tomu budete muset použít testování framework, který vytvoří a spustí testy pro .NET Core. V současné době máte tři možnosti:

- [xUnit](https://xunit.github.io/)
  * [Začínáme](http://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [Nástroj pro převod na xUnit projektu Mstestu](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](http://www.nunit.org/)
  * [Začínáme](https://github.com/nunit/docs/wiki/Installation)
  * [Příspěvku na blogu o migraci z Mstestu na NUnit](http://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [Mstestu](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>Doporučeným přístupem k portování

Nakonec přenosem úsilí závisí výraznou na struktury kódu rozhraní .NET Framework. Vhodný způsob k portu kódu je na začátku *základní* své knihovny, které jsou základní součástí vašeho kódu. To může být datových modelů nebo některé jiné základní třídy a metody, které všem ostatním používá přímo nebo nepřímo.

1. Port k testovacímu projektu, který testuje vrstvě své knihovny, který jste právě portování.
1. Zkopírujte přes základní knihovny do nového projektu .NET Core a vyberte verzi na Standard .NET chcete podporovat.
1. Proveďte požadované změny nutná, aby se kód mohl zkompilovat. Velká část to může být nutné přidat závislosti balíčků NuGet pro vaše *csproj* souboru.
1. Spusťte testy a provést všechny potřebné úpravy.
1. Vyberte další vrstva kódu na port a opakujte předchozí kroky.

Pokud začínat základní své knihovny a přesunout i od základní a otestovat každé vrstvě podle potřeby, portování je systematické proces kde problémy jsou izolovány. na jednu vrstvu kódu v čase.
