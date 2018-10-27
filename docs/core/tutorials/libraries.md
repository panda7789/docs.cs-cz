---
title: Vývoj knihoven pomocí nástrojů pro různé platformy
description: Zjistěte, jak vytvořit knihovny pro .NET pomocí nástrojů rozhraní příkazového řádku .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 05/01/2017
ms.openlocfilehash: eb1dc404f9a08940464eca83a6848076b589afa8
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188258"
---
# <a name="developing-libraries-with-cross-platform-tools"></a><span data-ttu-id="103f4-103">Vývoj knihoven pomocí nástrojů pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="103f4-103">Developing Libraries with Cross Platform Tools</span></span>

<span data-ttu-id="103f4-104">Tento článek popisuje, jak napsat knihoven pro .NET pomocí nástrojů příkazového řádku pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="103f4-104">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="103f4-105">Rozhraní příkazového řádku poskytuje efektivní a nízké úrovně funkce, která funguje v jakémkoli operačním systému podporovaný.</span><span class="sxs-lookup"><span data-stu-id="103f4-105">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="103f4-106">Stále můžete vytvářet knihovny se zmírněními hrozeb Visual Studio, a pokud je to upřednostňovaný prostředí [příručce sady Visual Studio](libraries-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="103f4-106">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](libraries-with-vs.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="103f4-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="103f4-107">Prerequisites</span></span>

<span data-ttu-id="103f4-108">Potřebujete [.NET Core SDK a rozhraní příkazového řádku](https://www.microsoft.com/net/core) na vašem počítači nainstalovaný.</span><span class="sxs-lookup"><span data-stu-id="103f4-108">You need [the .NET Core SDK and CLI](https://www.microsoft.com/net/core) installed on your machine.</span></span>

<span data-ttu-id="103f4-109">V částech tohoto dokumentu se zabývá verze rozhraní .NET Framework, je nutné [rozhraní .NET Framework](http://getdotnet.azurewebsites.net/) nainstalovaná na počítači s Windows.</span><span class="sxs-lookup"><span data-stu-id="103f4-109">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](http://getdotnet.azurewebsites.net/) installed on a Windows machine.</span></span>

<span data-ttu-id="103f4-110">Kromě toho pokud chcete podporovat starší cíle rozhraní .NET Framework, je potřeba nainstalovat cílení/developer Pack pro starší verze rozhraní framework z [.NET cílové platformy stránky](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span><span class="sxs-lookup"><span data-stu-id="103f4-110">Additionally, if you wish to support older .NET Framework targets, you need to install targeting/developer packs for older framework versions from the [.NET target platforms page](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html).</span></span> <span data-ttu-id="103f4-111">Najdete v této tabulce:</span><span class="sxs-lookup"><span data-stu-id="103f4-111">Refer to this table:</span></span>

| <span data-ttu-id="103f4-112">Verze rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="103f4-112">.NET Framework Version</span></span> | <span data-ttu-id="103f4-113">Co se má stáhnout</span><span class="sxs-lookup"><span data-stu-id="103f4-113">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="103f4-114">4.6.1</span><span class="sxs-lookup"><span data-stu-id="103f4-114">4.6.1</span></span>                  | <span data-ttu-id="103f4-115">Rozhraní .NET framework 4.6.1 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="103f4-115">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="103f4-116">4.6</span><span class="sxs-lookup"><span data-stu-id="103f4-116">4.6</span></span>                    | <span data-ttu-id="103f4-117">Rozhraní .NET framework 4.6 Targeting Pack</span><span class="sxs-lookup"><span data-stu-id="103f4-117">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="103f4-118">4.5.2</span><span class="sxs-lookup"><span data-stu-id="103f4-118">4.5.2</span></span>                  | <span data-ttu-id="103f4-119">Rozhraní .NET framework 4.5.2 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="103f4-119">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="103f4-120">4.5.1</span><span class="sxs-lookup"><span data-stu-id="103f4-120">4.5.1</span></span>                  | <span data-ttu-id="103f4-121">Rozhraní .NET framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="103f4-121">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="103f4-122">4.5</span><span class="sxs-lookup"><span data-stu-id="103f4-122">4.5</span></span>                    | <span data-ttu-id="103f4-123">Sada Windows SDK pro aplikace pro Windows 8</span><span class="sxs-lookup"><span data-stu-id="103f4-123">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="103f4-124">4.0</span><span class="sxs-lookup"><span data-stu-id="103f4-124">4.0</span></span>                    | <span data-ttu-id="103f4-125">Windows SDK pro Windows 7 a rozhraní .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="103f4-125">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="103f4-126">2.0, 3.0 a 3.5</span><span class="sxs-lookup"><span data-stu-id="103f4-126">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="103f4-127">Modul Runtime rozhraní .NET framework 3.5 SP1 (nebo verze systému Windows 8 +)</span><span class="sxs-lookup"><span data-stu-id="103f4-127">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="103f4-128">Tom, jak cílit na .NET Standard</span><span class="sxs-lookup"><span data-stu-id="103f4-128">How to target the .NET Standard</span></span>

<span data-ttu-id="103f4-129">Pokud si nejste zcela obeznámeni s .NET Standard, přečtěte si [.NET Standard](../../standard/net-standard.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="103f4-129">If you're not quite familiar with the .NET Standard, refer to the [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="103f4-130">V tomto článku je tabulka, která mapuje na různé implementace .NET Standard verze:</span><span class="sxs-lookup"><span data-stu-id="103f4-130">In that article, there is a table which maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](~/includes/net-standard-table.md)]

<span data-ttu-id="103f4-131">Zde je, co tato tabulka znamená, že pro účely vytvoření knihovny:</span><span class="sxs-lookup"><span data-stu-id="103f4-131">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="103f4-132">Verze .NET standardu vyberete bude kompromis mezi přístup k nejnovější rozhraní API a možnosti cílit na více implementací rozhraní .NET a .NET Standard verze.</span><span class="sxs-lookup"><span data-stu-id="103f4-132">The version of the .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="103f4-133">Řídit řadu targetable platformy a verze na verzi výběrem `netstandardX.X` (kde `X.X` je číslo verze) a jeho přidání do souboru projektu (`.csproj` nebo `.fsproj`).</span><span class="sxs-lookup"><span data-stu-id="103f4-133">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (Where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="103f4-134">Existují tři primární možnosti při cílení na .NET Standard, v závislosti na potřebách.</span><span class="sxs-lookup"><span data-stu-id="103f4-134">You have three primary options when targeting the .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="103f4-135">Můžete použít výchozí verzi .NET Standard poskytuje šablony - `netstandard1.4` – které dává vám přístup k většině rozhraní API na .NET Standard, ale stále kompatibilní s UWP, rozhraní .NET Framework 4.6.1 a budoucích .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="103f4-135">You can use the default version of the .NET Standard supplied by templates - `netstandard1.4` - which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and the forthcoming .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="103f4-136">Pomocí úpravy hodnoty v můžete použít nižší nebo vyšší verze rozhraní .NET Standard `TargetFramework` uzlu souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="103f4-136">You can use a lower or higher version of the .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>
    
    <span data-ttu-id="103f4-137">Verze .NET standard jsou zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="103f4-137">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="103f4-138">To znamená, že `netstandard1.0` knihovny spouštět `netstandard1.1` platformy a vyšší.</span><span class="sxs-lookup"><span data-stu-id="103f4-138">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="103f4-139">Však neexistuje žádná dopředné kompatibility – nižší platformy .NET Standard nemůže odkazovat na větší z nich.</span><span class="sxs-lookup"><span data-stu-id="103f4-139">However, there is no forward compatibility - lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="103f4-140">To znamená, že `netstandard1.0` knihovny nelze referenční dokumentace knihovny, které cílí `netstandard1.1` nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="103f4-140">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="103f4-141">Vyberte verzi Standard, která má správné kombinace podpoře platforem a rozhraní API pro vaše potřeby.</span><span class="sxs-lookup"><span data-stu-id="103f4-141">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="103f4-142">Doporučujeme `netstandard1.4` teď.</span><span class="sxs-lookup"><span data-stu-id="103f4-142">We recommend `netstandard1.4` for now.</span></span>
    
3. <span data-ttu-id="103f4-143">Pokud chcete cílit na rozhraní .NET Framework verze 4.0 nebo níže, nebo chcete použít rozhraní API, které jsou k dispozici v rozhraní .NET Framework, ale ne v .NET Standard (například `System.Drawing`), přečtěte si následující části a zjistěte, jak multitarget.</span><span class="sxs-lookup"><span data-stu-id="103f4-143">If you want to target the .NET Framework versions 4.0 or below, or you wish to use an API available in the .NET Framework but not in the .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-the-net-framework"></a><span data-ttu-id="103f4-144">Jak se zaměřit na rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="103f4-144">How to target the .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="103f4-145">Tyto pokyny předpokládají, že máte na svém počítači nainstalováno rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="103f4-145">These instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="103f4-146">Odkazovat [požadavky](#prerequisites) získání závislostí nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="103f4-146">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="103f4-147">Mějte na paměti, že některé verze rozhraní .NET Framework se tady použít jsou už v technické podpory.</span><span class="sxs-lookup"><span data-stu-id="103f4-147">Keep in mind that some of the .NET Framework versions used here are no longer in support.</span></span> <span data-ttu-id="103f4-148">Odkazovat [rozhraní .NET Framework podpory životního cyklu nejčastější dotazy k zásadám](https://support.microsoft.com/gp/framework_faq/en-us) týkajících se nepodporovaných verzí.</span><span class="sxs-lookup"><span data-stu-id="103f4-148">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="103f4-149">Pokud chcete dosáhnout maximálního počtu vývojáři a projekty, použijte jako základní cílové rozhraní .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="103f4-149">If you want to reach the maximum number of developers and projects, use the .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="103f4-150">Chcete-li cílit na rozhraní .NET Framework, je potřeba začít s použitím správné cílové rozhraní Framework Moniker (TFM), která odpovídá verzi rozhraní .NET Framework, kterou chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="103f4-150">To target the .NET Framework, you will need to begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

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

<span data-ttu-id="103f4-151">Vložte tento TFM do `TargetFramework` část souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="103f4-151">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="103f4-152">Například tady je způsob, měli byste napsat knihovnu, která cílí na rozhraní .NET Framework 4.0:</span><span class="sxs-lookup"><span data-stu-id="103f4-152">For example, here's how you would write a library which targets the .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="103f4-153">A to je všechno!</span><span class="sxs-lookup"><span data-stu-id="103f4-153">And that's it!</span></span> <span data-ttu-id="103f4-154">I když to zkompilovat pouze pro rozhraní .NET Framework 4, můžete použít knihovnu v novějších verzích rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="103f4-154">Although this compiled only for the .NET Framework 4, you can use the library on newer versions of the .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="103f4-155">Jak Multitarget</span><span class="sxs-lookup"><span data-stu-id="103f4-155">How to Multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="103f4-156">Následující pokyny předpokládají, že máte na svém počítači nainstalováno rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="103f4-156">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="103f4-157">Odkazovat [požadavky](#prerequisites) naleznete další závislosti, které je potřeba nainstalovat a kam stáhnete z.</span><span class="sxs-lookup"><span data-stu-id="103f4-157">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="103f4-158">Budete muset svůj projekt podporuje rozhraní .NET Framework a .NET Core cíleny na starší verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="103f4-158">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="103f4-159">V tomto scénáři, pokud chcete použít pro novější cíle novějších rozhraní API a jazykovým konstrukcím, použijte `#if` direktiv ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="103f4-159">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="103f4-160">Potřebujete také přidat různé balíčky a závislosti pro každou platformu, na kterou cílíte zahrnout do různých rozhraní API potřebné pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="103f4-160">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="103f4-161">Řekněme například, že máte knihovnu, která provádí síťové operace přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="103f4-161">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="103f4-162">Pro .NET Standard a .NET Framework verze 4.5 nebo vyšší, můžete použít `HttpClient` třídy z `System.Net.Http` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="103f4-162">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="103f4-163">Však nemají dřívějších verzích rozhraní .NET Framework `HttpClient` třídy, takže můžete použít `WebClient` třídy z `System.Net` obor názvů pro ty místo.</span><span class="sxs-lookup"><span data-stu-id="103f4-163">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="103f4-164">Váš soubor projektu může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="103f4-164">Your project file could look like this:</span></span>

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

<span data-ttu-id="103f4-165">Všimněte si tři hlavní změny tady:</span><span class="sxs-lookup"><span data-stu-id="103f4-165">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="103f4-166">`TargetFramework` Uzlu se nahradil `TargetFrameworks`, a tři Tfm jsou vyjádřeny v.</span><span class="sxs-lookup"><span data-stu-id="103f4-166">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="103f4-167">Je `<ItemGroup>` uzel `net40 ` cílové souhrnné informace v jednom odkazu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="103f4-167">There is an `<ItemGroup>` node for the `net40 ` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="103f4-168">Je `<ItemGroup>` uzel `net45` cílové stahování dva odkazy na rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="103f4-168">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="103f4-169">Systém sestavení je seznámen následující symboly preprocesoru používané `#if` direktivy:</span><span class="sxs-lookup"><span data-stu-id="103f4-169">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](~/includes/preprocessor-symbols.md)]

<span data-ttu-id="103f4-170">Tady je příklad provedete použití podmíněné kompilace na cíle:</span><span class="sxs-lookup"><span data-stu-id="103f4-170">Here is an example making use of conditional compilation per-target:</span></span>

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

<span data-ttu-id="103f4-171">Pokud vytvoříte tento projekt s `dotnet build`, uvidíte tři adresářů podřízených adresáři `bin/` složky:</span><span class="sxs-lookup"><span data-stu-id="103f4-171">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="103f4-172">Každý z nich obsahuje `.dll` soubory pro každý cíl.</span><span class="sxs-lookup"><span data-stu-id="103f4-172">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="103f4-173">Testování knihovny v rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="103f4-173">How to test libraries on .NET Core</span></span>

<span data-ttu-id="103f4-174">Je důležité mít možnost Testovat napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="103f4-174">It's important to be able to test across platforms.</span></span> <span data-ttu-id="103f4-175">Můžete použít buď [xUnit](https://xunit.github.io/) nebo MSTest úprav.</span><span class="sxs-lookup"><span data-stu-id="103f4-175">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="103f4-176">Obě jsou dokonale vhodný pro testování vaší knihovny v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="103f4-176">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="103f4-177">Jak nastavit řešení s testovacími projekty, bude záviset na [struktura vašeho řešení](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="103f4-177">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="103f4-178">V následujícím příkladu se předpokládá, že live test a zdrojového adresáře ve stejném adresáři nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="103f4-178">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="103f4-179">Tento mechanismus využívá některé [příkazy rozhraní příkazového řádku .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="103f4-179">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="103f4-180">Zobrazit [dotnet nové](../tools/dotnet-new.md) a [dotnet sln](../tools/dotnet-sln.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="103f4-180">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="103f4-181">Nastavení řešení.</span><span class="sxs-lookup"><span data-stu-id="103f4-181">Set up your solution.</span></span> <span data-ttu-id="103f4-182">Můžete tak učinit pomocí následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="103f4-182">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="103f4-183">To vytvoří projekty a propojit dohromady v řešení.</span><span class="sxs-lookup"><span data-stu-id="103f4-183">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="103f4-184">V adresáři `SolutionWithSrcAndTest` by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="103f4-184">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="103f4-185">Přejděte do adresáře projektu testu a přidejte odkaz na `MyProject.Test` z `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="103f4-185">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="103f4-186">Obnovení balíčků a sestavit projekty:</span><span class="sxs-lookup"><span data-stu-id="103f4-186">Restore packages and build projects:</span></span>

   ```bash
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

1. <span data-ttu-id="103f4-187">Ověřte, že xUnit běží spuštěním `dotnet test` příkazu.</span><span class="sxs-lookup"><span data-stu-id="103f4-187">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="103f4-188">Pokud jste se rozhodli použít MSTest, byste místo toho spustit MSTest runner konzoly.</span><span class="sxs-lookup"><span data-stu-id="103f4-188">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>
    
<span data-ttu-id="103f4-189">A to je všechno!</span><span class="sxs-lookup"><span data-stu-id="103f4-189">And that's it!</span></span> <span data-ttu-id="103f4-190">Teď můžete otestovat vaši knihovnu na všech platformách pomocí nástrojů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="103f4-190">You can now test your library across all platforms using command line tools.</span></span> <span data-ttu-id="103f4-191">Pokračovat v testování teď, když máte všechno, co nastavíte, testování knihovny je velmi jednoduchý:</span><span class="sxs-lookup"><span data-stu-id="103f4-191">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="103f4-192">Proveďte změny v knihovně.</span><span class="sxs-lookup"><span data-stu-id="103f4-192">Make changes to your library.</span></span>
1. <span data-ttu-id="103f4-193">Spuštění testů z příkazového řádku v adresáři test s `dotnet test` příkazu.</span><span class="sxs-lookup"><span data-stu-id="103f4-193">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="103f4-194">Váš kód bude automaticky znovu vytvořen při vyvolání `dotnet test` příkazu.</span><span class="sxs-lookup"><span data-stu-id="103f4-194">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="103f4-195">Jak používat více projektů</span><span class="sxs-lookup"><span data-stu-id="103f4-195">How to use multiple projects</span></span>

<span data-ttu-id="103f4-196">Běžné potřebu větší knihovny, je umístit funkce v různých projektech.</span><span class="sxs-lookup"><span data-stu-id="103f4-196">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="103f4-197">Představte si, že jste si přáli sestavit knihovnu, která by mohla využívat idiomatickou jazyků C# a F #.</span><span class="sxs-lookup"><span data-stu-id="103f4-197">Imagine you wished to build a library which could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="103f4-198">To by znamenalo, že spotřebitelé knihovny je využívat způsoby, které jsou přirozené pro C# nebo F #.</span><span class="sxs-lookup"><span data-stu-id="103f4-198">That would mean that consumers of your library consume them in ways which are natural to C# or F#.</span></span> <span data-ttu-id="103f4-199">Například v jazyce C# může využívat knihovny takto:</span><span class="sxs-lookup"><span data-stu-id="103f4-199">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="103f4-200">V jazyce F # může vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="103f4-200">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="103f4-201">Scénáře využití, jako je to znamená, že rozhraní API, ke kterému přistupujete musí mít odlišnou strukturu pro C# a F #.</span><span class="sxs-lookup"><span data-stu-id="103f4-201">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="103f4-202">Běžným přístupem k provádění to je faktor veškerou logiku knihovny do projektu core, s projekty C# a F # definice rozhraní API vrstvy, které volají do tohoto projektu core.</span><span class="sxs-lookup"><span data-stu-id="103f4-202">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="103f4-203">Zbytek části budete používat následující názvy:</span><span class="sxs-lookup"><span data-stu-id="103f4-203">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="103f4-204">**AwesomeLibrary.Core** – základní projekt, který bude obsahovat veškerou logiku pro knihovnu</span><span class="sxs-lookup"><span data-stu-id="103f4-204">**AwesomeLibrary.Core** - A core project which contains all logic for the library</span></span>
* <span data-ttu-id="103f4-205">**AwesomeLibrary.CSharp** – projekt pomocí veřejných rozhraní API určené pro použití v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="103f4-205">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="103f4-206">**AwesomeLibrary.FSharp** – projekt pomocí veřejných rozhraní API určené pro použití v jazyce F #</span><span class="sxs-lookup"><span data-stu-id="103f4-206">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="103f4-207">Spuštěním následujících příkazů v terminálu vytvořit stejnou strukturu jako vodítko při tom tato:</span><span class="sxs-lookup"><span data-stu-id="103f4-207">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

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

<span data-ttu-id="103f4-208">Tato možnost přidá výše uvedených tří projektů a soubor řešení, které propojí je dohromady.</span><span class="sxs-lookup"><span data-stu-id="103f4-208">This will add the three projects above and a solution file which links them together.</span></span> <span data-ttu-id="103f4-209">Vytváření souboru řešení a propojování projektů vám umožní obnovit a sestavit projekty z nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="103f4-209">Creating the solution file and linking projects will allow you to restore and build projects from a top-level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="103f4-210">Odkazování na projekt na projekt</span><span class="sxs-lookup"><span data-stu-id="103f4-210">Project-to-project referencing</span></span>

<span data-ttu-id="103f4-211">Použití rozhraní příkazového řádku .NET Core k přidání odkazu na projekt je nejlepší způsob, jak odkazovat na projekt.</span><span class="sxs-lookup"><span data-stu-id="103f4-211">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="103f4-212">Z **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** adresáře projektu, můžete spustit následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="103f4-212">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```console
$ dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="103f4-213">Soubory projektu pro obě **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** bude nyní odkaz **AwesomeLibrary.Core** jako `ProjectReference` cíl.</span><span class="sxs-lookup"><span data-stu-id="103f4-213">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="103f4-214">Můžete to ověřit tak kontrolu souborů projektu a zobrazuje v je následující:</span><span class="sxs-lookup"><span data-stu-id="103f4-214">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="103f4-215">V této části můžete ručně přidat do každého souboru projektu, pokud nechcete používat rozhraní příkazového řádku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="103f4-215">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="103f4-216">Strukturování řešení</span><span class="sxs-lookup"><span data-stu-id="103f4-216">Structuring a solution</span></span>

<span data-ttu-id="103f4-217">Jiný důležitý aspekt řešení vícenásobného projektu se vytvářejí dobré celkovou strukturu projektu.</span><span class="sxs-lookup"><span data-stu-id="103f4-217">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="103f4-218">Kód můžete uspořádat, ale potřebujete, a tak dlouho, dokud každý projekt odkazujete na soubor řešení s `dotnet sln add`, bude možné spustit `dotnet restore` a `dotnet build` na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="103f4-218">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
