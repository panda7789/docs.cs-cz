---
title: .NET Core Runtime IDentifier (RID) catalog
description: Learn about the Runtime IDentifier (RID) and how RIDs are used in .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: f90aabf0d10ce61dc10fcd952d66ca00e66d282d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428735"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="7f3da-103">.NET Core RID Catalog</span><span class="sxs-lookup"><span data-stu-id="7f3da-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="7f3da-104">RID is short for *Runtime IDentifier*.</span><span class="sxs-lookup"><span data-stu-id="7f3da-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="7f3da-105">RID values are used to identify target platforms where the application runs.</span><span class="sxs-lookup"><span data-stu-id="7f3da-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="7f3da-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span><span class="sxs-lookup"><span data-stu-id="7f3da-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="7f3da-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="7f3da-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="7f3da-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span><span class="sxs-lookup"><span data-stu-id="7f3da-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="7f3da-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span><span class="sxs-lookup"><span data-stu-id="7f3da-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="7f3da-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span><span class="sxs-lookup"><span data-stu-id="7f3da-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="7f3da-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="7f3da-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="7f3da-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="7f3da-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="7f3da-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="7f3da-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="7f3da-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="7f3da-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="7f3da-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="7f3da-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="7f3da-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="7f3da-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="7f3da-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="7f3da-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="7f3da-118">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="7f3da-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="7f3da-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span><span class="sxs-lookup"><span data-stu-id="7f3da-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="7f3da-120">`[os]` is the operating/platform system moniker.</span><span class="sxs-lookup"><span data-stu-id="7f3da-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="7f3da-121">For example, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="7f3da-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="7f3da-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span><span class="sxs-lookup"><span data-stu-id="7f3da-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="7f3da-123">For example, `15.10`.</span><span class="sxs-lookup"><span data-stu-id="7f3da-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="7f3da-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span><span class="sxs-lookup"><span data-stu-id="7f3da-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="7f3da-125">`[architecture]` is the processor architecture.</span><span class="sxs-lookup"><span data-stu-id="7f3da-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="7f3da-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span><span class="sxs-lookup"><span data-stu-id="7f3da-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="7f3da-127">`[additional qualifiers]` further differentiate different platforms.</span><span class="sxs-lookup"><span data-stu-id="7f3da-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="7f3da-128">For example: `aot`.</span><span class="sxs-lookup"><span data-stu-id="7f3da-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="7f3da-129">RID graph</span><span class="sxs-lookup"><span data-stu-id="7f3da-129">RID graph</span></span>

<span data-ttu-id="7f3da-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span><span class="sxs-lookup"><span data-stu-id="7f3da-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="7f3da-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span><span class="sxs-lookup"><span data-stu-id="7f3da-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="7f3da-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span><span class="sxs-lookup"><span data-stu-id="7f3da-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="7f3da-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span><span class="sxs-lookup"><span data-stu-id="7f3da-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="7f3da-134">These statements indicate compatible RIDs.</span><span class="sxs-lookup"><span data-stu-id="7f3da-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="7f3da-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span><span class="sxs-lookup"><span data-stu-id="7f3da-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="7f3da-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span><span class="sxs-lookup"><span data-stu-id="7f3da-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="7f3da-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span><span class="sxs-lookup"><span data-stu-id="7f3da-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="7f3da-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="7f3da-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="7f3da-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span><span class="sxs-lookup"><span data-stu-id="7f3da-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="7f3da-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span><span class="sxs-lookup"><span data-stu-id="7f3da-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="7f3da-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span><span class="sxs-lookup"><span data-stu-id="7f3da-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="7f3da-142">All RIDs eventually map back to the root `any` RID.</span><span class="sxs-lookup"><span data-stu-id="7f3da-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="7f3da-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span><span class="sxs-lookup"><span data-stu-id="7f3da-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="7f3da-144">RIDs are **opaque strings** and should be treated as black boxes.</span><span class="sxs-lookup"><span data-stu-id="7f3da-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="7f3da-145">Don't build RIDs programmatically.</span><span class="sxs-lookup"><span data-stu-id="7f3da-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="7f3da-146">Use RIDs that are already defined for the platform.</span><span class="sxs-lookup"><span data-stu-id="7f3da-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="7f3da-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span><span class="sxs-lookup"><span data-stu-id="7f3da-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="7f3da-148">Using RIDs</span><span class="sxs-lookup"><span data-stu-id="7f3da-148">Using RIDs</span></span>

<span data-ttu-id="7f3da-149">To be able to use RIDs, you have to know which RIDs exist.</span><span class="sxs-lookup"><span data-stu-id="7f3da-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="7f3da-150">New values are added regularly to the platform.</span><span class="sxs-lookup"><span data-stu-id="7f3da-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="7f3da-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span><span class="sxs-lookup"><span data-stu-id="7f3da-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="7f3da-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span><span class="sxs-lookup"><span data-stu-id="7f3da-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="7f3da-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span><span class="sxs-lookup"><span data-stu-id="7f3da-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="7f3da-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span><span class="sxs-lookup"><span data-stu-id="7f3da-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="7f3da-155">The following list shows a small subset of the most common RIDs used for each OS.</span><span class="sxs-lookup"><span data-stu-id="7f3da-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="7f3da-156">Windows RIDs</span><span class="sxs-lookup"><span data-stu-id="7f3da-156">Windows RIDs</span></span>

<span data-ttu-id="7f3da-157">Only common values are listed.</span><span class="sxs-lookup"><span data-stu-id="7f3da-157">Only common values are listed.</span></span> <span data-ttu-id="7f3da-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span><span class="sxs-lookup"><span data-stu-id="7f3da-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

- <span data-ttu-id="7f3da-159">Portable (.NET Core 2.0 or later versions)</span><span class="sxs-lookup"><span data-stu-id="7f3da-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="7f3da-160">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="7f3da-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="7f3da-161">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7f3da-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="7f3da-162">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="7f3da-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="7f3da-163">See [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) for more information.</span><span class="sxs-lookup"><span data-stu-id="7f3da-163">See [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="7f3da-164">Linux RIDs</span><span class="sxs-lookup"><span data-stu-id="7f3da-164">Linux RIDs</span></span>

<span data-ttu-id="7f3da-165">Only common values are listed.</span><span class="sxs-lookup"><span data-stu-id="7f3da-165">Only common values are listed.</span></span> <span data-ttu-id="7f3da-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span><span class="sxs-lookup"><span data-stu-id="7f3da-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span> <span data-ttu-id="7f3da-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span><span class="sxs-lookup"><span data-stu-id="7f3da-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="7f3da-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span><span class="sxs-lookup"><span data-stu-id="7f3da-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="7f3da-169">Portable (.NET Core 2.0 or later versions)</span><span class="sxs-lookup"><span data-stu-id="7f3da-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="7f3da-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu and derivatives)</span><span class="sxs-lookup"><span data-stu-id="7f3da-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu and derivatives)</span></span>
  - <span data-ttu-id="7f3da-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span><span class="sxs-lookup"><span data-stu-id="7f3da-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="7f3da-172">`linux-arm` (Linux distributions running on ARM like Raspberry Pi)</span><span class="sxs-lookup"><span data-stu-id="7f3da-172">`linux-arm` (Linux distributions running on ARM like Raspberry Pi)</span></span>
- <span data-ttu-id="7f3da-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="7f3da-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="7f3da-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span><span class="sxs-lookup"><span data-stu-id="7f3da-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="7f3da-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span><span class="sxs-lookup"><span data-stu-id="7f3da-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="7f3da-176">Tizen (.NET Core 2.0 or later versions)</span><span class="sxs-lookup"><span data-stu-id="7f3da-176">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="7f3da-177">See [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-linux) for more information.</span><span class="sxs-lookup"><span data-stu-id="7f3da-177">See [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-linux) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="7f3da-178">macOS RIDs</span><span class="sxs-lookup"><span data-stu-id="7f3da-178">macOS RIDs</span></span>

<span data-ttu-id="7f3da-179">macOS RIDs use the older "OSX" branding.</span><span class="sxs-lookup"><span data-stu-id="7f3da-179">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="7f3da-180">Only common values are listed.</span><span class="sxs-lookup"><span data-stu-id="7f3da-180">Only common values are listed.</span></span> <span data-ttu-id="7f3da-181">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span><span class="sxs-lookup"><span data-stu-id="7f3da-181">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

- <span data-ttu-id="7f3da-182">Portable (.NET Core 2.0 or later versions)</span><span class="sxs-lookup"><span data-stu-id="7f3da-182">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="7f3da-183">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="7f3da-183">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="7f3da-184">macOS 10.10  Yosemite</span><span class="sxs-lookup"><span data-stu-id="7f3da-184">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="7f3da-185">macOS 10.11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="7f3da-185">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="7f3da-186">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span><span class="sxs-lookup"><span data-stu-id="7f3da-186">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="7f3da-187">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span><span class="sxs-lookup"><span data-stu-id="7f3da-187">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="7f3da-188">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span><span class="sxs-lookup"><span data-stu-id="7f3da-188">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="7f3da-189">See [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-macos) for more information.</span><span class="sxs-lookup"><span data-stu-id="7f3da-189">See [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-macos) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f3da-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f3da-190">See also</span></span>

- [<span data-ttu-id="7f3da-191">Runtime IDs</span><span class="sxs-lookup"><span data-stu-id="7f3da-191">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/src/pkg/Microsoft.NETCore.Platforms/readme.md)
