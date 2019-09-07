---
title: Vytváření distribučních balíčků .NET Core
description: Naučte se, jak zabalit, pojmenovat a verze .NET Core pro distribuci.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: d72677cba1e7685f8e05cf479ec508683dd77b55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394163"
---
# <a name="net-core-distribution-packaging"></a><span data-ttu-id="301d8-103">Vytváření distribučních balíčků .NET Core</span><span class="sxs-lookup"><span data-stu-id="301d8-103">.NET Core distribution packaging</span></span>

<span data-ttu-id="301d8-104">Rozhraní .NET Core bude k dispozici na více a více platformách. je vhodné se naučit, jak balíček, název a verzi.</span><span class="sxs-lookup"><span data-stu-id="301d8-104">As .NET Core becomes available on more and more platforms, it's useful to learn how to package, name, and version it.</span></span> <span data-ttu-id="301d8-105">Tímto způsobem můžou údržba balíčků pomáhat zajistit konzistentní prostředí bez ohledu na to, kde se uživatelé spouštějí .NET.</span><span class="sxs-lookup"><span data-stu-id="301d8-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="301d8-106">Tento článek je užitečný pro uživatele, kteří jsou:</span><span class="sxs-lookup"><span data-stu-id="301d8-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="301d8-107">Probíhá pokus o sestavení .NET Core ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="301d8-107">Attempting to build .NET Core from source.</span></span>
- <span data-ttu-id="301d8-108">Chcete provádět změny .NET Core CLI, které by mohly mít vliv na výsledné rozložení nebo vytvořené balíčky.</span><span class="sxs-lookup"><span data-stu-id="301d8-108">Wanting to make changes to the .NET Core CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="301d8-109">Rozložení disku</span><span class="sxs-lookup"><span data-stu-id="301d8-109">Disk layout</span></span>

<span data-ttu-id="301d8-110">Při instalaci nástroje .NET Core se skládá z několika součástí, které jsou v systému souborů uvedeny následovně:</span><span class="sxs-lookup"><span data-stu-id="301d8-110">When installed, .NET Core consists of several components that are laid out as follows in the filesystem:</span></span>

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
├── packs
│   ├── Microsoft.AspNetCore.App.Ref
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref
│       └── <netstandard version>        (15)
├── shared
│   ├── Microsoft.NETCore.App
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App
│       └── <desktop app version> (7)
└── templates
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="301d8-111">(1) **dotnet** hostitel (označovaný také jako "muxer") má dvě odlišné role: aktivujte modul runtime pro spuštění aplikace a aktivujte sadu SDK k odeslání příkazů do ní.</span><span class="sxs-lookup"><span data-stu-id="301d8-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="301d8-112">Hostitel je nativní spustitelný soubor (`dotnet.exe`).</span><span class="sxs-lookup"><span data-stu-id="301d8-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="301d8-113">I když existuje jeden hostitel, většina ostatních komponent je v adresářích se správou verzí (2, 3, 5, 6).</span><span class="sxs-lookup"><span data-stu-id="301d8-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="301d8-114">To znamená, že v systému může být k dispozici více verzí, protože jsou nainstalovány vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="301d8-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="301d8-115">(2) **hostitel/FXR/\<FXR verze >** obsahuje logiku překladu rozhraní, kterou používá hostitel.</span><span class="sxs-lookup"><span data-stu-id="301d8-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="301d8-116">Hostitel používá nejnovější hostfxr, která je nainstalována.</span><span class="sxs-lookup"><span data-stu-id="301d8-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="301d8-117">Hostfxr zodpovídá za výběr vhodného modulu runtime při spouštění aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="301d8-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET Core application.</span></span> <span data-ttu-id="301d8-118">Například aplikace sestavená pro .NET Core 2.0.0 používá modul runtime 2.0.5, pokud je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="301d8-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="301d8-119">Podobně hostfxr vybere vhodnou sadu SDK během vývoje.</span><span class="sxs-lookup"><span data-stu-id="301d8-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="301d8-120">(3) **sada SDK\</SDK verze >** sadě SDK (také označované jako "nástroje") je sada spravovaných nástrojů, které se používají k psaní a vytváření knihoven a aplikací .NET Core.</span><span class="sxs-lookup"><span data-stu-id="301d8-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET Core libraries and applications.</span></span> <span data-ttu-id="301d8-121">Sada SDK obsahuje rozhraní příkazového řádku (CLI) .NET Core, kompilátory spravovaných jazyků, MSBuild a přidružené úlohy a cíle sestavení, NuGet, nové šablony projektů a tak dále.</span><span class="sxs-lookup"><span data-stu-id="301d8-121">The SDK includes the .NET Core Command-line interface (CLI), the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="301d8-122">(4) **sada SDK/NuGetFallbackFolder** obsahuje mezipaměť balíčků NuGet, které sada SDK používá během operace obnovení, například při spuštění `dotnet restore` nebo. `dotnet build /t:Restore`</span><span class="sxs-lookup"><span data-stu-id="301d8-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="301d8-123">Tato složka se používá pouze před rozhraním .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="301d8-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="301d8-124">Nemůže být sestaven ze zdroje, protože obsahuje předem sestavené binární prostředky z `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="301d8-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="301d8-125">**Sdílená** složka obsahuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="301d8-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="301d8-126">Sdílené rozhraní poskytuje sadu knihoven v centrálním umístění, aby mohly být používány různými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="301d8-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="301d8-127">(5) **Shared/Microsoft. NETCore. app\</runtime verze >** toto rozhraní obsahuje modul runtime .NET Core a podporuje spravované knihovny.</span><span class="sxs-lookup"><span data-stu-id="301d8-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET Core runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="301d8-128">(6) **Shared/Microsoft. AspNetCore. { Aplikace, všechny verze}\</aspnetcore >** obsahuje ASP.NET Core knihovny.</span><span class="sxs-lookup"><span data-stu-id="301d8-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="301d8-129">Knihovny `Microsoft.AspNetCore.App` jsou vyvíjeny a podporovány v rámci projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="301d8-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET Core project.</span></span> <span data-ttu-id="301d8-130">Knihovny jsou v `Microsoft.AspNetCore.All` oblasti nadmnožinou, které také obsahují knihovny třetích stran.</span><span class="sxs-lookup"><span data-stu-id="301d8-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="301d8-131">(7) **Shared/Microsoft. Desktop. app\</Desktop verze aplikace >** obsahuje knihovny desktopů Windows.</span><span class="sxs-lookup"><span data-stu-id="301d8-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="301d8-132">Tato součást není zahrnutá na platformách jiných než Windows.</span><span class="sxs-lookup"><span data-stu-id="301d8-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="301d8-133">(8) **License. txt, ThirdPartyNotices. txt** jsou licence .NET Core a licence knihoven třetích stran používané v .NET Core v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="301d8-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET Core license and licenses of third-party libraries used in .NET Core, respectively.</span></span>

- <span data-ttu-id="301d8-134">(9, 10) **dotnet. 1. gz, dotnet** `dotnet.1.gz` je ruční stránka dotnet.</span><span class="sxs-lookup"><span data-stu-id="301d8-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="301d8-135">`dotnet`je symlink na hostitele dotnet (1).</span><span class="sxs-lookup"><span data-stu-id="301d8-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="301d8-136">Tyto soubory jsou nainstalovány ve dobře známých umístěních pro integraci systému.</span><span class="sxs-lookup"><span data-stu-id="301d8-136">These files are installed at well known locations for system integration.</span></span>

- <span data-ttu-id="301d8-137">(11.12) **Microsoft. NETCore. app. ref, Microsoft. AspNetCore. app. ref** popisují rozhraní API `x.y` verze .NET Core a ASP.NET Core v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="301d8-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET Core and ASP.NET Core respectively.</span></span> <span data-ttu-id="301d8-138">Tyto sady jsou používány při kompilování pro tyto cílové verze.</span><span class="sxs-lookup"><span data-stu-id="301d8-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="301d8-139">(13) **Microsoft. NETCore. app. Host.\< > identifikátorů RID** obsahuje nativní binární soubor `rid`pro platformu.</span><span class="sxs-lookup"><span data-stu-id="301d8-139">(13) **Microsoft.NETCore.App.Host.\<rid>** contains a native binary for platform `rid`.</span></span> <span data-ttu-id="301d8-140">Tento binární soubor je šablonou při kompilování aplikace .NET Core do nativního binárního souboru pro danou platformu.</span><span class="sxs-lookup"><span data-stu-id="301d8-140">This binary is a template when compiling a .NET Core application into a native binary for that platform.</span></span>

- <span data-ttu-id="301d8-141">(14) **Microsoft. WindowsDesktop. app. ref** popisuje rozhraní API `x.y` aplikací klasické pracovní plochy systému Windows.</span><span class="sxs-lookup"><span data-stu-id="301d8-141">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="301d8-142">Tyto soubory se používají při kompilování pro daný cíl.</span><span class="sxs-lookup"><span data-stu-id="301d8-142">These files are used when compiling for that target.</span></span> <span data-ttu-id="301d8-143">Tento příkaz není k dispozici na platformách jiných než Windows.</span><span class="sxs-lookup"><span data-stu-id="301d8-143">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="301d8-144">(15) **NETStandard. Library. ref** popisuje rozhraní NETStandard `x.y` API.</span><span class="sxs-lookup"><span data-stu-id="301d8-144">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="301d8-145">Tyto soubory se používají při kompilování pro daný cíl.</span><span class="sxs-lookup"><span data-stu-id="301d8-145">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="301d8-146">(16) **/etc/dotnet/install_location** je soubor, který obsahuje úplnou cestu ke složce, která obsahuje `dotnet` binární soubor hostitele.</span><span class="sxs-lookup"><span data-stu-id="301d8-146">(16) **/etc/dotnet/install_location** is a file that contains the full path to the folder that contains the `dotnet` host binary.</span></span> <span data-ttu-id="301d8-147">Cesta může být ukončena novým řádkem.</span><span class="sxs-lookup"><span data-stu-id="301d8-147">The path may be terminated with a newline.</span></span> <span data-ttu-id="301d8-148">Není nutné přidávat tento soubor, pokud je `/usr/share/dotnet`kořenový adresář.</span><span class="sxs-lookup"><span data-stu-id="301d8-148">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="301d8-149">(17) **šablony** obsahují šablony používané sadou SDK.</span><span class="sxs-lookup"><span data-stu-id="301d8-149">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="301d8-150">Například `dotnet new` vyhledá šablony projektu zde.</span><span class="sxs-lookup"><span data-stu-id="301d8-150">For example, `dotnet new` finds project templates here.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="301d8-151">Doporučené balíčky</span><span class="sxs-lookup"><span data-stu-id="301d8-151">Recommended packages</span></span>

<span data-ttu-id="301d8-152">Verze .NET Core je založena na číslech verzí komponenty `[major].[minor]` modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="301d8-152">.NET Core versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="301d8-153">Verze SDK používá stejný `[major].[minor]` a má nezávisle `[patch]` , která kombinuje sémantiku funkcí a oprav pro sadu SDK.</span><span class="sxs-lookup"><span data-stu-id="301d8-153">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="301d8-154">Příklad: Sada SDK verze 2.2.302 je druhá verze verze sady SDK pro třetí funkce, která podporuje modul runtime 2,2.</span><span class="sxs-lookup"><span data-stu-id="301d8-154">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="301d8-155">Další informace o tom, jak funguje Správa verzí, najdete v tématu [Přehled verzí .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="301d8-155">For more information about how versioning works, see [.NET Core versioning overview](../versions/index.md).</span></span>

<span data-ttu-id="301d8-156">Některé balíčky obsahují část čísla verze v názvu.</span><span class="sxs-lookup"><span data-stu-id="301d8-156">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="301d8-157">To vám umožní nainstalovat určitou verzi.</span><span class="sxs-lookup"><span data-stu-id="301d8-157">This allows you to install a specific version.</span></span>
<span data-ttu-id="301d8-158">Zbytek verze není zahrnutý v názvu verze.</span><span class="sxs-lookup"><span data-stu-id="301d8-158">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="301d8-159">Správce balíčků operačního systému tak může aktualizovat balíčky (například automaticky instalovat opravy zabezpečení).</span><span class="sxs-lookup"><span data-stu-id="301d8-159">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="301d8-160">Podporovaní správci balíčků jsou specifická pro Linux.</span><span class="sxs-lookup"><span data-stu-id="301d8-160">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="301d8-161">Následující seznam obsahuje doporučené balíčky:</span><span class="sxs-lookup"><span data-stu-id="301d8-161">The following lists the recommended packages:</span></span>

- <span data-ttu-id="301d8-162">`dotnet-sdk-[major].[minor]`– Nainstaluje nejnovější sadu SDK pro konkrétní modul runtime.</span><span class="sxs-lookup"><span data-stu-id="301d8-162">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="301d8-163">**Verze:** \<verze modulu runtime ></span><span class="sxs-lookup"><span data-stu-id="301d8-163">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="301d8-164">**Příklad:** dotnet-sdk-2,1</span><span class="sxs-lookup"><span data-stu-id="301d8-164">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="301d8-165">**Zobrazí** (3),(4)</span><span class="sxs-lookup"><span data-stu-id="301d8-165">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="301d8-166">**Závislosti:** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`,`dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="301d8-166">**Dependencies:** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="301d8-167">`aspnetcore-runtime-[major].[minor]`– Nainstaluje konkrétní modul runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="301d8-167">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="301d8-168">**Verze:** \<> verze modulu runtime aspnetcore</span><span class="sxs-lookup"><span data-stu-id="301d8-168">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="301d8-169">**Příklad:** aspnetcore-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="301d8-169">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="301d8-170">**Zobrazí** 6</span><span class="sxs-lookup"><span data-stu-id="301d8-170">**Contains:** (6)</span></span>
  - <span data-ttu-id="301d8-171">**Závislosti:** `dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="301d8-171">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="301d8-172">`dotnet-runtime-deps-[major].[minor]` _(Volitelné)_ – nainstaluje závislosti pro spouštění aplikací, které jsou součástí sebe.</span><span class="sxs-lookup"><span data-stu-id="301d8-172">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="301d8-173">**Verze:** \<verze modulu runtime ></span><span class="sxs-lookup"><span data-stu-id="301d8-173">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="301d8-174">**Příklad:** dotnet-runtime-deps-2,1</span><span class="sxs-lookup"><span data-stu-id="301d8-174">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="301d8-175">**Závislosti:** _distribuce specifické závislosti_</span><span class="sxs-lookup"><span data-stu-id="301d8-175">**Dependencies:** _distro specific dependencies_</span></span>

- <span data-ttu-id="301d8-176">`dotnet-runtime-[major].[minor]`– Nainstaluje konkrétní modul runtime.</span><span class="sxs-lookup"><span data-stu-id="301d8-176">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="301d8-177">**Verze:** \<verze modulu runtime ></span><span class="sxs-lookup"><span data-stu-id="301d8-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="301d8-178">**Příklad:** dotnet-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="301d8-178">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="301d8-179">**Zobrazí** čl</span><span class="sxs-lookup"><span data-stu-id="301d8-179">**Contains:** (5)</span></span>
  - <span data-ttu-id="301d8-180">**Závislosti:** `dotnet-hostfxr:<runtime version>+`,`dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="301d8-180">**Dependencies:** `dotnet-hostfxr:<runtime version>+`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="301d8-181">`dotnet-hostfxr`-Dependency</span><span class="sxs-lookup"><span data-stu-id="301d8-181">`dotnet-hostfxr` - dependency</span></span>
  - <span data-ttu-id="301d8-182">**Verze:** \<verze modulu runtime ></span><span class="sxs-lookup"><span data-stu-id="301d8-182">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="301d8-183">**Příklad:** dotnet-hostfxr</span><span class="sxs-lookup"><span data-stu-id="301d8-183">**Example:** dotnet-hostfxr</span></span>
  - <span data-ttu-id="301d8-184">**Zobrazí** odst</span><span class="sxs-lookup"><span data-stu-id="301d8-184">**Contains:** (2)</span></span>
  - <span data-ttu-id="301d8-185">**Závislosti:** `host:<runtime version>+`</span><span class="sxs-lookup"><span data-stu-id="301d8-185">**Dependencies:** `host:<runtime version>+`</span></span>

- <span data-ttu-id="301d8-186">`dotnet-host`-Dependency</span><span class="sxs-lookup"><span data-stu-id="301d8-186">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="301d8-187">**Verze:** \<verze modulu runtime ></span><span class="sxs-lookup"><span data-stu-id="301d8-187">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="301d8-188">**Příklad:** dotnet-Host</span><span class="sxs-lookup"><span data-stu-id="301d8-188">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="301d8-189">**Zobrazí** (1), (8), (9), (10), (16)</span><span class="sxs-lookup"><span data-stu-id="301d8-189">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="301d8-190">`dotnet-apphost-pack-[major].[minor]`-Dependency</span><span class="sxs-lookup"><span data-stu-id="301d8-190">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="301d8-191">**Verze:** \<verze modulu runtime ></span><span class="sxs-lookup"><span data-stu-id="301d8-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="301d8-192">**Zobrazí** 13,5</span><span class="sxs-lookup"><span data-stu-id="301d8-192">**Contains:** (13)</span></span>

- <span data-ttu-id="301d8-193">`dotnet-targeting-pack-[major].[minor]`– Umožňuje zaměřit se na nenejnovější modul runtime.</span><span class="sxs-lookup"><span data-stu-id="301d8-193">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="301d8-194">**Verze:** \<verze modulu runtime ></span><span class="sxs-lookup"><span data-stu-id="301d8-194">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="301d8-195">**Zobrazí** 12,5</span><span class="sxs-lookup"><span data-stu-id="301d8-195">**Contains:** (12)</span></span>

- <span data-ttu-id="301d8-196">`aspnetcore-targeting-pack-[major].[minor]`– Umožňuje zaměřit se na nenejnovější modul runtime.</span><span class="sxs-lookup"><span data-stu-id="301d8-196">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="301d8-197">**Verze:** \<> verze modulu runtime aspnetcore</span><span class="sxs-lookup"><span data-stu-id="301d8-197">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="301d8-198">**Zobrazí** odst</span><span class="sxs-lookup"><span data-stu-id="301d8-198">**Contains:** (11)</span></span>

- <span data-ttu-id="301d8-199">`netstandard-targeting-pack-[major].[minor]`– Povoluje cílení na verzi netstandard</span><span class="sxs-lookup"><span data-stu-id="301d8-199">`netstandard-targeting-pack-[major].[minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="301d8-200">**Verze:** \<> verze sady SDK</span><span class="sxs-lookup"><span data-stu-id="301d8-200">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="301d8-201">**Zobrazí** 15</span><span class="sxs-lookup"><span data-stu-id="301d8-201">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="301d8-202">**Verze:** \<> verze sady SDK</span><span class="sxs-lookup"><span data-stu-id="301d8-202">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="301d8-203">**Zobrazí** 15</span><span class="sxs-lookup"><span data-stu-id="301d8-203">**Contains:** (15)</span></span>

<span data-ttu-id="301d8-204">Vyžaduje porozumění _distribuce specifickým závislostem._ `dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="301d8-204">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro specific dependencies_.</span></span> <span data-ttu-id="301d8-205">Vzhledem k tomu, že systém sestavení distribuce může být schopný tuto hodnotu automaticky odvodit, balíček je volitelný. v takovém případě se tyto závislosti `dotnet-runtime-[major].[minor]` přidávají přímo do balíčku.</span><span class="sxs-lookup"><span data-stu-id="301d8-205">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="301d8-206">Když je obsah balíčku ve složce se správou verzí, název `[major].[minor]` balíčku se shoduje s názvem složky se správou verzí.</span><span class="sxs-lookup"><span data-stu-id="301d8-206">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="301d8-207">Pro všechny balíčky s výjimkou `netstandard-targeting-pack-[major].[minor]`, to se také shoduje s verzí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="301d8-207">For all packages, except the `netstandard-targeting-pack-[major].[minor]`, this also matches with the .NET Core version.</span></span>

<span data-ttu-id="301d8-208">Závislosti mezi balíčky by měly používat požadavek _rovnající se nebo vyšší_ verze.</span><span class="sxs-lookup"><span data-stu-id="301d8-208">Dependencies between packages should use a _equal or greater than_ version requirement.</span></span> <span data-ttu-id="301d8-209">Například `dotnet-sdk-2.2:2.2.401` vyžaduje `aspnetcore-runtime-2.2 >= 2.2.6`.</span><span class="sxs-lookup"><span data-stu-id="301d8-209">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="301d8-210">Díky tomu může uživatel upgradovat instalaci prostřednictvím kořenového balíčku (např. `dnf update dotnet-sdk-2.2`).</span><span class="sxs-lookup"><span data-stu-id="301d8-210">This makes it possible for the user to upgrade their installation via a root package (e.g. `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="301d8-211">Většina distribucí vyžaduje, aby všechny artefakty byly sestaveny ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="301d8-211">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="301d8-212">To má nějaký dopad na balíčky:</span><span class="sxs-lookup"><span data-stu-id="301d8-212">This has some impact on the packages:</span></span>

- <span data-ttu-id="301d8-213">Knihovny třetích stran v části `shared/Microsoft.AspNetCore.All` nejde snadno sestavit ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="301d8-213">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="301d8-214">Takže se složka z `aspnetcore-runtime` balíčku vynechá.</span><span class="sxs-lookup"><span data-stu-id="301d8-214">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="301d8-215">Je naplněno pomocí binárních artefaktů z `nuget.org`. `NuGetFallbackFolder`</span><span class="sxs-lookup"><span data-stu-id="301d8-215">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="301d8-216">Měla by zůstat prázdná.</span><span class="sxs-lookup"><span data-stu-id="301d8-216">It should remain empty.</span></span>

<span data-ttu-id="301d8-217">Více `dotnet-sdk` balíčků může poskytovat stejné soubory `NuGetFallbackFolder`pro.</span><span class="sxs-lookup"><span data-stu-id="301d8-217">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="301d8-218">Aby se zabránilo problémům se správcem balíčků, měly by být tyto soubory stejné (kontrolní součet, datum změny atd.).</span><span class="sxs-lookup"><span data-stu-id="301d8-218">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="301d8-219">Vytváření balíčků</span><span class="sxs-lookup"><span data-stu-id="301d8-219">Building packages</span></span>

<span data-ttu-id="301d8-220">Úložiště [dotnet/source-Build](https://github.com/dotnet/source-build) poskytuje pokyny pro sestavení zdrojové tarballu .NET Core SDK a všech jeho součástí.</span><span class="sxs-lookup"><span data-stu-id="301d8-220">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET Core SDK and all its components.</span></span> <span data-ttu-id="301d8-221">Výstup úložiště zdrojového sestavení odpovídá rozložení popsanému v první části tohoto článku.</span><span class="sxs-lookup"><span data-stu-id="301d8-221">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
