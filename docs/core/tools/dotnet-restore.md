---
title: dotnet restore – příkaz
description: Naučte se obnovit závislosti a nástroje specifické pro projekt pomocí příkazu dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: c510aec8411fb0650b8caa4c3926181aa8071a66
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849606"
---
# <a name="dotnet-restore"></a>dotnet restore

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet restore`– Obnoví závislosti a nástroje projektu.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```console
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a>Popis

`dotnet restore` Příkaz používá NuGet k obnovení závislostí a také nástrojů specifických pro projekt, které jsou uvedeny v souboru projektu. Ve výchozím nastavení jsou obnovení závislostí a nástrojů spouštěny paralelně.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Pro obnovení závislostí potřebuje NuGet informační kanály, ve kterých se balíčky nacházejí. Informační kanály jsou obvykle poskytovány prostřednictvím konfiguračního souboru *NuGet. config* . Výchozí konfigurační soubor se poskytne při instalaci nástrojů rozhraní příkazového řádku. Další kanály určíte tak, že vytvoříte vlastní soubor *NuGet. config* v adresáři projektu. Na příkazovém řádku můžete zadat také další kanály na vyvolání.

U závislostí určíte, kde se obnovené balíčky umístí během operace obnovení pomocí `--packages` argumentu. Pokud není zadaný, použije se výchozí mezipaměť balíčků NuGet, která se nachází v `.nuget/packages` adresáři domovského adresáře uživatele ve všech operačních systémech. Například */Home/user1* v systému Linux nebo *C:\Users\user1* ve Windows.

U nástrojů `dotnet restore` specifických pro projekt nejprve obnovte balíček, ve kterém je nástroj zabalen, a poté pokračuje v obnovování závislostí nástroje, jak je uvedeno v souboru projektu.

### <a name="nugetconfig-differences"></a>rozdíly v NuGet. config

Chování `dotnet restore` příkazu je ovlivněno nastavením v souboru *NuGet. config* , pokud je k dispozici. Například nastavení `globalPackagesFolder` v *souboru NuGet. config* umístí obnovené balíčky NuGet do zadané složky. Toto je alternativa k zadání `--packages` možnosti `dotnet restore` příkazu. Další informace najdete v referenčních informacích k [NuGet. config](/nuget/schema/nuget-config-file).

Existují tři specifická nastavení, která `dotnet restore` ignorují:

- [bindingRedirects](/nuget/schema/nuget-config-file#bindingredirects-section)

  Přesměrování vazby nefungují s `<PackageReference>` prvky a .NET Core podporuje `<PackageReference>` pouze prvky pro balíčky NuGet.

- [řešení](/nuget/schema/nuget-config-file#solution-section)

  Toto nastavení je specifické pro Visual Studio a neplatí pro .NET Core. .NET Core nepoužívá `packages.config` soubor a místo toho používá `<PackageReference>` elementy pro balíčky NuGet.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  Toto nastavení se nedá použít, protože [NuGet zatím nepodporuje ověřování](https://github.com/NuGet/Home/issues/7939) pro důvěryhodné balíčky v různých platformách.

## <a name="implicit-dotnet-restore"></a>Nepřímo`dotnet restore`

Počínaje rozhraním .NET Core 2,0 `dotnet restore` se v případě potřeby spouští implicitně, když vydáte následující příkazy:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Ve většině případů už nemusíte explicitně používat `dotnet restore` příkaz.

V některých případech může být nepraktické spustit `dotnet restore` implicitně. Například některé automatizované systémy, například systémy sestavení, musí volat `dotnet restore` explicitně k řízení, když dojde k obnovení, aby bylo možné řídit využití sítě. Chcete- `dotnet restore` li zabránit spuštění implicitně, můžete `--no-restore` použít příznak s některým z těchto příkazů k zakázání implicitního obnovení.

## <a name="arguments"></a>Arguments

`ROOT`

Volitelná cesta k souboru projektu, který má být obnoven.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--configfile <FILE>`

Konfigurační soubor NuGet (*NuGet. config*), který se má použít pro operaci obnovení.

`--disable-parallel`

Zakáže obnovení více projektů paralelně.

`--force`

Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`--ignore-failed-sources`

Pouze upozornit na zdroje, které selhaly, pokud existují balíčky, které splňují požadavky na verzi.

`--no-cache`

Určuje, že nejsou balíčky mezipaměti a požadavky HTTP.

`--no-dependencies`

Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.

`--packages <PACKAGES_DIRECTORY>`

Určuje adresář pro obnovené balíčky.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Určuje modul runtime pro obnovení balíčku. Slouží k obnovení balíčků pro moduly runtime, které nejsou explicitně uvedeny v `<RuntimeIdentifiers>` značce v souboru *. csproj* . Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md). Zadáním této možnosti několikrát zadejte víc identifikátorů RID.

`-s|--source <SOURCE>`

Určuje zdroj balíčku NuGet, který se použije během operace obnovení. Toto nastavení přepíše všechny zdroje zadané v souborech *NuGet. config* . Více zdrojů lze zadat zadáním této možnosti několikrát.

`--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`

`--interactive`

Umožňuje příkazu zastavit a počkat na vstup nebo akci uživatele (například k dokončení ověřování). Vzhledem k tomu, že .NET Core 2.1.400.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--configfile <FILE>`

Konfigurační soubor NuGet (*NuGet. config*), který se má použít pro operaci obnovení.

`--disable-parallel`

Zakáže obnovení více projektů paralelně.

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`--ignore-failed-sources`

Pouze upozornit na zdroje, které selhaly, pokud existují balíčky, které splňují požadavky na verzi.

`--no-cache`

Určuje, že nejsou balíčky mezipaměti a požadavky HTTP.

`--no-dependencies`

Při obnovení projektu s odkazy z projektu na projekt (P2P) obnoví kořenový projekt a nikoli odkazy.

`--packages <PACKAGES_DIRECTORY>`

Určuje adresář pro obnovené balíčky.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Určuje modul runtime pro obnovení balíčku. Slouží k obnovení balíčků pro moduly runtime, které nejsou explicitně uvedeny v `<RuntimeIdentifiers>` značce v souboru *. csproj* . Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md). Zadáním této možnosti několikrát zadejte víc identifikátorů RID.

`-s|--source <SOURCE>`

Určuje zdroj balíčku NuGet, který se použije během operace obnovení. Tím dojde k přepsání všech zdrojů zadaných v souborech *NuGet. config* a efektivně si přečtete soubor *NuGet. config* , <packageSource> jako kdyby tam element nebyl. Více zdrojů lze zadat zadáním této možnosti několikrát.

`--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]`

---

## <a name="examples"></a>Příklady

Obnovit závislosti a nástroje pro projekt v aktuálním adresáři:

`dotnet restore`

Obnovit závislosti a nástroje pro `app1` projekt nalezené v dané cestě:

`dotnet restore ~/projects/app1/app1.csproj`

Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souboru, který jste zadali jako zdroj:

`dotnet restore -s c:\packages\mypackages`

Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí dvou cest k souborům, které jsou k dispozici jako zdroje:

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

Obnoví závislosti a nástroje pro projekt v aktuálním adresáři a zobrazí jenom minimální výstup:

`dotnet restore --verbosity minimal`
