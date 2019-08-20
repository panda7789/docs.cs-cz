---
title: -Resource (C# možnosti kompilátoru)
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
ms.openlocfilehash: e14bf59f5922a918b627af22c052c8efd9081e84
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602522"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="acc2b-102">-Resource (C# možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="acc2b-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="acc2b-103">Vloží zadaný prostředek do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="acc2b-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acc2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="acc2b-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="acc2b-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="acc2b-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="acc2b-106">.NET Framework soubor prostředků, který chcete vložit do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="acc2b-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="acc2b-107">`identifier`volitelné</span><span class="sxs-lookup"><span data-stu-id="acc2b-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="acc2b-108">Logický název prostředku; název, který se použije k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="acc2b-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="acc2b-109">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="acc2b-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="acc2b-110">`accessibility-modifier`volitelné</span><span class="sxs-lookup"><span data-stu-id="acc2b-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="acc2b-111">Přístupnost prostředku: Public nebo Private.</span><span class="sxs-lookup"><span data-stu-id="acc2b-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="acc2b-112">Výchozí hodnota je Public.</span><span class="sxs-lookup"><span data-stu-id="acc2b-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acc2b-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="acc2b-113">Remarks</span></span>  
 <span data-ttu-id="acc2b-114">Použijte [-linkresource –](./linkresource-compiler-option.md) k propojení prostředku se sestavením a nepřidejte soubor prostředků do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="acc2b-114">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="acc2b-115">Ve výchozím nastavení jsou prostředky v sestavení veřejné, když jsou vytvořeny pomocí C# kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="acc2b-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="acc2b-116">Chcete-li zajistit soukromí prostředků, `private` zadejte jako modifikátor přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="acc2b-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="acc2b-117">Žádná jiná přístupnost `public` `private` není povolena.</span><span class="sxs-lookup"><span data-stu-id="acc2b-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="acc2b-118">Pokud `filename` je vytvořen soubor prostředků .NET Framework, například pomocí nástroje [Resgen. exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat <xref:System.Resources> pomocí členů v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="acc2b-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="acc2b-119">Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="acc2b-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="acc2b-120">Pro všechny ostatní prostředky použijte `GetManifestResource` metody <xref:System.Reflection.Assembly> ve třídě pro přístup k prostředku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="acc2b-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="acc2b-121">**-res** je krátká forma **prostředku**.</span><span class="sxs-lookup"><span data-stu-id="acc2b-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="acc2b-122">Pořadí prostředků ve výstupním souboru je určeno z pořadí zadaného na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="acc2b-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="acc2b-123">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="acc2b-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="acc2b-124">Přidejte soubor prostředků do projektu.</span><span class="sxs-lookup"><span data-stu-id="acc2b-124">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="acc2b-125">Vyberte soubor, který chcete vložit do **Průzkumník řešení**.</span><span class="sxs-lookup"><span data-stu-id="acc2b-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="acc2b-126">Vyberte **akci sestavení** pro soubor v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="acc2b-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="acc2b-127">Nastavte **akci sestavení** na **Integrovaný prostředek**.</span><span class="sxs-lookup"><span data-stu-id="acc2b-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="acc2b-128">Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.FileProperties2.BuildAction%2A>v tématu.</span><span class="sxs-lookup"><span data-stu-id="acc2b-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acc2b-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="acc2b-129">Example</span></span>  
 <span data-ttu-id="acc2b-130">Zkompilovat `in.cs` a připojit soubor `rf.resource`prostředků:</span><span class="sxs-lookup"><span data-stu-id="acc2b-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="acc2b-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acc2b-131">See also</span></span>

- [<span data-ttu-id="acc2b-132">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="acc2b-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="acc2b-133">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="acc2b-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
