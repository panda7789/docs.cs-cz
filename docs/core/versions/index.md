---
title: Správa verzí .NET core
description: Pochopit, jak funguje správa verzí .NET Core.
author: bleroy
ms.author: mairaw
ms.date: 02/13/2018
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f6f684b1-1d2c-4105-8376-7c1959e23803
ms.workload:
- dotnetcore
ms.openlocfilehash: 70c7f179f3451e51d5ab383cde80959a69f959a1
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2018
---
# <a name="net-core-versioning"></a>Správa verzí .NET core

.NET core je tvořen [balíčky NuGet](../packages.md), nástroje a rozhraní, které jsou distribuovány jako jednotku. Každý z těchto úrovní platformy může obsahovat verzí samostatně, povolení vyšší flexibility. Zatímco v tomto ohledu je flexibilitu významné Správa verzí, je zde také pádem si chtít verze platformy jako jednotku, kterou chcete snadněji pochopili produktu.

Tento článek zaměřuje na určující, jak jsou verzí rozhraní .NET Core SDK a modulu runtime.

Neobsahuje velké množství přesunutí části této verze nezávisle .NET Core. Od verze rozhraní .NET Core 2.0, je však snadno pochopit číslo verze nejvyšší úrovně, které každý uživatel rozumí být *verzi* ".NET Core" jako celek. Zbytek tohoto dokumentu přejde na podrobné informace o Správa verzí všech těchto částí. Tyto podrobnosti může být důležité, pokud jste správce balíčků, například.

> [!IMPORTANT]
> Správa verzí podrobnosti popsané v tomto tématu se nevztahují na aktuální verzi rozhraní .NET Core SDK a modulu runtime.
> Verze schématu se mění v budoucích verzích. Zobrazí aktuální návrh na [dotnet nebo návrhy](https://github.com/dotnet/designs/pull/29) úložiště.

## <a name="versioning-details"></a>Správa verzí podrobnosti

Stahování s .NET Core 2.0, zobrazit číslo jedné verze v názvu souboru. Byly unified následující čísla verzí:

* Sdílený framework a přidružené runtime.
* .NET Core SDK a přidružené rozhraní .NET Core CLI.
* `Microsoft.NETCore.App` Metapackage.

Použití číslo díky jedna verze, což usnadňuje uživatelům vědět, jaká verze sady SDK k instalaci na jejich počítačích vývojářů a jaké odpovídající verzi systému sdílený framework by měla být pokud nastane čas zřídit provozním prostředí. Při stahování sady SDK nebo modul runtime, číslo verze, které vidíte se bude shodovat.

### <a name="installers"></a>Instalační programy

Pomocí rozhraní .NET 2.0 jádra, soubory ke stažení pro [denně sestavení](https://github.com/dotnet/core-setup#daily-builds) a [uvolní](https://www.microsoft.com/net/download/core) dodržovat nové schéma pojmenování je srozumitelnější.
Instalační program uživatelského rozhraní v těchto souborů ke stažení se také upravit tak, aby jasně prezentovat názvy a verze instalovaných komponent. Konkrétně titulů zobrazují stejné číslo verze, která je v názvu souboru ke stažení.

#### <a name="file-name-format"></a>Formát názvu souboru

`[product]-[component]-[major].[minor].[patch]-[previewN]-[optional build #]-[rid].[file ext]`

Tady jsou některé příklady tento formát:

```
dotnet-runtime-2.0.4-macos.10.12-x64.pkg            # Mac runtime installer
dotnet-sdk-2.0.4-win10-x64.exe                      # Windows SDK installer
dotnet-sdk-2.0.4-fedora.24-x64.tar.gz               # Fedora 24 binary archive

#Ubuntu file set needed for the SDK
dotnet-host-2.0.4-ubuntu.16.04-x64.deb              # Host / muxer and host policy
dotnet-runtime-2.0.4-ubuntu.16.04-x64.deb           # runtime
dotnet-sdk-2.0.4-ubuntu.16.04-x64.deb               # SDK tools
```

Formát je čitelná a zřetelně zobrazí, co jste stahování, jaká verze je a kde můžete použít. Název balíčku runtime zahrnuje `runtime`, a sada SDK zahrnuje `SDK`.

#### <a name="ui-string-format"></a>Formát řetězce uživatelského rozhraní

Všechny popisy webu a řetězce uživatelského rozhraní v instalačních programů jsou uchovány konzistentní, přesnost a jednoduchý. V následující tabulce jsou uvedeny některé příklady:

| Instalační služba | Název okna                          | Další obsah v instalační program | Co je nainstalována                               |
| :--       | :--                                   | :--                        | :--                                             |
| Sada SDK       | Instalační program rozhraní .NET core 2.0 sady SDK (x 64)     | .NET Core 2.0.4 SDK        | .NET core verze 2.0.4 nástroje + .NET Core verze 2.0.4 Runtime |
| Modul runtime   | Instalačního programu .NET core 2.0 Runtime (x64) | Základní verze 2.0.4 Runtime rozhraní .NET    | Základní verze 2.0.4 Runtime rozhraní .NET                         |

Verze Preview se liší pouze mírně:

| Instalační služba | Název okna                                    | Další obsah v instalační program        | Co je nainstalována                                                   |
| :--       | :--                                             | :--                               | :--                                                                 |
| Sada SDK       | Instalační program sady SDK (x 64) .NET core 2.0 Preview 1     | .NET core 2.0.0 Preview 1 SDK     | .NET core 2.0.0 Preview 1 nástroje + .NET Core 2.0.0 Preview 1 Runtime |
| Modul runtime   | Instalační program rozhraní .NET core 2.0 Preview 1 Runtime (x64) | .NET core 2.0.0 Preview 1 Runtime | .NET core 2.0.0 Preview 1 Runtime                                   |

Může se stát, že vydání sady SDK obsahuje více než jednu verzi modulu runtime. Pokud k tomu dojde, instalační program UX vypadá takto (pouze verze sady SDK se zobrazí a nainstalovaná verze modulu Runtime jsou zobrazeny na souhrnné stránce na konci procesu instalace v systému Windows a Mac):

| Instalační služba | Název okna                      | Další obsah v instalační program                                   | Co je nainstalována                                                         |
| :--       | :--                               | :--                                                          | :--                                                                       |
| Sada SDK       | Instalační program rozhraní .NET core 2.1 sady SDK (x 64) | .NET core 2.1.1 SDK <br> .NET core 2.1.1 Runtime <br> .NET core 2.0.6 Runtime | .NET core 2.1.1 nástroje + .NET Core 2.1.1 Runtime + .NET Core 2.0.6 Runtime |

Je také možné, že je třeba aktualizovat, bez změny v modulu runtime .NET Core nástroje. V takovém případě verze sady SDK je zvýšena (například na 2.1.2) a pak modulu Runtime zachytí další chvíli trvat, než ho se dodává (například modul Runtime a SDK dodávat příštím jako 2.1.3).

### <a name="package-managers"></a>Správce balíčků

.NET core lze distribuovat pomocí jiné entity než Microsoft. Konkrétně Linux distribuční vlastníci a údržby balíček programu může přidat balíčky .NET Core jejich správce balíčku. Doporučení na tom, jak tyto balíčky by měl být s názvem a verzí, naleznete v tématu [.NET Core distribuční balení](../build/distribution-packaging.md).

#### <a name="minimum-package-set"></a>Minimální balíčku sady

* `dotnet-runtime-[major].[minor]`: runtime se zadanou verzí (pouze nejnovější verzi oprav pro danou hlavní + menší kombinaci by měl být k dispozici v Správce balíčků). Nové verze oprava aktualizovat balíček, ale nové menší nebo hlavní verze jsou samostatné balíčky.

  **Závislosti**: `dotnet-host`

* `dotnet-sdk`: nejnovější sadu SDK. `update` Zobrazí souhrn předání hlavní, vedlejší verzi a oprava verze.

  **Závislosti**: nejnovější `dotnet-sdk-[major].[minor]`.

* `dotnet-sdk-[major].[minor]`: Sada SDK se zadanou verzí. Verze zadaná je nejvyšší verze součástí zahrnuty sdílené rozhraní, tak, aby uživatelé můžete snadno týkají sady SDK sdílený framework. Nové verze oprava aktualizovat balíček, ale nové menší nebo hlavní verze jsou samostatné balíčky.

  **Závislosti**: `dotnet-host`, jeden nebo více `dotnet-runtime-[major].[minor]` (jeden z nich se používá ve samotný kód SDK, jiné jsou zde uživatelům sestavení a spuštění).

* `dotnet-host`: nejnovější hostitele.

##### <a name="preview-versions"></a>Verze Preview

Balíček pracovníků programu rozhodnout pro zahrnují verze preview runtime a sady SDK. Zahrnutí těchto verzí preview bez uvedené verze `dotnet-sdk` balíček, ale můžete je uvolněte jako verzí balíčků pomocí další preview připojí k hlavní verze a podverze části názvu. Například může existovat `dotnet-sdk-2.0-preview1-final` balíčku.

### <a name="docker"></a>Docker

Obecné zásady vytváření názvů značku Docker je umístit číslo verze před název součásti. Dále je možné využít touto konvencí. Aktuální značky se týkají pouze verze modulu Runtime následujícím způsobem.

* 1.0.8-Runtime
* 1.0.8-sdk
* 2.0.4-runtime
* 2.0.4-sdk
* 2.1.1-Runtime
* 2.1.1-sdk

Značky SDK je třeba aktualizovat představují verze sady SDK místo modulu Runtime.

Je také možné, ale reship s existující runtime opravené nástroje příkazového řádku .NET Core (zahrnutý v sadě SDK). V takovém případě je vyšší verze sady SDK (například k 2.1.2) a pak modulu Runtime zachytí další chvíli trvat, než ho se dodává (například modul Runtime a SDK dodávat tento čas jako 2.1.3).

## <a name="semantic-versioning"></a>Sémantické verze

.NET core používá [sémantické verze (SemVer)](http://semver.org/), přijetí použití `MAJOR.MINOR.PATCH` Správa verzí, popsat úroveň a typ změny pomocí různých částí číslo verze.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Volitelné `PRERELEASE` a `BUILDNUMBER` částí nikdy jsou součástí podporovaných verzích a existovat pouze na noční sestavení, místní sestavení ze zdroje cílů a uvolní nepodporovanou verzi preview.

### <a name="how-version-numbers-are-incremented"></a>Jak se zvýší číslo verze?

`MAJOR` se zvýší, když:

- Stará verze už není podporovaná.
- Novější `MAJOR` je přijali verzi existující závislosti.
- Výchozí nastavení kompatibility datového toku zvuku v nabízí se změní na "off".

`MINOR` se zvýší, když:

- Přidání útoku na veřejné rozhraní API.
- Přidá nové chování.
- Novější `MINOR` je přijali verzi existující závislosti.
- Zavádí nové závislosti.

`PATCH` se zvýší, když:

- Opravy chyb jsou vytvářeny.
- Je přidána podpora pro novější platformu.
- Novější `PATCH` je přijali verzi existující závislosti.
- Všechny ostatní změny nevejde jeden z předchozích případech.

Pokud existuje více změn, nejvyšší element vliv na jednotlivé změny se zvýší, a následující těm, které jsou nastaveny na nulu. Například když `MAJOR` se zvýší, `MINOR` a `PATCH` nastaveny na nulu. Když `MINOR` se zvýší, `PATCH` obnoví nulové chvíli `MAJOR` nedotčené.

### <a name="preview-versions"></a>Verze Preview

Verze Preview mají `-preview[number]-([build]|"final")` připojenou k verzi. Například `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Obsluhy verze

Po vydání nedostane mimo verzi větve obecně zastavení generovala denně sestavení a místo toho spusťte generovala údržby sestavení. Obsluhy verze mají `-servicing-[number]` připojenou k verzi. Například `2.0.1-servicing-006924`.

### <a name="lts-vs-current"></a>LTS oproti aktuální

Existují dvě vlaky verzí pro .NET Core: podpora dlouho termín (LTS) a aktuální. Který umožňuje uživatelům vybrat úroveň stability a nové funkce, které chtějí při stále není podporována.

- LTS znamená méně často získat nové funkce, ale máte víc vyspělých platformy. LTS má také delší době podpory.
- Aktuální znamená častěji získat nové funkce a rozhraní API, ale nevýhodou je, že máte okno kratší dobu instalaci aktualizací a tyto aktualizace dojít častěji. Aktuální také plně podporované, ale je kratší než LTS období podpory.

"Aktuální" verze může získat povýšen na LTS.

"LTS" a "Aktuální" by měly být považovány štítků, které jsme umístí konkrétní verze, aby prohlášení o úroveň přidružené podpory.

Další informace najdete v tématu [.NET Core podporu životního cyklu fakt list](https://www.microsoft.com/net/core/support).

## <a name="versioning-scheme-details"></a>Správa verzí schéma podrobnosti

.NET core se provádí z následujících částí:

- Hostitel: buď *dotnet.exe* pro framework závislé aplikace, nebo  *\<appname > .exe* pro samostatné aplikace.
- SDK (sada nástrojů pro potřeby na počítači pro vývojáře, ale ne v produkčním prostředí).
- Runtime.
- Implementace sdílený framework distribuovaných jako balíčky. Každý balíček je verzí nezávisle, hlavně pro správu verzí opravy.
- Volitelně můžete sadu [metapackages](../packages.md) které se odkazují podrobných balíčky jako verzí jednotku. Metapackages může být odděleně od balíčky verzí.

.NET core také obsahuje sadu cílové rozhraní (například `netstandard` nebo `netcoreapp`) progresivně větší sada rozhraní API, které představují jako se zvýší číslo verze.

### <a name="net-standard"></a>Standardní rozhraní .NET

.NET standard používá `MAJOR.MINOR` schéma správy verzí. `PATCH` úroveň není užitečné pro .NET Standard, protože ho představují sadu smluv, které jsou vstupní na méně často a není k dispozici stejné požadavky pro správu verzí jako skutečný implementace.

Neexistuje žádné skutečné párování mezi .NET Standard verze a verze .NET Core: implementace rozhraní .NET 2.0 standardní se stane rozhraní .NET 2.0 jádra, ale neexistuje žádná záruka, která bude na stejnou verzi rozhraní .NET standardní mapování budoucích verzích .NET Core. .NET core se dají dodávat rozhraní API, které nejsou definované .NET Standard a jako takový může dodávat nové verze bez nutnosti nového Standard .NET. .NET standard je také konceptu, které se vztahují na jiné cíle, jako je rozhraní .NET Framework nebo Mono, i v případě, že došlo k jeho zahájení se shoduje s s .NET Core.

### <a name="packages"></a>Balíčky

Knihovna balíčky momentální a verze nezávisle. Balíčky, které se překrývají s systém .NET Framework. \* sestavení obvykle používají verze 4.x, volbě vhodného Správa verzí rozhraní .NET Framework 4.x (historických volba). Balíčky, které se nepřekrývají s knihovnami .NET Framework (například [ `System.Reflection.Metadata` ](https://www.nuget.org/packages/System.Reflection.Metadata)) obvykle spuštění na 1.0 a zvýšit odtud.

Balíčky popsaného [ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library) jsou považovány speciálně, protože nejsou v základní platformy.

`NETStandard.Library` balíčky se obvykle verze jako sada, protože mají úrovni implementace závislosti mezi nimi.

### <a name="metapackages"></a>Metapackages

Správa verzí pro .NET Core metapackages je založen na verzi .NET Core, které jsou součástí.

Například metapackages v .NET Core 2.1.3 by všechny mít 2.1 jako jejich `MAJOR` a `MINOR` čísla verzí.

Pokaždé, když jsou aktualizovány všechny odkazované balíčky, zvýší se verze opravy pro metapackage. Oprava verze neobsahují ve verzi aktualizované framework. V důsledku toho metapackages nejsou striktně kompatibilní se standardem SemVer protože jejich verze schématu nepředstavuje stupeň změny v základní balíčků, ale hlavně úrovně rozhraní API.

Aktuálně existují dvě primární metapackages pro .NET Core:

**Microsoft.NETCore.App**

- od verze rozhraní .NET Core 1.0 (tyto verze odpovídat) verze 1.0.
- Se mapuje `netcoreapp` framework.
- Popisuje balíčky v distribuci .NET Core.

Poznámka: [ `Microsoft.NETCore.Portable.Compatibility` ](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) je jiný metapackage .NET Core, který již existuje, chcete-li povolit kompatibilitu s předběžné .NET standardní implementace rozhraní .NET. Ji není namapován na konkrétní rozhraní, takže ji jako balíček verze.

**NETStandard.Library**

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) Popisuje knihovny, které jsou součástí [.NET Standard](../../standard/library.md). Platí pro všechny implementace rozhraní .NET, které podporují Standard .NET, například rozhraní .NET Framework, .NET Core a Mono.

### <a name="target-frameworks"></a>Cílové rozhraní

Target framework verze jsou aktualizovány při přidání nového rozhraní API. Nemají žádné konceptu opravu verze, vzhledem k tomu, že představují tvar rozhraní API a není implementace aspekty. Správa verzí pro hlavní a podverze dodržuje pravidla SemVer dříve zadaný a se shoduje s `MAJOR` a `MINOR` čísla .NET Core distribuce, které je provede.

## <a name="versioning-in-practice"></a>Správa verzí v praxi

Když si stáhnete .NET Core, název stažený soubor představuje verze, například `dotnet-sdk-2.0.4-win10-x64.exe`.

Existují potvrzení a vyžadování požadavkům na .NET Core úložiště na webu GitHub na každý den, což vede k nové sestavení mnoho knihoven. Není potřeba vytvářet nové veřejné verze .NET Core pro každé změně. Místo toho jsou změny agregován v neurčeném časový úsek (například týdny nebo měsíce) před provedením nové veřejné stabilní verze .NET Core.

Nová verze .NET Core by mohly znamenat několik věcí:

- Nové verze balíčků a metapackages.
- Nové verze různých rozhraní, za předpokladu, že přidání nových rozhraní API.
- Nová verze rozdělení .NET Core.

### <a name="shipping-a-patch-release"></a>Přesouvání vydání opravy

Po přesouvání hlavní verzi .NET Core, jako je například verze 2.0.0, úroveň oprav změn do knihoven .NET Core, opravte chyby a zlepšení výkonu a spolehlivosti. To znamená, že byly zavedeny žádné nové rozhraní API. Různé metapackages jsou aktualizovány tak, aby odkazovaly aktualizované balíčky knihovny .NET Core. Jsou verzí jako opravy aktualizací metapackages (`MAJOR.MINOR.PATCH`). Cílové rozhraní jsou aktualizovány nikdy jako součást vydání opravy. Nová distribuce .NET Core vydání s číslem verze, která se shoduje s `Microsoft.NETCore.App` metapackage.

### <a name="shipping-a-minor-release"></a>Přesouvání vedlejší verze

Po přesouvání verzi .NET Core s zvýšena `MAJOR` číslo verze nových rozhraní API jsou přidány do knihovny .NET Core povolit nové scénáře. Různé metapackages jsou aktualizovány tak, aby odkazovaly aktualizované balíčky knihovny .NET Core. Metapackages jsou verzí jako opravy aktualizace s `MAJOR` a `MINOR` čísla verzí odpovídající novou verzi. Nové názvy cílový framework s novým `MAJOR.MINOR` verzi jsou přidány k popisu nových rozhraní API (například `netcoreapp2.1`). Nová distribuce .NET Core vydání s odpovídající číslo verze `Microsoft.NETCore.App` metapackage.

### <a name="shipping-a-major-release"></a>Přesouvání hlavní verze

Pokaždé, když se dodává novou hlavní verzi .NET Core, `MAJOR` získá zvýší číslo verze a `MINOR` číslo verze získá nastaven na hodnotu nula. Nový hlavní verzi obsahuje alespoň všechna rozhraní API, které byly přidány jako vedlejší verze po předchozí hlavní verzi. Nový hlavní verzi by měl povolit důležité nové scénáře, a může ho také vyřadit podpora pro starší platformy.

Různé metapackages jsou aktualizovány tak, aby odkazovaly aktualizované balíčky knihovny .NET Core. [ `Microsoft.NETCore.App` ](https://www.nuget.org/packages/Microsoft.NETCore.App) Metapackage a `netcore` cílové rozhraní jsou verzí jako hlavní aktualizace odpovídající `MAJOR` číslo verze nové verze.

## <a name="see-also"></a>Viz také

[Cílové verze rozhraní .NET Framework](../../standard/frameworks.md)  
[Vytváření distribučních balíčků .NET Core](../build/distribution-packaging.md)  
[List fakt životního cyklu podpory základní rozhraní .NET](https://www.microsoft.com/net/core/support)  
[.NET core 2 + verze vazby](https://github.com/dotnet/designs/issues/3)  
