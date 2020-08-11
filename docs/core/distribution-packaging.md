---
title: Vytváření distribučních balíčků .NET Core
description: Naučte se, jak zabalit, pojmenovat a verze .NET Core pro distribuci.
author: tmds
ms.date: 10/09/2019
ms.openlocfilehash: 3324a6a151fc6dc46a8f13ea17c89da99d108d82
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062883"
---
# <a name="net-core-distribution-packaging"></a><span data-ttu-id="12ec4-103">Vytváření distribučních balíčků .NET Core</span><span class="sxs-lookup"><span data-stu-id="12ec4-103">.NET Core distribution packaging</span></span>

<span data-ttu-id="12ec4-104">Rozhraní .NET Core bude k dispozici na více a více platformách. je vhodné se naučit, jak balíček, název a verzi.</span><span class="sxs-lookup"><span data-stu-id="12ec4-104">As .NET Core becomes available on more and more platforms, it's useful to learn how to package, name, and version it.</span></span> <span data-ttu-id="12ec4-105">Tímto způsobem můžou údržba balíčků pomáhat zajistit konzistentní prostředí bez ohledu na to, kde se uživatelé spouštějí .NET.</span><span class="sxs-lookup"><span data-stu-id="12ec4-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="12ec4-106">Tento článek je užitečný pro uživatele, kteří jsou:</span><span class="sxs-lookup"><span data-stu-id="12ec4-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="12ec4-107">Probíhá pokus o sestavení .NET Core ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="12ec4-107">Attempting to build .NET Core from source.</span></span>
- <span data-ttu-id="12ec4-108">Chcete provádět změny .NET Core CLI, které by mohly mít vliv na výsledné rozložení nebo vytvořené balíčky.</span><span class="sxs-lookup"><span data-stu-id="12ec4-108">Wanting to make changes to the .NET Core CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="12ec4-109">Rozložení disku</span><span class="sxs-lookup"><span data-stu-id="12ec4-109">Disk layout</span></span>

<span data-ttu-id="12ec4-110">Při instalaci nástroje .NET Core se skládá z několika součástí, které jsou v systému souborů uvedeny následovně:</span><span class="sxs-lookup"><span data-stu-id="12ec4-110">When installed, .NET Core consists of several components that are laid out as follows in the filesystem:</span></span>

```
{dotnet_root}                                     (*)
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host                                          (*)
│   └── fxr                                       (*)
│       └── <fxr version>        (2)
├── sdk                                           (*)
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)              (*)
├── packs                                         (*)
│   ├── Microsoft.AspNetCore.App.Ref              (*)
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref                 (*)
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>          (*)
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref          (*)
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref                   (*)
│       └── <netstandard version>        (15)
├── shared                                        (*)
│   ├── Microsoft.NETCore.App                     (*)
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App                  (*)
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All                  (*)
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App              (*)
│       └── <desktop app version> (7)
└── templates                                     (*)
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="12ec4-111">(1) **dotnet** hostitel (označovaný také jako "muxer") má dvě odlišné role: aktivujte modul runtime pro spuštění aplikace a aktivujte sadu SDK k odeslání příkazů do ní.</span><span class="sxs-lookup"><span data-stu-id="12ec4-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="12ec4-112">Hostitel je nativní spustitelný soubor ( `dotnet.exe` ).</span><span class="sxs-lookup"><span data-stu-id="12ec4-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="12ec4-113">I když existuje jeden hostitel, většina ostatních komponent je v adresářích se správou verzí (2, 3, 5, 6).</span><span class="sxs-lookup"><span data-stu-id="12ec4-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="12ec4-114">To znamená, že v systému může být k dispozici více verzí, protože jsou nainstalovány vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="12ec4-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="12ec4-115">(2) \*\*hostitel/FXR/ \<fxr version> \*\* obsahuje logiku překladu rozhraní, kterou používá hostitel.</span><span class="sxs-lookup"><span data-stu-id="12ec4-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="12ec4-116">Hostitel používá nejnovější hostfxr, která je nainstalována.</span><span class="sxs-lookup"><span data-stu-id="12ec4-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="12ec4-117">Hostfxr zodpovídá za výběr vhodného modulu runtime při spouštění aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12ec4-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET Core application.</span></span> <span data-ttu-id="12ec4-118">Například aplikace sestavená pro .NET Core 2.0.0 používá modul runtime 2.0.5, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="12ec4-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="12ec4-119">Podobně hostfxr vybere vhodnou sadu SDK během vývoje.</span><span class="sxs-lookup"><span data-stu-id="12ec4-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="12ec4-120">(3) **sada SDK \<sdk version> /** sada SDK (označovaná také jako "nástroje") je sada spravovaných nástrojů, které se používají k psaní a vytváření knihoven a aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12ec4-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET Core libraries and applications.</span></span> <span data-ttu-id="12ec4-121">Sada SDK obsahuje .NET Core CLI, kompilátory spravovaných jazyků, MSBuild a přidružené úlohy a cíle sestavení, NuGet, nové šablony projektů a tak dále.</span><span class="sxs-lookup"><span data-stu-id="12ec4-121">The SDK includes the .NET Core CLI, the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="12ec4-122">(4) **sada SDK/NuGetFallbackFolder** obsahuje mezipaměť balíčků NuGet, které sada SDK používá během operace obnovení, například při spuštění `dotnet restore` nebo `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="12ec4-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build`.</span></span> <span data-ttu-id="12ec4-123">Tato složka se používá pouze před rozhraním .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="12ec4-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="12ec4-124">Nemůže být sestaven ze zdroje, protože obsahuje předem sestavené binární prostředky z `nuget.org` .</span><span class="sxs-lookup"><span data-stu-id="12ec4-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="12ec4-125">**Sdílená** složka obsahuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="12ec4-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="12ec4-126">Sdílené rozhraní poskytuje sadu knihoven v centrálním umístění, aby mohly být používány různými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="12ec4-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="12ec4-127">(5) **Shared/Microsoft. NETCore. app \<runtime version> /** this Framework obsahuje modul runtime .NET Core a podporu spravovaných knihoven.</span><span class="sxs-lookup"><span data-stu-id="12ec4-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET Core runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="12ec4-128">(6) \*\*Shared/Microsoft. AspNetCore. { App, All}/ \<aspnetcore version> \*\* obsahuje knihovny ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="12ec4-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="12ec4-129">Knihovny `Microsoft.AspNetCore.App` jsou vyvíjeny a podporovány v rámci projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12ec4-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET Core project.</span></span> <span data-ttu-id="12ec4-130">Knihovny jsou v oblasti `Microsoft.AspNetCore.All` nadmnožinou, které také obsahují knihovny třetích stran.</span><span class="sxs-lookup"><span data-stu-id="12ec4-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="12ec4-131">(7) **Shared/Microsoft. Desktop. app \<desktop app version> /** obsahuje knihovny desktopů Windows.</span><span class="sxs-lookup"><span data-stu-id="12ec4-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="12ec4-132">Tato součást není zahrnutá na platformách jiných než Windows.</span><span class="sxs-lookup"><span data-stu-id="12ec4-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="12ec4-133">(8) **LICENSE.txt ThirdPartyNotices.txt** jsou licence .NET Core a licence knihoven třetích stran používané v rozhraní .NET Core v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="12ec4-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET Core license and licenses of third-party libraries used in .NET Core, respectively.</span></span>

- <span data-ttu-id="12ec4-134">(9, 10) **dotnet. 1. gz, dotnet** `dotnet.1.gz` je ruční stránka dotnet.</span><span class="sxs-lookup"><span data-stu-id="12ec4-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="12ec4-135">`dotnet`je symlink na hostitele dotnet (1).</span><span class="sxs-lookup"><span data-stu-id="12ec4-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="12ec4-136">Tyto soubory jsou nainstalovány ve známých umístěních pro integraci systému.</span><span class="sxs-lookup"><span data-stu-id="12ec4-136">These files are installed at well-known locations for system integration.</span></span>

- <span data-ttu-id="12ec4-137">(11.12) **Microsoft. NETCore. app. ref, Microsoft. AspNetCore. app. ref** popisují rozhraní API `x.y` verze .net Core a ASP.NET Core v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="12ec4-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET Core and ASP.NET Core respectively.</span></span> <span data-ttu-id="12ec4-138">Tyto sady jsou používány při kompilování pro tyto cílové verze.</span><span class="sxs-lookup"><span data-stu-id="12ec4-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="12ec4-139">(13) \*\*Microsoft. NETCore. app. Host. \<rid> \*\*</span><span class="sxs-lookup"><span data-stu-id="12ec4-139">(13) **Microsoft.NETCore.App.Host.\<rid>**</span></span> <span data-ttu-id="12ec4-140">obsahuje nativní binární soubor pro platformu `rid` .</span><span class="sxs-lookup"><span data-stu-id="12ec4-140">contains a native binary for platform `rid`.</span></span> <span data-ttu-id="12ec4-141">Tento binární soubor je šablonou při kompilování aplikace .NET Core do nativního binárního souboru pro danou platformu.</span><span class="sxs-lookup"><span data-stu-id="12ec4-141">This binary is a template when compiling a .NET Core application into a native binary for that platform.</span></span>

- <span data-ttu-id="12ec4-142">(14) **Microsoft. WindowsDesktop. app. ref** popisuje rozhraní API `x.y` aplikací klasické pracovní plochy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="12ec4-142">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="12ec4-143">Tyto soubory se používají při kompilování pro daný cíl.</span><span class="sxs-lookup"><span data-stu-id="12ec4-143">These files are used when compiling for that target.</span></span> <span data-ttu-id="12ec4-144">Tento příkaz není k dispozici na platformách jiných než Windows.</span><span class="sxs-lookup"><span data-stu-id="12ec4-144">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="12ec4-145">(15) **NETStandard. Library. ref** popisuje rozhraní NETStandard `x.y` API.</span><span class="sxs-lookup"><span data-stu-id="12ec4-145">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="12ec4-146">Tyto soubory se používají při kompilování pro daný cíl.</span><span class="sxs-lookup"><span data-stu-id="12ec4-146">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="12ec4-147">(16) **/etc/dotnet/install_location** je soubor, který obsahuje úplnou cestu pro `{dotnet_root}` .</span><span class="sxs-lookup"><span data-stu-id="12ec4-147">(16) **/etc/dotnet/install_location** is a file that contains the full path for `{dotnet_root}`.</span></span> <span data-ttu-id="12ec4-148">Cesta může končit novým řádkem.</span><span class="sxs-lookup"><span data-stu-id="12ec4-148">The path may end with a newline.</span></span> <span data-ttu-id="12ec4-149">Není nutné přidávat tento soubor, pokud je kořenový adresář `/usr/share/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="12ec4-149">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="12ec4-150">(17) **šablony** obsahují šablony používané sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="12ec4-150">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="12ec4-151">Například `dotnet new` vyhledá šablony projektu zde.</span><span class="sxs-lookup"><span data-stu-id="12ec4-151">For example, `dotnet new` finds project templates here.</span></span>

<span data-ttu-id="12ec4-152">Složky označené pomocí `(*)` jsou používány více balíčky.</span><span class="sxs-lookup"><span data-stu-id="12ec4-152">The folders marked with `(*)` are used by multiple packages.</span></span> <span data-ttu-id="12ec4-153">Některé formáty balíčků (například `rpm` ) vyžadují speciální zpracování těchto složek.</span><span class="sxs-lookup"><span data-stu-id="12ec4-153">Some package formats (for example, `rpm`) require special handling of such folders.</span></span> <span data-ttu-id="12ec4-154">Je potřeba, aby se tento balíček na starosti.</span><span class="sxs-lookup"><span data-stu-id="12ec4-154">The package maintainer must take care of this.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="12ec4-155">Doporučené balíčky</span><span class="sxs-lookup"><span data-stu-id="12ec4-155">Recommended packages</span></span>

<span data-ttu-id="12ec4-156">Verze .NET Core je založena na `[major].[minor]` číslech verzí komponenty modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="12ec4-156">.NET Core versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="12ec4-157">Verze SDK používá stejný `[major].[minor]` a má nezávisle `[patch]` , která kombinuje sémantiku funkcí a oprav pro sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="12ec4-157">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="12ec4-158">Například: SDK Version 2.2.302 je druhá verze verze sady SDK pro třetí funkce, která podporuje modul runtime 2,2.</span><span class="sxs-lookup"><span data-stu-id="12ec4-158">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="12ec4-159">Další informace o tom, jak funguje Správa verzí, najdete v tématu [Přehled verzí .NET Core](./versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="12ec4-159">For more information about how versioning works, see [.NET Core versioning overview](./versions/index.md).</span></span>

<span data-ttu-id="12ec4-160">Některé balíčky obsahují část čísla verze v názvu.</span><span class="sxs-lookup"><span data-stu-id="12ec4-160">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="12ec4-161">To vám umožní nainstalovat určitou verzi.</span><span class="sxs-lookup"><span data-stu-id="12ec4-161">This allows you to install a specific version.</span></span>
<span data-ttu-id="12ec4-162">Zbytek verze není zahrnutý v názvu verze.</span><span class="sxs-lookup"><span data-stu-id="12ec4-162">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="12ec4-163">Správce balíčků operačního systému tak může aktualizovat balíčky (například automaticky instalovat opravy zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="12ec4-163">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="12ec4-164">Podporovaní správci balíčků jsou specifická pro Linux.</span><span class="sxs-lookup"><span data-stu-id="12ec4-164">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="12ec4-165">Následující seznam obsahuje doporučené balíčky:</span><span class="sxs-lookup"><span data-stu-id="12ec4-165">The following lists the recommended packages:</span></span>

- <span data-ttu-id="12ec4-166">`dotnet-sdk-[major].[minor]`– Nainstaluje nejnovější sadu SDK pro konkrétní modul runtime.</span><span class="sxs-lookup"><span data-stu-id="12ec4-166">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="12ec4-167">**Verze:**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="12ec4-167">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="12ec4-168">**Příklad:** dotnet-sdk-2,1</span><span class="sxs-lookup"><span data-stu-id="12ec4-168">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="12ec4-169">**Obsahuje:** (3), (4)</span><span class="sxs-lookup"><span data-stu-id="12ec4-169">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="12ec4-170">**Závislosti:** `dotnet-runtime-[major].[minor]` , `aspnetcore-runtime-[major].[minor]` , `dotnet-targeting-pack-[major].[minor]` , `aspnetcore-targeting-pack-[major].[minor]` , `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` , `dotnet-apphost-pack-[major].[minor]` ,`dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="12ec4-170">**Dependencies:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="12ec4-171">`aspnetcore-runtime-[major].[minor]`– Nainstaluje konkrétní modul runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="12ec4-171">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="12ec4-172">**Verze:**\<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="12ec4-172">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="12ec4-173">**Příklad:** aspnetcore-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="12ec4-173">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="12ec4-174">**Obsahuje:** (6)</span><span class="sxs-lookup"><span data-stu-id="12ec4-174">**Contains:** (6)</span></span>
  - <span data-ttu-id="12ec4-175">**Závislosti:**`dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="12ec4-175">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="12ec4-176">`dotnet-runtime-deps-[major].[minor]`_(Volitelné)_ – nainstaluje závislosti pro spouštění aplikací, které jsou součástí sebe.</span><span class="sxs-lookup"><span data-stu-id="12ec4-176">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="12ec4-177">**Verze:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="12ec4-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="12ec4-178">**Příklad:** dotnet-runtime-deps-2,1</span><span class="sxs-lookup"><span data-stu-id="12ec4-178">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="12ec4-179">**Závislosti:** _závislosti specifické pro distribuci_</span><span class="sxs-lookup"><span data-stu-id="12ec4-179">**Dependencies:** _distribution-specific dependencies_</span></span>

- <span data-ttu-id="12ec4-180">`dotnet-runtime-[major].[minor]`– Nainstaluje konkrétní modul runtime.</span><span class="sxs-lookup"><span data-stu-id="12ec4-180">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="12ec4-181">**Verze:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="12ec4-181">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="12ec4-182">**Příklad:** dotnet-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="12ec4-182">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="12ec4-183">**Obsahuje:** (5)</span><span class="sxs-lookup"><span data-stu-id="12ec4-183">**Contains:** (5)</span></span>
  - <span data-ttu-id="12ec4-184">**Závislosti:** `dotnet-hostfxr-[major].[minor]` ,`dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="12ec4-184">**Dependencies:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="12ec4-185">`dotnet-hostfxr-[major].[minor]`-Dependency</span><span class="sxs-lookup"><span data-stu-id="12ec4-185">`dotnet-hostfxr-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="12ec4-186">**Verze:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="12ec4-186">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="12ec4-187">**Příklad:** dotnet-hostfxr-3,0</span><span class="sxs-lookup"><span data-stu-id="12ec4-187">**Example:** dotnet-hostfxr-3.0</span></span>
  - <span data-ttu-id="12ec4-188">**Obsahuje:** (2)</span><span class="sxs-lookup"><span data-stu-id="12ec4-188">**Contains:** (2)</span></span>
  - <span data-ttu-id="12ec4-189">**Závislosti:**`dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="12ec4-189">**Dependencies:** `dotnet-host`</span></span>

- <span data-ttu-id="12ec4-190">`dotnet-host`-Dependency</span><span class="sxs-lookup"><span data-stu-id="12ec4-190">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="12ec4-191">**Verze:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="12ec4-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="12ec4-192">**Příklad:** dotnet-Host</span><span class="sxs-lookup"><span data-stu-id="12ec4-192">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="12ec4-193">**Obsahuje:** (1), (8), (9), (10), (16)</span><span class="sxs-lookup"><span data-stu-id="12ec4-193">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="12ec4-194">`dotnet-apphost-pack-[major].[minor]`-Dependency</span><span class="sxs-lookup"><span data-stu-id="12ec4-194">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="12ec4-195">**Verze:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="12ec4-195">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="12ec4-196">**Obsahuje:** (13)</span><span class="sxs-lookup"><span data-stu-id="12ec4-196">**Contains:** (13)</span></span>

- <span data-ttu-id="12ec4-197">`dotnet-targeting-pack-[major].[minor]`– Umožňuje zaměřit se na nenejnovější modul runtime.</span><span class="sxs-lookup"><span data-stu-id="12ec4-197">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="12ec4-198">**Verze:**\<runtime version></span><span class="sxs-lookup"><span data-stu-id="12ec4-198">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="12ec4-199">**Obsahuje:** (12)</span><span class="sxs-lookup"><span data-stu-id="12ec4-199">**Contains:** (12)</span></span>

- <span data-ttu-id="12ec4-200">`aspnetcore-targeting-pack-[major].[minor]`– Umožňuje zaměřit se na nenejnovější modul runtime.</span><span class="sxs-lookup"><span data-stu-id="12ec4-200">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="12ec4-201">**Verze:**\<aspnetcore runtime version></span><span class="sxs-lookup"><span data-stu-id="12ec4-201">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="12ec4-202">**Obsahuje:** (11)</span><span class="sxs-lookup"><span data-stu-id="12ec4-202">**Contains:** (11)</span></span>

- <span data-ttu-id="12ec4-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`– Povoluje cílení na verzi netstandard</span><span class="sxs-lookup"><span data-stu-id="12ec4-203">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="12ec4-204">**Verze:**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="12ec4-204">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="12ec4-205">**Obsahuje:** (15)</span><span class="sxs-lookup"><span data-stu-id="12ec4-205">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="12ec4-206">**Verze:**\<sdk version></span><span class="sxs-lookup"><span data-stu-id="12ec4-206">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="12ec4-207">**Obsahuje:** (15)</span><span class="sxs-lookup"><span data-stu-id="12ec4-207">**Contains:** (15)</span></span>

<span data-ttu-id="12ec4-208">`dotnet-runtime-deps-[major].[minor]`Vyžaduje porozumění _závislostem specifickým pro distribuce_.</span><span class="sxs-lookup"><span data-stu-id="12ec4-208">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro-specific dependencies_.</span></span> <span data-ttu-id="12ec4-209">Vzhledem k tomu, že systém sestavení distribuce může být schopný tuto hodnotu automaticky odvodit, balíček je volitelný. v takovém případě se tyto závislosti přidávají přímo do `dotnet-runtime-[major].[minor]` balíčku.</span><span class="sxs-lookup"><span data-stu-id="12ec4-209">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="12ec4-210">Když je obsah balíčku ve složce se správou verzí, název balíčku se `[major].[minor]` shoduje s názvem složky se správou verzí.</span><span class="sxs-lookup"><span data-stu-id="12ec4-210">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="12ec4-211">Pro všechny balíčky s výjimkou `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` , to se také shoduje s verzí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12ec4-211">For all packages, except the `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, this also matches with the .NET Core version.</span></span>

<span data-ttu-id="12ec4-212">Závislosti mezi balíčky by měly používat požadavek _rovnající se nebo vyšší_ verze.</span><span class="sxs-lookup"><span data-stu-id="12ec4-212">Dependencies between packages should use an _equal or greater than_ version requirement.</span></span> <span data-ttu-id="12ec4-213">Například `dotnet-sdk-2.2:2.2.401` vyžaduje `aspnetcore-runtime-2.2 >= 2.2.6` .</span><span class="sxs-lookup"><span data-stu-id="12ec4-213">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="12ec4-214">Díky tomu může uživatel upgradovat svou instalaci prostřednictvím kořenového balíčku (například `dnf update dotnet-sdk-2.2` ).</span><span class="sxs-lookup"><span data-stu-id="12ec4-214">This makes it possible for the user to upgrade their installation via a root package (for example, `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="12ec4-215">Většina distribucí vyžaduje, aby všechny artefakty byly sestaveny ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="12ec4-215">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="12ec4-216">To má nějaký dopad na balíčky:</span><span class="sxs-lookup"><span data-stu-id="12ec4-216">This has some impact on the packages:</span></span>

- <span data-ttu-id="12ec4-217">Knihovny třetích stran v části `shared/Microsoft.AspNetCore.All` nejde snadno sestavit ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="12ec4-217">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="12ec4-218">Takže se složka z balíčku vynechá `aspnetcore-runtime` .</span><span class="sxs-lookup"><span data-stu-id="12ec4-218">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="12ec4-219">`NuGetFallbackFolder`Je naplněno pomocí binárních artefaktů z `nuget.org` .</span><span class="sxs-lookup"><span data-stu-id="12ec4-219">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="12ec4-220">Měla by zůstat prázdná.</span><span class="sxs-lookup"><span data-stu-id="12ec4-220">It should remain empty.</span></span>

<span data-ttu-id="12ec4-221">Více `dotnet-sdk` balíčků může poskytovat stejné soubory pro `NuGetFallbackFolder` .</span><span class="sxs-lookup"><span data-stu-id="12ec4-221">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="12ec4-222">Aby se zabránilo problémům se správcem balíčků, měly by být tyto soubory stejné (kontrolní součet, datum změny atd.).</span><span class="sxs-lookup"><span data-stu-id="12ec4-222">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="12ec4-223">Vytváření balíčků</span><span class="sxs-lookup"><span data-stu-id="12ec4-223">Building packages</span></span>

<span data-ttu-id="12ec4-224">Úložiště [dotnet/source-Build](https://github.com/dotnet/source-build) poskytuje pokyny pro sestavení zdrojové tarballu .NET Core SDK a všech jeho součástí.</span><span class="sxs-lookup"><span data-stu-id="12ec4-224">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET Core SDK and all its components.</span></span> <span data-ttu-id="12ec4-225">Výstup úložiště zdrojového sestavení odpovídá rozložení popsanému v první části tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="12ec4-225">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
