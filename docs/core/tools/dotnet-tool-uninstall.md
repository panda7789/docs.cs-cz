---
title: Příkaz odinstalovat nástroj dotnet
description: Příkaz odinstalace nástroje dotnet odinstaluje zadaný nástroj .NET Core z vašeho počítače.
ms.date: 02/14/2020
ms.openlocfilehash: 82799404c40baa3a39f4e2a5fdb414fb745ef448
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847830"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet tool uninstall`- Odinstaluje zadaný [nástroj .NET Core](global-tools.md) z vašeho počítače.

## <a name="synopsis"></a>Synopse

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>

dotnet tool uninstall <PACKAGE_NAME> <--tool-path>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Popis

Příkaz `dotnet tool uninstall` umožňuje odinstalovat nástroje .NET Core ze zařízení. Chcete-li použít příkaz, zadejte jednu z následujících možností:

* Chcete-li odinstalovat globální nástroj, který byl `--global` nainstalován ve výchozím umístění, použijte tuto možnost.
* Chcete-li odinstalovat globální nástroj, který byl `--tool-path` nainstalován ve vlastním umístění, použijte tuto možnost.
* Chcete-li odinstalovat místní nástroj, `--global` `--tool-path` vynechte možnosti a.

**Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0.**

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Název/ID balíčku NuGet, který obsahuje nástroj .NET Core k odinstalaci. Název balíčku můžete najít pomocí příkazu [seznamu nástrojů dotnet.](dotnet-tool-list.md)

## <a name="options"></a>Možnosti

- **`-g|--global`**

  Určuje, že nástroj, který má být odebrán, pochází z instalace pro celý uživatel. Nelze kombinovat s `--tool-path` možností. Vynechání obou `--global` `--tool-path` a určuje, že nástroj, který má být odebrán, je místní nástroj.

- **`-h|--help`**

  Vytiskne krátkou nápovědu pro příkaz.

- **`--tool-path <PATH>`**

  Určuje umístění, kam chcete nástroj odinstalovat. CESTA může být absolutní nebo relativní. Nelze kombinovat s `--global` možností. Vynechání obou `--global` `--tool-path` a určuje, že nástroj, který má být odebrán, je místní nástroj.

## <a name="examples"></a>Příklady

- **`dotnet tool uninstall -g dotnetsay`**

  Odinstaluje globální nástroj [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z konkrétního adresáře systému Windows.

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z konkrétního adresáře Linux/macOS.

- **`dotnet tool uninstall dotnetsay`**

  Odinstaluje místní nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z aktuálního adresáře.

## <a name="see-also"></a>Viz také

- [Nástroje .NET Core](global-tools.md)
- [Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET](global-tools-how-to-use.md)
- [Kurz: Instalace a použití místního nástroje .NET Core pomocí rozhraní CLI jádra .NET](local-tools-how-to-use.md)
