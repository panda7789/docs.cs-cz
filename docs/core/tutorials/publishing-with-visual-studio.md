---
title: "Publikování aplikace Hello World s Visual Studio 2017"
description: "Publikování vytvoří sadu souborů, které jsou potřebné ke spuštění vaší aplikace."
keywords: "Konzolové aplikace .NET, .NET core, publikování, nasazení"
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
ms.workload: dotnetcore
ms.openlocfilehash: 40479d85f9b31fcc80e3d12537126941878a09a4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a>Publikování aplikace Hello World s Visual Studio 2017

V [sestavení C# Hello, World aplikace s .NET Core ve Visual Studio 2017](with-visual-studio.md) nebo [sestavení aplikace Visual Basic Hello World s .NET Core ve Visual Studio 2017](vb-with-visual-studio.md), jste vytvořili konzolovou aplikaci Hello World . V [ladění aplikace C# Hello, World s Visual Studio 2017](debugging-with-visual-studio.md), můžete otestovat pomocí ladicího programu sady Visual Studio. Teď, když jste si jisti, že funguje podle očekávání, můžete publikovat tak, aby mohli ostatní uživatelé spouštět. Publikování vytvoří sadu souborů, které jsou potřebné ke spuštění vaší aplikace a soubory můžete nasadit jejich zkopírováním do cílového počítače.

K publikování a spuštění aplikace: 

1. Ujistěte se, že Visual Studio vytváří verzi vaší aplikace. V případě potřeby změňte nastavení konfigurace sestavení na panelu nástrojů z **ladění** k **verze**.

   ![Panel nástrojů Visual Studio](media/publishing-with-visual-studio/toolbar.png)

1. Klikněte pravým tlačítkem na **HelloWorld** projektu (ne HelloWorld řešení) a vyberte **publikovat** z nabídky. Můžete také vybrat **publikování HelloWorld** z hlavní sady Visual Studio **sestavení** nabídky.

   ![Panel nástrojů Visual Studio](media/publishing-with-visual-studio/publish1.png)


   ![Panel nástrojů Visual Studio](media/publishing-with-visual-studio/publishwindow.png)

1. Otevřete okno konzoly. Například v **typ pro hledání** textové pole na hlavním panelu systému Windows, zadejte `Command Prompt` (nebo `cmd` pro zkrácení) a otevřete okno konzoly můžete buď **příkazového řádku** plochy aplikace nebo stisknutím klávesy Enter, pokud je vybrána ve výsledcích hledání.

1. Přejděte k publikované aplikaci v `bin\release\PublishOutput` podadresáři adresáře projektu vaší aplikace. Jak ukazuje následující obrázek, publikované výstup obsahuje následující čtyři soubory:

      * *HelloWorld.deps.json*

         Soubor modulu runtime závislosti aplikace. Definuje součásti .NET Core a knihovny (včetně knihovnu DLL, která obsahuje aplikaci) potřebné ke spuštění vaší aplikace. Další informace najdete v tématu [souborů konfigurace modulu Runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).
 
      * *HelloWorld.dll*

         Soubor, který obsahuje vaše aplikace. Je knihovnu DLL, kterou lze provést zadáním `dotnet HelloWorld.dll` příkazu v okně konzoly. 

      * *HelloWorld.pdb* (pro nasazení volitelné)

         Soubor, který obsahuje symboly ladění. Není nutné k nasazení tohoto souboru spolu s vaší aplikace, i když byste měli uložit v případě, že budete muset ladění publikovanou verzi vaší aplikace.

      * *HelloWorld.runtimeconfig.json*

         Konfigurační soubor modulu runtime pro aplikace. Identifikuje verzi .NET Core, který vaše aplikace byla vytvořena za účelem spuštění. Další informace najdete v tématu [souborů konfigurace modulu Runtime](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).  

   ![Okno konzoly zobrazující publikované soubory](media/publishing-with-visual-studio/publishedfiles.png)

Proces publikování vytvoří nasazení závislé na framework, což je typ nasazení, kde je publikovaná aplikace poběží na žádnou platformu podporovanou nástrojem .NET Core s .NET Core nainstalované v systému. Uživatelé mohou spouštět aplikaci po vydání `dotnet HelloWorld.dll` příkazu v okně konzoly.

Další informace o publikování a nasazení aplikací .NET Core, najdete v části [nasazení aplikace .NET Core](../../core/deploying/index.md).
