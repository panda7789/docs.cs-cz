---
title: Publikování aplikace .NET Core Hello World pomocí sady Visual Studio 2017
description: Publikování vytvoří sadu souborů, které jsou potřeba ke spuštění aplikace .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: ae202d8102d470e4260394f427e861750d4f0ee6
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362467"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio-2017"></a>Publikování aplikace .NET Core Hello World pomocí sady Visual Studio 2017

V [sestavení C# aplikace Hello World pomocí .NET Core v sadě Visual Studio 2017](with-visual-studio.md) nebo [vytvořit aplikaci Hello World jazyka Visual Basic pomocí .NET Core v sadě Visual Studio 2017](vb-with-visual-studio.md), jste vytvořili konzolovou aplikaci Hello World . V [ladění jazyka C# aplikace Hello World pomocí sady Visual Studio 2017](debugging-with-visual-studio.md), můžete otestovat pomocí ladicího programu sady Visual Studio. Teď, když jste si jisti, že funguje podle očekávání, můžete publikovat tak, aby mohli ostatní uživatelé spouštět. Publikování vytvoří sadu souborů, které jsou potřeba ke spuštění aplikace a soubory můžete nasadit zkopírováním do cílového počítače.

K publikování a spuštění aplikace: 

1. Ujistěte se, že Visual Studio sestavuje verzi vaší aplikace. V případě potřeby změnit nastavení konfigurace sestavení na panelu nástrojů z **ladění** k **vydání**.

   ![Panel nástrojů Visual Studio s vybraná sestavení pro vydání](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Klikněte pravým tlačítkem na **HelloWorld** projektu (nikoli řešení HelloWorld) a vyberte **publikovat** z nabídky. Můžete také vybrat **publikovat HelloWorld** z hlavní aplikace Visual Studio **sestavení** nabídky.

   ![Visual Studio Publish context menu](media/publishing-with-visual-studio/publish-context-menu.png)


   ![Visual Studio publikovat okna](media/publishing-with-visual-studio/publish-settings-window.png)

1. Otevřete okno konzoly. Například v **typ hledání** textové pole na hlavním panelu Windows, zadejte `Command Prompt` (nebo `cmd` zkráceně) a otevřete okno konzoly tak, že vyberete **příkazového řádku** desktop aplikace nebo stisknutím klávesy Enter, pokud je vybrána ve výsledcích hledání.

1. Přejděte k publikované aplikaci v `bin\release\PublishOutput` podadresáři adresáře projektu vaší aplikace. Jak ukazuje následující obrázek, publikovaný výstup zahrnuje následující čtyři soubory:

      * *HelloWorld.deps.json*

         Soubor závislosti modulu runtime aplikace. Definuje komponenty .NET Core a knihovny (včetně knihovny DLL, která obsahuje vaše aplikace) potřebných ke spuštění vaší aplikace. Další informace najdete v tématu [konfigurační soubory modulu Runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).
 
      * *HelloWorld.dll*

         Soubor, který obsahuje vaši aplikaci. Je dynamické knihovny DLL, které můžete provést tak, že zadáte `dotnet HelloWorld.dll` příkazu v okně konzoly. 

      * *HelloWorld.pdb* (volitelné pro nasazení)

         Soubor, který obsahuje symboly ladění. Není nutné k nasazení tohoto souboru spolu s vaší aplikace, i když byste ji uložíte, v případě, že budete muset ladění publikované verze vaší aplikace.

      * *HelloWorld.runtimeconfig.json*

         Konfigurační soubor běhu aplikace. Určuje verzi .NET Core, vaše aplikace byla vytvořena pro spuštění na. Další informace najdete v tématu [konfigurační soubory modulu Runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).  

   ![Okno konzoly publikované soubory](media/publishing-with-visual-studio/published-files-output.png)

Proces publikování vytvoří nasazení závisí na architektuře, které je typ nasazení, ve kterém se spustí publikovanou aplikaci na žádnou platformu podporovanou nástrojem .NET Core s .NET Core v systému nainstalovány. Uživatelé můžou spouštět aplikace vydáním `dotnet HelloWorld.dll` příkazu z okna konzoly.

Další informace o publikování a nasazení aplikací .NET Core najdete v tématu [nasazení aplikace .NET Core](../../core/deploying/index.md).
