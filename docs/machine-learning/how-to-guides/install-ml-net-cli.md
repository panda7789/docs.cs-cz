---
title: Jak nainstalovat nástroj ML.NET rozhraní příkazového řádku (CLI)
description: Přečtěte si, jak nainstalovat, upgradovat, downgrade a odinstalovat nástroj cli rozhraní příkazového řádku (ML.NET.Learn, jak nainstalovat, upgradovat, downgrade a odinstalovat nástroj ML.NET rozhraní příkazového řádku (CLI).
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: 9f678c7117d32bf817139951db7eef2c3d0f5eb2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848636"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>Jak nainstalovat nástroj ML.NET rozhraní příkazového řádku (CLI)

Přečtěte si, jak nainstalovat ML.NET rozhraní příkazového řádku (rozhraní příkazového řádku) do Windows, Macu nebo Linuxu.

ML.NET CLI generuje kvalitní ML.NET modely a zdrojový kód pomocí automatizovaného strojového učení (AutoML) a trénovací datové sady.

> [!NOTE]
> Toto téma odkazuje na ML.NET cli a ML.NET AutoML, které jsou aktuálně ve verzi Preview, a materiál může být může být možné změnit.

## <a name="pre-requisites"></a>Požadavky

- [.NET Jádro 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- (Nepovinné) [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)

Vygenerované projekty kódu Jazyka C# můžete `F5` spustit pomocí `dotnet run` sady Visual Studio stisknutím klávesy nebo pomocí (.NET Core CLI).

Poznámka: Pokud po instalaci [sady .NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` příkaz nefunguje, odhlaste se ze systému Windows a znovu se přihlaste.

## <a name="install"></a>Instalace

ML.NET CLI je nainstalován jako každý jiný dotnet Global Tool. Použijete `dotnet tool install` příkaz příkazu PŘÍKAZ K PŘÍKAZU .NET Core CLI.

Následující příklad ukazuje, jak nainstalovat ML.NET příkazového příkazového odpočinu do výchozího umístění informačního kanálu NuGet:

```dotnetcli
dotnet tool install -g mlnet
```

Pokud nástroj nelze nainstalovat (to znamená, pokud není k dispozici ve výchozím kanálu NuGet), zobrazí se chybové zprávy. Zkontrolujte, zda jsou kontrolovány zdroje, které jste očekávali.

Pokud je instalace úspěšná, zobrazí se zpráva s příkazem používaným k volání nástroje a nainstalovanou verzí, podobně jako v následujícím příkladu:

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Můžete potvrdit, že instalace byla úspěšná zadáním následujícího příkazu:

```console
mlnet
```

Měli byste vidět nápovědu pro dostupné příkazy pro nástroj mlnet, jako je příkaz "auto-train".

## <a name="install-a-specific-release-version"></a>Instalace konkrétní verze

Pokud se pokoušíte nainstalovat předběžnou verzi nebo určitou verzi nástroje, můžete určit [architekturu](../../standard/frameworks.md) v následujícím formátu:

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

Můžete také zkontrolovat, zda je balíček správně nainstalován zadáním následujícího příkazu:

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>Odinstalace balíčku CLI

Chcete-li odinstalovat balíček z místního počítače, zadejte následující příkaz:

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>Aktualizace balíčku CLI

Zadejte následující příkaz pro aktualizaci balíčku z místního počítače:

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>Nastavení návrhů zapisování zapisování (automatické dokončování na tabulátorech)

Vzhledem k tomu, `System.CommandLine`že ML.NET cli je založena na , má vestavěnou podporu pro dokončení karty.

Příklad fungování automatického dokončování tabulátoru je uveden v následující animaci:

![image](./media/cli-tab-completion.gif)

'Tab-based auto-completion' (parametr suggestions) práce na *Windows PowerShell* a *macOS/Linux bash,* ale to nebude fungovat na *Windows CMD*.

Chcete-li jej povolit, musí koncový uživatel v aktuální verzi náhledu provést několik kroků jednou za prostředí, které je uvedeno níže. Jakmile to provedete, dokončení bude fungovat `System.CommandLine` pro všechny aplikace napsané pomocí například ML.NET CLI.

Na počítači, kde chcete povolit dokončení, budete muset udělat dvě věci.

1. Nainstalujte `dotnet-suggest` globální nástroj spuštěním následujícího příkazu:

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. Přidejte do profilu prostředí příslušný skript překrytí. Pravděpodobně bude pravděpodobně muset vytvořit soubor profilu prostředí. Překrytí skript bude předávat požadavky na `dotnet-suggest` dokončení z prostředí do `System.CommandLine`nástroje, který deleguje na příslušnou aplikaci založenou na.

    - Pro bash, přidejte obsah [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) na `~/.bash_profile`.

    - V prostředí PowerShell přidejte do profilu Prostředí PowerShell obsah [dotnet-suggest-shim.ps1.](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) Očekávanou cestu k profilu prostředí PowerShell najdete spuštěním následujícího příkazu v konzole:

    ```console
    echo $profile
    ```

(U ostatních granátů [vyhledejte](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) nebo otevřete [problém](https://github.com/dotnet/System.CommandLine/issues).)

## <a name="installation-directory"></a>Instalační adresář

Rozhraní ML.NET cli lze nainstalovat do výchozího adresáře nebo do určitého umístění. Výchozí adresáře jsou:

| Operační systém          | Cesta                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Tato umístění jsou přidány do cesty uživatele při prvním spuštění sady SDK, takže globální nástroje nainstalované tam lze volat přímo.

Poznámka: Globální nástroje jsou specifické pro uživatele, nikoli globální počítače. Být specifické pro uživatele znamená, že nelze nainstalovat globální nástroj, který je k dispozici všem uživatelům počítače. Nástroj je k dispozici pouze pro každý profil uživatele, ve kterém byl nástroj nainstalován.

Globální nástroje lze také nainstalovat do určitého adresáře. Při instalaci v určitém adresáři musí uživatel zajistit, aby byl příkaz k dispozici, a to zahrnutím tohoto adresáře do cesty, voláním příkazu se zadaným adresářem nebo voláním nástroje ze zadaného adresáře.
V tomto případě rozhraní CLI jádra .NET nepřidá toto umístění automaticky do proměnné prostředí PATH.

## <a name="see-also"></a>Viz také

- [přehled ML.NET CLI](../automate-training-with-cli.md)
- [Kurz: Analýza mínění pomocí ML.NET CLI](../tutorials/sentiment-analysis-cli.md)
- [ML.NET referenční příručka příkazu automatického vlakového ústrojí ML.NET](../reference/ml-net-cli-reference.md)
- [Telemetrie v ML.NET CLI](../resources/ml-net-cli-telemetry.md)
