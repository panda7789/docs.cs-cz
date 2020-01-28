---
title: Použití sady Compatibility Pack systému Windows k portu kódu .NET Core
description: Přečtěte si o sadě Windows Compatibility Pack a o tom, jak ji můžete použít k portování existujícího kódu .NET Framework do .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 91a653b2345d414c18ebdb6e8b7d6d49bbdbb83e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733608"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Použití sady Compatibility Pack systému Windows k portu kódu .NET Core

Některé nejběžnější problémy nalezené při přenosu stávajícího kódu do .NET Core jsou závislosti na rozhraních API a technologiích, které se nacházejí pouze v .NET Framework. *Sada Windows Compatibility Pack* poskytuje mnoho z těchto technologií, takže je mnohem snazší sestavovat aplikace .NET Core a knihovny .NET Standard.

Sada Compatibility Pack je logické [rozšíření .NET Standard 2,0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) , které významně zvyšuje sadu rozhraní API. Existující kód se zkompiluje téměř bez úprav. Aby se zajistilo, že se jedná o sadu rozhraní API, která poskytují všechny implementace rozhraní .NET, .NET Standard nezahrnuje technologie, které nemůžou fungovat na všech platformách, jako je registr, rozhraní WMI (Windows Management Instrumentation) (WMI) nebo rozhraní API pro vygenerování reflexe. Sada Compatibility Pack systému Windows je umístěna na .NET Standard a poskytuje přístup k těmto technologiím, které jsou výhradně pro Windows. To je zvlášť užitečné pro zákazníky, kteří se chtějí přesunout do .NET Core, ale naplánovat, aby se v systému Windows naplánovaly, a to aspoň jako první krok. V takovém případě je možné použít technologie jenom pro Windows k odebrání prahu migrace.

## <a name="package-contents"></a>Obsah balíčku

Sada Windows Compatibility Pack je poskytována prostřednictvím [balíčku NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) a může být odkazována z projektů, které cílí na rozhraní .NET Core nebo .NET Standard.

Poskytuje informace o rozhraních API 20 000, včetně pouze Windows, stejně jako rozhraní API pro různé platformy z následujících technologických oblastí:

- Znakové stránky
- CodeDom
- Konfigurace
- Adresářové služby
- Tažné
- ODBC
- Oprávnění
- Porty
- Seznamy Windows Access Control (ACL)
- Windows Communication Foundation (WCF)
- Kryptografie systému Windows
- Windows EventLog
- Služba WMI (Windows Management Instrumentation)
- Čítače výkonu Windows
- Registr systému Windows
- Ukládání prostředí Windows Runtime do mezipaměti
- Služby systému Windows

Další informace najdete v tématu [specifikace sady Compatibility Pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Začínáme

1. Před přenosem se ujistěte, že se podíváte na [proces přenosu](index.md).

2. Při přenosu stávajícího kódu do rozhraní .NET Core nebo .NET Standard nainstalujte [balíček NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

   Pokud chcete zůstat v systému Windows, je vše nastavené.

3. Pokud chcete spustit aplikaci .NET Core nebo knihovnu .NET Standard v systému Linux nebo macOS, pomocí [analyzátoru rozhraní API](../../standard/analyzers/api-analyzer.md) vyhledejte využití rozhraní API, které nebude fungovat pro různé platformy.

4. Buď odeberte použití těchto rozhraní API, nahraďte je alternativami pro různé platformy nebo je Zabezpečte pomocí kontroly platformy, například:

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

Ukázku najdete ve [videu kanálu 9 sady Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).
