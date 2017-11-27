---
title: "Katalog .NET core Runtime identifikátor (RID)"
description: "Další informace o identifikátoru Runtime (RID) a použití identifikátorů RID v .NET Core."
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 067f9cfc283a14b7ea59a7454b7f593ce6eb5806
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2017
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="349db-103">.NET core identifikátorů RID katalogu</span><span class="sxs-lookup"><span data-stu-id="349db-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="349db-104">Identifikátorů RID je zkratka pro *Runtime identifikátor*.</span><span class="sxs-lookup"><span data-stu-id="349db-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="349db-105">Hodnoty identifikátorů RID se používají k identifikaci cílové platformy, kde je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="349db-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="349db-106">Balíčky .NET jejich se používá k reprezentování specifické pro platformu prostředky do balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="349db-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="349db-107">Následující hodnoty jsou příklady identifikátorů RID: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, nebo `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="349db-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="349db-108">Pro balíčky s nativní závislosti identifikátor RID označí, na kterých platformách lze obnovit balíček.</span><span class="sxs-lookup"><span data-stu-id="349db-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="349db-109">Identifikátory RID, může být nastavena v `<RuntimeIdentifier>` element souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="349db-109">RIDs can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="349db-110">Používají se také prostřednictvím `--runtime` možnost s následující [.NET Core rozhraní příkazového řádku](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="349db-110">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="349db-111">sestavení DotNet.</span><span class="sxs-lookup"><span data-stu-id="349db-111">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="349db-112">Vyčištění DotNet.</span><span class="sxs-lookup"><span data-stu-id="349db-112">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="349db-113">pack DotNet.</span><span class="sxs-lookup"><span data-stu-id="349db-113">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="349db-114">publikování DotNet.</span><span class="sxs-lookup"><span data-stu-id="349db-114">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="349db-115">obnovení DotNet.</span><span class="sxs-lookup"><span data-stu-id="349db-115">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="349db-116">Spustit DotNet.</span><span class="sxs-lookup"><span data-stu-id="349db-116">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="349db-117">úložiště DotNet.</span><span class="sxs-lookup"><span data-stu-id="349db-117">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="349db-118">Identifikátory RID, představují konkrétní operační systémy obvykle podívejte se na tento vzor: `[os].[version]-[architecture]-[additional qualifiers]` kde:</span><span class="sxs-lookup"><span data-stu-id="349db-118">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="349db-119">`[os]`je přezdívka systému operační/platformy.</span><span class="sxs-lookup"><span data-stu-id="349db-119">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="349db-120">Například `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="349db-120">For example, `ubuntu`.</span></span>

- <span data-ttu-id="349db-121">`[version]`verze operačního systému ve formě oddělené tečkou (`.`) číslo verze.</span><span class="sxs-lookup"><span data-stu-id="349db-121">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="349db-122">Například `15.10`.</span><span class="sxs-lookup"><span data-stu-id="349db-122">For example, `15.10`.</span></span>

  - <span data-ttu-id="349db-123">Verze **by neměl** být marketingové verze, protože často představují více diskrétní verzí operačního systému s použitím různých útoku na platformě rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="349db-123">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="349db-124">`[architecture]`je na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="349db-124">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="349db-125">Příklad: `x86`, `x64`, `arm`, nebo `arm64`.</span><span class="sxs-lookup"><span data-stu-id="349db-125">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="349db-126">`[additional qualifiers]`dál rozlišit různých platformách.</span><span class="sxs-lookup"><span data-stu-id="349db-126">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="349db-127">Příklad: `aot` nebo `corert`.</span><span class="sxs-lookup"><span data-stu-id="349db-127">For example: `aot` or `corert`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="349db-128">Graf identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="349db-128">RID graph</span></span>

<span data-ttu-id="349db-129">Graf identifikátorů RID nebo modul runtime záložní grafu je seznam identifikátorů RID, které jsou vzájemně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="349db-129">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="349db-130">Identifikátory RID, které jsou definovány v [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) balíčku.</span><span class="sxs-lookup"><span data-stu-id="349db-130">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="349db-131">Můžete zobrazit seznam podporovaných identifikátorů RID a grafu identifikátorů RID ve [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru, který se nachází v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="349db-131">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="349db-132">V tomto souboru, uvidíte, že všechny identifikátory RID, s výjimkou toho, jaké základní obsahovat `"#import"` příkaz.</span><span class="sxs-lookup"><span data-stu-id="349db-132">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="349db-133">Tyto příkazy označují kompatibilní identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="349db-133">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="349db-134">Když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro zadaný modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="349db-134">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="349db-135">Pokud není nalezena přesná shoda, NuGet provede zpět grafu dokud nenajde nejbližší kompatibilní systém podle grafu identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="349db-135">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="349db-136">Následující příklad je skutečný položku `osx.10.12-x64` identifikátorů RID:</span><span class="sxs-lookup"><span data-stu-id="349db-136">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="349db-137">Výše uvedené identifikátorů RID Určuje, že `osx.10.12-x64` importuje `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="349db-137">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="349db-138">Ano, když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro `osx.10.12-x64` v balíčku.</span><span class="sxs-lookup"><span data-stu-id="349db-138">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="349db-139">Pokud NuGet nemůže najít konkrétní modul runtime, ho můžete obnovit balíčky, které určují `osx.10.11-x64` moduly runtime, např.</span><span class="sxs-lookup"><span data-stu-id="349db-139">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="349db-140">Následující příklad ukazuje mírně větší identifikátorů RID graf také definovat v *runtime.json* souboru:</span><span class="sxs-lookup"><span data-stu-id="349db-140">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="349db-141">Všechny identifikátory RID se nakonec mapování zpátky ke kořenové `any` identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="349db-141">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="349db-142">Existují některé aspekty o identifikátorů RID, které je třeba při práci s nimi mějte na paměti:</span><span class="sxs-lookup"><span data-stu-id="349db-142">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="349db-143">Jsou identifikátorů RID **neprůhledného řetězce** a by měl být považován za černé polí.</span><span class="sxs-lookup"><span data-stu-id="349db-143">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="349db-144">Nemáte prostřednictvím kódu programu sestavení identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="349db-144">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="349db-145">Použijte identifikátory RID, které jsou již definováni pro platformu.</span><span class="sxs-lookup"><span data-stu-id="349db-145">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="349db-146">Identifikátory RID musí být konkrétní, takže Nepředpokládejte, že je vše od skutečné hodnoty identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="349db-146">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="349db-147">Pomocí identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="349db-147">Using RIDs</span></span>

<span data-ttu-id="349db-148">Abyste mohli použít identifikátorů RID, budete muset vědět, které existují identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="349db-148">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="349db-149">Pro platformu jsou pravidelně přidávány nové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="349db-149">New values are added regularly to the platform.</span></span>
<span data-ttu-id="349db-150">Nejnovější a kompletní verze, najdete v článku [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="349db-150">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="349db-151">.NET core 2.0 SDK zavádí koncepci přenosné identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="349db-151">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="349db-152">Jsou nové hodnoty přidány do grafu, identifikátorů RID, které nejsou vázáno na konkrétní verzi nebo distribuce operačního systému.</span><span class="sxs-lookup"><span data-stu-id="349db-152">They are new values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="349db-153">Jsou zvláště užitečné při plánování práce s více distribucích systému Linux.</span><span class="sxs-lookup"><span data-stu-id="349db-153">They're particularly useful when dealing with multiple Linux distros.</span></span>

<span data-ttu-id="349db-154">V následujícím seznamu jsou nejběžnější identifikátorů RID, použít pro každý operační systém.</span><span class="sxs-lookup"><span data-stu-id="349db-154">The following list shows the most common RIDs used for each OS.</span></span> <span data-ttu-id="349db-155">Ho nezahrnuje `arm` nebo `corert` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="349db-155">It doesn't cover `arm` or `corert` values.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="349db-156">Windows identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="349db-156">Windows RIDs</span></span>

- <span data-ttu-id="349db-157">Přenositelností</span><span class="sxs-lookup"><span data-stu-id="349db-157">Portable</span></span>
  - `win-x86`
  - `win-x64`
- <span data-ttu-id="349db-158">Windows 7 nebo Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="349db-158">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="349db-159">Windows 8 nebo Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="349db-159">Windows 8 / Windows Server 2012</span></span>
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- <span data-ttu-id="349db-160">Windows 8.1 nebo Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="349db-160">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="349db-161">Windows 10 nebo Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="349db-161">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="349db-162">V tématu [požadavky pro .NET Core v systému Windows](windows-prerequisites.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="349db-162">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="349db-163">Linux identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="349db-163">Linux RIDs</span></span>

- <span data-ttu-id="349db-164">Přenositelností</span><span class="sxs-lookup"><span data-stu-id="349db-164">Portable</span></span>
  - `linux-x64`
- <span data-ttu-id="349db-165">CentOS</span><span class="sxs-lookup"><span data-stu-id="349db-165">CentOS</span></span>
  - `centos-x64`
  - `centos.7-x64`
- <span data-ttu-id="349db-166">Debian</span><span class="sxs-lookup"><span data-stu-id="349db-166">Debian</span></span>
  - `debian-x64`
  - `debian.8-x64`
- <span data-ttu-id="349db-167">Fedora</span><span class="sxs-lookup"><span data-stu-id="349db-167">Fedora</span></span>
  - `fedora-x64`
  - `fedora.24-x64`
  - <span data-ttu-id="349db-168">`fedora.25-x64`(.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="349db-168">`fedora.25-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="349db-169">`fedora.26-x64`(.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="349db-169">`fedora.26-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="349db-170">Gentoo (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="349db-170">Gentoo (.NET Core 2.0 or later versions)</span></span>
  - `gentoo-x64`
- <span data-ttu-id="349db-171">openSUSE</span><span class="sxs-lookup"><span data-stu-id="349db-171">openSUSE</span></span>
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- <span data-ttu-id="349db-172">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="349db-172">Oracle Linux</span></span>
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- <span data-ttu-id="349db-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="349db-173">Red Hat Enterprise Linux</span></span>
  - `rhel-x64`
  - <span data-ttu-id="349db-174">`rhel.6-x64`(.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="349db-174">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - <span data-ttu-id="349db-175">`rhel.7.3-x64`(.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="349db-175">`rhel.7.3-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="349db-176">`rhel.7.4-x64`(.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="349db-176">`rhel.7.4-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="349db-177">Tizen (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="349db-177">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
- <span data-ttu-id="349db-178">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="349db-178">Ubuntu</span></span>
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- <span data-ttu-id="349db-179">Ubuntu odvozené konfigurace</span><span class="sxs-lookup"><span data-stu-id="349db-179">Ubuntu derivatives</span></span>
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - <span data-ttu-id="349db-180">`linuxmint.18.1-x64`(.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="349db-180">`linuxmint.18.1-x64` (.NET Core 2.0 or later versions)</span></span>

<span data-ttu-id="349db-181">V tématu [požadavky pro .NET Core v systému Linux](linux-prerequisites.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="349db-181">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="349db-182">systému macOS identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="349db-182">macOS RIDs</span></span>

<span data-ttu-id="349db-183">systému macOS RID použijte starší branding "OSX".</span><span class="sxs-lookup"><span data-stu-id="349db-183">macOS RIDs use the older "OSX" branding.</span></span>

- <span data-ttu-id="349db-184">`osx-x64`(.NET core 2.0 nebo novější verze, minimální verze je `osx.10.12-x64`)</span><span class="sxs-lookup"><span data-stu-id="349db-184">`osx-x64` (.NET Core 2.0 or later versions, minimum version is `osx.10.12-x64`)</span></span>
- `osx.10.10-x64`
- `osx.10.11-x64`
- <span data-ttu-id="349db-185">`osx.10.12-x64`(.NET core 1.1 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="349db-185">`osx.10.12-x64` (.NET Core 1.1 or later versions)</span></span>
- `osx.10.13-x64`

<span data-ttu-id="349db-186">V tématu [požadavky pro .NET Core v systému macOS](macos-prerequisites.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="349db-186">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="android-rids-net-core-20-or-later-versions"></a><span data-ttu-id="349db-187">Android identifikátorů RID (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="349db-187">Android RIDs (.NET Core 2.0 or later versions)</span></span>

- `android`
- `android.21`

## <a name="see-also"></a><span data-ttu-id="349db-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="349db-188">See also</span></span>

[<span data-ttu-id="349db-189">ID modulu runtime</span><span class="sxs-lookup"><span data-stu-id="349db-189">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
