---
title: "Vývoj knihovny s křížové nástrojů platformy"
description: "Naučte se vytvářet knihovny pro .NET pomocí nástrojů příkazového řádku .NET Core."
keywords: "Rozhraní .NET, .NET core"
author: cartermp
ms.author: mairaw
ms.date: 05/01/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 9f6e8679-bd7e-4317-b3f9-7255a260d9cf
ms.workload: dotnetcore
ms.openlocfilehash: 8b809fbe73dfd382d568aba5d0f074915d727546
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="developing-libraries-with-cross-platform-tools"></a><span data-ttu-id="49541-104">Vývoj knihovny s křížové nástrojů platformy</span><span class="sxs-lookup"><span data-stu-id="49541-104">Developing Libraries with Cross Platform Tools</span></span>

<span data-ttu-id="49541-105">Tento článek popisuje jak napsat knihovny pro rozhraní .NET pomocí nástrojů příkazového řádku pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="49541-105">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="49541-106">Rozhraní příkazového řádku poskytuje efektivní a nízké úrovně prostředí, které funguje napříč libovolný podporovaný operační systém.</span><span class="sxs-lookup"><span data-stu-id="49541-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="49541-107">Přesto můžete vytvořit knihovny pomocí sady Visual Studio, a pokud je prostředí upřednostňované [v sadě Visual Studio příručce](libraries-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="49541-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](libraries-with-vs.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49541-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49541-108">Prerequisites</span></span>

<span data-ttu-id="49541-109">Je třeba [.NET Core SDK a rozhraní příkazového řádku](https://www.microsoft.com/net/core) nainstalovaný na počítači.</span><span class="sxs-lookup"><span data-stu-id="49541-109">You need [the .NET Core SDK and CLI](https://www.microsoft.com/net/core) installed on your machine.</span></span>

<span data-ttu-id="49541-110">V částech tohoto dokumentu se zabývá verze rozhraní .NET Framework, musíte [rozhraní .NET Framework](http://getdotnet.azurewebsites.net/) nainstalovaná na počítači s Windows.</span><span class="sxs-lookup"><span data-stu-id="49541-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](http://getdotnet.azurewebsites.net/) installed on a Windows machine.</span></span>

<span data-ttu-id="49541-111">Kromě toho, pokud chcete pro podporu starší rozhraní .NET Framework cíle, je potřeba nainstalovat cílení/vývojáře sady pro starší verze framework [.NET cílové platformy stránky](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span><span class="sxs-lookup"><span data-stu-id="49541-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting/developer packs for older framework versions from the [.NET target platforms page](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span></span> <span data-ttu-id="49541-112">Najdete v této tabulce:</span><span class="sxs-lookup"><span data-stu-id="49541-112">Refer to this table:</span></span>

| <span data-ttu-id="49541-113">Verze rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="49541-113">.NET Framework Version</span></span> | <span data-ttu-id="49541-114">Co chcete stáhnout</span><span class="sxs-lookup"><span data-stu-id="49541-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="49541-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="49541-115">4.6.1</span></span>                  | <span data-ttu-id="49541-116">Pack cílení na rozhraní .NET framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="49541-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="49541-117">4.6</span><span class="sxs-lookup"><span data-stu-id="49541-117">4.6</span></span>                    | <span data-ttu-id="49541-118">Pack cílení na rozhraní .NET framework 4.6</span><span class="sxs-lookup"><span data-stu-id="49541-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="49541-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="49541-119">4.5.2</span></span>                  | <span data-ttu-id="49541-120">Rozhraní .NET framework 4.5.2 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="49541-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="49541-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="49541-121">4.5.1</span></span>                  | <span data-ttu-id="49541-122">Rozhraní .NET framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="49541-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="49541-123">4.5</span><span class="sxs-lookup"><span data-stu-id="49541-123">4.5</span></span>                    | <span data-ttu-id="49541-124">Sada Windows SDK pro aplikace pro Windows 8</span><span class="sxs-lookup"><span data-stu-id="49541-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="49541-125">4.0</span><span class="sxs-lookup"><span data-stu-id="49541-125">4.0</span></span>                    | <span data-ttu-id="49541-126">Windows SDK pro systém Windows 7 a rozhraní .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="49541-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="49541-127">2.0, 3.0 a 3.5</span><span class="sxs-lookup"><span data-stu-id="49541-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="49541-128">Modul Runtime rozhraní .NET framework 3.5 SP1 (nebo verze systému Windows 8 +)</span><span class="sxs-lookup"><span data-stu-id="49541-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="49541-129">Postup cílí na Standard .NET</span><span class="sxs-lookup"><span data-stu-id="49541-129">How to target the .NET Standard</span></span>

<span data-ttu-id="49541-130">Pokud si nejste poměrně obeznámeni s .NET Standard, podívejte se na [.NET Standard](../../standard/net-standard.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="49541-130">If you're not quite familiar with the .NET Standard, refer to the [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="49541-131">V tomto článku je tabulka, která se mapuje na různé implementace .NET Standard verze:</span><span class="sxs-lookup"><span data-stu-id="49541-131">In that article, there is a table which maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

<span data-ttu-id="49541-132">Tady je tato tabulka znamená pro účely vytvoření knihovny:</span><span class="sxs-lookup"><span data-stu-id="49541-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="49541-133">Verze vyberete standardního .NET bude kompromis mezi přístup k nejnovější rozhraní API a schopnost cílové Další implementace rozhraní .NET a .NET Standard verze.</span><span class="sxs-lookup"><span data-stu-id="49541-133">The version of the .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="49541-134">Rozsah targetable platformy a verze řídit výběr verzi `netstandardX.X` (kde `X.X` je číslo verze) a její přidání do souboru projektu (`.csproj` nebo `.fsproj`).</span><span class="sxs-lookup"><span data-stu-id="49541-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (Where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="49541-135">Máte tři možnosti primární, když se cílí na Standard .NET, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="49541-135">You have three primary options when targeting the .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="49541-136">Můžete použít výchozí verze poskytl šablony - standardního .NET `netstandard1.4` – které dává vám přístup k většině rozhraní API v rozhraní .NET standardní ale stále mít kompatibilní s UPW, rozhraní .NET Framework 4.6.1 a chystaný standardní rozhraní .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="49541-136">You can use the default version of the .NET Standard supplied by templates - `netstandard1.4` - which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and the forthcoming .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="49541-137">Můžete použít nižší nebo vyšší verze rozhraní .NET standardního změnou hodnoty v `TargetFramework` uzlu souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="49541-137">You can use a lower or higher version of the .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>
    
    <span data-ttu-id="49541-138">.NET standard verze jsou zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="49541-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="49541-139">To znamená, že `netstandard1.0` knihovny spusťte na `netstandard1.1` platformy a vyšší.</span><span class="sxs-lookup"><span data-stu-id="49541-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="49541-140">Však neexistuje žádná dopřednou kompatibilitu – nižší platformy .NET standardní nemůže odkazovat na ty, které jsou vyšší.</span><span class="sxs-lookup"><span data-stu-id="49541-140">However, there is no forward compatibility - lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="49541-141">To znamená, že `netstandard1.0` knihovny nelze reference knihovny, které cílí `netstandard1.1` nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="49541-141">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="49541-142">Vyberte standardní verzi, která má správné směs podpora rozhraní API a platformy pro vaše potřeby.</span><span class="sxs-lookup"><span data-stu-id="49541-142">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="49541-143">Doporučujeme, abyste `netstandard1.4` teď.</span><span class="sxs-lookup"><span data-stu-id="49541-143">We recommend `netstandard1.4` for now.</span></span>
    
3. <span data-ttu-id="49541-144">Pokud budete chtít cílové verze rozhraní .NET Framework 4.0 nebo níže, nebo chcete použít rozhraní API, které jsou k dispozici v rozhraní .NET Framework, ale není v .NET Standard (například `System.Drawing`), přečtěte si následující části a zjistěte, jak multitarget.</span><span class="sxs-lookup"><span data-stu-id="49541-144">If you want to target the .NET Framework versions 4.0 or below, or you wish to use an API available in the .NET Framework but not in the .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-the-net-framework"></a><span data-ttu-id="49541-145">Postup cílové rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="49541-145">How to target the .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="49541-146">Tyto pokyny předpokládají, že máte rozhraní .NET Framework, který je nainstalovaný na počítači.</span><span class="sxs-lookup"><span data-stu-id="49541-146">These instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="49541-147">Odkazovat [požadavky](#prerequisites) získat závislosti nainstalována.</span><span class="sxs-lookup"><span data-stu-id="49541-147">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="49541-148">Mějte na paměti, že některá z verzí rozhraní .NET Framework použít se zde jsou již v technické podpory.</span><span class="sxs-lookup"><span data-stu-id="49541-148">Keep in mind that some of the .NET Framework versions used here are no longer in support.</span></span> <span data-ttu-id="49541-149">Odkazovat [rozhraní .NET Framework podporu životního cyklu nejčastější dotazy k zásadám](https://support.microsoft.com/gp/framework_faq/en-us) o Nepodporovaná verze.</span><span class="sxs-lookup"><span data-stu-id="49541-149">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="49541-150">Pokud chcete k dosažení maximální počet vývojáři a projekty, použijte jako cíl vaše základní rozhraní .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="49541-150">If you want to reach the maximum number of developers and projects, use the .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="49541-151">Pokud chcete zacílit rozhraní .NET Framework, musíte začít s využitím správný cílový Framework Přezdívka (TFM) odpovídající verzi rozhraní .NET Framework, které chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="49541-151">To target the .NET Framework, you will need to begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

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

<span data-ttu-id="49541-152">Potom vložte tento TFM do `TargetFramework` části souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="49541-152">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="49541-153">Můžete zde je ukázka, jak by zápisu knihovnu, která cílí rozhraní .NET Framework 4.0:</span><span class="sxs-lookup"><span data-stu-id="49541-153">For example, here's how you would write a library which targets the .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="49541-154">A je to!</span><span class="sxs-lookup"><span data-stu-id="49541-154">And that's it!</span></span> <span data-ttu-id="49541-155">I když to zkompilovat pouze pro rozhraní .NET Framework 4, můžete v knihovně na novější verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49541-155">Although this compiled only for the .NET Framework 4, you can use the library on newer versions of the .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="49541-156">Postup Multitarget</span><span class="sxs-lookup"><span data-stu-id="49541-156">How to Multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="49541-157">Následující pokyny předpokládají, že máte rozhraní .NET Framework, který je nainstalovaný na počítači.</span><span class="sxs-lookup"><span data-stu-id="49541-157">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="49541-158">Odkazovat [požadavky](#prerequisites) části Další závislosti, které je třeba nainstalovat a kam je z chcete stáhnout.</span><span class="sxs-lookup"><span data-stu-id="49541-158">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="49541-159">Musíte mít starší verze rozhraní .NET Framework Pokud projekt podporuje rozhraní .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49541-159">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="49541-160">V tomto scénáři, pokud chcete použít novější rozhraní API a jazykové konstrukty pro novější cíle, použijte `#if` direktivy v kódu.</span><span class="sxs-lookup"><span data-stu-id="49541-160">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="49541-161">Můžete také může být nutné přidat jiné balíčky a závislosti pro každou platformu, kterou jste cílení zahrnout různých rozhraní API pro každý případ potřeby.</span><span class="sxs-lookup"><span data-stu-id="49541-161">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="49541-162">Řekněme například, že je vaše knihovna, která provádí síťových operací přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="49541-162">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="49541-163">Pro .NET Standard a rozhraní .NET Framework verze 4.5 nebo vyšší, můžete použít `HttpClient` třídy z `System.Net.Http` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="49541-163">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="49541-164">Však nemají starší verze rozhraní .NET Framework `HttpClient` třídy, takže můžete použít `WebClient` třídy z `System.Net` obor názvů pro ty, místo toho.</span><span class="sxs-lookup"><span data-stu-id="49541-164">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="49541-165">Soubor projektu může vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="49541-165">Your project file could look like this:</span></span>

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

<span data-ttu-id="49541-166">Můžete si všimnout tři hlavní změny tady:</span><span class="sxs-lookup"><span data-stu-id="49541-166">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="49541-167">`TargetFramework` Uzlu nahradila `TargetFrameworks`, a tři TFMs jsou vyjádřeny v.</span><span class="sxs-lookup"><span data-stu-id="49541-167">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="49541-168">Je `<ItemGroup>` uzel `net40 ` cíl stahování v jeden odkaz na rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49541-168">There is an `<ItemGroup>` node for the `net40 ` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="49541-169">Je `<ItemGroup>` uzel `net45` cíl stahování v odkazech na dvě rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49541-169">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="49541-170">Systém sestavení si je vědoma následující preprocesoru symboly použité v `#if` direktivy:</span><span class="sxs-lookup"><span data-stu-id="49541-170">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="49541-171">Tady je příklad které využijí Podmíněná kompilace za cíl:</span><span class="sxs-lookup"><span data-stu-id="49541-171">Here is an example making use of conditional compilation per-target:</span></span>

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

<span data-ttu-id="49541-172">Pokud vytvoříte tento projekt s `dotnet build`, můžete si všimnout tři adresáře `bin/` složky:</span><span class="sxs-lookup"><span data-stu-id="49541-172">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="49541-173">Každá z těchto obsahovat `.dll` soubory pro každý cíl.</span><span class="sxs-lookup"><span data-stu-id="49541-173">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="49541-174">Postup testování knihovny na .NET Core</span><span class="sxs-lookup"><span data-stu-id="49541-174">How to test libraries on .NET Core</span></span>

<span data-ttu-id="49541-175">Je důležité, abyste mohli otestovat napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="49541-175">It's important to be able to test across platforms.</span></span> <span data-ttu-id="49541-176">Můžete použít buď [xUnit](http://xunit.github.io/) nebo Mstestu z pole.</span><span class="sxs-lookup"><span data-stu-id="49541-176">You can use either [xUnit](http://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="49541-177">Jsou obě perfektně vhodný pro testování vaší knihovny na .NET Core jednotky.</span><span class="sxs-lookup"><span data-stu-id="49541-177">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="49541-178">Jak nastavit řešení pomocí projektů testování, bude záviset na [struktura řešení](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="49541-178">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="49541-179">V následujícím příkladu se předpokládá, že test a zdrojového adresáře za provozu ve stejném adresáři nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="49541-179">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="49541-180">To se využívá část [.NET Core rozhraní příkazového řádku](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="49541-180">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="49541-181">V tématu [dotnet nové](../tools/dotnet-new.md) a [SLN – dotnet](../tools/dotnet-sln.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="49541-181">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="49541-182">Nastavte řešení.</span><span class="sxs-lookup"><span data-stu-id="49541-182">Set up your solution.</span></span> <span data-ttu-id="49541-183">Můžete tak učinit pomocí následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="49541-183">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="49541-184">Tato akce vytvoří projekty a propojit je společně v řešení.</span><span class="sxs-lookup"><span data-stu-id="49541-184">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="49541-185">V adresáři `SolutionWithSrcAndTest` by měla vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="49541-185">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="49541-186">Přejděte do adresáře k testovacímu projektu a přidejte odkaz na `MyProject.Test` z `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="49541-186">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="49541-187">Obnovení balíčků a sestavení projektů:</span><span class="sxs-lookup"><span data-stu-id="49541-187">Restore packages and build projects:</span></span>

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. <span data-ttu-id="49541-188">Ověřte, že xUnit běží spuštěním `dotnet test` příkaz.</span><span class="sxs-lookup"><span data-stu-id="49541-188">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="49541-189">Pokud zvolíte použití Mstestu, měli místo toho spustit nástroj runner Mstestu konzoly.</span><span class="sxs-lookup"><span data-stu-id="49541-189">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>
    
<span data-ttu-id="49541-190">A je to!</span><span class="sxs-lookup"><span data-stu-id="49541-190">And that's it!</span></span> <span data-ttu-id="49541-191">Nyní můžete otestovat knihovnu pro všechny platformy, pomocí nástrojů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="49541-191">You can now test your library across all platforms using command line tools.</span></span> <span data-ttu-id="49541-192">Chcete-li pokračovat, testování nyní, když máte všechno nastavit, aby testování vaše knihovna je velmi jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="49541-192">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="49541-193">Proveďte změny své knihovny.</span><span class="sxs-lookup"><span data-stu-id="49541-193">Make changes to your library.</span></span>
1. <span data-ttu-id="49541-194">Spouštění testů z příkazového řádku v adresáři test pomocí `dotnet test` příkaz.</span><span class="sxs-lookup"><span data-stu-id="49541-194">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="49541-195">Váš kód bude automaticky znovu vytvořen při vyvolání `dotnet test` příkaz.</span><span class="sxs-lookup"><span data-stu-id="49541-195">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="49541-196">Použití více projektů</span><span class="sxs-lookup"><span data-stu-id="49541-196">How to use multiple projects</span></span>

<span data-ttu-id="49541-197">Běžné potřebu větší knihovny je funkce umístit do různých projektů.</span><span class="sxs-lookup"><span data-stu-id="49541-197">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="49541-198">Představte si, že jste si přáli pro sestavení knihovny, které by mohly spotřebovat v idiomatickou C# a F #.</span><span class="sxs-lookup"><span data-stu-id="49541-198">Imagine you wished to build a library which could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="49541-199">To znamená, že příjemci ve své knihovny je můžou využívat způsoby, které jsou přirozené C# nebo F #.</span><span class="sxs-lookup"><span data-stu-id="49541-199">That would mean that consumers of your library consume them in ways which are natural to C# or F#.</span></span> <span data-ttu-id="49541-200">Například v jazyce C# může využívat knihovně takto:</span><span class="sxs-lookup"><span data-stu-id="49541-200">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="49541-201">V jazyce F # může vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="49541-201">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="49541-202">Spotřeba scénáře, jako to znamená, že rozhraní API přistupuje musejí mít jinou strukturu pro C# a F #.</span><span class="sxs-lookup"><span data-stu-id="49541-202">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="49541-203">Společný přístup k provedení to je zohlednit veškerou logiku knihovny do projektu jádra, s projekty C# a F # definice rozhraní API vrstvy, které volání do tohoto projektu jádra.</span><span class="sxs-lookup"><span data-stu-id="49541-203">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="49541-204">Zbývající části použije tyto názvy:</span><span class="sxs-lookup"><span data-stu-id="49541-204">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="49541-205">**AwesomeLibrary.Core** – základní projektu, který obsahuje veškerou logiku pro knihovnu</span><span class="sxs-lookup"><span data-stu-id="49541-205">**AwesomeLibrary.Core** - A core project which contains all logic for the library</span></span>
* <span data-ttu-id="49541-206">**AwesomeLibrary.CSharp** -projekt se veřejná rozhraní API určená pro používání v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="49541-206">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="49541-207">**AwesomeLibrary.FSharp** -projekt se veřejná rozhraní API určená pro používání v jazyce F #</span><span class="sxs-lookup"><span data-stu-id="49541-207">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="49541-208">V terminálu k vytvoření stejná struktura jako tento průvodce můžete spustit následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="49541-208">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

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

<span data-ttu-id="49541-209">Tím se přidá výše tři projekty a řešení soubor, který je společně odkazů.</span><span class="sxs-lookup"><span data-stu-id="49541-209">This will add the three projects above and a solution file which links them together.</span></span> <span data-ttu-id="49541-210">Soubor řešení vytváření a propojování projekty vám umožní obnovit a sestavení projektů z nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="49541-210">Creating the solution file and linking projects will allow you to restore and build projects from a top-level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="49541-211">Odkazování na projekt na projekt</span><span class="sxs-lookup"><span data-stu-id="49541-211">Project-to-project referencing</span></span>

<span data-ttu-id="49541-212">Nejlepší způsob, jak odkazovat na projekt je použití rozhraní příkazového řádku .NET Core přidat odkaz na projekt.</span><span class="sxs-lookup"><span data-stu-id="49541-212">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="49541-213">Z **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** adresáře projektu, můžete spustit následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="49541-213">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="49541-214">Soubory projektu pro obě **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** bude nyní odkaz **AwesomeLibrary.Core** jako `ProjectReference` cíl.</span><span class="sxs-lookup"><span data-stu-id="49541-214">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="49541-215">Můžete to ověřit tak, že zkontrolujete soubory projektu a zobrazuje následující v nich:</span><span class="sxs-lookup"><span data-stu-id="49541-215">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="49541-216">V této části můžete ručně přidat ke každému souboru projektu, pokud nechcete používat rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="49541-216">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="49541-217">Strukturování řešení</span><span class="sxs-lookup"><span data-stu-id="49541-217">Structuring a solution</span></span>

<span data-ttu-id="49541-218">Dalším důležitým aspektem řešení vícenásobného projektu navazuje dobrý celková struktura projektu.</span><span class="sxs-lookup"><span data-stu-id="49541-218">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="49541-219">Kód můžete uspořádat, ale chcete, a také propojit každý projekt, ze souboru řešení s `dotnet sln add`, nebudete moci spustit `dotnet restore` a `dotnet build` na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="49541-219">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
