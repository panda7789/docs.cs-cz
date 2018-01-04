---
title: "Portování do .NET Core - pomocí balíčku Windows kompatibility"
description: "Další informace o Windows Pack kompatibility a jak můžete ji použít k portu existující kód rozhraní .NET Framework na .NET Core"
keywords: "Rozhraní .NET, rozhraní .NET core, Windows, kompatibility"
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net-core
ms.workload: dotnetcore
ms.openlocfilehash: 3b1fe02aad4f78499158ecb7fa9b8521cb7d992e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="using-the-windows-compatibility-pack"></a>Pomocí balíčku Windows kompatibility

Jednou z nejběžnějších problémů, které vývojáři čelí při portování svůj existující kód na .NET Core je, jsou závislé na rozhraní API a technologie, které existují pouze v rozhraní .NET Framework. *Windows kompatibility Pack* je o zajišťování řada těchto technologii tak, aby vytváření aplikace .NET Core a také .NET standardní knihovny stalo mnohem víc přijatelná pro existující kód.

Tento balíček je logickou [rozšíření rozhraní .NET 2.0 standardní](../whats-new/index.md#api-changes-and-library-support) že výrazně zvyšuje sada rozhraní API a existující kód zkompiluje téměř beze změn. Ale chcete-li zachovat potenciálu .NET Standard ("je sada rozhraní API, které poskytují všechny implementace rozhraní .NET"), to nezahrnuli technologie, které nemůže pracovat pro všechny platformy, jako je například registr, systém Windows Management Instrumentation (WMI), nebo emitování reflexe Rozhraní API.

*Windows kompatibility Pack* je umístěna nad .NET Standard a poskytuje přístup k technologie, které jsou pouze v systému Windows. Je obzvláště užitečná pro zákazníky, které chcete přesunout do .NET Core, ale chcete zůstat v systému Windows jako první krok. V tomto scénáři nebude moci používat pouze pro systém Windows technologie je pouze mezní migrace nulové architektury výhod.

## <a name="package-contents"></a>Obsah balíčku

*Windows kompatibility Pack* je k dispozici prostřednictvím balíčku NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) a můžete na něj odkazovat z projektů cílení na .NET Core nebo .NET Standard.

Poskytuje přibližně 20 000 rozhraní API, včetně pouze pro systém Windows a také napříč platformami rozhraní API z těchto oblastí technologie:

* Znakové stránky
* Modelu codeDom
* Konfigurace
* Adresářové služby
* Kreslení
* ODBC
* Oprávnění
* Porty
* Seznamy řízení přístupu (ACL)
* Windows Communication Foundation (WCF)
* Kryptografie systému Windows
* Protokol událostí systému Windows
* Windows Management Instrumentation (WMI)
* Čítače výkonu systému Windows
* Registru systému Windows
* Ukládání do mezipaměti Windows Runtime
* Služby systému Windows

Další informace najdete v tématu [specifikace sady kompatibility](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Začínáme

1. Před přenosem, nezapomeňte si prohlédněte [portování proces](index.md).

2. Když portování stávajícího kódu pro .NET Core nebo .NET Standard, nainstalujte balíček NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

3. Pokud chcete zůstat v systému Windows, je vše připraveno.

4. Pokud chcete spustit aplikace .NET Core nebo .NET Standard knihovny na Linuxu nebo systému macOS, použijte [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) najít využití rozhraní API, která nebude fungovat napříč platformami.

5. Buď odeberte použití těchto rozhraní API, je nahradit alternativami napříč platformami nebo pomocí platformy kontrolu, jako je ochrana:

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

Pro ukázku, podívejte se [Channel 9 video kompatibility sady Windows](https://channel9.msdn.com/Events/Connect/2017/T123).

