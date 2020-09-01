---
description: -Resource (možnosti kompilátoru C#)
title: -Resource (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: 963004820f56272b4f1b1d92ccc4d0a60493a4a0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128696"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="7bcee-103">-Resource (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="7bcee-103">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="7bcee-104">Vloží zadaný prostředek do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="7bcee-104">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bcee-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7bcee-105">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7bcee-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7bcee-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="7bcee-107">.NET Framework soubor prostředků, který chcete vložit do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="7bcee-107">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="7bcee-108">`identifier` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="7bcee-108">`identifier` (optional)</span></span>  
 <span data-ttu-id="7bcee-109">Logický název prostředku; název, který se použije k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="7bcee-109">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="7bcee-110">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="7bcee-110">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="7bcee-111">`accessibility-modifier` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="7bcee-111">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="7bcee-112">Přístupnost prostředku: Public nebo Private.</span><span class="sxs-lookup"><span data-stu-id="7bcee-112">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="7bcee-113">Výchozí hodnota je Public.</span><span class="sxs-lookup"><span data-stu-id="7bcee-113">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bcee-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7bcee-114">Remarks</span></span>  
 <span data-ttu-id="7bcee-115">Použijte [-linkresource –](./linkresource-compiler-option.md) k propojení prostředku se sestavením a nepřidejte soubor prostředků do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="7bcee-115">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="7bcee-116">Ve výchozím nastavení jsou prostředky v sestavení veřejné, když jsou vytvořeny pomocí kompilátoru jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="7bcee-116">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="7bcee-117">Chcete-li zajistit soukromí prostředků, zadejte `private` jako modifikátor přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="7bcee-117">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="7bcee-118">Žádná jiná přístupnost není `public` `private` povolena.</span><span class="sxs-lookup"><span data-stu-id="7bcee-118">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="7bcee-119">Pokud `filename` je vytvořen soubor prostředků .NET Framework, například [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat pomocí členů v <xref:System.Resources> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7bcee-119">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="7bcee-120">Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7bcee-120">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7bcee-121">Pro všechny ostatní prostředky použijte `GetManifestResource` metody ve <xref:System.Reflection.Assembly> třídě pro přístup k prostředku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="7bcee-121">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="7bcee-122">**-res** je krátká forma **prostředku**.</span><span class="sxs-lookup"><span data-stu-id="7bcee-122">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="7bcee-123">Pořadí prostředků ve výstupním souboru je určeno z pořadí zadaného na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="7bcee-123">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7bcee-124">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7bcee-124">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="7bcee-125">Přidejte soubor prostředků do projektu.</span><span class="sxs-lookup"><span data-stu-id="7bcee-125">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="7bcee-126">Vyberte soubor, který chcete vložit do **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="7bcee-126">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="7bcee-127">Vyberte **akci sestavení** pro soubor v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="7bcee-127">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="7bcee-128">Nastavte **akci sestavení** na **Integrovaný prostředek**.</span><span class="sxs-lookup"><span data-stu-id="7bcee-128">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="7bcee-129">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.FileProperties2.BuildAction%2A> .</span><span class="sxs-lookup"><span data-stu-id="7bcee-129">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bcee-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="7bcee-130">Example</span></span>  
 <span data-ttu-id="7bcee-131">Zkompilovat `in.cs` a připojit soubor prostředků `rf.resource` :</span><span class="sxs-lookup"><span data-stu-id="7bcee-131">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="7bcee-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="7bcee-132">See also</span></span>

- [<span data-ttu-id="7bcee-133">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="7bcee-133">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="7bcee-134">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="7bcee-134">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
