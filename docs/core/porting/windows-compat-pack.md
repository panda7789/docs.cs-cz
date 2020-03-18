---
title: Použití sady Windows Compatibility Pack k portu kódu do jádra rozhraní .NET
description: Informace o nástroji Compatibility Pack pro systém Windows a o tom, jak ji můžete použít k portování existujícího kódu rozhraní .NET Framework do jádra .NET Core.
author: terrajobst
ms.date: 12/07/2018
ms.openlocfilehash: 91a653b2345d414c18ebdb6e8b7d6d49bbdbb83e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733608"
---
# <a name="use-the-windows-compatibility-pack-to-port-code-to-net-core"></a><span data-ttu-id="f3f86-103">Použití sady Windows Compatibility Pack k portu kódu do jádra rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="f3f86-103">Use the Windows Compatibility Pack to port code to .NET Core</span></span>

<span data-ttu-id="f3f86-104">Některé z nejběžnějších problémů nalezených při přenosu existujícího kódu do jádra .NET jsou závislosti na rozhraních API a technologiích, které se nacházejí pouze v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f3f86-104">Some of the most common issues found when porting existing code to .NET Core are dependencies on APIs and technologies that are only found in .NET Framework.</span></span> <span data-ttu-id="f3f86-105">*Sada Windows Compatibility Pack* poskytuje mnoho z těchto technologií, takže je mnohem jednodušší vytvářet aplikace .NET Core a knihovny .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f3f86-105">The *Windows Compatibility Pack* provides many of these technologies, so it's much easier to build .NET Core applications and .NET Standard libraries.</span></span>

<span data-ttu-id="f3f86-106">Balíček compatibility pack je logické [rozšíření .NET Standard 2.0,](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) které výrazně zvyšuje sadu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="f3f86-106">The compatibility pack is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases the API set.</span></span> <span data-ttu-id="f3f86-107">Existující kód se zkompiluje téměř bez úprav.</span><span class="sxs-lookup"><span data-stu-id="f3f86-107">Existing code compiles with almost no modifications.</span></span> <span data-ttu-id="f3f86-108">Chcete-li zachovat svůj příslib "sadu rozhraní API, které poskytují všechny implementace rozhraní .NET", .NET Standard nezahrnuje technologie, které nemohou fungovat na všech platformách, jako je například registr, WMI (Windows Management Instrumentation) nebo reflexe vyzařují rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="f3f86-108">To keep its promise of "the set of APIs that all .NET implementations provide", .NET Standard doesn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span> <span data-ttu-id="f3f86-109">Sada Kompatibilita systému Windows je na rozhraní .NET Standard a poskytuje přístup k těmto technologiím pouze pro systém Windows.</span><span class="sxs-lookup"><span data-stu-id="f3f86-109">The Windows Compatibility Pack sits on top of .NET Standard and provides access to these Windows-only technologies.</span></span> <span data-ttu-id="f3f86-110">Je to užitečné zejména pro zákazníky, kteří se chtějí přesunout do .NET Core, ale plánují zůstat v systému Windows, alespoň jako první krok.</span><span class="sxs-lookup"><span data-stu-id="f3f86-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows, at least as a first step.</span></span> <span data-ttu-id="f3f86-111">V tomto scénáři možnost používat technologie pouze systému Windows odstraňuje překážku migrace.</span><span class="sxs-lookup"><span data-stu-id="f3f86-111">In that scenario, being able to use Windows-only technologies removes the migration hurdle.</span></span>

## <a name="package-contents"></a><span data-ttu-id="f3f86-112">Obsah balení</span><span class="sxs-lookup"><span data-stu-id="f3f86-112">Package contents</span></span>

<span data-ttu-id="f3f86-113">Sada Kompatibilita systému Windows je poskytována prostřednictvím [balíčku Microsoft.Windows.Compatibility NuGet](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) a lze na něj odkazovat z projektů, které cílí na .NET Core nebo .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="f3f86-113">The Windows Compatibility Pack is provided via the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects that target .NET Core or .NET Standard.</span></span>

<span data-ttu-id="f3f86-114">Poskytuje přibližně 20 000 oken API, včetně pouze systémových oken a také multiplatformních api z následujících technologických oblastí:</span><span class="sxs-lookup"><span data-stu-id="f3f86-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

- <span data-ttu-id="f3f86-115">Znakové stránky</span><span class="sxs-lookup"><span data-stu-id="f3f86-115">Code Pages</span></span>
- <span data-ttu-id="f3f86-116">Codedom</span><span class="sxs-lookup"><span data-stu-id="f3f86-116">CodeDom</span></span>
- <span data-ttu-id="f3f86-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f3f86-117">Configuration</span></span>
- <span data-ttu-id="f3f86-118">Adresářové služby</span><span class="sxs-lookup"><span data-stu-id="f3f86-118">Directory Services</span></span>
- <span data-ttu-id="f3f86-119">Kresba</span><span class="sxs-lookup"><span data-stu-id="f3f86-119">Drawing</span></span>
- <span data-ttu-id="f3f86-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="f3f86-120">ODBC</span></span>
- <span data-ttu-id="f3f86-121">Oprávnění</span><span class="sxs-lookup"><span data-stu-id="f3f86-121">Permissions</span></span>
- <span data-ttu-id="f3f86-122">Porty</span><span class="sxs-lookup"><span data-stu-id="f3f86-122">Ports</span></span>
- <span data-ttu-id="f3f86-123">Seznamy řízení přístupu systému Windows (ACL)</span><span class="sxs-lookup"><span data-stu-id="f3f86-123">Windows Access Control Lists (ACL)</span></span>
- <span data-ttu-id="f3f86-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="f3f86-124">Windows Communication Foundation (WCF)</span></span>
- <span data-ttu-id="f3f86-125">Kryptografie systému Windows</span><span class="sxs-lookup"><span data-stu-id="f3f86-125">Windows Cryptography</span></span>
- <span data-ttu-id="f3f86-126">Protokol událostí systému Windows</span><span class="sxs-lookup"><span data-stu-id="f3f86-126">Windows EventLog</span></span>
- <span data-ttu-id="f3f86-127">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="f3f86-127">Windows Management Instrumentation (WMI)</span></span>
- <span data-ttu-id="f3f86-128">Čítače výkonu systému Windows</span><span class="sxs-lookup"><span data-stu-id="f3f86-128">Windows Performance Counters</span></span>
- <span data-ttu-id="f3f86-129">Registr Windows</span><span class="sxs-lookup"><span data-stu-id="f3f86-129">Windows Registry</span></span>
- <span data-ttu-id="f3f86-130">Ukládání do mezipaměti prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="f3f86-130">Windows Runtime Caching</span></span>
- <span data-ttu-id="f3f86-131">Služby systému Windows</span><span class="sxs-lookup"><span data-stu-id="f3f86-131">Windows Services</span></span>

<span data-ttu-id="f3f86-132">Další informace naleznete ve [specifikaci sady Compatibility Pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span><span class="sxs-lookup"><span data-stu-id="f3f86-132">For more information, see the [specification of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="f3f86-133">Začínáme</span><span class="sxs-lookup"><span data-stu-id="f3f86-133">Get started</span></span>

1. <span data-ttu-id="f3f86-134">Před přenesením se nezapomeňte podívat na [proces přenosu](index.md).</span><span class="sxs-lookup"><span data-stu-id="f3f86-134">Before porting, make sure to take a look at the [Porting process](index.md).</span></span>

2. <span data-ttu-id="f3f86-135">Při přenosu existujícího kódu do rozhraní .NET Core nebo .NET Standard nainstalujte [balíček NuGet microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="f3f86-135">When porting existing code to .NET Core or .NET Standard, install the [Microsoft.Windows.Compatibility NuGet package](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

   <span data-ttu-id="f3f86-136">Pokud chcete zůstat ve Windows, máte vše nastaveno.</span><span class="sxs-lookup"><span data-stu-id="f3f86-136">If you want to stay on Windows, you're all set.</span></span>

3. <span data-ttu-id="f3f86-137">Pokud chcete spustit aplikaci .NET Core nebo knihovnu .NET Standard v Systému Linux nebo macOS, použijte [analyzátor rozhraní API](../../standard/analyzers/api-analyzer.md) k vyhledání využití rozhraní API, která nebudou fungovat napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="f3f86-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](../../standard/analyzers/api-analyzer.md) to find usage of APIs that won't work cross-platform.</span></span>

4. <span data-ttu-id="f3f86-138">Buď odeberte použití těchto api, nahraďte je alternativami pro různé platformy, nebo je střežte pomocí kontroly platformy, například:</span><span class="sxs-lookup"><span data-stu-id="f3f86-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="f3f86-139">Ukázku najdete ve [videu kanálu 9 v balíčku Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span><span class="sxs-lookup"><span data-stu-id="f3f86-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>
