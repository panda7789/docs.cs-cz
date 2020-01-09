---
title: Použití sady Compatibility Pack systému Windows k portu kódu .NET Core
description: Přečtěte si o sadě Windows Compatibility Pack a o tom, jak ji můžete použít k portování existujícího kódu .NET Framework do .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 65530987a3cded941b6a292118ed9bfdb6f5b86c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715471"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Použití sady Compatibility Pack systému Windows k portu kódu .NET Core

Některé nejběžnější problémy nalezené při přenosu stávajícího kódu do .NET Core jsou závislosti na rozhraních API a technologiích, které se nacházejí pouze v .NET Framework. *Sada Windows Compatibility Pack* poskytuje mnoho z těchto technologií, takže je mnohem snazší sestavovat aplikace .NET Core a knihovny .NET Standard.

Tento balíček je logickým [rozšířením .NET Standard 2,0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) , které významně zvyšuje sadu rozhraní API a zkompiluje existující kód s téměř bez úprav. Aby se zajistila snaha o .NET Standard ("je to sada rozhraní API, která poskytuje všechny implementace rozhraní .NET"), sada neobsahuje technologie, které nemůžou fungovat na všech platformách, jako je registr, rozhraní WMI (Windows Management Instrumentation) (WMI) nebo generování reflexe. Třídy.

Sada Compatibility Pack systému Windows je umístěna na .NET Standard a poskytuje přístup pouze k technologiím, které jsou v systému Windows. Je zvláště užitečné pro zákazníky, kteří se chtějí přesunout do .NET Core, ale naplánovat, aby v systému Windows zůstali jako první krok. V takovém případě není možné používat technologie jenom pro Windows, ale jenom migrační systém bez výhod architektury.

## <a name="package-contents"></a>Obsah balíčku

Sada Windows Compatibility Pack je poskytována prostřednictvím [balíčku NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) a může být odkazována z projektů, které cílí na rozhraní .NET Core nebo .NET Standard.

Poskytuje informace o rozhraních API 20 000, včetně pouze Windows, stejně jako rozhraní API pro různé platformy z následujících technologických oblastí:

- Znakové stránky
- CodeDom
- Konfigurace
- Adresářové služby
- Kreslení
- ODBC
- Oprávnění
- Porty
- Seznamy Windows Access Control (ACL)
- Windows Communication Foundation (WCF)
- Kryptografie systému Windows
- Windows EventLog
- Služba WMI (Windows Management Instrumentation)
- Čítače výkonu Windows
- Registr Windows
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
