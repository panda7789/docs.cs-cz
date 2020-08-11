---
title: .NET Core CLI
titleSuffix: ''
description: Přehled .NET Core CLI a jeho funkcí.
ms.topic: overview
ms.date: 02/13/2020
ms.openlocfilehash: 18dde384058206f437b53572b2f8331d65324482
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062688"
---
# <a name="net-core-cli-overview"></a>Přehled rozhraní .NET Core CLI

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

Rozhraní příkazového řádku .NET Core (CLI) je sada nástrojů pro různé platformy pro vývoj, sestavování, spouštění a publikování aplikací .NET Core.

.NET Core CLI je součástí [.NET Core SDK](../sdk.md). Informace o tom, jak nainstalovat .NET Core SDK, najdete v tématu [instalace .NET Core](../install/windows.md).

## <a name="cli-commands"></a>Příkazy rozhraní CLI

Ve výchozím nastavení jsou nainstalovány následující příkazy:

### <a name="basic-commands"></a>Základní příkazy

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a>Příkazy pro modifikaci projektů

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a>Rozšířené příkazy

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a>Příkazy správy nástrojů

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- [`tool restore`](global-tools.md#install-a-local-tool)K dispozici od .NET Core SDK 3,0.
- [`tool run`](global-tools.md#invoke-a-local-tool)K dispozici od .NET Core SDK 3,0.
- [`tool uninstall`](dotnet-tool-uninstall.md)

Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku. Můžete psát nástroje sami nebo instalovat nástroje napsané třetí stranou. Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje. Další informace najdete v tématu [Přehled nástrojů .NET Core](global-tools.md).

## <a name="command-structure"></a>Struktura příkazu

Struktura příkazu rozhraní příkazového řádku se skládá z [ovladače ("dotnet")](#driver), [příkazu](#command)a možných [argumentů](#arguments) příkazů a [možností](#options). Tento model se zobrazí ve většině operací CLI, jako je například vytvoření nové konzolové aplikace a její spuštění z příkazového řádku, protože následující příkazy se zobrazí při spuštění z adresáře s názvem *my_app*:

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>Ovladač

Ovladač má název [dotnet](dotnet.md) a má dvě zodpovědnosti, buď spuštění [aplikace závislé na rozhraní](../deploying/index.md) , nebo spuštění příkazu.

Chcete-li spustit aplikaci závislou na rozhraní, zadejte aplikaci za ovladačem, například `dotnet /path/to/my_app.dll` . Při provádění příkazu ze složky, kde se nachází knihovna DLL aplikace, stačí provést `dotnet my_app.dll` . Pokud chcete použít konkrétní verzi modulu runtime .NET Core, použijte `--fx-version <VERSION>` možnost (viz Referenční dokumentace [příkazu dotnet](dotnet.md) ).

Když zadáte příkaz do ovladače, `dotnet.exe` spustí se proces spuštění příkazu CLI. Příklad:

```dotnetcli
dotnet build
```

Nejdřív ovladač určuje verzi sady SDK, která se má použít. Pokud k souboru není [global.js](global-json.md) , použije se nejnovější verze sady SDK, která je k dispozici. To může být buď verze Preview, nebo stabilní, v závislosti na tom, co je v počítači nejnovější.  Po určení verze sady SDK se spustí příkaz.

### <a name="command"></a>Příkaz

Příkaz provede akci. Například `dotnet build` sestavení kódu. `dotnet publish`publikuje kód. Příkazy jsou implementovány jako Konzolová aplikace pomocí `dotnet {command}` konvence.

### <a name="arguments"></a>Arguments

Argumenty, které předáte na příkazovém řádku, jsou argumenty příkazu, který jste vyvolali. Například když spustíte `dotnet publish my_app.csproj` , `my_app.csproj` argument označuje projekt k publikování a je předán do `publish` příkazu.

### <a name="options"></a>Možnosti

Možnosti, které zadáte na příkazovém řádku, jsou možnosti vyvolání příkazu. Například když spustíte `dotnet publish --output /build_output` , `--output` možnost a její hodnota jsou předány do `publish` příkazu.

## <a name="see-also"></a>Viz také

- [dotnet/úložiště GitHub SDK](https://github.com/dotnet/sdk/)
- [Průvodce instalací .NET Core](../install/windows.md)
