---
title: Příkaz balíčku seznamu dotnet
description: Příkaz "dotnet list package" poskytuje vhodnou možnost pro seznam odkazů na balíček pro projekt nebo řešení.
ms.date: 02/14/2020
ms.openlocfilehash: 12d64600d178ea8cf490a0d6917e67bd3d8c6d21
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463665"
---
# <a name="dotnet-list-package"></a>dotnet list package

**Tento článek se týká:** ✔️ .NET Core 2.2 SDK a novější verze

## <a name="name"></a>Název

`dotnet list package`- Uvádí odkazy na balíček pro projekt nebo řešení.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet list [<PROJECT>|<SOLUTION>] package [--config <SOURCE>]
    [--framework <FRAMEWORK>] [--highest-minor] [--highest-patch]
    [--include-prerelease] [--include-transitive] [--interactive]
    [--outdated] [--source <SOURCE>]

dotnet list package -h|--help
```

## <a name="description"></a>Popis

Příkaz `dotnet list package` poskytuje vhodnou možnost vypsat všechny odkazy na balíček NuGet pro konkrétní projekt nebo řešení. Nejprve je třeba vytvořit projekt, aby byly prostředky potřebné pro tento příkaz ke zpracování. Následující příklad ukazuje výstup `dotnet list package` příkazu pro [sentimentanalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) projektu:

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  1.4.0       1.4.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

Sloupec **Požadován** odkazuje na verzi balíčku zadanou v souboru projektu a může se týkat oblasti. Ve sloupci **Vyřešeno** je uvedena verze, kterou projekt aktuálně používá, a je vždy jednou hodnotou. Balíčky zobrazující `(A)` vpravo vedle jejich názvy představují [implicitní odkazy na balíčky,](csproj.md#implicit-package-references) které jsou odvozeny z nastavení projektu (typ`Sdk` nebo `<TargetFramework>` `<TargetFrameworks>` vlastnost atd.)

Pomocí `--outdated` této možnosti můžete zjistit, jestli jsou k dispozici novější verze balíčků, které používáte ve svých projektech. Ve výchozím `--outdated` nastavení uvádí seznam nejnovějších stabilních balíčků, pokud přeložená verze není také předběžnou verzí. Chcete-li zahrnout předběžné verze při výpisu novějších verzí, zadejte také `--include-prerelease` možnost. Následující příklady ukazují výstup `dotnet list package --outdated --include-prerelease` příkazu pro stejný projekt jako předchozí příklad:

```output
The following sources were used:
   https://api.nuget.org/v3/index.json
   C:\Program Files (x86)\Microsoft SDKs\NuGetPackages\

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         1.4.0       1.4.0      1.5.0-preview
```

Pokud potřebujete zjistit, zda má projekt přenosné závislosti, `--include-transitive` použijte tuto možnost. Přenosité závislosti dojít při přidání balíčku do projektu, který zase spoléhá na jiný balíček. Následující příklad ukazuje výstup ze `dotnet list package --include-transitive` spuštění příkazu pro projekt [HelloPlugin,](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) který zobrazuje balíčky nejvyšší úrovně a balíčky, na kterých závisí:

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Transitive Package      Resolved
   > PluginBase            1.0.0
```

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Soubor projektu nebo řešení, na kterém chcete pracovat. Pokud není zadán, příkaz prohledá aktuální adresář pro jeden. Pokud je nalezeno více než jedno řešení nebo projekt, je vyvolána chyba.

## <a name="options"></a>Možnosti

- **`--config <SOURCE>`**

  NuGet zdroje pro použití při hledání novějších balíčků. Vyžaduje `--outdated` možnost.

- **`--framework <FRAMEWORK>`**

  Zobrazí pouze balíčky použitelné pro zadanou [cílovou architekturu](../../standard/frameworks.md). Chcete-li určit více architektur, opakujte možnost vícekrát. Například: `--framework netcoreapp2.2 --framework netstandard2.0`.

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--highest-minor`**

  Bere v úvahu pouze balíčky s odpovídající číslo hlavní verze při hledání novější chbalíčky. Vyžaduje `--outdated` možnost.

- **`--highest-patch`**

  Bere v úvahu pouze balíčky s odpovídající hlavní a dílčí čísla verzí při hledání novějších balíčků. Vyžaduje `--outdated` možnost.

- **`--include-prerelease`**

  Bere v úvahu balíčky s předběžnými verzemi při hledání novějších balíčků. Vyžaduje `--outdated` možnost.

- **`--include-transitive`**

  Kromě balíčků nejvyšší úrovně obsahuje seznam přenosných balíčků. Při zadávání této možnosti získáte seznam balíčků, na kterých závisí balíčky nejvyšší úrovně.

- **`--interactive`**

  Umožňuje příkazu zastavit a čekat na vstup uživatele nebo akci. Například k dokončení ověřování. K dispozici od .NET Core 3.0 SDK.

- **`--outdated`**

  Seznam balíčků, které mají k dispozici novější verze.

- **`-s|--source <SOURCE>`**

  NuGet zdroje pro použití při hledání novějších balíčků. Vyžaduje `--outdated` možnost.

## <a name="examples"></a>Příklady

- Seznam odkazů na balíček konkrétního projektu:

  ```dotnetcli
  dotnet list SentimentAnalysis.csproj package
  ```

- Seznam odkazů na balíčky, které mají k dispozici novější verze, včetně předběžných verzí:

  ```dotnetcli
  dotnet list package --outdated --include-prerelease
  ```

- Seznam odkazů na balíček pro konkrétní cílový rámec:

  ```dotnetcli
  dotnet list package --framework netcoreapp3.0
  ```
