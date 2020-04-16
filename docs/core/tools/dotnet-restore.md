---
title: dotnet obnovit, příkaz
description: Pomocí příkazu dotnet restore se dozvíte, jak obnovit závislosti a nástroje specifické pro projekt.
ms.date: 02/27/2020
ms.openlocfilehash: f49f0cda4424a4cc54ab7d4d4c6f729919dc7e60
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463423"
---
# <a name="dotnet-restore"></a>dotnet restore

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

## <a name="name"></a>Název

`dotnet restore`- Obnoví závislosti a nástroje projektu.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet restore` používá NuGet k obnovení závislostí, stejně jako nástroje specifické pro projekt, které jsou zadány v souboru projektu. Ve výchozím nastavení jsou obnovení závislostí a nástrojů spouštěny paralelně.

Chcete-li obnovit závislosti, NuGet potřebuje kanály, kde jsou umístěny balíčky. Informační kanály jsou obvykle poskytovány prostřednictvím konfiguračního souboru *nuget.config.* Při instalaci sady .NET Core SDK je k dispozici výchozí konfigurační soubor. Další informační kanály zadáte vytvořením vlastního souboru *nuget.config* v adresáři projektu. Kanály *nuget.config* můžete přepsat pomocí `-s` možnosti - .

U závislostí určíte, kam budou obnovené balíčky umístěny během operace obnovení pomocí argumentu. `--packages` Pokud není zadán, je použita výchozí mezipaměť balíčku `.nuget/packages` NuGet, která se nachází v adresáři v domovském adresáři uživatele ve všech operačních systémech. Například */home/user1* v Systému Linux nebo *C:\Users\user1* v systému Windows.

Pro nástroje specifické pro `dotnet restore` projekt nejprve obnoví balíček, ve kterém je nástroj zabalen a potom pokračuje obnovit závislosti nástroje, jak je uvedeno v jeho souboru projektu.

### <a name="nugetconfig-differences"></a>nuget.config rozdíly

Chování příkazu `dotnet restore` je ovlivněno nastavením v souboru *nuget.config,* pokud je k dispozici. Například nastavení `globalPackagesFolder` v *nuget.config* umístí obnovené balíčky NuGet do zadané složky. Toto je alternativa `--packages` k určení `dotnet restore` možnosti v příkazu. Další informace naleznete v [odkazu nuget.config](/nuget/schema/nuget-config-file).

Existují tři konkrétní `dotnet restore` nastavení, která ignorují:

- [vazbyPřesměrování](/nuget/schema/nuget-config-file#bindingredirects-section)

  Přesměrování vazby nefungují s `<PackageReference>` prvky a .NET Core podporuje `<PackageReference>` pouze prvky pro balíčky NuGet.

- [Řešení](/nuget/schema/nuget-config-file#solution-section)

  Toto nastavení je specifické pro visual studio a nevztahuje se na jádro .NET. .NET Core nepoužívá `packages.config` soubor a místo `<PackageReference>` toho používá prvky pro balíčky NuGet.

- [důvěryhodní podepisující](/nuget/schema/nuget-config-file#trustedsigners-section)

  Toto nastavení není použitelné, protože [NuGet ještě nepodporuje ověřování](https://github.com/NuGet/Home/issues/7939) důvěryhodných balíčků napříč platformami.

## <a name="implicit-restore"></a>Implicitní obnovení

Příkaz `dotnet restore` je spuštěn implicitně v případě potřeby při spuštění následujících příkazů:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Ve většině případů není nutné explicitně `dotnet restore` použít příkaz.

Někdy může být nepohodlné `dotnet restore` spustit implicitně. Například některé automatizované systémy, jako jsou systémy `dotnet restore` sestavení, musí explicitně volat, aby řídily, kdy dojde k obnovení, aby mohly řídit využití sítě. Chcete-li zabránit `dotnet restore` spuštění implicitně, `--no-restore` můžete použít příznak s některou z těchto příkazů zakázat implicitní obnovení.

## <a name="arguments"></a>Argumenty

- **`ROOT`**

  Volitelná cesta k souboru projektu k obnovení.

## <a name="options"></a>Možnosti

- **`--configfile <FILE>`**

  Konfigurační soubor NuGet *(nuget.config),* který se má použít pro operaci obnovení.

- **`--disable-parallel`**

  Zakáže obnovení více projektů paralelně.

- **`--force`**

  Vynutí vyřešení všech závislostí, i když bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *project.assets.json.*

- **`--force-evaluate`**

  Vynutí obnovení přehodnotit všechny závislosti i v případě, že soubor zámku již existuje.

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--ignore-failed-sources`**

  Pouze upozornit na zdroje selhání, pokud existují balíčky splňující požadavek na verzi.

- **`--interactive`**

  Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci (například k dokončení ověřování). Od .NET Core 2.1.400.

- **`--lock-file-path <LOCK_FILE_PATH>`**

  Výstupní umístění, kde je zapsán soubor zámku projektu. Ve výchozím nastavení se jedná *o soubor PROJECT_ROOT\packages.lock.json*.

- **`--locked-mode`**

  Nepovoluj aktualizaci souboru zámku projektu.

- **`--no-cache`**

  Určuje, že se nebudou ukládáy balíčky a požadavky HTTP.

- **`--no-dependencies`**

  Při obnovení projektu s odkazy projekt-projekt (P2P) obnoví kořenový projekt a nikoli odkazy.

- **`--packages <PACKAGES_DIRECTORY>`**

  Určuje adresář pro obnovené balíčky.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Určuje dobu runtime pro obnovení balíčku. Používá se k obnovení balíčků pro runtimes, které nejsou výslovně uvedeny ve značce `<RuntimeIdentifiers>` v souboru *.csproj.* Seznam identifikátorů modulu Runtime (RID) naleznete v [katalogu RID](../rid-catalog.md). Zadejte více ridů zadáním této možnosti vícekrát.

- **`-s|--source <SOURCE>`**

  Určuje zdroj balíčku NuGet, který se má použít během operace obnovení. Toto nastavení přepíše všechny zdroje zadané v souborech *nuget.config.* Zadáním této možnosti vícekrát lze poskytnout více zdrojů.

- **`--use-lockfile`**

  Umožňuje generovat a používat soubor zámku projektu s obnovením.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a . Výchozí hodnota `minimal`je .

## <a name="examples"></a>Příklady

- Obnovení závislostí a nástrojů pro projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet restore
  ```

- Obnovit závislosti a nástroje `app1` pro projekt nalezený v dané cestě:

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souboru, která je k dispozici jako zdroj:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí dvou cest k souborům, které jsou k dispozici jako zdroje:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- Obnovení závislostí a nástrojů pro projekt v aktuálním adresáři zobrazujícího podrobný výstup:

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
