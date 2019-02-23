---
title: .NET core Runtime identifikátor (RID) katalogu
description: Další informace o identifikátor modulu Runtime (RID) a používání identifikátorů RID v .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: 0d03e39c755b43e145edf5efe48422cbae7abcab
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745739"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="13faf-103">Katalog identifikátorů RID .NET core</span><span class="sxs-lookup"><span data-stu-id="13faf-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="13faf-104">Je zkratka pro identifikátorů RID *identifikátor modulu Runtime*.</span><span class="sxs-lookup"><span data-stu-id="13faf-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="13faf-105">Identifikátor RID hodnoty se používají k identifikaci cílové platformy, kde je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="13faf-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="13faf-106">Balíčky .NET, se používá k reprezentování specifické pro platformu prostředky v balíčcích NuGet.</span><span class="sxs-lookup"><span data-stu-id="13faf-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="13faf-107">Následující hodnoty jsou příklady identifikátorů RID: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, nebo `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="13faf-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="13faf-108">Pro balíčky s nativní závislosti označí RID, na kterých platformách lze obnovit balíček.</span><span class="sxs-lookup"><span data-stu-id="13faf-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="13faf-109">Jediný identifikátorů RID je možné nastavit v `<RuntimeIdentifier>` prvek souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="13faf-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="13faf-110">Více identifikátorů RID je definovat jako seznam oddělený středníkem v souboru projektu `<RuntimeIdentifiers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="13faf-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="13faf-111">Používají se také prostřednictvím `--runtime` možnost následujícím [příkazy rozhraní příkazového řádku .NET Core](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="13faf-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="13faf-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="13faf-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="13faf-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="13faf-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="13faf-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="13faf-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="13faf-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="13faf-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="13faf-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="13faf-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="13faf-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="13faf-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="13faf-118">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="13faf-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="13faf-119">Identifikátory RID, představující konkrétní operační systémy obvykle podle tohoto vzoru: `[os].[version]-[architecture]-[additional qualifiers]` kde:</span><span class="sxs-lookup"><span data-stu-id="13faf-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="13faf-120">`[os]` je moniker provozní/platform system.</span><span class="sxs-lookup"><span data-stu-id="13faf-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="13faf-121">Například, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="13faf-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="13faf-122">`[version]` verze operačního systému ve formě oddělené tečkou (`.`) číslo verze.</span><span class="sxs-lookup"><span data-stu-id="13faf-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="13faf-123">Například, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="13faf-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="13faf-124">Verze **by neměl** být marketingové verze, jak často představují více samostatných verzí operačního systému s použitím různých styčné plochy rozhraní API platformy.</span><span class="sxs-lookup"><span data-stu-id="13faf-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="13faf-125">`[architecture]` je na architektuře procesoru.</span><span class="sxs-lookup"><span data-stu-id="13faf-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="13faf-126">Příklad: `x86`, `x64`, `arm`, nebo `arm64`.</span><span class="sxs-lookup"><span data-stu-id="13faf-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="13faf-127">`[additional qualifiers]` dál rozlišit různé platformy.</span><span class="sxs-lookup"><span data-stu-id="13faf-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="13faf-128">Například: `aot`.</span><span class="sxs-lookup"><span data-stu-id="13faf-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="13faf-129">Identifikátor RID grafu</span><span class="sxs-lookup"><span data-stu-id="13faf-129">RID graph</span></span>

<span data-ttu-id="13faf-130">Graf identifikátorů RID nebo záložní grafu modulu runtime je seznam identifikátorů RID, které jsou vzájemně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="13faf-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="13faf-131">Identifikátory RID, které jsou definovány v [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) balíčku.</span><span class="sxs-lookup"><span data-stu-id="13faf-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="13faf-132">Můžete zobrazit seznam podporovaných identifikátorů RID a graf identifikátorů RID [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) soubor, který se nachází v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="13faf-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="13faf-133">V tomto souboru, uvidíte, že všechny identifikátory RID, s výjimkou je základní obsahovat `"#import"` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13faf-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="13faf-134">Tyto příkazy označují kompatibilní identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="13faf-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="13faf-135">Když NuGet obnoví balíčky, pokusí se vyhledat přesnou shodu zadaného modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="13faf-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="13faf-136">Pokud se najde přesná shoda, NuGet vás zpět grafu dokud vyhledá nejbližší kompatibilní systému podle identifikátorů RID grafu.</span><span class="sxs-lookup"><span data-stu-id="13faf-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="13faf-137">V následujícím příkladu je skutečná položku `osx.10.12-x64` identifikátorů RID:</span><span class="sxs-lookup"><span data-stu-id="13faf-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="13faf-138">Výše uvedené identifikátorů RID, který určuje `osx.10.12-x64` importuje `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="13faf-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="13faf-139">Proto když NuGet obnoví balíčky, pokusí se vyhledat přesnou shodu pro `osx.10.12-x64` v balíčku.</span><span class="sxs-lookup"><span data-stu-id="13faf-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="13faf-140">Pokud NuGet nemůžete najít konkrétní modulu runtime, můžete obnovit balíčky, které určují `osx.10.11-x64` moduly runtime, například.</span><span class="sxs-lookup"><span data-stu-id="13faf-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="13faf-141">Následující příklad ukazuje mírně větší identifikátorů RID graf také definováno v *runtime.json* souboru:</span><span class="sxs-lookup"><span data-stu-id="13faf-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="13faf-142">Všechny identifikátory RID se nakonec mapování zpět do kořenového adresáře `any` identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="13faf-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="13faf-143">Zde jsou některé důležité informace o identifikátorech RID, které je třeba vzít v úvahu při práci s nimi:</span><span class="sxs-lookup"><span data-stu-id="13faf-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="13faf-144">Jsou identifikátory RID **neprůhledné řetězce** a by měl být považován za černé skříňky.</span><span class="sxs-lookup"><span data-stu-id="13faf-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="13faf-145">Nezačleňujte identifikátorů RID prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="13faf-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="13faf-146">Použijte identifikátory RID, které jsou již definovány pro platformu.</span><span class="sxs-lookup"><span data-stu-id="13faf-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="13faf-147">Identifikátory RID musí mít konkrétní, takže Nepředpokládejte, že je vše od skutečné hodnoty identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="13faf-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="13faf-148">Pomocí identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="13faf-148">Using RIDs</span></span>

<span data-ttu-id="13faf-149">Aby bylo možné používat identifikátory RID, budete muset vědět, které existují identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="13faf-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="13faf-150">Na platformu jsou pravidelně přidávat nové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="13faf-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="13faf-151">Nejnovější a dokončení, najdete v článku [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="13faf-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="13faf-152">.NET core 2.0 SDK zavádí koncepci přenosné identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="13faf-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="13faf-153">Jsou nové hodnoty, které se přidávají do grafu identifikátorů RID, které nejsou vázány na konkrétní verzi nebo distribuce operačního systému a jsou upřednostňované volbou, pokud používáte .NET Core 2.0 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="13faf-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="13faf-154">Jsou užitečné zejména při práci s více distribuce Linuxu od většina distribuce identifikátorů RID se mapují na přenosné identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="13faf-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="13faf-155">Následující seznam obsahuje malou podmnožinu nejběžnější identifikátory RID používat pro každý operační systém.</span><span class="sxs-lookup"><span data-stu-id="13faf-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="13faf-156">Identifikátory RID Windows</span><span class="sxs-lookup"><span data-stu-id="13faf-156">Windows RIDs</span></span>

<span data-ttu-id="13faf-157">Pouze běžné hodnoty jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="13faf-157">Only common values are listed.</span></span> <span data-ttu-id="13faf-158">Nejnovější a dokončení, najdete v článku [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="13faf-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

- <span data-ttu-id="13faf-159">Přenosná (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="13faf-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="13faf-160">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="13faf-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="13faf-161">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="13faf-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="13faf-162">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="13faf-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="13faf-163">Zobrazit [předpoklady pro .NET Core ve Windows](windows-prerequisites.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="13faf-163">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="13faf-164">Linux identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="13faf-164">Linux RIDs</span></span>

<span data-ttu-id="13faf-165">Pouze běžné hodnoty jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="13faf-165">Only common values are listed.</span></span> <span data-ttu-id="13faf-166">Nejnovější a dokončení, najdete v článku [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="13faf-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span> <span data-ttu-id="13faf-167">Zařízení se systémem distribuce není uvedená níže může pracovat s některou z přenosné identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="13faf-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="13faf-168">Například zařízení Raspberry Pi s Linuxová distribuce není uvedená, je možné cílit s `linux-arm`.</span><span class="sxs-lookup"><span data-stu-id="13faf-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="13faf-169">Přenosná (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="13faf-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="13faf-170">`linux-x64` (Většina klientů distribucí, jako jsou CentOS, Debian, Fedora, Ubuntu nebo odvozené konfigurace)</span><span class="sxs-lookup"><span data-stu-id="13faf-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu and derivatives)</span></span>
  - <span data-ttu-id="13faf-171">`linux-musl-x64` (Zjednodušené distribuce využívající [musl](https://wiki.musl-libc.org/projects-using-musl.html) Alpine Linuxu, jako je)</span><span class="sxs-lookup"><span data-stu-id="13faf-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="13faf-172">`linux-arm` (Běžící na ARM Linuxových distribucí, jako je Raspberry Pi)</span><span class="sxs-lookup"><span data-stu-id="13faf-172">`linux-arm` (Linux distributions running on ARM like Raspberry Pi)</span></span>
- <span data-ttu-id="13faf-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="13faf-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="13faf-174">`rhel-x64` (Nahrazena `linux-x64` pro RHEL vyšší než verze 6)</span><span class="sxs-lookup"><span data-stu-id="13faf-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="13faf-175">`rhel.6-x64` (.NET core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="13faf-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="13faf-176">Tizen (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="13faf-176">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="13faf-177">Zobrazit [předpoklady pro .NET Core v Linuxu](linux-prerequisites.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="13faf-177">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="13faf-178">macOS identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="13faf-178">macOS RIDs</span></span>

<span data-ttu-id="13faf-179">macOS identifikátory RID používat starší branding "OSX".</span><span class="sxs-lookup"><span data-stu-id="13faf-179">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="13faf-180">Pouze běžné hodnoty jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="13faf-180">Only common values are listed.</span></span> <span data-ttu-id="13faf-181">Nejnovější a dokončení, najdete v článku [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) souboru v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="13faf-181">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

- <span data-ttu-id="13faf-182">Přenosná (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="13faf-182">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="13faf-183">`osx-x64` (Minimální verze operačního systému je macOS 10.12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="13faf-183">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="13faf-184">macOS 10.10  Yosemite</span><span class="sxs-lookup"><span data-stu-id="13faf-184">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="13faf-185">macOS 10.11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="13faf-185">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="13faf-186">macOS 10.12 Sierra (.NET Core 1.1 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="13faf-186">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="13faf-187">macOS 10.13 High Sierra (.NET Core 1.1 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="13faf-187">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="13faf-188">macOS 10.14 Mojave (.NET Core 1.1 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="13faf-188">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="13faf-189">Zobrazit [předpoklady pro .NET Core v macOS](macos-prerequisites.md) pro další informace.</span><span class="sxs-lookup"><span data-stu-id="13faf-189">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="13faf-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13faf-190">See also</span></span>

- [<span data-ttu-id="13faf-191">ID modulu runtime</span><span class="sxs-lookup"><span data-stu-id="13faf-191">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
