---
title: -linkresource (C# Možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: 41af8e0ba8ffebd07d3cb1d2bc5fbc04b8cd595d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173728"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="992dd-102">-linkresource (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="992dd-102">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="992dd-103">Vytvoří odkaz na prostředek rozhraní .NET Framework ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="992dd-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="992dd-104">Soubor prostředků není přidán do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="992dd-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="992dd-105">To se liší od [-resource](./resource-compiler-option.md) možnost, která se vložit soubor prostředků ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="992dd-105">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="992dd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="992dd-106">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="992dd-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="992dd-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="992dd-108">Soubor prostředku rozhraní .NET Framework, ke kterému chcete vytvořit propojení ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="992dd-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="992dd-109">`identifier` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="992dd-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="992dd-110">Logický název prostředku; název, který se používá k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="992dd-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="992dd-111">Výchozí je název souboru.</span><span class="sxs-lookup"><span data-stu-id="992dd-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="992dd-112">`accessibility-modifier` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="992dd-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="992dd-113">Dostupnost zdroje: veřejné nebo soukromé.</span><span class="sxs-lookup"><span data-stu-id="992dd-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="992dd-114">Výchozí hodnota je veřejná.</span><span class="sxs-lookup"><span data-stu-id="992dd-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="992dd-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="992dd-115">Remarks</span></span>  
 <span data-ttu-id="992dd-116">Ve výchozím nastavení jsou propojené prostředky veřejné v sestavení při jejich vytvoření pomocí kompilátoru Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="992dd-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="992dd-117">Chcete-li prostředky jako `private` modifikátor usnadnění zadat jako soukromý.</span><span class="sxs-lookup"><span data-stu-id="992dd-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="992dd-118">Žádný jiný modifikátor než `public` nebo `private` je povolen.</span><span class="sxs-lookup"><span data-stu-id="992dd-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="992dd-119">**-linkresource** vyžaduje jednu z možností [-target](./target-compiler-option.md) než **-target:module**.</span><span class="sxs-lookup"><span data-stu-id="992dd-119">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="992dd-120">Pokud `filename` je soubor prostředků rozhraní .NET Framework vytvořený například [programem Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat pomocí členů v oboru <xref:System.Resources> názvů.</span><span class="sxs-lookup"><span data-stu-id="992dd-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="992dd-121">Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="992dd-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="992dd-122">Pro všechny ostatní prostředky `GetManifestResource` použijte <xref:System.Reflection.Assembly> metody ve třídě pro přístup k prostředku za běhu.</span><span class="sxs-lookup"><span data-stu-id="992dd-122">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="992dd-123">Soubor zadaný `filename` v může být libovolný formát.</span><span class="sxs-lookup"><span data-stu-id="992dd-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="992dd-124">Můžete například chtít vytvořit nativní součást sestavení DLL, aby mohla být nainstalována do globální mezipaměti sestavení a přístupná ze spravovaného kódu v sestavení.</span><span class="sxs-lookup"><span data-stu-id="992dd-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="992dd-125">Druhý z následujících příkladů ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="992dd-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="992dd-126">Totéž můžete provést v propojovacím zařízení sestavení.</span><span class="sxs-lookup"><span data-stu-id="992dd-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="992dd-127">Třetí z následujících příkladů ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="992dd-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="992dd-128">Další informace naleznete v [tématu Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) a [práce se sestaveními a globální mezipaměti sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="992dd-128">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="992dd-129">**-linkres** je krátká forma **-linkresource**.</span><span class="sxs-lookup"><span data-stu-id="992dd-129">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="992dd-130">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.</span><span class="sxs-lookup"><span data-stu-id="992dd-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="992dd-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="992dd-131">Example</span></span>  
 <span data-ttu-id="992dd-132">Kompilace `in.cs` a propojení `rf.resource`se souborem prostředků :</span><span class="sxs-lookup"><span data-stu-id="992dd-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="992dd-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="992dd-133">Example</span></span>  
 <span data-ttu-id="992dd-134">Kompilace `A.cs` do dll, odkaz na nativní DLL N.dll a umístit výstup do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="992dd-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="992dd-135">V tomto příkladu bude v gac umístěny a.dll i N.dll.</span><span class="sxs-lookup"><span data-stu-id="992dd-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="992dd-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="992dd-136">Example</span></span>  
 <span data-ttu-id="992dd-137">Tento příklad dělá totéž jako předchozí, ale pomocí možnosti propojovacího nástroje sestavení.</span><span class="sxs-lookup"><span data-stu-id="992dd-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="992dd-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="992dd-138">See also</span></span>

- [<span data-ttu-id="992dd-139">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="992dd-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="992dd-140">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="992dd-140">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="992dd-141">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="992dd-141">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="992dd-142">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="992dd-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
