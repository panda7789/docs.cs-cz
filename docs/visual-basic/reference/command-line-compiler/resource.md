---
title: -prostředku (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 46122eaa7ca54679c9a52b939f9100c9a0747e7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639085"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="86287-102">-prostředku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86287-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="86287-103">Vloží spravovaný prostředek sestavení.</span><span class="sxs-lookup"><span data-stu-id="86287-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86287-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86287-104">Syntax</span></span>  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="86287-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="86287-105">Arguments</span></span>  
  
|<span data-ttu-id="86287-106">Termín</span><span class="sxs-lookup"><span data-stu-id="86287-106">Term</span></span>|<span data-ttu-id="86287-107">Definice</span><span class="sxs-lookup"><span data-stu-id="86287-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="86287-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="86287-108">Required.</span></span> <span data-ttu-id="86287-109">Název souboru prostředků pro vložení do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="86287-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="86287-110">Ve výchozím nastavení `filename` veřejnou v sestavení.</span><span class="sxs-lookup"><span data-stu-id="86287-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="86287-111">Název souboru uzavřete do uvozovek ("") Pokud obsahuje mezery.</span><span class="sxs-lookup"><span data-stu-id="86287-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="86287-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="86287-112">Optional.</span></span> <span data-ttu-id="86287-113">Logický název prostředku. Název používaný k načtení.</span><span class="sxs-lookup"><span data-stu-id="86287-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="86287-114">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="86287-114">The default is the name of the file.</span></span> <span data-ttu-id="86287-115">Volitelně můžete určit, zda je prostředek veřejné nebo soukromé v manifestu sestavení, stejně jako u následující: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="86287-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86287-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86287-116">Remarks</span></span>  
 <span data-ttu-id="86287-117">Použití `-linkresource` pro propojení prostředku do sestavení bez umístění souboru prostředků do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="86287-117">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="86287-118">Pokud `filename` je [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] soubor prostředků vytvořený, například podle [Resgen.exe (Generátor zdrojových souborů)](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, můžete přistupovat pomocí členů z <xref:System.Resources> obor názvů (viz <xref:System.Resources.ResourceManager> Další informace).</span><span class="sxs-lookup"><span data-stu-id="86287-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="86287-119">Pro přístup k dalším prostředkům v době běhu, použijte jednu z následujících metod: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, nebo <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="86287-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="86287-120">Krátký tvar `-resource` je `-res`.</span><span class="sxs-lookup"><span data-stu-id="86287-120">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="86287-121">Informace o tom, jak nastavit `-resource` v sadě Visual Studio IDE, naleznete v tématu [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="86287-121">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="86287-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="86287-122">Example</span></span>  
 <span data-ttu-id="86287-123">Následující kód zkompiluje `In.vb` a soubor prostředků bude k obrazci `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="86287-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="86287-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86287-124">See also</span></span>

- [<span data-ttu-id="86287-125">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="86287-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="86287-126">-win32resource</span><span class="sxs-lookup"><span data-stu-id="86287-126">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [<span data-ttu-id="86287-127">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86287-127">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [<span data-ttu-id="86287-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86287-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="86287-129">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="86287-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
