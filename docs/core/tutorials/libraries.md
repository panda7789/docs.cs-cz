---
title: Vývoj knihoven pomocí nástrojů pro různé platformy
description: Naučte se vytvářet knihovny .NET Core pomocí nástrojů .NET Core CLI. Vytvoříte knihovnu, která podporuje více rozhraní.
author: cartermp
ms.date: 05/01/2017
ms.openlocfilehash: 4132113037e6c5ec555d2d1859b8217a1a53d07f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714032"
---
# <a name="develop-libraries-with-cross-platform-tools"></a><span data-ttu-id="d8927-104">Vývoj knihoven pomocí nástrojů pro různé platformy</span><span class="sxs-lookup"><span data-stu-id="d8927-104">Develop libraries with cross-platform tools</span></span>

<span data-ttu-id="d8927-105">Tento článek popisuje, jak psát knihovny pro .NET pomocí nástrojů rozhraní příkazového řádku pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="d8927-105">This article covers how to write libraries for .NET using cross-platform CLI tools.</span></span> <span data-ttu-id="d8927-106">Rozhraní příkazového řádku poskytuje efektivní a nízké prostředí, které funguje v jakémkoli podporovaném operačním systému.</span><span class="sxs-lookup"><span data-stu-id="d8927-106">The CLI provides an efficient and low-level experience that works across any supported OS.</span></span> <span data-ttu-id="d8927-107">Knihovny můžete vytvářet i v aplikaci Visual Studio a pokud je vaše preferované prostředí, [Přečtěte si průvodce sadou Visual Studio](library-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="d8927-107">You can still build libraries with Visual Studio, and if that is your preferred experience [refer to the Visual Studio guide](library-with-visual-studio.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d8927-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8927-108">Prerequisites</span></span>

<span data-ttu-id="d8927-109">Potřebujete na svém počítači nainstalované [.NET Core SDK a CLI](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="d8927-109">You need [the .NET Core SDK and CLI](https://dotnet.microsoft.com/download) installed on your machine.</span></span>

<span data-ttu-id="d8927-110">V části tohoto dokumentu, které se týkají .NET Framework verzí, potřebujete [.NET Framework](https://dotnet.microsoft.com) nainstalovány na počítači s Windows.</span><span class="sxs-lookup"><span data-stu-id="d8927-110">For the sections of this document dealing with .NET Framework versions, you need the [.NET Framework](https://dotnet.microsoft.com) installed on a Windows machine.</span></span>

<span data-ttu-id="d8927-111">Kromě toho, pokud chcete podporovat starší .NET Framework cíle, je nutné nainstalovat sady Target Packs nebo sady Developer Pack ze [stránky archivu stahování v rozhraní .NET](https://dotnet.microsoft.com/download/archives).</span><span class="sxs-lookup"><span data-stu-id="d8927-111">Additionally, if you wish to support older .NET Framework targets, you need to install targeting packs or developer packs from the [.NET download archives page](https://dotnet.microsoft.com/download/archives).</span></span> <span data-ttu-id="d8927-112">Další informace najdete v této tabulce:</span><span class="sxs-lookup"><span data-stu-id="d8927-112">Refer to this table:</span></span>

| <span data-ttu-id="d8927-113">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d8927-113">.NET Framework version</span></span> | <span data-ttu-id="d8927-114">Co stáhnout</span><span class="sxs-lookup"><span data-stu-id="d8927-114">What to download</span></span>                                       |
| ---------------------- | ------------------------------------------------------ |
| <span data-ttu-id="d8927-115">4.6.1</span><span class="sxs-lookup"><span data-stu-id="d8927-115">4.6.1</span></span>                  | <span data-ttu-id="d8927-116">.NET Framework 4.6.1 targeting pack</span><span class="sxs-lookup"><span data-stu-id="d8927-116">.NET Framework 4.6.1 Targeting Pack</span></span>                    |
| <span data-ttu-id="d8927-117">4.6</span><span class="sxs-lookup"><span data-stu-id="d8927-117">4.6</span></span>                    | <span data-ttu-id="d8927-118">Sada targeting pack .NET Framework 4,6</span><span class="sxs-lookup"><span data-stu-id="d8927-118">.NET Framework 4.6 Targeting Pack</span></span>                      |
| <span data-ttu-id="d8927-119">4.5.2</span><span class="sxs-lookup"><span data-stu-id="d8927-119">4.5.2</span></span>                  | <span data-ttu-id="d8927-120">.NET Framework 4.5.2 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="d8927-120">.NET Framework 4.5.2 Developer Pack</span></span>                    |
| <span data-ttu-id="d8927-121">4.5.1</span><span class="sxs-lookup"><span data-stu-id="d8927-121">4.5.1</span></span>                  | <span data-ttu-id="d8927-122">.NET Framework 4.5.1 Developer Pack</span><span class="sxs-lookup"><span data-stu-id="d8927-122">.NET Framework 4.5.1 Developer Pack</span></span>                    |
| <span data-ttu-id="d8927-123">4,5</span><span class="sxs-lookup"><span data-stu-id="d8927-123">4.5</span></span>                    | <span data-ttu-id="d8927-124">Sada Windows SDK pro aplikace pro Windows 8</span><span class="sxs-lookup"><span data-stu-id="d8927-124">Windows Software Development Kit for Windows 8</span></span>         |
| <span data-ttu-id="d8927-125">4.0</span><span class="sxs-lookup"><span data-stu-id="d8927-125">4.0</span></span>                    | <span data-ttu-id="d8927-126">Windows SDK pro Windows 7 a .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="d8927-126">Windows SDK for Windows 7 and .NET Framework 4</span></span>         |
| <span data-ttu-id="d8927-127">2,0, 3,0 a 3,5</span><span class="sxs-lookup"><span data-stu-id="d8927-127">2.0, 3.0, and 3.5</span></span>      | <span data-ttu-id="d8927-128">Runtime .NET Framework 3,5 SP1 (nebo Windows 8 + verze)</span><span class="sxs-lookup"><span data-stu-id="d8927-128">.NET Framework 3.5 SP1 Runtime (or Windows 8+ version)</span></span> |

## <a name="how-to-target-the-net-standard"></a><span data-ttu-id="d8927-129">Jak cílit na .NET Standard</span><span class="sxs-lookup"><span data-stu-id="d8927-129">How to target the .NET Standard</span></span>

<span data-ttu-id="d8927-130">Pokud nejste obeznámeni s .NET Standard, další informace najdete v [.NET Standard](../../standard/net-standard.md) .</span><span class="sxs-lookup"><span data-stu-id="d8927-130">If you're not familiar with .NET Standard, refer to [.NET Standard](../../standard/net-standard.md) to learn more.</span></span>

<span data-ttu-id="d8927-131">V tomto článku je k dispozici tabulka, která mapuje .NET Standard verze na různé implementace:</span><span class="sxs-lookup"><span data-stu-id="d8927-131">In that article, there is a table that maps .NET Standard versions to various implementations:</span></span>

[!INCLUDE [net-standard-table](../../../includes/net-standard-table.md)]

<span data-ttu-id="d8927-132">Zde je uvedeno, co tato tabulka znamená pro účely vytvoření knihovny:</span><span class="sxs-lookup"><span data-stu-id="d8927-132">Here's what this table means for the purposes of creating a library:</span></span>

<span data-ttu-id="d8927-133">Verze .NET Standard, kterou vyberete, bude kompromis mezi přístupem k nejnovějším rozhraním API a možností cílit na více implementací rozhraní .NET a .NET Standard verzí.</span><span class="sxs-lookup"><span data-stu-id="d8927-133">The version of .NET Standard you pick will be a tradeoff between access to the newest APIs and the ability to target more .NET implementations and .NET Standard versions.</span></span> <span data-ttu-id="d8927-134">Rozsah cílových platforem a verzí ovládáte tak, že vybíráte verzi `netstandardX.X` (kde `X.X` je číslo verze) a přidáte ho do souboru projektu (`.csproj` nebo `.fsproj`).</span><span class="sxs-lookup"><span data-stu-id="d8927-134">You control the range of targetable platforms and versions by picking a version of `netstandardX.X` (where `X.X` is a version number) and adding it to your project file (`.csproj` or `.fsproj`).</span></span>

<span data-ttu-id="d8927-135">V závislosti na vašich potřebách máte tři primární možnosti, které cílí na .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="d8927-135">You have three primary options when targeting .NET Standard, depending on your needs.</span></span>

1. <span data-ttu-id="d8927-136">Můžete použít výchozí verzi .NET Standard poskytnutou šablonami, `netstandard1.4`, která vám umožní přístup k většině rozhraní API na .NET Standard, zatímco pořád jsou kompatibilní s UWP, .NET Framework 4.6.1 a .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="d8927-136">You can use the default version of .NET Standard supplied by templates, `netstandard1.4`, which gives you access to most APIs on .NET Standard while still being compatible with UWP, .NET Framework 4.6.1, and .NET Standard 2.0.</span></span>

    ```xml
    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>netstandard1.4</TargetFramework>
      </PropertyGroup>
    </Project>
    ```

2. <span data-ttu-id="d8927-137">Můžete použít nižší nebo vyšší verzi .NET Standard úpravou hodnoty v uzlu `TargetFramework` souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d8927-137">You can use a lower or higher version of .NET Standard by modifying the value in the `TargetFramework` node of your project file.</span></span>

    <span data-ttu-id="d8927-138">Verze .NET Standard jsou zpětně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="d8927-138">.NET Standard versions are backward compatible.</span></span> <span data-ttu-id="d8927-139">To znamená, že `netstandard1.0` knihoven běží na `netstandard1.1`ch platformách a vyšších.</span><span class="sxs-lookup"><span data-stu-id="d8927-139">That means that `netstandard1.0` libraries run on `netstandard1.1` platforms and higher.</span></span> <span data-ttu-id="d8927-140">Nejedná se však o dopředné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="d8927-140">However, there is no forward compatibility.</span></span> <span data-ttu-id="d8927-141">Nižší .NET Standard platformy nemůžou odkazovat na vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="d8927-141">Lower .NET Standard platforms cannot reference higher ones.</span></span> <span data-ttu-id="d8927-142">To znamená, že knihovny `netstandard1.0` nemohou odkazovat na knihovny cílené na `netstandard1.1` nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="d8927-142">This means that `netstandard1.0` libraries cannot reference libraries targeting `netstandard1.1` or higher.</span></span> <span data-ttu-id="d8927-143">Vyberte standardní verzi, která má správnou kombinaci rozhraní API a podpory platforem podle vašich potřeb.</span><span class="sxs-lookup"><span data-stu-id="d8927-143">Select the Standard version that has the right mix of APIs and platform support for your needs.</span></span> <span data-ttu-id="d8927-144">Pro teď doporučujeme `netstandard1.4`.</span><span class="sxs-lookup"><span data-stu-id="d8927-144">We recommend `netstandard1.4` for now.</span></span>

3. <span data-ttu-id="d8927-145">Pokud chcete cílit .NET Framework verze 4,0 nebo nižší nebo chcete použít rozhraní API dostupné v .NET Framework, ale ne v .NET Standard (například `System.Drawing`), přečtěte si následující oddíly a Naučte se, jak cílit.</span><span class="sxs-lookup"><span data-stu-id="d8927-145">If you want to target .NET Framework versions 4.0 or below, or you wish to use an API available in .NET Framework but not in .NET Standard (for example, `System.Drawing`), read the following sections and learn how to multitarget.</span></span>

## <a name="how-to-target-net-framework"></a><span data-ttu-id="d8927-146">Jak cílit na .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d8927-146">How to target .NET Framework</span></span>

> [!NOTE]
> <span data-ttu-id="d8927-147">V těchto pokynech se předpokládá, že máte na svém počítači nainstalovanou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8927-147">These instructions assume you have .NET Framework installed on your machine.</span></span> <span data-ttu-id="d8927-148">Pokud chcete získat nainstalované závislosti, přečtěte si [požadavky](#prerequisites) .</span><span class="sxs-lookup"><span data-stu-id="d8927-148">Refer to the [Prerequisites](#prerequisites) to get dependencies installed.</span></span>

<span data-ttu-id="d8927-149">Mějte na paměti, že některé z .NET Framework používané verze už nejsou podporované.</span><span class="sxs-lookup"><span data-stu-id="d8927-149">Keep in mind that some of the .NET Framework versions used here are no longer supported.</span></span> <span data-ttu-id="d8927-150">Přečtěte si [Nejčastější dotazy k zásadám životního cyklu podpory .NET Framework](https://support.microsoft.com/gp/framework_faq/en-us) pro nepodporované verze.</span><span class="sxs-lookup"><span data-stu-id="d8927-150">Refer to the [.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us) about unsupported versions.</span></span>

<span data-ttu-id="d8927-151">Pokud chcete dosáhnout maximálního počtu vývojářů a projektů, použijte jako cíl standardních hodnot .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="d8927-151">If you want to reach the maximum number of developers and projects, use .NET Framework 4.0 as your baseline target.</span></span> <span data-ttu-id="d8927-152">Chcete-li cílit na .NET Framework, začněte pomocí správného monikeru cílového rozhraní .NET Framework (TFM), který odpovídá .NET Framework verzi, kterou chcete podporovat.</span><span class="sxs-lookup"><span data-stu-id="d8927-152">To target .NET Framework, begin by using the correct Target Framework Moniker (TFM) that corresponds to the .NET Framework version you wish to support.</span></span>

| <span data-ttu-id="d8927-153">Verze rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d8927-153">.NET Framework version</span></span> | <span data-ttu-id="d8927-154">TFM</span><span class="sxs-lookup"><span data-stu-id="d8927-154">TFM</span></span>      |
| ---------------------- | -------- |
| <span data-ttu-id="d8927-155">.NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="d8927-155">.NET Framework 2.0</span></span>     | `net20`  |
| <span data-ttu-id="d8927-156">.NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="d8927-156">.NET Framework 3.0</span></span>     | `net30`  |
| <span data-ttu-id="d8927-157">.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="d8927-157">.NET Framework 3.5</span></span>     | `net35`  |
| <span data-ttu-id="d8927-158">.NET Framework 4.0</span><span class="sxs-lookup"><span data-stu-id="d8927-158">.NET Framework 4.0</span></span>     | `net40`  |
| <span data-ttu-id="d8927-159">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="d8927-159">.NET Framework 4.5</span></span>     | `net45`  |
| <span data-ttu-id="d8927-160">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="d8927-160">.NET Framework 4.5.1</span></span>   | `net451` |
| <span data-ttu-id="d8927-161">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="d8927-161">.NET Framework 4.5.2</span></span>   | `net452` |
| <span data-ttu-id="d8927-162">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="d8927-162">.NET Framework 4.6</span></span>     | `net46`  |
| <span data-ttu-id="d8927-163">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="d8927-163">.NET Framework 4.6.1</span></span>   | `net461` |
| <span data-ttu-id="d8927-164">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="d8927-164">.NET Framework 4.6.2</span></span>   | `net462` |
| <span data-ttu-id="d8927-165">Rozhraní .NET framework 4.7</span><span class="sxs-lookup"><span data-stu-id="d8927-165">.NET Framework 4.7</span></span>     | `net47`  |
| <span data-ttu-id="d8927-166">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="d8927-166">.NET Framework 4.8</span></span>     | `net48`  |

<span data-ttu-id="d8927-167">Pak tento TFM vložíte do oddílu `TargetFramework` souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="d8927-167">You then insert this TFM into the `TargetFramework` section of your project file.</span></span> <span data-ttu-id="d8927-168">Tady je příklad, jak byste měli napsat knihovnu, která cílí na .NET Framework 4,0:</span><span class="sxs-lookup"><span data-stu-id="d8927-168">For example, here's how you would write a library that targets .NET Framework 4.0:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net40</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="d8927-169">A je to!</span><span class="sxs-lookup"><span data-stu-id="d8927-169">And that's it!</span></span> <span data-ttu-id="d8927-170">I když se tato kompilace kompiluje jenom pro .NET Framework 4, můžete použít knihovnu v novějších verzích .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8927-170">Although this compiled only for .NET Framework 4, you can use the library on newer versions of .NET Framework.</span></span>

## <a name="how-to-multitarget"></a><span data-ttu-id="d8927-171">Jak cílit</span><span class="sxs-lookup"><span data-stu-id="d8927-171">How to multitarget</span></span>

> [!NOTE]
> <span data-ttu-id="d8927-172">V následujících pokynech se předpokládá, že máte na svém počítači nainstalovanou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8927-172">The following instructions assume you have the .NET Framework installed on your machine.</span></span> <span data-ttu-id="d8927-173">Informace o závislostech, které potřebujete nainstalovat a odkud je stáhnout z nástroje, najdete v části [požadavky](#prerequisites) .</span><span class="sxs-lookup"><span data-stu-id="d8927-173">Refer to the [Prerequisites](#prerequisites) section to learn which dependencies you need to install and where to download them from.</span></span>

<span data-ttu-id="d8927-174">Je možné, že budete muset cílit na starší verze .NET Framework, pokud projekt podporuje .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d8927-174">You may need to target older versions of the .NET Framework when your project supports both the .NET Framework and .NET Core.</span></span> <span data-ttu-id="d8927-175">Pokud v tomto scénáři chcete pro novější cíle používat novější rozhraní API a jazykové konstrukce, použijte ve svém kódu direktivy `#if`.</span><span class="sxs-lookup"><span data-stu-id="d8927-175">In this scenario, if you want to use newer APIs and language constructs for the newer targets, use `#if` directives in your code.</span></span> <span data-ttu-id="d8927-176">Také může být nutné přidat různé balíčky a závislosti pro každou platformu, na kterou cílíte, aby zahrnovala různá rozhraní API potřebná pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="d8927-176">You also might need to add different packages and dependencies for each platform you're targeting to include the different APIs needed for each case.</span></span>

<span data-ttu-id="d8927-177">Řekněme například, že máte knihovnu, která provádí síťové operace přes HTTP.</span><span class="sxs-lookup"><span data-stu-id="d8927-177">For example, let's say you have a library that performs networking operations over HTTP.</span></span> <span data-ttu-id="d8927-178">Pro .NET Standard a .NET Framework verze 4,5 nebo vyšší lze použít třídu `HttpClient` z oboru názvů `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="d8927-178">For .NET Standard and the .NET Framework versions 4.5 or higher, you can use the `HttpClient` class from the `System.Net.Http` namespace.</span></span> <span data-ttu-id="d8927-179">Starší verze .NET Framework však nemají `HttpClient` třídu, takže můžete místo toho použít třídu `WebClient` z oboru názvů `System.Net`.</span><span class="sxs-lookup"><span data-stu-id="d8927-179">However, earlier versions of the .NET Framework don't have the `HttpClient` class, so you could use the `WebClient` class from the `System.Net` namespace for those instead.</span></span>

<span data-ttu-id="d8927-180">Váš soubor projektu by mohl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="d8927-180">Your project file could look like this:</span></span>

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

<span data-ttu-id="d8927-181">Tady si všimnete tří hlavních změn:</span><span class="sxs-lookup"><span data-stu-id="d8927-181">You'll notice three major changes here:</span></span>

1. <span data-ttu-id="d8927-182">Uzel `TargetFramework` byl nahrazen `TargetFrameworks`a tři TFM jsou vyjádřeny uvnitř.</span><span class="sxs-lookup"><span data-stu-id="d8927-182">The `TargetFramework` node has been replaced by `TargetFrameworks`, and three TFMs are expressed inside.</span></span>
1. <span data-ttu-id="d8927-183">V jednom .NET Framework odkazu je `<ItemGroup>` uzel pro `net40` cíle.</span><span class="sxs-lookup"><span data-stu-id="d8927-183">There is an `<ItemGroup>` node for the `net40` target pulling in one .NET Framework reference.</span></span>
1. <span data-ttu-id="d8927-184">Existuje `<ItemGroup>` uzel pro `net45` cílení na přijetí ve dvou .NET Framework odkazech.</span><span class="sxs-lookup"><span data-stu-id="d8927-184">There is an `<ItemGroup>` node for the `net45` target pulling in two .NET Framework references.</span></span>

<span data-ttu-id="d8927-185">Systém sestavení ví o následujících symbolech preprocesoru, které se používají v direktivách `#if`:</span><span class="sxs-lookup"><span data-stu-id="d8927-185">The build system is aware of the following preprocessor symbols used in `#if` directives:</span></span>

[!INCLUDE [Preprocessor symbols](../../../includes/preprocessor-symbols.md)]

<span data-ttu-id="d8927-186">Tady je příklad, který využívá Podmíněná kompilace na cíl:</span><span class="sxs-lookup"><span data-stu-id="d8927-186">Here is an example making use of conditional compilation per-target:</span></span>

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

<span data-ttu-id="d8927-187">Pokud tento projekt sestavíte pomocí `dotnet build`, všimnete si tří adresářů v rámci složky `bin/`:</span><span class="sxs-lookup"><span data-stu-id="d8927-187">If you build this project with `dotnet build`, you'll notice three directories under the `bin/` folder:</span></span>

```
net40/
net45/
netstandard1.4/
```

<span data-ttu-id="d8927-188">Každá z nich obsahuje soubory `.dll` pro každý cíl.</span><span class="sxs-lookup"><span data-stu-id="d8927-188">Each of these contain the `.dll` files for each target.</span></span>

## <a name="how-to-test-libraries-on-net-core"></a><span data-ttu-id="d8927-189">Postup testování knihoven v .NET Core</span><span class="sxs-lookup"><span data-stu-id="d8927-189">How to test libraries on .NET Core</span></span>

<span data-ttu-id="d8927-190">Je důležité, abyste mohli testovat napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="d8927-190">It's important to be able to test across platforms.</span></span> <span data-ttu-id="d8927-191">V poli můžete použít buď [xUnit](https://xunit.github.io/) nebo MSTest.</span><span class="sxs-lookup"><span data-stu-id="d8927-191">You can use either [xUnit](https://xunit.github.io/) or MSTest out of the box.</span></span> <span data-ttu-id="d8927-192">Obě jsou dokonale vhodné pro testování částí knihovny v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d8927-192">Both are perfectly suitable for unit testing your library on .NET Core.</span></span> <span data-ttu-id="d8927-193">Způsob nastavení řešení pomocí testovacích projektů bude záviset na [struktuře řešení](#structuring-a-solution).</span><span class="sxs-lookup"><span data-stu-id="d8927-193">How you set up your solution with test projects will depend on the [structure of your solution](#structuring-a-solution).</span></span> <span data-ttu-id="d8927-194">Následující příklad předpokládá, že testovací a zdrojové adresáře jsou ve stejném adresáři nejvyšší úrovně v provozu.</span><span class="sxs-lookup"><span data-stu-id="d8927-194">The following example assumes that the test and source directories live in the same top-level directory.</span></span>

> [!NOTE]
> <span data-ttu-id="d8927-195">Používá se k tomu několik [příkazů .NET Core CLI](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="d8927-195">This uses some [.NET Core CLI commands](../tools/index.md).</span></span> <span data-ttu-id="d8927-196">Další informace naleznete v tématu [dotnet New](../tools/dotnet-new.md) a [dotnet sln](../tools/dotnet-sln.md) .</span><span class="sxs-lookup"><span data-stu-id="d8927-196">See [dotnet new](../tools/dotnet-new.md) and [dotnet sln](../tools/dotnet-sln.md) for more information.</span></span>

1. <span data-ttu-id="d8927-197">Nastavte své řešení.</span><span class="sxs-lookup"><span data-stu-id="d8927-197">Set up your solution.</span></span> <span data-ttu-id="d8927-198">Můžete to udělat pomocí následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="d8927-198">You can do so with the following commands:</span></span>

   ```bash
   mkdir SolutionWithSrcAndTest
   cd SolutionWithSrcAndTest
   dotnet new sln
   dotnet new classlib -o MyProject
   dotnet new xunit -o MyProject.Test
   dotnet sln add MyProject/MyProject.csproj
   dotnet sln add MyProject.Test/MyProject.Test.csproj
   ```

   <span data-ttu-id="d8927-199">Tím se vytvoří projekty a spojí se dohromady v řešení.</span><span class="sxs-lookup"><span data-stu-id="d8927-199">This will create projects and link them together in a solution.</span></span> <span data-ttu-id="d8927-200">Váš adresář pro `SolutionWithSrcAndTest` by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="d8927-200">Your directory for `SolutionWithSrcAndTest` should look like this:</span></span>

   ```
   /SolutionWithSrcAndTest
   |__SolutionWithSrcAndTest.sln
   |__MyProject/
   |__MyProject.Test/
   ```

1. <span data-ttu-id="d8927-201">Přejděte do adresáře testovacího projektu a přidejte odkaz na `MyProject.Test` z `MyProject`.</span><span class="sxs-lookup"><span data-stu-id="d8927-201">Navigate to the test project's directory and add a reference to `MyProject.Test` from `MyProject`.</span></span>

   ```bash
   cd MyProject.Test
   dotnet add reference ../MyProject/MyProject.csproj
   ```

1. <span data-ttu-id="d8927-202">Obnovit balíčky a sestavit projekty:</span><span class="sxs-lookup"><span data-stu-id="d8927-202">Restore packages and build projects:</span></span>

   ```dotnetcli
   dotnet restore
   dotnet build
   ```

   [!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

1. <span data-ttu-id="d8927-203">Spuštěním příkazu `dotnet test` ověřte, že xUnit běží.</span><span class="sxs-lookup"><span data-stu-id="d8927-203">Verify that xUnit runs by executing the `dotnet test` command.</span></span> <span data-ttu-id="d8927-204">Pokud jste se rozhodli používat MSTest, měl by se místo toho spustit spouštěč konzoly MSTest.</span><span class="sxs-lookup"><span data-stu-id="d8927-204">If you chose to use MSTest, then the MSTest console runner should run instead.</span></span>

<span data-ttu-id="d8927-205">A je to!</span><span class="sxs-lookup"><span data-stu-id="d8927-205">And that's it!</span></span> <span data-ttu-id="d8927-206">Pomocí nástrojů příkazového řádku teď můžete svoji knihovnu testovat napříč všemi platformami.</span><span class="sxs-lookup"><span data-stu-id="d8927-206">You can now test your library across all platforms using command-line tools.</span></span> <span data-ttu-id="d8927-207">Pokud chcete pokračovat v testování, když máte všechno nastavené, testování knihovny je velmi jednoduché:</span><span class="sxs-lookup"><span data-stu-id="d8927-207">To continue testing now that you have everything set up, testing your library is very simple:</span></span>

1. <span data-ttu-id="d8927-208">Proveďte změny v knihovně.</span><span class="sxs-lookup"><span data-stu-id="d8927-208">Make changes to your library.</span></span>
1. <span data-ttu-id="d8927-209">Spusťte testy z příkazového řádku v adresáři testu s příkazem `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="d8927-209">Run tests from the command line, in your test directory, with `dotnet test` command.</span></span>

<span data-ttu-id="d8927-210">Váš kód bude automaticky znovu vytvořen při vyvolání příkazu `dotnet test`.</span><span class="sxs-lookup"><span data-stu-id="d8927-210">Your code will be automatically rebuilt when you invoke `dotnet test` command.</span></span>

## <a name="how-to-use-multiple-projects"></a><span data-ttu-id="d8927-211">Používání více projektů</span><span class="sxs-lookup"><span data-stu-id="d8927-211">How to use multiple projects</span></span>

<span data-ttu-id="d8927-212">Běžnou potřebou pro větší knihovny je umístit funkci do různých projektů.</span><span class="sxs-lookup"><span data-stu-id="d8927-212">A common need for larger libraries is to place functionality in different projects.</span></span>

<span data-ttu-id="d8927-213">Představte si, že chcete vytvořit knihovnu, která by mohla C# být F#spotřebována v idiomatickou a.</span><span class="sxs-lookup"><span data-stu-id="d8927-213">Imagine you want to build a library that could be consumed in idiomatic C# and F#.</span></span> <span data-ttu-id="d8927-214">To by znamenalo, že uživatelé vaší knihovny ji spotřebují způsobem, který je C# přirozený F#nebo.</span><span class="sxs-lookup"><span data-stu-id="d8927-214">That would mean that consumers of your library consume it in ways that are natural to C# or F#.</span></span> <span data-ttu-id="d8927-215">Například C# můžete použít knihovnu podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="d8927-215">For example, in C# you might consume the library like this:</span></span>

```csharp
using AwesomeLibrary.CSharp;

public Task DoThings(Data data)
{
    var convertResult = await AwesomeLibrary.ConvertAsync(data);
    var result = AwesomeLibrary.Process(convertResult);
    // do something with result
}
```

<span data-ttu-id="d8927-216">V F#nástroji může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="d8927-216">In F#, it might look like this:</span></span>

```fsharp
open AwesomeLibrary.FSharp

let doWork data = async {
    let! result = AwesomeLibrary.AsyncConvert data // Uses an F# async function rather than C# async method
    // do something with result
}
```

<span data-ttu-id="d8927-217">Scénáře spotřeby, jako je to znamená, že rozhraní API, ke kterým se přistupovalo, musí mít jinou strukturu pro C# a F#.</span><span class="sxs-lookup"><span data-stu-id="d8927-217">Consumption scenarios like this mean that the APIs being accessed have to have a different structure for C# and F#.</span></span>  <span data-ttu-id="d8927-218">Běžným přístupem k tomu je faktorovat všechny logiky knihovny do základního projektu, s C# a F# projekty definující vrstvy rozhraní API, které volají do tohoto základního projektu.</span><span class="sxs-lookup"><span data-stu-id="d8927-218">A common approach to accomplishing this is to factor all of the logic of a library into a core project, with C# and F# projects defining the API layers that call into that core project.</span></span>  <span data-ttu-id="d8927-219">Zbytek oddílu bude používat následující názvy:</span><span class="sxs-lookup"><span data-stu-id="d8927-219">The rest of the section will use the following names:</span></span>

* <span data-ttu-id="d8927-220">**AwesomeLibrary. Core** – projekt jádra, který obsahuje všechny logiky pro knihovnu</span><span class="sxs-lookup"><span data-stu-id="d8927-220">**AwesomeLibrary.Core** - A core project that contains all logic for the library</span></span>
* <span data-ttu-id="d8927-221">**AwesomeLibrary. CSharp** – projekt s veřejnými rozhraními API určenými pro využití vC#</span><span class="sxs-lookup"><span data-stu-id="d8927-221">**AwesomeLibrary.CSharp** - A project with public APIs intended for consumption in C#</span></span>
* <span data-ttu-id="d8927-222">**AwesomeLibrary. FSharp** – projekt s veřejnými rozhraními API určenými pro využití vF#</span><span class="sxs-lookup"><span data-stu-id="d8927-222">**AwesomeLibrary.FSharp** - A project with public APIs intended for consumption in F#</span></span>

<span data-ttu-id="d8927-223">V terminálu můžete spustit následující příkazy, které tvoří stejnou strukturu jako tato příručka:</span><span class="sxs-lookup"><span data-stu-id="d8927-223">You can run the following commands in your terminal to produce the same structure as this guide:</span></span>

```console
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

<span data-ttu-id="d8927-224">Tím se přidají tři projekty výše a soubor řešení, který je propojuje dohromady.</span><span class="sxs-lookup"><span data-stu-id="d8927-224">This will add the three projects above and a solution file that links them together.</span></span> <span data-ttu-id="d8927-225">Vytvoření souboru řešení a propojení projektů vám umožní obnovit a sestavit projekty z nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="d8927-225">Creating the solution file and linking projects will allow you to restore and build projects from a top level.</span></span>

### <a name="project-to-project-referencing"></a><span data-ttu-id="d8927-226">Odkazování na projekt na projekt</span><span class="sxs-lookup"><span data-stu-id="d8927-226">Project-to-project referencing</span></span>

<span data-ttu-id="d8927-227">Nejlepším způsobem, jak odkazovat na projekt, je použít .NET Core CLI pro přidání odkazu na projekt.</span><span class="sxs-lookup"><span data-stu-id="d8927-227">The best way to reference a project is to use the .NET Core CLI to add a project reference.</span></span> <span data-ttu-id="d8927-228">Z adresářů projektu **AwesomeLibrary. CSharp** a **AwesomeLibrary. FSharp** můžete spustit následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d8927-228">From the **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** project directories, you can run the following command:</span></span>

```dotnetcli
dotnet add reference ../AwesomeLibrary.Core/AwesomeLibrary.Core.csproj
```

<span data-ttu-id="d8927-229">Soubory projektu pro **AwesomeLibrary. CSharp** a **AwesomeLibrary. FSharp** nyní budou odkazovat na **AwesomeLibrary. Core** jako na cíl `ProjectReference`.</span><span class="sxs-lookup"><span data-stu-id="d8927-229">The project files for both **AwesomeLibrary.CSharp** and **AwesomeLibrary.FSharp** will now reference **AwesomeLibrary.Core** as a `ProjectReference` target.</span></span>  <span data-ttu-id="d8927-230">To můžete ověřit kontrolou souborů projektu a zobrazením následujících v těchto souborech:</span><span class="sxs-lookup"><span data-stu-id="d8927-230">You can verify this by inspecting the project files and seeing the following in them:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\AwesomeLibrary.Core\AwesomeLibrary.Core.csproj" />
</ItemGroup>
```

<span data-ttu-id="d8927-231">Tuto část můžete přidat do každého souboru projektu ručně, pokud nechcete používat .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="d8927-231">You can add this section to each project file manually if you prefer not to use the .NET Core CLI.</span></span>

### <a name="structuring-a-solution"></a><span data-ttu-id="d8927-232">Strukturování řešení</span><span class="sxs-lookup"><span data-stu-id="d8927-232">Structuring a solution</span></span>

<span data-ttu-id="d8927-233">Dalším důležitým aspektem řešení pro více projektů je vytvoření dobré celkové struktury projektu.</span><span class="sxs-lookup"><span data-stu-id="d8927-233">Another important aspect of multi-project solutions is establishing a good overall project structure.</span></span> <span data-ttu-id="d8927-234">Můžete organizovat kód, a Pokud propojíte každý projekt se souborem řešení pomocí `dotnet sln add`, bude možné spustit `dotnet restore` a `dotnet build` na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="d8927-234">You can organize code however you like, and as long as you link each project to your solution file with `dotnet sln add`, you will be able to run `dotnet restore` and `dotnet build` at the solution level.</span></span>
