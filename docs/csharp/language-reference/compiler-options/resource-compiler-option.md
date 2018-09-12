---
title: -resource (možnosti kompilátoru C#)
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
ms.openlocfilehash: e02eda66ab9fadbc7b5b042c8940096c70ef6a03
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44710486"
---
# <a name="-resource-c-compiler-options"></a><span data-ttu-id="80fd6-102">-resource (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="80fd6-102">-resource (C# Compiler Options)</span></span>
<span data-ttu-id="80fd6-103">Vloží zadaný prostředek do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="80fd6-103">Embeds the specified resource into the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80fd6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80fd6-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="80fd6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="80fd6-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="80fd6-106">Soubor prostředků rozhraní .NET Framework, který chcete vložit do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="80fd6-106">The .NET Framework resource file that you want to embed in the output file.</span></span>  
  
 <span data-ttu-id="80fd6-107">`identifier` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="80fd6-107">`identifier` (optional)</span></span>  
 <span data-ttu-id="80fd6-108">Logický název prostředku. název, který se používá k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="80fd6-108">The logical name for the resource; the name that is used to load the resource.</span></span> <span data-ttu-id="80fd6-109">Výchozí hodnota je název názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="80fd6-109">The default is the name of the file name.</span></span>  
  
 <span data-ttu-id="80fd6-110">`accessibility-modifier` (volitelné)</span><span class="sxs-lookup"><span data-stu-id="80fd6-110">`accessibility-modifier` (optional)</span></span>  
 <span data-ttu-id="80fd6-111">Dostupnost prostředku: veřejné nebo soukromé.</span><span class="sxs-lookup"><span data-stu-id="80fd6-111">The accessibility of the resource: public or private.</span></span> <span data-ttu-id="80fd6-112">Výchozí hodnota je veřejná.</span><span class="sxs-lookup"><span data-stu-id="80fd6-112">The default is public.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80fd6-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80fd6-113">Remarks</span></span>  
 <span data-ttu-id="80fd6-114">Použití [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) propojení prostředku sestavení a nelze přidat soubor prostředků do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="80fd6-114">Use [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) to link a resource to an assembly and not add the resource file to the output file.</span></span>  
  
 <span data-ttu-id="80fd6-115">Ve výchozím nastavení jsou prostředky v sestavení veřejné při jejich vytváření pomocí kompilátoru jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="80fd6-115">By default, resources are public in the assembly when they are created by using the C# compiler.</span></span> <span data-ttu-id="80fd6-116">Aby se mohly prostředky privátní, zadejte `private` jako modifikátor přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="80fd6-116">To make the resources private, specify `private` as the accessibility modifier.</span></span> <span data-ttu-id="80fd6-117">Žádné další usnadnění jiných než `public` nebo `private` je povolen.</span><span class="sxs-lookup"><span data-stu-id="80fd6-117">No other accessibility other than `public` or `private` is allowed.</span></span>  
  
 <span data-ttu-id="80fd6-118">Pokud `filename` je soubor prostředků rozhraní .NET Framework vytvořený, například podle [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, můžete přistupovat pomocí členů z <xref:System.Resources> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="80fd6-118">If `filename` is a .NET Framework resource file created, for example, by [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="80fd6-119">Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80fd6-119">For more information, see <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span> <span data-ttu-id="80fd6-120">U všech ostatních prostředků, použijte `GetManifestResource` metody v <xref:System.Reflection.Assembly> pro přístup k prostředku v době běhu.</span><span class="sxs-lookup"><span data-stu-id="80fd6-120">For all other resources, use the `GetManifestResource` methods in the <xref:System.Reflection.Assembly> class to access the resource at run time.</span></span>  
  
 <span data-ttu-id="80fd6-121">**-res** je zkratka pro **-prostředků**.</span><span class="sxs-lookup"><span data-stu-id="80fd6-121">**-res** is the short form of **-resource**.</span></span>  
  
 <span data-ttu-id="80fd6-122">Pořadí zdrojů do výstupního souboru je určen podle pořadí zadaném v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="80fd6-122">The order of the resources in the output file is determined from the order specified on the command line.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="80fd6-123">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="80fd6-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="80fd6-124">Přidejte soubor prostředků do vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="80fd6-124">Add a resource file to your project.</span></span>  
  
2.  <span data-ttu-id="80fd6-125">Vyberte soubor, který chcete vložit **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="80fd6-125">Select the file that you want to embed in **Solution Explorer**.</span></span>  
  
3.  <span data-ttu-id="80fd6-126">Vyberte **akce sestavení** souborem v **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="80fd6-126">Select **Build Action** for the file in the **Properties** window.</span></span>  
  
4.  <span data-ttu-id="80fd6-127">Nastavte **akce sestavení** k **vloženého prostředku**.</span><span class="sxs-lookup"><span data-stu-id="80fd6-127">Set **Build Action** to **Embedded Resource**.</span></span>  
  
 <span data-ttu-id="80fd6-128">Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span><span class="sxs-lookup"><span data-stu-id="80fd6-128">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.FileProperties2.BuildAction%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80fd6-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="80fd6-129">Example</span></span>  
 <span data-ttu-id="80fd6-130">Kompilace `in.cs` a připojte soubor prostředků `rf.resource`:</span><span class="sxs-lookup"><span data-stu-id="80fd6-130">Compile `in.cs` and attach resource file `rf.resource`:</span></span>  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="80fd6-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="80fd6-131">See Also</span></span>  

- [<span data-ttu-id="80fd6-132">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="80fd6-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="80fd6-133">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="80fd6-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
