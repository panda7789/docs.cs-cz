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
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="fff3c-103">Použití sady Compatibility Pack systému Windows k portu kódu .NET Core</span><span class="sxs-lookup"><span data-stu-id="fff3c-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="fff3c-104">Některé nejběžnější problémy nalezené při přenosu stávajícího kódu do .NET Core jsou závislosti na rozhraních API a technologiích, které se nacházejí pouze v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fff3c-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="fff3c-105">*Sada Windows Compatibility Pack* poskytuje mnoho z těchto technologií, takže je mnohem snazší sestavovat aplikace .NET Core a knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="fff3c-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="fff3c-106">Sada Compatibility Pack je logické [rozšíření .NET Standard 2,0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) , které významně zvyšuje sadu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="fff3c-106">The compatibility pack is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases the API set.</span></span> <span data-ttu-id="fff3c-107">Existující kód se zkompiluje téměř bez úprav.</span><span class="sxs-lookup"><span data-stu-id="fff3c-107">Existing code compiles with almost no modifications.</span></span> <span data-ttu-id="fff3c-108">Aby se zajistilo, že se jedná o sadu rozhraní API, která poskytují všechny implementace rozhraní .NET, .NET Standard nezahrnuje technologie, které nemůžou fungovat na všech platformách, jako je registr, rozhraní WMI (Windows Management Instrumentation) (WMI) nebo rozhraní API pro vygenerování reflexe.</span><span class="sxs-lookup"><span data-stu-id="fff3c-108">To keep its promise of "the set of APIs that all .NET implementations provide", .NET Standard doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span> <span data-ttu-id="fff3c-109">Sada Compatibility Pack systému Windows je umístěna na .NET Standard a poskytuje přístup k těmto technologiím, které jsou výhradně pro Windows.</span><span class="sxs-lookup"><span data-stu-id="fff3c-109">The Windows Compatibility Pack sits on top of .NET Standard and provides access to these Windows-only technologies.</span></span> <span data-ttu-id="fff3c-110">To je zvlášť užitečné pro zákazníky, kteří se chtějí přesunout do .NET Core, ale naplánovat, aby se v systému Windows naplánovaly, a to aspoň jako první krok.</span><span class="sxs-lookup"><span data-stu-id="fff3c-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows, at least as a first step.</span></span> <span data-ttu-id="fff3c-111">V takovém případě je možné použít technologie jenom pro Windows k odebrání prahu migrace.</span><span class="sxs-lookup"><span data-stu-id="fff3c-111">In that scenario, being able to use Windows-only technologies removes the migration hurdle.</span></span>

## <a name="package-contents"></a><span data-ttu-id="fff3c-112">Obsah balíčku</span><span class="sxs-lookup"><span data-stu-id="fff3c-112">Package contents</span></span>

<span data-ttu-id="fff3c-113">Sada Windows Compatibility Pack je poskytována prostřednictvím [balíčku NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) a může být odkazována z projektů, které cílí na rozhraní .NET Core nebo .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="fff3c-113">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET Core or .NET Standard.</span></span>

<span data-ttu-id="fff3c-114">Poskytuje informace o rozhraních API 20 000, včetně pouze Windows, stejně jako rozhraní API pro různé platformy z následujících technologických oblastí:</span><span class="sxs-lookup"><span data-stu-id="fff3c-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="fff3c-115">Znakové stránky</span><span class="sxs-lookup"><span data-stu-id="fff3c-115">Code Pages</span></span>
- <span data-ttu-id="fff3c-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="fff3c-116">CodeDom</span></span>
- <span data-ttu-id="fff3c-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="fff3c-117">Configuration</span></span>
- <span data-ttu-id="fff3c-118">Adresářové služby</span><span class="sxs-lookup"><span data-stu-id="fff3c-118">Directory Services</span></span>
- <span data-ttu-id="fff3c-119">Tažné</span><span class="sxs-lookup"><span data-stu-id="fff3c-119">Drawing</span></span>
- <span data-ttu-id="fff3c-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="fff3c-120">ODBC</span></span>
- <span data-ttu-id="fff3c-121">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="fff3c-121">Permissions</span></span>
- <span data-ttu-id="fff3c-122">Porty</span><span class="sxs-lookup"><span data-stu-id="fff3c-122">Ports</span></span>
- <span data-ttu-id="fff3c-123">Seznamy Windows Access Control (ACL)</span><span class="sxs-lookup"><span data-stu-id="fff3c-123">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="fff3c-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="fff3c-124">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="fff3c-125">Kryptografie systému Windows</span><span class="sxs-lookup"><span data-stu-id="fff3c-125">Windows Cryptography</span></span>
- <span data-ttu-id="fff3c-126">Windows EventLog</span><span class="sxs-lookup"><span data-stu-id="fff3c-126">Windows EventLog</span></span>
- <span data-ttu-id="fff3c-127">Služba WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="fff3c-127">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="fff3c-128">Čítače výkonu Windows</span><span class="sxs-lookup"><span data-stu-id="fff3c-128">Windows Performance Counters</span></span>
- <span data-ttu-id="fff3c-129">Registr systému Windows</span><span class="sxs-lookup"><span data-stu-id="fff3c-129">Windows Registry</span></span>
- <span data-ttu-id="fff3c-130">Ukládání prostředí Windows Runtime do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="fff3c-130">Windows Runtime Caching</span></span>
- <span data-ttu-id="fff3c-131">Služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="fff3c-131">Windows Services</span></span>

<span data-ttu-id="fff3c-132">Další informace najdete v tématu [specifikace sady Compatibility Pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="fff3c-132">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="fff3c-133">Začínáme</span><span class="sxs-lookup"><span data-stu-id="fff3c-133">Get started</span></span>

1. <span data-ttu-id="fff3c-134">Před přenosem se ujistěte, že se podíváte na [proces přenosu](index.md).</span><span class="sxs-lookup"><span data-stu-id="fff3c-134">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="fff3c-135">Při přenosu stávajícího kódu do rozhraní .NET Core nebo .NET Standard nainstalujte [balíček NuGet Microsoft. Windows. Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="fff3c-135">When porting existing code to .NET Core or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="fff3c-136">Pokud chcete zůstat v systému Windows, je vše nastavené.</span><span class="sxs-lookup"><span data-stu-id="fff3c-136">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="fff3c-137">Pokud chcete spustit aplikaci .NET Core nebo knihovnu .NET Standard v systému Linux nebo macOS, pomocí [analyzátoru rozhraní API](../../standard/analyzers/api-analyzer.md) vyhledejte využití rozhraní API, které nebude fungovat pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="fff3c-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="fff3c-138">Buď odeberte použití těchto rozhraní API, nahraďte je alternativami pro různé platformy nebo je Zabezpečte pomocí kontroly platformy, například:</span><span class="sxs-lookup"><span data-stu-id="fff3c-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="fff3c-139">Ukázku najdete ve [videu kanálu 9 sady Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="fff3c-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
