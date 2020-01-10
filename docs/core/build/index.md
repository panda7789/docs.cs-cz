---
title: Sestavení .NET Core ze zdroje
description: Naučte se, jak vytvořit .NET Core a .NET Core CLI ze zdrojového kódu.
author: bleroy
ms.date: 06/28/2017
ms.openlocfilehash: fe5431667d861d830c2ec56252e6e3e2ca08a866
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740913"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="6a8d2-103">Sestavení .NET Core ze zdroje</span><span class="sxs-lookup"><span data-stu-id="6a8d2-103">Build .NET Core from source</span></span>

<span data-ttu-id="6a8d2-104">Možnost sestavování .NET Core z jeho zdrojového kódu je důležitá v různých způsobech: usnadňuje portování .NET Core na nové platformy, umožňuje příspěvky a opravy produktu a umožňuje vytváření vlastních verzí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="6a8d2-105">Tento článek obsahuje pokyny pro vývojáře, kteří chtějí sestavovat a distribuovat vlastní verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="6a8d2-106">Sestavení CLR ze zdroje</span><span class="sxs-lookup"><span data-stu-id="6a8d2-106">Build the CLR from source</span></span>

<span data-ttu-id="6a8d2-107">Zdrojový kód pro rozhraní .NET CoreCLR lze nalézt v úložišti [dotnet/runtime](https://github.com/dotnet/runtime/) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-107">The source code for the .NET CoreCLR can be found in the [dotnet/runtime](https://github.com/dotnet/runtime/) repository on GitHub.</span></span>

<span data-ttu-id="6a8d2-108">Sestavení v současné době závisí na následujících předpokladech:</span><span class="sxs-lookup"><span data-stu-id="6a8d2-108">The build currently depends on the following prerequisites:</span></span>

- [<span data-ttu-id="6a8d2-109">Git</span><span class="sxs-lookup"><span data-stu-id="6a8d2-109">Git</span></span>](https://git-scm.com/)
- [<span data-ttu-id="6a8d2-110">CMake</span><span class="sxs-lookup"><span data-stu-id="6a8d2-110">CMake</span></span>](https://cmake.org/)
- [<span data-ttu-id="6a8d2-111">Python</span><span class="sxs-lookup"><span data-stu-id="6a8d2-111">Python</span></span>](https://www.python.org/)
- <span data-ttu-id="6a8d2-112">C++ kompilátor.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-112">a C++ compiler.</span></span>

<span data-ttu-id="6a8d2-113">Po instalaci těchto požadavků můžete sestavit modul CLR vyvoláním skriptu sestavení (`build.cmd` ve Windows nebo `build.sh` v systémech Linux a macOS) na bázi úložiště [dotnet/runtime](https://github.com/dotnet/runtime/) .</span><span class="sxs-lookup"><span data-stu-id="6a8d2-113">After you've installed these prerequisites, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/runtime](https://github.com/dotnet/runtime/) repository.</span></span>

<span data-ttu-id="6a8d2-114">Instalace komponent se liší v závislosti na operačním systému (OS).</span><span class="sxs-lookup"><span data-stu-id="6a8d2-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="6a8d2-115">Podívejte se na pokyny pro sestavení pro konkrétní operační systém:</span><span class="sxs-lookup"><span data-stu-id="6a8d2-115">See the build instructions for your specific OS:</span></span>

- [<span data-ttu-id="6a8d2-116">Windows</span><span class="sxs-lookup"><span data-stu-id="6a8d2-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
- [<span data-ttu-id="6a8d2-117">Linux</span><span class="sxs-lookup"><span data-stu-id="6a8d2-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
- [<span data-ttu-id="6a8d2-118">macOS</span><span class="sxs-lookup"><span data-stu-id="6a8d2-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
- [<span data-ttu-id="6a8d2-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="6a8d2-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
- [<span data-ttu-id="6a8d2-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="6a8d2-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="6a8d2-121">V operačním systému neexistují žádné křížové sestavování (jenom pro ARM, které je postavené na platformě x64).</span><span class="sxs-lookup"><span data-stu-id="6a8d2-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="6a8d2-122">Musíte být na konkrétní platformě pro sestavení této platformy.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="6a8d2-123">Sestavení má dvě hlavní `buildTypes`:</span><span class="sxs-lookup"><span data-stu-id="6a8d2-123">The build has two main `buildTypes`:</span></span>

- <span data-ttu-id="6a8d2-124">Ladit (výchozí) – zkompiluje modul runtime s minimálními optimalizacemi a dalšími kontrolami za běhu (kontrolní výrazy).</span><span class="sxs-lookup"><span data-stu-id="6a8d2-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="6a8d2-125">Toto snížení úrovně optimalizace a další kontroly pomaleji spouštění za běhu, ale jsou cenné pro ladění.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="6a8d2-126">Toto je doporučené nastavení pro vývojová a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-126">This is the recommended setting for development and testing environments.</span></span>
- <span data-ttu-id="6a8d2-127">Release – zkompiluje modul runtime s úplnými optimalizacemi a bez dalších kontrol za běhu.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="6a8d2-128">To bude mít za následek mnohem rychlejší výkon, ale může trvat delší dobu, než se sestaví a může být obtížné ho ladit.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-128">This will yield much faster run-time performance, but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="6a8d2-129">Chcete-li vybrat tento typ sestavení, předejte `release` skriptu sestavení.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="6a8d2-130">Kromě toho ve výchozím nastavení sestavení nejen vytvoří běhové spustitelné soubory, ale také vytvoří všechny testy.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="6a8d2-131">Existuje poměrně několik testů, které zabírají značnou dobu, která není nutná, pokud chcete experimentovat pouze se změnami.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="6a8d2-132">Sestavení testů můžete přeskočit přidáním argumentu `skiptests` do skriptu sestavení, jako v následujícím příkladu (nahraďte `.\build` `./build.sh` na počítačích se systémem UNIX):</span><span class="sxs-lookup"><span data-stu-id="6a8d2-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests
```

<span data-ttu-id="6a8d2-133">Předchozí příklad ukázal, jak sestavit `Debug` charakter, který má povolené kontroly doby vývoje (kontrolní výrazy) a optimalizace, které jsou zakázané.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="6a8d2-134">Chcete-li sestavit charakter vydaných verzí (s plnou rychlostí), postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="6a8d2-134">To build the release (full speed) flavor, do the following:</span></span>

```bat
    .\build release skiptests
```

<span data-ttu-id="6a8d2-135">Další možnosti sestavení můžete najít pomocí sestavení pomocí-?</span><span class="sxs-lookup"><span data-stu-id="6a8d2-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="6a8d2-136">nebo – kvalifikátor pomocníka.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-136">or -help qualifier.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="6a8d2-137">Použití sestavení</span><span class="sxs-lookup"><span data-stu-id="6a8d2-137">Using Your Build</span></span>

<span data-ttu-id="6a8d2-138">Sestavení umístí všechny své vygenerované soubory pod `bin` adresářem na bázi úložiště.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="6a8d2-139">K dispozici je adresář *bin\Log* , který obsahuje soubory protokolu generované během sestavení (nejužitečnější při neúspěšném sestavení).</span><span class="sxs-lookup"><span data-stu-id="6a8d2-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="6a8d2-140">Skutečný výstup je umístěný v *bin\Product\[platformě]. [Architektura procesoru]. [typ sestavení]* Adresář, například *bin\product\ Windows_NT. x64. Release*.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="6a8d2-141">Zatímco výstup "raw" sestavení je někdy užitečné, obvykle se zajímá pouze o balíčky NuGet, které jsou umístěny v podadresáři `.nuget\pkg` předchozího výstupního adresáře.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="6a8d2-142">Existují dvě základní techniky použití nového modulu runtime:</span><span class="sxs-lookup"><span data-stu-id="6a8d2-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="6a8d2-143">**K vytvoření aplikace použijte dotnet. exe a NuGet**.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="6a8d2-144">Pokyny k vytvoření programu, který používá váš nový modul runtime, pomocí balíčků NuGet, které jste právě vytvořili, a rozhraní příkazového řádku dotnet (CLI) najdete v tématu [použití sestavení](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-your-build.md) .</span><span class="sxs-lookup"><span data-stu-id="6a8d2-144">See [Using Your Build](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-your-build.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="6a8d2-145">Tato technika je předpokládaný způsob, jakým vývojáři mimo modul runtime využívají nový modul runtime.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>

 2. <span data-ttu-id="6a8d2-146">Pomocí souboru korutiny **. exe spusťte aplikaci pomocí nebalených knihoven DLL**.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="6a8d2-147">Toto úložiště také definuje jednoduchého hostitele s názvem spoluspustit. exe, který neprovádí žádnou závislost na NuGet.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="6a8d2-148">Je nutné sdělit hostiteli, kde mají získat požadované knihovny DLL, které skutečně používáte, a je nutné je ručně shromáždit společně.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="6a8d2-149">Tato technika je používána všemi testy v úložišti [dotnet/runtime](https://github.com/dotnet/runtime) a je užitečná pro rychlou místní smyčku "Edit-Compile-debug", jako je například předběžné testování částí.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-149">This technique is used by all the tests in the [dotnet/runtime](https://github.com/dotnet/runtime) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="6a8d2-150">Podrobnosti o použití této techniky najdete v tématu [spouštění aplikací .NET Core pomocí souboru. exe.](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-corerun.md)</span><span class="sxs-lookup"><span data-stu-id="6a8d2-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-corerun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="6a8d2-151">Sestavení CLI ze zdroje</span><span class="sxs-lookup"><span data-stu-id="6a8d2-151">Build the CLI from source</span></span>

<span data-ttu-id="6a8d2-152">Zdrojový kód pro .NET Core CLI lze nalézt v úložišti [dotnet/CLI](https://github.com/dotnet/cli/) na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="6a8d2-153">Aby bylo možné sestavit .NET Core CLI, potřebujete na svém počítači nainstalované následující.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

- <span data-ttu-id="6a8d2-154">Windows & Linux:</span><span class="sxs-lookup"><span data-stu-id="6a8d2-154">Windows & Linux:</span></span>
  - <span data-ttu-id="6a8d2-155">Git v cestě</span><span class="sxs-lookup"><span data-stu-id="6a8d2-155">git on the PATH</span></span>
- <span data-ttu-id="6a8d2-156">MacOS</span><span class="sxs-lookup"><span data-stu-id="6a8d2-156">macOS:</span></span>
  - <span data-ttu-id="6a8d2-157">Git v cestě</span><span class="sxs-lookup"><span data-stu-id="6a8d2-157">git on the PATH</span></span>
  - <span data-ttu-id="6a8d2-158">Xcode</span><span class="sxs-lookup"><span data-stu-id="6a8d2-158">Xcode</span></span>
  - <span data-ttu-id="6a8d2-159">OpenSSL</span><span class="sxs-lookup"><span data-stu-id="6a8d2-159">OpenSSL</span></span>

<span data-ttu-id="6a8d2-160">Aby bylo možné sestavovat, spouštět `build.cmd` ve Windows nebo `build.sh` v systémech Linux a macOS z kořenového adresáře.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="6a8d2-161">Pokud nechcete spouštět testy, spusťte `build.cmd -t:Compile` nebo `./build.sh -t:Compile`.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-161">If you don't want to execute tests, run `build.cmd -t:Compile` or `./build.sh -t:Compile`.</span></span> <span data-ttu-id="6a8d2-162">Chcete-li sestavit rozhraní příkazového řádku v macOS Sierra, je nutné nastavit proměnnou prostředí DOTNET_RUNTIME_ID spuštěním `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="6a8d2-163">Použití sestavení</span><span class="sxs-lookup"><span data-stu-id="6a8d2-163">Using your build</span></span>

<span data-ttu-id="6a8d2-164">K vyzkoušení nově vytvořeného rozhraní příkazového řádku použijte `dotnet` spustitelný soubor z *artefaktů/{OS} – {arch}/STAGE2* .</span><span class="sxs-lookup"><span data-stu-id="6a8d2-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="6a8d2-165">Pokud chcete použít výstup sestavení při vyvolání `dotnet` z aktuální konzoly, můžete také přidat *artefakty/{OS}-{arch}/STAGE2* do cesty.</span><span class="sxs-lookup"><span data-stu-id="6a8d2-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a8d2-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a8d2-166">See also</span></span>

- [<span data-ttu-id="6a8d2-167">Modul runtime .NET</span><span class="sxs-lookup"><span data-stu-id="6a8d2-167">.NET Runtime</span></span>](https://github.com/dotnet/runtime/blob/master/README.md)
- [<span data-ttu-id="6a8d2-168">.NET Core CLI příručka pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="6a8d2-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [<span data-ttu-id="6a8d2-169">Vytváření distribučních balíčků .NET Core</span><span class="sxs-lookup"><span data-stu-id="6a8d2-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
