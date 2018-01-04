---
title: "Postupy: Vytváření sestavení s jediným souborem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd9f2bab23fff1bbc4ebb521b167ac8031af3bc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="82e71-102">Postupy: Vytváření sestavení s jediným souborem</span><span class="sxs-lookup"><span data-stu-id="82e71-102">How to: Build a Single-File Assembly</span></span>
<span data-ttu-id="82e71-103">Jeden soubor sestavení, které je nejjednodušší typ sestavení, obsahuje informace o typu a implementace, a taky [manifest sestavení](../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="82e71-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="82e71-104">Můžete použít kompilátory příkazového řádku nebo [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] vytvořit jeden soubor sestavení.</span><span class="sxs-lookup"><span data-stu-id="82e71-104">You can use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to create a single-file assembly.</span></span> <span data-ttu-id="82e71-105">Ve výchozím nastavení vytvoří kompilátor soubor sestavení s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="82e71-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]<span data-ttu-id="82e71-106">pro C# a Visual Basic lze použít pouze k vytvoření sestavení tvořená jedním souborem.</span><span class="sxs-lookup"><span data-stu-id="82e71-106"> for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="82e71-107">Pokud chcete vytvořit vícesouborového sestavení, musíte použít kompilátory příkazového řádku nebo [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] pro Visual C++.</span><span class="sxs-lookup"><span data-stu-id="82e71-107">If you want to create multifile assemblies, you must use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++.</span></span>  
  
 <span data-ttu-id="82e71-108">Následující postupy ukazují, jak vytvořit jeden soubor sestavení pomocí kompilátory příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="82e71-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="82e71-109">Chcete-li vytvořit sestavení s příponou .exe</span><span class="sxs-lookup"><span data-stu-id="82e71-109">To create an assembly with an .exe extension</span></span>  
  
1.  <span data-ttu-id="82e71-110">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="82e71-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="82e71-111">\<*příkaz kompilátoru*> \<*název modulu*></span><span class="sxs-lookup"><span data-stu-id="82e71-111">\<*compiler command*> \<*module name*></span></span>  
  
     <span data-ttu-id="82e71-112">V tomto příkazu *kompilátoru příkaz* je příkaz kompilátoru pro jazyk použitý v modulu kódu, a *název modulu* je název modulu kódu ke kompilaci do sestavení.</span><span class="sxs-lookup"><span data-stu-id="82e71-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="82e71-113">Následující příklad vytvoří sestavení s názvem `myCode.exe` z modulu kódu názvem `myCode`.</span><span class="sxs-lookup"><span data-stu-id="82e71-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="82e71-114">Vytvoření sestavení s příponou .exe a zadejte název výstupního souboru</span><span class="sxs-lookup"><span data-stu-id="82e71-114">To create an assembly with an .exe extension and specify the output file name</span></span>  
  
1.  <span data-ttu-id="82e71-115">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="82e71-115">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="82e71-116">\<*příkaz kompilátoru*> **/out:**\<*název souboru*> \<*název modulu*></span><span class="sxs-lookup"><span data-stu-id="82e71-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>  
  
     <span data-ttu-id="82e71-117">V tomto příkazu *kompilátoru příkaz* je příkaz kompilátoru pro jazyk použitý v modulu kódu, *název souboru* je název výstupního souboru, a *název modulu* je název modul kódu ke kompilaci do sestavení.</span><span class="sxs-lookup"><span data-stu-id="82e71-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="82e71-118">Následující příklad vytvoří sestavení s názvem `myAssembly.exe` z modulu kódu názvem `myCode`.</span><span class="sxs-lookup"><span data-stu-id="82e71-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a><span data-ttu-id="82e71-119">Vytváření sestavení knihovny</span><span class="sxs-lookup"><span data-stu-id="82e71-119">Creating Library Assemblies</span></span>  
 <span data-ttu-id="82e71-120">Sestavení knihovny je podobná knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="82e71-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="82e71-121">Obsahuje typy, které se odkazuje ostatních sestavení, ale nemá žádné vstupní bod zahájit provádění.</span><span class="sxs-lookup"><span data-stu-id="82e71-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>  
  
#### <a name="to-create-a-library-assembly"></a><span data-ttu-id="82e71-122">Chcete-li vytvořit sestavení knihovny</span><span class="sxs-lookup"><span data-stu-id="82e71-122">To create a library assembly</span></span>  
  
1.  <span data-ttu-id="82e71-123">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="82e71-123">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="82e71-124">\<*příkaz kompilátoru*> **/t:library** \< *název modulu*></span><span class="sxs-lookup"><span data-stu-id="82e71-124">\<*compiler command*> **/t:library** \<*module name*></span></span>  
  
     <span data-ttu-id="82e71-125">V tomto příkazu *kompilátoru příkaz* je příkaz kompilátoru pro jazyk použitý v modulu kódu, a *název modulu* je název modulu kódu ke kompilaci do sestavení.</span><span class="sxs-lookup"><span data-stu-id="82e71-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="82e71-126">Můžete také použít jiné možnosti kompilátoru, jako **/out:** možnost.</span><span class="sxs-lookup"><span data-stu-id="82e71-126">You can also use other compiler options, such as the **/out:** option.</span></span>  
  
 <span data-ttu-id="82e71-127">Následující příklad vytvoří sestavení knihovny s názvem `myCodeAssembly.dll` z modulu kódu názvem `myCode`.</span><span class="sxs-lookup"><span data-stu-id="82e71-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="82e71-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="82e71-128">See Also</span></span>  
 [<span data-ttu-id="82e71-129">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="82e71-129">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="82e71-130">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="82e71-130">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 [<span data-ttu-id="82e71-131">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="82e71-131">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="82e71-132">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="82e71-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
