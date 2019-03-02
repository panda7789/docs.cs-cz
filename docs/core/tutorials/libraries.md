---
title: Vývoj knihoven pomocí nástrojů pro různé platformy
description: Zjistěte, jak vytvářet knihovny .NET Core pomocí nástroje příkazového řádku .NET Core. Vytvoříte knihovnu, která podporuje více platforem.
author: cartermp
ms.date: 05/01/2017
ms.custom: seodec18
ms.openlocfilehash: 9dd1d8477f8e34e79ff521463972e26a21ad1dfd
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212063"
---
# <a name="developing-libraries-with-cross-platform-tools"></a><span data-ttu-id="9f664-104">Vývoj knihoven pomocí nástrojů pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="9f664-104">Developing Libraries with Cross Platform Tools</span></span>

<span data-ttu-id="9f664-105">Tento článek popisuje, jak napsat knihoven pro .NET pomocí nástrojů příkazového řádku pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="9f664-105">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="9f664-106">Rozhraní příkazového řádku poskytuje efektivní a nízké úrovně funkce, která funguje v jakémkoli operačním systému podporovaný.</span><span class="sxs-lookup"><span data-stu-id="9f664-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="9f664-107">Stále můžete vytvářet knihovny se zmírněními hrozeb Visual Studio, a pokud je to upřednostňovaný prostředí [příručce sady Visual Studio](libraries-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="9f664-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](libraries-with-vs.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9f664-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9f664-108">Prerequisites</span></span>

<span data-ttu-id="9f664-109">Potřebujete [.NET Core SDK a rozhraní příkazového řádku](https://www.microsoft.com/net/core) na vašem počítači nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="9f664-109">You need [the .NET Core SDK and CLI](https://www.microsoft.com/net/core) installed on your machine.</span></span>

<span data-ttu-id="9f664-110">V částech tohoto dokumentu se zabývá verze rozhraní .NET Framework, je nutné [rozhraní .NET Framework](https://dotnet.microsoft.com) nainstalovaná na počítači s Windows.</span><span class="sxs-lookup"><span data-stu-id="9f664-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="9f664-111">Kromě toho pokud chcete podporovat starší cíle rozhraní .NET Framework, je potřeba nainstalovat cílení/developer Pack pro starší verze rozhraní framework z [stáhnout .NET archivuje stránky](https://dotnet.microsoft.com/download/archives).</span><span class="sxs-lookup"><span data-stu-id="9f664-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting/developer packs for older framework versions from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="9f664-112">Najdete v této tabulce:</span><span class="sxs-lookup"><span data-stu-id="9f664-112">Refer to this table:</span></span>

| <span data-ttu-id="9f664-113">Verze rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="9f664-113">.NET Framework Version</span></span> | <span data-ttu-id="9f664-114">Co se má stáhnout</span><span class="sxs-lookup"><span data-stu-id="9f664-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="9f664-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="9f664-115">4.6.1</span></span>                  | <span data-ttu-id="9f664-116">Rozhraní .NET framework 4.6.1 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="9f664-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="9f664-117">4.6</span><span class="sxs-lookup"><span data-stu-id="9f664-117">4.6</span></span>                    | <span data-ttu-id="9f664-118">Rozhraní .NET framework 4.6 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="9f664-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="9f664-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="9f664-119">4.5.2</span></span>                  | <span data-ttu-id="9f664-120">Rozhraní .NET framework 4.5.2 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="9f664-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="9f664-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="9f664-121">4.5.1</span></span>                  | <span data-ttu-id="9f664-122">Rozhraní .NET framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="9f664-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="9f664-123">4.5</span><span class="sxs-lookup"><span data-stu-id="9f664-123">4.5</span></span>                    | <span data-ttu-id="9f664-124">Sada Windows SDK pro aplikace pro Windows 8</span><span class="sxs-lookup"><span data-stu-id="9f664-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="9f664-125">4.0</span><span class="sxs-lookup"><span data-stu-id="9f664-125">4.0</span></span>                    | <span data-ttu-id="9f664-126">Windows SDK pro Windows 7 a rozhraní .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="9f664-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="9f664-127">2.0, 3.0 a 3.5</span><span class="sxs-lookup"><span data-stu-id="9f664-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="9f664-128">Modul Runtime rozhraní .NET framework 3.5 SP1 (nebo verze systému Windows 8 +)</span><span class="sxs-lookup"><span data-stu-id="9f664-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="9f664-129">Tom, jak cílit na .NET Standard</span><span class="sxs-lookup"><span data-stu-id="9f664-129">How to target the .NET Standard</span></span>

<span data-ttu-id="9f664-130">Pokud si nejste zcela obeznámeni s .NET Standard, přečtěte si [.NET Standard](../../standard/net-standard.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="9f664-130">If you're not quite familiar with the .NET Standard, refer to the [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="9f664-131">V tomto článku je tabulka, která mapuje na různé implementace .NET Standard verze:</span><span class="sxs-lookup"><span data-stu-id="9f664-131">In that article, there is a table which maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="9f664-132">Zde je, co tato tabulka znamená, že pro účely vytvoření knihovny:</span><span class="sxs-lookup"><span data-stu-id="9f664-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="9f664-133">Verze .NET standardu vyberete bude kompromis mezi přístup k nejnovější rozhraní API a možnosti cílit na více implementací rozhraní .NET a .NET Standard verze.</span><span class="sxs-lookup"><span data-stu-id="9f664-133">The version of the .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="9f664-134">Řídit řadu targetable platformy a verze na verzi výběrem `netstandardX.X` (kde `X.X` je číslo verze) a jeho přidání do souboru projektu (`.csproj` nebo `.fsproj`).</span><span class="sxs-lookup"><span data-stu-id="9f664-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (Where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="9f664-135">Existují tři primární možnosti při cílení na .NET Standard, v závislosti na potřebách.</span><span class="sxs-lookup"><span data-stu-id="9f664-135">You have three primary options when targeting the .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="9f664-136">Můžete použít výchozí verzi .NET Standard poskytuje šablony - `netstandard1.4` – které dává vám přístup k většině rozhraní API na .NET Standard, ale stále kompatibilní s UWP, rozhraní .NET Framework 4.6.1 a budoucích .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="9f664-136">You can use the default version of the .NET Standard supplied by templates - `netstandard1.4` - which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and the forthcoming .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="9f664-137">Pomocí úpravy hodnoty v můžete použít nižší nebo vyšší verze rozhraní .NET Standard `TargetFramework` uzlu souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9f664-137">You can use a lower or higher version of the .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="9f664-138">Verze .NET standard jsou zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="9f664-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="9f664-139">To znamená, že `netstandard1.0` knihovny spouštět `netstandard1.1` platformy a vyšší.</span><span class="sxs-lookup"><span data-stu-id="9f664-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="9f664-140">Však neexistuje žádná dopředné kompatibility – nižší platformy .NET Standard nemůže odkazovat na větší z nich.</span><span class="sxs-lookup"><span data-stu-id="9f664-140">However, there is no forward compatibility - lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="9f664-141">To znamená, že `netstandard1.0` knihovny nelze referenční dokumentace knihovny, které cílí `netstandard1.1` nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="9f664-141">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="9f664-142">Vyberte verzi Standard, která má správné kombinace podpoře platforem a rozhraní API pro vaše potřeby.</span><span class="sxs-lookup"><span data-stu-id="9f664-142">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="9f664-143">Doporučujeme `netstandard1.4` teď.</span><span class="sxs-lookup"><span data-stu-id="9f664-143">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="9f664-144">Pokud chcete cílit na rozhraní .NET Framework verze 4.0 nebo níže, nebo chcete použít rozhraní API, které jsou k dispozici v rozhraní .NET Framework, ale ne v .NET Standard (například `System.Drawing`), přečtěte si následující části a zjistěte, jak multitarget.</span><span class="sxs-lookup"><span data-stu-id="9f664-144">If you want to target the .NET Framework versions 4.0 or below, or you wish to use an API available in the .NET Framework but not in the .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-the-net-framework"></a><span data-ttu-id="9f664-145">Jak se zaměřit na rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9f664-145">How to target the .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="9f664-146">Tyto pokyny předpokládají, že máte na svém počítači nainstalováno rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f664-146">These instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="9f664-147">Odkazovat [požadavky](#prerequisites) získání závislostí nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="9f664-147">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="9f664-148">Mějte na paměti, že některé verze rozhraní .NET Framework se tady použít jsou už v technické podpory.</span><span class="sxs-lookup"><span data-stu-id="9f664-148">Keep in mind that some of the .NET Framework versions used here are no longer in support.</span></span> <span data-ttu-id="9f664-149">Odkazovat [rozhraní .NET Framework podpory životního cyklu nejčastější dotazy k zásadám](https://support.microsoft.com/gp/framework_faq/en-us) týkajících se nepodporovaných verzí.</span><span class="sxs-lookup"><span data-stu-id="9f664-149">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="9f664-150">Pokud chcete dosáhnout maximálního počtu vývojáři a projekty, použijte jako základní cílové rozhraní .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="9f664-150">If you want to reach the maximum number of developers and projects, use the .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="9f664-151">Chcete-li cílit na rozhraní .NET Framework, je potřeba začít s použitím správné cílové rozhraní Framework Moniker (TFM), která odpovídá verzi rozhraní .NET Framework, kterou chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="9f664-151">To target the .NET Framework, you will need to begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

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

<span data-ttu-id="9f664-152">Vložte tento TFM do `TargetFramework` část souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="9f664-152">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="9f664-153">Například tady je způsob, měli byste napsat knihovnu, která cílí na rozhraní .NET Framework 4.0:</span><span class="sxs-lookup"><span data-stu-id="9f664-153">For example, here's how you would write a library which targets the .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="9f664-154">A to je všechno!</span><span class="sxs-lookup"><span data-stu-id="9f664-154">And that's it!</span></span> <span data-ttu-id="9f664-155">I když to zkompilovat pouze pro rozhraní .NET Framework 4, můžete použít knihovnu v novějších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f664-155">Although this compiled only for the .NET Framework 4, you can use the library on newer versions of the .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="9f664-156">Jak Multitarget</span><span class="sxs-lookup"><span data-stu-id="9f664-156">How to Multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="9f664-157">Následující pokyny předpokládají, že máte na svém počítači nainstalováno rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f664-157">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="9f664-158">Odkazovat [požadavky](#prerequisites) naleznete další závislosti, které je potřeba nainstalovat a kam stáhnete z.</span><span class="sxs-lookup"><span data-stu-id="9f664-158">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="9f664-159">Budete muset svůj projekt podporuje rozhraní .NET Framework a .NET Core cíleny na starší verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f664-159">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="9f664-160">V tomto scénáři, pokud chcete použít pro novější cíle novějších rozhraní API a jazykovým konstrukcím, použijte `#if` direktiv ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="9f664-160">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="9f664-161">Potřebujete také přidat různé balíčky a závislosti pro každou platformu, na kterou cílíte zahrnout do různých rozhraní API potřebné pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="9f664-161">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="9f664-162">Řekněme například, že máte knihovnu, která provádí síťové operace přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="9f664-162">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="9f664-163">Pro .NET Standard a .NET Framework verze 4.5 nebo vyšší, můžete použít `HttpClient` třídy z `System.Net.Http` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9f664-163">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="9f664-164">Však nemají dřívějších verzích rozhraní .NET Framework `HttpClient` třídy, takže můžete použít `WebClient` třídy z `System.Net` obor názvů pro ty místo.</span><span class="sxs-lookup"><span data-stu-id="9f664-164">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="9f664-165">Váš soubor projektu může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="9f664-165">Your project file could look like this:</span></span>

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

<span data-ttu-id="9f664-166">Všimněte si tři hlavní změny tady:</span><span class="sxs-lookup"><span data-stu-id="9f664-166">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="9f664-167">`TargetFramework` Uzlu se nahradil `TargetFrameworks`, a tři Tfm jsou vyjádřeny v.</span><span class="sxs-lookup"><span data-stu-id="9f664-167">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="9f664-168">Je `<ItemGroup>` uzel `net40` cílové souhrnné informace v jednom odkazu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f664-168">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="9f664-169">Je `<ItemGroup>` uzel `net45` cílové stahování dva odkazy na rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f664-169">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="9f664-170">Systém sestavení je seznámen následující symboly preprocesoru používané `#if` direktivy:</span><span class="sxs-lookup"><span data-stu-id="9f664-170">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="9f664-171">Tady je příklad provedete použití podmíněné kompilace na cíle:</span><span class="sxs-lookup"><span data-stu-id="9f664-171">Here is an example making use of conditional compilation per-target:</span></span>

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
            string url = "https://www.dotnetfoundation.org/";

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
            string url = "https://www.dotnetfoundation.org/";

            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);

            int dotNetCount = Regex.Matches(result, ".NET").Count;

            return $"dotnetfoundation.org mentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
}
```

<span data-ttu-id="9f664-172">Pokud vytvoříte tento projekt s `dotnet build`, uvidíte tři adresářů podřízených adresáři `bin/` složky:</span><span class="sxs-lookup"><span data-stu-id="9f664-172">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="9f664-173">Každý z nich obsahuje `.dll` soubory pro každý cíl.</span><span class="sxs-lookup"><span data-stu-id="9f664-173">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="9f664-174">Testování knihovny v rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="9f664-174">How to test libraries on .NET Core</span></span>

<span data-ttu-id="9f664-175">Je důležité mít možnost Testovat napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="9f664-175">It's important to be able to test across platforms.</span></span> <span data-ttu-id="9f664-176">Můžete použít buď [xUnit](https://xunit.github.io/) nebo MSTest úprav.</span><span class="sxs-lookup"><span data-stu-id="9f664-176">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="9f664-177">Obě jsou dokonale vhodný pro testování vaší knihovny v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9f664-177">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="9f664-178">Jak nastavit řešení s testovacími projekty, bude záviset na [struktura vašeho řešení](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="9f664-178">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="9f664-179">V následujícím příkladu se předpokládá, že live test a zdrojového adresáře ve stejném adresáři nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="9f664-179">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="9f664-180">Tento mechanismus využívá některé [příkazy rozhraní příkazového řádku .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="9f664-180">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="9f664-181">Zobrazit [dotnet nové](../tools/dotnet-new.md) a [dotnet sln](../tools/dotnet-sln.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="9f664-181">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="9f664-182">Nastavení řešení.</span><span class="sxs-lookup"><span data-stu-id="9f664-182">Set up your solution.</span></span> <span data-ttu-id="9f664-183">Můžete tak učinit pomocí následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="9f664-183">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="9f664-184">To vytvoří projekty a propojit dohromady v řešení.</span><span class="sxs-lookup"><span data-stu-id="9f664-184">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="9f664-185">V adresáři `SolutionWithSrcAndTest` by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="9f664-185">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="9f664-186">Přejděte do adresáře projektu testu a přidejte odkaz na `MyProject.Test` z `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="9f664-186">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="9f664-187">Obnovení balíčků a sestavit projekty:</span><span class="sxs-lookup"><span data-stu-id="9f664-187">Restore packages and build projects:</span></span>

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="9f664-188">Ověřte, že xUnit běží spuštěním `dotnet test` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f664-188">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="9f664-189">Pokud jste se rozhodli použít MSTest, byste místo toho spustit MSTest runner konzoly.</span><span class="sxs-lookup"><span data-stu-id="9f664-189">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="9f664-190">A to je všechno!</span><span class="sxs-lookup"><span data-stu-id="9f664-190">And that's it!</span></span> <span data-ttu-id="9f664-191">Teď můžete otestovat vaši knihovnu na všech platformách pomocí nástrojů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="9f664-191">You can now test your library across all platforms using command line tools.</span></span> <span data-ttu-id="9f664-192">Pokračovat v testování teď, když máte všechno, co nastavíte, testování knihovny je velmi jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="9f664-192">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="9f664-193">Proveďte změny v knihovně.</span><span class="sxs-lookup"><span data-stu-id="9f664-193">Make changes to your library.</span></span>
1. <span data-ttu-id="9f664-194">Spuštění testů z příkazového řádku v adresáři test s `dotnet test` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f664-194">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="9f664-195">Váš kód bude automaticky znovu vytvořen při vyvolání `dotnet test` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9f664-195">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="9f664-196">Jak používat více projektů</span><span class="sxs-lookup"><span data-stu-id="9f664-196">How to use multiple projects</span></span>

<span data-ttu-id="9f664-197">Běžné potřebu větší knihovny, je umístit funkce v různých projektech.</span><span class="sxs-lookup"><span data-stu-id="9f664-197">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="9f664-198">Představte si nepřejí vytvoří knihovnu, která by mohla využívat v idiomatickou C# a F#.</span><span class="sxs-lookup"><span data-stu-id="9f664-198">Imagine you wished to build a library which could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="9f664-199">To by znamenalo, že spotřebitelé knihovny je využívat způsoby, které jsou přirozené C# nebo F#.</span><span class="sxs-lookup"><span data-stu-id="9f664-199">That would mean that consumers of your library consume them in ways which are natural to C# or F#.</span></span> <span data-ttu-id="9f664-200">Například v jazyce C# může využívat knihovny takto:</span><span class="sxs-lookup"><span data-stu-id="9f664-200">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="9f664-201">V F#, může vypadat třeba takto:</span><span class="sxs-lookup"><span data-stu-id="9f664-201">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="9f664-202">Scénáře využití, jako je to znamená, že rozhraní API, ke kterému přistupujete musí mít odlišnou strukturu pro C# a F#.</span><span class="sxs-lookup"><span data-stu-id="9f664-202">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="9f664-203">Běžným přístupem k provádění to je zohlednit veškerou logiku knihovny do projektu core s C# a F# projekty definice rozhraní API vrstvy toto volání do tohoto projektu core.</span><span class="sxs-lookup"><span data-stu-id="9f664-203">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="9f664-204">Zbytek části budete používat následující názvy:</span><span class="sxs-lookup"><span data-stu-id="9f664-204">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="9f664-205">**AwesomeLibrary.Core** – základní projekt, který bude obsahovat veškerou logiku pro knihovnu</span><span class="sxs-lookup"><span data-stu-id="9f664-205">**AwesomeLibrary.Core** - A core project which contains all logic for the library</span></span>
* <span data-ttu-id="9f664-206">**AwesomeLibrary.CSharp** – projekt pomocí veřejných rozhraní API určené pro použití v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9f664-206">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="9f664-207">**AwesomeLibrary.FSharp** – projekt pomocí veřejného rozhraní API určené pro využití vF#</span><span class="sxs-lookup"><span data-stu-id="9f664-207">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="9f664-208">Spuštěním následujících příkazů v terminálu vytvořit stejnou strukturu jako vodítko při tom tato:</span><span class="sxs-lookup"><span data-stu-id="9f664-208">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

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

<span data-ttu-id="9f664-209">Tato možnost přidá výše uvedených tří projektů a soubor řešení, které propojí je dohromady.</span><span class="sxs-lookup"><span data-stu-id="9f664-209">This will add the three projects above and a solution file which links them together.</span></span> <span data-ttu-id="9f664-210">Vytváření souboru řešení a propojování projektů vám umožní obnovit a sestavit projekty z nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="9f664-210">Creating the solution file and linking projects will allow you to restore and build projects from a top-level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="9f664-211">Odkazování na projekt na projekt</span><span class="sxs-lookup"><span data-stu-id="9f664-211">Project-to-project referencing</span></span>

<span data-ttu-id="9f664-212">Použití rozhraní příkazového řádku .NET Core k přidání odkazu na projekt je nejlepší způsob, jak odkazovat na projekt.</span><span class="sxs-lookup"><span data-stu-id="9f664-212">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="9f664-213">Z **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** adresáře projektu, můžete spustit následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="9f664-213">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```console
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="9f664-214">Soubory projektu pro obě **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** bude nyní odkaz **AwesomeLibrary.Core** jako `ProjectReference` cíl.</span><span class="sxs-lookup"><span data-stu-id="9f664-214">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="9f664-215">Můžete to ověřit tak kontrolu souborů projektu a zobrazuje v je následující:</span><span class="sxs-lookup"><span data-stu-id="9f664-215">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="9f664-216">V této části můžete ručně přidat do každého souboru projektu, pokud nechcete používat rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9f664-216">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="9f664-217">Strukturování řešení</span><span class="sxs-lookup"><span data-stu-id="9f664-217">Structuring a solution</span></span>

<span data-ttu-id="9f664-218">Jiný důležitý aspekt řešení vícenásobného projektu se vytvářejí dobré celkovou strukturu projektu.</span><span class="sxs-lookup"><span data-stu-id="9f664-218">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="9f664-219">Kód můžete uspořádat, ale potřebujete, a tak dlouho, dokud každý projekt odkazujete na soubor řešení s `dotnet sln add`, bude možné spustit `dotnet restore` a `dotnet build` na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="9f664-219">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
