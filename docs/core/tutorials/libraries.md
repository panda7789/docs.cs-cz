---
title: Vývoj knihovny s křížové nástrojů platformy
description: Naučte se vytvářet knihovny pro .NET pomocí nástrojů příkazového řádku .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 05/01/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 6bdb5b11a54ce23c676d10ef6e440fa46ea12f72
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="developing-libraries-with-cross-platform-tools"></a><span data-ttu-id="057bf-103">Vývoj knihovny s křížové nástrojů platformy</span><span class="sxs-lookup"><span data-stu-id="057bf-103">Developing Libraries with Cross Platform Tools</span></span>

<span data-ttu-id="057bf-104">Tento článek popisuje jak napsat knihovny pro rozhraní .NET pomocí nástrojů příkazového řádku pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="057bf-104">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="057bf-105">Rozhraní příkazového řádku poskytuje efektivní a nízké úrovně prostředí, které funguje napříč libovolný podporovaný operační systém.</span><span class="sxs-lookup"><span data-stu-id="057bf-105">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="057bf-106">Přesto můžete vytvořit knihovny pomocí sady Visual Studio, a pokud je prostředí upřednostňované [v sadě Visual Studio příručce](libraries-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="057bf-106">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](libraries-with-vs.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="057bf-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="057bf-107">Prerequisites</span></span>

<span data-ttu-id="057bf-108">Je třeba [.NET Core SDK a rozhraní příkazového řádku](https://www.microsoft.com/net/core) nainstalovaný na počítači.</span><span class="sxs-lookup"><span data-stu-id="057bf-108">You need [the .NET Core SDK and CLI](https://www.microsoft.com/net/core) installed on your machine.</span></span>

<span data-ttu-id="057bf-109">V částech tohoto dokumentu se zabývá verze rozhraní .NET Framework, musíte [rozhraní .NET Framework](http://getdotnet.azurewebsites.net/) nainstalovaná na počítači s Windows.</span><span class="sxs-lookup"><span data-stu-id="057bf-109">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](http://getdotnet.azurewebsites.net/) installed on a Windows machine.</span></span>

<span data-ttu-id="057bf-110">Kromě toho, pokud chcete pro podporu starší rozhraní .NET Framework cíle, je potřeba nainstalovat cílení/vývojáře sady pro starší verze framework [.NET cílové platformy stránky](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span><span class="sxs-lookup"><span data-stu-id="057bf-110">Additionally, if you wish to support older .NET Framework targets, you need to install targeting/developer packs for older framework versions from the [.NET target platforms page](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span></span> <span data-ttu-id="057bf-111">Najdete v této tabulce:</span><span class="sxs-lookup"><span data-stu-id="057bf-111">Refer to this table:</span></span>

| <span data-ttu-id="057bf-112">Verze rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="057bf-112">.NET Framework Version</span></span> | <span data-ttu-id="057bf-113">Co chcete stáhnout</span><span class="sxs-lookup"><span data-stu-id="057bf-113">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="057bf-114">4.6.1</span><span class="sxs-lookup"><span data-stu-id="057bf-114">4.6.1</span></span>                  | <span data-ttu-id="057bf-115">Pack cílení na rozhraní .NET framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="057bf-115">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="057bf-116">4.6</span><span class="sxs-lookup"><span data-stu-id="057bf-116">4.6</span></span>                    | <span data-ttu-id="057bf-117">Pack cílení na rozhraní .NET framework 4.6</span><span class="sxs-lookup"><span data-stu-id="057bf-117">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="057bf-118">4.5.2</span><span class="sxs-lookup"><span data-stu-id="057bf-118">4.5.2</span></span>                  | <span data-ttu-id="057bf-119">Rozhraní .NET framework 4.5.2 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="057bf-119">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="057bf-120">4.5.1</span><span class="sxs-lookup"><span data-stu-id="057bf-120">4.5.1</span></span>                  | <span data-ttu-id="057bf-121">Rozhraní .NET framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="057bf-121">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="057bf-122">4.5</span><span class="sxs-lookup"><span data-stu-id="057bf-122">4.5</span></span>                    | <span data-ttu-id="057bf-123">Sada Windows SDK pro aplikace pro Windows 8</span><span class="sxs-lookup"><span data-stu-id="057bf-123">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="057bf-124">4.0</span><span class="sxs-lookup"><span data-stu-id="057bf-124">4.0</span></span>                    | <span data-ttu-id="057bf-125">Windows SDK pro systém Windows 7 a rozhraní .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="057bf-125">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="057bf-126">2.0, 3.0 a 3.5</span><span class="sxs-lookup"><span data-stu-id="057bf-126">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="057bf-127">Modul Runtime rozhraní .NET framework 3.5 SP1 (nebo verze systému Windows 8 +)</span><span class="sxs-lookup"><span data-stu-id="057bf-127">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="057bf-128">Postup cílí na Standard .NET</span><span class="sxs-lookup"><span data-stu-id="057bf-128">How to target the .NET Standard</span></span>

<span data-ttu-id="057bf-129">Pokud si nejste poměrně obeznámeni s .NET Standard, podívejte se na [.NET Standard](../../standard/net-standard.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="057bf-129">If you're not quite familiar with the .NET Standard, refer to the [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="057bf-130">V tomto článku je tabulka, která se mapuje na různé implementace .NET Standard verze:</span><span class="sxs-lookup"><span data-stu-id="057bf-130">In that article, there is a table which maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

<span data-ttu-id="057bf-131">Tady je tato tabulka znamená pro účely vytvoření knihovny:</span><span class="sxs-lookup"><span data-stu-id="057bf-131">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="057bf-132">Verze vyberete standardního .NET bude kompromis mezi přístup k nejnovější rozhraní API a schopnost cílové Další implementace rozhraní .NET a .NET Standard verze.</span><span class="sxs-lookup"><span data-stu-id="057bf-132">The version of the .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="057bf-133">Rozsah targetable platformy a verze řídit výběr verzi `netstandardX.X` (kde `X.X` je číslo verze) a její přidání do souboru projektu (`.csproj` nebo `.fsproj`).</span><span class="sxs-lookup"><span data-stu-id="057bf-133">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (Where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="057bf-134">Máte tři možnosti primární, když se cílí na Standard .NET, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="057bf-134">You have three primary options when targeting the .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="057bf-135">Můžete použít výchozí verze poskytl šablony - standardního .NET `netstandard1.4` – které dává vám přístup k většině rozhraní API v rozhraní .NET standardní ale stále mít kompatibilní s UPW, rozhraní .NET Framework 4.6.1 a chystaný standardní rozhraní .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="057bf-135">You can use the default version of the .NET Standard supplied by templates - `netstandard1.4` - which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and the forthcoming .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="057bf-136">Můžete použít nižší nebo vyšší verze rozhraní .NET standardního změnou hodnoty v `TargetFramework` uzlu souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="057bf-136">You can use a lower or higher version of the .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>
    
    <span data-ttu-id="057bf-137">.NET standard verze jsou zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="057bf-137">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="057bf-138">To znamená, že `netstandard1.0` knihovny spusťte na `netstandard1.1` platformy a vyšší.</span><span class="sxs-lookup"><span data-stu-id="057bf-138">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="057bf-139">Však neexistuje žádná dopřednou kompatibilitu – nižší platformy .NET standardní nemůže odkazovat na ty, které jsou vyšší.</span><span class="sxs-lookup"><span data-stu-id="057bf-139">However, there is no forward compatibility - lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="057bf-140">To znamená, že `netstandard1.0` knihovny nelze reference knihovny, které cílí `netstandard1.1` nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="057bf-140">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="057bf-141">Vyberte standardní verzi, která má správné směs podpora rozhraní API a platformy pro vaše potřeby.</span><span class="sxs-lookup"><span data-stu-id="057bf-141">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="057bf-142">Doporučujeme, abyste `netstandard1.4` teď.</span><span class="sxs-lookup"><span data-stu-id="057bf-142">We recommend `netstandard1.4` for now.</span></span>
    
3. <span data-ttu-id="057bf-143">Pokud budete chtít cílové verze rozhraní .NET Framework 4.0 nebo níže, nebo chcete použít rozhraní API, které jsou k dispozici v rozhraní .NET Framework, ale není v .NET Standard (například `System.Drawing`), přečtěte si následující části a zjistěte, jak multitarget.</span><span class="sxs-lookup"><span data-stu-id="057bf-143">If you want to target the .NET Framework versions 4.0 or below, or you wish to use an API available in the .NET Framework but not in the .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-the-net-framework"></a><span data-ttu-id="057bf-144">Postup cílové rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="057bf-144">How to target the .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="057bf-145">Tyto pokyny předpokládají, že máte rozhraní .NET Framework, který je nainstalovaný na počítači.</span><span class="sxs-lookup"><span data-stu-id="057bf-145">These instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="057bf-146">Odkazovat [požadavky](#prerequisites) získat závislosti nainstalována.</span><span class="sxs-lookup"><span data-stu-id="057bf-146">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="057bf-147">Mějte na paměti, že některá z verzí rozhraní .NET Framework použít se zde jsou již v technické podpory.</span><span class="sxs-lookup"><span data-stu-id="057bf-147">Keep in mind that some of the .NET Framework versions used here are no longer in support.</span></span> <span data-ttu-id="057bf-148">Odkazovat [rozhraní .NET Framework podporu životního cyklu nejčastější dotazy k zásadám](https://support.microsoft.com/gp/framework_faq/en-us) o Nepodporovaná verze.</span><span class="sxs-lookup"><span data-stu-id="057bf-148">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="057bf-149">Pokud chcete k dosažení maximální počet vývojáři a projekty, použijte jako cíl vaše základní rozhraní .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="057bf-149">If you want to reach the maximum number of developers and projects, use the .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="057bf-150">Pokud chcete zacílit rozhraní .NET Framework, musíte začít s využitím správný cílový Framework Přezdívka (TFM) odpovídající verzi rozhraní .NET Framework, které chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="057bf-150">To target the .NET Framework, you will need to begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

```
.NET Framework 2.0   --> net20
.NET Framework 3.0   --> net30
.NET Framework 3.5   --> net35
.NET Framework 4.0   --> net40
.NET Framework 4.5   --> net45
.NET Framework 4.5.1 --> net451
.NET Framework 4.5.2 --> net452
.NET Framework 4.6   --> net46
.NET Framework 4.6.1 --> net461
.NET Framework 4.6.2 --> net462
.NET Framework 4.7   --> net47
```

<span data-ttu-id="057bf-151">Potom vložte tento TFM do `TargetFramework` části souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="057bf-151">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="057bf-152">Můžete zde je ukázka, jak by zápisu knihovnu, která cílí rozhraní .NET Framework 4.0:</span><span class="sxs-lookup"><span data-stu-id="057bf-152">For example, here's how you would write a library which targets the .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="057bf-153">A je to!</span><span class="sxs-lookup"><span data-stu-id="057bf-153">And that's it!</span></span> <span data-ttu-id="057bf-154">I když to zkompilovat pouze pro rozhraní .NET Framework 4, můžete v knihovně na novější verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="057bf-154">Although this compiled only for the .NET Framework 4, you can use the library on newer versions of the .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="057bf-155">Postup Multitarget</span><span class="sxs-lookup"><span data-stu-id="057bf-155">How to Multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="057bf-156">Následující pokyny předpokládají, že máte rozhraní .NET Framework, který je nainstalovaný na počítači.</span><span class="sxs-lookup"><span data-stu-id="057bf-156">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="057bf-157">Odkazovat [požadavky](#prerequisites) části Další závislosti, které je třeba nainstalovat a kam je z chcete stáhnout.</span><span class="sxs-lookup"><span data-stu-id="057bf-157">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="057bf-158">Musíte mít starší verze rozhraní .NET Framework Pokud projekt podporuje rozhraní .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="057bf-158">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="057bf-159">V tomto scénáři, pokud chcete použít novější rozhraní API a jazykové konstrukty pro novější cíle, použijte `#if` direktivy v kódu.</span><span class="sxs-lookup"><span data-stu-id="057bf-159">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="057bf-160">Můžete také může být nutné přidat jiné balíčky a závislosti pro každou platformu, kterou jste cílení zahrnout různých rozhraní API pro každý případ potřeby.</span><span class="sxs-lookup"><span data-stu-id="057bf-160">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="057bf-161">Řekněme například, že je vaše knihovna, která provádí síťových operací přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="057bf-161">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="057bf-162">Pro .NET Standard a rozhraní .NET Framework verze 4.5 nebo vyšší, můžete použít `HttpClient` třídy z `System.Net.Http` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="057bf-162">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="057bf-163">Však nemají starší verze rozhraní .NET Framework `HttpClient` třídy, takže můžete použít `WebClient` třídy z `System.Net` obor názvů pro ty, místo toho.</span><span class="sxs-lookup"><span data-stu-id="057bf-163">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="057bf-164">Soubor projektu může vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="057bf-164">Your project file could look like this:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.0 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net40'">
    <Reference Include="System.Net" />
  </ItemGroup>

  <!-- Need to conditionally bring in references for the .NET Framework 4.5 target -->
  <ItemGroup Condition="'$(TargetFramework)' == 'net45'">
    <Reference Include="System.Net.Http" />
    <Reference Include="System.Threading.Tasks" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="057bf-165">Můžete si všimnout tři hlavní změny tady:</span><span class="sxs-lookup"><span data-stu-id="057bf-165">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="057bf-166">`TargetFramework` Uzlu nahradila `TargetFrameworks`, a tři TFMs jsou vyjádřeny v.</span><span class="sxs-lookup"><span data-stu-id="057bf-166">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="057bf-167">Je `<ItemGroup>` uzel `net40 ` cíl stahování v jeden odkaz na rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="057bf-167">There is an `<ItemGroup>` node for the `net40 ` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="057bf-168">Je `<ItemGroup>` uzel `net45` cíl stahování v odkazech na dvě rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="057bf-168">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="057bf-169">Systém sestavení si je vědoma následující preprocesoru symboly použité v `#if` direktivy:</span><span class="sxs-lookup"><span data-stu-id="057bf-169">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="057bf-170">Tady je příklad které využijí Podmíněná kompilace za cíl:</span><span class="sxs-lookup"><span data-stu-id="057bf-170">Here is an example making use of conditional compilation per-target:</span></span>

```csharp
using System;
using System.Text.RegularExpressions;
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
 // This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif

namespace MultitargetLib
{
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "http://www.dotnetfoundation.org/";

            var uri = new Uri(url);

            string result = "";

            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "http://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="057bf-171">Pokud vytvoříte tento projekt s `dotnet build`, můžete si všimnout tři adresáře `bin/` složky:</span><span class="sxs-lookup"><span data-stu-id="057bf-171">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="057bf-172">Každá z těchto obsahovat `.dll` soubory pro každý cíl.</span><span class="sxs-lookup"><span data-stu-id="057bf-172">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="057bf-173">Postup testování knihovny na .NET Core</span><span class="sxs-lookup"><span data-stu-id="057bf-173">How to test libraries on .NET Core</span></span>

<span data-ttu-id="057bf-174">Je důležité, abyste mohli otestovat napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="057bf-174">It's important to be able to test across platforms.</span></span> <span data-ttu-id="057bf-175">Můžete použít buď [xUnit](http://xunit.github.io/) nebo Mstestu z pole.</span><span class="sxs-lookup"><span data-stu-id="057bf-175">You can use either [xUnit](http://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="057bf-176">Jsou obě perfektně vhodný pro testování vaší knihovny na .NET Core jednotky.</span><span class="sxs-lookup"><span data-stu-id="057bf-176">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="057bf-177">Jak nastavit řešení pomocí projektů testování, bude záviset na [struktura řešení](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="057bf-177">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="057bf-178">V následujícím příkladu se předpokládá, že test a zdrojového adresáře za provozu ve stejném adresáři nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="057bf-178">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="057bf-179">To se využívá část [.NET Core rozhraní příkazového řádku](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="057bf-179">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="057bf-180">V tématu [dotnet nové](../tools/dotnet-new.md) a [SLN – dotnet](../tools/dotnet-sln.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="057bf-180">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="057bf-181">Nastavte řešení.</span><span class="sxs-lookup"><span data-stu-id="057bf-181">Set up your solution.</span></span> <span data-ttu-id="057bf-182">Můžete tak učinit pomocí následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="057bf-182">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="057bf-183">Tato akce vytvoří projekty a propojit je společně v řešení.</span><span class="sxs-lookup"><span data-stu-id="057bf-183">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="057bf-184">V adresáři `SolutionWithSrcAndTest` by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="057bf-184">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="057bf-185">Přejděte do adresáře k testovacímu projektu a přidejte odkaz na `MyProject.Test` z `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="057bf-185">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="057bf-186">Obnovení balíčků a sestavení projektů:</span><span class="sxs-lookup"><span data-stu-id="057bf-186">Restore packages and build projects:</span></span>

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. <span data-ttu-id="057bf-187">Ověřte, že xUnit běží spuštěním `dotnet test` příkaz.</span><span class="sxs-lookup"><span data-stu-id="057bf-187">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="057bf-188">Pokud zvolíte použití Mstestu, měli místo toho spustit nástroj runner Mstestu konzoly.</span><span class="sxs-lookup"><span data-stu-id="057bf-188">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>
    
<span data-ttu-id="057bf-189">A je to!</span><span class="sxs-lookup"><span data-stu-id="057bf-189">And that's it!</span></span> <span data-ttu-id="057bf-190">Nyní můžete otestovat knihovnu pro všechny platformy, pomocí nástrojů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="057bf-190">You can now test your library across all platforms using command line tools.</span></span> <span data-ttu-id="057bf-191">Chcete-li pokračovat, testování nyní, když máte všechno nastavit, aby testování vaše knihovna je velmi jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="057bf-191">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="057bf-192">Proveďte změny své knihovny.</span><span class="sxs-lookup"><span data-stu-id="057bf-192">Make changes to your library.</span></span>
1. <span data-ttu-id="057bf-193">Spouštění testů z příkazového řádku v adresáři test pomocí `dotnet test` příkaz.</span><span class="sxs-lookup"><span data-stu-id="057bf-193">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="057bf-194">Váš kód bude automaticky znovu vytvořen při vyvolání `dotnet test` příkaz.</span><span class="sxs-lookup"><span data-stu-id="057bf-194">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="057bf-195">Použití více projektů</span><span class="sxs-lookup"><span data-stu-id="057bf-195">How to use multiple projects</span></span>

<span data-ttu-id="057bf-196">Běžné potřebu větší knihovny je funkce umístit do různých projektů.</span><span class="sxs-lookup"><span data-stu-id="057bf-196">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="057bf-197">Představte si, že jste si přáli pro sestavení knihovny, které by mohly spotřebovat v idiomatickou C# a F #.</span><span class="sxs-lookup"><span data-stu-id="057bf-197">Imagine you wished to build a library which could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="057bf-198">To znamená, že příjemci ve své knihovny je můžou využívat způsoby, které jsou přirozené C# nebo F #.</span><span class="sxs-lookup"><span data-stu-id="057bf-198">That would mean that consumers of your library consume them in ways which are natural to C# or F#.</span></span> <span data-ttu-id="057bf-199">Například v jazyce C# může využívat knihovně takto:</span><span class="sxs-lookup"><span data-stu-id="057bf-199">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="057bf-200">V jazyce F # může vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="057bf-200">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="057bf-201">Spotřeba scénáře, jako to znamená, že rozhraní API přistupuje musejí mít jinou strukturu pro C# a F #.</span><span class="sxs-lookup"><span data-stu-id="057bf-201">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="057bf-202">Společný přístup k provedení to je zohlednit veškerou logiku knihovny do projektu jádra, s projekty C# a F # definice rozhraní API vrstvy, které volání do tohoto projektu jádra.</span><span class="sxs-lookup"><span data-stu-id="057bf-202">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="057bf-203">Zbývající části použije tyto názvy:</span><span class="sxs-lookup"><span data-stu-id="057bf-203">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="057bf-204">**AwesomeLibrary.Core** – základní projektu, který obsahuje veškerou logiku pro knihovnu</span><span class="sxs-lookup"><span data-stu-id="057bf-204">**AwesomeLibrary.Core** - A core project which contains all logic for the library</span></span>
* <span data-ttu-id="057bf-205">**AwesomeLibrary.CSharp** -projekt se veřejná rozhraní API určená pro používání v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="057bf-205">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="057bf-206">**AwesomeLibrary.FSharp** -projekt se veřejná rozhraní API určená pro používání v jazyce F #</span><span class="sxs-lookup"><span data-stu-id="057bf-206">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="057bf-207">V terminálu k vytvoření stejná struktura jako tento průvodce můžete spustit následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="057bf-207">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```console
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang F#
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="057bf-208">Tím se přidá výše tři projekty a řešení soubor, který je společně odkazů.</span><span class="sxs-lookup"><span data-stu-id="057bf-208">This will add the three projects above and a solution file which links them together.</span></span> <span data-ttu-id="057bf-209">Soubor řešení vytváření a propojování projekty vám umožní obnovit a sestavení projektů z nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="057bf-209">Creating the solution file and linking projects will allow you to restore and build projects from a top-level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="057bf-210">Odkazování na projekt na projekt</span><span class="sxs-lookup"><span data-stu-id="057bf-210">Project-to-project referencing</span></span>

<span data-ttu-id="057bf-211">Nejlepší způsob, jak odkazovat na projekt je použití rozhraní příkazového řádku .NET Core přidat odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="057bf-211">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="057bf-212">Z **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** adresáře projektu, můžete spustit následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="057bf-212">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="057bf-213">Soubory projektu pro obě **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** bude nyní odkaz **AwesomeLibrary.Core** jako `ProjectReference` cíl.</span><span class="sxs-lookup"><span data-stu-id="057bf-213">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="057bf-214">Můžete to ověřit tak, že zkontrolujete soubory projektu a zobrazuje následující v nich:</span><span class="sxs-lookup"><span data-stu-id="057bf-214">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="057bf-215">V této části můžete ručně přidat ke každému souboru projektu, pokud nechcete používat rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="057bf-215">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="057bf-216">Strukturování řešení</span><span class="sxs-lookup"><span data-stu-id="057bf-216">Structuring a solution</span></span>

<span data-ttu-id="057bf-217">Dalším důležitým aspektem řešení vícenásobného projektu navazuje dobrý celková struktura projektu.</span><span class="sxs-lookup"><span data-stu-id="057bf-217">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="057bf-218">Kód můžete uspořádat, ale chcete, a také propojit každý projekt, ze souboru řešení s `dotnet sln add`, nebudete moci spustit `dotnet restore` a `dotnet build` na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="057bf-218">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
