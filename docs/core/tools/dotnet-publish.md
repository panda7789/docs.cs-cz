---
title: DotNet příkazu pro publikování
description: Dotnet publikovat příkaz publikuje do adresáře projektu .NET Core.
ms.date: 05/29/2018
ms.openlocfilehash: 24490bd0fbfca65692d7025b5ed2aea659c35473
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611546"
---
# <a name="dotnet-publish"></a>publikování DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet publish` – Balíčky aplikace a jeho závislosti do složky pro nasazení do hostujícího systému.

## <a name="synopsis"></a>Souhrn

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a>Popis

`dotnet publish` zkompiluje aplikaci, přečte závislých zadané v souboru projektu a publikuje výslednou sadu souborů do adresáře. Výstup zahrnuje následující prostředky:

* Zprostředkující jazyk (IL) kódu v sestavení *dll* rozšíření.
* *. deps.json* soubor, který zahrnuje všechny závislosti projektu.
* *. runtime.config.json* soubor, který určuje sdílený modul runtime, který aplikace očekává, a také další možnosti konfigurace pro modul runtime (například typ kolekce uvolnění paměti).
* Závislosti aplikace, které se kopírují z mezipaměti NuGet do výstupní složky.

`dotnet publish` Výstupu příkazu je připravená k nasazení do hostujícího systému (třeba server, PC, Mac, přenosných počítačů) pro spuštění. Je oficiálně podporované jedině Příprava aplikace pro nasazení. V závislosti na typu nasazení, které určuje projekt hostitelském systému může nebo nemusí mít .NET Core sdílený modul runtime na něm nainstalován. Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md). Struktura adresářů je publikovaná aplikace, najdete v části [adresářovou strukturu](/aspnet/core/hosting/directory-structure).

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Arguments

`PROJECT`

Projekt pro publikování. Je cestu a název souboru [ C# ](csproj.md), F#, nebo soubor projektu jazyka Visual Basic, nebo cestu k adresáři, který obsahuje C#, F#, nebo soubor projektu jazyka Visual Basic. Pokud není zadán, použije se výchozí do aktuálního adresáře.

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Publikuje aplikace pro danou [Cílová architektura](../../standard/frameworks.md). V souboru projektu je nutné zadat cílovou architekturu.

`--force`

Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné. Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--manifest <PATH_TO_MANIFEST_FILE>`

Určuje jeden nebo několik [cílit manifesty](../deploying/runtime-store.md) oříznout sadu balíčků, které jsou publikované v aplikaci používat. Soubor manifestu je část výstupu [ `dotnet store` příkaz](dotnet-store.md). Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest. Tato možnost je k dispozici od verze rozhraní .NET Core 2.0 SDK.

`--no-build`

Nedaří sestavit projekt před publikováním. Také implicitně nastaví `--no-restore` příznak.

`--no-dependencies`

Ignoruje odkazy typu projekt projekt a obnoví pouze zadané kořenového projektu.

`--no-restore`

Při spuštění příkazu se nebude spouštět implicitní obnovení.

`-o|--output <OUTPUT_DIRECTORY>`

Určuje cestu k výstupnímu adresáři. Pokud není zadán, použije se výchozí *./bin/[configuration]/[framework]/publish/* nasazení závisí na architektuře nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.
Pokud je relativní cesta, vygeneruje výstupní adresář je relativní vzhledem k umístění souboru projektu, ne do aktuálního pracovního adresáře.

`--self-contained`

Publikuje modulu runtime .NET Core s vaší aplikací, modul runtime nemusí být nainstalovaný na cílovém počítači. Pokud je zadaný identifikátor modulu runtime, výchozí hodnota je `true`. Další informace o různých typů najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikuje aplikace pro daný modul runtime. Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd). Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md). Výchozí hodnota je publikovat [nasazení závisí na architektuře (chyba)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Definuje verze příponu, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Publikuje aplikace pro danou [Cílová architektura](../../standard/frameworks.md). V souboru projektu je nutné zadat cílovou architekturu.

`--force`

Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné. Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--manifest <PATH_TO_MANIFEST_FILE>`

Určuje jeden nebo několik [cílit manifesty](../deploying/runtime-store.md) oříznout sadu balíčků, které jsou publikované v aplikaci používat. Soubor manifestu je část výstupu [ `dotnet store` příkaz](dotnet-store.md). Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest. Tato možnost je k dispozici od verze rozhraní .NET Core 2.0 SDK.

`--no-dependencies`

Ignoruje odkazy typu projekt projekt a obnoví pouze zadané kořenového projektu.

`--no-restore`

Při spuštění příkazu se nebude spouštět implicitní obnovení.

`-o|--output <OUTPUT_DIRECTORY>`

Určuje cestu k výstupnímu adresáři. Pokud není zadán, použije se výchozí *./bin/[configuration]/[framework]/publish/* nasazení závisí na architektuře nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.
Pokud je relativní cesta, vygeneruje výstupní adresář je relativní vzhledem k umístění souboru projektu, ne do aktuálního pracovního adresáře.

`--self-contained`

Publikuje modulu runtime .NET Core s vaší aplikací, modul runtime nemusí být nainstalovaný na cílovém počítači. Pokud je zadaný identifikátor modulu runtime, výchozí hodnota je `true`. Další informace o různých typů najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikuje aplikace pro daný modul runtime. Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd). Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md). Výchozí hodnota je publikovat [nasazení závisí na architektuře (chyba)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Definuje verze příponu, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Publikuje aplikace pro danou [Cílová architektura](../../standard/frameworks.md). V souboru projektu je nutné zadat cílovou architekturu.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--manifest <PATH_TO_MANIFEST_FILE>`

Určuje jeden nebo několik [cílit manifesty](../deploying/runtime-store.md) oříznout sadu balíčků, které jsou publikované v aplikaci používat. Soubor manifestu je část výstupu [ `dotnet store` příkaz](dotnet-store.md). Chcete-li zadat více manifesty, přidejte `--manifest` možnost pro každý manifest. Tato možnost je k dispozici od verze rozhraní .NET Core 2.0 SDK.

`-o|--output <OUTPUT_DIRECTORY>`

Určuje cestu k výstupnímu adresáři. Pokud není zadán, použije se výchozí *./bin/[configuration]/[framework]/publish/* nasazení závisí na architektuře nebo *./bin/[configuration]/[framework]/[runtime]/publish/* pro samostatná nasazení.
Pokud je relativní cesta, vygeneruje výstupní adresář je relativní vzhledem k umístění souboru projektu, ne do aktuálního pracovního adresáře.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikuje aplikace pro daný modul runtime. Používá se při vytváření [samostatná nasazení (SCD)](../deploying/index.md#self-contained-deployments-scd). Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md). Výchozí hodnota je publikovat [nasazení závisí na architektuře (chyba)](../deploying/index.md#framework-dependent-deployments-fdd).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Definuje verze příponu, která má nahradit hvězdičku (`*`) v poli verze souboru projektu.

---

## <a name="examples"></a>Příklady

Publikujte projekt v aktuálním adresáři:

`dotnet publish`

Publikování aplikace pomocí zadaný soubor projektu:

`dotnet publish ~/projects/app1/app1.csproj`

Publikujte projekt v aktuálním adresáři pomocí `netcoreapp1.1` framework:

`dotnet publish --framework netcoreapp1.1`

Publikujte aktuální aplikace pomocí `netcoreapp1.1` rozhraní framework a modulu runtime pro `OS X 10.10` (musí uvést tento identifikátorů RID v souboru projektu).

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

Aktuální aplikaci publikovat, ale nechcete obnovit odkazy na projekt na projekt (P2P), jenom kořenový projektu během operace obnovení (.NET Core SDK 2.0 a novější):

`dotnet publish --no-dependencies`

## <a name="see-also"></a>Viz také:

- [Cílové verze rozhraní .NET Framework](../../standard/frameworks.md)
- [Identifikátor modulu runtime (RID) katalogu](../rid-catalog.md)
