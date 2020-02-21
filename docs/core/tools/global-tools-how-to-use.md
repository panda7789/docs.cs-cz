---
title: 'Kurz: instalace a použití globálního nástroje .NET Core'
description: Naučte se instalovat a používat nástroj .NET jako globální nástroj.
ms.date: 02/12/2020
ms.openlocfilehash: 65047af9d8a7f2fd4c1a07f65af3a6ddbf870c5d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543871"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a>Kurz: instalace a použití globálního nástroje .NET Core pomocí .NET Core CLI

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

V tomto kurzu se naučíte, jak nainstalovat a používat globální nástroj. Použijete nástroj, který vytvoříte v [prvním kurzu této série](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Požadavky

* Dokončete [první kurz této série](global-tools-how-to-create.md).

## <a name="use-the-tool-as-a-global-tool"></a>Použití nástroje jako globálního nástroje

1. Nainstalujte nástroj z balíčku spuštěním příkazu pro [instalaci nástroje dotnet](dotnet-tool-install.md) ve složce *botsay-\<název >* projektu:

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg botsay-<name>
   ```

   Parametr `--global` přikáže .NET Core CLI k instalaci binárních souborů nástroje ve výchozím umístění, které je automaticky přidáno do proměnné prostředí PATH.

   Parametr `--add-source` instruuje .NET Core CLI, aby dočasně používal adresář *./nupkg* jako další zdrojový kanál pro balíčky NuGet. Váš balíček jste přiřadili k jedinečnému názvu, abyste se ujistili, že bude nalezen pouze v adresáři *./nupkg* , nikoli na webu NuGet.org. 

   Výstup ukazuje příkaz použitý pro volání nástroje a nainstalovanou verzi:

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. Vyvolat nástroj:

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > Pokud se tento příkaz nepovede, možná budete muset otevřít nový terminál, aby se cesta aktualizovala.

1. Odeberte nástroj spuštěním příkazu pro [odinstalaci nástroje dotnet](dotnet-tool-uninstall.md) :

   ```dotnetcli
   dotnet tool uninstall -g botsay-<name>
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>Použití nástroje jako globálního nástroje nainstalovaného ve vlastním umístění

1. Nainstalujte nástroj z balíčku.

   Ve Windows:

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg botsay-<name>
   ```

   V systému Linux nebo macOS:

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg botsay-<name>
   ```

   Parametr `--tool-path` oznamuje .NET Core CLI instalaci binárních souborů nástroje v zadaném umístění. Pokud adresář neexistuje, vytvoří se. Tento adresář není automaticky přidán do proměnné prostředí PATH.

   Výstup ukazuje příkaz použitý pro volání nástroje a nainstalovanou verzi:

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. Vyvolat nástroj:

   Ve Windows:

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   V systému Linux nebo macOS:

   ```console
   ~/bin/botsay hello from the bot
   ```

1. Odeberte nástroj spuštěním příkazu pro [odinstalaci nástroje dotnet](dotnet-tool-uninstall.md) :

   Ve Windows:

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools botsay --add-source ./nupkg botsay-<name>
   ```

   V systému Linux nebo macOS:

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin botsay-<name>
   ```

## <a name="troubleshoot"></a>Řešení potíží

Pokud se vám zobrazí chybová zpráva s postupem v tomto kurzu, přečtěte si téma [řešení potíží s používáním nástrojů .NET Core](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste nainstalovali a použili nástroj jako globální nástroj. Pokud chcete nainstalovat a používat stejný nástroj jako místní nástroj, přejděte k dalšímu kurzu.

> [!div class="nextstepaction"]
> [Instalace a použití místních nástrojů](local-tools-how-to-use.md)
