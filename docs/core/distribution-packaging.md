---
title: Vytváření distribučních balíčků .NET Core
description: Naučte se, jak zabalit, pojmenovat a verze .NET Core pro distribuci.
author: tmds
ms.date: 10/09/2019
ms.openlocfilehash: 1b5adf761a51e006f8309e1f326fc0a9c12aab7a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76748501"
---
# <a name="net-core-distribution-packaging"></a><span data-ttu-id="81c96-103">Vytváření distribučních balíčků .NET Core</span><span class="sxs-lookup"><span data-stu-id="81c96-103">.NET Core distribution packaging</span></span>

<span data-ttu-id="81c96-104">Rozhraní .NET Core bude k dispozici na více a více platformách. je vhodné se naučit, jak balíček, název a verzi.</span><span class="sxs-lookup"><span data-stu-id="81c96-104">As .NET Core becomes available on more and more platforms, it's useful to learn how to package, name, and version it.</span></span> <span data-ttu-id="81c96-105">Tímto způsobem můžou údržba balíčků pomáhat zajistit konzistentní prostředí bez ohledu na to, kde se uživatelé spouštějí .NET.</span><span class="sxs-lookup"><span data-stu-id="81c96-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="81c96-106">Tento článek je užitečný pro uživatele, kteří jsou:</span><span class="sxs-lookup"><span data-stu-id="81c96-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="81c96-107">Probíhá pokus o sestavení .NET Core ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="81c96-107">Attempting to build .NET Core from source.</span></span>
- <span data-ttu-id="81c96-108">Chcete provádět změny .NET Core CLI, které by mohly mít vliv na výsledné rozložení nebo vytvořené balíčky.</span><span class="sxs-lookup"><span data-stu-id="81c96-108">Wanting to make changes to the .NET Core CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="81c96-109">Rozložení disku</span><span class="sxs-lookup"><span data-stu-id="81c96-109">Disk layout</span></span>

<span data-ttu-id="81c96-110">Při instalaci nástroje .NET Core se skládá z několika součástí, které jsou v systému souborů uvedeny následovně:</span><span class="sxs-lookup"><span data-stu-id="81c96-110">When installed, .NET Core consists of several components that are laid out as follows in the filesystem:</span></span>

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

- <span data-ttu-id="81c96-111">(1) **dotnet** hostitel (označovaný také jako "muxer") má dvě odlišné role: aktivujte modul runtime pro spuštění aplikace a aktivujte sadu SDK k odeslání příkazů do ní.</span><span class="sxs-lookup"><span data-stu-id="81c96-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="81c96-112">Hostitel je nativní spustitelný soubor (`dotnet.exe`).</span><span class="sxs-lookup"><span data-stu-id="81c96-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="81c96-113">I když existuje jeden hostitel, většina ostatních komponent je v adresářích se správou verzí (2, 3, 5, 6).</span><span class="sxs-lookup"><span data-stu-id="81c96-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="81c96-114">To znamená, že v systému může být k dispozici více verzí, protože jsou nainstalovány vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="81c96-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="81c96-115">(2) **hostitel/FXR/\<FXR verze >** obsahuje logiku překladu rozhraní, kterou používá hostitel.</span><span class="sxs-lookup"><span data-stu-id="81c96-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="81c96-116">Hostitel používá nejnovější hostfxr, která je nainstalována.</span><span class="sxs-lookup"><span data-stu-id="81c96-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="81c96-117">Hostfxr zodpovídá za výběr vhodného modulu runtime při spouštění aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="81c96-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET Core application.</span></span> <span data-ttu-id="81c96-118">Například aplikace sestavená pro .NET Core 2.0.0 používá modul runtime 2.0.5, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="81c96-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="81c96-119">Podobně hostfxr vybere vhodnou sadu SDK během vývoje.</span><span class="sxs-lookup"><span data-stu-id="81c96-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="81c96-120">(3) sada SDK **/\<SDK verze >** sada SDK (označovaná také jako "nástroje") je sada spravovaných nástrojů, které se používají k psaní a vytváření knihoven a aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="81c96-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET Core libraries and applications.</span></span> <span data-ttu-id="81c96-121">Sada SDK obsahuje rozhraní příkazového řádku (CLI) .NET Core, kompilátory spravovaných jazyků, MSBuild a přidružené úlohy a cíle sestavení, NuGet, nové šablony projektů a tak dále.</span><span class="sxs-lookup"><span data-stu-id="81c96-121">The SDK includes the .NET Core Command-line interface (CLI), the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="81c96-122">(4) **sada SDK/NuGetFallbackFolder** obsahuje mezipaměť balíčků NuGet, které sada SDK používá během operace obnovení, například při spuštění `dotnet restore` nebo `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="81c96-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build`.</span></span> <span data-ttu-id="81c96-123">Tato složka se používá pouze před rozhraním .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="81c96-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="81c96-124">Nemůže být sestaven ze zdroje, protože obsahuje předem sestavené binární prostředky z `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="81c96-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="81c96-125">**Sdílená** složka obsahuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="81c96-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="81c96-126">Sdílené rozhraní poskytuje sadu knihoven v centrálním umístění, aby mohly být používány různými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="81c96-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="81c96-127">(5) **Shared/Microsoft. NETCore. app/\<runtime verze >** tato architektura obsahuje modul runtime .NET Core a podporu spravovaných knihoven.</span><span class="sxs-lookup"><span data-stu-id="81c96-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET Core runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="81c96-128">(6) **Shared/Microsoft. AspNetCore. { App, All}/\<aspnetcore verze >** obsahuje knihovny ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="81c96-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="81c96-129">Knihovny v rámci `Microsoft.AspNetCore.App` jsou vyvíjeny a podporovány v rámci projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="81c96-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET Core project.</span></span> <span data-ttu-id="81c96-130">Knihovny v rámci `Microsoft.AspNetCore.All` jsou nadmnožinou, která také obsahuje knihovny třetích stran.</span><span class="sxs-lookup"><span data-stu-id="81c96-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="81c96-131">(7) **sdílená aplikace/aplikace Microsoft. Desktop. app/\<desktop >** obsahuje knihovny desktopů Windows.</span><span class="sxs-lookup"><span data-stu-id="81c96-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="81c96-132">Tato součást není zahrnutá na platformách jiných než Windows.</span><span class="sxs-lookup"><span data-stu-id="81c96-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="81c96-133">(8) **License. txt, ThirdPartyNotices. txt** jsou licence .NET Core a licence knihoven třetích stran používané v .NET Core v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="81c96-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET Core license and licenses of third-party libraries used in .NET Core, respectively.</span></span>

- <span data-ttu-id="81c96-134">(9, 10) **dotnet. 1. gz, dotnet** `dotnet.1.gz` je ruční stránka dotnet.</span><span class="sxs-lookup"><span data-stu-id="81c96-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="81c96-135">`dotnet` je symlink na hostitele dotnet (1).</span><span class="sxs-lookup"><span data-stu-id="81c96-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="81c96-136">Tyto soubory jsou nainstalovány ve známých umístěních pro integraci systému.</span><span class="sxs-lookup"><span data-stu-id="81c96-136">These files are installed at well-known locations for system integration.</span></span>

- <span data-ttu-id="81c96-137">(11.12) **Microsoft. NETCore. app. ref, Microsoft. AspNetCore. app. ref** popisují rozhraní API `x.y` verze rozhraní .NET Core a ASP.NET Core v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="81c96-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET Core and ASP.NET Core respectively.</span></span> <span data-ttu-id="81c96-138">Tyto sady jsou používány při kompilování pro tyto cílové verze.</span><span class="sxs-lookup"><span data-stu-id="81c96-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="81c96-139">(13) **Microsoft. NETCore. app. Host.\<rid >** obsahuje nativní binární soubor pro `rid`platformy.</span><span class="sxs-lookup"><span data-stu-id="81c96-139">(13) **Microsoft.NETCore.App.Host.\<rid>** contains a native binary for platform `rid`.</span></span> <span data-ttu-id="81c96-140">Tento binární soubor je šablonou při kompilování aplikace .NET Core do nativního binárního souboru pro danou platformu.</span><span class="sxs-lookup"><span data-stu-id="81c96-140">This binary is a template when compiling a .NET Core application into a native binary for that platform.</span></span>

- <span data-ttu-id="81c96-141">(14) **Microsoft. WindowsDesktop. app. ref** popisuje rozhraní API `x.y`ch aplikací pro stolní počítače s Windows.</span><span class="sxs-lookup"><span data-stu-id="81c96-141">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="81c96-142">Tyto soubory se používají při kompilování pro daný cíl.</span><span class="sxs-lookup"><span data-stu-id="81c96-142">These files are used when compiling for that target.</span></span> <span data-ttu-id="81c96-143">Tento příkaz není k dispozici na platformách jiných než Windows.</span><span class="sxs-lookup"><span data-stu-id="81c96-143">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="81c96-144">(15) **NETStandard. Library. ref** popisuje rozhraní API pro NETStandard `x.y`.</span><span class="sxs-lookup"><span data-stu-id="81c96-144">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="81c96-145">Tyto soubory se používají při kompilování pro daný cíl.</span><span class="sxs-lookup"><span data-stu-id="81c96-145">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="81c96-146">(16) **/etc/dotnet/install_location** je soubor, který obsahuje úplnou cestu pro `{dotnet_root}`.</span><span class="sxs-lookup"><span data-stu-id="81c96-146">(16) **/etc/dotnet/install_location** is a file that contains the full path for `{dotnet_root}`.</span></span> <span data-ttu-id="81c96-147">Cesta může končit novým řádkem.</span><span class="sxs-lookup"><span data-stu-id="81c96-147">The path may end with a newline.</span></span> <span data-ttu-id="81c96-148">Tento soubor není nutné přidávat, pokud je kořenový `/usr/share/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="81c96-148">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="81c96-149">(17) **šablony** obsahují šablony používané sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="81c96-149">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="81c96-150">`dotnet new` například vyhledá šablony projektu.</span><span class="sxs-lookup"><span data-stu-id="81c96-150">For example, `dotnet new` finds project templates here.</span></span>

<span data-ttu-id="81c96-151">Složky označené `(*)` jsou používány více balíčky.</span><span class="sxs-lookup"><span data-stu-id="81c96-151">The folders marked with `(*)` are used by multiple packages.</span></span> <span data-ttu-id="81c96-152">Některé formáty balíčků (například `rpm`) vyžadují speciální zpracování těchto složek.</span><span class="sxs-lookup"><span data-stu-id="81c96-152">Some package formats (for example, `rpm`) require special handling of such folders.</span></span> <span data-ttu-id="81c96-153">Je potřeba, aby se tento balíček na starosti.</span><span class="sxs-lookup"><span data-stu-id="81c96-153">The package maintainer must take care of this.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="81c96-154">Doporučené balíčky</span><span class="sxs-lookup"><span data-stu-id="81c96-154">Recommended packages</span></span>

<span data-ttu-id="81c96-155">Verze .NET Core je založená na komponentách modulu runtime `[major].[minor]` číslech verzí.</span><span class="sxs-lookup"><span data-stu-id="81c96-155">.NET Core versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="81c96-156">Verze SDK používá stejný `[major].[minor]` a má nezávislou `[patch]`, která kombinuje sémantiku funkcí a oprav pro sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="81c96-156">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="81c96-157">Například: SDK Version 2.2.302 je druhá verze verze sady SDK pro třetí funkce, která podporuje modul runtime 2,2.</span><span class="sxs-lookup"><span data-stu-id="81c96-157">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="81c96-158">Další informace o tom, jak funguje Správa verzí, najdete v tématu [Přehled verzí .NET Core](./versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="81c96-158">For more information about how versioning works, see [.NET Core versioning overview](./versions/index.md).</span></span>

<span data-ttu-id="81c96-159">Některé balíčky obsahují část čísla verze v názvu.</span><span class="sxs-lookup"><span data-stu-id="81c96-159">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="81c96-160">To vám umožní nainstalovat určitou verzi.</span><span class="sxs-lookup"><span data-stu-id="81c96-160">This allows you to install a specific version.</span></span>
<span data-ttu-id="81c96-161">Zbytek verze není zahrnutý v názvu verze.</span><span class="sxs-lookup"><span data-stu-id="81c96-161">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="81c96-162">Správce balíčků operačního systému tak může aktualizovat balíčky (například automaticky instalovat opravy zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="81c96-162">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="81c96-163">Podporovaní správci balíčků jsou specifická pro Linux.</span><span class="sxs-lookup"><span data-stu-id="81c96-163">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="81c96-164">Následující seznam obsahuje doporučené balíčky:</span><span class="sxs-lookup"><span data-stu-id="81c96-164">The following lists the recommended packages:</span></span>

- <span data-ttu-id="81c96-165">`dotnet-sdk-[major].[minor]` – nainstaluje nejnovější sadu SDK pro konkrétní modul runtime.</span><span class="sxs-lookup"><span data-stu-id="81c96-165">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="81c96-166">**Verze:** \<runtime verze ></span><span class="sxs-lookup"><span data-stu-id="81c96-166">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="81c96-167">**Příklad:** dotnet-sdk-2,1</span><span class="sxs-lookup"><span data-stu-id="81c96-167">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="81c96-168">**Obsahuje:** (3), (4)</span><span class="sxs-lookup"><span data-stu-id="81c96-168">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="81c96-169">**Závislosti:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="81c96-169">**Dependencies:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="81c96-170">`aspnetcore-runtime-[major].[minor]` – nainstaluje konkrétní modul runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="81c96-170">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="81c96-171">**Verze:** \<aspnetcore verze modulu runtime ></span><span class="sxs-lookup"><span data-stu-id="81c96-171">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="81c96-172">**Příklad:** aspnetcore-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="81c96-172">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="81c96-173">**Obsahuje:** (6)</span><span class="sxs-lookup"><span data-stu-id="81c96-173">**Contains:** (6)</span></span>
  - <span data-ttu-id="81c96-174">**Závislosti:** `dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="81c96-174">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="81c96-175">`dotnet-runtime-deps-[major].[minor]` _(volitelné)_ – nainstaluje závislosti pro spouštění aplikací, které jsou v samostatném kontejneru.</span><span class="sxs-lookup"><span data-stu-id="81c96-175">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="81c96-176">**Verze:** \<runtime verze ></span><span class="sxs-lookup"><span data-stu-id="81c96-176">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="81c96-177">**Příklad:** dotnet-runtime-deps-2,1</span><span class="sxs-lookup"><span data-stu-id="81c96-177">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="81c96-178">**Závislosti:** _závislosti specifické pro distribuci_</span><span class="sxs-lookup"><span data-stu-id="81c96-178">**Dependencies:** _distribution-specific dependencies_</span></span>

- <span data-ttu-id="81c96-179">`dotnet-runtime-[major].[minor]` – nainstaluje konkrétní modul runtime.</span><span class="sxs-lookup"><span data-stu-id="81c96-179">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="81c96-180">**Verze:** \<runtime verze ></span><span class="sxs-lookup"><span data-stu-id="81c96-180">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="81c96-181">**Příklad:** dotnet-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="81c96-181">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="81c96-182">**Obsahuje:** (5)</span><span class="sxs-lookup"><span data-stu-id="81c96-182">**Contains:** (5)</span></span>
  - <span data-ttu-id="81c96-183">**Závislosti:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="81c96-183">**Dependencies:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="81c96-184">`dotnet-hostfxr-[major].[minor]` – závislost</span><span class="sxs-lookup"><span data-stu-id="81c96-184">`dotnet-hostfxr-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="81c96-185">**Verze:** \<runtime verze ></span><span class="sxs-lookup"><span data-stu-id="81c96-185">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="81c96-186">**Příklad:** dotnet-hostfxr-3,0</span><span class="sxs-lookup"><span data-stu-id="81c96-186">**Example:** dotnet-hostfxr-3.0</span></span>
  - <span data-ttu-id="81c96-187">**Obsahuje:** (2)</span><span class="sxs-lookup"><span data-stu-id="81c96-187">**Contains:** (2)</span></span>
  - <span data-ttu-id="81c96-188">**Závislosti:** `dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="81c96-188">**Dependencies:** `dotnet-host`</span></span>

- <span data-ttu-id="81c96-189">`dotnet-host` – závislost</span><span class="sxs-lookup"><span data-stu-id="81c96-189">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="81c96-190">**Verze:** \<runtime verze ></span><span class="sxs-lookup"><span data-stu-id="81c96-190">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="81c96-191">**Příklad:** dotnet-Host</span><span class="sxs-lookup"><span data-stu-id="81c96-191">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="81c96-192">**Obsahuje:** (1), (8), (9), (10), (16)</span><span class="sxs-lookup"><span data-stu-id="81c96-192">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="81c96-193">`dotnet-apphost-pack-[major].[minor]` – závislost</span><span class="sxs-lookup"><span data-stu-id="81c96-193">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="81c96-194">**Verze:** \<runtime verze ></span><span class="sxs-lookup"><span data-stu-id="81c96-194">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="81c96-195">**Obsahuje:** (13)</span><span class="sxs-lookup"><span data-stu-id="81c96-195">**Contains:** (13)</span></span>

- <span data-ttu-id="81c96-196">`dotnet-targeting-pack-[major].[minor]` – umožňuje zaměřit se na nenejnovější modul runtime.</span><span class="sxs-lookup"><span data-stu-id="81c96-196">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="81c96-197">**Verze:** \<runtime verze ></span><span class="sxs-lookup"><span data-stu-id="81c96-197">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="81c96-198">**Obsahuje:** (12)</span><span class="sxs-lookup"><span data-stu-id="81c96-198">**Contains:** (12)</span></span>

- <span data-ttu-id="81c96-199">`aspnetcore-targeting-pack-[major].[minor]` – umožňuje zaměřit se na nenejnovější modul runtime.</span><span class="sxs-lookup"><span data-stu-id="81c96-199">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="81c96-200">**Verze:** \<aspnetcore verze modulu runtime ></span><span class="sxs-lookup"><span data-stu-id="81c96-200">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="81c96-201">**Obsahuje:** (11)</span><span class="sxs-lookup"><span data-stu-id="81c96-201">**Contains:** (11)</span></span>

- <span data-ttu-id="81c96-202">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` – povoluje cílení na verzi netstandard.</span><span class="sxs-lookup"><span data-stu-id="81c96-202">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="81c96-203">**Verze:** \<sdk verze ></span><span class="sxs-lookup"><span data-stu-id="81c96-203">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="81c96-204">**Obsahuje:** (15)</span><span class="sxs-lookup"><span data-stu-id="81c96-204">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="81c96-205">**Verze:** \<sdk verze ></span><span class="sxs-lookup"><span data-stu-id="81c96-205">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="81c96-206">**Obsahuje:** (15)</span><span class="sxs-lookup"><span data-stu-id="81c96-206">**Contains:** (15)</span></span>

<span data-ttu-id="81c96-207">`dotnet-runtime-deps-[major].[minor]` vyžaduje porozumění _závislostem specifickým pro distribuce_.</span><span class="sxs-lookup"><span data-stu-id="81c96-207">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro-specific dependencies_.</span></span> <span data-ttu-id="81c96-208">Vzhledem k tomu, že systém sestavení distribuce může být schopný tuto hodnotu automaticky odvodit, balíček je nepovinný. v takovém případě se tyto závislosti přidají přímo do balíčku `dotnet-runtime-[major].[minor]`.</span><span class="sxs-lookup"><span data-stu-id="81c96-208">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="81c96-209">Když je obsah balíčku ve složce se správou verzí, název balíčku `[major].[minor]` odpovídat názvu složky se správou verzí.</span><span class="sxs-lookup"><span data-stu-id="81c96-209">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="81c96-210">Pro všechny balíčky, kromě `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, to se také shoduje s verzí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="81c96-210">For all packages, except the `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, this also matches with the .NET Core version.</span></span>

<span data-ttu-id="81c96-211">Závislosti mezi balíčky by měly používat požadavek _rovnající se nebo vyšší_ verze.</span><span class="sxs-lookup"><span data-stu-id="81c96-211">Dependencies between packages should use an _equal or greater than_ version requirement.</span></span> <span data-ttu-id="81c96-212">Například `dotnet-sdk-2.2:2.2.401` vyžaduje `aspnetcore-runtime-2.2 >= 2.2.6`.</span><span class="sxs-lookup"><span data-stu-id="81c96-212">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="81c96-213">Díky tomu může uživatel upgradovat svou instalaci prostřednictvím kořenového balíčku (například `dnf update dotnet-sdk-2.2`).</span><span class="sxs-lookup"><span data-stu-id="81c96-213">This makes it possible for the user to upgrade their installation via a root package (for example, `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="81c96-214">Většina distribucí vyžaduje, aby všechny artefakty byly sestaveny ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="81c96-214">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="81c96-215">To má nějaký dopad na balíčky:</span><span class="sxs-lookup"><span data-stu-id="81c96-215">This has some impact on the packages:</span></span>

- <span data-ttu-id="81c96-216">Knihovny třetích stran v rámci `shared/Microsoft.AspNetCore.All` nelze snadno sestavit ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="81c96-216">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="81c96-217">Aby byla složka vynechána v balíčku `aspnetcore-runtime`.</span><span class="sxs-lookup"><span data-stu-id="81c96-217">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="81c96-218">`NuGetFallbackFolder` se naplní pomocí binárních artefaktů z `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="81c96-218">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="81c96-219">Měla by zůstat prázdná.</span><span class="sxs-lookup"><span data-stu-id="81c96-219">It should remain empty.</span></span>

<span data-ttu-id="81c96-220">Více balíčků `dotnet-sdk` může poskytnout stejné soubory pro `NuGetFallbackFolder`.</span><span class="sxs-lookup"><span data-stu-id="81c96-220">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="81c96-221">Aby se zabránilo problémům se správcem balíčků, měly by být tyto soubory stejné (kontrolní součet, datum změny atd.).</span><span class="sxs-lookup"><span data-stu-id="81c96-221">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="81c96-222">Vytváření balíčků</span><span class="sxs-lookup"><span data-stu-id="81c96-222">Building packages</span></span>

<span data-ttu-id="81c96-223">Úložiště [dotnet/source-Build](https://github.com/dotnet/source-build) poskytuje pokyny pro sestavení zdrojové tarballu .NET Core SDK a všech jeho součástí.</span><span class="sxs-lookup"><span data-stu-id="81c96-223">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET Core SDK and all its components.</span></span> <span data-ttu-id="81c96-224">Výstup úložiště zdrojového sestavení odpovídá rozložení popsanému v první části tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="81c96-224">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
