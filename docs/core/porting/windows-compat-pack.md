---
title: Použití sady Windows Compatibility Pack k portu kódu do jádra rozhraní .NET
description: Informace o nástroji Compatibility Pack pro systém Windows a o tom, jak ji můžete použít k portování existujícího kódu rozhraní .NET Framework do jádra .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 166259ca37a2005d67f6c545e4843a940f05fb71
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80228640"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a>Použití sady Windows Compatibility Pack k portu kódu do jádra rozhraní .NET

Některé z nejběžnějších problémů nalezených při přenosu existujícího kódu do jádra .NET jsou závislosti na rozhraních API a technologiích, které se nacházejí pouze v rozhraní .NET Framework. *Sada Windows Compatibility Pack* poskytuje mnoho z těchto technologií, takže je mnohem jednodušší vytvářet aplikace .NET Core a knihovny .NET Standard.

Balíček compatibility pack je logické [rozšíření .NET Standard 2.0,](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) které výrazně zvyšuje sadu rozhraní API. Existující kód se zkompiluje téměř bez úprav. Chcete-li zachovat svůj příslib "sadu rozhraní API, které poskytují všechny implementace rozhraní .NET", .NET Standard nezahrnuje technologie, které nemohou fungovat na všech platformách, jako je například registr, WMI (Windows Management Instrumentation) nebo reflexe vyzařují rozhraní API. Sada Kompatibilita systému Windows je na rozhraní .NET Standard a poskytuje přístup k těmto technologiím pouze pro systém Windows. Je to užitečné zejména pro zákazníky, kteří se chtějí přesunout do .NET Core, ale plánují zůstat v systému Windows, alespoň jako první krok. V tomto scénáři možnost používat technologie pouze systému Windows odstraňuje překážku migrace.

## <a name="package-contents"></a>Obsah balení

Sada Kompatibilita systému Windows je poskytována prostřednictvím [balíčku Microsoft.Windows.Compatibility NuGet](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) a lze na něj odkazovat z projektů, které cílí na .NET Core nebo .NET Standard.

Poskytuje přibližně 20 000 oken API, včetně pouze systémových oken a také multiplatformních api z následujících technologických oblastí:

- Znakové stránky
- Codedom
- Konfigurace
- Adresářové služby
- Kresba
- ODBC
- Oprávnění
- Porty
- Seznamy řízení přístupu systému Windows (ACL)
- Windows Communication Foundation (WCF)
- Kryptografie systému Windows
- Protokol událostí systému Windows
- Windows Management Instrumentation (WMI)
- Čítače výkonu systému Windows
- Registr Windows
- Ukládání do mezipaměti prostředí Windows Runtime
- Služby systému Windows

Další informace naleznete ve [specifikaci sady Compatibility Pack](https://github.com/dotnet/designs/blob/master/accepted/2018/compat-pack/compat-pack.md).

## <a name="get-started"></a>Začínáme

1. Před přenesením se nezapomeňte podívat na [proces přenosu](index.md).

2. Při přenosu existujícího kódu do rozhraní .NET Core nebo .NET Standard nainstalujte [balíček NuGet microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).

   Pokud chcete zůstat ve Windows, máte vše nastaveno.

3. Pokud chcete spustit aplikaci .NET Core nebo knihovnu .NET Standard v Systému Linux nebo macOS, použijte [analyzátor rozhraní API](../../standard/analyzers/api-analyzer.md) k vyhledání využití rozhraní API, která nebudou fungovat napříč platformami.

4. Buď odeberte použití těchto api, nahraďte je alternativami pro různé platformy, nebo je střežte pomocí kontroly platformy, například:

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

Ukázku najdete ve [videu kanálu 9 v balíčku Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).
