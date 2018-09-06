---
title: .NET core migrace na formát csproj
description: .NET core project.json na csproj migrace
author: blackdwarf
ms.author: mairaw
ms.date: 07/19/2017
ms.openlocfilehash: da1995ed3b77cb802d1f3d04e6d741809de20927
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43872429"
---
# <a name="migrating-net-core-projects-to-the-csproj-format"></a>Migrace projektů .NET Core na formát csproj

V tomto dokumentu se týkají scénářů migrace pro projekty .NET Core a půjdou přes následující scénáře migrace tři:

1. [Migrace z platné schéma nejnovější *project.json* k *csproj*](#migration-from-projectjson-to-csproj)
2. [Migrace z DNX na csproj](#migration-from-dnx-to-csproj)
3. [Migrace z předchozích projektů csproj .NET Core a RC3 do konečné](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

## <a name="migration-from-projectjson-to-csproj"></a>Migrace z project.json na csproj

Migrace z *project.json* k *.csproj* lze provést pomocí jedné z následujících metod:

- [Visual Studio 2017](#visual-studio-2017)
- [migrace nástroje příkazového řádku DotNet](#dotnet-migrate)

Obě metody používají stejný základní modul k migraci projektů, takže výsledky budou stejné pro obě. Ve většině případů pomocí jedné z těchto dvou způsobů, jak migrovat *project.json* k *csproj* pouze jednu, která je potřeba a žádné další ruční úpravy souboru projektu je nezbytné. Výsledná *.csproj* soubor bude pojmenován stejně jako obsahující název adresáře.

### <a name="visual-studio-2017"></a>Visual Studio 2017

Při otevření *xproj* soubor nebo řešení, který se odkazuje na soubor *xproj* soubory, **jednosměrnou aktualizaci** se zobrazí dialogové okno. Dialogové okno zobrazuje projekty, které chcete migrovat.
Pokud otevřete soubor řešení, zobrazí se všechny projekty určené v souboru řešení. Zkontrolujte seznam projektů, které chcete migrovat a vyberte **OK**.

![Jednosměrný upgrade dialogové okno se seznamem projekty k migraci](media/one-way-upgrade.jpg)

Visual Studio bude migrovat projekty automaticky vybrána. Při migraci řešení, pokud není možnost všechny projekty, stejné zobrazí se dialogové okno s výzvou k upgradu Zbývající projekty z řešení. Po migraci oznámení o projekt, můžete zobrazit a upravit jeho obsah kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** okno a vyberete **upravit \<název projektu > .csproj**.

Soubory, které se migrovaly (*project.json*, *global.json*, *xproj* a soubor řešení) se přesune do *zálohování* složky. Soubor řešení, která je migrována se upgraduje na Visual Studio 2017 a nebude možné v předchozích verzích sady Visual Studio otevřete soubor řešení.
Soubor s názvem *UpgradeLog.htm* je také uložena a automaticky otevře, která obsahuje sestavu migrace.

> [!IMPORTANT]
> Nové nástroje není k dispozici v sadě Visual Studio 2015, proto nejde migraci vašich projektů pomocí této verze sady Visual Studio.

### <a name="dotnet-migrate"></a>DotNet migrate

Ve scénáři příkazového řádku, můžete použít [ `dotnet migrate` ](../tools/dotnet-migrate.md) příkazu. Se bude migrovat projekt, řešení nebo sadě složek v tomto pořadí, v závislosti na tom, které stojí za nebyly nalezeny.
Při migraci projekt, se migrují projektu a všechny jeho závislosti.

Soubory, které se migrovaly (*project.json*, *global.json* a *xproj*) bude přesunut do *zálohování* složky.

> [!NOTE]
> Pokud používáte Visual Studio Code `dotnet migrate` příkaz nezmění, jako soubory specifické pro Visual Studio Code `tasks.json`. Tyto soubory musí být změněno ručně.
> Toto je hodnota true, pokud používáte Ryder projektu nebo editor nebo integrované vývojové prostředí (IDE) jiné než Visual Studio.

Zobrazit [mapování mezi project.json a csproj vlastnosti](../tools/project-json-to-csproj.md) porovnání project.json a csproj formátů.

### <a name="common-issues"></a>Běžné problémy

- Pokud dojde k chybě: "žádná spustitelný soubor se nenašel odpovídající příkaz dotnet-migrace":

Spustit `dotnet --version` zobrazíte kterou verzi používáte. [`dotnet migrate`](../tools/dotnet-migrate.md) vyžaduje RC3 rozhraní příkazového řádku .NET Core nebo vyšší.
Pokud máte, zobrazí se tato chyba *global.json* soubor v aktuálním nebo nadřazeném adresáři a `sdk` verze je nastaveno na starší verze.

## <a name="migration-from-dnx-to-csproj"></a>Migrace z DNX na csproj

Pokud stále používáte DNX pro vývoj v .NET Core, proces migrace by měl provést ve dvou fázích:

1. Použití [pokyny k migraci existujícího DNX](from-dnx.md) migrace z DNX project-json povolené rozhraní příkazového řádku.
2. Postupujte podle kroků v předchozí části migrace z *project.json* k *.csproj*.  

> [!NOTE]
> DNX stát oficiálně zastaralé během verze Preview 1 z rozhraní příkazového řádku .NET Core.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migrace ze starší formáty souboru csproj .NET Core na verzi RTM csproj

Formát csproj .NET Core byly změny a vyvíjejí s každou novou verzí předběžné verze nástrojů. Neexistuje žádný nástroj, budete migrovat váš soubor projektu z předchozích verzí souboru csproj na nejnovější verzi, takže budete muset ručně upravit soubor projektu. Skutečné postup závisí na verzi souboru projektu, kterou migrujete. Níže uvádíme některé pokyny, které je třeba zvážit podle změn, ke kterým došlo mezi verzemi:

* Odebrat vlastnost verze nástroje z `<Project>` element, pokud existuje.
* Odebrat obor názvů XML (`xmlns`) z `<Project>` elementu.
* Pokud neexistuje, přidejte `Sdk` atribut `<Project>` elementu a nastavte ho na `Microsoft.NET.Sdk` nebo `Microsoft.NET.Sdk.Web`. Tento atribut určuje, že projekt používá sadu SDK má být použit. `Microsoft.NET.Sdk.Web` se používá pro webové aplikace.
* Odeberte `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` a `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` příkazů v horní a dolní část projektu. Import, tyto příkazy jsou odvozené od SDK, takže není nutné, aby se v projektu.
* Pokud máte `Microsoft.NETCore.App` nebo `NETStandard.Library` `<PackageReference>` položky ve vašem projektu, měli byste odebrat je. Odkazy na tyto balíčky jsou [mlčky předpokládané sadou SDK](https://aka.ms/sdkimplicitrefs).
* Odeberte `Microsoft.NET.Sdk` `<PackageReference>` element, pokud existuje. Prochází odkazu sady SDK `Sdk` atribut na `<Project>` elementu.
* Odeberte [globy](https://en.wikipedia.org/wiki/Glob_(programming)) , které jsou [mlčky předpokládané sadou SDK](../tools/csproj.md#default-compilation-includes-in-net-core-projects). Opuštění tyto globy ve vašem projektu způsobí chybu sestavení vzhledem k tomu, že bude duplikovat položky kompilace.

Po provedení těchto kroků by měl být váš projekt plně kompatibilní s formátem souboru csproj RTM .NET Core.

Příklady před a po dokončení migrace ze starého formátu csproj do nové, najdete v článku [aktualizace sady Visual Studio 2017 RC – vylepšení nástrojů .NET Core](https://blogs.msdn.microsoft.com/dotnet/2016/12/12/updating-visual-studio-2017-rc-net-core-tooling-improvements/) článek na blogu .NET.

## <a name="see-also"></a>Viz také:

- [Přenos, migrace a Upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
