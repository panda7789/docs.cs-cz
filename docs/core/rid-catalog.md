---
title: Katalog .NET core Runtime identifikátor (RID)
description: Další informace o identifikátoru Runtime (RID) a použití identifikátorů RID v .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 42707d96744ff765c2ea6ae2298da3e8b27f912f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="3581a-103">.NET core identifikátorů RID katalogu</span><span class="sxs-lookup"><span data-stu-id="3581a-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="3581a-104">Identifikátorů RID je zkratka pro *Runtime identifikátor*.</span><span class="sxs-lookup"><span data-stu-id="3581a-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="3581a-105">Hodnoty identifikátorů RID se používají k identifikaci cílové platformy, kde je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="3581a-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="3581a-106">Balíčky .NET jejich se používá k reprezentování specifické pro platformu prostředky do balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="3581a-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="3581a-107">Následující hodnoty jsou příklady identifikátorů RID: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, nebo `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="3581a-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="3581a-108">Pro balíčky s nativní závislosti identifikátor RID označí, na kterých platformách lze obnovit balíček.</span><span class="sxs-lookup"><span data-stu-id="3581a-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="3581a-109">Jediný identifikátorů RID, může být nastavena v `<RuntimeIdentifier>` element souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="3581a-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="3581a-110">Více identifikátorů RID, může být definováno jako seznam oddělený středníkem v souboru projektu `<RuntimeIdentifiers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3581a-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="3581a-111">Používají se také prostřednictvím `--runtime` možnost s následující [.NET Core rozhraní příkazového řádku](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="3581a-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="3581a-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="3581a-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="3581a-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="3581a-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="3581a-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="3581a-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="3581a-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="3581a-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="3581a-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3581a-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="3581a-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="3581a-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="3581a-118">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="3581a-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="3581a-119">Identifikátory RID, představují konkrétní operační systémy obvykle podívejte se na tento vzor: `[os].[version]-[architecture]-[additional qualifiers]` kde:</span><span class="sxs-lookup"><span data-stu-id="3581a-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="3581a-120">`[os]` je přezdívka systému operační/platformy.</span><span class="sxs-lookup"><span data-stu-id="3581a-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="3581a-121">Například `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="3581a-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="3581a-122">`[version]` verze operačního systému ve formě oddělené tečkou (`.`) číslo verze.</span><span class="sxs-lookup"><span data-stu-id="3581a-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="3581a-123">Například `15.10`.</span><span class="sxs-lookup"><span data-stu-id="3581a-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="3581a-124">Verze **by neměl** být marketingové verze, protože často představují více diskrétní verzí operačního systému s použitím různých útoku na platformě rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3581a-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="3581a-125">`[architecture]` je na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="3581a-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="3581a-126">Příklad: `x86`, `x64`, `arm`, nebo `arm64`.</span><span class="sxs-lookup"><span data-stu-id="3581a-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="3581a-127">`[additional qualifiers]` dál rozlišit různých platformách.</span><span class="sxs-lookup"><span data-stu-id="3581a-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="3581a-128">Příklad: `aot` nebo `corert`.</span><span class="sxs-lookup"><span data-stu-id="3581a-128">For example: `aot` or `corert`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="3581a-129">Graf identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="3581a-129">RID graph</span></span>

<span data-ttu-id="3581a-130">Graf identifikátorů RID nebo modul runtime záložní grafu je seznam identifikátorů RID, které jsou vzájemně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="3581a-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="3581a-131">Identifikátory RID, které jsou definovány v [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) balíčku.</span><span class="sxs-lookup"><span data-stu-id="3581a-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="3581a-132">Můžete zobrazit seznam podporovaných identifikátorů RID a grafu identifikátorů RID ve [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru, který se nachází v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="3581a-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="3581a-133">V tomto souboru, uvidíte, že všechny identifikátory RID, s výjimkou toho, jaké základní obsahovat `"#import"` příkaz.</span><span class="sxs-lookup"><span data-stu-id="3581a-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="3581a-134">Tyto příkazy označují kompatibilní identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="3581a-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="3581a-135">Když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro zadaný modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3581a-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="3581a-136">Pokud není nalezena přesná shoda, NuGet provede zpět grafu dokud nenajde nejbližší kompatibilní systém podle grafu identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="3581a-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="3581a-137">Následující příklad je skutečný položku `osx.10.12-x64` identifikátorů RID:</span><span class="sxs-lookup"><span data-stu-id="3581a-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="3581a-138">Výše uvedené identifikátorů RID Určuje, že `osx.10.12-x64` importuje `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="3581a-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="3581a-139">Ano, když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro `osx.10.12-x64` v balíčku.</span><span class="sxs-lookup"><span data-stu-id="3581a-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="3581a-140">Pokud NuGet nemůže najít konkrétní modul runtime, ho můžete obnovit balíčky, které určují `osx.10.11-x64` moduly runtime, např.</span><span class="sxs-lookup"><span data-stu-id="3581a-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="3581a-141">Následující příklad ukazuje mírně větší identifikátorů RID graf také definovat v *runtime.json* souboru:</span><span class="sxs-lookup"><span data-stu-id="3581a-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

<span data-ttu-id="3581a-142">Všechny identifikátory RID se nakonec mapování zpátky ke kořenové `any` identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="3581a-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="3581a-143">Existují některé aspekty o identifikátorů RID, které je třeba při práci s nimi mějte na paměti:</span><span class="sxs-lookup"><span data-stu-id="3581a-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="3581a-144">Jsou identifikátorů RID **neprůhledného řetězce** a by měl být považován za černé polí.</span><span class="sxs-lookup"><span data-stu-id="3581a-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="3581a-145">Nemáte prostřednictvím kódu programu sestavení identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="3581a-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="3581a-146">Použijte identifikátory RID, které jsou již definováni pro platformu.</span><span class="sxs-lookup"><span data-stu-id="3581a-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="3581a-147">Identifikátory RID musí být konkrétní, takže Nepředpokládejte, že je vše od skutečné hodnoty identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="3581a-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="3581a-148">Pomocí identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="3581a-148">Using RIDs</span></span>

<span data-ttu-id="3581a-149">Abyste mohli použít identifikátorů RID, budete muset vědět, které existují identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="3581a-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="3581a-150">Pro platformu jsou pravidelně přidávány nové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3581a-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="3581a-151">Nejnovější a kompletní verze, najdete v článku [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="3581a-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="3581a-152">.NET core 2.0 SDK zavádí koncepci přenosné identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="3581a-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="3581a-153">Jsou nové hodnoty přidány do grafu, identifikátorů RID, které nejsou vázáno na konkrétní verzi nebo distribuce operačního systému.</span><span class="sxs-lookup"><span data-stu-id="3581a-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="3581a-154">Jsou zvláště užitečné při plánování práce s více distribucích systému Linux.</span><span class="sxs-lookup"><span data-stu-id="3581a-154">They're particularly useful when dealing with multiple Linux distros.</span></span>

<span data-ttu-id="3581a-155">V následujícím seznamu jsou nejběžnější identifikátorů RID, použít pro každý operační systém.</span><span class="sxs-lookup"><span data-stu-id="3581a-155">The following list shows the most common RIDs used for each OS.</span></span> <span data-ttu-id="3581a-156">Ho nezahrnuje `arm` nebo `corert` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3581a-156">It doesn't cover `arm` or `corert` values.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="3581a-157">Windows identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="3581a-157">Windows RIDs</span></span>

- <span data-ttu-id="3581a-158">Přenositelností</span><span class="sxs-lookup"><span data-stu-id="3581a-158">Portable</span></span>
  - `win-x86`
  - `win-x64`
- <span data-ttu-id="3581a-159">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="3581a-159">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="3581a-160">Windows 8 nebo Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="3581a-160">Windows 8 / Windows Server 2012</span></span>
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- <span data-ttu-id="3581a-161">Windows 8.1 nebo Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="3581a-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="3581a-162">Windows 10 nebo Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="3581a-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="3581a-163">V tématu [požadavky pro .NET Core v systému Windows](windows-prerequisites.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="3581a-163">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="3581a-164">Linux identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="3581a-164">Linux RIDs</span></span>

- <span data-ttu-id="3581a-165">Přenositelností</span><span class="sxs-lookup"><span data-stu-id="3581a-165">Portable</span></span>
  - `linux-x64`
- <span data-ttu-id="3581a-166">CentOS</span><span class="sxs-lookup"><span data-stu-id="3581a-166">CentOS</span></span>
  - `centos-x64`
  - `centos.7-x64`
- <span data-ttu-id="3581a-167">Debian</span><span class="sxs-lookup"><span data-stu-id="3581a-167">Debian</span></span>
  - `debian-x64`
  - `debian.8-x64`
- <span data-ttu-id="3581a-168">Fedora</span><span class="sxs-lookup"><span data-stu-id="3581a-168">Fedora</span></span>
  - `fedora-x64`
  - `fedora.24-x64`
  - <span data-ttu-id="3581a-169">`fedora.25-x64` (.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="3581a-169">`fedora.25-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="3581a-170">`fedora.26-x64` (.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="3581a-170">`fedora.26-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="3581a-171">Gentoo (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="3581a-171">Gentoo (.NET Core 2.0 or later versions)</span></span>
  - `gentoo-x64`
- <span data-ttu-id="3581a-172">openSUSE</span><span class="sxs-lookup"><span data-stu-id="3581a-172">openSUSE</span></span>
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- <span data-ttu-id="3581a-173">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="3581a-173">Oracle Linux</span></span>
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- <span data-ttu-id="3581a-174">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="3581a-174">Red Hat Enterprise Linux</span></span>
  - `rhel-x64`
  - <span data-ttu-id="3581a-175">`rhel.6-x64` (.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="3581a-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - <span data-ttu-id="3581a-176">`rhel.7.3-x64` (.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="3581a-176">`rhel.7.3-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="3581a-177">`rhel.7.4-x64` (.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="3581a-177">`rhel.7.4-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="3581a-178">Tizen (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="3581a-178">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
- <span data-ttu-id="3581a-179">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="3581a-179">Ubuntu</span></span>
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- <span data-ttu-id="3581a-180">Ubuntu odvozené konfigurace</span><span class="sxs-lookup"><span data-stu-id="3581a-180">Ubuntu derivatives</span></span>
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - <span data-ttu-id="3581a-181">`linuxmint.18.1-x64` (.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="3581a-181">`linuxmint.18.1-x64` (.NET Core 2.0 or later versions)</span></span>

<span data-ttu-id="3581a-182">V tématu [požadavky pro .NET Core v systému Linux](linux-prerequisites.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="3581a-182">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="3581a-183">systému macOS identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="3581a-183">macOS RIDs</span></span>

<span data-ttu-id="3581a-184">systému macOS RID použijte starší branding "OSX".</span><span class="sxs-lookup"><span data-stu-id="3581a-184">macOS RIDs use the older "OSX" branding.</span></span>

- <span data-ttu-id="3581a-185">`osx-x64` (.NET core 2.0 nebo novější verze, minimální verze je `osx.10.12-x64`)</span><span class="sxs-lookup"><span data-stu-id="3581a-185">`osx-x64` (.NET Core 2.0 or later versions, minimum version is `osx.10.12-x64`)</span></span>
- `osx.10.10-x64`
- `osx.10.11-x64`
- <span data-ttu-id="3581a-186">`osx.10.12-x64` (.NET core 1.1 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="3581a-186">`osx.10.12-x64` (.NET Core 1.1 or later versions)</span></span>
- `osx.10.13-x64`

<span data-ttu-id="3581a-187">V tématu [požadavky pro .NET Core v systému macOS](macos-prerequisites.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="3581a-187">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="android-rids-net-core-20-or-later-versions"></a><span data-ttu-id="3581a-188">Android identifikátorů RID (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="3581a-188">Android RIDs (.NET Core 2.0 or later versions)</span></span>

- `android`
- `android.21`

## <a name="see-also"></a><span data-ttu-id="3581a-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="3581a-189">See also</span></span>

[<span data-ttu-id="3581a-190">ID modulu runtime</span><span class="sxs-lookup"><span data-stu-id="3581a-190">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
