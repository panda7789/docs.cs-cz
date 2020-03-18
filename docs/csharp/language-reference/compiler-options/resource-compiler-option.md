---
title: -resource (C# Možnosti kompilátoru)
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602522"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="2c95c-102">-resource (C# Možnosti kompilátoru)</span><span class="sxs-lookup"><span data-stu-id="2c95c-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="2c95c-103">Vloží zadaný prostředek do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="2c95c-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c95c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c95c-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2c95c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2c95c-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="2c95c-106">Soubor prostředků rozhraní .NET Framework, který chcete vložit do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="2c95c-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="2c95c-107">`identifier` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="2c95c-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="2c95c-108">Logický název prostředku; název, který se používá k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="2c95c-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="2c95c-109">Výchozí je název souboru.</span><span class="sxs-lookup"><span data-stu-id="2c95c-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="2c95c-110">`accessibility-modifier` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="2c95c-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="2c95c-111">Dostupnost zdroje: veřejné nebo soukromé.</span><span class="sxs-lookup"><span data-stu-id="2c95c-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="2c95c-112">Výchozí hodnota je veřejná.</span><span class="sxs-lookup"><span data-stu-id="2c95c-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c95c-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c95c-113">Remarks</span></span>  
 <span data-ttu-id="2c95c-114">Pomocí [prostředku -link](./linkresource-compiler-option.md) můžete propojit prostředek s sestavením a nepřidávat soubor prostředků do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="2c95c-114">Use [-linkresource](./linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="2c95c-115">Ve výchozím nastavení jsou prostředky veřejné v sestavení při jejich vytvoření pomocí kompilátoru Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="2c95c-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="2c95c-116">Chcete-li prostředky jako `private` modifikátor usnadnění zadat jako soukromý.</span><span class="sxs-lookup"><span data-stu-id="2c95c-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="2c95c-117">Žádná jiná přístupnost než `public` nebo `private` je povolena.</span><span class="sxs-lookup"><span data-stu-id="2c95c-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="2c95c-118">Pokud `filename` je soubor prostředků rozhraní .NET Framework vytvořený například [programem Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat pomocí členů v oboru <xref:System.Resources> názvů.</span><span class="sxs-lookup"><span data-stu-id="2c95c-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="2c95c-119">Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2c95c-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2c95c-120">Pro všechny ostatní prostředky `GetManifestResource` použijte <xref:System.Reflection.Assembly> metody ve třídě pro přístup k prostředku za běhu.</span><span class="sxs-lookup"><span data-stu-id="2c95c-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="2c95c-121">**-res** je krátká forma **-resource**.</span><span class="sxs-lookup"><span data-stu-id="2c95c-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="2c95c-122">Pořadí zdrojů ve výstupním souboru je určeno podle pořadí určeného na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="2c95c-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="2c95c-123">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2c95c-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="2c95c-124">Přidejte do projektu soubor zdrojů.</span><span class="sxs-lookup"><span data-stu-id="2c95c-124">Add a resource file to your project.</span></span>  
  
2. <span data-ttu-id="2c95c-125">Vyberte soubor, který chcete vložit do **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="2c95c-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3. <span data-ttu-id="2c95c-126">V okně **Vlastnosti** vyberte **Vytvořit akci** pro soubor.</span><span class="sxs-lookup"><span data-stu-id="2c95c-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4. <span data-ttu-id="2c95c-127">Nastavte **akci sestavení** na **vložený prostředek**.</span><span class="sxs-lookup"><span data-stu-id="2c95c-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="2c95c-128">Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.FileProperties2.BuildAction%2A>kompilátoru programově, naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="2c95c-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c95c-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c95c-129">Example</span></span>  
 <span data-ttu-id="2c95c-130">Kompilace `in.cs` a `rf.resource`připojení souboru prostředků :</span><span class="sxs-lookup"><span data-stu-id="2c95c-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c95c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c95c-131">See also</span></span>

- [<span data-ttu-id="2c95c-132">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2c95c-132">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="2c95c-133">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="2c95c-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
