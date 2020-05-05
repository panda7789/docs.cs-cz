---
title: Katalog identifikátorů runtime .NET Core (RID)
description: Přečtěte si o identifikátoru modulu runtime (RID) a způsobu použití identifikátorů RID v .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: b581f46becc6808ca957ac66c0c22e5e5f973bd1
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795557"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="65c4b-103">Katalog identifikátorů RID .NET Core</span><span class="sxs-lookup"><span data-stu-id="65c4b-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="65c4b-104">Identifikátor RID je pro *identifikátor modulu runtime*krátký.</span><span class="sxs-lookup"><span data-stu-id="65c4b-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="65c4b-105">Hodnoty RID slouží k identifikaci cílových platforem, ve kterých se aplikace spouští.</span><span class="sxs-lookup"><span data-stu-id="65c4b-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="65c4b-106">Jsou používány balíčky .NET k reprezentaci prostředků specifických pro platformu v balíčcích NuGet.</span><span class="sxs-lookup"><span data-stu-id="65c4b-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="65c4b-107">Následující hodnoty jsou příklady identifikátorů RID `linux-x64`:, `ubuntu.14.04-x64`, `win7-x64`nebo. `osx.10.12-x64`</span><span class="sxs-lookup"><span data-stu-id="65c4b-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="65c4b-108">U balíčků s nativními závislostmi Určuje identifikátor RID na kterých platformách se balíček dá obnovit.</span><span class="sxs-lookup"><span data-stu-id="65c4b-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="65c4b-109">V `<RuntimeIdentifier>` prvku souboru projektu lze nastavit jeden identifikátor RID.</span><span class="sxs-lookup"><span data-stu-id="65c4b-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="65c4b-110">V `<RuntimeIdentifiers>` prvku souboru projektu lze definovat více identifikátorů RID jako seznam středníkem oddělených hodnot.</span><span class="sxs-lookup"><span data-stu-id="65c4b-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="65c4b-111">Používají se také prostřednictvím `--runtime` možnosti s následujícími [.NET Core CLI příkazy](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="65c4b-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="65c4b-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="65c4b-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="65c4b-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="65c4b-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="65c4b-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="65c4b-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="65c4b-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="65c4b-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="65c4b-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="65c4b-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="65c4b-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="65c4b-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="65c4b-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="65c4b-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="65c4b-119">Identifikátorů RID, která představuje konkrétní operační systémy, se obvykle řídí `[os].[version]-[architecture]-[additional qualifiers]` tímto vzorem: kde:</span><span class="sxs-lookup"><span data-stu-id="65c4b-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="65c4b-120">`[os]`je moniker operačního systému/platformy.</span><span class="sxs-lookup"><span data-stu-id="65c4b-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="65c4b-121">Například, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="65c4b-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="65c4b-122">`[version]`verze operačního systému je ve formátu čísla verze odděleného tečkou (`.`).</span><span class="sxs-lookup"><span data-stu-id="65c4b-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="65c4b-123">Například, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="65c4b-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="65c4b-124">Verze **by neměla** být marketingová verze, protože často představují více diskrétních verzí operačního systému s různou oblastí rozhraní API platformy.</span><span class="sxs-lookup"><span data-stu-id="65c4b-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="65c4b-125">`[architecture]`je architekturou procesoru.</span><span class="sxs-lookup"><span data-stu-id="65c4b-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="65c4b-126">Například: `x86`, `x64`, `arm`nebo. `arm64`</span><span class="sxs-lookup"><span data-stu-id="65c4b-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="65c4b-127">`[additional qualifiers]`Další rozlišení různých platforem.</span><span class="sxs-lookup"><span data-stu-id="65c4b-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="65c4b-128">Například: `aot`.</span><span class="sxs-lookup"><span data-stu-id="65c4b-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="65c4b-129">Graf RID</span><span class="sxs-lookup"><span data-stu-id="65c4b-129">RID graph</span></span>

<span data-ttu-id="65c4b-130">Graf RID nebo modul runtime Fallback za běhu je seznam identifikátorů ridů, které jsou vzájemně kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="65c4b-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="65c4b-131">Identifikátorů RID jsou definované v balíčku [Microsoft. NETCore. Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) .</span><span class="sxs-lookup"><span data-stu-id="65c4b-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="65c4b-132">V souboru [*runtime. JSON*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) , který se nachází v `dotnet/runtime` úložišti, můžete zobrazit seznam podporovaných identifikátorů RID a grafu RID.</span><span class="sxs-lookup"><span data-stu-id="65c4b-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the `dotnet/runtime` repository.</span></span> <span data-ttu-id="65c4b-133">V tomto souboru vidíte, že všechny identifikátorů RID, s výjimkou základní třídy, obsahují `"#import"` příkaz.</span><span class="sxs-lookup"><span data-stu-id="65c4b-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="65c4b-134">Tyto příkazy označují kompatibilní identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="65c4b-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="65c4b-135">Když NuGet obnoví balíčky, pokusí se najít přesnou shodu pro zadaný modul runtime.</span><span class="sxs-lookup"><span data-stu-id="65c4b-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="65c4b-136">Pokud se nenajde přesná shoda, NuGet se vrátí do grafu, dokud nenajde nejbližší kompatibilní systém podle grafu RID.</span><span class="sxs-lookup"><span data-stu-id="65c4b-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="65c4b-137">V následujícím příkladu je aktuální položka pro `osx.10.12-x64` identifikátor RID:</span><span class="sxs-lookup"><span data-stu-id="65c4b-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="65c4b-138">Výše uvedené identifikátory RID určují `osx.10.12-x64` , `osx.10.11-x64`že importy.</span><span class="sxs-lookup"><span data-stu-id="65c4b-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="65c4b-139">Takže když NuGet obnoví balíčky, pokusí se najít přesnou shodu `osx.10.12-x64` v balíčku.</span><span class="sxs-lookup"><span data-stu-id="65c4b-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="65c4b-140">Pokud NuGet nemůže najít konkrétní modul runtime, může obnovit balíčky, které určují `osx.10.11-x64` moduly runtime, například.</span><span class="sxs-lookup"><span data-stu-id="65c4b-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="65c4b-141">Následující příklad ukazuje trochu větší graf RID, který je definován také v souboru *runtime. JSON* :</span><span class="sxs-lookup"><span data-stu-id="65c4b-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="65c4b-142">Všechny identifikátorů RID nakonec mapují zpátky na kořenový `any` identifikátor RID.</span><span class="sxs-lookup"><span data-stu-id="65c4b-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="65c4b-143">Existují některé okolnosti týkající se identifikátorů RID, které je třeba vzít v úvahu při práci s nimi:</span><span class="sxs-lookup"><span data-stu-id="65c4b-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="65c4b-144">Identifikátorů RID jsou **neprůhledné řetězce** a měly by se považovat za černé čtverečky.</span><span class="sxs-lookup"><span data-stu-id="65c4b-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="65c4b-145">Nevytvářejte identifikátorů RID programově.</span><span class="sxs-lookup"><span data-stu-id="65c4b-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="65c4b-146">Použijte identifikátorů RID, které už jsou pro platformu definované.</span><span class="sxs-lookup"><span data-stu-id="65c4b-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="65c4b-147">Identifikátorů RID musí být konkrétní, takže nemusíte nic od skutečné hodnoty RID předpokládat.</span><span class="sxs-lookup"><span data-stu-id="65c4b-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="65c4b-148">Použití identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="65c4b-148">Using RIDs</span></span>

<span data-ttu-id="65c4b-149">Aby bylo možné používat identifikátorů RID, musíte zjistit, které identifikátorů RID existují.</span><span class="sxs-lookup"><span data-stu-id="65c4b-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="65c4b-150">K platformě se pravidelně přidávají nové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="65c4b-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="65c4b-151">Nejnovější a kompletní verzi najdete v souboru [runtime. JSON](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v `dotnet/runtime` úložišti.</span><span class="sxs-lookup"><span data-stu-id="65c4b-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

<span data-ttu-id="65c4b-152">Sada .NET Core 2,0 SDK zavádí koncept přenosných identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="65c4b-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="65c4b-153">Jsou to nové hodnoty přidané do grafu RID, které nejsou vázané na konkrétní verzi nebo distribuci operačního systému, a jsou upřednostňovanou volbou při použití .NET Core 2,0 a vyšší.</span><span class="sxs-lookup"><span data-stu-id="65c4b-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="65c4b-154">Jsou zvláště užitečné při práci s více Linux distribuce, protože většina distribučních identifikátorů RID je mapována na přenosné identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="65c4b-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="65c4b-155">Následující seznam obsahuje malou podmnožinu nejběžnějších identifikátorů RID používaných pro každý operační systém.</span><span class="sxs-lookup"><span data-stu-id="65c4b-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="65c4b-156">Identifikátorů RID Windows</span><span class="sxs-lookup"><span data-stu-id="65c4b-156">Windows RIDs</span></span>

<span data-ttu-id="65c4b-157">Jsou uvedeny pouze běžné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="65c4b-157">Only common values are listed.</span></span> <span data-ttu-id="65c4b-158">Nejnovější a kompletní verzi najdete v souboru [runtime. JSON](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v `dotnet/runtime` úložišti.</span><span class="sxs-lookup"><span data-stu-id="65c4b-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="65c4b-159">Přenosná verze (.NET Core 2,0 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="65c4b-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="65c4b-160">Windows 7/Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="65c4b-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="65c4b-161">Windows 8.1/Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="65c4b-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="65c4b-162">Windows 10/Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="65c4b-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="65c4b-163">Další informace najdete v tématu [závislosti a požadavky .NET Core](install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="65c4b-163">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows).</span></span>

## <a name="linux-rids"></a><span data-ttu-id="65c4b-164">Linux identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="65c4b-164">Linux RIDs</span></span>

<span data-ttu-id="65c4b-165">Jsou uvedeny pouze běžné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="65c4b-165">Only common values are listed.</span></span> <span data-ttu-id="65c4b-166">Nejnovější a kompletní verzi najdete v souboru [runtime. JSON](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v `dotnet/runtime` úložišti.</span><span class="sxs-lookup"><span data-stu-id="65c4b-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span> <span data-ttu-id="65c4b-167">Zařízení s distribucí, která nejsou uvedená níže, můžou fungovat s jedním z přenosných identifikátorů RID.</span><span class="sxs-lookup"><span data-stu-id="65c4b-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="65c4b-168">Například zařízení Malina Pi, na kterých běží distribuce systému Linux, nejsou uvedená v `linux-arm`seznamu mohou být cílem.</span><span class="sxs-lookup"><span data-stu-id="65c4b-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="65c4b-169">Přenosná verze (.NET Core 2,0 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="65c4b-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="65c4b-170">`linux-x64`(Většina distribucí počítačů, jako jsou CentOS, Debian, Fedora, Ubuntu a deriváty)</span><span class="sxs-lookup"><span data-stu-id="65c4b-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu, and derivatives)</span></span>
  - <span data-ttu-id="65c4b-171">`linux-musl-x64`(Zjednodušené distribuce využívající [MUSL](https://wiki.musl-libc.org/projects-using-musl.html) jako Alpine Linux)</span><span class="sxs-lookup"><span data-stu-id="65c4b-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="65c4b-172">`linux-arm`(Distribuce systému Linux na ARM, jako je Raspbian v modelu 2 + pro maliny)</span><span class="sxs-lookup"><span data-stu-id="65c4b-172">`linux-arm` (Linux distributions running on ARM like Raspbian on Raspberry Pi Model 2+)</span></span>
  - <span data-ttu-id="65c4b-173">`linux-arm64`(Distribuce systému Linux spuštěná na 64 ARM, jako je Ubuntu Server 64-bit pro malinu Pi Model 3 +)</span><span class="sxs-lookup"><span data-stu-id="65c4b-173">`linux-arm64` (Linux distributions running on 64-bit ARM like Ubuntu Server 64-bit on Raspberry Pi Model 3+)</span></span>
- <span data-ttu-id="65c4b-174">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="65c4b-174">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="65c4b-175">`rhel-x64`(Nahrazeno serverem `linux-x64` pro RHEL nad verzí 6)</span><span class="sxs-lookup"><span data-stu-id="65c4b-175">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="65c4b-176">`rhel.6-x64`(.NET Core 2,0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="65c4b-176">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="65c4b-177">Tizen (.NET Core 2,0 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="65c4b-177">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="65c4b-178">Další informace najdete v tématu [závislosti a požadavky .NET Core](install/dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="65c4b-178">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux).</span></span>

## <a name="macos-rids"></a><span data-ttu-id="65c4b-179">macOS identifikátorů RID</span><span class="sxs-lookup"><span data-stu-id="65c4b-179">macOS RIDs</span></span>

<span data-ttu-id="65c4b-180">macOS identifikátorů RID používá starší značku "OSX".</span><span class="sxs-lookup"><span data-stu-id="65c4b-180">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="65c4b-181">Jsou uvedeny pouze běžné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="65c4b-181">Only common values are listed.</span></span> <span data-ttu-id="65c4b-182">Nejnovější a kompletní verzi najdete v souboru [runtime. JSON](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) v `dotnet/runtime` úložišti.</span><span class="sxs-lookup"><span data-stu-id="65c4b-182">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="65c4b-183">Přenosná verze (.NET Core 2,0 nebo novější)</span><span class="sxs-lookup"><span data-stu-id="65c4b-183">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="65c4b-184">`osx-x64`(Minimální verze operačního systému je macOS 10,12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="65c4b-184">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="65c4b-185">macOS 10,10 Yosemite</span><span class="sxs-lookup"><span data-stu-id="65c4b-185">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="65c4b-186">macOS 10,11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="65c4b-186">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="65c4b-187">macOS 10,12 Sierra (.NET Core 1,1 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="65c4b-187">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="65c4b-188">macOS 10,13 High Sierra (.NET Core 1,1 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="65c4b-188">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="65c4b-189">macOS 10,14 Mojave (.NET Core 1,1 nebo novější verze)</span><span class="sxs-lookup"><span data-stu-id="65c4b-189">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="65c4b-190">Další informace najdete v tématu [závislosti a požadavky .NET Core](install/dependencies.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="65c4b-190">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos).</span></span>

## <a name="see-also"></a><span data-ttu-id="65c4b-191">Viz také</span><span class="sxs-lookup"><span data-stu-id="65c4b-191">See also</span></span>

- [<span data-ttu-id="65c4b-192">ID modulu runtime</span><span class="sxs-lookup"><span data-stu-id="65c4b-192">Runtime IDs</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/readme.md)
