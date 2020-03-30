---
title: Úvod a přehled .NET Core
description: .NET Core je modulární, vysoce výkonná implementace rozhraní .NET pro vytváření aplikací pro Windows, Linux a macOS. Další informace o .NET Core pro started a) začínáme.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: a20cdda5cbd366d04e7ee9e8df3d1b15d10c1f4a
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391158"
---
# <a name="introduction-to-net-core"></a>Úvod do rozhraní .NET Core

[.NET Core](about.md) je [open-source,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)univerzální vývojová platforma. Můžete vytvářet aplikace .NET Core pro procesory Windows, macOS a Linux pro procesory x64, x86, ARM32 a ARM64 pomocí více programovacích jazyků. Architektury a rozhraní API jsou k dispozici pro [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [klientské ui](/dotnet/desktop-wpf/overview/index)a [strojové učení](/dotnet/machine-learning/).

[Stáhněte si sdk jádra .NET a](https://dotnet.microsoft.com/download) vyzkoušejte v počítači .NET Core. Nejnovější verze je [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

## <a name="download-net-core"></a>Stáhnout jádro rozhraní .NET

Jádro .NET můžete získat následujícími způsoby:

* [Instalační programy pro Windows a macOS](https://dotnet.microsoft.com/download)
* [Balíčky linuxu](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [Kontejnery Dockeru](https://hub.docker.com/_/microsoft-dotnet-core/)
* [Zipy a dehtové kuličky](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [Instalace skriptů](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [Poznámky k verzi](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a>Vytvoření první aplikace

Po instalaci sady .NET Core SDK otevřete příkazový řádek. K vytvoření a spuštění aplikace použijte následující příkazy:

```dotnetcli
dotnet new console
dotnet run
```

Měl by se zobrazit následující výstup:

```output
Hello World!
```

## <a name="contribute"></a>Přispět

.NET Core je otevřená platforma. Všichni jsou vítáni k účasti.

* Soubor problémy s produkty a otázky na [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).
* Příspěvky na produkt by měly být provedeny v jednom z úložišť projektů, jako je [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn)nebo [aspnetcore](https://github.com/dotnet/aspnetcore). Další informace naleznete [v tématu úložiště jádra .NET](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).

## <a name="support"></a>Podpora

.NET Core je podporován společností Microsoft v systémech Windows, macOS a Linux a Red Hat na Red Hat Enterprise Linux.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurzy jádra .NET](tutorials/index.md)

> [!div class="nextstepaction"]
> [Vyzkoušejte v prohlížeči rozhraní .NET Core](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
