---
title: příkaz seznam nástrojů dotnet
description: Příkaz seznamu nástrojů dotnet obsahuje seznam nástrojů .NET Core nainstalovaných v počítači.
ms.date: 02/14/2020
ms.openlocfilehash: def3c345a775e5a65ec3d37718d207c80ca7ceee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847869"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet tool list`- Zobrazí seznam všech [nástrojů .NET Core](global-tools.md) zadaného typu aktuálně nainstalovaného v počítači.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet tool list <-g|--global>

dotnet tool list <--tool-path>

dotnet tool list

dotnet tool list <-h|--help>
```

## <a name="description"></a>Popis

Příkaz `dotnet tool list` umožňuje zobrazit seznam všech globálních nástrojů .NET Core, cest nástrojů nebo místních nástrojů nainstalovaných v počítači. Příkaz obsahuje seznam názvu balíčku, nainstalované verze a příkazu nástroje.  Chcete-li použít příkaz, zadejte jednu z následujících možností:

* Globální nástroj nainstalovaný ve výchozím umístění. Použít `--global` možnost
* Globální nástroj nainstalovaný ve vlastním umístění. Použijte `--tool-path` tuto možnost.
* Místní nástroj. `--global` Vynechte `--tool-path` možnosti a.

**Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0.**

## <a name="options"></a>Možnosti

- **`-g|--global`**

  Uvádí globální nástroje pro celou uživatele. Nelze kombinovat s `--tool-path` možností. Vynechání obou `--global` `--tool-path` a uvádí místní nástroje.

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--tool-path <PATH>`**

  Určuje vlastní umístění, kde lze najít globální nástroje. CESTA může být absolutní nebo relativní. Nelze kombinovat s `--global` možností. Vynechání obou `--global` `--tool-path` a uvádí místní nástroje.

## <a name="examples"></a>Příklady

- **`dotnet tool list -g`**

  Zobrazí seznam všech globálních nástrojů nainstalovaných v celém uživatelském počítači v počítači (aktuální profil uživatele).

- **`dotnet tool list --tool-path c:\global-tools`**

  Zobrazí seznam globálních nástrojů z určitého adresáře systému Windows.

- **`dotnet tool list --tool-path ~/bin`**

  Uvádí globální nástroje z konkrétního adresáře Linux/macOS.

- **`dotnet tool list`**

  Zobrazí seznam všech místních nástrojů dostupných v aktuálním adresáři.

## <a name="see-also"></a>Viz také

- [Nástroje .NET Core](global-tools.md)
- [Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET](global-tools-how-to-use.md)
- [Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET](local-tools-how-to-use.md)
