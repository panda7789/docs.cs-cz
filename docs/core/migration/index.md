---
title: Migrace .NET Core ze služby Project. JSON
description: Naučte se migrovat starší projekt .NET Core pomocí Project. JSON.
ms.date: 07/19/2017
ms.custom: seodec18
ms.openlocfilehash: 167f0707bbaf34ce12a1c56ee2320e7cc4f48bd3
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698922"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>Migrace projektů .NET Core ze služby Project. JSON

Tento dokument popisuje následující tři scénáře migrace pro projekty .NET Core:

1. [Migrace z platného nejnovějšího schématu *Project. JSON* na *csproj*](#migration-from-projectjson-to-csproj)
2. [Migrace z DNX do csproj](#migration-from-dnx-to-csproj)
3. [Migrace z RC3 a předchozích projektů .NET Core csproj do konečného formátu](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

Tento dokument se vztahuje pouze na starší projekty .NET Core, které používají Project. JSON. Nevztahuje se na migraci z .NET Framework do .NET Core.

## <a name="migration-from-projectjson-to-csproj"></a>Migrace z Project. JSON na csproj

Migraci z *Project. JSON* na *. csproj* lze provést pomocí jedné z následujících metod:

- [Visual Studio](#visual-studio)
- [Nástroj příkazového řádku dotnet pro migraci](#dotnet-migrate)

Obě metody používají stejný základní modul pro migraci projektů, takže výsledky budou stejné pro obě. Ve většině případů jedním z těchto dvou způsobů, jak migrovat soubor *Project. JSON* na *csproj* , je jediná věc, kterou potřebujete, a není nutné provádět žádné další ruční úpravy souboru projektu. Výsledný soubor *. csproj* bude pojmenován stejně jako obsahující název adresáře.

### <a name="visual-studio"></a>Visual Studio

Po otevření souboru *. xproj* nebo souboru řešení, který odkazuje na soubory *. xproj* v aplikaci Visual Studio 2017 nebo visual Studio 2019 verze 16,2 a starší se zobrazí dialogové okno **jednosměrného upgradu** . V dialogovém okně se zobrazí projekty, které mají být migrovány. Pokud otevřete soubor řešení, zobrazí se všechny projekty zadané v souboru řešení. Zkontrolujte seznam projektů, které chcete migrovat, a vyberte **OK**.

![Dialog s jednosměrným upgradem zobrazující seznam projektů, které se mají migrovat](media/one-way-upgrade.jpg)

Visual Studio automaticky migruje vybrané projekty. Pokud při migraci řešení nezvolíte možnost všechny projekty, zobrazí se stejné dialogové okno s výzvou k upgradu zbývajících projektů z tohoto řešení. Po dokončení migrace projektu můžete zobrazit a upravit jeho obsah tak, že kliknete pravým tlačítkem myši na projekt v okně **Průzkumník řešení** a vyberete **Upravit \<project název >. csproj**.

Migrované soubory (*Project. JSON*, *Global. JSON*, *. xproj*a soubor řešení) se přesunou do složky *zálohy* . Migrovaný soubor řešení je upgradován na Visual Studio 2017 nebo Visual Studio 2019 a nebudete moci otevřít tento soubor řešení v aplikaci Visual Studio 2015 nebo starší verze. Soubor s názvem *UpgradeLog. htm* , který obsahuje sestavu migrace, se také ukládá a otevírá automaticky.

> [!IMPORTANT]
> Nemůžete migrovat projekty pomocí sady Visual Studio 2015.

### <a name="dotnet-migrate"></a>dotnet migrate

Ve scénáři příkazového řádku můžete použít příkaz [`dotnet migrate`](../tools/dotnet-migrate.md) . Migruje projekt, řešení nebo sadu složek v tomto pořadí v závislosti na tom, které z nich byly nalezeny. Při migraci projektu se migruje projekt a všechny jeho závislosti.

Migrované soubory (*Project. JSON*, *Global. JSON*a *. xproj*) se přesunou do složky *zálohy* .

> [!NOTE]
> Pokud používáte Visual Studio Code, příkaz `dotnet migrate` neupraví soubory specifické pro Visual Studio Code, jako je například `tasks.json`. Tyto soubory je třeba změnit ručně.
> To platí také v případě, že používáte Project Ryder nebo jakýkoli Editor nebo integrované vývojové prostředí (IDE) jiné než Visual Studio.

Prohlédněte si [mapování mezi vlastnostmi Project. JSON a csproj](../tools/project-json-to-csproj.md) pro porovnání formátů Project. JSON a csproj.

### <a name="common-issues"></a>Běžné problémy

- Pokud se zobrazí chyba: nebyl nalezen žádný spustitelný soubor, který by odpovídal příkazu dotnet – migrace:

Spuštěním `dotnet --version` zobrazíte verzi, kterou používáte. [`dotnet migrate`](../tools/dotnet-migrate.md) vyžaduje .NET Core CLI RC3 nebo vyšší.
Tato chyba se zobrazí, pokud máte globální soubor *. JSON* v aktuálním nebo nadřazeném adresáři a verze `sdk` je nastavená na starší verzi.

## <a name="migration-from-dnx-to-csproj"></a>Migrace z DNX do csproj

Pokud stále používáte DNX pro vývoj v .NET Core, proces migrace by se měl provádět ve dvou fázích:

1. Použijte [stávající pokyny k migraci DNX](from-dnx.md) k migraci z DNX na rozhraní PŘÍKAZového řádku s povoleným formátem JSON pro Project.
2. Postupujte podle kroků z předchozí části a migrujte z *Project. JSON* na *. csproj*.  

> [!NOTE]
> DNX se oficiálně zastaralá během vydání verze Preview 1 .NET Core CLI.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Migrace z dřívějších formátů .NET Core csproj do RTM csproj

Formát .NET Core csproj se mění a vyvíjí u každé nové předběžné verze nástrojů. Neexistuje žádný nástroj, který by migrovali soubor projektu z dřívějších verzí sady csproj na nejnovější, takže je nutné ručně upravit soubor projektu. Skutečný postup závisí na verzi souboru projektu, který migrujete. Níže jsou uvedeny pokyny, které je třeba vzít v úvahu v závislosti na změnách, ke kterým došlo mezi verzemi:

- Odeberte vlastnost verze nástrojů z prvku `<Project>`, pokud existuje.
- Odeberte obor názvů XML (`xmlns`) z prvku `<Project>`.
- Pokud neexistuje, přidejte atribut `Sdk` do prvku `<Project>` a nastavte jej na `Microsoft.NET.Sdk` nebo `Microsoft.NET.Sdk.Web`. Tento atribut určuje, že projekt používá sadu SDK, která má být použita. pro Web Apps se používá `Microsoft.NET.Sdk.Web`.
- Odeberte příkazy `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` a `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` v horní a dolní části projektu. Tyto příkazy import jsou odvozeny v sadě SDK, takže není nutné, aby byly v projektu.
- Pokud máte v projektu @no__t položky-0 nebo `NETStandard.Library` `<PackageReference>`, měli byste je odebrat. Tyto odkazy na balíčky jsou [odvozeny v sadě SDK](https://aka.ms/sdkimplicitrefs).
- Odeberte prvek `Microsoft.NET.Sdk` `<PackageReference>`, pokud existuje. Odkaz na sadu SDK přichází prostřednictvím atributu `Sdk` u prvku `<Project>`.
- Odeberte [globy](https://en.wikipedia.org/wiki/Glob_(programming)) , které jsou [zahrnuté v sadě SDK](../tools/csproj.md#default-compilation-includes-in-net-core-projects). Ponecháním těchto globy ve vašem projektu dojde k chybě při sestavování, protože položky kompilace budou duplikovány.

Po provedení těchto kroků by váš projekt měl být plně kompatibilní s formátem RTM .NET Core csproj.

Příklady před a po migraci ze starého formátu csproj na nový najdete v článku [aktualizace nástrojů pro vylepšení sady Visual Studio 2017 RC – .NET Core](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) na blogu .NET.

## <a name="see-also"></a>Viz také:

- [Port, migrace a upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
