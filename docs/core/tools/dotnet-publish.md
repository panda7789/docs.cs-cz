---
title: dotnet publish – příkaz
description: Příkaz dotnet publish publikuje projekt .NET Core do adresáře.
ms.date: 05/29/2018
ms.openlocfilehash: 0653a7b1e1abd6d7ffd3d21a0410279235b43a28
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451289"
---
# <a name="dotnet-publish"></a>dotnet publish

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet publish` – zabalí aplikaci a její závislosti do složky pro nasazení do hostitelského systému.

## <a name="synopsis"></a>Stručný obsah

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[.NET Core 2,1](#tab/netcore21)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20"></a>[.NET Core 2,0](#tab/netcore20)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1x"></a>[.NET Core 1. x](#tab/netcore1x)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a>Popis

`dotnet publish` zkompiluje aplikaci, přečte jejich závislosti zadané v souboru projektu a publikuje výslednou sadu souborů do adresáře. Výstup obsahuje následující prostředky:

- Kód zprostředkujícího jazyka (IL) v sestavení s příponou *DLL* .
- soubor *. DEPS. JSON* , který obsahuje všechny závislosti projektu.
- soubor *. runtimeconfig. JSON* , který určuje sdílený modul runtime, který aplikace očekává, a další možnosti konfigurace pro modul runtime (například typ uvolňování paměti).
- Závislosti aplikace, které jsou zkopírovány z mezipaměti NuGet do výstupní složky.

Výstup příkazu `dotnet publish` je připravený k nasazení do hostitelského systému (například server, počítač, Mac, notebook) k provedení. Jedná se o jediný oficiálně podporovaný způsob, jak připravit aplikaci pro nasazení. V závislosti na typu nasazení, které projekt určuje, hostující systém může nebo nemusí mít nainstalovaný modul .NET Core Shared runtime. Další informace najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md). Adresářovou strukturu publikované aplikace najdete v tématu [Struktura adresáře](/aspnet/core/hosting/directory-structure).

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Argumenty

`PROJECT`

Projekt, který se má publikovat Jedná se o cestu a název souboru [C#](csproj.md)projektu, F#nebo Visual Basic, nebo o cestu k adresáři, který obsahuje soubor projektu C#, F#nebo Visual Basic. Pokud není zadaný, použije se ve výchozím nastavení aktuální adresář.

## <a name="options"></a>Možnosti

# <a name="net-core-21"></a>[.NET Core 2,1](#tab/netcore21)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md). V souboru projektu je nutné zadat cílovou architekturu.

`--force`

Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`--manifest <PATH_TO_MANIFEST_FILE>`

Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací. Soubor manifestu je součástí výstupu [příkazu`dotnet store`](dotnet-store.md). Chcete-li zadat více manifestů, přidejte možnost `--manifest` pro každý manifest. Tato možnost je k dispozici počínaje verzí .NET Core 2,0 SDK.

`--no-build`

Nevytvoří projekt před publikováním. Také implicitně nastaví příznak `--no-restore`.

`--no-dependencies`

Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.

`--no-restore`

Při spuštění příkazu neprovede implicitní obnovení.

`-o|--output <OUTPUT_DIRECTORY>`

Určuje cestu k výstupnímu adresáři. Pokud není zadaný, použije se výchozí hodnota *./bin/[Configuration]/[Framework]/Publish/* pro nasazení závislé na rozhraní nebo *./bin/[Configuration]/[Framework]/[runtime]/Publish/* pro samostatně uzavřené nasazení.
Pokud je cesta relativní, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.

`--self-contained`

Publikuje modul runtime .NET Core ve vaší aplikaci, takže modul runtime nemusí být na cílovém počítači nainstalován. Je-li zadán identifikátor modulu runtime, je jeho výchozí hodnota `true`. Další informace o různých typech nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikuje aplikaci pro daný modul runtime. Používá se při vytváření [samostatně zahrnutého nasazení (SCD)](../deploying/index.md#publish-self-contained). Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md). Výchozím nastavením je publikování [nasazení závislého na rozhraní (FDD)](../deploying/index.md#publish-runtime-dependent).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.

# <a name="net-core-20"></a>[.NET Core 2,0](#tab/netcore20)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md). V souboru projektu je nutné zadat cílovou architekturu.

`--force`

Vynutí vyřešení všech závislostí i v případě, že bylo poslední obnovení úspěšné. Zadání tohoto příznaku je stejné jako odstranění souboru *Project. assets. JSON* .

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`--manifest <PATH_TO_MANIFEST_FILE>`

Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací. Soubor manifestu je součástí výstupu [příkazu`dotnet store`](dotnet-store.md). Chcete-li zadat více manifestů, přidejte možnost `--manifest` pro každý manifest. Tato možnost je k dispozici počínaje verzí .NET Core 2,0 SDK.

`--no-dependencies`

Ignoruje odkazy z projektu na projekt a obnoví pouze kořenový projekt.

`--no-restore`

Při spuštění příkazu neprovede implicitní obnovení.

`-o|--output <OUTPUT_DIRECTORY>`

Určuje cestu k výstupnímu adresáři. Pokud není zadaný, použije se výchozí hodnota *./bin/[Configuration]/[Framework]/Publish/* pro nasazení závislé na rozhraní nebo *./bin/[Configuration]/[Framework]/[runtime]/Publish/* pro samostatně uzavřené nasazení.
Pokud je cesta relativní, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.

`--self-contained`

Publikuje modul runtime .NET Core ve vaší aplikaci, takže modul runtime nemusí být na cílovém počítači nainstalován. Je-li zadán identifikátor modulu runtime, je jeho výchozí hodnota `true`. Další informace o různých typech nasazení naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md).

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikuje aplikaci pro daný modul runtime. Používá se při vytváření [samostatně zahrnutého nasazení (SCD)](../deploying/index.md#publish-self-contained). Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md). Výchozím nastavením je publikování [nasazení závislého na rozhraní (FDD)](../deploying/index.md#publish-runtime-dependent).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.

# <a name="net-core-1x"></a>[.NET Core 1. x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Publikuje aplikaci pro zadanou [cílovou architekturu](../../standard/frameworks.md). V souboru projektu je nutné zadat cílovou architekturu.

`-h|--help`

Vypíše krátkou nápovědu k příkazu.

`--manifest <PATH_TO_MANIFEST_FILE>`

Určuje jeden nebo několik [cílových manifestů](../deploying/runtime-store.md) , které se použijí ke zkrácení sady balíčků publikovaných s aplikací. Soubor manifestu je součástí výstupu [příkazu`dotnet store`](dotnet-store.md). Chcete-li zadat více manifestů, přidejte možnost `--manifest` pro každý manifest. Tato možnost je k dispozici počínaje verzí .NET Core 2,0 SDK.

`-o|--output <OUTPUT_DIRECTORY>`

Určuje cestu k výstupnímu adresáři. Pokud není zadaný, použije se výchozí hodnota *./bin/[Configuration]/[Framework]/Publish/* pro nasazení závislé na rozhraní nebo *./bin/[Configuration]/[Framework]/[runtime]/Publish/* pro samostatně uzavřené nasazení.
Pokud je cesta relativní, vygenerovaný výstupní adresář je relativní vzhledem k umístění souboru projektu, nikoli k aktuálnímu pracovnímu adresáři.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publikuje aplikaci pro daný modul runtime. Používá se při vytváření [samostatně zahrnutého nasazení (SCD)](../deploying/index.md#publish-self-contained). Seznam identifikátorů modulu runtime (identifikátorů RID) najdete v [katalogu RID](../rid-catalog.md). Výchozím nastavením je publikování [nasazení závislého na rozhraní (FDD)](../deploying/index.md#publish-runtime-dependent).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Definuje příponu verze, která nahradí hvězdičku (`*`) v poli verze souboru projektu.

---

## <a name="examples"></a>Příklady

Publikovat projekt v aktuálním adresáři:

`dotnet publish`

Publikovat aplikaci pomocí zadaného souboru projektu:

`dotnet publish ~/projects/app1/app1.csproj`

Publikujte projekt v aktuálním adresáři pomocí `netcoreapp1.1` Framework:

`dotnet publish --framework netcoreapp1.1`

Publikování aktuální aplikace pomocí rozhraní `netcoreapp1.1` Framework a modulu runtime pro `OS X 10.10` (Tento identifikátor RID musíte uvést v souboru projektu).

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

Publikování aktuální aplikace, ale neobnovování odkazů na projekt na projekt (P2P), pouze kořenový projekt během operace obnovení (.NET Core SDK 2,0 a novější verze):

`dotnet publish --no-dependencies`

## <a name="see-also"></a>Viz také

- [Cílové architektury](../../standard/frameworks.md)
- [Katalog identifikátoru runtime (RID)](../rid-catalog.md)
