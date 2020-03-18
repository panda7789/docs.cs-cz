---
title: Začínáme s rozhraním .NET Core
description: Najděte materiály, kde se dozvíte, jak vytvářet aplikace .NET Core ve Windows, Linuxu a macOS.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 0968d9db1dbfbdc8c586328ee8e02315f17950b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714394"
---
# <a name="get-started-with-net-core"></a>Začínáme s rozhraním .NET Core

Tento článek obsahuje informace o začínáme s .NET Core. .NET Core lze nainstalovat do Windows, Linux a macOS. Můžete kódovat ve svém oblíbeném textovém editoru a vytvářet knihovny a aplikace pro různé platformy.

Pokud si nejste jisti, co je jádro .NET core nebo jak se vztahuje k jiným technologiím .NET, začněte s přehledem [What is .NET.](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) Jednoduše řečeno, .NET Core je open source implementace .NET napříč platformami.

## <a name="create-an-application"></a>Vytvoření aplikace

Nejprve stáhněte a nainstalujte do počítače sadu [.NET Core SDK.](https://dotnet.microsoft.com/download)

Dále otevřete terminál, například **PowerShell**, **Příkazový řádek**nebo **bash**. Zadejte `dotnet` následující příkazy pro vytvoření a spuštění aplikace jazyka C#:

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

Měl by se zobrazit následující výstup:

```console
Hello World!
```

Blahopřejeme! Vytvořili jste jednoduchou aplikaci .NET Core. K vytvoření aplikace .NET Core můžete také použít [kód sady Visual Studio](./tutorials/with-visual-studio-code.md), Visual [Studio](./tutorials/with-visual-studio.md) (jenom windows) nebo Visual Studio [pro Mac](./tutorials/using-on-mac-vs.md) (pouze macOS).

## <a name="tutorials"></a>Kurzy

Začínáme s vývojem základních aplikací .NET podle těchto podrobných kurzů:

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

- [Vytvoření první aplikace konzoly .NET Core ve Visual Studiu 2019](./tutorials/with-visual-studio.md)
- [Vytvoření knihovny tříd se standardem .NET standard v sadě Visual Studio](./tutorials/library-with-visual-studio.md)
- [Začínáme s rozhraním .NET Core pomocí rozhraní CLI jádra .NET](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![ikona filmové kamery pro video](./media/video-icon.png "Podívejte se na video") | Podívejte [se, jak nainstalovat a používat visual studio kód a .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video na kanálu 9. |
| ![ikona filmové kamery pro video](./media/video-icon.png "Podívejte se na video") | Podívejte se na videa [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) na YouTube. |

Seznam podporovaných verzí systému Windows naleznete v článku [závislosti a požadavky jádra .NET.](install/dependencies.md?pivots=os-windows)

# <a name="linux"></a>[Linux](#tab/linux)

Začínáme s vývojem základních aplikací .NET podle těchto podrobných kurzů:

- [Začínáme s rozhraním .NET Core pomocí příkazového řádku](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| ![ikona filmové kamery pro video](./media/video-icon.png "Podívejte se na video") | Podívejte se na video o [tom, jak začít s visual studio kód pomocí C# a .NET Core na Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu). |

Seznam podporovaných distribucí a verzí linuxu naleznete v článku [o závislostech a požadavcích jádra .NET.](install/dependencies.md?pivots=os-linux)

# <a name="macos"></a>[Macos](#tab/macos)

Začínáme s vývojem základních aplikací .NET podle těchto podrobných kurzů:

- [Začínáme s .NET Core v systému macOS pomocí sady Visual Studio Code](./tutorials/using-on-macos.md)
- [Začínáme s rozhraním .NET Core pomocí příkazového řádku](./tutorials/cli-create-console-app.md)
- [Začínáme s .NET Core v systému macOS pomocí sady Visual Studio pro Mac](./tutorials/using-on-mac-vs.md)
- [Vytvoření kompletního řešení .NET Core na macOS pomocí Visual Studia pro Mac](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| ![ikona filmové kamery pro video](media/video-icon.png "Podívejte se na video") | Podívejte se na video o [tom, jak začít s visual studio kód pomocí C# a .NET Core na macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac). |

Seznam podporovaných verzí OS X / macOS najdete v článku [o závislostech a požadavcích jádra .NET.](install/dependencies.md?pivots=os-macos)

---
