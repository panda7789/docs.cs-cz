---
title: Úvod k .NET Core a přehled
description: .NET Core je modulární a vysoce výkonná implementace .NET pro vytváření aplikací pro Windows, Linux a macOS. Seznamte se s .NET Core, abyste mohli začít.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: b28ad965e54680e2e1134c389266741ade28084f
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226579"
---
# <a name="introduction-to-net-core"></a>Úvod do .NET Core

[.NET Core](about.md) je [Open Source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)vývojová platforma pro obecné účely. Můžete vytvářet aplikace .NET Core pro Windows, macOS a Linux pro procesory x64, x86, ARM32 a ARM64 pomocí několika programovacích jazyků. K dispozici jsou architektury a rozhraní API pro [Cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [klientské uživatelské rozhraní](../desktop-wpf/overview/index.md)a [strojové učení](/dotnet/machine-learning/).

[Stáhněte si .NET Core SDK](https://dotnet.microsoft.com/download) a vyzkoušejte na svém počítači .NET Core. Nejnovější verze je [.NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

## <a name="download-net-core"></a>Stáhnout .NET Core

.NET Core můžete získat následujícími způsoby:

* [Instalační programy pro Windows a macOS](https://dotnet.microsoft.com/download)
* [Balíčky Linux](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [Kontejnery Dockeru](https://hub.docker.com/_/microsoft-dotnet-core/)
* [Zips a tarballs](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [Nainstalovat skripty](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [Zpráva k vydání verze](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a>Vytvoření první aplikace

Po instalaci .NET Core SDK otevřete příkazový řádek. K vytvoření a spuštění aplikace použijte následující příkazy:

```dotnetcli
dotnet new console
dotnet run
```

Měl by se zobrazit následující výstup:

```output
Hello World!
```

## <a name="contribute"></a>Přispět

.NET Core je otevřená platforma. Všichni uživatelé jsou vítají účast.

* Problémy se souborovým produktem a dotazy na [komunitě vývojářů](https://developercommunity.visualstudio.com/spaces/61/index.html).
* Příspěvky na produkt by se měly provádět v jednom z úložišť projektů, jako je například [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/SDK](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn)nebo [aspnetcore](https://github.com/dotnet/aspnetcore). Další informace najdete v tématu [úložišť .NET Core](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).

## <a name="support"></a>Podpora

.NET Core podporuje Microsoft na Windows, macOS a Linux a Red Hat na Red Hat Enterprise Linux.

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [Kurzy k .NET Core](tutorials/index.md)

> [!div class="nextstepaction"]
> [Vyzkoušejte .NET Core v prohlížeči](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
