---
title: .NET core migrace do formátu csproj
description: .NET core project.json csproj migrace
author: blackdwarf
ms.author: mairaw
ms.date: 07/19/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 102b875072ed77a328bdb6a62ed6cc98612ff059
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="migrating-net-core-projects-to-the-csproj-format"></a>Migrace .NET Core projekty do formátu .csproj

Tento dokument popisuje scénáře migrace pro projekty .NET Core a budou přenášeny po následující tři migrační scénáře:

1. [Migrace z platné schéma nejnovější *project.json* k *csproj*](#migration-from-projectjson-to-csproj)
2. [Migrace ze DNX csproj](#migration-from-dnx-to-csproj)
3. [Migrace z RC3 a předchozí .NET Core csproj projekty do konečné podoby](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

## <a name="migration-from-projectjson-to-csproj"></a>Migrace ze souboru project.json csproj
Migrace z *project.json* k *.csproj* lze provést pomocí jedné z následujících metod:

- [Visual Studio 2017](#visual-studio-2017)
- [Nástroj příkazového řádku migrovat DotNet.](#dotnet-migrate)
 
Obě metody používají stejný základní modul k migraci projektů, takže výsledky budou stejné pro. Ve většině případů pomocí jedné z těchto dva způsoby, jak migrovat *project.json* k *csproj* je jediné, co je potřeba a žádné další ruční úpravy souboru projektu je nezbytné. Výsledná *.csproj* soubor bude mít název stejný jako název obsahujícího adresáře.

### <a name="visual-studio-2017"></a>Visual Studio 2017

Při otevření *.xproj* soubor nebo soubor, který odkazuje na řešení *.xproj* soubory, **jednosměrný upgrade** otevře se dialogové okno. Dialogové okno zobrazí projekty, které chcete migrovat. Pokud otevřete soubor řešení, objeví se všechny projekty zadaný v souboru řešení. Zkontrolujte seznam projektů, které chcete migrovat a vyberte **OK**.

![Jednosměrné upgradu dialogové okno zobrazující seznam projektů, které chcete migrovat](media/one-way-upgrade.jpg)

Visual Studio bude migrovat projektech vybraných automaticky. Při migraci řešení, když nebude všechny projekty, stejnou zobrazí se dialogové okno s dotazem, můžete upgradovat Zbývající projekty z tohoto řešení. Po migraci projektu, můžete zobrazit a upravit její obsah kliknutím pravým tlačítkem myši na projekt v **Průzkumníku řešení** okno a vybrat **upravit \<název projektu > .csproj**.

Soubory, které byly migrovány (*project.json*, *global.json*, *.xproj* a soubor řešení) bude přesunut do *zálohování* složky. Soubor řešení, která je migrována bude upgradována na Visual Studio 2017 a nebudete moct otevřít tento soubor řešení v předchozích verzích sady Visual Studio. Soubor s názvem *UpgradeLog.htm* je také uložena a automaticky otevře obsahující sestavu migraci.

> [!IMPORTANT]
> Nové nástrojů není k dispozici v sadě Visual Studio 2015, proto nelze provést migraci vašich projektů pomocí této verze sady Visual Studio.

### <a name="dotnet-migrate"></a>migrace DotNet.

Ve scénáři, příkazového řádku, můžete použít [ `dotnet migrate` ](../tools/dotnet-migrate.md) příkaz. Jeho bude migrovat na projekt, řešení nebo sadu složek v tomto pořadí, v závislosti na ty, které nebyly nalezeny. Když provádíte migraci projektu, se migrují projekt a všechny jeho závislé součásti.

Soubory, které byly migrovány (*project.json*, *global.json* a *.xproj*) bude přesunut do *zálohování* složky.

> [!NOTE]
> Pokud používáte Visual Studio Code `dotnet migrate` příkaz nezmění, jako soubory specifické pro Visual Studio Code `tasks.json`. Tyto soubory musí ručně změnit. Toto je hodnota true, pokud používáte Ryder projektu nebo libovolný editor nebo integrované vývojové prostředí (IDE) jiné než Visual Studio. 

V tématu [mapování mezi project.json a csproj vlastnosti](../tools/project-json-to-csproj.md) porovnání project.json a csproj formáty.

### <a name="common-issues"></a>Běžné problémy

- Pokud dojde k chybě: "žádný spustitelný soubor nalezen odpovídající příkaz dotnet-migrovat":

Spustit `dotnet --version` zobrazíte kterou verzi, kterou používáte. [`dotnet migrate`](../tools/dotnet-migrate.md) vyžaduje rozhraní .NET Core rozhraní příkazového řádku RC3 nebo vyšší.
Budete se tato chyba, pokud máte *global.json* souboru v aktuální nebo nadřazený adresář a `sdk` verze je nastaveno na starší verze.

## <a name="migration-from-dnx-to-csproj"></a>Migrace ze DNX csproj
Pokud stále používáte DNX pro vývoj .NET Core, procesu migrace je potřeba ve dvou fázích:

1. Použití [existující pokyny pro migraci DNX](from-dnx.md) při migraci z DNX do projektu json povolené rozhraní příkazového řádku.
2. Postupujte podle pokynů z předchozí části k migraci z *project.json* k *.csproj*.  

> [!NOTE]
> DNX se oficiálně nepoužívá během Preview 1 verzi rozhraní příkazového řádku .NET Core. 

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migrace ze starších formátech csproj .NET Core RTM csproj
Formát csproj .NET Core je změna a vyvíjející se každý nový předběžné verze nástrojů. Neexistuje žádný nástroj, který bude migrovat souboru projektu z dřívějších verzí csproj nejnovější, proto musíte ručně upravit soubor projektu. Skutečné kroky závisí na verzi souboru projektu, který migrujete. Toto je některé pokyny, které je třeba zvážit podle změny, které došlo mezi verzemi:

* Odeberte vlastnost verze nástroje pro z `<Project>` elementu, pokud existuje. 
* Odebrat obor názvů XML (`xmlns`) z `<Project>` elementu.
* Pokud neexistuje, přidejte `Sdk` atribut `<Project>` elementu a nastavte ji na `Microsoft.NET.Sdk` nebo `Microsoft.NET.Sdk.Web`. Tento atribut určuje, že projektu používá sady SDK k použití. `Microsoft.NET.Sdk.Web` používá se pro webové aplikace.
* Odeberte `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` a `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` příkazy z horní a dolní projektu. Import, tyto příkazy jsou implicitní sadou SDK, takže není nutné, aby se v projektu. 
* Pokud máte `Microsoft.NETCore.App` nebo `NETStandard.Library` `<PackageReference>` položek ve vašem projektu, odstraňte je. Tyto odkazy balíčku jsou [implicitní SDK](https://aka.ms/sdkimplicitrefs). 
* Odeberte `Microsoft.NET.Sdk` `<PackageReference>` elementu, pokud existuje. Odkaz na sadu SDK přicházejí `Sdk` atributu u `<Project>` elementu. 
* Odeberte [globs](https://en.wikipedia.org/wiki/Glob_(programming)) , které jsou [implicitní SDK](../tools/csproj.md#default-compilation-includes-in-net-core-projects). Ponechat tyto globs ve vašem projektu dojde k chybě při sestavování vzhledem k tomu, že bude být duplicitní položky kompilace. 

Po provedení těchto kroků by měl být plně kompatibilní s formátem csproj RTM .NET Core projektu. 

Příklady před a po migraci z starý formát csproj do nového, najdete v článku [aktualizace Visual Studio 2017 RC – vylepšení nástrojů .NET Core](https://blogs.msdn.microsoft.com/dotnet/2016/12/12/updating-visual-studio-2017-rc-net-core-tooling-improvements/) článek na blogu .NET.

## <a name="see-also"></a>Viz také
[Port, migrace a Upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
