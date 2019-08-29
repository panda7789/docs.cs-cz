---
title: Sestavení .NET Core ze zdroje
description: Naučte se, jak vytvořit .NET Core a .NET Core CLI ze zdrojového kódu.
author: bleroy
ms.date: 06/28/2017
ms.custom: seodec18
ms.openlocfilehash: dcd7c909325eec5a79db74098d7ac880000eafa1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105383"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="55ec4-103">Sestavení .NET Core ze zdroje</span><span class="sxs-lookup"><span data-stu-id="55ec4-103">Build .NET Core from source</span></span>

<span data-ttu-id="55ec4-104">Možnost sestavování .NET Core z jeho zdrojového kódu je důležitá v různých způsobech: usnadňuje portování .NET Core na nové platformy, umožňuje příspěvky a opravy produktu a umožňuje vytváření vlastních verzí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="55ec4-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="55ec4-105">Tento článek obsahuje pokyny pro vývojáře, kteří chtějí sestavovat a distribuovat vlastní verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="55ec4-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="55ec4-106">Sestavení CLR ze zdroje</span><span class="sxs-lookup"><span data-stu-id="55ec4-106">Build the CLR from source</span></span>

<span data-ttu-id="55ec4-107">Zdrojový kód pro .NET CoreCLR najdete v úložišti [dotnet/CoreCLR](https://github.com/dotnet/coreclr/) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="55ec4-107">The source code for the .NET CoreCLR can be found in the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository on GitHub.</span></span>

<span data-ttu-id="55ec4-108">Sestavení v současné době závisí na následujících předpokladech:</span><span class="sxs-lookup"><span data-stu-id="55ec4-108">The build currently depends on the following prerequisites:</span></span>

- [<span data-ttu-id="55ec4-109">Git</span><span class="sxs-lookup"><span data-stu-id="55ec4-109">Git</span></span>](https://git-scm.com/)
- [<span data-ttu-id="55ec4-110">CMake</span><span class="sxs-lookup"><span data-stu-id="55ec4-110">CMake</span></span>](https://cmake.org/)
- [<span data-ttu-id="55ec4-111">Python</span><span class="sxs-lookup"><span data-stu-id="55ec4-111">Python</span></span>](https://www.python.org/)
- <span data-ttu-id="55ec4-112">C++ kompilátor.</span><span class="sxs-lookup"><span data-stu-id="55ec4-112">a C++ compiler.</span></span>

<span data-ttu-id="55ec4-113">Po instalaci těchto požadavků můžete sestavit modul CLR vyvoláním skriptu sestavení (`build.cmd` ve Windows nebo `build.sh` na platformě Linux a MacOS) na bázi úložiště [dotnet/CoreCLR](https://github.com/dotnet/coreclr/) .</span><span class="sxs-lookup"><span data-stu-id="55ec4-113">After you've installed these prerequisites, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository.</span></span>

<span data-ttu-id="55ec4-114">Instalace komponent se liší v závislosti na operačním systému (OS).</span><span class="sxs-lookup"><span data-stu-id="55ec4-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="55ec4-115">Podívejte se na pokyny pro sestavení pro konkrétní operační systém:</span><span class="sxs-lookup"><span data-stu-id="55ec4-115">See the build instructions for your specific OS:</span></span>

- [<span data-ttu-id="55ec4-116">Windows</span><span class="sxs-lookup"><span data-stu-id="55ec4-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
- [<span data-ttu-id="55ec4-117">Linux</span><span class="sxs-lookup"><span data-stu-id="55ec4-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
- [<span data-ttu-id="55ec4-118">macOS</span><span class="sxs-lookup"><span data-stu-id="55ec4-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
- [<span data-ttu-id="55ec4-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="55ec4-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
- [<span data-ttu-id="55ec4-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="55ec4-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="55ec4-121">V operačním systému neexistují žádné křížové sestavování (jenom pro ARM, které je postavené na platformě x64).</span><span class="sxs-lookup"><span data-stu-id="55ec4-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="55ec4-122">Musíte být na konkrétní platformě pro sestavení této platformy.</span><span class="sxs-lookup"><span data-stu-id="55ec4-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="55ec4-123">Sestavení má dvě hlavní `buildTypes`:</span><span class="sxs-lookup"><span data-stu-id="55ec4-123">The build has two main `buildTypes`:</span></span>

- <span data-ttu-id="55ec4-124">Ladit (výchozí) – zkompiluje modul runtime s minimálními optimalizacemi a dalšími kontrolami za běhu (kontrolní výrazy).</span><span class="sxs-lookup"><span data-stu-id="55ec4-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="55ec4-125">Toto snížení úrovně optimalizace a další kontroly pomaleji spouštění za běhu, ale jsou cenné pro ladění.</span><span class="sxs-lookup"><span data-stu-id="55ec4-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="55ec4-126">Toto je doporučené nastavení pro vývojová a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="55ec4-126">This is the recommended setting for development and testing environments.</span></span>
- <span data-ttu-id="55ec4-127">Release – zkompiluje modul runtime s úplnými optimalizacemi a bez dalších kontrol za běhu.</span><span class="sxs-lookup"><span data-stu-id="55ec4-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="55ec4-128">Výsledkem bude mnohem rychlejší doba běhu, ale může trvat delší dobu, než se sestaví a může být obtížné ho ladit.</span><span class="sxs-lookup"><span data-stu-id="55ec4-128">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="55ec4-129">Pro `release` výběr tohoto typu sestavení předejte skriptu sestavení.</span><span class="sxs-lookup"><span data-stu-id="55ec4-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="55ec4-130">Kromě toho ve výchozím nastavení sestavení nejen vytvoří běhové spustitelné soubory, ale také vytvoří všechny testy.</span><span class="sxs-lookup"><span data-stu-id="55ec4-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="55ec4-131">Existuje poměrně několik testů, které zabírají značnou dobu, která není nutná, pokud chcete experimentovat pouze se změnami.</span><span class="sxs-lookup"><span data-stu-id="55ec4-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="55ec4-132">Můžete přeskočit sestavení testů přidáním `skiptests` argumentu do skriptu sestavení, jako v následujícím příkladu (nahraďte `.\build` je v počítačích se `./build.sh` systémem UNIX):</span><span class="sxs-lookup"><span data-stu-id="55ec4-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests
```

<span data-ttu-id="55ec4-133">Předchozí příklad ukázal, jak sestavit `Debug` charakter, který má povolené kontroly doby vývoje (kontrolní výrazy) a optimalizace, které jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="55ec4-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="55ec4-134">Chcete-li sestavit charakter vydaných verzí (s plnou rychlostí), postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="55ec4-134">To build the release (full speed) flavor, do the following:</span></span>

```bat
    .\build release skiptests
```

<span data-ttu-id="55ec4-135">Další možnosti sestavení můžete najít pomocí sestavení pomocí-?</span><span class="sxs-lookup"><span data-stu-id="55ec4-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="55ec4-136">nebo – kvalifikátor pomocníka.</span><span class="sxs-lookup"><span data-stu-id="55ec4-136">or -help qualifier.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="55ec4-137">Použití sestavení</span><span class="sxs-lookup"><span data-stu-id="55ec4-137">Using Your Build</span></span>

<span data-ttu-id="55ec4-138">Sestavení umístí všechny své vygenerované soubory `bin` do adresáře na bázi úložiště.</span><span class="sxs-lookup"><span data-stu-id="55ec4-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="55ec4-139">K dispozici je adresář *bin\Log* , který obsahuje soubory protokolu generované během sestavení (nejužitečnější při neúspěšném sestavení).</span><span class="sxs-lookup"><span data-stu-id="55ec4-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="55ec4-140">Skutečný výstup je umístěný v *bin\Product\[platformě]. [ Architektura procesoru]. [typ sestavení]* Adresář, například *bin\Product\Windows_NT.x64.Release*.</span><span class="sxs-lookup"><span data-stu-id="55ec4-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="55ec4-141">Zatímco výstup "raw" sestavení je někdy užitečné, obvykle se zajímá pouze o balíčky NuGet, které jsou umístěny v `.nuget\pkg` podadresáři předchozího výstupního adresáře.</span><span class="sxs-lookup"><span data-stu-id="55ec4-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="55ec4-142">Existují dvě základní techniky použití nového modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="55ec4-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="55ec4-143">**K vytvoření aplikace použijte dotnet. exe a NuGet**.</span><span class="sxs-lookup"><span data-stu-id="55ec4-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="55ec4-144">Pokyny k vytvoření programu, který používá váš nový modul runtime, pomocí balíčků NuGet, které jste právě vytvořili, a rozhraní příkazového řádku dotnet (CLI) najdete v tématu [použití sestavení](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) .</span><span class="sxs-lookup"><span data-stu-id="55ec4-144">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="55ec4-145">Tato technika je předpokládaný způsob, jakým vývojáři mimo modul runtime využívají nový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="55ec4-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>

 2. <span data-ttu-id="55ec4-146">Pomocí souboru korutiny **. exe spusťte aplikaci pomocí nebalených knihoven DLL**.</span><span class="sxs-lookup"><span data-stu-id="55ec4-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="55ec4-147">Toto úložiště také definuje jednoduchého hostitele s názvem spoluspustit. exe, který neprovádí žádnou závislost na NuGet.</span><span class="sxs-lookup"><span data-stu-id="55ec4-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="55ec4-148">Je nutné sdělit hostiteli, kde mají získat požadované knihovny DLL, které skutečně používáte, a je nutné je ručně shromáždit společně.</span><span class="sxs-lookup"><span data-stu-id="55ec4-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="55ec4-149">Tato technika je používána všemi testy v úložišti [dotnet/CoreCLR](https://github.com/dotnet/coreclr) a je užitečná pro rychlou místní smyčku "Edit-Compile-debug", jako je například předběžné testování částí.</span><span class="sxs-lookup"><span data-stu-id="55ec4-149">This technique is used by all the tests in the [dotnet/coreclr](https://github.com/dotnet/coreclr) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="55ec4-150">Podrobnosti o použití této techniky najdete v tématu [spouštění aplikací .NET Core pomocí souboru. exe.](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md)</span><span class="sxs-lookup"><span data-stu-id="55ec4-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="55ec4-151">Sestavení CLI ze zdroje</span><span class="sxs-lookup"><span data-stu-id="55ec4-151">Build the CLI from source</span></span>

<span data-ttu-id="55ec4-152">Zdrojový kód pro .NET Core CLI lze nalézt v úložišti [dotnet/CLI](https://github.com/dotnet/cli/) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="55ec4-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="55ec4-153">Aby bylo možné sestavit .NET Core CLI, potřebujete na svém počítači nainstalované následující.</span><span class="sxs-lookup"><span data-stu-id="55ec4-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

- <span data-ttu-id="55ec4-154">Windows & Linux:</span><span class="sxs-lookup"><span data-stu-id="55ec4-154">Windows & Linux:</span></span>
  - <span data-ttu-id="55ec4-155">Git v cestě</span><span class="sxs-lookup"><span data-stu-id="55ec4-155">git on the PATH</span></span>
- <span data-ttu-id="55ec4-156">MacOS</span><span class="sxs-lookup"><span data-stu-id="55ec4-156">macOS:</span></span>
  - <span data-ttu-id="55ec4-157">Git v cestě</span><span class="sxs-lookup"><span data-stu-id="55ec4-157">git on the PATH</span></span>
  - <span data-ttu-id="55ec4-158">Xcode</span><span class="sxs-lookup"><span data-stu-id="55ec4-158">Xcode</span></span>
  - <span data-ttu-id="55ec4-159">OpenSSL</span><span class="sxs-lookup"><span data-stu-id="55ec4-159">OpenSSL</span></span>

<span data-ttu-id="55ec4-160">Aby bylo možné sestavovat `build.cmd` , spouštět v systému `build.sh` Windows nebo v systémech Linux a MacOS z kořenového adresáře.</span><span class="sxs-lookup"><span data-stu-id="55ec4-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="55ec4-161">Pokud nechcete spouštět testy, spusťte příkaz `build.cmd -t:Compile` nebo. `./build.sh -t:Compile`</span><span class="sxs-lookup"><span data-stu-id="55ec4-161">If you don't want to execute tests, run `build.cmd -t:Compile` or `./build.sh -t:Compile`.</span></span> <span data-ttu-id="55ec4-162">Chcete-li sestavit rozhraní příkazového řádku v macOS Sierra, je nutné nastavit proměnnou prostředí DOTNET_RUNTIME_ID `export DOTNET_RUNTIME_ID=osx.10.11-x64`spuštěním.</span><span class="sxs-lookup"><span data-stu-id="55ec4-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="55ec4-163">Použití sestavení</span><span class="sxs-lookup"><span data-stu-id="55ec4-163">Using your build</span></span>

<span data-ttu-id="55ec4-164">Použijte spustitelný soubor z *artefaktů/{OS}-{arch}/STAGE2* a vyzkoušejte nově sestavené rozhraní příkazového řádku. `dotnet`</span><span class="sxs-lookup"><span data-stu-id="55ec4-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="55ec4-165">Pokud chcete použít výstup sestavení při vyvolání `dotnet` z aktuální konzoly, můžete také přidat artefakty */{OS}-{arch}/STAGE2* do cesty.</span><span class="sxs-lookup"><span data-stu-id="55ec4-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="55ec4-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55ec4-166">See also</span></span>

- [<span data-ttu-id="55ec4-167">Modul CLR (Common Language Runtime) .NET Core (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="55ec4-167">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
- [<span data-ttu-id="55ec4-168">.NET Core CLI příručka pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="55ec4-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [<span data-ttu-id="55ec4-169">Vytváření distribučních balíčků .NET Core</span><span class="sxs-lookup"><span data-stu-id="55ec4-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
