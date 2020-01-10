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
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="2d055-103">Použití sady Compatibility Pack systému Windows k portu kódu .NET Core</span><span class="sxs-lookup"><span data-stu-id="2d055-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="2d055-104">Některé nejběžnější problémy nalezené při přenosu stávajícího kódu do .NET Core jsou závislosti na rozhraních API a technologiích, které se nacházejí pouze v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d055-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="2d055-105">*Sada Windows Compatibility Pack* poskytuje mnoho z těchto technologií, takže je mnohem snazší sestavovat aplikace .NET Core a knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2d055-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="2d055-106">Tento balíček je logickým [rozšířením .NET Standard 2,0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) , které významně zvyšuje sadu rozhraní API a zkompiluje existující kód s téměř bez úprav.</span><span class="sxs-lookup"><span data-stu-id="2d055-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="2d055-107">Aby se zajistila snaha o .NET Standard ("je to sada rozhraní API, která poskytuje všechny implementace rozhraní .NET"), sada neobsahuje technologie, které nemůžou fungovat na všech platformách, jako je registr, rozhraní WMI (Windows Management Instrumentation) (WMI) nebo generování reflexe. Třídy.</span><span class="sxs-lookup"><span data-stu-id="2d055-107">In order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), the pack doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="2d055-108">Sada Compatibility Pack systému Windows je umístěna na .NET Standard a poskytuje přístup pouze k technologiím, které jsou v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2d055-108">The Windows Compatibility Pack sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="2d055-109">Je zvláště užitečné pro zákazníky, kteří se chtějí přesunout do .NET Core, ale naplánovat, aby v systému Windows zůstali jako první krok.</span><span class="sxs-lookup"><span data-stu-id="2d055-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="2d055-110">V takovém případě není možné používat technologie jenom pro Windows, ale jenom migrační systém bez výhod architektury.</span><span class="sxs-lookup"><span data-stu-id="2d055-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with no architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="2d055-111">Obsah balíčku</span><span class="sxs-lookup"><span data-stu-id="2d055-111">Package contents</span></span>

<span data-ttu-id="2d055-112">Sada Windows Compatibility Pack je poskytována prostřednictvím [balíčku NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) a může být odkazována z projektů, které cílí na rozhraní .NET Core nebo .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="2d055-112">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET Core or .NET Standard.</span></span>

<span data-ttu-id="2d055-113">Poskytuje informace o rozhraních API 20 000, včetně pouze Windows, stejně jako rozhraní API pro různé platformy z následujících technologických oblastí:</span><span class="sxs-lookup"><span data-stu-id="2d055-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="2d055-114">Znakové stránky</span><span class="sxs-lookup"><span data-stu-id="2d055-114">Code Pages</span></span>
- <span data-ttu-id="2d055-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="2d055-115">CodeDom</span></span>
- <span data-ttu-id="2d055-116">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="2d055-116">Configuration</span></span>
- <span data-ttu-id="2d055-117">Adresářové služby</span><span class="sxs-lookup"><span data-stu-id="2d055-117">Directory Services</span></span>
- <span data-ttu-id="2d055-118">Kreslení</span><span class="sxs-lookup"><span data-stu-id="2d055-118">Drawing</span></span>
- <span data-ttu-id="2d055-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="2d055-119">ODBC</span></span>
- <span data-ttu-id="2d055-120">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="2d055-120">Permissions</span></span>
- <span data-ttu-id="2d055-121">Porty</span><span class="sxs-lookup"><span data-stu-id="2d055-121">Ports</span></span>
- <span data-ttu-id="2d055-122">Seznamy Windows Access Control (ACL)</span><span class="sxs-lookup"><span data-stu-id="2d055-122">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="2d055-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="2d055-123">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="2d055-124">Kryptografie systému Windows</span><span class="sxs-lookup"><span data-stu-id="2d055-124">Windows Cryptography</span></span>
- <span data-ttu-id="2d055-125">Windows EventLog</span><span class="sxs-lookup"><span data-stu-id="2d055-125">Windows EventLog</span></span>
- <span data-ttu-id="2d055-126">Služba WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="2d055-126">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="2d055-127">Čítače výkonu Windows</span><span class="sxs-lookup"><span data-stu-id="2d055-127">Windows Performance Counters</span></span>
- <span data-ttu-id="2d055-128">Registr Windows</span><span class="sxs-lookup"><span data-stu-id="2d055-128">Windows Registry</span></span>
- <span data-ttu-id="2d055-129">Ukládání prostředí Windows Runtime do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="2d055-129">Windows Runtime Caching</span></span>
- <span data-ttu-id="2d055-130">Služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="2d055-130">Windows Services</span></span>

<span data-ttu-id="2d055-131">Další informace najdete v tématu [specifikace sady Compatibility Pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="2d055-131">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="2d055-132">Začínáme</span><span class="sxs-lookup"><span data-stu-id="2d055-132">Get started</span></span>

1. <span data-ttu-id="2d055-133">Před přenosem se ujistěte, že se podíváte na [proces přenosu](index.md).</span><span class="sxs-lookup"><span data-stu-id="2d055-133">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="2d055-134">Při přenosu stávajícího kódu do rozhraní .NET Core nebo .NET Standard nainstalujte [balíček NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="2d055-134">When porting existing code to .NET Core or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="2d055-135">Pokud chcete zůstat v systému Windows, je vše nastavené.</span><span class="sxs-lookup"><span data-stu-id="2d055-135">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="2d055-136">Pokud chcete spustit aplikaci .NET Core nebo knihovnu .NET Standard v systému Linux nebo macOS, pomocí [analyzátoru rozhraní API](../../standard/analyzers/api-analyzer.md) vyhledejte využití rozhraní API, které nebude fungovat pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="2d055-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="2d055-137">Buď odeberte použití těchto rozhraní API, nahraďte je alternativami pro různé platformy nebo je Zabezpečte pomocí kontroly platformy, například:</span><span class="sxs-lookup"><span data-stu-id="2d055-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="2d055-138">Ukázku najdete ve [videu kanálu 9 sady Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="2d055-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
