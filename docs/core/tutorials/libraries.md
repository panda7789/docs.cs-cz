---
title: Vývoj knihoven pomocí rozhraní CLI jádra .NET
description: Přečtěte si, jak vytvořit knihovny .NET Core pomocí rozhraní CLI jádra .NET. Vytvoříte knihovnu, která podporuje více architektur.
author: cartermp
ms.date: 05/01/2017
ms.openlocfilehash: c23c1f027b4d6d09c50eb2257d34f72ec56302f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503507"
---
# <a name="develop-libraries-with-the-net-core-cli"></a><span data-ttu-id="00845-104">Vývoj knihoven pomocí rozhraní CLI jádra .NET</span><span class="sxs-lookup"><span data-stu-id="00845-104">Develop libraries with the .NET Core CLI</span></span>

<span data-ttu-id="00845-105">Tento článek popisuje, jak psát knihovny pro rozhraní .NET pomocí rozhraní CLI jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="00845-105">This article covers how to write libraries for .NET using the .NET Core CLI.</span></span> <span data-ttu-id="00845-106">ClI poskytuje efektivní a nízké úrovně prostředí, které funguje v rámci všech podporovaných operačních systémů.</span><span class="sxs-lookup"><span data-stu-id="00845-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="00845-107">Stále můžete vytvářet knihovny s Visual Studio a pokud je vaše upřednostňované prostředí [naleznete v průvodci Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="00845-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="00845-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00845-108">Prerequisites</span></span>

<span data-ttu-id="00845-109">Potřebujete v [počítači nainstalovanou sadu .NET Core SDK a CLI.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="00845-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="00845-110">Pro části tohoto dokumentu, které se zabývají verzemi rozhraní .NET Framework, potřebujete rozhraní [.NET Framework](https://dotnet.microsoft.com) nainstalované v počítači se systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="00845-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="00845-111">Pokud chcete podporovat starší cíle rozhraní .NET Framework, je třeba nainstalovat balíčky cílení nebo vývojářské balíčky ze [stránky archivů ke stažení rozhraní .NET](https://dotnet.microsoft.com/download/archives).</span><span class="sxs-lookup"><span data-stu-id="00845-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="00845-112">Viz tato tabulka:</span><span class="sxs-lookup"><span data-stu-id="00845-112">Refer to this table:</span></span>

| <span data-ttu-id="00845-113">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="00845-113">.NET Framework version</span></span> | <span data-ttu-id="00845-114">Co stáhnout</span><span class="sxs-lookup"><span data-stu-id="00845-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="00845-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="00845-115">4.6.1</span></span>                  | <span data-ttu-id="00845-116">Balíček cílení rozhraní .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="00845-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="00845-117">4.6</span><span class="sxs-lookup"><span data-stu-id="00845-117">4.6</span></span>                    | <span data-ttu-id="00845-118">Balíček cílení rozhraní .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="00845-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="00845-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="00845-119">4.5.2</span></span>                  | <span data-ttu-id="00845-120">Sada .NET Framework 4.5.2 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="00845-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="00845-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="00845-121">4.5.1</span></span>                  | <span data-ttu-id="00845-122">Sada .NET Framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="00845-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="00845-123">4.5</span><span class="sxs-lookup"><span data-stu-id="00845-123">4.5</span></span>                    | <span data-ttu-id="00845-124">Sada Windows SDK pro aplikace pro Windows 8</span><span class="sxs-lookup"><span data-stu-id="00845-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="00845-125">4.0</span><span class="sxs-lookup"><span data-stu-id="00845-125">4.0</span></span>                    | <span data-ttu-id="00845-126">Sada Windows SDK pro systémy Windows 7 a rozhraní .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="00845-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="00845-127">2,0, 3,0 a 3,5</span><span class="sxs-lookup"><span data-stu-id="00845-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="00845-128">Běhčasu .NET Framework 3.5 SP1 (nebo verze windows 8+)</span><span class="sxs-lookup"><span data-stu-id="00845-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="00845-129">Jak cílit na standard .NET</span><span class="sxs-lookup"><span data-stu-id="00845-129">How to target the .NET Standard</span></span>

<span data-ttu-id="00845-130">Pokud nejste obeznámeni s .NET Standard, naleznete [v .NET Standard](../../standard/net-standard.md) další informace.</span><span class="sxs-lookup"><span data-stu-id="00845-130">If you're not familiar with .NET Standard, refer to [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="00845-131">V tomto článku je tabulka, která mapuje verze .NET Standard na různé implementace:</span><span class="sxs-lookup"><span data-stu-id="00845-131">In that article, there is a table that maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="00845-132">Tato tabulka znamená pro vytvoření knihovny:</span><span class="sxs-lookup"><span data-stu-id="00845-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="00845-133">Verze rozhraní .NET Standard, kterou vyberete, bude kompromisem mezi přístupem k nejnovějším rozhraním API a možností zaměřit se na další implementace rozhraní .NET a verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="00845-133">The version of .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="00845-134">Rozsah cílových platforem a verzí můžete řídit `netstandardX.X` výběrem `X.X` verze (kde je číslo verze) a`.csproj` `.fsproj`jeho přidáním do souboru projektu ( nebo ).</span><span class="sxs-lookup"><span data-stu-id="00845-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="00845-135">Máte tři primární možnosti při cílení .NET Standard, v závislosti na vašich potřebách.</span><span class="sxs-lookup"><span data-stu-id="00845-135">You have three primary options when targeting .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="00845-136">Můžete použít výchozí verzi standardu .NET, `netstandard1.4`která je dodávána šablonami , která umožňuje přístup k většině rozhraní API ve standardu .NET Standard, zatímco je stále kompatibilní s uwp, rozhraními .NET Framework 4.6.1 a .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="00845-136">You can use the default version of .NET Standard supplied by templates, `netstandard1.4`, which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="00845-137">Nižší nebo vyšší verzi standardu .NET můžete použít úpravou hodnoty v `TargetFramework` uzlu souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="00845-137">You can use a lower or higher version of .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="00845-138">Verze .NET Standard jsou zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="00845-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="00845-139">To znamená, že `netstandard1.0` `netstandard1.1` knihovny běží na platformách a vyšší.</span><span class="sxs-lookup"><span data-stu-id="00845-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="00845-140">Neexistuje však žádná dopředná kompatibilita.</span><span class="sxs-lookup"><span data-stu-id="00845-140">However, there is no forward compatibility.</span></span> <span data-ttu-id="00845-141">Nižší platformy .NET Standard nemohou odkazovat na vyšší.</span><span class="sxs-lookup"><span data-stu-id="00845-141">Lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="00845-142">To znamená, že `netstandard1.0` knihovny `netstandard1.1` nemohou odkazovat na knihovny, které cílí na nebo jsou vyšší.</span><span class="sxs-lookup"><span data-stu-id="00845-142">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="00845-143">Vyberte standardní verzi, která má správnou kombinaci api a podpory platformy pro vaše potřeby.</span><span class="sxs-lookup"><span data-stu-id="00845-143">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="00845-144">Prozatím `netstandard1.4` doporučujeme.</span><span class="sxs-lookup"><span data-stu-id="00845-144">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="00845-145">Pokud chcete cílit na rozhraní .NET Framework verze 4.0 nebo nižší nebo chcete použít rozhraní API dostupné `System.Drawing`v rozhraní .NET Framework, ale ne v rozhraní .NET Standard (například), přečtěte si následující části a zjistěte, jak vícecílit.</span><span class="sxs-lookup"><span data-stu-id="00845-145">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="00845-146">Jak cílit na rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="00845-146">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="00845-147">Tyto pokyny předpokládají, že máte v počítači nainstalovanou architekturu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00845-147">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="00845-148">Naleznete [požadavky získat](#prerequisites) nainstalované závislosti.</span><span class="sxs-lookup"><span data-stu-id="00845-148">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="00845-149">Mějte na paměti, že některé verze rozhraní .NET Framework, které jsou zde používány, již nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="00845-149">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="00845-150">Informace o nepodporovaných verzích naleznete v [nejčastějších dotazech k zásadám životního cyklu podpory rozhraní .NET](https://support.microsoft.com/gp/framework_faq/en-us) Framework.</span><span class="sxs-lookup"><span data-stu-id="00845-150">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="00845-151">Pokud chcete dosáhnout maximálního počtu vývojářů a projektů, použijte rozhraní .NET Framework 4.0 jako cíl směrného plánu.</span><span class="sxs-lookup"><span data-stu-id="00845-151">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="00845-152">Chcete-li cílit na rozhraní .NET Framework, začněte pomocí správného zástupný název cílového rozhraní (TFM), který odpovídá verzi rozhraní .NET Framework, kterou chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="00845-152">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="00845-153">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="00845-153">.NET Framework version</span></span> | <span data-ttu-id="00845-154">Tfm</span><span class="sxs-lookup"><span data-stu-id="00845-154">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="00845-155">.NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="00845-155">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="00845-156">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="00845-156">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="00845-157">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="00845-157">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="00845-158">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="00845-158">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="00845-159">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="00845-159">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="00845-160">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="00845-160">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="00845-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="00845-161">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="00845-162">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="00845-162">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="00845-163">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="00845-163">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="00845-164">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="00845-164">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="00845-165">Rozhraní .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="00845-165">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="00845-166"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="00845-166">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="00845-167">Potom vložíte tento TFM do `TargetFramework` části souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="00845-167">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="00845-168">Například, tady je návod, jak byste napsat knihovnu, která se zaměřuje na rozhraní .NET Framework 4.0:</span><span class="sxs-lookup"><span data-stu-id="00845-168">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="00845-169">A to je vše!</span><span class="sxs-lookup"><span data-stu-id="00845-169">And that's it!</span></span> <span data-ttu-id="00845-170">I když to zkompilován pouze pro rozhraní .NET Framework 4, můžete použít knihovnu na novější verze rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00845-170">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="00845-171">Jak vícecílit</span><span class="sxs-lookup"><span data-stu-id="00845-171">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="00845-172">Následující pokyny předpokládají, že máte v počítači nainstalovanou architekturu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00845-172">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="00845-173">V části [Požadavky](#prerequisites) se dozvíte, které závislosti je třeba nainstalovat a odkud je stáhnout.</span><span class="sxs-lookup"><span data-stu-id="00845-173">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="00845-174">Možná budete muset cílit na starší verze rozhraní .NET Framework, pokud váš projekt podporuje rozhraní .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="00845-174">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="00845-175">V tomto scénáři pokud chcete použít novější rozhraní API a jazykové konstrukce `#if` pro novější cíle, použijte direktivy v kódu.</span><span class="sxs-lookup"><span data-stu-id="00845-175">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="00845-176">Také může být nutné přidat různé balíčky a závislosti pro každou platformu, na kterou cílíte, aby zahrnovala různá řešení API potřebná pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="00845-176">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="00845-177">Řekněme například, že máte knihovnu, která provádí síťové operace přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="00845-177">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="00845-178">Pro standard .NET Standard a rozhraní .NET Framework verze 4.5 nebo vyšší můžete použít třídu `HttpClient` z oboru `System.Net.Http` názvů.</span><span class="sxs-lookup"><span data-stu-id="00845-178">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="00845-179">Dřívější verze rozhraní .NET Framework však nemají `HttpClient` třídu, takže `WebClient` místo toho `System.Net` můžete použít třídu z oboru názvů pro ty.</span><span class="sxs-lookup"><span data-stu-id="00845-179">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="00845-180">Soubor projektu může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="00845-180">Your project file could look like this:</span></span>

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

<span data-ttu-id="00845-181">Zde si všimnete tří hlavních změn:</span><span class="sxs-lookup"><span data-stu-id="00845-181">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="00845-182">Uzel `TargetFramework` byl nahrazen `TargetFrameworks`a tři TFM jsou vyjádřeny uvnitř.</span><span class="sxs-lookup"><span data-stu-id="00845-182">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="00845-183">Existuje `<ItemGroup>` uzel pro `net40` cíl tahání v jednom odkazu rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00845-183">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="00845-184">Existuje `<ItemGroup>` uzel pro `net45` cíl tahání ve dvou odkazech rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00845-184">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="00845-185">Systém sestavení si je vědom následujících `#if` preprocesorových symbolů používaných v direktivách:</span><span class="sxs-lookup"><span data-stu-id="00845-185">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="00845-186">Zde je příklad využití podmíněné kompilace na cíl:</span><span class="sxs-lookup"><span data-stu-id="00845-186">Here is an example making use of conditional compilation per-target:</span></span>

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

<span data-ttu-id="00845-187">Pokud tento projekt `dotnet build`vytváříte s , zaznamenáte `bin/` ve složce tři adresáře:</span><span class="sxs-lookup"><span data-stu-id="00845-187">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="00845-188">Každý z nich `.dll` obsahuje soubory pro každý cíl.</span><span class="sxs-lookup"><span data-stu-id="00845-188">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="00845-189">Jak testovat knihovny na .NET Core</span><span class="sxs-lookup"><span data-stu-id="00845-189">How to test libraries on .NET Core</span></span>

<span data-ttu-id="00845-190">Je důležité, aby bylo možné testovat napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="00845-190">It's important to be able to test across platforms.</span></span> <span data-ttu-id="00845-191">Můžete použít [buď xUnit](https://xunit.github.io/) nebo MSTest po vybalení z krabice.</span><span class="sxs-lookup"><span data-stu-id="00845-191">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="00845-192">Obě jsou dokonale vhodné pro testování částí knihovny na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="00845-192">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="00845-193">Způsob nastavení řešení pomocí testovacích projektů bude záviset na [struktuře vašeho řešení](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="00845-193">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="00845-194">Následující příklad předpokládá, že testovací a zdrojové adresáře žijí ve stejném adresáři nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="00845-194">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="00845-195">To používá některé příkazy [rozhraní příkazového příkazu .NET Core CLI.](../tools/index.md)</span><span class="sxs-lookup"><span data-stu-id="00845-195">This uses some [.NET Core CLI](../tools/index.md) commands.</span></span> <span data-ttu-id="00845-196">Další informace naleznete [v tématu dotnet new](../tools/dotnet-new.md) a [dotnet sln.](../tools/dotnet-sln.md)</span><span class="sxs-lookup"><span data-stu-id="00845-196">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="00845-197">Nastavte řešení.</span><span class="sxs-lookup"><span data-stu-id="00845-197">Set up your solution.</span></span> <span data-ttu-id="00845-198">Můžete tak učinit pomocí následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="00845-198">You can do so with the following commands:</span></span>

   ```dotnetcli
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="00845-199">Tím se vytvoří projekty a propojí je v řešení.</span><span class="sxs-lookup"><span data-stu-id="00845-199">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="00845-200">Adresář pro `SolutionWithSrcAndTest` by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="00845-200">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="00845-201">Přejděte do adresáře testovacího projektu `MyProject.Test` a `MyProject`přidejte odkaz z aplikace .</span><span class="sxs-lookup"><span data-stu-id="00845-201">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```dotnetcli
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="00845-202">Obnovení balíčků a vytváření projektů:</span><span class="sxs-lookup"><span data-stu-id="00845-202">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="00845-203">Ověřte, zda xUnit `dotnet test` běží spuštěním příkazu.</span><span class="sxs-lookup"><span data-stu-id="00845-203">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="00845-204">Pokud jste zvolili použití MSTest, pak konzola MSTest runner by měl spustit místo.</span><span class="sxs-lookup"><span data-stu-id="00845-204">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="00845-205">A to je vše!</span><span class="sxs-lookup"><span data-stu-id="00845-205">And that's it!</span></span> <span data-ttu-id="00845-206">Nyní můžete otestovat knihovnu na všech platformách pomocí nástrojů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="00845-206">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="00845-207">Chcete-li pokračovat v testování nyní, že máte vše nastaveno, testování knihovny je velmi jednoduché:</span><span class="sxs-lookup"><span data-stu-id="00845-207">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="00845-208">Proveďte změny v knihovně.</span><span class="sxs-lookup"><span data-stu-id="00845-208">Make changes to your library.</span></span>
1. <span data-ttu-id="00845-209">Spusťte testy z příkazového řádku `dotnet test` v testovacím adresáři pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="00845-209">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="00845-210">Váš kód bude automaticky znovu `dotnet test` sestaven při vyvolání příkazu.</span><span class="sxs-lookup"><span data-stu-id="00845-210">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="00845-211">Jak používat více projektů</span><span class="sxs-lookup"><span data-stu-id="00845-211">How to use multiple projects</span></span>

<span data-ttu-id="00845-212">Běžnou potřebou větších knihoven je umístění funkcí v různých projektech.</span><span class="sxs-lookup"><span data-stu-id="00845-212">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="00845-213">Představte si, že chcete vytvořit knihovnu, která by mohla být spotřebována v idiomatic C# a F#.</span><span class="sxs-lookup"><span data-stu-id="00845-213">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="00845-214">To by znamenalo, že spotřebitelé vaší knihovny spotřebovávají způsobem, který je přirozený pro C# nebo F#.</span><span class="sxs-lookup"><span data-stu-id="00845-214">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="00845-215">Například v C# můžete využívat knihovnu takto:</span><span class="sxs-lookup"><span data-stu-id="00845-215">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="00845-216">V F# to může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="00845-216">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="00845-217">Scénáře spotřeby, jako je tento, znamenají, že rozhraní API, která jsou přístupná, musí mít jinou strukturu pro C# a F#.</span><span class="sxs-lookup"><span data-stu-id="00845-217">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="00845-218">Běžným přístupem k dosažení tohoto je faktor všechny logiky knihovny do základního projektu, s C# a F# projekty definující vrstvy rozhraní API, které volají do tohoto základního projektu.</span><span class="sxs-lookup"><span data-stu-id="00845-218">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="00845-219">Zbytek oddílu bude používat následující názvy:</span><span class="sxs-lookup"><span data-stu-id="00845-219">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="00845-220">**AwesomeLibrary.Core** - základní projekt, který obsahuje všechny logiky pro knihovnu</span><span class="sxs-lookup"><span data-stu-id="00845-220">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="00845-221">**AwesomeLibrary.CSharp** - projekt s veřejnými rozhraními API určenými ke spotřebě v C #</span><span class="sxs-lookup"><span data-stu-id="00845-221">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="00845-222">**AwesomeLibrary.FSharp** - projekt s veřejnými rozhraními API určenými ke spotřebě v F #</span><span class="sxs-lookup"><span data-stu-id="00845-222">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="00845-223">V terminálu můžete spustit následující příkazy a vytvořit tak stejnou strukturu jako tato příručka:</span><span class="sxs-lookup"><span data-stu-id="00845-223">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```dotnetcli
mkdir AwesomeLibrary && cd AwesomeLibrary
dotnet new sln
mkdir AwesomeLibrary.Core && cd AwesomeLibrary.Core && dotnet new classlib
cd ..
mkdir AwesomeLibrary.CSharp && cd AwesomeLibrary.CSharp && dotnet new classlib
cd ..
mkdir AwesomeLibrary.FSharp && cd AwesomeLibrary.FSharp && dotnet new classlib -lang "F#"
cd ..
dotnet sln add AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
dotnet sln add AwesomeLibrary.CSharp/AwesomeLibrary.CSharp.csproj
dotnet sln add AwesomeLibrary.FSharp/AwesomeLibrary.FSharp.fsproj
```

<span data-ttu-id="00845-224">Tím přidáte tři výše uvedené projekty a soubor řešení, který je propojí dohromady.</span><span class="sxs-lookup"><span data-stu-id="00845-224">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="00845-225">Vytvoření souboru řešení a propojení projektů vám umožní obnovit a vytvářet projekty z nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="00845-225">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="00845-226">Odkazování na projekt-projekt</span><span class="sxs-lookup"><span data-stu-id="00845-226">Project-to-project referencing</span></span>

<span data-ttu-id="00845-227">Nejlepší způsob, jak odkazovat na projekt, je použít rozhraní CLI jádra .NET k přidání odkazu na projekt.</span><span class="sxs-lookup"><span data-stu-id="00845-227">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="00845-228">Z adresářů projektu **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** můžete spustit následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="00845-228">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="00845-229">Soubory projektu pro **AwesomeLibrary.CSharp** a **AwesomeLibrary.FSharp** bude nyní odkazovat **AwesomeLibrary.Core** jako `ProjectReference` cíl.</span><span class="sxs-lookup"><span data-stu-id="00845-229">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="00845-230">Můžete to ověřit kontrolou souborů projektu a zobrazením následujících položek v nich:</span><span class="sxs-lookup"><span data-stu-id="00845-230">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="00845-231">Tuto část můžete přidat do každého souboru projektu ručně, pokud nechcete používat rozhraní CLI jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="00845-231">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="00845-232">Strukturování roztoku</span><span class="sxs-lookup"><span data-stu-id="00845-232">Structuring a solution</span></span>

<span data-ttu-id="00845-233">Dalším důležitým aspektem řešení pro více projektů je vytvoření dobré celkové struktury projektů.</span><span class="sxs-lookup"><span data-stu-id="00845-233">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="00845-234">Můžete uspořádat kód, jak se vám líbí, a tak `dotnet sln add`dlouho, jak propojit `dotnet restore` každý `dotnet build` projekt se souborem řešení s , budete moci spustit a na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="00845-234">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
