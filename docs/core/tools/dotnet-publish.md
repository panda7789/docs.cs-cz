---
title: dotnet publish – příkaz
description: Příkaz dotnet publish publikuje projekt nebo řešení .NET Core do adresáře.
ms.date: 02/24/2020
ms.openlocfilehash: cf41ee09244faad03feb8ccda19135b8c7780106
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156995"
---
# <a name="dotnet-publish"></a>dotnet publish

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet publish` – publikuje aplikaci a její závislosti do složky pro nasazení do hostitelského systému.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration] 
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a>Popis

`dotnet publish` zkompiluje aplikaci, přečte jejich závislosti zadané v souboru projektu a publikuje výslednou sadu souborů do adresáře. Výstup obsahuje následující prostředky:

- Kód zprostředkujícího jazyka (IL) v sestavení s příponou *DLL* .
- Soubor *. DEPS. JSON* , který obsahuje všechny závislosti projektu.
- Soubor *. runtimeconfig. JSON* , který určuje sdílený modul runtime, který aplikace očekává, a další možnosti konfigurace pro modul runtime (například typ uvolňování paměti).
- Závislosti aplikace, které jsou zkopírovány z mezipaměti NuGet do výstupní složky.

Výstup příkazu `dotnet publish` je připravený k nasazení do hostitelského systému (například server, počítač, Mac, notebook) k provedení. Jedná se o jediný oficiálně podporovaný způsob, jak připravit aplikaci pro nasazení. V závislosti na typu nasazení, které projekt určuje, hostující systém může nebo nemusí mít nainstalovaný modul .NET Core Shared runtime.

## <a name="arguments"></a>Argumenty

- **`PROJECT|SOLUTION`**

  Projekt nebo řešení, které se má publikovat
  
  * `PROJECT` je cesta a název souboru [C#](csproj.md)projektu, F#nebo Visual Basic nebo cesta k adresáři, který obsahuje soubor projektu C#, F#nebo Visual Basic. Pokud adresář není zadaný, použije se ve výchozím nastavení aktuální adresář.

  * `SOLUTION` je cesta a název souboru řešení ( *. sln* rozšíření) nebo cesta k adresáři, který obsahuje soubor řešení. Pokud adresář není zadaný, použije se ve výchozím nastavení aktuální adresář. **K dispozici od sady .NET Core 3,0 SDK.** 

## <a name="options"></a>Možnosti

- **`-c|--configuration <CONFIGURATION>`**

  Definuje konfiguraci sestavení. Výchozí hodnota pro většinu projektů je `Debug`, ale můžete přepsat nastavení konfigurace sestavení v projektu.

- **`-f|--framework <FRAMEWORK>`**

  Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md). V souboru projektu je nutné zadat cílovou architekturu.

- **`--force`**

  Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--interactive`** **k dispozici počínaje verzí .NET Core 3,0 SDK.**

  Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele. Například k dokončení ověřování. 

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací. Soubor manifestu je součástí výstupu [příkazu`dotnet store`](dotnet-store.md). Chcete-li zadat více manifestů, přidejte možnost `--manifest` pro každý manifest.

- **`--no-build`**

  Nevytvoří projekt před publikováním. Také implicitně nastaví příznak `--no-restore`.

- **`--no-dependencies`**

  Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.

- **`--nologo`** **k dispozici počínaje verzí .NET Core 3,0 SDK.**

  Nezobrazuje úvodní nápis nebo zprávu o autorských právech. 

- **`--no-restore`**

  Při spuštění příkazu neprovede implicitní obnovení.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Určuje cestu k výstupnímu adresáři. Pokud není zadaný, použije se výchozí hodnota *./bin/[Configuration]/[Framework]/Publish/* pro spustitelný soubor závislý na modulu runtime a binární soubory pro více platforem. Výchozí hodnota je *./bin/[Configuration]/[Framework]/[runtime]/Publish/* pro samostatně obsažený spustitelný soubor.

  Pokud je cesta relativní, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.

- **`--self-contained [true|false]`**

  Publikuje modul runtime .NET Core ve vaší aplikaci, takže modul runtime nemusí být na cílovém počítači nainstalován. Výchozí hodnota je `true`, pokud je zadán identifikátor modulu runtime. Další informace najdete v tématu [aplikace .NET Core – publikování](../deploying/index.md) a [publikování aplikací .net Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md).

- **`--no-self-contained`** **k dispozici počínaje verzí .NET Core 3,0 SDK.**

  Ekvivalent `--self-contained false`.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Publikuje aplikaci pro daný modul runtime. Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md). Další informace najdete v tématu [aplikace .NET Core – publikování](../deploying/index.md) a [publikování aplikací .net Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md).

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.

## <a name="examples"></a>Příklady

- Vytvořte [binární soubor pro více platforem závislý na modulu runtime](../deploying/index.md#produce-a-cross-platform-binary) pro projekt v aktuálním adresáři:

  ```dotnetcli
  dotnet publish
  ```

  Od .NET Core 3,0 SDK tento příklad také vytvoří [spustitelný soubor závislý na modulu runtime](../deploying/index.md#publish-runtime-dependent) pro aktuální platformu.

- Vytvoření [samostatného spustitelného souboru](../deploying/index.md#publish-self-contained) pro projekt v aktuálním adresáři pro konkrétní modul runtime:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  Identifikátor RID musí být v souboru projektu.

- Vytvořte [spustitelný soubor závislý na modulu runtime](../deploying/index.md#publish-runtime-dependent) pro projekt v aktuálním adresáři pro konkrétní platformu:

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  Identifikátor RID musí být v souboru projektu. Tento příklad platí pro .NET Core 3,0 SDK a novější verze.

- Publikování projektu v aktuálním adresáři pro konkrétní modul runtime a cílové rozhraní:

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- Publikovat zadaný soubor projektu:

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- Publikování aktuální aplikace, ale neobnovujte odkazy na projekt na projekt (P2P), pouze kořenový projekt během operace obnovení:

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>Viz také

- [Přehled publikování aplikace .NET Core](../deploying/index.md)
- [Publikování aplikací .NET Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md)
- [Cílové architektury](../../standard/frameworks.md)
- [Katalog identifikátoru runtime (RID)](../rid-catalog.md)
- [Práce s MacOS Catalina notarization](../install/macos-notarization-issues.md) Další informace najdete v následujících zdrojích informací:
- [Adresářová struktura publikované aplikace](/aspnet/core/hosting/directory-structure)
