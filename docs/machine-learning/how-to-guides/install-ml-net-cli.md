---
title: Jak nainstalovat nástroj rozhraní příkazového řádku ML.NET (CLI)
description: Naučte se instalovat, upgradovat, downgradovat a odinstalovat nástroj rozhraní příkazového řádku ML.NET (CLI).
ms.date: 12/18/2019
ms.author: nakersha
author: natke
ms.openlocfilehash: 07b6e924ed9c6b0c278a86539ebe7d750f9ced37
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636585"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>Jak nainstalovat nástroj rozhraní příkazového řádku ML.NET (CLI)

Naučte se, jak nainstalovat rozhraní příkazového řádku (ML.NET) CLI do systému Windows, Mac nebo Linux.

ML.NET CLI generuje kvalitní ML.NET modely a zdrojový kód s využitím automatizovaného strojového učení (AutoML) a datové sady školení.

> [!NOTE]
> Toto téma odkazuje na ML.NET CLI a ML.NET AutoML, které jsou momentálně ve verzi Preview, a materiál může být změněn.

## <a name="pre-requisites"></a>Požadavky

- [Sada .NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- Volitelné [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)

Vygenerované C# projekty kódu se sadou Visual Studio můžete spustit stisknutím klávesy `F5` nebo pomocí `dotnet run` (.NET Core CLI).

Poznámka: když po instalaci [sady .NET Core 2,2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) nefunguje příkaz `dotnet tool`, odhlaste se z Windows a znovu se přihlaste.

## <a name="install"></a>Instalace produktu

Rozhraní příkazového řádku ML.NET je nainstalováno jako jakýkoli jiný globální nástroj dotnet. Použijete příkaz `dotnet tool install` .NET Core CLI.

Následující příklad ukazuje, jak nainstalovat rozhraní příkazového řádku ML.NET ve výchozím umístění informačního kanálu NuGet:

```dotnetcli
dotnet tool install -g mlnet
```

Pokud nástroj není možné nainstalovat (to znamená, pokud není k dispozici ve výchozím kanálu NuGet), zobrazí se chybové zprávy. Ověřte, zda jsou kontrolovány informační kanály, které jste očekávali.

Pokud je instalace úspěšná, zobrazí se zpráva s příkazem použitým pro volání nástroje a nainstalované verze, podobně jako v následujícím příkladu:

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Instalaci můžete ověřit tak, že zadáte následující příkaz:

```console
mlnet
```

Měli byste vidět nápovědu k dostupným příkazům pro nástroj mlnet, jako je například příkaz Auto-vlak.

## <a name="install-a-specific-release-version"></a>Instalace konkrétní vydané verze

Pokud se pokoušíte nainstalovat předběžnou verzi nebo konkrétní verzi nástroje, můžete určit [rozhraní](../../standard/frameworks.md) pomocí následujícího formátu:

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

Můžete také zjistit, jestli je balíček správně nainstalovaný, zadáním následujícího příkazu:

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>Odinstalace balíčku CLI

Zadejte následující příkaz pro odinstalaci balíčku z místního počítače:

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>Aktualizace balíčku CLI

Zadáním následujícího příkazu aktualizujete balíček z místního počítače:

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>Nastavení návrhů CLI (automatické dokončování založené na kartě)

Vzhledem k tomu, že rozhraní příkazového řádku ML.NET je založené na `System.CommandLine`, má vestavěnou podporu pro dokončování karet.

Příklad toho, jak funguje automatické dokončování karet, je znázorněno v následující animaci:

![obrázek](./media/cli-tab-completion.gif)

Automatické dokončování na kartě (návrhy parametrů) funguje v *prostředí Windows PowerShell* a *MacOS/Linux bash* , ale nebude fungovat na *Windows CMD*.

Aby ho bylo možné povolit, musí koncový uživatel v aktuální verzi Preview pro každé prostředí provést několik kroků, které jsou uvedené níže. Až to uděláte, dokončování budou fungovat pro všechny aplikace napsané pomocí `System.CommandLine`, jako je ML.NET CLI.

V počítači, ve kterém chcete povolit dokončování, budete muset provést dvě věci.

1. Pomocí následujícího příkazu nainstalujte nástroj `dotnet-suggest` Global:

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. Přidejte příslušný skript pro překrytí do profilu prostředí. Možná budete muset vytvořit soubor profilu prostředí. Skript překrytí přepošle žádosti o dokončení z vašeho prostředí na nástroj `dotnet-suggest`, který se deleguje na příslušnou aplikaci založenou na `System.CommandLine`.

    - V případě bash přidejte obsah pole [dotnet-navrhuje-Shim. bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) do `~/.bash_profile`.

    - V případě PowerShellu přidejte do svého profilu PowerShellu obsah [dotnet-Suggest-Shim. ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) . Očekávanou cestu k profilu PowerShellu můžete najít spuštěním následujícího příkazu v konzole:

    ```console
    echo $profile
    ```

(Pro další prostředí [vyhledejte](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) nebo otevřete [problém](https://github.com/dotnet/System.CommandLine/issues).)

## <a name="installation-directory"></a>Instalační adresář

ML.NET CLI se dá nainstalovat do výchozího adresáře nebo do konkrétního umístění. Výchozí adresáře jsou:

| OS          | Cesta                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Tato umístění jsou přidána do cesty uživatele při prvním spuštění sady SDK, takže je možné nainstalovanou sadu globálních nástrojů volat přímo.

Poznámka: globální nástroje jsou specifické pro uživatele, ne jako globální počítač. To znamená, že nemůžete nainstalovat globální nástroj, který je k dispozici pro všechny uživatele počítače. Nástroj je k dispozici pouze pro každý profil uživatele, ve kterém byl nástroj nainstalován.

Globální nástroje je také možné nainstalovat do konkrétního adresáře. Při instalaci do konkrétního adresáře musí uživatel ověřit, zda je příkaz k dispozici, zahrnutím tohoto adresáře do cesty, voláním příkazu se zadaným adresářem nebo voláním nástroje ze zadaného adresáře.
V takovém případě .NET Core CLI nepřidá toto umístění automaticky do proměnné prostředí PATH.

## <a name="see-also"></a>Viz také:

- [ML.NET CLI – přehled](../automate-training-with-cli.md)
- [Kurz: analýza mínění pomocí rozhraní příkazového řádku ML.NET](../tutorials/sentiment-analysis-cli.md)
- [Referenční příručka k příkazu ML.NET CLI pro automatické učení](../reference/ml-net-cli-reference.md)
- [Telemetrie v ML.NET CLI](../resources/ml-net-cli-telemetry.md)
