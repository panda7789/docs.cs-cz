---
title: Publikování aplikace Hello World .NET Core pomocí sady Visual Studio 2017
description: Publikování vytvoří sadu souborů, které jsou nutné ke spuštění aplikace .NET Core.
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f8c37f47cc8dfb999f2371773a50c2dd91e074a5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660478"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio-2017"></a>Publikování aplikace Hello World .NET Core pomocí sady Visual Studio 2017

V [sestavování aplikace C# Hello World s .NET Core v aplikaci Visual Studio 2017](with-visual-studio.md) nebo [sestavení Visual Basic Hello World aplikace pomocí .NET core v aplikaci Visual Studio 2017](vb-with-visual-studio.md)jste vytvořili konzolovou aplikaci Hello World. V části [ladění C# aplikace Hello World pomocí sady Visual Studio 2017](debugging-with-visual-studio.md)jste otestovali pomocí ladicího programu sady Visual Studio. Teď, když jste si jisti, že funguje podle očekávání, můžete ji publikovat, aby ji ostatní uživatelé mohli spustit. Publikování vytvoří sadu souborů, které jsou potřeba ke spuštění vaší aplikace, a soubory můžete nasadit tak, že je zkopírujete do cílového počítače.

Publikování a spuštění aplikace: 

1. Ujistěte se, že Visual Studio sestavuje prodejní verzi vaší aplikace. V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z části **ladit** na **verzi**.

   ![Panel nástrojů sady Visual Studio s vybraným sestavením pro vydání](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. Klikněte pravým tlačítkem na projekt **HelloWorld** (ne na řešení HelloWorld) a v nabídce vyberte **publikovat** . Můžete také vybrat **publikovat HelloWorld** z hlavní nabídky **sestavení** sady Visual Studio.

   ![Místní nabídka publikování Visual studia](media/publishing-with-visual-studio/publish-context-menu.png)

   ![Okno pro publikování v aplikaci Visual Studio](media/publishing-with-visual-studio/publish-settings-window.png)

1. Otevřete okno konzoly. Například do textového pole **typ tady pro hledání** na hlavním panelu Windows zadejte `Command Prompt` (nebo `cmd` pro krátké) a otevřete okno konzoly. buď vyberte aplikaci desktopového **řádku** nebo stiskněte klávesu ENTER, pokud je vybraná na výsledky hledání

1. Přejděte k publikované aplikaci v `bin\release\PublishOutput` podadresáři adresáře projektu vaší aplikace. Jak ukazuje následující obrázek, publikovaný výstup obsahuje následující čtyři soubory:

      * *HelloWorld.deps.json*

         Soubor závislostí modulu runtime aplikace Definuje součásti .NET Core a knihovny (včetně knihovny dynamického propojení, která obsahuje vaši aplikaci) potřebné ke spuštění vaší aplikace. Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).
 
      * *HelloWorld.dll*

         Soubor, který obsahuje vaši aplikaci. Je to dynamická knihovna, kterou lze spustit zadáním `dotnet HelloWorld.dll` příkazu v okně konzoly. 

      * *HelloWorld. pdb* (volitelné pro nasazení)

         Soubor, který obsahuje symboly ladění. Nemusíte tento soubor nasazovat společně s vaší aplikací, i když byste ho měli uložit v události, kterou potřebujete k ladění publikované verze vaší aplikace.

      * *HelloWorld.runtimeconfig.json*

         Konfigurační soubor modulu runtime aplikace Identifikuje verzi .NET Core, na které byla aplikace sestavena. Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).  

   ![Okno konzoly zobrazující publikované soubory](media/publishing-with-visual-studio/published-files-output.png)

Proces publikování vytvoří nasazení závislé na rozhraní, což je typ nasazení, ve kterém bude publikována aplikace na libovolné platformě podporované rozhraním .NET Core s nainstalovaným rozhraním .NET Core v systému. Uživatelé můžou aplikaci spustit vyvoláním `dotnet HelloWorld.dll` příkazu z okna konzoly.

Další informace o publikování a nasazování aplikací .NET Core najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md).
