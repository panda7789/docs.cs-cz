---
title: Katalog identifikátorů runtime .NET Core (RID)
description: Přečtěte si o identifikátoru modulu runtime (RID) a způsobu použití identifikátorů RID v .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: e6bc3f75858d4b67cc8598e49ff4ad75521f16d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100923"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="051f9-103">Katalog identifikátorů RID .NET Core</span><span class="sxs-lookup"><span data-stu-id="051f9-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="051f9-104">Identifikátor RID je pro *identifikátor modulu runtime*krátký.</span><span class="sxs-lookup"><span data-stu-id="051f9-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="051f9-105">Hodnoty RID slouží k identifikaci cílových platforem, ve kterých se aplikace spouští.</span><span class="sxs-lookup"><span data-stu-id="051f9-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="051f9-106">Jsou používány balíčky .NET k reprezentaci prostředků specifických pro platformu v balíčcích NuGet.</span><span class="sxs-lookup"><span data-stu-id="051f9-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="051f9-107">Následující hodnoty jsou příklady identifikátorů RID: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`nebo `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="051f9-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="051f9-108">U balíčků s nativními závislostmi Určuje identifikátor RID na kterých platformách se balíček dá obnovit.</span><span class="sxs-lookup"><span data-stu-id="051f9-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="051f9-109">Jeden identifikátor RID lze nastavit v prvku `<RuntimeIdentifier>` souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="051f9-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="051f9-110">Více identifikátorů RID lze definovat jako seznam středníkem oddělených v `<RuntimeIdentifiers>` elementu souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="051f9-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="051f9-111">Používají se taky prostřednictvím možnosti `--runtime` s následujícími [.NET Core CLI příkazy](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="051f9-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="051f9-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="051f9-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="051f9-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="051f9-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="051f9-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="051f9-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="051f9-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="051f9-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="051f9-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="051f9-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="051f9-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="051f9-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="051f9-118">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="051f9-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="051f9-119">Identifikátorů RID, které reprezentují konkrétní operační systémy, se obvykle řídí tímto vzorem: `[os].[version]-[architecture]-[additional qualifiers]`, kde:</span><span class="sxs-lookup"><span data-stu-id="051f9-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="051f9-120">`[os]` je moniker operačního systému nebo platformy.</span><span class="sxs-lookup"><span data-stu-id="051f9-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="051f9-121">Například `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="051f9-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="051f9-122">`[version]` je verze operačního systému ve formě čísla verze odděleného tečkou (`.`).</span><span class="sxs-lookup"><span data-stu-id="051f9-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="051f9-123">Například `15.10`.</span><span class="sxs-lookup"><span data-stu-id="051f9-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="051f9-124">Verze **by neměla** být marketingová verze, protože často představují více diskrétních verzí operačního systému s různou oblastí rozhraní API platformy.</span><span class="sxs-lookup"><span data-stu-id="051f9-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="051f9-125">`[architecture]` je architektura procesoru.</span><span class="sxs-lookup"><span data-stu-id="051f9-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="051f9-126">Například: `x86`, `x64`, `arm`nebo `arm64`.</span><span class="sxs-lookup"><span data-stu-id="051f9-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="051f9-127">`[additional qualifiers]` dále odlišit různé platformy.</span><span class="sxs-lookup"><span data-stu-id="051f9-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="051f9-128">Například: `aot`.</span><span class="sxs-lookup"><span data-stu-id="051f9-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="051f9-129">Graf RID</span><span class="sxs-lookup"><span data-stu-id="051f9-129">RID graph</span></span>

<span data-ttu-id="051f9-130">Graf RID nebo modul runtime Fallback za běhu je seznam identifikátorů ridů, které jsou vzájemně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="051f9-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="051f9-131">Identifikátorů RID jsou definované v balíčku [Microsoft. NETCore. Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) .</span><span class="sxs-lookup"><span data-stu-id="051f9-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="051f9-132">Můžete se podívat na seznam podporovaných identifikátorů RID a grafu RID v souboru [*runtime. JSON*](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) , který se nachází v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="051f9-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="051f9-133">V tomto souboru vidíte, že všechny identifikátorů RID, s výjimkou základní třídy, obsahují příkaz `"#import"`.</span><span class="sxs-lookup"><span data-stu-id="051f9-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="051f9-134">Tyto příkazy označují kompatibilní identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="051f9-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="051f9-135">Když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro zadaný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="051f9-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="051f9-136">Pokud se nenajde přesná shoda, NuGet se vrátí do grafu, dokud nenajde nejbližší kompatibilní systém podle grafu RID.</span><span class="sxs-lookup"><span data-stu-id="051f9-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="051f9-137">V následujícím příkladu je aktuální položka pro `osx.10.12-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="051f9-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="051f9-138">Výše uvedené identifikátory RID určuje, že `osx.10.12-x64` import `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="051f9-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="051f9-139">Takže když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro `osx.10.12-x64` v balíčku.</span><span class="sxs-lookup"><span data-stu-id="051f9-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="051f9-140">Pokud NuGet nemůže najít konkrétní modul runtime, může obnovit balíčky, které určují `osx.10.11-x64` modul runtime, například.</span><span class="sxs-lookup"><span data-stu-id="051f9-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="051f9-141">Následující příklad ukazuje trochu větší graf RID, který je definován také v souboru *runtime. JSON* :</span><span class="sxs-lookup"><span data-stu-id="051f9-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="051f9-142">Všechny identifikátorů RID nakonec mapují zpátky na kořenový `any` identifikátor RID.</span><span class="sxs-lookup"><span data-stu-id="051f9-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="051f9-143">Existují některé okolnosti týkající se identifikátorů RID, které je třeba vzít v úvahu při práci s nimi:</span><span class="sxs-lookup"><span data-stu-id="051f9-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="051f9-144">Identifikátorů RID jsou **neprůhledné řetězce** a měly by se považovat za černé čtverečky.</span><span class="sxs-lookup"><span data-stu-id="051f9-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="051f9-145">Nevytvářejte identifikátorů RID programově.</span><span class="sxs-lookup"><span data-stu-id="051f9-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="051f9-146">Použijte identifikátorů RID, které už jsou pro platformu definované.</span><span class="sxs-lookup"><span data-stu-id="051f9-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="051f9-147">Identifikátorů RID musí být konkrétní, takže nemusíte nic od skutečné hodnoty RID předpokládat.</span><span class="sxs-lookup"><span data-stu-id="051f9-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="051f9-148">Použití identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="051f9-148">Using RIDs</span></span>

<span data-ttu-id="051f9-149">Aby bylo možné používat identifikátorů RID, musíte zjistit, které identifikátorů RID existují.</span><span class="sxs-lookup"><span data-stu-id="051f9-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="051f9-150">K platformě se pravidelně přidávají nové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="051f9-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="051f9-151">Nejnovější a kompletní verzi najdete v souboru [runtime. JSON](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="051f9-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="051f9-152">Sada .NET Core 2,0 SDK zavádí koncept přenosných identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="051f9-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="051f9-153">Jsou to nové hodnoty přidané do grafu RID, které nejsou vázané na konkrétní verzi nebo distribuci operačního systému, a jsou upřednostňovanou volbou při použití .NET Core 2,0 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="051f9-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="051f9-154">Jsou zvláště užitečné při práci s více Linux distribuce, protože většina distribučních identifikátorů RID je mapována na přenosné identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="051f9-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="051f9-155">Následující seznam obsahuje malou podmnožinu nejběžnějších identifikátorů RID používaných pro každý operační systém.</span><span class="sxs-lookup"><span data-stu-id="051f9-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="051f9-156">Identifikátorů RID Windows</span><span class="sxs-lookup"><span data-stu-id="051f9-156">Windows RIDs</span></span>

<span data-ttu-id="051f9-157">Jsou uvedeny pouze běžné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="051f9-157">Only common values are listed.</span></span> <span data-ttu-id="051f9-158">Nejnovější a kompletní verzi najdete v souboru [runtime. JSON](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="051f9-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

- <span data-ttu-id="051f9-159">Přenosná verze (.NET Core 2,0 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="051f9-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="051f9-160">Windows 7/Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="051f9-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="051f9-161">Windows 8.1/Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="051f9-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="051f9-162">Windows 10/Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="051f9-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="051f9-163">Další informace najdete v tématu [předpoklady pro .NET Core v systému Windows](windows-prerequisites.md) .</span><span class="sxs-lookup"><span data-stu-id="051f9-163">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="051f9-164">Linux identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="051f9-164">Linux RIDs</span></span>

<span data-ttu-id="051f9-165">Jsou uvedeny pouze běžné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="051f9-165">Only common values are listed.</span></span> <span data-ttu-id="051f9-166">Nejnovější a kompletní verzi najdete v souboru [runtime. JSON](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="051f9-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span> <span data-ttu-id="051f9-167">Zařízení s distribucí, která nejsou uvedená níže, můžou fungovat s jedním z přenosných identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="051f9-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="051f9-168">Například zařízení maliny PI, na kterých běží distribuce systému Linux, nejsou uvedená v seznamu mohou být cílem `linux-arm`.</span><span class="sxs-lookup"><span data-stu-id="051f9-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="051f9-169">Přenosná verze (.NET Core 2,0 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="051f9-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="051f9-170">`linux-x64` (Většina distribucí počítačů, jako jsou CentOS, Debian, Fedora, Ubuntu a deriváty)</span><span class="sxs-lookup"><span data-stu-id="051f9-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu and derivatives)</span></span>
  - <span data-ttu-id="051f9-171">`linux-musl-x64` (prosté distribuce pomocí [MUSL](https://wiki.musl-libc.org/projects-using-musl.html) jako Alpine Linux)</span><span class="sxs-lookup"><span data-stu-id="051f9-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="051f9-172">`linux-arm` (distribuce systému Linux spuštěná na ARM, jako je například Malina PI)</span><span class="sxs-lookup"><span data-stu-id="051f9-172">`linux-arm` (Linux distributions running on ARM like Raspberry Pi)</span></span>
- <span data-ttu-id="051f9-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="051f9-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="051f9-174">`rhel-x64` (nahrazeno `linux-x64` pro RHEL nad verzí 6)</span><span class="sxs-lookup"><span data-stu-id="051f9-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="051f9-175">`rhel.6-x64` (.NET Core 2,0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="051f9-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="051f9-176">Tizen (.NET Core 2,0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="051f9-176">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="051f9-177">Další informace najdete v tématu [předpoklady pro .NET Core na platformě Linux](linux-prerequisites.md) .</span><span class="sxs-lookup"><span data-stu-id="051f9-177">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="051f9-178">macOS identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="051f9-178">macOS RIDs</span></span>

<span data-ttu-id="051f9-179">macOS identifikátorů RID používá starší značku "OSX".</span><span class="sxs-lookup"><span data-stu-id="051f9-179">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="051f9-180">Jsou uvedeny pouze běžné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="051f9-180">Only common values are listed.</span></span> <span data-ttu-id="051f9-181">Nejnovější a kompletní verzi najdete v souboru [runtime. JSON](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) v úložišti CoreFX.</span><span class="sxs-lookup"><span data-stu-id="051f9-181">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

- <span data-ttu-id="051f9-182">Přenosná verze (.NET Core 2,0 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="051f9-182">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="051f9-183">`osx-x64` (minimální verze operačního systému je macOS 10,12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="051f9-183">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="051f9-184">macOS 10,10 Yosemite</span><span class="sxs-lookup"><span data-stu-id="051f9-184">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="051f9-185">macOS 10,11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="051f9-185">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="051f9-186">macOS 10,12 Sierra (.NET Core 1,1 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="051f9-186">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="051f9-187">macOS 10,13 High Sierra (.NET Core 1,1 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="051f9-187">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="051f9-188">macOS 10,14 Mojave (.NET Core 1,1 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="051f9-188">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="051f9-189">Další informace najdete v tématu [předpoklady pro .NET Core v MacOS](macos-prerequisites.md) .</span><span class="sxs-lookup"><span data-stu-id="051f9-189">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="051f9-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="051f9-190">See also</span></span>

- [<span data-ttu-id="051f9-191">ID modulu runtime</span><span class="sxs-lookup"><span data-stu-id="051f9-191">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/readme.md)
