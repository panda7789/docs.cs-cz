---
title: 'Kurz: Instalace a použití globálního nástroje .NET Core'
description: Přečtěte si, jak nainstalovat a používat nástroj .NET jako globální nástroj.
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156735"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a>Kurz: Instalace a použití globálního nástroje .NET Core pomocí rozhraní CLI jádra .NET

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

Tento kurz vás naučí, jak nainstalovat a používat globální nástroj. Nástroj, který vytvoříte v [prvním kurzu této řady](global-tools-how-to-create.md).

## <a name="prerequisites"></a>Požadavky

* Dokončete [první kurz této série](global-tools-how-to-create.md).

## <a name="use-the-tool-as-a-global-tool"></a>Použití nástroje jako globálního nástroje

1. Nainstalujte nástroj z balíčku spuštěním příkazu [instalace nástroje dotnet](dotnet-tool-install.md) ve složce projektu *Microsoft.botsay:*

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   Parametr `--global` sděluje rozhraní .NET Core CLI k instalaci binárních souborů nástrojů do výchozího umístění, které je automaticky přidáno do proměnné prostředí PATH.

   Parametr `--add-source` říká rozhraní .NET Core CLI dočasně použít adresář *./nupkg* jako další zdrojový zdroj pro balíčky NuGet. Dali jste svému balíčku jedinečný název, abyste se ujistili, že bude nalezen pouze v adresáři *./nupkg,* nikoli na webu Nuget.org.

   Výstup zobrazuje příkaz použitý k volání nástroje a nainstalovanou verzi:

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Vyvolat nástroj:

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > Pokud se tento příkaz nezdaří, bude pravděpodobně nutné otevřít nový terminál pro aktualizaci cesty.

1. Nástroj odeberte spuštěním příkazu [odinstalovat nástroj dotnet:](dotnet-tool-uninstall.md)

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>Použití nástroje jako globálního nástroje nainstalovaného ve vlastním umístění

1. Nainstalujte nástroj z balíčku.

   Ve Windows:

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   Na Linuxu nebo macOS:

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   Parametr `--tool-path` informuje rozhraní CLI jádra .NET k instalaci binárních souborů nástrojů do zadaného umístění. Pokud adresář neexistuje, je vytvořen. Tento adresář není automaticky přidán do proměnné prostředí PATH.

   Výstup zobrazuje příkaz použitý k volání nástroje a nainstalovanou verzi:

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. Vyvolat nástroj:

   Ve Windows:

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   Na Linuxu nebo macOS:

   ```console
   ~/bin/botsay hello from the bot
   ```

1. Nástroj odeberte spuštěním příkazu [odinstalovat nástroj dotnet:](dotnet-tool-uninstall.md)

   Ve Windows:

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   Na Linuxu nebo macOS:

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a>Řešení potíží

Pokud se při sledování kurzu zobrazí chybová zpráva, [přečtěte si článek Poradce při potížích s používáním nástroje .NET Core](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste nainstalovali a použili nástroj jako globální nástroj. Chcete-li nainstalovat a používat stejný nástroj jako místní nástroj, přejde meze k dalšímu kurzu.

> [!div class="nextstepaction"]
> [Instalace a používání místních nástrojů](local-tools-how-to-use.md)
