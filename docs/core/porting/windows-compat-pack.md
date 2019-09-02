---
title: Použití sady Compatibility Pack systému Windows k portu kódu .NET Core
description: Přečtěte si o sadě Windows Compatibility Pack a o tom, jak ji můžete použít k portování existujícího kódu .NET Framework do .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 71e390881d4e9c7836622abeed49c0ea2e5f7526
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202560"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Použití sady Compatibility Pack systému Windows k portu kódu .NET Core

Některé nejběžnější problémy nalezené při přenosu stávajícího kódu do .NET Core jsou závislosti na rozhraních API a technologiích, které se nacházejí pouze v .NET Framework. *Sada Windows Compatibility Pack* poskytuje mnoho z těchto technologií, takže je mnohem snazší sestavovat aplikace .NET Core a knihovny .NET Standard.

Tento balíček je logickým [rozšířením .NET Standard 2,0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) , které významně zvyšuje sadu rozhraní API a zkompiluje existující kód s téměř bez úprav. Pokud ale chcete zachovat příslib .NET Standard ("je to sada rozhraní API, která poskytuje všechny implementace rozhraní .NET"), nezahrnuje technologie, které nemůžou fungovat na všech platformách, jako je registr, rozhraní WMI (Windows Management Instrumentation) (WMI) nebo generování reflexe. Třídy.

*Sada Compatibility Pack systému Windows* je umístěna na .NET Standard a poskytuje přístup pouze k technologiím, které jsou v systému Windows. Je zvláště užitečné pro zákazníky, kteří se chtějí přesunout do .NET Core, ale naplánovat, aby v systému Windows zůstali jako první krok. V takovém případě není možné používat technologie jenom pro Windows, ale jenom migrační systém s nulovými výhodami architektury.

## <a name="package-contents"></a>Obsah balíčku

*Sada Windows Compatibility Pack* je poskytována prostřednictvím balíčku NuGet [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) a lze na ně odkazovat z projektů cílících na rozhraní .NET Core nebo .NET Standard.

Poskytuje informace o rozhraních API 20 000, včetně pouze Windows, stejně jako rozhraní API pro různé platformy z následujících technologických oblastí:

* Znakové stránky
* CodeDom
* Konfiguraci
* Adresářové služby
* Tažné
* ODBC
* Oprávnění
* Porty
* Seznamy Windows Access Control (ACL)
* Windows Communication Foundation (WCF)
* Kryptografie systému Windows
* Windows EventLog
* Rozhraní WMI (Windows Management Instrumentation) (WMI)
* Čítače výkonu systému Windows
* Registr systému Windows
* Ukládání prostředí Windows Runtime do mezipaměti
* Služby systému Windows

Další informace najdete v tématu [specifikace sady Compatibility Pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).

## <a name="get-started"></a>Začínáme

1. Před přenosem se ujistěte, že se podíváte na [proces přenosu](index.md).

2. Při přenosu stávajícího kódu do rozhraní .NET Core nebo .NET Standard nainstalujte balíček NuGet [Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

3. Pokud chcete zůstat v systému Windows, je vše nastavené.

4. Pokud chcete spustit aplikaci .NET Core nebo knihovnu .NET Standard v systému Linux nebo macOS, pomocí [analyzátoru rozhraní API](../../standard/analyzers/api-analyzer.md) vyhledejte využití rozhraní API, které nebude fungovat pro různé platformy.

5. Buď odeberte použití těchto rozhraní API, nahraďte je alternativami pro různé platformy nebo je Zabezpečte pomocí kontroly platformy, například:

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
