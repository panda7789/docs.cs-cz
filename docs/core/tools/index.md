---
title: Nástroje rozhraní příkazového řádku .NET Core (CLI)
description: Přehled nástrojů a funkcí rozhraní příkazového řádku (CLI) .NET Core
ms.date: 08/14/2017
ms.custom: seodec18
ms.openlocfilehash: 50d1bbdd87ecd275b97603a1b47c6f13f879365a
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969884"
---
# <a name="net-core-command-line-interface-cli-tools"></a>Nástroje rozhraní příkazového řádku .NET Core (CLI)

Rozhraní příkazového řádku .NET Core (CLI) je nové sada nástrojů pro různé platformy pro vývoj aplikací .NET. Rozhraní příkazového řádku je základ, na kterém můžou REST nástroje, jako jsou například integrovaná vývojová prostředí (IDEs), editory a orchestrace sestavení.

## <a name="installation"></a>Instalace

Buď použijte nativní instalační programy, nebo použijte skripty instalačního prostředí:

- Nativní instalační programy se primárně používají na počítačích vývojáře a používají nativní mechanizmus instalace každého podporované platformy, například balíčky DEB na Ubuntu nebo sady MSI v systému Windows. Tyto instalační programy instalují a konfigurují prostředí pro okamžité použití vývojářem, ale vyžadují na počítači oprávnění správce. Pokyny k instalaci si můžete zobrazit v [Průvodci instalací .NET Core](https://aka.ms/dotnetcoregs).
- Skripty prostředí se primárně používají k nastavení serverů sestavení nebo k instalaci nástrojů bez oprávnění správce. Nainstalovat skripty neinstalují požadavky na počítač, který je nutné nainstalovat ručně. Další informace naleznete v [tématu Install Script reference](dotnet-install-script.md). Informace o tom, jak nastavit rozhraní příkazového řádku pro server sestavení kontinuální integrace (CI), najdete v tématu [použití .NET Core SDK a nástrojů v rámci kontinuální integrace (CI)](using-ci-with-cli.md).

Ve výchozím nastavení se rozhraní příkazového řádku instaluje souběžně (SxS), takže v jednom počítači může existovat více verzí nástrojů rozhraní příkazového řádku. Určení verze používané na počítači, kde je nainstalováno více verzí, je podrobněji vysvětleno v části [ovladače](#driver) .

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

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a>Faktorů

Ovladač má název [dotnet](dotnet.md) a má dvě zodpovědnosti, buď spuštění [aplikace závislé na rozhraní](../deploying/index.md) , nebo spuštění příkazu. 

Chcete-li spustit aplikaci závislou na rozhraní, zadejte aplikaci za ovladačem, například `dotnet /path/to/my_app.dll`. Při provádění příkazu ze složky, kde se nachází knihovna DLL aplikace, stačí provést `dotnet my_app.dll`. Pokud chcete použít konkrétní verzi modulu runtime .NET Core, použijte `--fx-version <VERSION>` možnost (viz Referenční dokumentace [příkazu dotnet](dotnet.md) ).

Když zadáte příkaz do ovladače, `dotnet.exe` spustí se proces spuštění příkazu CLI. Příklad:

```bash
> dotnet build
```

Nejdřív ovladač určuje verzi sady SDK, která se má použít. Pokud není k dispozici [možnost Global. JSON](global-json.md), použije se nejnovější verze sady SDK. To může být buď verze Preview, nebo stabilní, v závislosti na tom, co je v počítači nejnovější.  Po určení verze sady SDK se spustí příkaz.

### <a name="command"></a>Příkaz

Příkaz provede akci. Například `dotnet build` sestavení kódu. `dotnet publish`publikuje kód. Příkazy jsou implementovány jako Konzolová aplikace pomocí `dotnet {command}` konvence.

### <a name="arguments"></a>Arguments

Argumenty, které předáte na příkazovém řádku, jsou argumenty příkazu, který jste vyvolali. Například když `dotnet publish my_app.csproj`spustíte `my_app.csproj` , argument označuje projekt, který se má publikovat `publish` a který se předává do příkazu.

### <a name="options"></a>Možnosti

Možnosti, které zadáte na příkazovém řádku, jsou možnosti vyvolání příkazu. Například když `dotnet publish --output /build_output`spustíte `--output` , možnost a její `publish` hodnota jsou předány do příkazu.

## <a name="migration-from-projectjson"></a>Migrace z Project. JSON

Pokud jste použili nástroj Preview 2 pro vytváření projektů založených na *projektu Project. JSON*, Projděte si téma věnované [migraci dotnet](dotnet-migrate.md) pro informace o migraci projektu do MSBuild/ *. csproj* pro použití s nástroji pro vydávání verzí. Pro projekty .NET Core vytvořené před vydáním nástroje verze Preview 2 buď ručně aktualizujte projekt podle pokynů v části [migrace z DNX na .NET Core CLI (Project. JSON)](../migration/from-dnx.md) a pak použijte `dotnet migrate` nebo přímo Upgradujte své projekty.

## <a name="see-also"></a>Viz také:

- [dotnet/CLI – úložiště GitHub](https://github.com/dotnet/cli/)
- [Průvodce instalací .NET Core](https://aka.ms/dotnetcoregs)
