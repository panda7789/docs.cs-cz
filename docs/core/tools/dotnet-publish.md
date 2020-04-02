---
title: dotnet publikovat, příkaz
description: Příkaz publikování dotnet publikuje projekt nebo řešení .NET Core do adresáře.
ms.date: 02/24/2020
ms.openlocfilehash: 0e18220443f3713c86c257fcf401b98ddd716ebc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588272"
---
# <a name="dotnet-publish"></a>dotnet publish

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet publish`- Publikuje aplikaci a její závislosti do složky pro nasazení do hostitelského systému.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a>Popis

`dotnet publish`zkompiluje aplikaci, pročte její závislosti zadané v souboru projektu a publikuje výslednou sadu souborů do adresáře. Výstup zahrnuje následující aktiva:

- Kód zprostředkujícího jazyka (IL) v sestavení s rozšířením *dll.*
- Soubor *.deps.json,* který obsahuje všechny závislosti projektu.
- Soubor *.runtimeconfig.json,* který určuje sdílený runtime, který aplikace očekává, stejně jako další možnosti konfigurace pro runtime (například typ uvolňování paměti).
- Závislosti aplikace, které jsou zkopírovány z mezipaměti NuGet do výstupní složky.

Výstup `dotnet publish` příkazu je připraven k nasazení do hostitelského systému (například server, PC, Mac, notebook) pro spuštění. Je to jediný oficiálně podporovaný způsob, jak připravit aplikaci pro nasazení. V závislosti na typu nasazení, který projekt určuje, může nebo nemusí mít hostitelský systém na něm nainstalovanou sdílenou runtime .NET Core. Další informace naleznete v [tématu Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).

### <a name="msbuild"></a>MSBuild

Příkaz `dotnet publish` volá MSBuild, který `Publish` vyvolá cíl. Všechny parametry `dotnet publish` předané jsou předány MSBuild. A `-c` `-o` parametry mapovat na MSBuild `Configuration` a `OutputPath` vlastnosti, v uvedeném pořadí.

Příkaz `dotnet publish` přijímá možnosti MSBuild, `-p` například `-l` pro nastavení vlastností a definování protokolování. Vlastnost MSBuild můžete například nastavit pomocí formátu: `-p:<NAME>=<VALUE>`. Můžete také nastavit vlastnosti související s publikováním odkazem na soubor *PubXML,* například:

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

Další informace najdete v následujících materiálech:

- [Odkaz na příkazový řádek MSBuild](/visualstudio/msbuild/msbuild-command-line-reference)
- [Visual Studio publikuje profily (.pubxml) pro nasazení aplikace ASP.NET Core](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)

## <a name="arguments"></a>Argumenty

- **`PROJECT|SOLUTION`**

  Projekt nebo řešení publikovat.
  
  * `PROJECT`je cesta a název souboru projektu [jazyka C#](csproj.md), F# nebo Visual Basic nebo cesta k adresáři, který obsahuje soubor projektu Jazyka C#, F# nebo Visual Basic. Pokud adresář není zadán, je výchozí pro aktuální adresář.

  * `SOLUTION`je cesta a název souboru řešení (*přípona .sln)* nebo cesta k adresáři, který obsahuje soubor řešení. Pokud adresář není zadán, je výchozí pro aktuální adresář. K dispozici od .NET Core 3.0 SDK.

## <a name="options"></a>Možnosti

- **`-c|--configuration <CONFIGURATION>`**

  Definuje konfiguraci sestavení. Výchozí hodnota pro `Debug`většinu projektů je , ale můžete přepsat nastavení konfigurace sestavení v projektu.

- **`-f|--framework <FRAMEWORK>`**

  Publikuje aplikaci pro zadaný [cílový rámec](../../standard/frameworks.md). Je nutné zadat cílovou architekturu v souboru projektu.

- **`--force`**

  Vynutí vyřešení všech závislostí, i když bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *project.assets.json.*

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--interactive`**

  Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci. Například k dokončení ověřování. K dispozici od .NET Core 3.0 SDK.

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Určuje jeden nebo více [cílových manifestů,](../deploying/runtime-store.md) které se mají použít k oříznutí sady balíčků publikovaných s aplikací. Soubor manifestu je součástí výstupu [ `dotnet store` příkazu](dotnet-store.md). Chcete-li zadat více `--manifest` manifestů, přidejte možnost pro každý manifest.

- **`--no-build`**

  Nesestavuje projekt před publikováním. Také implicitně nastaví příznak. `--no-restore`

- **`--no-dependencies`**

  Ignoruje odkazy projektu na projekt a obnoví pouze kořenový projekt.

- **`--nologo`**

  Nezobrazuje spouštěcí banner ani zprávu o autorských právech. K dispozici od .NET Core 3.0 SDK.

- **`--no-restore`**

  Nespustí implicitní obnovení při spuštění příkazu.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Určuje cestu pro výstupní adresář.
  
  Pokud není zadán, je výchozí *[project_file_folder]./bin/[konfigurace]/[framework]/publish/* pro spustitelný modul závislý na spustitelném modulu a binární soubory mezi platformami. Ve výchozím nastavení je *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* pro samostatný spustitelný soubor.

  - Sada .NET Core 3.x SDK a novější
  
    Pokud je při publikování projektu zadána relativní cesta, je vygenerovaný výstupní adresář relativní vzhledem k aktuálnímu pracovnímu adresáři, nikoli k umístění souboru projektu.

    Pokud je při publikování řešení zadána relativní cesta, veškerý výstup pro všechny projekty přejde do zadané složky vzhledem k aktuálnímu pracovnímu adresáři. Chcete-li vytvořit výstup publikování jít do samostatných složek pro `PublishDir` každý projekt, `--output` zadejte relativní cestu pomocí msbuild vlastnost místo možnosti. Například `dotnet publish -p:PublishDir=.\publish` odešle výstup publikování pro `publish` každý projekt do složky ve složce, která obsahuje soubor projektu.

  - Sada SDK rozhraní .NET Core 2.x
  
    Pokud je při publikování projektu zadána relativní cesta, je vygenerovaný výstupní adresář relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.

    Pokud je při publikování řešení zadána relativní cesta, výstup každého projektu přejde do samostatné složky vzhledem k umístění souboru projektu. Pokud je při publikování řešení zadána absolutní cesta, veškerý výstup publikování pro všechny projekty přejde do zadané složky.

- **`--self-contained [true|false]`**

  Publikuje zaběhu .NET Core s vaší aplikací, takže runtime nemusí být nainstalován v cílovém počítači. Výchozí `true` hodnota je, pokud je zadán identifikátor modulu runtime a projekt je spustitelný projekt (nikoli projekt knihovny). Další informace naleznete v tématu [publikování a](../deploying/index.md) publikování [aplikací .NET Core pomocí rozhraní .NET Core .](../deploying/deploy-with-cli.md)

  Pokud je tato možnost `true` použita bez zadání nebo `false`, výchozí je `true`. V takovém případě nedávejte řešení nebo argument `--self-contained`projektu `true` ihned po , protože nebo `false` se očekává v této pozici.

- **`--no-self-contained`**

  Odpovídá `--self-contained false`. K dispozici od .NET Core 3.0 SDK.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Publikuje aplikaci pro daný běhový čas. Seznam identifikátorů modulu Runtime (RID) naleznete v [katalogu RID](../rid-catalog.md). Další informace naleznete v tématu [publikování a](../deploying/index.md) publikování [aplikací .NET Core pomocí rozhraní .NET Core .](../deploying/deploy-with-cli.md)

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a . Výchozí hodnota `minimal`je .

- **`--version-suffix <VERSION_SUFFIX>`**

  Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.

## <a name="examples"></a>Příklady

- Vytvořte [binární soubor pro běhový čas závislý na více platformách](../deploying/index.md#produce-a-cross-platform-binary) pro projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet publish
  ```

  Počínaje .NET Core 3.0 SDK, tento příklad také vytvoří [spustitelný soubor závislý na modulu runtime](../deploying/index.md#publish-runtime-dependent) pro aktuální platformu.

- Vytvořte [samostatný spustitelný soubor](../deploying/index.md#publish-self-contained) pro projekt v aktuálním adresáři pro konkrétní modul runtime:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  Rid musí být v souboru projektu.

- Vytvořte [spustitelný soubor závislý na modulu runtime](../deploying/index.md#publish-runtime-dependent) pro projekt v aktuálním adresáři pro konkrétní platformu:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  Rid musí být v souboru projektu. Tento příklad platí pro .NET Core 3.0 SDK a novější verze.

- Publikujte projekt v aktuálním adresáři pro konkrétní rozhraní runtime a cílový rámec:

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Publikování zadaného souboru projektu:

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Publikujte aktuální aplikaci, ale neobnovte odkazy projektu na projekt (P2P), pouze kořenový projekt během operace obnovení:

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Viz také

- [Přehled publikování aplikace .NET Core](../deploying/index.md)
- [Publikování aplikací .NET Core pomocí rozhraní CLI jádra ROZHRANÍ .NET](../deploying/deploy-with-cli.md)
- [Cílové architektury](../../standard/frameworks.md)
- [Katalog IDentifier (RID) modulu runtime](../rid-catalog.md)
- [Práce s macOS Catalina Notarization](../install/macos-notarization-issues.md)
- [Adresářová struktura publikované aplikace](/aspnet/core/hosting/directory-structure)
- [Odkaz na příkazový řádek MSBuild](/visualstudio/msbuild/msbuild-command-line-reference)
- [Visual Studio publikuje profily (.pubxml) pro nasazení aplikace ASP.NET Core](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)
