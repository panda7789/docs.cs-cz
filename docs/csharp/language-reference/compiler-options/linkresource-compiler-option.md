---
description: -linkresource – (možnosti kompilátoru C#)
title: -linkresource – (možnosti kompilátoru C#)
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
ms.openlocfilehash: 162baad57397b6d992dcf8f03f0b3661e0105cb8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125342"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="119f9-103">-linkresource – (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="119f9-103">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="119f9-104">Vytvoří odkaz na prostředek .NET Framework ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="119f9-104">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="119f9-105">Soubor prostředků se nepřidá do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="119f9-105">The resource file is not added to the output file.</span></span> <span data-ttu-id="119f9-106">To se liší od možnosti [-Resource](./resource-compiler-option.md) , která vloží soubor prostředků do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="119f9-106">This differs from the [-resource](./resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="119f9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="119f9-107">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="119f9-108">Argumenty</span><span class="sxs-lookup"><span data-stu-id="119f9-108">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="119f9-109">.NET Framework soubor prostředků, na který chcete propojit ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="119f9-109">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="119f9-110">`identifier` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="119f9-110">`identifier` (optional)</span></span>  
 <span data-ttu-id="119f9-111">Logický název prostředku; název, který se použije k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="119f9-111">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="119f9-112">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="119f9-112">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="119f9-113">`accessibility-modifier` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="119f9-113">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="119f9-114">Přístupnost prostředku: Public nebo Private.</span><span class="sxs-lookup"><span data-stu-id="119f9-114">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="119f9-115">Výchozí hodnota je Public.</span><span class="sxs-lookup"><span data-stu-id="119f9-115">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="119f9-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="119f9-116">Remarks</span></span>  
 <span data-ttu-id="119f9-117">Ve výchozím nastavení jsou propojené prostředky v sestavení veřejné, když jsou vytvořeny pomocí kompilátoru jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="119f9-117">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="119f9-118">Chcete-li zajistit soukromí prostředků, zadejte `private` jako modifikátor přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="119f9-118">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="119f9-119">Žádný jiný modifikátor `public` `private` není povolený.</span><span class="sxs-lookup"><span data-stu-id="119f9-119">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="119f9-120">**-linkresource –** vyžaduje jednu z možností [TARGETu](./target-compiler-option.md) s výjimkou **target: Module**.</span><span class="sxs-lookup"><span data-stu-id="119f9-120">**-linkresource** requires one of the [-target](./target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="119f9-121">Pokud `filename` je vytvořen soubor prostředků .NET Framework, například [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat pomocí členů v <xref:System.Resources> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="119f9-121">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="119f9-122">Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="119f9-122">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="119f9-123">Pro všechny ostatní prostředky použijte `GetManifestResource` metody ve <xref:System.Reflection.Assembly> třídě pro přístup k prostředku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="119f9-123">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="119f9-124">Soubor určený v `filename` může být libovolného formátu.</span><span class="sxs-lookup"><span data-stu-id="119f9-124">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="119f9-125">Například můžete chtít vytvořit nativní knihovnu DLL součásti sestavení, aby mohla být nainstalována do globální mezipaměti sestavení (GAC) a zpřístupněna ze spravovaného kódu v sestavení.</span><span class="sxs-lookup"><span data-stu-id="119f9-125">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="119f9-126">Druhý z následujících příkladů ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="119f9-126">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="119f9-127">Stejnou věc lze provést v linkeru sestavení.</span><span class="sxs-lookup"><span data-stu-id="119f9-127">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="119f9-128">Třetí z následujících příkladů ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="119f9-128">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="119f9-129">Další informace naleznete v tématu [Al.exe (linker sestavení)](../../../framework/tools/al-exe-assembly-linker.md) a [práce se sestaveními a globální mezipamětí sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="119f9-129">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="119f9-130">**-linkres –** je krátká forma **-linkresource –**.</span><span class="sxs-lookup"><span data-stu-id="119f9-130">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="119f9-131">Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.</span><span class="sxs-lookup"><span data-stu-id="119f9-131">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="119f9-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="119f9-132">Example</span></span>  
 <span data-ttu-id="119f9-133">Kompilovat `in.cs` a propojit se souborem prostředků `rf.resource` :</span><span class="sxs-lookup"><span data-stu-id="119f9-133">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="119f9-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="119f9-134">Example</span></span>  
 <span data-ttu-id="119f9-135">Zkompilujte `A.cs` do knihovny DLL, připojte se k nativní knihovně dll N.dll a vložte výstup do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="119f9-135">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="119f9-136">V tomto příkladu se budou v globální mezipaměti sestavení (GAC) nacházet jak A.dll, tak N.dll.</span><span class="sxs-lookup"><span data-stu-id="119f9-136">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="119f9-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="119f9-137">Example</span></span>  
 <span data-ttu-id="119f9-138">Tento příklad provede stejnou věc jako předchozí, ale pomocí možností linkeru sestavení.</span><span class="sxs-lookup"><span data-stu-id="119f9-138">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="119f9-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="119f9-139">See also</span></span>

- [<span data-ttu-id="119f9-140">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="119f9-140">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="119f9-141">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="119f9-141">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="119f9-142">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="119f9-142">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="119f9-143">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="119f9-143">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
