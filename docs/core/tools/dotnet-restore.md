---
title: dotnet restore – příkaz
description: Naučte se obnovit závislosti a nástroje specifické pro projekt pomocí příkazu dotnet restore.
ms.date: 02/27/2020
ms.openlocfilehash: cc8f374468ba95baccf058ac0b0a0175672cdf01
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158304"
---
# <a name="dotnet-restore"></a>dotnet restore

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet restore`– Obnoví závislosti a nástroje projektu.

## <a name="synopsis"></a>Stručný obsah

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

`dotnet restore` Příkaz používá NuGet k obnovení závislostí a také nástrojů specifických pro projekt, které jsou uvedeny v souboru projektu.  Ve většině případů nemusíte explicitně používat `dotnet restore` příkaz, protože obnovení NuGet se v případě potřeby spouští implicitně, když spustíte následující příkazy:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

V některých případech může být nepraktické spustit implicitní obnovení NuGet pomocí těchto příkazů. Například některé automatizované systémy, například systémy sestavení, musí volat `dotnet restore` explicitně k řízení, když dojde k obnovení, aby bylo možné řídit využití sítě. Chcete-li zabránit implicitnímu obnovení NuGet, můžete použít `--no-restore` příznak s některým z těchto příkazů k zakázání implicitního obnovení.

### <a name="specify-feeds"></a>Zadat informační kanály

Pro obnovení závislostí potřebuje NuGet informační kanály, ve kterých se balíčky nacházejí. Informační kanály jsou obvykle poskytovány prostřednictvím konfiguračního souboru *NuGet. config* . Výchozí konfigurační soubor se poskytne při instalaci .NET Core SDK. Chcete-li zadat další informační kanály, proveďte jednu z následujících akcí:

- Vytvořte vlastní soubor *NuGet. config* v adresáři projektu. Další informace najdete v tématu [běžné konfigurace NuGet](/nuget/consume-packages/configuring-nuget-behavior) a [rozdíly v souboru NuGet. config](#nugetconfig-differences) dále v tomto článku.
- Použijte `dotnet nuget` příkazy, jako [`dotnet nuget add source`](dotnet-nuget-add-source.md)je.

Informační kanály *NuGet. config* můžete přepsat `-s` možností.

Informace o tom, jak používat ověřené informační kanály, najdete v tématu [využívání balíčků ze ověřených informačních kanálů](/nuget/consume-packages/consuming-packages-authenticated-feeds).

### <a name="global-packages-folder"></a>Složka globálních balíčků

U závislostí můžete určit, kde se obnovené balíčky umístí během operace obnovení pomocí `--packages` argumentu. Pokud není zadaný, použije se výchozí mezipaměť balíčků NuGet, která se nachází v `.nuget/packages` adresáři domovského adresáře uživatele ve všech operačních systémech. Například */Home/user1* v systému Linux nebo *C:\Users\user1* ve Windows.

### <a name="project-specific-tooling"></a>Nástroje specifické pro projekt

U nástrojů specifických pro projekt `dotnet restore` nejprve obnovte balíček, ve kterém je nástroj zabalen, a poté pokračuje v obnovování závislostí nástroje, jak je uvedeno v souboru projektu.

### <a name="nugetconfig-differences"></a>rozdíly v NuGet. config

Chování `dotnet restore` příkazu je ovlivněno nastavením v souboru *NuGet. config* , pokud je k dispozici. Například nastavení `globalPackagesFolder` v *souboru NuGet. config* umístí obnovené balíčky NuGet do zadané složky. Toto je alternativa k zadání `--packages` možnosti `dotnet restore` příkazu. Další informace najdete v referenčních informacích k [NuGet. config](/nuget/schema/nuget-config-file).

Existují tři specifická nastavení, která `dotnet restore` ignorují:

- [bindingRedirects](/nuget/schema/nuget-config-file#bindingredirects-section)

  Přesměrování vazby nefungují s `<PackageReference>` prvky a .NET Core podporuje `<PackageReference>` pouze prvky pro balíčky NuGet.

- [řešení](/nuget/schema/nuget-config-file#solution-section)

  Toto nastavení je specifické pro Visual Studio a neplatí pro .NET Core. .NET Core nepoužívá `packages.config` soubor a místo toho používá `<PackageReference>` elementy pro balíčky NuGet.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  Toto nastavení se nedá použít, protože [NuGet zatím nepodporuje ověřování](https://github.com/NuGet/Home/issues/7939) pro důvěryhodné balíčky v různých platformách.

## <a name="arguments"></a>Argumenty

- **`ROOT`**

  Volitelná cesta k souboru projektu, který má být obnoven.

## <a name="options"></a>Možnosti

- **`--configfile <FILE>`**

  Konfigurační soubor NuGet (*NuGet. config*), který se má použít pro operaci obnovení.

- **`--disable-parallel`**

  Zakáže obnovení více projektů paralelně.

- **`--force`**

  Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .

- **`--force-evaluate`**

  Vynutí obnovení, aby se znovu vyhodnotily všechny závislosti i v případě, že soubor zámku již existuje.

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--ignore-failed-sources`**

  Pouze upozornit na zdroje, které selhaly, pokud existují balíčky, které splňují požadavky na verzi.

- **`--interactive`**

  Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování). Vzhledem k tomu, že .NET Core 2.1.400.

- **`--lock-file-path <LOCK_FILE_PATH>`**

  Výstupní umístění, kde je zapsán soubor zámku projektu. Ve výchozím nastavení je to *PROJECT_ROOT \Packages.Lock.JSON*.

- **`--locked-mode`**

  Nepovolujte aktualizaci souboru zámku projektu.

- **`--no-cache`**

  Určuje, že nejsou požadavky HTTP cache.

- **`--no-dependencies`**

  Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.

- **`--packages <PACKAGES_DIRECTORY>`**

  Určuje adresář pro obnovené balíčky.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Určuje modul runtime pro obnovení balíčku. Slouží k obnovení balíčků pro moduly runtime, které nejsou explicitně uvedeny v `<RuntimeIdentifiers>` značce v souboru *. csproj* . Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md). Zadáním této možnosti několikrát zadejte víc identifikátorů RID.

- **`-s|--source <SOURCE>`**

  Určuje zdroj balíčku NuGet, který se použije během operace obnovení. Toto nastavení přepíše všechny zdroje zadané v souborech *NuGet. config* . Více zdrojů lze zadat zadáním této možnosti několikrát.

- **`--use-lockfile`**

  Povoluje vygenerování souboru zámku projektu a jeho použití s obnovením.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a `diag[nostic]`. Výchozí hodnota je `minimal`.

## <a name="examples"></a>Příklady

- Obnovit závislosti a nástroje pro projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet restore
  ```

- Obnovit závislosti a nástroje pro `app1` projekt nalezené v dané cestě:

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souboru, který jste zadali jako zdroj:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí dvou cest k souborům, které jsou k dispozici jako zdroje:

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- Obnoví závislosti a nástroje pro projekt v aktuálním adresáři se zobrazeným podrobným výstupem:

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
