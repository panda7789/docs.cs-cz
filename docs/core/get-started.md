---
title: Začínáme s .NET Core
description: Vyhledejte prostředky, které se naučíte sestavovat aplikace .NET Core v systémech Windows, Linux a macOS.
author: adegeo
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 56eebc0fc5bad6f57d93358cbbef389d6355d66b
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656687"
---
# <a name="get-started-with-net-core"></a>Začínáme s .NET Core

Tento článek poskytuje informace o tom, jak začít s .NET Core. .NET Core se dá nainstalovat na Windows, Linux a macOS. Můžete kódovat ve svém oblíbeném textovém editoru a vytvářejte knihovny a aplikace pro více platforem.

Pokud si nejste jistí, co je .NET Core nebo jak souvisí s dalšími technologiemi .NET, začněte s přehledem [co je .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) . Jednoduše řečeno, .NET Core je open source implementace .NET pro více platforem.

## <a name="create-an-application"></a>Vytvoření aplikace

Nejprve Stáhněte a nainstalujte [.NET Core SDK](https://dotnet.microsoft.com/download) do počítače.

Pak otevřete terminál, jako je například **PowerShell**, **příkazový řádek**nebo **bash**. Zadejte následující `dotnet` příkazy pro vytvoření a spuštění aplikace v jazyce C#:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Měl by se zobrazit následující výstup:

```console
Hello World!
```

Congratulations! Vytvořili jste jednoduchou aplikaci .NET Core. K vytvoření aplikace .NET Core můžete použít taky [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (jenom Windows) nebo [Visual Studio pro Mac](tutorials/with-visual-studio-mac.md) (jenom MacOS).

## <a name="tutorials"></a>Kurzy

Začněte vyvíjet aplikace .NET Core pomocí následujících podrobných kurzů:

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

- [Vytvoření první konzolové aplikace .NET Core v aplikaci Visual Studio 2019](./tutorials/with-visual-studio.md)
- [Sestavení knihovny tříd pomocí .NET Standard v aplikaci Visual Studio](./tutorials/library-with-visual-studio.md)
- [Kurz: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio Code](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| ![ikona filmové kamery pro video](./media/video-icon.png "Přehrát video") | Podívejte se, [Jak nainstalovat a používat Visual Studio Code a video .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) na Channel 9. |
| ![ikona filmové kamery pro video](./media/video-icon.png "Přehrát video") | Podívejte se na videa k [platformě .NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) na YouTube. |

Seznam podporovaných verzí Windows najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?pivots=os-windows) .

# <a name="linux"></a>[Linux](#tab/linux)

Začněte vyvíjet aplikace .NET Core pomocí následujících podrobných kurzů:

- [Kurz: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio Code](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| ![ikona filmové kamery pro video](./media/video-icon.png "Přehrát video") | Podívejte se na video o [zahájení práce s Visual Studio Code pomocí C# a .NET Core v Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu). |

Seznam podporovaných distribuce a verzí pro Linux najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?pivots=os-linux) .

# <a name="macos"></a>[macOS](#tab/macos)

Začněte vyvíjet aplikace .NET Core pomocí následujících podrobných kurzů:

- [Kurz: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio Code](tutorials/with-visual-studio-code.md)
- [Kurz: Vytvoření konzolové aplikace .NET Core pomocí Visual Studio pro Mac](tutorials/with-visual-studio-mac.md)
- [Sestavení knihovny .NET Standard v macOS pomocí Visual Studio pro Mac](tutorials/library-with-visual-studio-mac.md)

|   |   |
|---|---|
| ![ikona filmové kamery pro video](media/video-icon.png "Přehrát video") | Podívejte se na video o [zahájení práce s Visual Studio Code pomocí C# a .NET Core v MacOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac). |

Seznam podporovaných verzí OS X/macOS najdete v článku [závislosti a požadavky .NET Core](install/dependencies.md?pivots=os-macos) .

---
