---
title: 'Postupy: Vytváření sestavení s jediným souborem'
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a73b2d8948c9a046fd77c02f1bcc87f5738105d9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303996"
---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="f53e6-102">Postupy: Vytváření sestavení s jediným souborem</span><span class="sxs-lookup"><span data-stu-id="f53e6-102">How to: Build a Single-File Assembly</span></span>

<span data-ttu-id="f53e6-103">Jeden soubor sestavení, které se o nejjednodušší typ sestavení, obsahuje informace o typu a implementaci, jakož i [manifestu sestavení](../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="f53e6-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="f53e6-104">Kompilátory příkazového řádku nebo Visual Studio můžete použít k vytvoření jednosouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="f53e6-104">You can use command-line compilers or Visual Studio to create a single-file assembly.</span></span> <span data-ttu-id="f53e6-105">Ve výchozím nastavení kompilátor vytvoří sestavení soubor s příponou .exe.</span><span class="sxs-lookup"><span data-stu-id="f53e6-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>

> [!NOTE]
> <span data-ttu-id="f53e6-106">Visual Studio pro C# a Visual Basic lze použít pouze k vytvoření jednosouborového sestavení.</span><span class="sxs-lookup"><span data-stu-id="f53e6-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="f53e6-107">Pokud chcete vytvořit vícesouborové sestavení, musíte použít kompilátory příkazového řádku nebo Visual C++.</span><span class="sxs-lookup"><span data-stu-id="f53e6-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="f53e6-108">Následující postupy ukazují, jak vytvořit jeden soubor sestavení použití kompilátorů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f53e6-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="f53e6-109">K vytvoření sestavení s příponou .exe</span><span class="sxs-lookup"><span data-stu-id="f53e6-109">To create an assembly with an .exe extension</span></span>

1. <span data-ttu-id="f53e6-110">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f53e6-110">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="f53e6-111">\<*příkaz kompilátoru*> \<*název modulu*></span><span class="sxs-lookup"><span data-stu-id="f53e6-111">\<*compiler command*> \<*module name*></span></span>

     <span data-ttu-id="f53e6-112">V tomto příkazu *kompilátoru příkaz* je příkaz kompilátor pro jazyk používaný v modulu kódu, a *název modulu* je název modulu kódu zkompilovat do sestavení.</span><span class="sxs-lookup"><span data-stu-id="f53e6-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

 <span data-ttu-id="f53e6-113">Následující příklad vytvoří sestavení s názvem `myCode.exe` z modulu kódu volá `myCode`.</span><span class="sxs-lookup"><span data-stu-id="f53e6-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>

```console
csc myCode.cs
```

```console
vbc myCode.vb
```

### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="f53e6-114">K vytvoření sestavení s příponou .exe a určuje název výstupního souboru</span><span class="sxs-lookup"><span data-stu-id="f53e6-114">To create an assembly with an .exe extension and specify the output file name</span></span>

1. <span data-ttu-id="f53e6-115">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f53e6-115">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="f53e6-116">\<*příkaz kompilátoru*> **/out:**\<*název_souboru*> \<*název modulu*></span><span class="sxs-lookup"><span data-stu-id="f53e6-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

     <span data-ttu-id="f53e6-117">V tomto příkazu *kompilátoru příkaz* je příkaz kompilátor pro jazyk používaný v modulu kódu, *název_souboru* je název výstupního souboru a *název modulu* je název Kód modulu je kompilována do sestavení.</span><span class="sxs-lookup"><span data-stu-id="f53e6-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

 <span data-ttu-id="f53e6-118">Následující příklad vytvoří sestavení s názvem `myAssembly.exe` z modulu kódu volá `myCode`.</span><span class="sxs-lookup"><span data-stu-id="f53e6-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>

```console
csc -out:myAssembly.exe myCode.cs
```

```console
vbc -out:myAssembly.exe myCode.vb
```

## <a name="creating-library-assemblies"></a><span data-ttu-id="f53e6-119">Vytváření sestavení knihovny</span><span class="sxs-lookup"><span data-stu-id="f53e6-119">Creating Library Assemblies</span></span>
 <span data-ttu-id="f53e6-120">Sestavení knihovny je podobný knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="f53e6-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="f53e6-121">Obsahuje typy, které se odkazuje jiná sestavení, ale nemá žádný vstupní bod zahájit provádění.</span><span class="sxs-lookup"><span data-stu-id="f53e6-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

### <a name="to-create-a-library-assembly"></a><span data-ttu-id="f53e6-122">Chcete-li vytvořit sestavení knihovny</span><span class="sxs-lookup"><span data-stu-id="f53e6-122">To create a library assembly</span></span>

1. <span data-ttu-id="f53e6-123">V příkazovém řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f53e6-123">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="f53e6-124">\<*příkaz kompilátoru*> **- t: Knihovna** \< *název modulu*></span><span class="sxs-lookup"><span data-stu-id="f53e6-124">\<*compiler command*> **-t:library** \<*module name*></span></span>

     <span data-ttu-id="f53e6-125">V tomto příkazu *kompilátoru příkaz* je příkaz kompilátor pro jazyk používaný v modulu kódu, a *název modulu* je název modulu kódu zkompilovat do sestavení.</span><span class="sxs-lookup"><span data-stu-id="f53e6-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="f53e6-126">Můžete také použít jiné možnosti kompilátoru, jako **-out:** možnost.</span><span class="sxs-lookup"><span data-stu-id="f53e6-126">You can also use other compiler options, such as the **-out:** option.</span></span>

 <span data-ttu-id="f53e6-127">Následující příklad vytvoří sestavení knihovny s názvem `myCodeAssembly.dll` z modulu kódu volá `myCode`.</span><span class="sxs-lookup"><span data-stu-id="f53e6-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>

```console
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="f53e6-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f53e6-128">See also</span></span>

- [<span data-ttu-id="f53e6-129">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="f53e6-129">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="f53e6-130">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="f53e6-130">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="f53e6-131">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="f53e6-131">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="f53e6-132">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="f53e6-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)