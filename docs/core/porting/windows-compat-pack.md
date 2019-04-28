---
title: Použití sady Windows Compatibility Pack port kódu až po .NET Core
description: Další informace o Windows Compatibility Pack a jak můžete pomocí jeho port existujícího kódu rozhraní .NET Framework do .NET Core
author: terrajobst
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: c4fd888e0fbce86ab317f18fd77374af5d3ca244
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663099"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Použití sady Windows Compatibility Pack port kódu až po .NET Core

Některé z nejběžnějších problémů zjištěných při přenášíte stávající kód až po .NET Core jsou závislosti na rozhraní API a technologií, které se nacházejí pouze v rozhraní .NET Framework. *Windows Compatibility Pack* poskytuje mnoho z těchto technologií tak, aby byl mnohem jednodušší vytvářet aplikace .NET Core a knihovny .NET Standard.

Tento balíček je logické [rozšíření .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) , výrazně zvyšuje sada rozhraní API a existující kód zkompiluje téměř bez možnosti úprav. Ale pokud chcete zachovat uskutečnění .NET Standard ("je sada rozhraní API, která poskytují všechny implementace .NET"), to nezahrnuli technologie, které nemůže pracovat na všech platformách, jako je například registru Windows Management Instrumentation (WMI), nebo generování reflexe Rozhraní API.

*Windows Compatibility Pack* nachází nad .NET Standard a poskytuje přístup k technologiím, které jsou pouze Windows. To je obzvláště užitečné pro zákazníky, které chcete přesunout do .NET Core, ale plán zůstat na Windows jako první krok. V takovém scénáři nebude moct používat jenom pro Windows technologie je pouze mezní migrace s nulovou výhody architektury.

## <a name="package-contents"></a>Obsah balíčku

*Windows Compatibility Pack* je k dispozici prostřednictvím balíčku NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) a můžete na něj odkazovat z projektů, které cílí na .NET Core nebo .NET Standard.

Poskytuje informace o 20 000 rozhraní API, včetně jen pro Windows i multiplatformní rozhraní API z těchto oblastí technologie:

* Znakové stránky
* CodeDom
* Konfigurace
* Adresářové služby
* Kreslení
* ODBC
* Oprávnění
* Porty
* Windows seznamy řízení přístupu (ACL)
* Windows Communication Foundation (WCF)
* Windows Cryptography
* Windows EventLog
* Windows Management Instrumentation (WMI)
* Čítače výkonu Windows
* Registru Windows
* Ukládání do mezipaměti Windows Runtime
* Služby systému Windows

Další informace najdete v tématu [specifikace sady kompatibility](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Začínáme

1. Před přenos, ujistěte se, že se podívat na [portování procesu](index.md).

2. Pokud přenášíte stávající kód .NET Core nebo .NET Standard, nainstalujte balíček NuGet [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

3. Pokud budete chtít zůstat na Windows, všechno je nastavené.

4. Pokud chcete spustit aplikaci .NET Core nebo .NET Standard knihovny v Linuxu nebo macOS, použijte [analyzátor rozhraní API](https://devblogs.microsoft.com/dotnet/introducing-api-analyzer/) najít využití rozhraní API, která nebude fungovat napříč platformami.

5. Odeberte použití těchto rozhraní API, je nahradit alternativami napříč platformami nebo chránit je pomocí kontroly platformy, jako jsou:

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

Předváděcí akci, podívejte se [videa Channel 9 sady Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).
