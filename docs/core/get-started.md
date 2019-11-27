---
title: Začínáme s .NET Core
description: Vyhledejte prostředky, které se naučíte sestavovat aplikace .NET Core v systémech Windows, Linux a macOS.
author: thraka
ms.author: adegeo
ms.date: 09/19/2019
ms.openlocfilehash: 78066f2904f6a874b71165e4fe1769b6b778ae41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428865"
---
# <a name="get-started-with-net-core"></a>Začínáme s .NET Core

Tento článek poskytuje informace o tom, jak začít s .NET Core. .NET Core se dá nainstalovat na Windows, Linux a macOS. Můžete kódovat ve svém oblíbeném textovém editoru a vytvářejte knihovny a aplikace pro více platforem. 

Pokud si nejste jistí, co je .NET Core nebo jak souvisí s dalšími technologiemi .NET, začněte s přehledem [co je .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) . Jednoduše řečeno, .NET Core je open source implementace .NET pro více platforem.

## <a name="create-an-application"></a>Vytvoření aplikace

Nejprve Stáhněte a nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download) do počítače.

Pak otevřete terminál, jako je například **PowerShell**, **příkazový řádek**nebo **bash**. Zadejte následující `dotnet` příkazy pro vytvoření a spuštění C# aplikace:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Měl by se zobrazit následující výstup:

```console
Hello World!
```

Blahopřejeme! Vytvořili jste jednoduchou aplikaci .NET Core. K vytvoření aplikace .NET Core můžete použít taky [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (jenom Windows) nebo [Visual Studio pro Mac](tutorials/using-on-mac-vs.md) (jenom MacOS).

## <a name="tutorials"></a>Kurzy

Můžete začít vyvíjet aplikace .NET Core pomocí následujících podrobných kurzů.

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

- [Sestavte aplikaci C# "Hello World" pomocí .NET Core v aplikaci Visual Studio 2017.](./tutorials/with-visual-studio.md)
- [Sestavte knihovnu C# tříd pomocí .NET Core v aplikaci Visual Studio 2017.](./tutorials/library-with-visual-studio.md)
- [Sestavte Visual Basic aplikaci Hello World pomocí .NET Core v aplikaci Visual Studio 2017.](./tutorials/vb-with-visual-studio.md)
- [Sestavte knihovnu tříd pomocí Visual Basic a .NET Core v aplikaci Visual Studio 2017.](./tutorials/vb-library-with-visual-studio.md)  
- Podívejte se na video o [tom, jak nainstalovat a používat Visual Studio Code a .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).
- Podívejte se na video o [instalaci a používání sady Visual Studio 2017 a .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).
- [Začínáme s .NET Core pomocí příkazového řádku.](tutorials/using-with-xplat-cli.md)

Seznam podporovaných verzí Windows najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-windows) .

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

Můžete začít s vývojem aplikace .NET Core pomocí těchto podrobných kurzů:

- [Začínáme s .NET Core pomocí příkazového řádku.](tutorials/using-with-xplat-cli.md)
- Podívejte se na video o [zahájení práce s Visual Studio Code C# používání a .NET Core v Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).

Seznam podporovaných distribuce a verzí pro Linux najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-linux) .

# <a name="macostabmacos"></a>[macOS](#tab/macos)

Můžete začít s vývojem aplikace .NET Core pomocí těchto podrobných kurzů:

- Podívejte se na video o [zahájení práce s Visual Studio Code C# používání a .NET Core v MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).
- [Začínáme s .NET Core v macOS s využitím Visual Studio Code.](tutorials/using-on-macos.md)
- [Začínáme s .NET Core pomocí příkazového řádku.](tutorials/using-with-xplat-cli.md)
- [Začínáme s .NET Core v macOS pomocí Visual Studio pro Mac.](tutorials/using-on-mac-vs.md)
- [Sestavte kompletní řešení .NET Core na macOS pomocí Visual Studio pro Mac.](tutorials/using-on-mac-vs-full-solution.md)

Seznam podporovaných verzí OS X/macOS najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?tabs=netcore30&pivots=os-macos) .

---
