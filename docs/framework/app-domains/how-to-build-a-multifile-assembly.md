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
ms.openlocfilehash: 3072be4e870b64edcea32bb7159db8c64c50d840
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183097"
---
# <a name="how-to-build-a-multifile-assembly"></a><span data-ttu-id="2f137-102">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="2f137-102">How to: Build a Multifile Assembly</span></span>
<span data-ttu-id="2f137-103">Tento článek vysvětluje, jak vytvořit vícesouborové sestavení a obsahuje kód, který ukazuje každý krok v postupu.</span><span class="sxs-lookup"><span data-stu-id="2f137-103">This article explains how to create a multifile assembly and provides code that illustrates each step in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f137-104">Visual Studio IDE rozhraním C# a Visual Basic můžete použít jenom k vytvoření jednosouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f137-104">The Visual Studio IDE for C# and Visual Basic can only be used to create single-file assemblies.</span></span> <span data-ttu-id="2f137-105">Pokud chcete vytvořit vícesouborové sestavení, musíte použít kompilátory příkazového řádku nebo Visual Studio s Visual C++.</span><span class="sxs-lookup"><span data-stu-id="2f137-105">If you want to create multifile assemblies, you must use the command-line compilers or Visual Studio with Visual C++.</span></span>  
  
### <a name="to-create-a-multifile-assembly"></a><span data-ttu-id="2f137-106">K vytvoření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="2f137-106">To create a multifile assembly</span></span>  
  
1.  <span data-ttu-id="2f137-107">Zkompilujte všechny soubory, které obsahují obory názvů odkazované jinými moduly v sestavení, do modulů kódu.</span><span class="sxs-lookup"><span data-stu-id="2f137-107">Compile all files that contain namespaces referenced by other modules in the assembly into code modules.</span></span> <span data-ttu-id="2f137-108">Výchozí přípona pro moduly kódu je .netmodule.</span><span class="sxs-lookup"><span data-stu-id="2f137-108">The default extension for code modules is .netmodule.</span></span>  
  
     <span data-ttu-id="2f137-109">Předpokládejme například, že `Stringer` soubor má obor názvů s názvem `myStringer`, který obsahuje třídy nazvané `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="2f137-109">For example, let's say the `Stringer` file has a namespace called `myStringer`, which includes a class called `Stringer`.</span></span> <span data-ttu-id="2f137-110">`Stringer` Třída obsahuje metodu nazvanou `StringerMethod` jeden řádek, který zapisuje do konzoly.</span><span class="sxs-lookup"><span data-stu-id="2f137-110">The `Stringer` class contains a method called `StringerMethod` that writes a single line to the console.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     <span data-ttu-id="2f137-111">Chcete-li tento kód zkompilovat, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="2f137-111">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     <span data-ttu-id="2f137-112">Zadání *modulu* parametr **t:** – možnost kompilátoru označuje, že soubor by měl být zkompilován jako modul, nikoli jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f137-112">Specifying the *module* parameter with the **/t:** compiler option indicates that the file should be compiled as a module rather than as an assembly.</span></span> <span data-ttu-id="2f137-113">Kompilátor vytvoří modul s názvem `Stringer.netmodule`, který lze přidat do sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f137-113">The compiler produces a module called `Stringer.netmodule`, which can be added to an assembly.</span></span>  
  
2.  <span data-ttu-id="2f137-114">Zkompilujte všechny ostatní moduly pomocí nezbytných možností kompilátoru k označení modulů, které jsou odkazovány v kódu.</span><span class="sxs-lookup"><span data-stu-id="2f137-114">Compile all other modules, using the necessary compiler options to indicate the other modules that are referenced in the code.</span></span> <span data-ttu-id="2f137-115">Tento krok používá **/addmodule** – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2f137-115">This step uses the **/addmodule** compiler option.</span></span>  
  
     <span data-ttu-id="2f137-116">V následujícím příkladu se modul kódu s názvem `Client` má vstupní bod `Main` metodu, která odkazuje na metodu v `Stringer.dll` modulu vytvořili v kroku 1.</span><span class="sxs-lookup"><span data-stu-id="2f137-116">In the following example, a code module called `Client` has an entry point `Main` method that references a method in the `Stringer.dll` module created in step 1.</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     <span data-ttu-id="2f137-117">Chcete-li tento kód zkompilovat, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="2f137-117">Use the following command to compile this code:</span></span>  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     <span data-ttu-id="2f137-118">Zadejte **/t: Module** možnost, protože tento modul bude přidán do sestavení v příštím kroku.</span><span class="sxs-lookup"><span data-stu-id="2f137-118">Specify the **/t:module** option because this module will be added to an assembly in a future step.</span></span> <span data-ttu-id="2f137-119">Zadejte **/addmodule** možnost, protože kód v `Client` odkazuje na obor názvů vytvořený kódem v `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="2f137-119">Specify the **/addmodule** option because the code in `Client` references a namespace created by the code in `Stringer.netmodule`.</span></span> <span data-ttu-id="2f137-120">Kompilátor vytvoří modul s názvem `Client.netmodule` , který obsahuje odkaz na jiný modul `Stringer.netmodule`.</span><span class="sxs-lookup"><span data-stu-id="2f137-120">The compiler produces a module called `Client.netmodule` that contains a reference to another module, `Stringer.netmodule`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2f137-121">C# a kompilátory jazyka Visual Basic podporují přímé vytváření vícesouborových sestavení pomocí dvou následujících různých syntaxí.</span><span class="sxs-lookup"><span data-stu-id="2f137-121">The C# and Visual Basic compilers support directly creating multifile assemblies using the following two different syntaxes.</span></span>  
    >   
    >  -   <span data-ttu-id="2f137-122">Dvě kompilace vytvoří dvousouborové sestavení:</span><span class="sxs-lookup"><span data-stu-id="2f137-122">Two compilations create a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   <span data-ttu-id="2f137-123">Jedna kompilace vytvoří dvousouborové sestavení:</span><span class="sxs-lookup"><span data-stu-id="2f137-123">One compilation creates a two-file assembly:</span></span>  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  <span data-ttu-id="2f137-124">Použití [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) se vytvořit výstupní soubor, který obsahuje manifest sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f137-124">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the output file that contains the assembly manifest.</span></span> <span data-ttu-id="2f137-125">Tento soubor obsahuje referenční informace pro všechny moduly nebo prostředky, které jsou součástí sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f137-125">This file contains reference information for all modules or resources that are part of the assembly.</span></span>  
  
     <span data-ttu-id="2f137-126">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="2f137-126">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="2f137-127">**Al** \< *název modulu*> \<*název modulu*>...</span><span class="sxs-lookup"><span data-stu-id="2f137-127">**al** \<*module name*> \<*module name*> …</span></span> <span data-ttu-id="2f137-128">**/ main:**\<*název metody*> **/out:**\<*název_souboru*>   **/target :**\<*typ souboru sestavení*></span><span class="sxs-lookup"><span data-stu-id="2f137-128">**/main:**\<*method name*> **/out:**\<*file name*> **/target:**\<*assembly file type*></span></span>  
  
     <span data-ttu-id="2f137-129">V tomto příkazu *název modulu* argumenty určují název každého modulu, který chcete zahrnout do sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f137-129">In this command, the *module name* arguments specify the name of each module to include in the assembly.</span></span> <span data-ttu-id="2f137-130">**/Main:** Určuje název metody, která je vstupním bodem sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f137-130">The **/main:** option specifies the method name that is the assembly's entry point.</span></span> <span data-ttu-id="2f137-131">**/Out:** parametr určuje název výstupního souboru, který obsahuje metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f137-131">The **/out:** option specifies the name of the output file, which contains assembly metadata.</span></span> <span data-ttu-id="2f137-132">**/Target:** možnost určuje, že je sestavení spustitelný soubor (.exe) soubor konzoly aplikace, soubor Windows (.win) spustitelný soubor nebo soubor knihovny (.lib).</span><span class="sxs-lookup"><span data-stu-id="2f137-132">The **/target:** option specifies that the assembly is a console application executable (.exe) file, a Windows executable (.win) file, or a library (.lib) file.</span></span>  
  
     <span data-ttu-id="2f137-133">V následujícím příkladu vytvoří Al.exe sestavení, které je spustitelným souborem konzolové aplikace volá `myAssembly.exe`.</span><span class="sxs-lookup"><span data-stu-id="2f137-133">In the following example, Al.exe creates an assembly that is a console application executable called `myAssembly.exe`.</span></span> <span data-ttu-id="2f137-134">Aplikace se skládá ze dvou modulů s názvy `Client.netmodule` a `Stringer.netmodule`, spustitelný soubor s názvem `myAssembly.exe,` obsahující jenom metadata sestavení.</span><span class="sxs-lookup"><span data-stu-id="2f137-134">The application consists of two modules called `Client.netmodule` and `Stringer.netmodule`, and the executable file called `myAssembly.exe,` which contains only assembly metadata.</span></span> <span data-ttu-id="2f137-135">Vstupní bod sestavení je `Main` metody ve třídě `MainClientApp`, který se nachází v `Client.dll`.</span><span class="sxs-lookup"><span data-stu-id="2f137-135">The entry point of the assembly is the `Main` method in the class `MainClientApp`, which is located in `Client.dll`.</span></span>  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     <span data-ttu-id="2f137-136">Můžete použít [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zkontrolovat obsah sestavení nebo zjistit, zda je soubor sestavení nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="2f137-136">You can use the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to examine the contents of an assembly, or determine whether a file is an assembly or a module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f137-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f137-137">See Also</span></span>  
- [<span data-ttu-id="2f137-138">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="2f137-138">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
- [<span data-ttu-id="2f137-139">Postupy: Zobrazení obsahu sestavení</span><span class="sxs-lookup"><span data-stu-id="2f137-139">How to: View Assembly Contents</span></span>](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
- [<span data-ttu-id="2f137-140">Jak běhové prostředí vyhledává sestavení</span><span class="sxs-lookup"><span data-stu-id="2f137-140">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [<span data-ttu-id="2f137-141">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="2f137-141">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
