---
title: Začínáme s .NET Core
description: Najděte si materiály pro další informace o vytváření aplikací .NET Core ve Windows, Linuxu a macOS.
author: thraka
ms.author: adegeo
ms.date: 06/27/2018
ms.openlocfilehash: fa5deb46b64e1a09c9ad6582486a993a24336b42
ms.sourcegitcommit: 702d5ffc6e733b6c4ded85bf1c92e2293638ee9a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/04/2018
ms.locfileid: "37792397"
---
# <a name="get-started-with-net-core"></a>Začínáme s .NET Core

Tento článek obsahuje informace o zahájení práce s .NET Core. .NET core je nainstalovat ve Windows, Linuxu a macOS. Můžete kód ve svém oblíbeném textovém editoru a vytvářet multiplatformní knihovny a aplikace. 

Pokud si nejste jisti, co je .NET Core nebo toho, jak souvisí jiné technologie .NET, začínat [co je .NET](https://www.microsoft.com/net/learn/what-is-dotnet) Přehled. Jednoduše řečeno, .NET Core je open source, napříč platformami implementace .NET.

## <a name="create-an-application"></a>Vytvoření aplikace

Nejprve stáhnout a nainstalovat [.NET Core SDK](https://www.microsoft.com/net/download/) ve vašem počítači.

Dále otevřete terminál **PowerShell**, **příkazového řádku**, nebo **bash**. Zadejte následující příkaz `dotnet` příkazy k vytvoření a spuštění aplikace v jazyce C#.

```console
dotnet new console --output sample1
dotnet run --project sample1
```

Byste měli vidět následující výstup:

```console
Hello World!
```

Blahopřejeme! Vytvoříte jednoduchou aplikaci .NET Core. Můžete také použít [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio 2017](tutorials/with-visual-studio.md) (jenom Windows), nebo [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS pouze), chcete-li vytvořit aplikaci .NET Core.

## <a name="tutorials"></a>Kurzy

Můžete začít vyvíjet aplikace .NET Core pomocí následujících tyto podrobné kurzy.

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

* [Vytvořte aplikaci "Hello World" C# pomocí .NET Core v sadě Visual Studio 2017.](./tutorials/with-visual-studio.md)

* [Vytvoření knihovny tříd jazyka C# pomocí platformy .NET Core v sadě Visual Studio 2017.](./tutorials/library-with-visual-studio.md)

* [Vytvořte si aplikaci Visual Basic "Hello World" pomocí .NET Core v sadě Visual Studio 2017.](./tutorials/vb-with-visual-studio.md)

* [Vytvoření knihovny tříd pomocí jazyka Visual Basic a .NET Core v sadě Visual Studio 2017.](./tutorials/vb-library-with-visual-studio.md)  

* Podívejte se na video na [jak nainstalovat a používat Visual Studio Code a .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).

* Podívejte se na video na [jak nainstalovat a používat Visual Studio 2017 a .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).

* [Začínáme s .NET Core pomocí příkazového řádku.](tutorials/using-with-xplat-cli.md)

Najdete v článku [požadavky pro Windows. vývojové](windows-prerequisites.md) článku pro seznam podporovaných verzí Windows.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Můžete začít vyvíjet aplikace .NET Core pomocí následujících tyto podrobné kurzy.

* [Začínáme s .NET Core pomocí příkazového řádku.](tutorials/using-with-xplat-cli.md)

* Podívejte se na video na [Začínáme se službou Visual Studio Code pomocí jazyka C# a .NET Core na Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

Najdete v článku [předpoklady pro vývoj pro Linux](linux-prerequisites.md) článku pro seznam podporovaných distribucích systému Linux a verze.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Můžete začít vyvíjet aplikace .NET Core pomocí následujících tyto podrobné kurzy.

* Podívejte se na video na [Začínáme se službou Visual Studio Code pomocí jazyka C# a .NET Core v systému macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).

* [Začínáme s .NET Core v systému macOS, pomocí nástroje Visual Studio Code.](tutorials/using-on-macos.md)

* [Začínáme s .NET Core pomocí příkazového řádku.](tutorials/using-with-xplat-cli.md)

* [Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac.](tutorials/using-on-mac-vs.md)

* [Vytvoření kompletního řešení .NET Core v systému macOS pomocí sady Visual Studio pro Mac.](tutorials/using-on-mac-vs-full-solution.md)

Najdete v článku [předpoklady pro vývoj v macOS](macos-prerequisites.md) článku pro seznam podporovaných OS X / macOS verze.

***