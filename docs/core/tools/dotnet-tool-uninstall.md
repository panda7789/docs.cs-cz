---
title: příkaz dotnet nástroje pro odinstalaci
description: Příkaz pro odinstalaci nástroje dotnet odinstaluje zadaný nástroj .NET Core ze svého počítače.
ms.date: 02/14/2020
ms.openlocfilehash: 82dad0206d9c3e2ef0f41c353f4a608f10e4f127
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543440"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet tool uninstall` – odinstaluje zadaný [nástroj .NET Core](global-tools.md) ze svého počítače.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <PACKAGE_NAME>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Popis

Příkaz `dotnet tool uninstall` poskytuje způsob, jak odinstalovat nástroje .NET Core z počítače. Chcete-li použít příkaz, zadejte jednu z následujících možností:

* K odinstalaci globálního nástroje, který byl nainstalován ve výchozím umístění, použijte možnost `--global`.
* K odinstalaci globálního nástroje, který byl nainstalován ve vlastním umístění, použijte možnost `--tool-path`.
* Chcete-li odinstalovat místní nástroj, vynechejte možnosti `--global` a `--tool-path`.

**K dispozici jsou místní nástroje od .NET Core SDK 3,0.**

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Název nebo ID balíčku NuGet, který obsahuje nástroj .NET Core, který se má odinstalovat Název balíčku můžete najít pomocí příkazu pro [Výpis seznamu nástrojů dotnet](dotnet-tool-list.md) .

## <a name="options"></a>Možnosti

- **`-g|--global`**

  Určuje, že nástroj, který se má odebrat, pochází z instalace v rámci uživatele. Nelze kombinovat s možností `--tool-path`. Vynechání `--global` a `--tool-path` určuje, že nástroj, který má být odebrán, je místní nástroj. 

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--tool-path <PATH>`**

  Určuje umístění pro odinstalaci nástroje. Cesta může být absolutní nebo relativní. Nelze kombinovat s možností `--global`. Vynechání `--global` a `--tool-path` určuje, že nástroj, který má být odebrán, je místní nástroj. 

## <a name="examples"></a>Příklady

- **`dotnet tool uninstall -g dotnetsay`**

  Odinstaluje nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global.

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z určitého adresáře Windows.

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  Odinstaluje globální nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z konkrétního adresáře Linux/MacOS.

- **`dotnet tool uninstall dotnetsay`**

  Odinstaluje místní nástroj [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z aktuálního adresáře.

## <a name="see-also"></a>Viz také:

- [Nástroje .NET Core](global-tools.md)
