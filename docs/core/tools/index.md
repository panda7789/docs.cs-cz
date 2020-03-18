---
title: Rozhraní příkazového řádku .NET Core
titleSuffix: ''
description: Přehled rozhraní .NET Core CLI a jeho funkcí.
ms.date: 02/13/2020
ms.openlocfilehash: 45a40063f70a621e807abf5e01ceecb125aecd7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399117"
---
# <a name="net-core-cli-overview"></a>Přehled rozhraní CLI jádra .NET

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

Rozhraní příkazového řádku .NET Core (CLI) je nástroj pro různé platformy pro vývoj, vytváření, spouštění a publikování aplikací .NET Core.

Rozhraní .NET Core CLI je součástí sady [.NET Core SDK](../sdk.md). Informace o instalaci sady .NET Core SDK naleznete [v tématu Instalace sady .NET Core SDK](../install/sdk.md).

## <a name="cli-commands"></a>Příkazy příkazového příkazu

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

### <a name="tool-management-commands"></a>Příkazy pro správu nástrojů

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- [`tool restore`](global-tools.md#install-a-local-tool)K dispozici od .NET Core SDK 3.0.
- [`tool run`](global-tools.md#invoke-a-local-tool)K dispozici od .NET Core SDK 3.0.
- [`tool uninstall`](dotnet-tool-uninstall.md)

Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku. Můžete psát nástroje sami nebo instalovat nástroje napsané třetími stranami. Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje. Další informace naleznete v tématu [Přehled nástrojů .NET Core](global-tools.md).

## <a name="command-structure"></a>Struktura příkazů

Struktura příkazu příkazu příkazu se skládá z [ovladače ("dotnet")](#driver), [příkazu](#command)a případně [argumentů](#arguments) a [možností](#options)příkazu . Tento vzor se zobrazí ve většině operací rozhraní příkazového řádku, jako je například vytvoření nové konzolové aplikace a její spuštění z příkazového řádku, jak se následující příkazy zobrazují při spuštění z adresáře s názvem *my_app*:

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>Ovladač

Ovladač má název [dotnet](dotnet.md) a má dvě odpovědnosti, buď spuštění [aplikace závislé na rozhraní](../deploying/index.md) nebo provádění příkazu.

Chcete-li spustit aplikaci závislou na rámci, zadejte aplikaci za ovladačem, `dotnet /path/to/my_app.dll`například . Při provádění příkazu ze složky, kde se nachází dll aplikace, jednoduše spustit `dotnet my_app.dll`. Pokud chcete použít určitou verzi rozhraní .NET Core `--fx-version <VERSION>` Runtime, použijte tuto možnost (viz odkaz na [příkaz dotnet).](dotnet.md)

Když zadáte příkaz k ovladači, `dotnet.exe` spustí proces spuštění příkazu příkazu. Například:

```dotnetcli
dotnet build
```

Nejprve ovladač určuje verzi sady SDK, která má být používána. Pokud neexistuje žádný soubor [global.json,](global-json.md) použije se nejnovější verze sady SDK, která je k dispozici. To může být buď náhled nebo stabilní verze, v závislosti na tom, co je nejnovější v počítači.  Jakmile je určena verze sady SDK, provede příkaz.

### <a name="command"></a>Příkaz

Příkaz provede akci. Například `dotnet build` vytvoří kód. `dotnet publish`zveřejňuje kód. Příkazy jsou implementovány jako konzolové aplikace pomocí konvence. `dotnet {command}`

### <a name="arguments"></a>Argumenty

Argumenty, které předáte na příkazovém řádku, jsou argumenty do volaný příkaz. Například při `dotnet publish my_app.csproj`spuštění `my_app.csproj` argument označuje projekt publikovat a je `publish` předán příkazu.

### <a name="options"></a>Možnosti

Možnosti, které předáte na příkazovém řádku, jsou možnosti vyvolaný příkaz. Například při `dotnet publish --output /build_output`spuštění `--output` , možnost a jeho `publish` hodnota jsou předány příkazu.

## <a name="see-also"></a>Viz také

- [úložiště GitHub dotnet/sdk](https://github.com/dotnet/sdk/)
- [Instalační příručka jádra rozhraní .NET](../install/sdk.md)
