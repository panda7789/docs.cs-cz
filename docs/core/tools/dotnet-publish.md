---
title: dotnet publish – příkaz
description: Příkaz dotnet publish publikuje projekt nebo řešení .NET Core do adresáře.
ms.date: 02/24/2020
ms.openlocfilehash: 59fdbfa875dad13963ae198acc6a31b537279dfe
ms.sourcegitcommit: c8c3e1c63a00b7d27f76f5e50ee6469e6bdc8987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87251176"
---
# <a name="dotnet-publish"></a>dotnet publish

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet publish`-Publikuje aplikaci a její závislosti do složky pro nasazení do hostitelského systému.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a>Popis

`dotnet publish`zkompiluje aplikaci, přečte prostřednictvím svých závislostí zadaných v souboru projektu a publikuje výslednou sadu souborů do adresáře. Výstup obsahuje následující prostředky:

- Kód zprostředkujícího jazyka (IL) v sestavení s příponou *DLL* .
- *.deps.jsv* souboru, který obsahuje všechny závislosti projektu.
- *.runtimeconfig.jsv* souboru, který určuje sdílený modul runtime, který aplikace očekává, a další možnosti konfigurace pro modul runtime (například typ uvolňování paměti).
- Závislosti aplikace, které jsou zkopírovány z mezipaměti NuGet do výstupní složky.

`dotnet publish`Výstup příkazu je připravený k nasazení do hostitelského systému (například server, počítač, Mac, notebook) k provedení. Jedná se o jediný oficiálně podporovaný způsob, jak připravit aplikaci pro nasazení. V závislosti na typu nasazení, které projekt určuje, hostující systém může nebo nemusí mít nainstalovaný modul .NET Core Shared runtime. Další informace najdete v tématu [publikování aplikací .NET Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md).

### <a name="implicit-restore"></a>Implicitní obnovení

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a>MSBuild

`dotnet publish`Příkaz volá MSBuild, který vyvolá `Publish` cíl. Všechny parametry předané do `dotnet publish` jsou předány do nástroje MSBuild. `-c`Parametry a se `-o` mapují do `Configuration` vlastností a v `PublishDir` uvedeném pořadí.

`dotnet publish`Příkaz přijímá možnosti nástroje MSBuild, jako je například `-p` pro nastavení vlastností a `-l` k definování protokolovacího nástroje. Můžete například nastavit vlastnost MSBuild pomocí formátu: `-p:<NAME>=<VALUE>` . Vlastnosti související s publikováním můžete také nastavit tak, že odkazujete na soubor *. pubxml* , například:

```dotnetcli
dotnet publish -p:PublishProfile=FolderProfile
```

Předchozí příklad používá soubor *FolderProfile. pubxml* , který se nachází ve složce * \<project_folder> /Properties/PublishProfiles* . Pokud při nastavování vlastnosti určíte cestu a příponu souboru `PublishProfile` , budou ignorovány. Nástroj MSBuild ve výchozím nastavení vyhledává ve složce *Properties/PublishProfiles* a předpokládá příponu souboru *pubxml* . Chcete-li zadat cestu a název souboru včetně přípony, nastavte `PublishProfileFullPath` vlastnost namísto `PublishProfile` Vlastnosti.

Další informace naleznete v následujících zdrojích:

- [Referenční dokumentace pro použití nástroje MSBuild v příkazovém řádku](/visualstudio/msbuild/msbuild-command-line-reference)
- [Publikační profily sady Visual Studio (. pubxml) pro nasazení aplikace ASP.NET Core](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)

## <a name="arguments"></a>Arguments

- **`PROJECT|SOLUTION`**

  Projekt nebo řešení, které se má publikovat
  
  * `PROJECT`je cesta a název souboru projektu [jazyka c#](csproj.md), f # nebo Visual Basic nebo cesta k adresáři, který obsahuje soubor projektu jazyka C#, f # nebo Visual Basic. Pokud adresář není zadaný, použije se ve výchozím nastavení aktuální adresář.

  * `SOLUTION`je cesta a název souboru řešení (*. sln* rozšíření) nebo cesta k adresáři, který obsahuje soubor řešení. Pokud adresář není zadaný, použije se ve výchozím nastavení aktuální adresář. K dispozici od verze .NET Core 3,0 SDK.

## <a name="options"></a>Možnosti

- **`-c|--configuration <CONFIGURATION>`**

  Definuje konfiguraci sestavení. Výchozí hodnota pro většinu projektů je `Debug` , ale můžete přepsat nastavení konfigurace sestavení v projektu.

- **`-f|--framework <FRAMEWORK>`**

  Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md). V souboru projektu je nutné zadat cílovou architekturu.

- **`--force`**

  Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění *project.assets.jsv* souboru.

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--interactive`**

  Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele. Například k dokončení ověřování. K dispozici od verze .NET Core 3,0 SDK.

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací. Soubor manifestu je součástí výstupu [ `dotnet store` příkazu](dotnet-store.md). Chcete-li zadat více manifestů, přidejte `--manifest` možnost pro každý manifest.

- **`--no-build`**

  Nevytvoří projekt před publikováním. Také implicitně nastaví `--no-restore` příznak.

- **`--no-dependencies`**

  Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.

- **`--nologo`**

  Nezobrazuje úvodní nápis nebo zprávu o autorských právech. K dispozici od verze .NET Core 3,0 SDK.

- **`--no-restore`**

  Při spuštění příkazu neprovede implicitní obnovení.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Určuje cestu k výstupnímu adresáři.
  
  Pokud není zadaný, použije se výchozí hodnota *[project_file_folder]./bin/[Configuration]/[Framework]/Publish/* pro spustitelný soubor závislý na modulu runtime a binární soubory pro více platforem. Pro samostatně uložený spustitelný soubor má výchozí nastavení *[project_file_folder]/bin/[Configuration]/[Framework]/[runtime]/Publish/* .

  Je-li výstupní složka ve webovém projektu ve složce projektu, `dotnet publish` výsledkem úspěchu příkazů jsou vnořené výstupní složky. Pokud je například složka projektu *MyProject*a výstupní složka pro publikování je *MyProject/Published*a `dotnet publish` dvakrát spustíte, druhý příkaz spustí do *MyProject/Publish/* Publish a Publishing soubory obsahu, jako jsou soubory *. config* a *. JSON* . Chcete-li se vyhnout vnořování publikačních složek, zadejte složku pro publikování, která není **přímo** ve složce projektu, nebo vylučte složku pro publikování z projektu. Chcete-li vyloučit složku pro publikování s názvem *publishoutput*, přidejte následující element do `PropertyGroup` elementu v souboru *. csproj* :

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - .NET Core 3. x SDK a novější
  
    Pokud je při publikování projektu zadána relativní cesta, vygenerovaný výstupní adresář je relativní vzhledem k aktuálnímu pracovnímu adresáři, nikoli k umístění souboru projektu.

    Pokud je při publikování řešení zadána relativní cesta, veškerý výstup pro všechny projekty přejde do zadané složky vzhledem k aktuálnímu pracovnímu adresáři. Chcete-li, aby výstup pro publikování přešel do samostatných složek pro každý projekt, zadejte relativní cestu pomocí `PublishDir` vlastnosti MSBuild namísto `--output` Možnosti. Například `dotnet publish -p:PublishDir=.\publish` odesílá výstup publikování pro každý projekt do `publish` složky ve složce, která obsahuje soubor projektu.

  - Sada .NET Core 2. x SDK
  
    Pokud je při publikování projektu zadána relativní cesta, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.

    Pokud je při publikování řešení zadána relativní cesta, výstup každého projektu přejde do samostatné složky vzhledem k umístění souboru projektu. Pokud je při publikování řešení zadána absolutní cesta, veškerý výstup publikování pro všechny projekty přejde do zadané složky.

- **`-p:PublishReadyToRun=true`**

  Zkompiluje sestavení aplikace jako formát ReadyToRun (R2R). R2R je forma kompilace v čase před zahájením (AOT). Další informace najdete v tématu [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images). K dispozici od verze .NET Core 3,0 SDK.

  Tuto možnost doporučujeme zadat v profilu publikování, nikoli na příkazovém řádku. Další informace najdete v tématu [MSBuild](#msbuild).

- **`-p:PublishSingleFile=true`**

  Zabalí aplikaci do spustitelného souboru s jedním souborem konkrétní platformy. Spustitelný soubor je samorozbalovací a obsahuje všechny závislosti (včetně nativních), které jsou nutné ke spuštění aplikace. Při prvním spuštění aplikace se aplikace extrahuje do adresáře na základě názvu aplikace a identifikátoru buildu. Spuštění je rychlejší, když aplikaci znovu spustíte. Pokud se nepoužije nová verze, aplikace se už nebude muset extrahovat druhou dobu. K dispozici od verze .NET Core 3,0 SDK.

  Další informace o publikování v jednom souboru najdete v [dokumentu návrhu sady prostředků s jedním souborem](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).

  Tuto možnost doporučujeme zadat v profilu publikování, nikoli na příkazovém řádku. Další informace najdete v tématu [MSBuild](#msbuild).

- **`-p:PublishTrimmed=true`**

  Ořízne nepoužívané knihovny, aby se snížila velikost nasazení aplikace při publikování samostatného spustitelného souboru. Další informace najdete v tématu [stříhání samostatných nasazení a spustitelných souborů](../deploying/trim-self-contained.md). K dispozici od verze .NET Core 3,0 SDK.

  Tuto možnost doporučujeme zadat v profilu publikování, nikoli na příkazovém řádku. Další informace najdete v tématu [MSBuild](#msbuild).

- **`--self-contained [true|false]`**

  Publikuje modul runtime .NET Core ve vaší aplikaci, takže modul runtime nemusí být na cílovém počítači nainstalován. Výchozí hodnota je `true` , pokud je zadán identifikátor modulu runtime a projekt je spustitelný projekt (ne projekt knihovny). Další informace najdete v tématu [aplikace .NET Core – publikování](../deploying/index.md) a [publikování aplikací .net Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md).

  Pokud je tato možnost použita bez zadání `true` nebo `false` , je výchozí hodnota `true` . V takovém případě neumísťujte argument řešení nebo projektu hned po `--self-contained` , protože `true` nebo `false` se na této pozici očekává.

- **`--no-self-contained`**

  Ekvivalent `--self-contained false` . K dispozici od verze .NET Core 3,0 SDK.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Publikuje aplikaci pro daný modul runtime. Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md). Další informace najdete v tématu [aplikace .NET Core – publikování](../deploying/index.md) a [publikování aplikací .net Core pomocí .NET Core CLI](../deploying/deploy-with-cli.md).

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` . Výchozí hodnota je `minimal` .

- **`--version-suffix <VERSION_SUFFIX>`**

  Definuje příponu verze, která nahradí hvězdičku ( `*` ) v poli verze souboru projektu.

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
- [Práce s macOS Catalina notarization](../install/macos-notarization-issues.md)
- [Adresářová struktura publikované aplikace](/aspnet/core/hosting/directory-structure)
- [Referenční dokumentace pro použití nástroje MSBuild v příkazovém řádku](/visualstudio/msbuild/msbuild-command-line-reference)
- [Publikační profily sady Visual Studio (. pubxml) pro nasazení aplikace ASP.NET Core](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)
- [ILLInk. Tasks](https://aka.ms/dotnet-illink)
