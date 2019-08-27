---
title: 'Postupy: Vytváření vícesouborového sestavení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a964e73cc41cebad33a3edc34b89ef240fbc62c8
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040859"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="c1d8e-102">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="c1d8e-102">How to: Build a Multifile Assembly</span></span>

<span data-ttu-id="c1d8e-103">Tento článek vysvětluje, jak vytvořit vícesouborové sestavení a poskytuje kód, který ukazuje každý krok v proceduře.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="c1d8e-104">Integrované vývojové prostředí (IDE C# ) sady Visual Studio pro a Visual Basic lze použít pouze k vytváření sestavení s jedním souborem.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="c1d8e-105">Chcete-li vytvořit vícesouborové sestavení, je nutné použít kompilátory příkazového řádku nebo aplikaci Visual Studio se sadou Visual C++Studio.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>

### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="c1d8e-106">Vytvoření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="c1d8e-106">To create a multifile assembly</span></span>

01. <span data-ttu-id="c1d8e-107">Zkompilujte všechny soubory, které obsahují obory názvů odkazované jinými moduly v sestavení, do modulů kódu.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="c1d8e-108">Výchozím rozšířením pro moduly kódu je. netmodule.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-108">The default extension for code modules is .netmodule.</span></span>

    <span data-ttu-id="c1d8e-109">Řekněme například, že `Stringer` soubor obsahuje obor názvů s názvem `myStringer`, který obsahuje třídu s názvem `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="c1d8e-110">Třída obsahuje metodu s názvem `StringerMethod` , která zapisuje jednu čáru do konzoly. `Stringer`</span><span class="sxs-lookup"><span data-stu-id="c1d8e-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
    [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
    [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]

    <span data-ttu-id="c1d8e-111">Pro zkompilování tohoto kódu použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="c1d8e-111">Use the following command to compile this code:</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
    [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
    [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]

    <span data-ttu-id="c1d8e-112">Zadání parametru *Module* s možností kompilátoru **/t:** označuje, že soubor by měl být zkompilován jako modul, nikoli jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-112">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="c1d8e-113">Kompilátor vytvoří modul s názvem `Stringer.netmodule`, který lze přidat do sestavení.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-113">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>

02. <span data-ttu-id="c1d8e-114">Zkompilujte všechny ostatní moduly pomocí nezbytných možností kompilátoru k označení dalších modulů, které jsou odkazovány v kódu.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-114">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="c1d8e-115">Tento krok používá možnost kompilátoru **/addmodule** .</span><span class="sxs-lookup"><span data-stu-id="c1d8e-115">This step uses the **/addmodule** compiler option.</span></span>

    <span data-ttu-id="c1d8e-116">V následujícím příkladu má modul kódu s názvem `Client` metodu vstupního bodu `Main` , která `Stringer.dll` odkazuje na metodu v modulu vytvořenou v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-116">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
    [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
    [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]

    <span data-ttu-id="c1d8e-117">Pro zkompilování tohoto kódu použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="c1d8e-117">Use the following command to compile this code:</span></span>

    [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
    [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
    [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]

    <span data-ttu-id="c1d8e-118">Zadejte možnost **/t: Module** , protože tento modul se přidá do sestavení v budoucím kroku.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-118">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="c1d8e-119">Určete možnost **/addmodule** , protože kód v `Client` odkazuje na obor názvů vytvořený kódem v. `Stringer.netmodule`</span><span class="sxs-lookup"><span data-stu-id="c1d8e-119">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="c1d8e-120">Kompilátor vytvoří modul s názvem `Client.netmodule` , který obsahuje odkaz na jiný modul,. `Stringer.netmodule`</span><span class="sxs-lookup"><span data-stu-id="c1d8e-120">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>

    >[!NOTE]
    ><span data-ttu-id="c1d8e-121">Kompilátory C# a Visual Basic podporují přímé vytváření vícesouborového sestavení pomocí následujících dvou různých syntaxí.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-121">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>
    >
    >- <span data-ttu-id="c1d8e-122">Dvě kompilace vytvoří sestavení se dvěma soubory:[!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]</span><span class="sxs-lookup"><span data-stu-id="c1d8e-122">Two compilations create a two-file assembly: [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]</span></span>
    >  [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
    >  [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]
    >
    >- <span data-ttu-id="c1d8e-123">Jedna kompilace vytvoří sestavení se dvěma soubory:[!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]</span><span class="sxs-lookup"><span data-stu-id="c1d8e-123">One compilation creates a two-file assembly: [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]</span></span>
    >  [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
    >  [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]

03. <span data-ttu-id="c1d8e-124">Použijte [linker sestavení (Al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) k vytvoření výstupního souboru, který obsahuje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-124">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="c1d8e-125">Tento soubor obsahuje referenční informace pro všechny moduly nebo prostředky, které jsou součástí sestavení.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-125">This file contains reference information for all modules or resources that are part of the assembly.</span></span>

    <span data-ttu-id="c1d8e-126">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="c1d8e-126">At the command prompt, type the following command:</span></span>

    <span data-ttu-id="c1d8e-127">**Al** \<*název modulu*název modulu >...> \<</span><span class="sxs-lookup"><span data-stu-id="c1d8e-127">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="c1d8e-128">**/Main:** \<*název\*\*\*metody/out:*\* název souboru/target:\<*typ souboru* sestavení\<> > ></span><span class="sxs-lookup"><span data-stu-id="c1d8e-128">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>

    <span data-ttu-id="c1d8e-129">V tomto příkazu argumenty *názvu modulu* určují název každého modulu, který chcete zahrnout do sestavení.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-129">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="c1d8e-130">Parametr **/Main:** Určuje název metody, která je vstupním bodem sestavení.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-130">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="c1d8e-131">Možnost **/out:** Určuje název výstupního souboru, který obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-131">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="c1d8e-132">Možnost **/target:** určuje, že sestavení je spustitelný soubor aplikace konzoly (. exe), spustitelný soubor systému Windows (. Win) nebo soubor knihovny (. lib).</span><span class="sxs-lookup"><span data-stu-id="c1d8e-132">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>

    <span data-ttu-id="c1d8e-133">V následujícím příkladu Al. exe vytvoří sestavení, které je spustitelný soubor aplikace konzoly s názvem `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-133">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="c1d8e-134">Aplikace se skládá ze dvou modulů `Client.netmodule` nazvaných `Stringer.netmodule`a a spustitelného souboru s `myAssembly.exe,` názvem, který obsahuje pouze metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-134">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata.</span></span> <span data-ttu-id="c1d8e-135">Vstupním bodem sestavení je `Main` metoda ve třídě `MainClientApp`, která je umístěna v `Client.dll`.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-135">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>

    ```
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    <span data-ttu-id="c1d8e-136">Můžete použít [jazyk MSIL Disassembler (Ildasm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) k prohlédnutí obsahu sestavení nebo určení, zda je soubor sestavením nebo modulem.</span><span class="sxs-lookup"><span data-stu-id="c1d8e-136">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1d8e-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1d8e-137">See also</span></span>

- [<span data-ttu-id="c1d8e-138">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="c1d8e-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="c1d8e-139">Postupy: Zobrazit obsah sestavení</span><span class="sxs-lookup"><span data-stu-id="c1d8e-139">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)
- [<span data-ttu-id="c1d8e-140">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="c1d8e-140">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="c1d8e-141">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="c1d8e-141">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
