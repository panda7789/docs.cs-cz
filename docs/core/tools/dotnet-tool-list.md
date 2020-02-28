---
title: příkaz pro seznam nástrojů dotnet
description: Příkaz pro výpis seznamu nástrojů dotnet obsahuje seznam nástrojů .NET Core, které jsou nainstalovány na vašem počítači.
ms.date: 02/14/2020
ms.openlocfilehash: f231dcfe64a925f75f948d508e7a2d83befd9a00
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156982"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet tool list` – zobrazí seznam všech [nástrojů .NET Core](global-tools.md) zadaného typu, které jsou aktuálně nainstalované na vašem počítači.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list
dotnet tool list <-h|--help>
```

## <a name="description"></a>Popis

Příkaz `dotnet tool list` slouží jako způsob zobrazení seznamu všech nástrojů .NET Core Global, nástroje-Path nebo místních nástrojů, které jsou nainstalovány na vašem počítači. Příkaz vypíše název balíčku, nainstalovanou verzi a příkaz nástroje.  Chcete-li použít příkaz, zadejte jednu z následujících možností:

* Globální nástroj nainstalovaný ve výchozím umístění. Použití možnosti `--global`
* Globální nástroj nainstalovaný ve vlastním umístění. Použijte možnost `--tool-path`.
* Místní nástroj. Vynechejte možnosti `--global` a `--tool-path`.

**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**

## <a name="options"></a>Možnosti

- **`-g|--global`**

  Obsahuje seznam globálních nástrojů pro všechny uživatele. Nelze kombinovat s možností `--tool-path`. Vynechání `--global` a `--tool-path` seznam místních nástrojů.

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--tool-path <PATH>`**

  Určuje vlastní umístění, kde se mají najít globální nástroje. Cesta může být absolutní nebo relativní. Nelze kombinovat s možností `--global`. Vynechání `--global` a `--tool-path` seznam místních nástrojů.

## <a name="examples"></a>Příklady

- **`dotnet tool list -g`**

  Zobrazí seznam všech globálních nástrojů nainstalovaných v celém počítači (aktuální profil uživatele).

- **`dotnet tool list --tool-path c:\global-tools`**

  Zobrazí seznam globálních nástrojů z konkrétního adresáře Windows.

- **`dotnet tool list --tool-path ~/bin`**

  Zobrazí seznam globálních nástrojů z konkrétního adresáře Linux/macOS.

- **`dotnet tool list`**

  Zobrazí seznam všech místních nástrojů dostupných v aktuálním adresáři.

## <a name="see-also"></a>Viz také

- [Nástroje .NET Core](global-tools.md)
