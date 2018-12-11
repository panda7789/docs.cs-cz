---
title: Sestavení .NET Core ze zdroje
description: Zjistěte, jak sestavení .NET Core a .NET Core CLI ze zdrojového kódu.
author: bleroy
ms.date: 06/28/2017
ms.custom: seodec18
ms.openlocfilehash: 036d7fb64d74c00b4ac0e3d34bacc834f3c3a198
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170064"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="72667-103">Sestavení .NET Core ze zdroje</span><span class="sxs-lookup"><span data-stu-id="72667-103">Build .NET Core from source</span></span>

<span data-ttu-id="72667-104">Možnost vyvíjet aplikace .NET Core z jeho zdrojový kód je důležité několika různými způsoby: usnadňuje na port .NET Core pro nové platformy, umožňuje příspěvky a opravy produktu a umožňuje vytvářet vlastní verze rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="72667-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="72667-105">Tento článek obsahuje pokyny pro vývojáře, kteří chtějí vytvářet a distribuovat vlastní verzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="72667-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="72667-106">Sestavení CLR ze zdroje</span><span class="sxs-lookup"><span data-stu-id="72667-106">Build the CLR from source</span></span>

<span data-ttu-id="72667-107">Zdrojový kód pro .NET CoreCLR najdete v [dotnet/coreclr](https://github.com/dotnet/coreclr/) úložišti na Githubu.</span><span class="sxs-lookup"><span data-stu-id="72667-107">The source code for the .NET CoreCLR can be found in the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository on GitHub.</span></span>

<span data-ttu-id="72667-108">Sestavení aktuálně závisí na následujících požadavků:</span><span class="sxs-lookup"><span data-stu-id="72667-108">The build currently depends on the following prerequisites:</span></span>

* [<span data-ttu-id="72667-109">Git</span><span class="sxs-lookup"><span data-stu-id="72667-109">Git</span></span>](https://git-scm.com/)
* [<span data-ttu-id="72667-110">CMake</span><span class="sxs-lookup"><span data-stu-id="72667-110">CMake</span></span>](https://cmake.org/)
* [<span data-ttu-id="72667-111">Python</span><span class="sxs-lookup"><span data-stu-id="72667-111">Python</span></span>](https://www.python.org/)
* <span data-ttu-id="72667-112">Kompilátor jazyka C++.</span><span class="sxs-lookup"><span data-stu-id="72667-112">a C++ compiler.</span></span>

<span data-ttu-id="72667-113">Po instalaci těchto nezbytných podmínkách, můžete vytvořit CLR vyvoláním skript sestavení (`build.cmd` na Windows, nebo `build.sh` v Linuxu a macOS) na základě [dotnet/coreclr](https://github.com/dotnet/coreclr/) úložiště.</span><span class="sxs-lookup"><span data-stu-id="72667-113">After you've installed these prerequisites, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository.</span></span>

<span data-ttu-id="72667-114">Instalace komponent se liší v závislosti na operačním systému (OS).</span><span class="sxs-lookup"><span data-stu-id="72667-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="72667-115">Přečtěte si pokyny sestavení pro konkrétní operační systém:</span><span class="sxs-lookup"><span data-stu-id="72667-115">See the build instructions for your specific OS:</span></span>

* [<span data-ttu-id="72667-116">Windows</span><span class="sxs-lookup"><span data-stu-id="72667-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
* [<span data-ttu-id="72667-117">Linux</span><span class="sxs-lookup"><span data-stu-id="72667-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
* [<span data-ttu-id="72667-118">macOS</span><span class="sxs-lookup"><span data-stu-id="72667-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
* [<span data-ttu-id="72667-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="72667-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
* [<span data-ttu-id="72667-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="72667-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="72667-121">Nevzniká žádný napříč vytváření přes operační systém (pouze pro ARM, které je postavené na X64).</span><span class="sxs-lookup"><span data-stu-id="72667-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="72667-122">Musíte být na konkrétní platformě k vytvoření této platformy.</span><span class="sxs-lookup"><span data-stu-id="72667-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="72667-123">Sestavení má dvě hlavní `buildTypes`:</span><span class="sxs-lookup"><span data-stu-id="72667-123">The build has two main `buildTypes`:</span></span>

* <span data-ttu-id="72667-124">Ladění (výchozí) – zkompiluje modul runtime s minimální optimalizace a kontroly za běhu další (kontrolních příkazů).</span><span class="sxs-lookup"><span data-stu-id="72667-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="72667-125">Toto omezení úroveň optimalizace a další kontroly zpomalit spuštění modulu runtime, ale jsou důležité pro ladění.</span><span class="sxs-lookup"><span data-stu-id="72667-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="72667-126">Toto je doporučené nastavení pro vývojová a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="72667-126">This is the recommended setting for development and testing environments.</span></span>
* <span data-ttu-id="72667-127">Release – zkompiluje modul runtime se úplná optimalizace a bez kontroly další za běhu.</span><span class="sxs-lookup"><span data-stu-id="72667-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="72667-128">To povede k mnohem rychlejšímu běhu výkon, ale může trvat delší dobu sestavení a může být obtížné ladit.</span><span class="sxs-lookup"><span data-stu-id="72667-128">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="72667-129">Předejte `release` k buildu skript, který tuto možnost vyberte, typ sestavení.</span><span class="sxs-lookup"><span data-stu-id="72667-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="72667-130">Kromě toho ve výchozím nastavení sestavení nejen vytvoří spustitelné soubory modulu runtime, ale zároveň vytvoří všechny testy.</span><span class="sxs-lookup"><span data-stu-id="72667-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="72667-131">Existuje mnoho zkoušky významné množství času, které není nezbytné, pokud chcete experimentovat s změny.</span><span class="sxs-lookup"><span data-stu-id="72667-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="72667-132">Můžete přeskočit sestavení testů tak, že přidáte `skiptests` argument na skript sestavení, jako v následujícím příkladu (nahradit `.\build` s `./build.sh` na počítačích Unix):</span><span class="sxs-lookup"><span data-stu-id="72667-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests
```

<span data-ttu-id="72667-133">Předchozí příklad ukázal, jak vytvořit `Debug` charakter, který má kontrol za vývoj (kontrolní výrazy) povolené i zakázané optimalizace.</span><span class="sxs-lookup"><span data-stu-id="72667-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="72667-134">K sestavení charakter (plné rychlosti) verzi, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="72667-134">To build the release (full speed) flavor, do the following:</span></span>

```bat
    .\build release skiptests
```

<span data-ttu-id="72667-135">Můžete najít další možnosti sestavení se sestavením pomocí /?</span><span class="sxs-lookup"><span data-stu-id="72667-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="72667-136">nebo – help kvalifikátoru.</span><span class="sxs-lookup"><span data-stu-id="72667-136">or -help qualifier.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="72667-137">Pomocí sestavení</span><span class="sxs-lookup"><span data-stu-id="72667-137">Using Your Build</span></span>

<span data-ttu-id="72667-138">Sestavení umístí všechny jeho generované soubory v rámci `bin` adresáři základní úložiště.</span><span class="sxs-lookup"><span data-stu-id="72667-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="72667-139">Je *bin\Log* adresáře, který obsahuje soubory protokolu vygenerované během sestavování (nejužitečnější, když sestavení selže).</span><span class="sxs-lookup"><span data-stu-id="72667-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="72667-140">Aktuální výstup je umístěn v *bin\Product\[platformy]. [ Architektura procesoru]. [typ sestavení]*  adresář, jako například *bin\Product\Windows_NT.x64.Release*.</span><span class="sxs-lookup"><span data-stu-id="72667-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="72667-141">'Nezpracovanou' výstupy sestavení je někdy užitečné, obvykle vás zajímá jenom balíčky NuGet, které jsou umístěny v `.nuget\pkg` podadresář předchozí výstupní adresář.</span><span class="sxs-lookup"><span data-stu-id="72667-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="72667-142">Existují dva základní postupy pro použití nového modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="72667-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="72667-143">**Můžete vytvořit aplikaci dotnet.exe a NuGet**.</span><span class="sxs-lookup"><span data-stu-id="72667-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="72667-144">Zobrazit [pomocí sestavení](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) pokyny k vytvoření programu, který používá nový modul runtime pomocí balíčků NuGet jste právě vytvořili a "dotnet" rozhraní příkazového řádku (CLI).</span><span class="sxs-lookup"><span data-stu-id="72667-144">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="72667-145">Tato technika je, že vývojáři – modul runtime očekávané způsob, jak můžou využívat nové prostředí runtime.</span><span class="sxs-lookup"><span data-stu-id="72667-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>

 2. <span data-ttu-id="72667-146">**Ke spuštění aplikace pomocí nezabalené knihovny DLL použijte corerun.exe**.</span><span class="sxs-lookup"><span data-stu-id="72667-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="72667-147">Toto úložiště také definuje jednoduché hostitelské volá corerun.exe, který nemá žádné závislosti na webu NuGet.</span><span class="sxs-lookup"><span data-stu-id="72667-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="72667-148">Musíte určit hostitele získání požadovaných knihoven DLL, které skutečně používáte, a budete muset ručně shromáždit je společně.</span><span class="sxs-lookup"><span data-stu-id="72667-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="72667-149">Tato technika je používána všemi testy v [dotnet/coreclr](https://github.com/dotnet/coreclr) úložiště a je užitečné pro rychlé místní "úpravy kompilace – ladění" smyčka například předběžné testování částí.</span><span class="sxs-lookup"><span data-stu-id="72667-149">This technique is used by all the tests in the [dotnet/coreclr](https://github.com/dotnet/coreclr) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="72667-150">Zobrazit [spouštění aplikací .NET Core s CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) podrobnosti o použití této techniky.</span><span class="sxs-lookup"><span data-stu-id="72667-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="72667-151">Rozhraní příkazového řádku ze zdroje sestavení</span><span class="sxs-lookup"><span data-stu-id="72667-151">Build the CLI from source</span></span>

<span data-ttu-id="72667-152">Zdrojový kód pro rozhraní příkazového řádku .NET Core najdete v [dotnet/cli](https://github.com/dotnet/cli/) úložišti na Githubu.</span><span class="sxs-lookup"><span data-stu-id="72667-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="72667-153">Aby bylo možné sestavit rozhraní příkazového řádku .NET Core, potřebujete následující v počítači byly nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="72667-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

* <span data-ttu-id="72667-154">Windows a Linuxu:</span><span class="sxs-lookup"><span data-stu-id="72667-154">Windows & Linux:</span></span>
  * <span data-ttu-id="72667-155">Git na CESTĚ</span><span class="sxs-lookup"><span data-stu-id="72667-155">git on the PATH</span></span>
* <span data-ttu-id="72667-156">macOS:</span><span class="sxs-lookup"><span data-stu-id="72667-156">macOS:</span></span>
  * <span data-ttu-id="72667-157">Git na CESTĚ</span><span class="sxs-lookup"><span data-stu-id="72667-157">git on the PATH</span></span>
  * <span data-ttu-id="72667-158">Xcode</span><span class="sxs-lookup"><span data-stu-id="72667-158">Xcode</span></span>
  * <span data-ttu-id="72667-159">OpenSSL</span><span class="sxs-lookup"><span data-stu-id="72667-159">OpenSSL</span></span>

<span data-ttu-id="72667-160">Aby bylo možné sestavit, spustit `build.cmd` na Windows, nebo `build.sh` v Linuxu a macOS z kořenového adresáře.</span><span class="sxs-lookup"><span data-stu-id="72667-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="72667-161">Pokud nechcete, aby ke spuštění testů, spouštění `build.cmd -t:Compile` nebo `./build.sh -t:Compile`.</span><span class="sxs-lookup"><span data-stu-id="72667-161">If you don't want to execute tests, run `build.cmd -t:Compile` or `./build.sh -t:Compile`.</span></span> <span data-ttu-id="72667-162">K vytvoření rozhraní příkazového řádku v systému macOS Sierra, je nutné nastavit proměnnou prostředí DOTNET_RUNTIME_ID spuštěním `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="72667-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="72667-163">Pomocí sestavení</span><span class="sxs-lookup"><span data-stu-id="72667-163">Using your build</span></span>

<span data-ttu-id="72667-164">Použití `dotnet` spustitelného souboru z *artefakty / {os} – {arch} / stage2* můžete vyzkoušet na nově vytvořený rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="72667-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="72667-165">Pokud chcete použít výstup při vyvolání sestavení `dotnet` na aktuální konzolu, můžete také přidat *artefakty / {os} – {arch} / stage2* k CESTĚ.</span><span class="sxs-lookup"><span data-stu-id="72667-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="72667-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72667-166">See also</span></span>

* [<span data-ttu-id="72667-167">.NET core Common Language Runtime (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="72667-167">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
* [<span data-ttu-id="72667-168">Příručka pro vývojáře rozhraní příkazového řádku .NET core</span><span class="sxs-lookup"><span data-stu-id="72667-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [<span data-ttu-id="72667-169">Vytváření distribučních balíčků .NET Core</span><span class="sxs-lookup"><span data-stu-id="72667-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
