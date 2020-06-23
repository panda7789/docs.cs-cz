---
title: 'Postupy: sestavení .NET Framework sestavení s jedním souborem'
description: Prozkoumejte, jak vytvořit sestavení s jedním souborem v rozhraní .NET. Sestavení s jedním souborem může být knihovna (. dll), která cílí na rozhraní .NET, nebo může být spustitelný soubor (. exe).
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: 482a973631e899b8d4bfc4640eef1ea26173605e
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104917"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a><span data-ttu-id="f8c9b-104">Postupy: sestavení .NET Framework sestavení s jedním souborem</span><span class="sxs-lookup"><span data-stu-id="f8c9b-104">How to: Build a .NET Framework single-file assembly</span></span>

<span data-ttu-id="f8c9b-105">Sestavení s jedním souborem, což je nejjednodušší typ sestavení, obsahuje informace o typu a implementaci a také [manifest sestavení](../../standard/assembly/manifest.md).</span><span class="sxs-lookup"><span data-stu-id="f8c9b-105">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../standard/assembly/manifest.md).</span></span> <span data-ttu-id="f8c9b-106">Pomocí kompilátorů příkazového řádku nebo sady Visual Studio můžete vytvořit sestavení s jedním souborem, které cílí na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-106">You can use command-line compilers or Visual Studio to create a single-file assembly that targets the .NET Framework.</span></span> <span data-ttu-id="f8c9b-107">Ve výchozím nastavení kompilátor vytvoří soubor sestavení s příponou *. exe* .</span><span class="sxs-lookup"><span data-stu-id="f8c9b-107">By default, the compiler creates an assembly file with an *.exe* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="f8c9b-108">Visual Studio pro C# a Visual Basic lze použít pouze k vytváření sestavení s jedním souborem.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-108">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="f8c9b-109">Chcete-li vytvořit vícesouborové sestavení, je nutné použít kompilátory příkazového řádku nebo Visual C++.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-109">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="f8c9b-110">Následující postupy ukazují, jak vytvořit sestavení s jedním souborem pomocí kompilátorů příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-110">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="f8c9b-111">Vytvoření sestavení s příponou. exe</span><span class="sxs-lookup"><span data-stu-id="f8c9b-111">Create an assembly with an .exe extension</span></span>

<span data-ttu-id="f8c9b-112">Do příkazového řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f8c9b-112">At the command prompt, type the following command:</span></span>

<span data-ttu-id="f8c9b-113">\<*compiler command*> \<*module name*></span><span class="sxs-lookup"><span data-stu-id="f8c9b-113">\<*compiler command*> \<*module name*></span></span>

<span data-ttu-id="f8c9b-114">V tomto příkazu je *příkaz kompilátoru* příkazem kompilátoru pro jazyk použitý v modulu kódu a *název modulu* je název modulu kódu, který se má kompilovat do sestavení.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-114">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="f8c9b-115">Následující příklad vytvoří sestavení s názvem *myCode.exe* z modulu Code s názvem `myCode` .</span><span class="sxs-lookup"><span data-stu-id="f8c9b-115">The following example creates an assembly named *myCode.exe* from a code module called `myCode`.</span></span>

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="f8c9b-116">Vytvořte sestavení s příponou. exe a zadejte název výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-116">Create an assembly with an .exe extension and specify the output file name</span></span>

<span data-ttu-id="f8c9b-117">Do příkazového řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f8c9b-117">At the command prompt, type the following command:</span></span>

<span data-ttu-id="f8c9b-118">\<*compiler command*>**/out:** \<*file name*>\<*module name*></span><span class="sxs-lookup"><span data-stu-id="f8c9b-118">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

<span data-ttu-id="f8c9b-119">V tomto příkazu je *příkaz kompilátoru* příkazem kompilátoru pro jazyk používaný v modulu kódu, *název souboru* je název výstupního souboru a *název modulu* je název modulu kódu, který má být zkompilován do sestavení.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-119">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

<span data-ttu-id="f8c9b-120">Následující příklad vytvoří sestavení s názvem *myAssembly.exe* z modulu Code s názvem `myCode` .</span><span class="sxs-lookup"><span data-stu-id="f8c9b-120">The following example creates an assembly named *myAssembly.exe* from a code module called `myCode`.</span></span>

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a><span data-ttu-id="f8c9b-121">Vytváření sestavení knihovny</span><span class="sxs-lookup"><span data-stu-id="f8c9b-121">Create library assemblies</span></span>
 <span data-ttu-id="f8c9b-122">Sestavení knihovny je podobné knihovně tříd.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-122">A library assembly is similar to a class library.</span></span> <span data-ttu-id="f8c9b-123">Obsahuje typy, které budou odkazovány jinými sestaveními, ale nemá žádný vstupní bod k zahájení provádění.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-123">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

<span data-ttu-id="f8c9b-124">Chcete-li vytvořit sestavení knihovny, zadejte na příkazovém řádku následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="f8c9b-124">To create a library assembly, at the command prompt, type the following command:</span></span>

<span data-ttu-id="f8c9b-125">\<*compiler command*>**– t:Library**\<*module name*></span><span class="sxs-lookup"><span data-stu-id="f8c9b-125">\<*compiler command*> **-t:library** \<*module name*></span></span>

<span data-ttu-id="f8c9b-126">V tomto příkazu je *příkaz kompilátoru* příkazem kompilátoru pro jazyk použitý v modulu kódu a *název modulu* je název modulu kódu, který se má kompilovat do sestavení.</span><span class="sxs-lookup"><span data-stu-id="f8c9b-126">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="f8c9b-127">Můžete také použít další možnosti kompilátoru, jako je například možnost **-out:** .</span><span class="sxs-lookup"><span data-stu-id="f8c9b-127">You can also use other compiler options, such as the **-out:** option.</span></span>

<span data-ttu-id="f8c9b-128">Následující příklad vytvoří sestavení knihovny s názvem *myCodeAssembly.dll* z modulu Code s názvem `myCode` .</span><span class="sxs-lookup"><span data-stu-id="f8c9b-128">The following example creates a library assembly named *myCodeAssembly.dll* from a code module called `myCode`.</span></span>

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="f8c9b-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8c9b-129">See also</span></span>

- [<span data-ttu-id="f8c9b-130">Vytváření sestavení</span><span class="sxs-lookup"><span data-stu-id="f8c9b-130">Create assemblies</span></span>](../../standard/assembly/create.md)
- [<span data-ttu-id="f8c9b-131">Vícesouborová sestavení</span><span class="sxs-lookup"><span data-stu-id="f8c9b-131">Multifile assemblies</span></span>](multifile-assemblies.md)
- [<span data-ttu-id="f8c9b-132">Postupy: Vytváření vícesouborového sestavení</span><span class="sxs-lookup"><span data-stu-id="f8c9b-132">How to: Build a multifile assembly</span></span>](build-multifile-assembly.md)
- [<span data-ttu-id="f8c9b-133">Programování se sestaveními</span><span class="sxs-lookup"><span data-stu-id="f8c9b-133">Program with assemblies</span></span>](../../standard/assembly/index.md)
