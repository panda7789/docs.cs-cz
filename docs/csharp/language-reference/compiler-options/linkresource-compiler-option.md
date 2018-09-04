---
title: -linkresource (možnosti kompilátoru C#)
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
ms.openlocfilehash: feca4713fe0e704799e2abbae3818edd0f3a5c84
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523172"
---
# <a name="-linkresource-c-compiler-options"></a><span data-ttu-id="6003b-102">-linkresource (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="6003b-102">-linkresource (C# Compiler Options)</span></span>
<span data-ttu-id="6003b-103">Ve výstupním souboru vytvoří odkaz na prostředek rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6003b-103">Creates a link to a .NET Framework resource in the output file.</span></span> <span data-ttu-id="6003b-104">Soubor prostředků se nepřidal do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="6003b-104">The resource file is not added to the output file.</span></span> <span data-ttu-id="6003b-105">Tím se liší od [-prostředků](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) možnost, která vložit soubor prostředků do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="6003b-105">This differs from the [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) option which does embed a resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6003b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6003b-106">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6003b-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="6003b-107">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="6003b-108">Soubor prostředků rozhraní .NET Framework, na který chcete propojit ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="6003b-108">The .NET Framework resource file to which you want to link from the assembly.</span></span>  
  
 <span data-ttu-id="6003b-109">`identifier` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="6003b-109">`identifier` (optional)</span></span>  
 <span data-ttu-id="6003b-110">Logický název prostředku. název, který se používá k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="6003b-110">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="6003b-111">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="6003b-111">The default is the name of the file.</span></span>  
  
 <span data-ttu-id="6003b-112">`accessibility-modifier` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="6003b-112">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="6003b-113">Dostupnost prostředku: veřejné nebo soukromé.</span><span class="sxs-lookup"><span data-stu-id="6003b-113">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="6003b-114">Výchozí hodnota je veřejná.</span><span class="sxs-lookup"><span data-stu-id="6003b-114">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6003b-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6003b-115">Remarks</span></span>  
 <span data-ttu-id="6003b-116">Ve výchozím nastavení jsou propojené prostředky v sestavení veřejné při jejich vytváření pomocí kompilátoru jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="6003b-116">By default, linked resources are public in the assembly when they are created with the C# compiler.</span></span> <span data-ttu-id="6003b-117">Aby se mohly prostředky privátní, zadejte `private` jako modifikátor přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="6003b-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="6003b-118">Žádný jiný modifikátor jiných než `public` nebo `private` je povolen.</span><span class="sxs-lookup"><span data-stu-id="6003b-118">No other modifier other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="6003b-119">**-linkresource** vyžaduje jednu z [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) možností jiných než **-target: module**.</span><span class="sxs-lookup"><span data-stu-id="6003b-119">**-linkresource** requires one of the [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) options other than **-target:module**.</span></span>  
  
 <span data-ttu-id="6003b-120">Pokud `filename` je soubor prostředků rozhraní .NET Framework vytvořený, například podle [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, můžete přistupovat pomocí členů z <xref:System.Resources> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6003b-120">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="6003b-121">Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6003b-121">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6003b-122">U všech ostatních prostředků, použijte `GetManifestResource` metody v <xref:System.Reflection.Assembly> pro přístup k prostředku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6003b-122">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="6003b-123">Soubor zadaný v `filename` může být libovolný formát.</span><span class="sxs-lookup"><span data-stu-id="6003b-123">The file specified in `filename` can be any format.</span></span> <span data-ttu-id="6003b-124">Můžete například vytvořit nativní knihovna DLL stane součástí sestavení, takže může být nainstalováno do globální mezipaměti sestavení a získat přístup ze spravovaného kódu v sestavení.</span><span class="sxs-lookup"><span data-stu-id="6003b-124">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span> <span data-ttu-id="6003b-125">Druhá následující příklady ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="6003b-125">The second of the following examples shows how to do this.</span></span> <span data-ttu-id="6003b-126">Můžete provést totéž v Linkeru sestavení.</span><span class="sxs-lookup"><span data-stu-id="6003b-126">You can do the same thing in the Assembly Linker.</span></span> <span data-ttu-id="6003b-127">Třetí následující příklady ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="6003b-127">The third of the following examples shows how to do this.</span></span> <span data-ttu-id="6003b-128">Další informace najdete v tématu [Al.exe (Linker sestavení)](../../../framework/tools/al-exe-assembly-linker.md) a [práce se sestaveními a s globální pamětí sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="6003b-128">For more information, see [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) and [Working with Assemblies and the Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).</span></span>  
  
 <span data-ttu-id="6003b-129">**-linkres** je zkratka pro **- linkresource**.</span><span class="sxs-lookup"><span data-stu-id="6003b-129">**-linkres** is the short form of **-linkresource**.</span></span>  
  
 <span data-ttu-id="6003b-130">Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.</span><span class="sxs-lookup"><span data-stu-id="6003b-130">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6003b-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="6003b-131">Example</span></span>  
 <span data-ttu-id="6003b-132">Kompilace `in.cs` a odkaz na soubor prostředků `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="6003b-132">Compile `in.cs` and link to resource file `rf.resource`:</span></span>  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a><span data-ttu-id="6003b-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="6003b-133">Example</span></span>  
 <span data-ttu-id="6003b-134">Kompilace `A.cs` do knihovny DLL, odkaz tuto knihovnu nativní knihovny DLL knihovnou n.dll a umístí výstup v globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="6003b-134">Compile `A.cs` into a DLL, link to a native DLL N.dll, and put the output in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="6003b-135">V tomto příkladu A.dll i N.dll bude nacházet v mezipaměti GAC.</span><span class="sxs-lookup"><span data-stu-id="6003b-135">In this example, both A.dll and N.dll will reside in the GAC.</span></span>  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a><span data-ttu-id="6003b-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="6003b-136">Example</span></span>  
 <span data-ttu-id="6003b-137">V tomto příkladu udělá to stejné jako předchozí, ale pomocí možností propojovacího programu sestavení.</span><span class="sxs-lookup"><span data-stu-id="6003b-137">This example does the same thing as the previous one, but by using Assembly Linker options.</span></span>  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="6003b-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="6003b-138">See Also</span></span>  

- [<span data-ttu-id="6003b-139">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6003b-139">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="6003b-140">Al.exe (linker sestavení)</span><span class="sxs-lookup"><span data-stu-id="6003b-140">Al.exe (Assembly Linker)</span></span>](../../../framework/tools/al-exe-assembly-linker.md)  
- [<span data-ttu-id="6003b-141">Práce se sestaveními a s globální pamětí sestavení</span><span class="sxs-lookup"><span data-stu-id="6003b-141">Working with Assemblies and the Global Assembly Cache</span></span>](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
- [<span data-ttu-id="6003b-142">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="6003b-142">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
