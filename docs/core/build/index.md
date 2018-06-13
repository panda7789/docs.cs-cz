---
title: Sestavení .NET Core ze zdroje.
description: Naučte se vytvářet .NET Core a rozhraní příkazového řádku .NET Core ze zdrojového kódu.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.openlocfilehash: 55a35223a4bc11156e056cceb7f86365c4906222
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216009"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="cd00e-103">Sestavení .NET Core ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="cd00e-103">Build .NET Core from source</span></span>

<span data-ttu-id="cd00e-104">Možnost pro sestavení .NET Core z jeho zdrojový kód je důležité několika způsoby: umožňuje jednodušší port .NET Core pro nové platformy, to umožňuje příspěvky a opravy produktu a umožňuje vytvoření vlastní verze rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="cd00e-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="cd00e-105">Tento článek poskytuje pokyny pro vývojáře, kteří chtějí vytvořit a distribuovat jejich vlastní verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd00e-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="cd00e-106">Sestavení CLR ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="cd00e-106">Build the CLR from source</span></span>

<span data-ttu-id="cd00e-107">Zdrojový kód pro rozhraní .NET CoreCLR naleznete v [dotnet/coreclr](https://github.com/dotnet/coreclr/) úložišti na Githubu.</span><span class="sxs-lookup"><span data-stu-id="cd00e-107">The source code for the .NET CoreCLR can be found in the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository on GitHub.</span></span>

<span data-ttu-id="cd00e-108">Sestavení aktuálně závisí na následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="cd00e-108">The build currently depends on the following prerequisites:</span></span>
* [<span data-ttu-id="cd00e-109">Git</span><span class="sxs-lookup"><span data-stu-id="cd00e-109">Git</span></span>](https://git-scm.com/)
* [<span data-ttu-id="cd00e-110">CMake</span><span class="sxs-lookup"><span data-stu-id="cd00e-110">CMake</span></span>](https://cmake.org/)
* [<span data-ttu-id="cd00e-111">Python</span><span class="sxs-lookup"><span data-stu-id="cd00e-111">Python</span></span>](https://www.python.org/)
* <span data-ttu-id="cd00e-112">Kompilátor C++.</span><span class="sxs-lookup"><span data-stu-id="cd00e-112">a C++ compiler.</span></span>

<span data-ttu-id="cd00e-113">Po instalaci tyto součásti jsou nainstalovány, můžete vytvořit modulu CLR vyvoláním skriptu buildu (`build.cmd` v systému Windows, nebo `build.sh` na Linuxu a systému macOS) na bázi [dotnet/coreclr](https://github.com/dotnet/coreclr/) úložiště.</span><span class="sxs-lookup"><span data-stu-id="cd00e-113">After you've installed these prerequisites are installed, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository.</span></span>

<span data-ttu-id="cd00e-114">Instalaci součástí lišit v závislosti na operační systém (OS).</span><span class="sxs-lookup"><span data-stu-id="cd00e-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="cd00e-115">Přečtěte si pokyny sestavení pro konkrétní operačním systému:</span><span class="sxs-lookup"><span data-stu-id="cd00e-115">See the build instructions for your specific OS:</span></span>

 * [<span data-ttu-id="cd00e-116">Windows</span><span class="sxs-lookup"><span data-stu-id="cd00e-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
 * [<span data-ttu-id="cd00e-117">Linux</span><span class="sxs-lookup"><span data-stu-id="cd00e-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
 * [<span data-ttu-id="cd00e-118">macOS</span><span class="sxs-lookup"><span data-stu-id="cd00e-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
 * [<span data-ttu-id="cd00e-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="cd00e-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md) 
 * [<span data-ttu-id="cd00e-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="cd00e-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="cd00e-121">Neexistuje žádné sestavení mezi napříč operačního systému (pouze pro ARM, který je založený na X64).</span><span class="sxs-lookup"><span data-stu-id="cd00e-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="cd00e-122">Musíte být na konkrétní platformu, která sestavení této platformě.</span><span class="sxs-lookup"><span data-stu-id="cd00e-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="cd00e-123">Sestavení má dva hlavní `buildTypes`:</span><span class="sxs-lookup"><span data-stu-id="cd00e-123">The build has two main `buildTypes`:</span></span>

 * <span data-ttu-id="cd00e-124">Ladění (výchozí) – kompilovaný modul runtime s minimálním optimalizace a kontroly další runtime (vyhodnotí).</span><span class="sxs-lookup"><span data-stu-id="cd00e-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="cd00e-125">Toto snížení úroveň optimalizace a další kontroly zpomalit spuštění modulu runtime, ale jsou důležité pro ladění.</span><span class="sxs-lookup"><span data-stu-id="cd00e-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="cd00e-126">Toto je doporučené nastavení pro vývoj a testování prostředí.</span><span class="sxs-lookup"><span data-stu-id="cd00e-126">This is the recommended setting for development and testing environments.</span></span>
 * <span data-ttu-id="cd00e-127">Release – kompilovaný modul runtime úplná optimalizací a bez kontroly další runtime.</span><span class="sxs-lookup"><span data-stu-id="cd00e-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="cd00e-128">To předá mnohem rychlejší běhu výkon, ale může trvat delší dobu sestavení a může být obtížné ladění.</span><span class="sxs-lookup"><span data-stu-id="cd00e-128">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="cd00e-129">Předat `release` k sestavení vytvořit skript pro tuto možnost vyberte, typu.</span><span class="sxs-lookup"><span data-stu-id="cd00e-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="cd00e-130">Kromě toho ve výchozím nastavení sestavení nejen vytvoří spustitelné soubory modulu runtime, ale také sestavuje všechny testy.</span><span class="sxs-lookup"><span data-stu-id="cd00e-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="cd00e-131">Existuje několik testů, trvá významné množství času, které není nezbytné, pokud chcete experimentovat s změny.</span><span class="sxs-lookup"><span data-stu-id="cd00e-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="cd00e-132">Přidáním, můžete přeskočit sestavení testy `skiptests` argument skript sestavení, jako v následujícím příkladu (Nahraďte `.\build` s `./build.sh` na počítačích systému Unix):</span><span class="sxs-lookup"><span data-stu-id="cd00e-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests 
```

<span data-ttu-id="cd00e-133">Předchozí příklad ukázal, jak stavět `Debug` příchuť, který má kontroly runtime vývoj (vyhodnotí) povolených a zakázaných optimalizace.</span><span class="sxs-lookup"><span data-stu-id="cd00e-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="cd00e-134">K vytvoření příchuť (vysokorychlostní) verze, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="cd00e-134">To build the release (full speed) flavor, do the following:</span></span>

```bat 
    .\build release skiptests
```

<span data-ttu-id="cd00e-135">Můžete najít další možnosti sestavení s sestavení pomocí?</span><span class="sxs-lookup"><span data-stu-id="cd00e-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="cd00e-136">nebo – help kvalifikátor.</span><span class="sxs-lookup"><span data-stu-id="cd00e-136">or -help qualifier.</span></span>   

### <a name="using-your-build"></a><span data-ttu-id="cd00e-137">Pomocí vašeho sestavení</span><span class="sxs-lookup"><span data-stu-id="cd00e-137">Using Your Build</span></span>

<span data-ttu-id="cd00e-138">Sestavení umístí všechny jeho soubory generované v rámci `bin` adresář na bázi úložiště.</span><span class="sxs-lookup"><span data-stu-id="cd00e-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="cd00e-139">Je *bin\Log* adresář, který obsahuje soubory protokolu vygenerovaných během sestavení (velmi užitečné při sestavení selže).</span><span class="sxs-lookup"><span data-stu-id="cd00e-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="cd00e-140">Skutečný výstup je umístěn v *bin\Product\[platformu]. [Architektura procesoru]. [vytvořit typ]*  adresář, jako třeba *bin\Product\Windows_NT.x64.Release*.</span><span class="sxs-lookup"><span data-stu-id="cd00e-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="cd00e-141">Zatímco 'nezpracovaná' výstup sestavení je někdy vhodná, obvykle vás zajímá jenom balíčky NuGet, které jsou umístěny v `.nuget\pkg` podadresáři předchozí výstupnímu adresáři.</span><span class="sxs-lookup"><span data-stu-id="cd00e-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="cd00e-142">Existují dva základní postupy pro používání váš nový modul runtime:</span><span class="sxs-lookup"><span data-stu-id="cd00e-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="cd00e-143">**Použitím dotnet.exe a NuGet k vytvoření aplikace**.</span><span class="sxs-lookup"><span data-stu-id="cd00e-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="cd00e-144">V tématu [pomocí vaše sestavení](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) pokyny pro vytvoření programu, který používá váš nový modul runtime s použitím balíčky NuGet, kterou jste právě vytvořili a rozhraní příkazového řádku (CLI), dotnet'.</span><span class="sxs-lookup"><span data-stu-id="cd00e-144">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="cd00e-145">Tento postup je, že jsou pravděpodobností používat váš nový modul runtime vývojáři – modul runtime očekávaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="cd00e-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>    

 2. <span data-ttu-id="cd00e-146">**Můžete spustit aplikaci pomocí nezabalené knihovny DLL pomocí corerun.exe**.</span><span class="sxs-lookup"><span data-stu-id="cd00e-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="cd00e-147">Toto úložiště taky definuje jednoduché hostitele názvem corerun.exe které nevyžaduje žádné závislosti na NuGet.</span><span class="sxs-lookup"><span data-stu-id="cd00e-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="cd00e-148">Budete muset zadat hostitele, kde se dá stáhnout požadované knihovny DLL, které skutečně používáte, a budete muset ručně shromáždit je společně.</span><span class="sxs-lookup"><span data-stu-id="cd00e-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="cd00e-149">Tento postup je používána všemi testy v [dotnet/coreclr](https://github.com/dotnet/coreclr) úložišti a jsou užitečné pro rychlé místní "upravit kompilaci ladění" smyčky například předběžné testování částí.</span><span class="sxs-lookup"><span data-stu-id="cd00e-149">This technique is used by all the tests in the [dotnet/coreclr](https://github.com/dotnet/coreclr) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="cd00e-150">V tématu [provádění aplikací využívajících .NET Core s CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) podrobnosti o použití této techniky.</span><span class="sxs-lookup"><span data-stu-id="cd00e-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="cd00e-151">Sestavení rozhraní příkazového řádku ze zdroje.</span><span class="sxs-lookup"><span data-stu-id="cd00e-151">Build the CLI from source</span></span>

<span data-ttu-id="cd00e-152">Zdrojový kód pro rozhraní příkazového řádku .NET Core naleznete v [dotnet/cli](https://github.com/dotnet/cli/) úložišti na Githubu.</span><span class="sxs-lookup"><span data-stu-id="cd00e-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="cd00e-153">Chcete-li vytvořit základní rozhraní .NET, rozhraní příkazového řádku, potřebujete následující nainstalovaný na počítači.</span><span class="sxs-lookup"><span data-stu-id="cd00e-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

* <span data-ttu-id="cd00e-154">Windows a Linux:</span><span class="sxs-lookup"><span data-stu-id="cd00e-154">Windows & Linux:</span></span>
    - <span data-ttu-id="cd00e-155">Git v CESTĚ</span><span class="sxs-lookup"><span data-stu-id="cd00e-155">git on the PATH</span></span>
* <span data-ttu-id="cd00e-156">systému macOS:</span><span class="sxs-lookup"><span data-stu-id="cd00e-156">macOS:</span></span>
    - <span data-ttu-id="cd00e-157">Git v CESTĚ</span><span class="sxs-lookup"><span data-stu-id="cd00e-157">git on the PATH</span></span>
    - <span data-ttu-id="cd00e-158">Xcode</span><span class="sxs-lookup"><span data-stu-id="cd00e-158">Xcode</span></span>
    - <span data-ttu-id="cd00e-159">OpenSSL</span><span class="sxs-lookup"><span data-stu-id="cd00e-159">OpenSSL</span></span>

<span data-ttu-id="cd00e-160">K vytvoření, spuštění `build.cmd` v systému Windows, nebo `build.sh` na Linuxu a systému macOS z kořenového adresáře.</span><span class="sxs-lookup"><span data-stu-id="cd00e-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="cd00e-161">Pokud nechcete provést testy, spusťte `build.cmd /t:Compile` nebo `./build.sh /t:Compile`.</span><span class="sxs-lookup"><span data-stu-id="cd00e-161">If you don't want to execute tests, run `build.cmd /t:Compile` or `./build.sh /t:Compile`.</span></span> <span data-ttu-id="cd00e-162">K vytvoření rozhraní příkazového řádku v systému macOS Sierra, budete muset nastavit proměnnou prostředí DOTNET_RUNTIME_ID spuštěním `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="cd00e-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="cd00e-163">Pomocí vašeho sestavení</span><span class="sxs-lookup"><span data-stu-id="cd00e-163">Using your build</span></span>

<span data-ttu-id="cd00e-164">Použití `dotnet` spustitelného souboru z *artefakty / {os}-{architektura} / stage2* můžete vyzkoušet na nově vytvořený rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="cd00e-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="cd00e-165">Pokud chcete použít sestavení výstup v případě vyvolání `dotnet` z aktuální konzoly, můžete také přidat *artefakty / {os}-{architektura} / stage2* k CESTĚ.</span><span class="sxs-lookup"><span data-stu-id="cd00e-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd00e-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd00e-166">See also</span></span>

* [<span data-ttu-id="cd00e-167">.NET core modul Common Language Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="cd00e-167">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
* [<span data-ttu-id="cd00e-168">Příručka vývojáře rozhraní příkazového řádku .NET core</span><span class="sxs-lookup"><span data-stu-id="cd00e-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [<span data-ttu-id="cd00e-169">Vytváření distribučních balíčků .NET Core</span><span class="sxs-lookup"><span data-stu-id="cd00e-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
