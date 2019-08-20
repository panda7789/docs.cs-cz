---
title: -linkresource – (C# možnosti kompilátoru)
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
ms.openlocfilehash: 454915454f3faf15933257f3e3e221afec51d0ee
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606763"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="44991-102">-linkresource – (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="44991-102">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="44991-103">Vytvoří odkaz na prostředek .NET Framework ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="44991-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="44991-104">Soubor prostředků se nepřidá do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="44991-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="44991-105">To se liší od možnosti [-Resource](./resource-compiler-option.md) , která vloží soubor prostředků do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="44991-105">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44991-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44991-106">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="44991-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="44991-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="44991-108">.NET Framework soubor prostředků, na který chcete propojit ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="44991-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="44991-109">`identifier`volitelné</span><span class="sxs-lookup"><span data-stu-id="44991-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="44991-110">Logický název prostředku; název, který se použije k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="44991-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="44991-111">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="44991-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="44991-112">`accessibility-modifier`volitelné</span><span class="sxs-lookup"><span data-stu-id="44991-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="44991-113">Přístupnost prostředku: Public nebo Private.</span><span class="sxs-lookup"><span data-stu-id="44991-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="44991-114">Výchozí hodnota je Public.</span><span class="sxs-lookup"><span data-stu-id="44991-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44991-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44991-115">Remarks</span></span>  
 <span data-ttu-id="44991-116">Ve výchozím nastavení jsou propojené prostředky v sestavení veřejné, když jsou vytvořeny pomocí C# kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="44991-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="44991-117">Chcete-li zajistit soukromí prostředků, `private` zadejte jako modifikátor přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="44991-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="44991-118">Žádný jiný modifikátor `public` `private` není povolený.</span><span class="sxs-lookup"><span data-stu-id="44991-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="44991-119">**-linkresource –** vyžaduje jednu z možností [TARGETu](./target-compiler-option.md) s výjimkou **target: Module**.</span><span class="sxs-lookup"><span data-stu-id="44991-119">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="44991-120">Pokud `filename` je vytvořen soubor prostředků .NET Framework, například pomocí nástroje [Resgen. exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat <xref:System.Resources> pomocí členů v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="44991-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="44991-121">Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="44991-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="44991-122">Pro všechny ostatní prostředky použijte `GetManifestResource` metody <xref:System.Reflection.Assembly> ve třídě pro přístup k prostředku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="44991-122">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="44991-123">Soubor určený v `filename` může být libovolného formátu.</span><span class="sxs-lookup"><span data-stu-id="44991-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="44991-124">Například můžete chtít vytvořit nativní knihovnu DLL součásti sestavení, aby mohla být nainstalována do globální mezipaměti sestavení (GAC) a zpřístupněna ze spravovaného kódu v sestavení.</span><span class="sxs-lookup"><span data-stu-id="44991-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="44991-125">Druhý z následujících příkladů ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="44991-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="44991-126">Stejnou věc lze provést v linkeru sestavení.</span><span class="sxs-lookup"><span data-stu-id="44991-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="44991-127">Třetí z následujících příkladů ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="44991-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="44991-128">Další informace naleznete v tématu [Al. exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) a [práce se sestaveními a globální mezipamětí sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="44991-128">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="44991-129">**-linkres –** je krátká forma **-linkresource –** .</span><span class="sxs-lookup"><span data-stu-id="44991-129">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="44991-130">Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.</span><span class="sxs-lookup"><span data-stu-id="44991-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44991-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="44991-131">Example</span></span>  
 <span data-ttu-id="44991-132">Kompilovat `in.cs` a propojit se souborem `rf.resource`prostředků:</span><span class="sxs-lookup"><span data-stu-id="44991-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="44991-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="44991-133">Example</span></span>  
 <span data-ttu-id="44991-134">Zkompilujte `A.cs` do knihovny DLL, připojte se k nativní knihovně DLL N. dll a vložte výstup do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="44991-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="44991-135">V tomto příkladu se knihovna DLL a N. dll nachází v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="44991-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="44991-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="44991-136">Example</span></span>  
 <span data-ttu-id="44991-137">Tento příklad provede stejnou věc jako předchozí, ale pomocí možností linkeru sestavení.</span><span class="sxs-lookup"><span data-stu-id="44991-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="44991-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44991-138">See also</span></span>

- [<span data-ttu-id="44991-139">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="44991-139">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="44991-140">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="44991-140">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="44991-141">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="44991-141">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="44991-142">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="44991-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
