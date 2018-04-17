---
title: Sestavení .NET Core ze zdroje.
description: Naučte se vytvářet .NET Core a rozhraní příkazového řádku .NET Core ze zdrojového kódu.
keywords: Zdroj rozhraní .NET, .NET core, sestavení
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8b49079c-6ede-429a-92d7-ecd2fda1ab0e
ms.workload:
- dotnetcore
ms.openlocfilehash: a14e8dbf3f9be9910a2c50cfbcb3f52f4e7385e1
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="f44be-104">Sestavení .NET Core ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="f44be-104">Build .NET Core from source</span></span>

<span data-ttu-id="f44be-105">Možnost pro sestavení .NET Core z jeho zdrojový kód je důležité několika způsoby: umožňuje jednodušší port .NET Core pro nové platformy, to umožňuje příspěvky a opravy produktu a umožňuje vytvoření vlastní verze rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="f44be-105">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="f44be-106">Tento článek poskytuje pokyny pro vývojáře, kteří chtějí vytvořit a distribuovat jejich vlastní verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f44be-106">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="f44be-107">Sestavení CLR ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="f44be-107">Build the CLR from source</span></span>

<span data-ttu-id="f44be-108">Zdrojový kód pro rozhraní .NET CoreCLR naleznete v [dotnet/coreclr](https://github.com/dotnet/coreclr/) úložišti na Githubu.</span><span class="sxs-lookup"><span data-stu-id="f44be-108">The source code for the .NET CoreCLR can be found in the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository on GitHub.</span></span>

<span data-ttu-id="f44be-109">Sestavení aktuálně závisí na následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="f44be-109">The build currently depends on the following prerequisites:</span></span>
* [<span data-ttu-id="f44be-110">Git</span><span class="sxs-lookup"><span data-stu-id="f44be-110">Git</span></span>](https://git-scm.com/)
* [<span data-ttu-id="f44be-111">CMake</span><span class="sxs-lookup"><span data-stu-id="f44be-111">CMake</span></span>](https://cmake.org/)
* [<span data-ttu-id="f44be-112">Python</span><span class="sxs-lookup"><span data-stu-id="f44be-112">Python</span></span>](https://www.python.org/)
* <span data-ttu-id="f44be-113">Kompilátor C++.</span><span class="sxs-lookup"><span data-stu-id="f44be-113">a C++ compiler.</span></span>

<span data-ttu-id="f44be-114">Po instalaci tyto součásti jsou nainstalovány, můžete vytvořit modulu CLR vyvoláním skriptu buildu (`build.cmd` v systému Windows, nebo `build.sh` na Linuxu a systému macOS) na bázi [dotnet/coreclr](https://github.com/dotnet/coreclr/) úložiště.</span><span class="sxs-lookup"><span data-stu-id="f44be-114">After you've installed these prerequisites are installed, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository.</span></span>

<span data-ttu-id="f44be-115">Instalaci součástí lišit v závislosti na operační systém (OS).</span><span class="sxs-lookup"><span data-stu-id="f44be-115">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="f44be-116">Přečtěte si pokyny sestavení pro konkrétní operačním systému:</span><span class="sxs-lookup"><span data-stu-id="f44be-116">See the build instructions for your specific OS:</span></span>

 * [<span data-ttu-id="f44be-117">Windows</span><span class="sxs-lookup"><span data-stu-id="f44be-117">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
 * [<span data-ttu-id="f44be-118">Linux</span><span class="sxs-lookup"><span data-stu-id="f44be-118">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
 * [<span data-ttu-id="f44be-119">macOS</span><span class="sxs-lookup"><span data-stu-id="f44be-119">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
 * [<span data-ttu-id="f44be-120">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="f44be-120">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md) 
 * [<span data-ttu-id="f44be-121">NetBSD</span><span class="sxs-lookup"><span data-stu-id="f44be-121">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="f44be-122">Neexistuje žádné sestavení mezi napříč operačního systému (pouze pro ARM, který je založený na X64).</span><span class="sxs-lookup"><span data-stu-id="f44be-122">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="f44be-123">Musíte být na konkrétní platformu, která sestavení této platformě.</span><span class="sxs-lookup"><span data-stu-id="f44be-123">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="f44be-124">Sestavení má dva hlavní `buildTypes`:</span><span class="sxs-lookup"><span data-stu-id="f44be-124">The build has two main `buildTypes`:</span></span>

 * <span data-ttu-id="f44be-125">Ladění (výchozí) – kompilovaný modul runtime s minimálním optimalizace a kontroly další runtime (vyhodnotí).</span><span class="sxs-lookup"><span data-stu-id="f44be-125">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="f44be-126">Toto snížení úroveň optimalizace a další kontroly zpomalit spuštění modulu runtime, ale jsou důležité pro ladění.</span><span class="sxs-lookup"><span data-stu-id="f44be-126">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="f44be-127">Toto je doporučené nastavení pro vývoj a testování prostředí.</span><span class="sxs-lookup"><span data-stu-id="f44be-127">This is the recommended setting for development and testing environments.</span></span>
 * <span data-ttu-id="f44be-128">Release – kompilovaný modul runtime úplná optimalizací a bez kontroly další runtime.</span><span class="sxs-lookup"><span data-stu-id="f44be-128">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="f44be-129">To předá mnohem rychlejší běhu výkon, ale může trvat delší dobu sestavení a může být obtížné ladění.</span><span class="sxs-lookup"><span data-stu-id="f44be-129">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="f44be-130">Předat `release` k sestavení vytvořit skript pro tuto možnost vyberte, typu.</span><span class="sxs-lookup"><span data-stu-id="f44be-130">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="f44be-131">Kromě toho ve výchozím nastavení sestavení nejen vytvoří spustitelné soubory modulu runtime, ale také sestavuje všechny testy.</span><span class="sxs-lookup"><span data-stu-id="f44be-131">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="f44be-132">Existuje několik testů, trvá významné množství času, které není nezbytné, pokud chcete experimentovat s změny.</span><span class="sxs-lookup"><span data-stu-id="f44be-132">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="f44be-133">Přidáním, můžete přeskočit sestavení testy `skiptests` argument skript sestavení, jako v následujícím příkladu (Nahraďte `.\build` s `./build.sh` na počítačích systému Unix):</span><span class="sxs-lookup"><span data-stu-id="f44be-133">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests 
```

<span data-ttu-id="f44be-134">Předchozí příklad ukázal, jak stavět `Debug` příchuť, který má kontroly runtime vývoj (vyhodnotí) povolených a zakázaných optimalizace.</span><span class="sxs-lookup"><span data-stu-id="f44be-134">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="f44be-135">K vytvoření příchuť (vysokorychlostní) verze, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="f44be-135">To build the release (full speed) flavor, do the following:</span></span>

```bat 
    .\build release skiptests
```

<span data-ttu-id="f44be-136">Můžete najít další možnosti sestavení s sestavení pomocí?</span><span class="sxs-lookup"><span data-stu-id="f44be-136">You can find more build options with build by using the -?</span></span> <span data-ttu-id="f44be-137">nebo – help kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="f44be-137">or -help qualifier.</span></span>   

### <a name="using-your-build"></a><span data-ttu-id="f44be-138">Pomocí vašeho sestavení</span><span class="sxs-lookup"><span data-stu-id="f44be-138">Using Your Build</span></span>

<span data-ttu-id="f44be-139">Sestavení umístí všechny jeho soubory generované v rámci `bin` adresář na bázi úložiště.</span><span class="sxs-lookup"><span data-stu-id="f44be-139">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="f44be-140">Je *bin\Log* adresář, který obsahuje soubory protokolu vygenerovaných během sestavení (velmi užitečné při sestavení selže).</span><span class="sxs-lookup"><span data-stu-id="f44be-140">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="f44be-141">Skutečný výstup je umístěn v *bin\Product\[platformu]. [Architektura procesoru]. [vytvořit typ]*  adresář, jako třeba *bin\Product\Windows_NT.x64.Release*.</span><span class="sxs-lookup"><span data-stu-id="f44be-141">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="f44be-142">Zatímco 'nezpracovaná' výstup sestavení je někdy vhodná, obvykle vás zajímá jenom balíčky NuGet, které jsou umístěny v `.nuget\pkg` podadresáři předchozí výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="f44be-142">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="f44be-143">Existují dva základní postupy pro používání váš nový modul runtime:</span><span class="sxs-lookup"><span data-stu-id="f44be-143">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="f44be-144">**Použitím dotnet.exe a NuGet k vytvoření aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f44be-144">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="f44be-145">V tématu [pomocí vaše sestavení](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) pokyny pro vytvoření programu, který používá váš nový modul runtime s použitím balíčky NuGet, kterou jste právě vytvořili a rozhraní příkazového řádku (CLI), dotnet'.</span><span class="sxs-lookup"><span data-stu-id="f44be-145">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="f44be-146">Tento postup je, že jsou pravděpodobností používat váš nový modul runtime vývojáři – modul runtime očekávaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="f44be-146">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>    

 2. <span data-ttu-id="f44be-147">**Můžete spustit aplikaci pomocí nezabalené knihovny DLL pomocí corerun.exe**.</span><span class="sxs-lookup"><span data-stu-id="f44be-147">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="f44be-148">Toto úložiště taky definuje jednoduché hostitele názvem corerun.exe které nevyžaduje žádné závislosti na NuGet.</span><span class="sxs-lookup"><span data-stu-id="f44be-148">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="f44be-149">Budete muset zadat hostitele, kde se dá stáhnout požadované knihovny DLL, které skutečně používáte, a budete muset ručně shromáždit je společně.</span><span class="sxs-lookup"><span data-stu-id="f44be-149">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="f44be-150">Tento postup je používána všemi testy v [dotnet/coreclr](https://github.com/dotnet/coreclr) úložišti a jsou užitečné pro rychlé místní "upravit kompilaci ladění" smyčky například předběžné testování částí.</span><span class="sxs-lookup"><span data-stu-id="f44be-150">This technique is used by all the tests in the [dotnet/coreclr](https://github.com/dotnet/coreclr) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="f44be-151">V tématu [provádění aplikací využívajících .NET Core s CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) podrobnosti o použití této techniky.</span><span class="sxs-lookup"><span data-stu-id="f44be-151">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="f44be-152">Sestavení rozhraní příkazového řádku ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="f44be-152">Build the CLI from source</span></span>

<span data-ttu-id="f44be-153">Zdrojový kód pro rozhraní příkazového řádku .NET Core naleznete v [dotnet/cli](https://github.com/dotnet/cli/) úložišti na Githubu.</span><span class="sxs-lookup"><span data-stu-id="f44be-153">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="f44be-154">Chcete-li vytvořit základní rozhraní .NET, rozhraní příkazového řádku, potřebujete následující nainstalovaný na počítači.</span><span class="sxs-lookup"><span data-stu-id="f44be-154">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

* <span data-ttu-id="f44be-155">Windows a Linux:</span><span class="sxs-lookup"><span data-stu-id="f44be-155">Windows & Linux:</span></span>
    - <span data-ttu-id="f44be-156">Git v CESTĚ</span><span class="sxs-lookup"><span data-stu-id="f44be-156">git on the PATH</span></span>
* <span data-ttu-id="f44be-157">systému macOS:</span><span class="sxs-lookup"><span data-stu-id="f44be-157">macOS:</span></span>
    - <span data-ttu-id="f44be-158">Git v CESTĚ</span><span class="sxs-lookup"><span data-stu-id="f44be-158">git on the PATH</span></span>
    - <span data-ttu-id="f44be-159">Xcode</span><span class="sxs-lookup"><span data-stu-id="f44be-159">Xcode</span></span>
    - <span data-ttu-id="f44be-160">OpenSSL</span><span class="sxs-lookup"><span data-stu-id="f44be-160">OpenSSL</span></span>

<span data-ttu-id="f44be-161">K vytvoření, spuštění `build.cmd` v systému Windows, nebo `build.sh` na Linuxu a systému macOS z kořenového adresáře.</span><span class="sxs-lookup"><span data-stu-id="f44be-161">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="f44be-162">Pokud nechcete provést testy, spusťte `build.cmd /t:Compile` nebo `./build.sh /t:Compile`.</span><span class="sxs-lookup"><span data-stu-id="f44be-162">If you don't want to execute tests, run `build.cmd /t:Compile` or `./build.sh /t:Compile`.</span></span> <span data-ttu-id="f44be-163">K vytvoření rozhraní příkazového řádku v systému macOS Sierra, budete muset nastavit proměnnou prostředí DOTNET_RUNTIME_ID spuštěním `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="f44be-163">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="f44be-164">Pomocí vašeho sestavení</span><span class="sxs-lookup"><span data-stu-id="f44be-164">Using your build</span></span>

<span data-ttu-id="f44be-165">Použití `dotnet` spustitelného souboru z *artefakty / {os}-{architektura} / stage2* můžete vyzkoušet na nově vytvořený rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f44be-165">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="f44be-166">Pokud chcete použít sestavení výstup v případě vyvolání `dotnet` z aktuální konzoly, můžete také přidat *artefakty / {os}-{architektura} / stage2* k CESTĚ.</span><span class="sxs-lookup"><span data-stu-id="f44be-166">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="f44be-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="f44be-167">See also</span></span>

* [<span data-ttu-id="f44be-168">.NET core modul Common Language Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="f44be-168">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
* [<span data-ttu-id="f44be-169">Příručka vývojáře rozhraní příkazového řádku .NET core</span><span class="sxs-lookup"><span data-stu-id="f44be-169">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [<span data-ttu-id="f44be-170">Vytváření distribučních balíčků .NET Core</span><span class="sxs-lookup"><span data-stu-id="f44be-170">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
