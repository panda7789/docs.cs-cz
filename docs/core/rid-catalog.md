---
title: Katalog IDentifier (RID) modulu .NET Core Runtime
description: Další informace o runtime IDentifier (RID) a jak ridy se používají v .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: feb19632f16a047ecfb2dcb697a9b837824a1929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451730"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="e84e5-103">Katalog RID jádra rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="e84e5-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="e84e5-104">RID je zkratka pro *Runtime IDentifier*.</span><span class="sxs-lookup"><span data-stu-id="e84e5-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="e84e5-105">Hodnoty RID se používají k identifikaci cílových platforem, na kterých je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="e84e5-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="e84e5-106">Používají je balíčky .NET k reprezentaci prostředků specifických pro platformu v balíčcích NuGet.</span><span class="sxs-lookup"><span data-stu-id="e84e5-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="e84e5-107">Následující hodnoty jsou příklady `linux-x64`ridů: , `ubuntu.14.04-x64`, `win7-x64`, nebo `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="e84e5-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="e84e5-108">Pro balíčky s nativní závislosti RID určuje, na kterých platformách balíček lze obnovit.</span><span class="sxs-lookup"><span data-stu-id="e84e5-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="e84e5-109">V prvku souboru `<RuntimeIdentifier>` projektu lze nastavit jeden rid.</span><span class="sxs-lookup"><span data-stu-id="e84e5-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="e84e5-110">Více RIdů lze definovat jako seznam oddělený středníkem v `<RuntimeIdentifiers>` prvku souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="e84e5-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="e84e5-111">Používají se také prostřednictvím možnosti `--runtime` s [následujícími příkazy .NET Core CLI](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="e84e5-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="e84e5-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="e84e5-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="e84e5-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="e84e5-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="e84e5-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="e84e5-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="e84e5-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="e84e5-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="e84e5-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="e84e5-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="e84e5-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="e84e5-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="e84e5-118">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="e84e5-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="e84e5-119">Ridy, které představují konkrétní operační `[os].[version]-[architecture]-[additional qualifiers]` systémy, obvykle postupujte podle tohoto vzoru: kde:</span><span class="sxs-lookup"><span data-stu-id="e84e5-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="e84e5-120">`[os]`je zástupný název systému nebo platformy.</span><span class="sxs-lookup"><span data-stu-id="e84e5-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="e84e5-121">Například, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="e84e5-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="e84e5-122">`[version]`je verze operačního systému ve formě čísla`.`verze oddělené tečkou ( ).</span><span class="sxs-lookup"><span data-stu-id="e84e5-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="e84e5-123">Například, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="e84e5-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="e84e5-124">Verze **by neměla** být marketingové verze, protože často představují více diskrétníverze operačního systému s různou plochou rozhraní API platformy.</span><span class="sxs-lookup"><span data-stu-id="e84e5-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="e84e5-125">`[architecture]`je architektura procesoru.</span><span class="sxs-lookup"><span data-stu-id="e84e5-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="e84e5-126">Například: `x86` `x64`, `arm`, `arm64`, nebo .</span><span class="sxs-lookup"><span data-stu-id="e84e5-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="e84e5-127">`[additional qualifiers]`dále odlišují různé platformy.</span><span class="sxs-lookup"><span data-stu-id="e84e5-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="e84e5-128">Například: `aot`.</span><span class="sxs-lookup"><span data-stu-id="e84e5-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="e84e5-129">Graf RID</span><span class="sxs-lookup"><span data-stu-id="e84e5-129">RID graph</span></span>

<span data-ttu-id="e84e5-130">Graf RID nebo záložní graf runtime je seznam ridů, které jsou vzájemně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="e84e5-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="e84e5-131">Rids jsou definovány v balíčku [Microsoft.NETCore.Platforms.](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/)</span><span class="sxs-lookup"><span data-stu-id="e84e5-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="e84e5-132">Seznam podporovaných ridů a graf RID můžete zobrazit v souboru [*runtime.json,*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) který je umístěn v `dotnet/runtime` úložišti.</span><span class="sxs-lookup"><span data-stu-id="e84e5-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the `dotnet/runtime` repository.</span></span> <span data-ttu-id="e84e5-133">V tomto souboru můžete vidět, že všechny RIDs, `"#import"` s výjimkou základní jeden, obsahují příkaz.</span><span class="sxs-lookup"><span data-stu-id="e84e5-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="e84e5-134">Tyto příkazy označují kompatibilní ids.</span><span class="sxs-lookup"><span data-stu-id="e84e5-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="e84e5-135">Když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro zadaný běh.</span><span class="sxs-lookup"><span data-stu-id="e84e5-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="e84e5-136">Pokud není nalezena přesná shoda, NuGet přejde zpět grafu, dokud nenajde nejbližší kompatibilní systém podle grafu RID.</span><span class="sxs-lookup"><span data-stu-id="e84e5-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="e84e5-137">Následující příklad je skutečná položka `osx.10.12-x64` pro RID:</span><span class="sxs-lookup"><span data-stu-id="e84e5-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="e84e5-138">Výše uvedený rid `osx.10.12-x64` určuje, `osx.10.11-x64`že importy .</span><span class="sxs-lookup"><span data-stu-id="e84e5-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="e84e5-139">Takže když NuGet obnoví balíčky, pokusí se `osx.10.12-x64` najít přesnou shodu v balíčku.</span><span class="sxs-lookup"><span data-stu-id="e84e5-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="e84e5-140">Pokud NuGet nemůže najít konkrétní runtime, může `osx.10.11-x64` obnovit balíčky, které určují runtime, například.</span><span class="sxs-lookup"><span data-stu-id="e84e5-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="e84e5-141">Následující příklad ukazuje mírně větší graf RID definovaný také v souboru *runtime.json:*</span><span class="sxs-lookup"><span data-stu-id="e84e5-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="e84e5-142">Všechny RID nakonec mapovat zpět `any` do kořenového RID.</span><span class="sxs-lookup"><span data-stu-id="e84e5-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="e84e5-143">Existují některé důležité informace o RIDs, které musíte mít na paměti při práci s nimi:</span><span class="sxs-lookup"><span data-stu-id="e84e5-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="e84e5-144">Rids jsou **neprůhledné řetězce** a měly by být považovány za černé skříňky.</span><span class="sxs-lookup"><span data-stu-id="e84e5-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="e84e5-145">Nevytvářejte RIDs programově.</span><span class="sxs-lookup"><span data-stu-id="e84e5-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="e84e5-146">Použijte RIDs, které jsou již definovány pro platformu.</span><span class="sxs-lookup"><span data-stu-id="e84e5-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="e84e5-147">Rids musí být konkrétní, takže nepředpokládejte nic ze skutečné hodnoty RID.</span><span class="sxs-lookup"><span data-stu-id="e84e5-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="e84e5-148">Použití ridů</span><span class="sxs-lookup"><span data-stu-id="e84e5-148">Using RIDs</span></span>

<span data-ttu-id="e84e5-149">Abyste mohli používat RIDs, musíte vědět, které RIDs existují.</span><span class="sxs-lookup"><span data-stu-id="e84e5-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="e84e5-150">Na platformu se pravidelně přidávají nové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e84e5-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="e84e5-151">Nejnovější a úplnou verzi naleznete v souboru [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v `dotnet/runtime` úložišti.</span><span class="sxs-lookup"><span data-stu-id="e84e5-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

<span data-ttu-id="e84e5-152">Sada .NET Core 2.0 SDK představuje koncept přenosných RIDů.</span><span class="sxs-lookup"><span data-stu-id="e84e5-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="e84e5-153">Jedná se o nové hodnoty přidané do grafu RID, které nejsou vázány na konkrétní verzi nebo distribuci operačního systému a jsou upřednostňovanou volbou při použití rozhraní .NET Core 2.0 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="e84e5-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="e84e5-154">Jsou obzvláště užitečné při práci s více distribucí Linuxu, protože většina distribučních RIDů je mapována na přenosné RIDs.</span><span class="sxs-lookup"><span data-stu-id="e84e5-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="e84e5-155">V následujícím seznamu je uvedena malá podmnožina nejběžnějších kontrolních disteorů používaných pro každý operační tým.</span><span class="sxs-lookup"><span data-stu-id="e84e5-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="e84e5-156">Windows RIDs</span><span class="sxs-lookup"><span data-stu-id="e84e5-156">Windows RIDs</span></span>

<span data-ttu-id="e84e5-157">Jsou uvedeny pouze běžné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e84e5-157">Only common values are listed.</span></span> <span data-ttu-id="e84e5-158">Nejnovější a úplnou verzi najdete v souboru `dotnet/runtime` [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v úložišti.</span><span class="sxs-lookup"><span data-stu-id="e84e5-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="e84e5-159">Přenosné (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="e84e5-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="e84e5-160">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="e84e5-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="e84e5-161">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="e84e5-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="e84e5-162">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="e84e5-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="e84e5-163">Další informace naleznete v tématu [.NET Core závislosti a požadavky](install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="e84e5-163">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows).</span></span>

## <a name="linux-rids"></a><span data-ttu-id="e84e5-164">Linuxové RID</span><span class="sxs-lookup"><span data-stu-id="e84e5-164">Linux RIDs</span></span>

<span data-ttu-id="e84e5-165">Jsou uvedeny pouze běžné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e84e5-165">Only common values are listed.</span></span> <span data-ttu-id="e84e5-166">Nejnovější a úplnou verzi naleznete v souboru [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v `dotnet/runtime` úložišti.</span><span class="sxs-lookup"><span data-stu-id="e84e5-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span> <span data-ttu-id="e84e5-167">Zařízení s distribucí, která není uvedena níže, mohou pracovat s jedním z přenosných zařízení ID.</span><span class="sxs-lookup"><span data-stu-id="e84e5-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="e84e5-168">Například zařízení Raspberry Pi se systémem linuxové `linux-arm`distribuce, která není uvedena, mohou být cílena pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="e84e5-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="e84e5-169">Přenosné (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="e84e5-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="e84e5-170">`linux-x64`(Většina desktopových distribucí jako CentOS, Debian, Fedora, Ubuntu a deriváty)</span><span class="sxs-lookup"><span data-stu-id="e84e5-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu, and derivatives)</span></span>
  - <span data-ttu-id="e84e5-171">`linux-musl-x64`(Lehké distribuce pomocí [musl](https://wiki.musl-libc.org/projects-using-musl.html) jako Alpine Linux)</span><span class="sxs-lookup"><span data-stu-id="e84e5-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="e84e5-172">`linux-arm`(Linuxové distribuce běžící na ARM jako Raspberry Pi)</span><span class="sxs-lookup"><span data-stu-id="e84e5-172">`linux-arm` (Linux distributions running on ARM like Raspberry Pi)</span></span>
- <span data-ttu-id="e84e5-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="e84e5-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="e84e5-174">`rhel-x64`(Nahrazeno `linux-x64` pro RHEL nad verzí 6)</span><span class="sxs-lookup"><span data-stu-id="e84e5-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="e84e5-175">`rhel.6-x64`(.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="e84e5-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="e84e5-176">Tizen (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="e84e5-176">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="e84e5-177">Další informace naleznete v tématu [.NET Core závislosti a požadavky](install/dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="e84e5-177">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux).</span></span>

## <a name="macos-rids"></a><span data-ttu-id="e84e5-178">MacOS RIDs</span><span class="sxs-lookup"><span data-stu-id="e84e5-178">macOS RIDs</span></span>

<span data-ttu-id="e84e5-179">MacOS RID s použitím starší značky "OSX".</span><span class="sxs-lookup"><span data-stu-id="e84e5-179">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="e84e5-180">Jsou uvedeny pouze běžné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e84e5-180">Only common values are listed.</span></span> <span data-ttu-id="e84e5-181">Nejnovější a úplnou verzi naleznete v souboru [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v `dotnet/runtime` úložišti.</span><span class="sxs-lookup"><span data-stu-id="e84e5-181">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="e84e5-182">Přenosné (.NET Core 2.0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="e84e5-182">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="e84e5-183">`osx-x64`(Minimální verze operačního systému je macOS 10.12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="e84e5-183">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="e84e5-184">macOS 10.10 Yosemite</span><span class="sxs-lookup"><span data-stu-id="e84e5-184">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="e84e5-185">macOS 10.11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="e84e5-185">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="e84e5-186">macOS 10.12 Sierra (verze.NET Core 1.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="e84e5-186">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="e84e5-187">macOS 10.13 High Sierra (.NET Core 1.1 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="e84e5-187">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="e84e5-188">macOS 10.14 Mojave (verze.NET Core 1.1 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="e84e5-188">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="e84e5-189">Další informace naleznete v tématu [.NET Core závislosti a požadavky](install/dependencies.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="e84e5-189">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos).</span></span>

## <a name="see-also"></a><span data-ttu-id="e84e5-190">Viz také</span><span class="sxs-lookup"><span data-stu-id="e84e5-190">See also</span></span>

- [<span data-ttu-id="e84e5-191">ID běhu</span><span class="sxs-lookup"><span data-stu-id="e84e5-191">Runtime IDs</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/readme.md)
