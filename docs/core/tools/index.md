---
title: Rozhraní příkazového řádku .NET Core
titleSuffix: ''
description: Přehled .NET Core CLI a jeho funkcí.
ms.date: 08/14/2017
ms.openlocfilehash: b0a8e0dd8cf77bb6f7567c27e9972f62515ec0f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920481"
---
# <a name="net-core-cli-overview"></a>Přehled .NET Core CLI

Rozhraní příkazového řádku .NET Core (CLI) je sada nástrojů pro různé platformy pro vývoj, sestavování, spouštění a publikování aplikací .NET Core.

.NET Core CLI je součástí [.NET Core SDK](../sdk.md). Informace o tom, jak nainstalovat .NET Core SDK, najdete v tématu [instalace .NET Core SDK](../install/sdk.md).

## <a name="cli-commands"></a>Příkazy rozhraní příkazového řádku

Ve výchozím nastavení jsou nainstalovány následující příkazy:

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Základní příkazy**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [budování](dotnet-build.md)
- [opětovn](dotnet-publish.md)
- [spouštěl](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [Přenes](dotnet-migrate.md)
- [Odstranit](dotnet-clean.md)
- [sln](dotnet-sln.md)
- [Pomoc](dotnet-help.md)
- [store](dotnet-store.md)

**Příkazy pro úpravy projektu**

- [Přidat balíček](dotnet-add-package.md)
- [Přidat odkaz](dotnet-add-reference.md)
- [odebrat balíček](dotnet-remove-package.md)
- [odebrat odkaz](dotnet-remove-reference.md)
- [odkaz na seznam](dotnet-list-reference.md)

**Rozšířené příkazy**

- [odstranění NuGet](dotnet-nuget-delete.md)
- [národní prostředí NuGet](dotnet-nuget-locals.md)
- [nabízení NuGet](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [instalace skriptu dotnet](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Základní příkazy**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [budování](dotnet-build.md)
- [opětovn](dotnet-publish.md)
- [spouštěl](dotnet-run.md)
- [test](dotnet-test.md)
- [vstest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [Přenes](dotnet-migrate.md)
- [Odstranit](dotnet-clean.md)
- [sln](dotnet-sln.md)

**Příkazy pro úpravy projektu**

- [Přidat balíček](dotnet-add-package.md)
- [Přidat odkaz](dotnet-add-reference.md)
- [odebrat balíček](dotnet-remove-package.md)
- [odebrat odkaz](dotnet-remove-reference.md)
- [odkaz na seznam](dotnet-list-reference.md)

**Rozšířené příkazy**

- [odstranění NuGet](dotnet-nuget-delete.md)
- [národní prostředí NuGet](dotnet-nuget-locals.md)
- [nabízení NuGet](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [instalace skriptu dotnet](dotnet-install-script.md)

---

Rozhraní příkazového řádku přijímá model rozšiřitelnosti, který umožňuje určit další nástroje pro vaše projekty. Další informace naleznete v tématu [.NET Core CLI rozšiřující model](extensibility.md) .

## <a name="command-structure"></a>Struktura příkazu

Struktura příkazu rozhraní příkazového řádku se skládá z [ovladače ("dotnet")](#driver), [příkazu](#command)a možných [argumentů](#arguments) příkazů a [možností](#options). Tento model se zobrazí ve většině operací CLI, jako je například vytvoření nové konzolové aplikace a její spuštění z příkazového řádku, protože následující příkazy se zobrazí při spuštění z adresáře s názvem *my_app*:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a>Faktorů

Ovladač má název [dotnet](dotnet.md) a má dvě zodpovědnosti, buď spuštění [aplikace závislé na rozhraní](../deploying/index.md) , nebo spuštění příkazu. 

Chcete-li spustit aplikaci závislou na rozhraní, zadejte aplikaci za ovladačem, například `dotnet /path/to/my_app.dll`. Při provádění příkazu ze složky, kde se nachází knihovna DLL aplikace, stačí provést `dotnet my_app.dll`. Pokud chcete použít konkrétní verzi modulu runtime .NET Core, použijte možnost `--fx-version <VERSION>` (viz Referenční dokumentace [příkazu dotnet](dotnet.md) ).

Když zadáte příkaz do ovladače, `dotnet.exe` spustí proces spuštění příkazu CLI. Příklad:

```dotnetcli
dotnet build
```

Nejdřív ovladač určuje verzi sady SDK, která se má použít. Pokud není k dispozici [možnost Global. JSON](global-json.md), použije se nejnovější verze sady SDK. To může být buď verze Preview, nebo stabilní, v závislosti na tom, co je v počítači nejnovější.  Po určení verze sady SDK se spustí příkaz.

### <a name="command"></a>Příkaz

Příkaz provede akci. Například `dotnet build` sestavení kódu. `dotnet publish` publikuje kód. Příkazy jsou implementovány jako Konzolová aplikace pomocí `dotnet {command}` konvence.

### <a name="arguments"></a>Arguments

Argumenty, které předáte na příkazovém řádku, jsou argumenty příkazu, který jste vyvolali. Například při spuštění `dotnet publish my_app.csproj`argument `my_app.csproj` označuje projekt k publikování a je předán do příkazu `publish`.

### <a name="options"></a>Možnosti

Možnosti, které zadáte na příkazovém řádku, jsou možnosti vyvolání příkazu. Například když spustíte `dotnet publish --output /build_output`, možnost `--output` a její hodnota se předají do příkazu `publish`.

## <a name="migration-from-projectjson"></a>Migrace z Project. JSON

Pokud jste použili nástroj Preview 2 pro vytváření projektů založených na *projektu Project. JSON*, Projděte si téma věnované [migraci dotnet](dotnet-migrate.md) pro informace o migraci projektu do MSBuild/ *. csproj* pro použití s nástroji pro vydávání verzí. Pro projekty .NET Core vytvořené před vydáním nástroje verze Preview 2 buď ručně aktualizujte projekt podle pokynů v části [migrace z DNX na .NET Core CLI (Project. JSON)](../migration/from-dnx.md) a pak použijte `dotnet migrate` nebo přímo upgradujte projekty.

## <a name="see-also"></a>Viz také:

- [dotnet/úložiště GitHub SDK](https://github.com/dotnet/sdk/)
- [Průvodce instalací .NET Core](https://aka.ms/dotnetcoregs)
