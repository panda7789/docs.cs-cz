---
title: Přenos aplikací .NET Core – knihovny
description: Zjistěte, jak přenést projekty knihovny z rozhraní .NET Framework do .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 07/14/2017
ms.openlocfilehash: eb6b8506d8df218a053242cd0b8d3097fa6d9fd3
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041658"
---
# <a name="porting-to-net-core---libraries"></a>Přenos aplikací .NET Core – knihovny

Tento článek popisuje přenosem kód knihovny pro .NET Core tak, aby běžel napříč platformami.

## <a name="prerequisites"></a>Požadavky

Tento článek předpokládá, že jste:

- Používání sady Visual Studio 2017 nebo novější.
  - .NET core není podporované v dřívějších verzích sady Visual Studio
- Vysvětlení [doporučuje portování procesu](index.md).
- Byly vyřešeny problémy s [závislostí třetích stran](third-party-deps.md).

Měli byste si také se seznámit s obsahem v následujících tématech:

[.NET standard](~/docs/standard/net-standard.md)   
Toto téma popisuje formální specifikaci rozhraní API .NET, která mají být k dispozici na všech implementace .NET.

[Balíčky, Metabalíčky a architektury](~/docs/core/packages.md)   
Tento článek popisuje, jak definuje a používá balíčky .NET Core a jak balíčky podporují kód spuštěný na více implementací rozhraní .NET.

[Vývoj knihoven pomocí nástrojů pro různé platformy](~/docs/core/tutorials/libraries.md)   
Toto téma vysvětluje, jak psát knihoven pro .NET pomocí nástrojů příkazového řádku pro různé platformy.

[Doplňky *csproj* formát pro .NET Core](~/docs/core/tools/csproj.md)   
Tento článek popisuje změny, které byly přidány do souboru projektu jako součást přesunu do *csproj* a MSBuild.

[Přenos aplikací .NET Core – analýza závislostí třetích stran strany](~/docs/core/porting/third-party-deps.md)   
Toto téma popisuje přenositelnost závislostí třetích stran a co dělat, když závislost balíčku NuGet není spuštěna v rozhraní .NET Core.

## <a name="net-framework-technologies-unavailable-on-net-core"></a>Technologií rozhraní .NET framework není k dispozici v rozhraní .NET Core

Několik technologií, které jsou k dispozici pro knihovny rozhraní .NET Framework nejsou k dispozici pro použití s .NET Core, jako je například objektů třídy AppDomains, vzdálené komunikace, zabezpečení přístupu kódu (CAS) a transparentnost zabezpečení. Pokud vaše knihovny spoléhat na jeden nebo více z těchto technologií, vezměte v úvahu alternativních přístupů popsaných níže. Další informace o kompatibilitě rozhraní API CoreFX tým udržuje [seznam konce změny/compat chování a zastaralé nebo starší verze rozhraní API](https://github.com/dotnet/corefx/wiki/ApiCompat) v Githubu.

To, že rozhraní API nebo technologie v současnosti není implementovaná nebude neznamená, že má nepodporovanou záměrně. Založte problém v [úložišti dotnet/corefx problémy](https://github.com/dotnet/corefx/issues) v Githubu o konkrétní rozhraní API a technologií. [Portování požadavky otázky](https://github.com/dotnet/corefx/labels/port-to-core) jsou označené `port-to-core` popisek.

### <a name="appdomains"></a>AppDomains

Objektů třídy AppDomains izolace aplikace od sebe. Objektů třídy AppDomains vyžadují podpora modulu CLR a obvykle jsou dost drahé. Nejsou implementované v .NET Core. Plánujeme není na přidání této funkce v budoucnu. Izolace kódu, doporučujeme samostatné procesy nebo pomocí kontejnerů jako alternativu. Pro dynamické načítání sestavení, doporučujeme vám nový <xref:System.Runtime.Loader.AssemblyLoadContext> třídy.

Pro usnadnění migrace kódu z rozhraní .NET Framework, jsme jste některé z vystavené <xref:System.AppDomain> rovinu rozhraní API v .NET Core. Některé z rozhraní API pracuje normálně (například <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), některé členy Neprovádět žádnou akci (třeba <xref:System.AppDomain.SetCachePath%2A>), a některé z nich výjimku <xref:System.PlatformNotSupportedException> (například <xref:System.AppDomain.CreateDomain%2A>). Zkontrolujte typy použít proti [ `System.AppDomain` zdroj odkazu](https://github.com/dotnet/corefx/blob/master/src/System.Runtime.Extensions/src/System/AppDomain.cs) v [úložiště GitHub dotnet/corefx](https://github.com/dotnet/corefx) nezapomeňte vybrat větev, která odpovídá verzi implementovaná.

### <a name="remoting"></a>Vzdálená komunikace

Vzdálené komunikace .NET byla identifikována jako problematické architektury. Používá se pro komunikaci mezi domény aplikace, které se už nepodporuje. Vzdálená komunikace také vyžaduje podpora modulu CLR, které je náročné na údržbu. Z těchto důvodů se nepodporuje vzdálené komunikace .NET na .NET Core a není plánujeme v budoucnu doplnění podpory pro něj.

Komunikace mezi procesy, vezměte v úvahu mechanismus meziprocesové komunikace (IPC) jako alternativu k vzdálené komunikace, jako <xref:System.IO.Pipes> nebo <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> třídy.

V počítačích použijte jako alternativu řešení založené na síti. Pokud možno použijte protokol s nízkou režií prostého textu, jako je například HTTP. [Kestrel webový server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), webový server používá ASP.NET Core, je možnost tady. Také zvážit použití <xref:System.Net.Sockets> pro scénáře založené na síti, mezi počítači. Další možnosti najdete v tématu [.NET Open Source projektů pro vývojáře: zasílání zpráv](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

### <a name="code-access-security-cas"></a>Zabezpečení přístupu kódu (CAS)

Izolace (sandbox), která se spoléhá na modul runtime nebo rozhraní, chcete-li omezit které prostředky spravované aplikace nebo knihovna používá nebo běží, [není podporován v rozhraní .NET Framework](~/docs/framework/misc/code-access-security.md) a proto se taky nepodporuje v rozhraní .NET Core. Věříme, že existují moc velký počet případů v rozhraní .NET Framework a modulu runtime kde dojde k zvýšení oprávnění pokračovat zpracování certifikační Autority jako hranice zabezpečení. Certifikační Autority navíc díky implementaci složitější a často má vliv na správnost výkon pro aplikace, které nechcete použít.

Volit raději hranice zabezpečení poskytované operačního systému, například virtualizace, kontejnerů nebo uživatelské účty pro spouštění procesů s nejmenší sadu oprávnění.

### <a name="security-transparency"></a>Transparentnost zabezpečení

Podobně jako u certifikační Autority, transparentnost zabezpečení umožňuje oddělení kódu v izolovaném prostoru z zabezpečení kritického kódu deklarativní způsobem, ale je [již nejsou podporovány jako hranice zabezpečení](~/docs/framework/misc/security-transparent-code.md). Tato funkce je nejčastěji používá program Silverlight. 

Volit raději hranice zabezpečení poskytované operačního systému, například virtualizace, kontejnerů nebo uživatelské účty pro spouštění procesů s nejmenší sadu oprávnění.

## <a name="converting-a-pcl-project"></a>Převod projekt PCL

Cíle projektu PCL můžete převést do .NET Standard načítání knihovny v sadě Visual Studio 2017 a provedením následujících kroků:

1. Klikněte pravým tlačítkem na soubor projektu a vyberte **vlastnosti**.
1. V části **knihovny**vyberte **Standard platformy cílové .NET**.

Pokud vaše balíčky podpory NuGet 3.0, projektu změnit cílení na .NET Standard.

Pokud vaše balíčky bez podpory NuGet 3.0, zobrazí se dialogové okno ze sady Visual Studio s výzvou k odinstalovat aktuální balíčky. Pokud se zobrazí toto upozornění, proveďte následující kroky:

1. Klikněte pravým tlačítkem na projekt, vyberte **spravovat balíčky NuGet**.
1. Poznamenejte si projektu balíčky.
1. Odinstalace balíčků jeden po druhém.
1. Může být potřeba restartovat Visual Studio a dokončete proces odinstalace. Pokud ano, **restartovat** tlačítko je v článku **Správce balíčků NuGet** okna.
1. Když projekt znovu načte, zaměřuje .NET Standard. Přidáte balíčky, které jsou vyžadovány pro odinstalaci.

## <a name="retargeting-your-net-framework-code-to-net-framework-462"></a>Mění se cílení kód rozhraní .NET Framework do .NET Framework 4.6.2

Pokud je váš kód není zaměřen na rozhraní .NET Framework 4.6.2, doporučujeme změnit cílení na rozhraní .NET Framework 4.6.2. Tím se zajistí dostupnosti nejnovější alternativy rozhraní API pro případy, kdy .NET Standard nepodporuje existující rozhraní API.

Pro každý ze svých projektů v sadě Visual Studio, budete chtít port, postupujte takto:

1. Klikněte pravým tlačítkem na projekt a vyberte vlastnosti.
1. V **Cílová architektura** rozevíracího seznamu vyberte **rozhraní .NET Framework 4.6.2**.
1. Znovu zkompilujte vaše projekty.

Protože projekty teď cílí na rozhraní .NET Framework 4.6.2, použijte tuto verzi rozhraní .NET Framework jako základu pro portování kódu.

## <a name="determining-the-portability-of-your-code"></a>Určení přenositelnost kódu

Dalším krokem je spuštění Portability Analyzeru rozhraní API (ApiPort), aby se vygenerovala sestava přenositelnost pro analýzu.

Ujistěte se, že rozumíte [analyzátor přenositelnosti rozhraní API (ApiPort)](../../standard/analyzers/portability-analyzer.md) a generování sestav přenositelnost pro cílení na .NET Core. Postup tuto pravděpodobně se liší podle vašich potřeb a osobní chutí. Následují několik různých přístupů. Může být pro vás sami kombinování kroky těchto přístupů v závislosti na tom, jak váš kód strukturovaná.

### <a name="dealing-primarily-with-the-compiler"></a>Především zabývají kompilátor

Tento přístup může být nejvhodnější pro malé projekty nebo projekty, které nepoužívají mnoho rozhraní API .NET Framework. Tento přístup je jednoduchý:

1. Volitelně můžete spustit ApiPort na váš projekt. Pokud spustíte ApiPort, seznamte se ze sestavy na problémy, se kterými budete potřebovat adresu.
1. Zkopírujte celý kód do nového projektu .NET Core.
1. Při odkazování na sestavy přenositelnost (je-li generovat), řešení chyb kompilátoru, dokud se projekt zkompiluje plně.

Přestože tento přístup nestrukturovaných, přístup zaměřený na kód často vede k řešení problémů rychle a může být nejlepším řešením pro menší projekty nebo knihovny. Projekt obsahující pouze datových modelů může být ideální volbou pro tento přístup.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>Zachování na rozhraní .NET Framework, dokud se nevyřeší problémy s přenositelností

Tento přístup může být nejlepší, pokud chcete mít kód, který zkompiluje během celého procesu. Tento přístup je následujícím způsobem:

1. Spusťte ApiPort na projektu.
1. Řešení potíží s pomocí různých rozhraní API, která jsou přenositelné.
1. Poznamenejte si všechny oblasti, kde budete moci používat s přímým přístupem alternativní.
1. Opakujte předchozí kroky pro všechny projekty, které jste přenos, dokud nejste jisti, že každá je připraven k zkopírovat do nového projektu .NET Core.
1. Zkopírujte kód do nového projektu .NET Core.
1. Fungovat případné potíže, pokud jste si poznamenali, že s přímým přístupem alternativní neexistuje.

Tento přístup opatrní je více strukturovanými než jednoduše práce si chyby kompilátoru, ale je stále poměrně zaměřený na kód a má výhodu vždy mít kód, který zkompiluje. Způsob, jak vyřešit některé problémy, které nejde ji adresovat podle pouze pomocí jiného rozhraní API se výrazně liší. Můžete zjistit, které potřebujete pro vývoj další komplexní plánování pro určité projekty, které se vztahuje na další přístup se považuje za.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Komplexní plán útoku

Tento přístup může být nejvhodnější pro projekty větší a složitější, kde změna struktury kódu nebo zcela přepsání některých oblastech kódu může být potřeba podporovat .NET Core. Tento přístup je následujícím způsobem:

1. Spusťte ApiPort na projektu.
1. Vysvětlení použití jednotlivých typů nepřenosné a že má vliv celkové přenositelnost.
   - Pochopení povahy z těchto typů. Jsou malá v číslech ale používané často? Jsou velké číslo, ale používá zřídka? Jejich používání se soustřeďuje nebo se šíří prostřednictvím vašeho kódu?
   - Je snadné k izolaci kód, který není přenosné, takže můžete s ním naložit efektivněji?
   - Je třeba jak Refaktorovat kód?
   - Pro tyto typy, které nejsou přenosné existují alternativní rozhraní API, která stejný úkol provést? Například pokud používáte <xref:System.Net.WebClient> třídy, je možné použít <xref:System.Net.Http.HttpClient> namísto třídy.
   - Existují různé Přenositelná rozhraní API dostupné pro provádění různých úloh, i v případě, že se nejedná o což je náhrada databáze? Například pokud používáte <xref:System.Xml.Schema.XmlSchema> k analyzovat soubor XML, ale nevyžadují XML schématu zjišťování, které můžete využít <xref:System.Xml.Linq> rozhraní API a implementovat parsování sami na rozdíl od spoléhání se na rozhraní API.
1. Pokud máte sestavení, které je obtížné port stojí všechnu je nyní v rozhraní .NET Framework? Tady je pár věcí k uvážení:
   - Některé funkce mohou mít v knihovně, která je nekompatibilní s .NET Core, protože příliš často závisí na funkcích rozhraní .NET Framework nebo s Windows. Je může být vhodné zanechání, které tuto funkci teď a uvolněním verzi .NET Core knihovny s méně funkcemi dočasně, dokud prostředky jsou k dispozici k portu funkce?
   - By Refaktorujte pomoct?
1. Je přijatelné pro zápis vlastní implementaci rozhraní není k dispozici rozhraní API .NET?
   Zvažte kopírování, úpravou a použitím kódu z [referenční zdroje rozhraní .NET Framework](https://github.com/Microsoft/referencesource). Odkaz na zdrojový kód je licencován [licencí MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), takže budete mít významný dá volnost, abyste zdroj jako základ pro váš vlastní kód. Jenom nezapomeňte správně atribut Microsoft ve vašem kódu.
1. Tento postup opakujte podle potřeby pro různé projekty.
 
Z analytické fáze může chvíli trvat v závislosti na velikosti vašeho základu kódu. Výdaje v této fázi chcete důkladně porozumět rozsahu, změny potřebné a obvykle při vytváření plánu vám ušetří čas čas v dlouhodobém horizontu, zejména v případě, že máte komplexní základ kódu.

Váš plán může zahrnovat provedení významných změn do vašeho základu kódu zároveň stále cílí na rozhraní .NET Framework 4.6.2, takže jde strukturovanějších verzi předchozí postup. Jak přejít o spuštění vašeho plánu je závislá na vašem základu kódu.

### <a name="mixing-approaches"></a>Kombinováním přístupů

Je pravděpodobné, že budete kombinaci výše uvedených přístupů na základě jednotlivých projektů. Byste měli dělat to, co vám nejvíce vyhovuje vám a pro vašeho základu kódu.

## <a name="porting-your-tests"></a>Portování testů

Nejlepší způsob, jak Ujistěte se, že všechno funguje, když jste přenést váš kód je k testování kódu, protože port až po .NET Core. K tomuto účelu, budete muset použít testovací rozhraní, které sestaví a spustí testy pro .NET Core. V současné době máte tři možnosti:

- [xUnit](https://xunit.github.io/)
  * [Začínáme](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  * [Nástroj pro převod projekt MSTest xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  * [Začínáme](https://github.com/nunit/docs/wiki/Installation)
  * [Blogový příspěvek o migraci z MSTest na NUnit](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>Doporučený postup pro přenos

Nakonec přenosem úsilí závisí do značné míry na strukturování kódu rozhraní .NET Framework. Než začneme je dobrým způsobem, jak přeneste kód *základní* knihovny, které jsou základní součástí kódu. To může být datové modely nebo některé základní třídy a metody, které všechno ostatní používá přímo nebo nepřímo.

1. Port testovacího projektu, který testuje vrstvě knihovny, který jste právě přenos.
1. Zkopírovat základní knihovny do nového projektu .NET Core a vyberte verzi jazyka .NET Standard si přejete podporovat.
1. Proveďte změny nutná, aby se kód mohl zkompilovat. Velká část to může být nutné přidat závislosti balíčků NuGet do vaší *csproj* souboru.
1. Spustit testy a provést všechny potřebné úpravy.
1. Vyberte další vrstvu kódu na port a opakujte předchozí kroky.

Je-li začít se základnou knihovny a přesunout ven ze základní třídy a otestovat každou vrstvu podle potřeby, přenos provádí systematické kde problémy jsou izolované na jednu vrstvu kódu v čase.
