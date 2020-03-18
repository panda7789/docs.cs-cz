---
title: Migrace jádra .NET z souboru project.json
description: Zjistěte, jak migrovat starší projekt .NET Core pomocí souboru project.json
ms.date: 07/19/2017
ms.openlocfilehash: 8a9dc05c82fd5476a70ee36a294a287abbfb68c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77450684"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>Migrace základních projektů .NET z aplikace project.json

Tento dokument popisuje následující tři scénáře migrace pro projekty .NET Core:

1. [Migrace z platného nejnovějšího schématu *project.json* na *csproj*](#migration-from-projectjson-to-csproj)
2. [Migrace z DNX na csproj](#migration-from-dnx-to-csproj)
3. [Přechod z RC3 a předchozích projektů .NET Core csproj do konečného formátu](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

Tento dokument je použitelný pouze pro starší projekty .NET Core, které používají project.json. Nevztahuje se na migraci z rozhraní .NET Framework na .NET Core.

## <a name="migration-from-projectjson-to-csproj"></a>Migrace z project.json na csproj

Přechod z *project.json* na *.csproj* lze provést pomocí jedné z následujících metod:

- [Visual Studio](#visual-studio)
- [nástroj příkazového řádku dotnet migrate](#dotnet-migrate)

Obě metody používají stejný základní modul pro migraci projektů, takže výsledky budou stejné pro oba. Ve většině případů pomocí jednoho z těchto dvou způsobů migrace *project.json* na *csproj* je jediná věc, která je potřeba, a žádné další ruční úpravy souboru projektu je nutné. Výsledný soubor *.csproj* bude pojmenován stejně jako obsahující název adresáře.

### <a name="visual-studio"></a>Visual Studio

Když otevřete soubor *.xproj* nebo soubor řešení, který odkazuje na soubory *.xproj* v sadě Visual Studio 2017 nebo Visual Studio 2019 verze 16.2 a starší, zobrazí se dialogové okno **jednosměrného upgradu.** V dialogovém okně se zobrazí projekty, které mají být migrovány. Pokud otevřete soubor řešení, jsou uvedeny všechny projekty zadané v souboru řešení. Zkontrolujte seznam projektů, které mají být migrovány, a vyberte **ok**.

![Dialogové okno jednosměrného upgradu se seznamem projektů, které mají být migrovány](media/one-way-upgrade.jpg)

Visual Studio migruje vybrané projekty automaticky. Při migraci řešení, pokud nevyberete všechny projekty, se zobrazí stejné dialogové okno s žádostí o upgrade zbývajících projektů z tohoto řešení. Po migraci projektu můžete zobrazit a upravit jeho obsah klepnutím pravým tlačítkem myši na projekt v okně **Průzkumník řešení** a výběrem **možnosti Upravit \<název projektu>.csproj**.

Přenesené soubory *(project.json*, *global.json*, *.xproj*a soubor řešení) jsou *přesunuty* do složky Backup. Soubor přeneseného řešení se upgraduje na Visual Studio 2017 nebo Visual Studio 2019 a tento soubor řešení nebudete moct otevřít v visual tase 2015 nebo starších verzích. Soubor s názvem *UpgradeLog.htm,* který obsahuje sestavu migrace je také uložen a otevřen automaticky.

> [!IMPORTANT]
> Ve Visual Studiu 2019 verze 16.3 a novějších nelze načíst nebo migrovat soubor *.xproj.* Visual Studio 2015 navíc neposkytuje možnost migrace souboru *.xproj.* Pokud používáte některou z těchto verzí sady Visual Studio, nainstalujte vhodnou verzi sady Visual Studio nebo použijte nástroj pro migraci příkazového řádku, který je popsán dále.

### <a name="dotnet-migrate"></a>dotnet migrate

Ve scénáři příkazového řádku můžete [`dotnet migrate`](../tools/dotnet-migrate.md) použít příkaz. Migruje projekt, řešení nebo sadu složek v tomto pořadí, v závislosti na tom, které byly nalezeny. Při migraci projektu se migruje projekt a všechny jeho závislosti.

Přenesené soubory *(project.json*, *global.json*a *.xproj*) jsou přesunuty do *záložní* složky.

> [!NOTE]
> Pokud používáte visual studio `dotnet migrate` kód, příkaz nemění Soubory specifické pro kód sady Visual Studio, jako je *například tasks.json*. Tyto soubory je třeba změnit ručně.
> To platí také, pokud používáte editor nebo integrované vývojové prostředí (IDE) než Visual Studio.

Porovnání formátů *project.json* a *.csproj* naleznete v [tématu Mapování mezi vlastnostmi project.json a csproj.](../tools/project-json-to-csproj.md)

Pokud se zobrazí chyba:

> Nebyl nalezen žádný spustitelný soubor odpovídající příkaz dotnet-migrate

Spuštěním `dotnet --version` zobrazíte, kterou verzi používáte. [`dotnet migrate`](../tools/dotnet-migrate.md)byl zaveden v .NET Core SDK 1.0.0 a odebrán ve verzi 3.0.100.
Tato chyba se zobrazí, pokud máte soubor *global.json* v aktuálním `sdk` nebo nadřazeném adresáři a verze, kterou určuje, je mimo tento rozsah.

## <a name="migration-from-dnx-to-csproj"></a>Migrace z DNX na csproj

Pokud stále používáte DNX pro vývoj jádra .NET, proces migrace by měl být proveden ve dvou fázích:

1. Pomocí [existujících pokynů pro migraci DNX](from-dnx.md) migrujte z rozhraní cli s podporou projektu-json.
2. Podle pokynů z předchozí části migrujte z *souboru project.json* na *soubor .csproj*.

> [!NOTE]
> DNX se stala oficiálně zastaralé během verze Preview 1 rozhraní CLI .NET Core.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migrace z dřívějších formátů csproj .NET Core do RTM csproj

Formát .NET Core csproj se mění a vyvíjí s každou novou předběžnou verzí nástroje. Neexistuje žádný nástroj, který bude migrovat soubor projektu z dřívějších verzí csproj na nejnovější, takže je třeba ručně upravit soubor projektu. Skutečné kroky závisí na verzi souboru projektu, který migrujete. Následuje některé pokyny, které je třeba zvážit na základě změn, ke kterým došlo mezi verzemi:

- Odeberte vlastnost verze `<Project>` nástrojů z prvku, pokud existuje.
- Odeberte z`xmlns`elementu `<Project>` obor názvů XML ( ).
- Pokud neexistuje, přidejte `Sdk` atribut do `<Project>` prvku a nastavte `Microsoft.NET.Sdk` `Microsoft.NET.Sdk.Web`jej na nebo . Tento atribut určuje, že projekt používá sadu SDK, která má být použita. `Microsoft.NET.Sdk.Web`se používá pro webové aplikace.
- Odeberte příkazy `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` a `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` z horní a dolní části projektu. Tyto příkazy importu jsou implicitní sadou SDK, takže není nutné, aby byly v projektu.
- Pokud máte `Microsoft.NETCore.App` `NETStandard.Library` `<PackageReference>` nebo položky v projektu, měli byste je odebrat. Tyto odkazy na balíček jsou [implikovány sadou SDK](https://aka.ms/sdkimplicitrefs).
- `Microsoft.NET.Sdk` `<PackageReference>` Odeberte prvek, pokud existuje. Odkaz sady SDK `Sdk` prochází atributem na `<Project>` prvku.
- Odeberte [globs,](https://en.wikipedia.org/wiki/Glob_(programming)) které jsou [implikovány sadou SDK](../project-sdk/overview.md#default-compilation-includes). Ponechání těchto globs v projektu způsobí chybu na sestavení, protože kompilace položky budou duplikovány.

Po těchto krocích by měl být projekt plně kompatibilní s formátem CSProJ RTM .NET Core.

Příklady před a po migraci ze starého formátu csproj do nového, naleznete [v aktualizaci Visual Studio 2017 RC – .NET Core Tooling vylepšení](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) článku na blogu .NET.

## <a name="see-also"></a>Viz také

- [Port, migrace a upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
