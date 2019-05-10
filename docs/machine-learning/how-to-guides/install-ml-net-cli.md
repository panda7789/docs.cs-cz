---
title: Postup instalace nástroje ML.NET rozhraní příkazového řádku (CLI)
description: Přehled a instalace nástroje ML.NET rozhraní příkazového řádku (CLI).
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 869c443d519557c9d3976676047e63a4a072d2d3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066235"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>Postup instalace nástroje ML.NET rozhraní příkazového řádku (CLI)

ML.NET CLI (rozhraní příkazového řádku) je nástroj, který můžete spustit na libovolné příkazového řádku (Windows, Mac nebo Linux) pro vytváření kvalitní ML.NET modely a zdrojový kód podle cvičných datových sad, které zadáte.

> [!NOTE]
> Toto téma odkazuje na ML.NET rozhraní příkazového řádku a ML.NET AutoML, které jsou aktuálně ve verzi Preview, a materiálu se můžou stát terčem změnit.

## <a name="pre-requisites"></a>Požadavky

- [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- (Volitelné) [Visual Studio 2017 nebo 2019](https://visualstudio.microsoft.com/vs/)

Můžete spustit buď generované C# projekty s Visual Studio F5 nebo pomocí kódu `dotnet run` (.NET Core CLI).

Poznámka: Pokud po instalaci [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) `dotnet tool` příkaz nefunguje, odhlásit z Windows a znovu se přihlaste.

## <a name="install"></a>Instalace

Rozhraní příkazového řádku ML.NET je nainstalována jako jakékoli jiné dotnet globální nástroj. Můžete použít `dotnet tool install` rozhraní příkazového řádku .NET Core. 

Následující příklad ukazuje, jak nainstalovat rozhraní příkazového řádku ML.NET výchozí umístění kanál NuGet:

```console
> dotnet tool install -g mlnet
```

Pokud nástroj nejde nainstalovat, (tj. Pokud není k dispozici na výchozím nastavení informačního kanálu NuGet), zobrazí se chybové zprávy. Zkontrolujte, že se kontroluje informační kanály, které jste očekávali.

Pokud je instalace úspěšná, zobrazí se zpráva zobrazující příkazu používaný k volání nástroje a verze nainstalovaná, podobně jako v následujícím příkladu:

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

Můžete potvrdit, že instalace proběhla úspěšně tak, že zadáte následující příkaz:

```console
> mlnet
```

Měli byste vidět nápovědy pro příkazy dostupné pro nástroj mlnet například příkaz "Automatické – train".

## <a name="install-a-specific-release-version"></a>Instalace konkrétní verze

Pokud se snažíte nainstalovat předběžné verzi nebo konkrétní verzi nástroje, můžete zadat číslo verze v následujícím formátu:

```console
> dotnet tool install -g <package-name> --version <version-number>
```

Můžete také zkontrolovat, pokud je tak, že zadáte následující příkaz správně nainstalován balíček:

```console
> dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>Odinstalovat balíček rozhraní příkazového řádku

Zadejte následující příkaz pro odinstalaci balíčku z místního počítače:

```console
> dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>Aktualizovat balíček rozhraní příkazového řádku

Zadejte následující příkaz k aktualizaci balíčku z místního počítače:

```console
> dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>Nastavení rozhraní příkazového řádku návrhy (založené na kartě Automatické dokončování)

Vzhledem k tomu, že rozhraní příkazového řádku ML.NET vychází `System.CommandLine`, obsahuje integrovanou podporu dokončování pomocí tabulátoru.

V následující animaci je uveden příklad toho, jak funguje automatické dokončování pomocí tabulátoru:

![obrázek](./media/cli-tab-completion.gif)

"Založené na kartě Automatické dokončování" (parametr návrhy) funguje na *prostředí Windows PowerShell* a *bash v systému macOS nebo Linux* ale nebudou fungovat ve *Windows CMD*.

Ho Pokud chcete povolit, v aktuální verzi preview, musí koncový uživatel provést několik kroků jednou pro každé prostředí, které jsou uvedené níže. Až to uděláte, budou fungovat dokončování pro všechny aplikace napsané s využitím `System.CommandLine` například ML.NET rozhraní příkazového řádku.

Na počítači, kde byste chtěli povolit dokončení budete muset udělat dvě věci.

1. Nainstalujte `dotnet-suggest` globální nástroj spuštěním následujícího příkazu:

    ```console
    > dotnet tool install dotnet-suggest -g
    ```

2. Přidáte skript odpovídající překrytí k vašemu profilu prostředí. Budete muset vytvořit prostředí soubor profilu. Skript překrytí bude předávat dokončení požadavků z vašeho prostředí `dotnet-suggest` nástroj, který deleguje na příslušné `System.CommandLine`– na základě aplikace.

    * Pro prostředí bash, přidejte obsah [dotnet navrhnout shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) k `~/.bash_profile`.

    * Pro PowerShell, přidejte obsah [dotnet navrhnout shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) k vašemu profilu prostředí PowerShell. Můžete najít očekávanou cestou k vašemu profilu prostředí PowerShell spuštěním následujícího příkazu v konzole:

    ```console
    > echo $profile
    ``` 

(Pro další prostředí [vyhledejte](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) nebo otevřete [problém](https://github.com/dotnet/System.CommandLine/issues).)

## <a name="installation-directory"></a>Instalační adresář

Rozhraní příkazového řádku ML.NET mohou být nainstalovány ve výchozím adresáři nebo v konkrétním umístění. Výchozí adresáře jsou:

| Operační systém          | Cesta                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Tato místa jsou přidány do cesty uživatele při prvním spuštění sady SDK, tak že nainstalované nástroje pro globální mohou být volány.

Poznámka: globální nástroje jsou specifické pro uživatele, počítače nejsou globální. Jsou specifické pro uživatele znamená, že nemůžete nainstalovat globální nástroj, který je k dispozici pro všechny uživatele počítače. Nástroj je k dispozici pouze pro každý uživatelský profil ve kterém byl nainstalován nástroj.

Globální nástroje můžete také nainstalovat v konkrétní adresář. Při instalaci v konkrétní adresář, uživatel musí zajistit příkaz je k dispozici, včetně tohoto adresáře v cestě, voláním příkazu se do adresáře určeného, nebo zavolání nástroj v rámci zadaného adresáře.
Rozhraní příkazového řádku .NET Core nepodporuje toto umístění v tomto případě automaticky přidat do proměnné prostředí PATH.

## <a name="see-also"></a>Viz také:

- [Kurz: Začínáme s ML.NET rozhraní příkazového řádku nástroje.](../tutorials/mlnet-cli.md)
- [Automaticky trénování modelů pomocí nástroje příkazového řádku ML.NET](../automate-training-with-cli.md)
- [Rozhraní příkazového řádku ML.NET automaticky trénování příkaz referenční příručka](../reference/ml-net-cli-reference.md) 
- [Telemetrie v rozhraní příkazového řádku ML.NET](../resources/ml-net-cli-telemetry.md)
