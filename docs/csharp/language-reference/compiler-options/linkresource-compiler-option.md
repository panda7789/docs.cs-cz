---
title: "-linkresource (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7da5a55fa96c11d79f8c616cf0f1f4e0ed109bfa
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="19499-102">-linkresource (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="19499-102">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="19499-103">Vytvoří odkaz na prostředek rozhraní .NET Framework ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="19499-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="19499-104">Souboru prostředků nebyla přidána do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="19499-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="19499-105">Tím se liší od [– prostředek](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) možnost, která vložení zdrojového souboru do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="19499-105">This differs from the [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19499-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19499-106">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="19499-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="19499-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="19499-108">Soubor prostředků rozhraní .NET Framework, do kterého chcete propojit ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="19499-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="19499-109">`identifier`(volitelné)</span><span class="sxs-lookup"><span data-stu-id="19499-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="19499-110">Logický název prostředku; název, který se používá k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="19499-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="19499-111">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="19499-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="19499-112">`accessibility-modifier`(volitelné)</span><span class="sxs-lookup"><span data-stu-id="19499-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="19499-113">Usnadnění prostředku: veřejné nebo soukromé.</span><span class="sxs-lookup"><span data-stu-id="19499-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="19499-114">Výchozí hodnota je veřejná.</span><span class="sxs-lookup"><span data-stu-id="19499-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19499-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19499-115">Remarks</span></span>  
 <span data-ttu-id="19499-116">Ve výchozím nastavení jsou propojené prostředky při jejich vytváření pomocí kompilátor jazyka C# veřejné v sestavení.</span><span class="sxs-lookup"><span data-stu-id="19499-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="19499-117">Chcete-li prostředky privátní, zadejte `private` jako modifikátor dostupnosti.</span><span class="sxs-lookup"><span data-stu-id="19499-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="19499-118">Žádný jiný modifikátor kromě `public` nebo `private` je povolen.</span><span class="sxs-lookup"><span data-stu-id="19499-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="19499-119">**-linkresource** vyžaduje jednu z [-cíl](../../../csharp/language-reference/compiler-options/target-compiler-option.md) možnosti jiné než **-target: module**.</span><span class="sxs-lookup"><span data-stu-id="19499-119">**-linkresource** requires one of the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="19499-120">Pokud `filename` je soubor prostředků rozhraní .NET Framework, který je vytvořen, například pomocí [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí k němu se členy v <xref:System.Resources> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="19499-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="19499-121">Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19499-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="19499-122">U všech ostatních prostředků, použijte `GetManifestResource` metody v <xref:System.Reflection.Assembly> třídy pro přístup k prostředku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="19499-122">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="19499-123">V souboru určeném v `filename` může být libovolného formátu.</span><span class="sxs-lookup"><span data-stu-id="19499-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="19499-124">Například můžete chtít nativní knihovny DLL součástí sestavení, ujistěte se, aby mohli být nainstalován do globální mezipaměti sestavení a získat přístup ze spravovaného kódu v sestavení.</span><span class="sxs-lookup"><span data-stu-id="19499-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="19499-125">Druhý následující příklady ukazuje, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="19499-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="19499-126">Můžete to samé v Linker sestavení.</span><span class="sxs-lookup"><span data-stu-id="19499-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="19499-127">Třetí následující příklady ukazuje, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="19499-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="19499-128">Další informace najdete v tématu [Al.exe (Linker sestavení)](../../../framework/tools/al-exe-assembly-linker.md) a [práce se sestaveními a globální mezipaměť sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="19499-128">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="19499-129">**-linkres** je zkratka pro **- linkresource**.</span><span class="sxs-lookup"><span data-stu-id="19499-129">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="19499-130">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="19499-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19499-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="19499-131">Example</span></span>  
 <span data-ttu-id="19499-132">Kompilace `in.cs` a odkaz na soubor prostředků `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="19499-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="19499-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="19499-133">Example</span></span>  
 <span data-ttu-id="19499-134">Kompilace `A.cs` do knihovny DLL, odkaz tuto knihovnu nativní knihovny DLL knihovnou n.dll a umístí výstup v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="19499-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="19499-135">V tomto příkladu bude A.dll i N.dll nacházet v mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="19499-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="19499-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="19499-136">Example</span></span>  
 <span data-ttu-id="19499-137">Tento příklad provede stejnou akci, jako předchozí, ale s použitím možnosti Linker sestavení.</span><span class="sxs-lookup"><span data-stu-id="19499-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="19499-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="19499-138">See Also</span></span>  
 [<span data-ttu-id="19499-139">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="19499-139">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="19499-140">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="19499-140">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)  
 [<span data-ttu-id="19499-141">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="19499-141">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="19499-142">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="19499-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
