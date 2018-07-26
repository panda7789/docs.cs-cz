---
title: Správa verzí rozhraní .NET core
description: Zjistěte, jak funguje správa verzí rozhraní .NET Core.
author: bleroy
ms.author: mairaw
ms.date: 02/13/2018
ms.openlocfilehash: aa4f05a1a95c1bfbd16f41ca695ea23d48606772
ms.sourcegitcommit: 702d5ffc6e733b6c4ded85bf1c92e2293638ee9a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/04/2018
ms.locfileid: "37792319"
---
# <a name="net-core-versioning"></a>Správa verzí rozhraní .NET core

.NET core je tvořen [balíčky NuGet](../packages.md), nástrojů a architektur, distribuovaným jako celek. Každá z těchto úrovní platformy může být označené verzí samostatně, umožňuje lepší pružnost. Přestože existuje určitá flexibilita významné správy verzí v tomto ohledu, je zde také chce verze platformy jako jednotku k používání produktu snazší snadněji jim porozumíte.

Tento článek se zaměřuje na bylo zcela zřejmé, jak se systémovou správou verzí rozhraní .NET Core SDK a modulu runtime.

Existuje velké množství pohyblivých částí tuto verzi nezávisle na sobě v .NET Core. Od verze rozhraní .NET Core 2.0, je však snadno pochopit číslo verze nejvyšší úrovně, které každý uživatel rozumí být *verzi* ".NET Core" jako celek. Zbývající část tohoto dokumentu přejde do podrobností správy verzí všechny tyto součásti. Tyto údaje mohou být důležité, pokud jste správce balíčků, například.

> [!IMPORTANT]
> Podrobnosti správy verzí je vysvětleno v tomto tématu se nevztahují na aktuální verzi .NET Core SDK a modulu runtime.
> Verze schématu se mění v budoucích verzích. Zobrazí se aktuální návrh na [dotnet/návrhy](https://github.com/dotnet/designs/pull/29) úložiště.

## <a name="versioning-details"></a>Správa verzí podrobnosti

Soubory ke stažení s .NET Core 2.0, zobrazit číslo verze jednoho v názvu souboru. Tato čísla verzí bylo jednotné.

* Sdílené architektuře a přidružený modul runtime.
* Sada .NET Core SDK a přidružený příkazového řádku .NET Core.
* `Microsoft.NETCore.App` Microsoft.aspnetcore.all.

Použijte číselné provede jednu verzi usnadnit uživatelům vědět, jakou verzi sady SDK k instalaci na svých vývojových počítačích a které odpovídající verzi rozhraní sdílené by měl být nastane čas ke zřízení produkčním prostředí. Při stahování sady SDK nebo modul runtime, číslo verze, které se zobrazí se to být stejný.

### <a name="version-selection"></a>Výběr verze

.NET core se použije sada zásady, které určují, které verze modulu runtime .NET Core a sady SDK se používají v různých scénářích. Tyto scénáře a zásady jsou plně prozkoumali v následujícím článku na [výběr verze](selection.md).

Tyto zásady jako následující role si můžete představit:

* Povolte snadné a efektivní nasazení .NET Core, včetně aktualizace zabezpečení a spolehlivosti.
* Umožňují vývojářům používat nejnovější nástroje a příkazy, které jsou nezávislé na cílový modul runtime.

### <a name="installers"></a>Instalační programy

S .NET Core 2.0, soubory ke stažení pro [denně vytvoří](https://github.com/dotnet/core-setup#daily-builds) a [uvolní](https://www.microsoft.com/net/download/core) dodržovat nové schéma pojmenování snadněji jim porozumíte.
Instalační program uživatelského rozhraní v těchto souborech ke stažení změnil také jasně prezentovat na názvy a verze instalovaných komponent. Zejména názvy nyní zobrazit stejné číslo verze, která je v názvu souboru stažení.

#### <a name="file-name-format"></a>Formát názvu souboru

`[product]-[component]-[major].[minor].[patch]-[previewN]-[optional build #]-[rid].[file ext]`

Tady je několik příkladů tento formát:

```
dotnet-runtime-2.0.4-osx.10.12-x64.pkg            # Mac runtime installer
dotnet-sdk-2.0.4-win-x64.exe                      # Windows SDK installer
dotnet-sdk-2.0.4-linux-x64.tar.gz                 # Linux binary archive

#Ubuntu file set needed for the SDK
dotnet-host-2.0.4-ubuntu.16.04-x64.deb            # Host / muxer and host policy
dotnet-runtime-2.0.4-ubuntu.16.04-x64.deb         # runtime
dotnet-sdk-2.0.4-ubuntu.16.04-x64.deb             # SDK tools
```

Formát je čitelný a jasně ukazuje to, co si stáhnete, jaká verze je a kde ho můžete použít. Název balíčku modulu runtime obsahuje `runtime`, a sada SDK zahrnuje `SDK`.

#### <a name="ui-string-format"></a>Formát řetězce uživatelského rozhraní

Všechny popisy webu a řetězce uživatelského rozhraní v instalační programy jsou udržovány konzistentní vzhledem k aplikacím, přesné a jednoduché. V následující tabulce jsou uvedeny některé příklady:

| Instalační služba | Titulek okna                          | Další obsah v instalačním programu | Co je nainstalována                               |
| :--       | :--                                   | :--                        | :--                                             |
| Sada SDK       | Instalační program rozhraní .NET core 2.0 SDK (x 64)     | .NET core 2.0.4 SDK        | Nástroje .NET core 2.0.4 + modulu Runtime .NET Core 2.0.4 |
| Modul runtime   | Instalační program modulu Runtime (x64) .NET core 2.0 | Modul Runtime .NET core 2.0.4    | Modul Runtime .NET core 2.0.4                         |

Verze Preview se liší jen mírně:

| Instalační služba | Titulek okna                                    | Další obsah v instalačním programu        | Co je nainstalována                                                   |
| :--       | :--                                             | :--                               | :--                                                                 |
| Sada SDK       | Instalační program sady SDK (x 64) pro .NET core 2.0 ve verzi Preview 1     | .NET core 2.0.0 1 SDK ve verzi Preview.     | Nástroje .NET core 2.0.0 ve verzi Preview 1 + .NET Core 2.0.0 ve verzi Preview 1 modulu Runtime |
| Modul runtime   | Instalační program modulu Runtime (x64) .NET core 2.0 ve verzi Preview 1 | Modul Runtime .NET core 2.0.0 ve verzi Preview 1 | Modul Runtime .NET core 2.0.0 ve verzi Preview 1                                   |

Může se stát, že verzi sady SDK obsahuje více než jedna verze modulu runtime. Pokud k tomu dojde, instalační program uživatelského prostředí vypadá takto (pouze verze sady SDK se zobrazí a nainstalované verze modulu Runtime se zobrazí na stránce souhrnu na konci procesu instalace pro Windows a Mac):

| Instalační služba | Titulek okna                      | Další obsah v instalačním programu                                   | Co je nainstalována                                                         |
| :--       | :--                               | :--                                                          | :--                                                                       |
| Sada SDK       | Instalační program rozhraní .NET core 2.1 sady SDK (x 64) | .NET core 2.1.1 SDK <br> Modul Runtime .NET core 2.1.1 <br> Modul Runtime .NET core 2.0.6 | Nástroje .NET core 2.1.1 modulu Runtime .NET Core 2.1.1 + modulu Runtime .NET Core 2.0.6 |

Je také možné, že nástroje .NET Core, který je potřeba aktualizovat, bez změny v modulu runtime. V takovém případě verzi sady SDK je zvýšena (například na 2.1.2) a potom modul Runtime až při příštím ji zachytila se dodává (například modul Runtime a sadu SDK dodávat příště jako 2.1.3).

### <a name="package-managers"></a>Správce balíčků

.NET core můžete distribuovat jinými entitami než Microsoft. Konkrétně se vlastníci distribuce Linuxu a programu balíčku může přidat balíčky .NET Core k jejich Správce balíčků. Doporučení na tom, jak by měl být tyto balíčky s názvem a verzí, najdete v tématu [vytváření distribučních balíčků .NET Core](../build/distribution-packaging.md).

#### <a name="minimum-package-set"></a>Minimální balíček sady

* `dotnet-runtime-[major].[minor]`: modul runtime se zadanou verzí (pouze nejnovější verzi opravy pro danou hlavní + dílčí kombinaci by měla být k dispozici ve správci balíčků). Nové verze patch aktualizujte balíček, ale jsou samostatné balíčky nový dílčí nebo hlavní verze.

  **Závislosti**: `dotnet-host`

* `dotnet-sdk`: nejnovější sadu SDK. `update` Zobrazí souhrn po vpřed hlavní, vedlejší verzi a opravy verzí.

  **Závislosti**: nejnovější `dotnet-sdk-[major].[minor]`.

* `dotnet-sdk-[major].[minor]`: Sada SDK se zadanou verzí. Zadaná verze je zahrnuté nejvyšší verzi součástí sdíleného rozhraní, tak, aby uživatelé mohou snadno týkají sady SDK sdílené architektuře. Nové verze patch aktualizujte balíček, ale jsou samostatné balíčky nový dílčí nebo hlavní verze.

  **Závislosti**: `dotnet-host`, jeden nebo více `dotnet-runtime-[major].[minor]` (jeden z nich se používá ve samotný kód sady SDK, ostatní jsou zde uživatelům vytvářet a spouštět proti).

* `dotnet-host`: nejnovější hostitele.

##### <a name="preview-versions"></a>Verze Preview

Balíček programu může rozhodnout zahrnují verze modulu runtime a sadu SDK ve verzi preview. Nevkládejte bez označení verze těchto verzí preview `dotnet-sdk` balíček, ale můžete uvolnit je jako vyvíjených balíčků s značku další ve verzi preview, připojí k hlavní verze a podverze části názvu. Například může existovat `dotnet-sdk-2.0-preview1-final` balíčku.

### <a name="docker"></a>Docker

Obecné Docker tag zásady vytváření názvů, je umístit před název komponenty čísla verze. Tato konvence může i nadále používat. Aktuální značky zahrnují pouze verze modulu Runtime.

* 1.0.8-Runtime
* 1.0.8-sdk
* 2.0.4-runtime
* 2.0.4-sdk
* 2.1.1-Runtime
* 2.1.1-SDK

Značky sady SDK se musí aktualizovat pro reprezentaci verze sady SDK místo modulu Runtime.

Je také možné, že jsou ale reship s existující modul runtime odstranit nástroje .NET Core CLI (je součástí sady SDK). V takovém případě je vyšší verzi sady SDK (například k 2.1.2) a potom modul Runtime až při příštím ji zachytila se dodává (například modul Runtime a sadu SDK dodávat následující čas jako 2.1.3).

## <a name="semantic-versioning"></a>Semantic Versioning

.NET core používá [Semantic Versioning (SemVer)](http://semver.org/), přijetí použití `MAJOR.MINOR.PATCH` správy verzí, pomocí různých částí čísla verze pro popis míry a typ změny.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Volitelný `PRERELEASE` a `BUILDNUMBER` části nikdy jsou součástí podporované verze a existovat pouze na denně automatizovaných buildů, místní sestavení z cíle zdroje a uvolní nepodporované ve verzi preview.

### <a name="how-version-numbers-are-incremented"></a>Jakým způsobem jsou zvětšeny čísla verzí?

`MAJOR` se zvýší, když:

- Starší verze se už nepodporuje.
- Novější `MAJOR` přijaté verze existujícího závislosti.
- Ve výchozím nastavení kompatibility datového toku zvuku nabízí se změní na "off".

`MINOR` se zvýší, když:

- Přidání veřejné svrchní oblasti rozhraní API.
- Přidání nové chování.
- Novější `MINOR` přijaté verze existujícího závislosti.
- Nové závislosti se používá.

`PATCH` se zvýší, když:

- Opravy chyb jsou provedeny.
- Je přidaná podpora pro projekty novější platformy.
- Novější `PATCH` přijaté verze existujícího závislosti.
- Jiné změny nevejde jedním z předchozích případů.

Pokud existuje více změn, nejvyšší prvek ovlivněny změnami v jednotlivých se zvýší, a následující dotazy nastaveny na nulu. Například když `MAJOR` se zvýší, `MINOR` a `PATCH` nastaveny na nulu. Když `MINOR` se zvýší, `PATCH` resetuje na nula při `MAJOR` nedotčené.

### <a name="preview-versions"></a>Verze Preview

Verze Preview `-preview[number]-([build]|"final")` připojenou k verzi. Například `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Údržba verze

Po vydání nedostane mimo větví vydaných verzí obecně stop vytváření denně sestavení a místo zahájení výroby servisní sestavení. Servisní verze mají `-servicing-[number]` připojenou k verzi. Například `2.0.1-servicing-006924`.

### <a name="lts-vs-current"></a>LTS oproti aktuální

Existují dva železniční vydání pro .NET Core: dlouhá období podpory (LTS) a aktuální. Který umožňuje uživatelům vybrat úroveň stability a nové funkce, které se mají při i nadále podporovány.

- LTS znamená, že nové funkce získáte méně často, ale měli vyspělejší platformu. LTS má také do delšího období podpory.
- Aktuální znamená, že máte k dispozici nové funkce a rozhraní API častěji, ale nevýhodou je, že máte na kratší časové instalovat aktualizace a tyto aktualizace okno stane častěji. Aktuálně se podporují i ale období podpory je kratší než LTS.

"Aktuální" verze může získat povýšen na LTS.

"L" a "Aktuální" by měly být považovány popisky, které jsme umístit na konkrétní verze, aby příkaz o přidružená úroveň podpory.

Další informace najdete v tématu [.NET Core podpory životního cyklu fakt list](https://www.microsoft.com/net/core/support).

## <a name="versioning-scheme-details"></a>Podrobnosti o schéma vytváření verzí

.NET core je vytvořen z následujících částí:

- Hostitel: buď *dotnet.exe* závisí na architektuře aplikací, nebo  *\<název_aplikace > .exe* pro samostatné aplikace.
- Sady SDK (sada nástrojů pro potřeby počítače pro vývojáře, ale ne v produkčním prostředí).
- Modul runtime.
- Implementace sdílené architektuře distribuuje jako balíčky. Každý balíček je označené verzí nezávisle na sobě, zejména pro opravy správy verzí.
- Volitelně můžete sadu [metabalíčky](../packages.md) jako celek označené verzí, které odkazují na podrobných balíčky. Metabalíčky může být označené verzí odděleně od balíčků.

.NET core zahrnuje také sadu cílových rozhraní (například `netstandard` nebo `netcoreapp`), které představují postupně větší sady rozhraní API, jako jsou zvětšeny čísla verzí.

### <a name="net-standard"></a>.NET standard

.NET standard používá `MAJOR.MINOR` schéma vytváření verzí. `PATCH` úroveň není užitečná pro .NET Standard, protože představují sadu smluv, které jsou provést iteraci na méně často a není k dispozici stejné požadavky na správu verzí jako skutečná implementace.

Neexistuje žádný skutečný párování mezi verze .NET Standard a .NET Core: .NET Core 2.0 dojde k implementaci rozhraní .NET Standard 2.0, ale neexistuje žádná záruka, že budoucích verzích .NET Core se namapuje na stejnou verzi .NET Standard. .NET core se dají dodávat rozhraní API, která nejsou definovány .NET Standard a v důsledku toho může odeslat nové verze bez nutnosti nový standardní .NET. .NET standard je také koncept se vztahuje na jiné cíle, například rozhraní .NET Framework nebo Mono, i v případě, že se shoduje s .NET Core, došlo k jeho vzniku.

### <a name="packages"></a>Balíčky

Knihovna balíčků vyvíjí a verze nezávisle na sobě. Balíčky, které se překrývají s systém rozhraní .NET Framework. \* sestavení obvykle používají verze 4.x, zarovnání s verzí rozhraní .NET Framework 4.x (historické podle výběru). Balíčky, které se nepřekrývají s knihovnami .NET Framework (například [ `System.Reflection.Metadata` ](https://www.nuget.org/packages/System.Reflection.Metadata)) obvykle začínají 1.0 a zvýší z něj.

Balíčky popsal [ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library) jsou zpracovány speciálně kvůli se základní platformy.

`NETStandard.Library` balíčky se obvykle verzi jako sadu, protože mají úrovni implementace závislosti mezi nimi.

### <a name="metapackages"></a>Metabalíčky

Správa verzí pro .NET Core metabalíčky je založen na verzi .NET Core, které jsou součástí.

Například metabalíčky v .NET Core 2.1.3 by všechny mají 2.1 jako jejich `MAJOR` a `MINOR` čísla verzí.

Verze opravy pro Microsoft.aspnetcore.all se zvýší pokaždé, když se aktualizuje všechny odkazované balíčky. Oprava nezahrnují aktualizované framework verze. V důsledku toho metabalíčky nejsou striktně kompatibilní SemVer vzhledem k tomu, že jejich schéma vytváření verzí nepředstavuje míru změn v podkladové balíčků, ale hlavně o úroveň rozhraní API.

Aktuálně existují dva primární metabalíčky pro .NET Core:

**Microsoft.NETCore.App**

- verze 1.0 k .NET Core 1.0 (tyto verze odpovídá).
- Mapuje `netcoreapp` rozhraní framework.
- Popisuje balíčky v distribuci .NET Core.

Poznámka: [ `Microsoft.NETCore.Portable.Compatibility` ](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) je jiný Microsoft.aspnetcore.all .NET Core, která existuje k zajištění kompatibility s předběžné .NET standardní implementace rozhraní .NET. To není namapován na určité rozhraní, takže ho verze, jako je balíček.

**NETStandard.Library**

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) Popisuje knihoven, které jsou součástí [.NET Standard](../../standard/library.md). Platí pro všechny implementace .NET, které podporují .NET Standard, jako je například rozhraní .NET Framework a .NET Core, Mono.

### <a name="target-frameworks"></a>Cílové architektury

Rozhraní Target framework verze jsou aktualizovány při přidání nového rozhraní API. Mají koncept verzi opravy, protože představují obrazec rozhraní API a ne se týká implementace. Hlavní a dílčí verze následuje pravidla SemVer dříve zadaný a koliduje s `MAJOR` a `MINOR` čísla distribuce .NET Core, které je implementují.

## <a name="versioning-in-practice"></a>Správa verzí v praxi

Když si stáhnete .NET Core, název staženého souboru přenáší verze, například `dotnet-sdk-2.0.4-win10-x64.exe`.

Nejsou potvrzení změn a žádosti o přijetí změn v úložišti .NET Core na Githubu každý den, což vede k nové sestavení mnoho knihoven. Není praktické k vytvoření nových veřejných verzích .NET Core pro každou změnu. Místo toho jsou změny agregován v neurčeném časový úsek (například týdny nebo měsíce) před vytvořením nové veřejné stabilní verzi .NET Core.

Novou verzi .NET Core může znamenat několik věcí:

- Nové verze balíčků a metabalíčky.
- Nové verze různé architektury, za předpokladu, že přidání nových rozhraní API.
- Nová verze dané distribuce .NET Core.

### <a name="shipping-a-patch-release"></a>Přesouvání vydané verzi opravy

Po odeslání hlavní verze .NET Core, jako je například verze 2.0.0, dojde ke změně úroveň opravy na knihovny .NET Core opravovat chyby a zvýšit výkon a spolehlivost. To znamená, že jsou zavedené žádná nová rozhraní API. Různé metabalíčky jsou aktualizovány tak, aby odkazovaly aktualizované balíčků knihovny .NET Core. Jsou opatřeny samostatnými verzemi jako opravy aktualizací metabalíčky (`MAJOR.MINOR.PATCH`). Cílová rozhraní jsou aktualizovány nikdy jako součást aktualizací. Nová distribuce .NET Core je vydáno s číslem verze, která odpovídá `Microsoft.NETCore.App` Microsoft.aspnetcore.all.

### <a name="shipping-a-minor-release"></a>Přesouvání dílčí verze

Po odeslání verzi .NET Core s zvýšena `MAJOR` číslo verze na knihovny .NET Core umožňuje nové scénáře, jako jsou přidali nová rozhraní API. Různé metabalíčky jsou aktualizovány tak, aby odkazovaly aktualizované balíčků knihovny .NET Core. Metabalíčky jsou opatřeny samostatnými verzemi jako aktualizace s `MAJOR` a `MINOR` čísla verze odpovídající novou verzi Frameworku. Nové názvy cílové rozhraní framework s novými `MAJOR.MINOR` verzi jsou přidány k popisu nových rozhraní API (například `netcoreapp2.1`). Nová distribuce .NET Core jsou vydány s odpovídající číslo verze `Microsoft.NETCore.App` Microsoft.aspnetcore.all.

### <a name="shipping-a-major-release"></a>Přesouvání hlavní verze

Pokaždé, když se novou hlavní verzi .NET Core se dodává `MAJOR` získá zvýší číslo verze a `MINOR` získá číslo verze resetuje na nulu. Na novou hlavní verzi obsahuje alespoň všechna rozhraní API, které byly přidány jako vedlejší verze po předchozí hlavní verzi. Novou hlavní verzi by měl povolit důležité nové scénáře a vyřadit ho může také podpora pro starší platformy.

Různé metabalíčky jsou aktualizovány tak, aby odkazovaly aktualizované balíčků knihovny .NET Core. [ `Microsoft.NETCore.App` ](https://www.nuget.org/packages/Microsoft.NETCore.App) Microsoft.aspnetcore.all a `netcore` rozhraní .NET framework jsou opatřeny samostatnými verzemi jako hlavní aktualizace odpovídající `MAJOR` číslo verze novou verzi.

## <a name="see-also"></a>Viz také:

[Cílové verze rozhraní .NET Framework](../../standard/frameworks.md)  
[Vytváření distribučních balíčků .NET Core](../build/distribution-packaging.md)  
[.NET core podpory životního cyklu fakt list](https://www.microsoft.com/net/core/support)  
[Vázání verze rozhraní .NET core 2 +](https://github.com/dotnet/designs/issues/3)  
