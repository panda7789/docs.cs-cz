---
title: .NET Core CLI
titleSuffix: ''
description: Přehled .NET Core CLI a jeho funkcí.
ms.date: 02/13/2020
ms.openlocfilehash: c491088f26a9aa1c065414e76fb0b80d554380b4
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625979"
---
# <a name="net-core-cli-overview"></a>Přehled .NET Core CLI

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

Rozhraní příkazového řádku .NET Core (CLI) je sada nástrojů pro různé platformy pro vývoj, sestavování, spouštění a publikování aplikací .NET Core.

.NET Core CLI je součástí [.NET Core SDK](../sdk.md). Informace o tom, jak nainstalovat .NET Core SDK, najdete v tématu [instalace .NET Core SDK](../install/sdk.md).

## <a name="cli-commands"></a>Příkazy rozhraní příkazového řádku

Ve výchozím nastavení jsou nainstalovány následující příkazy:

### <a name="basic-commands"></a>Základní příkazy

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [budování](dotnet-build.md)
- [publikování](dotnet-publish.md)
- [spouštěl](dotnet-run.md)
- [napaden](dotnet-test.md)
- [VSTest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [migraci](dotnet-migrate.md)
- [Odstranit](dotnet-clean.md)
- [SLN](dotnet-sln.md)
- [Pomoc](dotnet-help.md)
- [uchovávat](dotnet-store.md)

### <a name="project-modification-commands"></a>Příkazy pro modifikaci projektů

- [Přidat balíček](dotnet-add-package.md)
- [Přidat odkaz](dotnet-add-reference.md)
- [odebrat balíček](dotnet-remove-package.md)
- [odebrat odkaz](dotnet-remove-reference.md)
- [odkaz na seznam](dotnet-list-reference.md)

### <a name="advanced-commands"></a>Rozšířené příkazy

- [odstranění NuGet](dotnet-nuget-delete.md)
- [národní prostředí NuGet](dotnet-nuget-locals.md)
- [nabízení NuGet](dotnet-nuget-push.md)
- [nástroji](dotnet-msbuild.md)
- [instalace skriptu dotnet](dotnet-install-script.md)

### <a name="tool-management-commands"></a>Příkazy správy nástrojů

- [Instalace nástroje](dotnet-tool-install.md)
- [seznam nástrojů](dotnet-tool-list.md)
- [Aktualizace nástroje](dotnet-tool-update.md)
- [obnovení nástroje](global-tools.md#install-a-local-tool) **dostupné od .NET Core SDK 3,0**
- [spuštění nástroje](global-tools.md#invoke-a-local-tool) je **dostupné od .NET Core SDK 3,0**
- [Odinstalace nástroje](dotnet-tool-uninstall.md)

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

Chcete-li spustit aplikaci závislou na rozhraní, zadejte aplikaci za ovladačem, například `dotnet /path/to/my_app.dll`. Při provádění příkazu ze složky, kde se nachází knihovna DLL aplikace, stačí provést `dotnet my_app.dll`. Pokud chcete použít konkrétní verzi modulu runtime .NET Core, použijte možnost `--fx-version <VERSION>` (viz Referenční dokumentace [příkazu dotnet](dotnet.md) ).

Když zadáte příkaz do ovladače, `dotnet.exe` spustí proces spuštění příkazu CLI. Příklad:

```dotnetcli
dotnet build
```

Nejdřív ovladač určuje verzi sady SDK, která se má použít. Pokud není k dispozici žádný soubor [Global. JSON](global-json.md) , použije se nejnovější verze sady SDK. To může být buď verze Preview, nebo stabilní, v závislosti na tom, co je v počítači nejnovější.  Po určení verze sady SDK se spustí příkaz.

### <a name="command"></a>Příkaz

Příkaz provede akci. Například `dotnet build` sestavení kódu. `dotnet publish` publikuje kód. Příkazy jsou implementovány jako Konzolová aplikace pomocí `dotnet {command}` konvence.

### <a name="arguments"></a>Argumenty

Argumenty, které předáte na příkazovém řádku, jsou argumenty příkazu, který jste vyvolali. Například při spuštění `dotnet publish my_app.csproj`argument `my_app.csproj` označuje projekt k publikování a je předán do příkazu `publish`.

### <a name="options"></a>Možnosti

Možnosti, které zadáte na příkazovém řádku, jsou možnosti vyvolání příkazu. Například když spustíte `dotnet publish --output /build_output`, možnost `--output` a její hodnota se předají do příkazu `publish`.

## <a name="see-also"></a>Viz také

- [dotnet/úložiště GitHub SDK](https://github.com/dotnet/sdk/)
- [Průvodce instalací .NET Core](../install/sdk.md)
