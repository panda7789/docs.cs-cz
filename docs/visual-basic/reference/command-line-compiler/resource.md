---
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: a781d543dd32ffb3d0ac0b11c544dbfd8cd5d806
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348556"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="f2c29-102">-Resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2c29-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="f2c29-103">Vloží spravovaný prostředek do sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2c29-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2c29-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2c29-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="f2c29-105">nebo</span><span class="sxs-lookup"><span data-stu-id="f2c29-105">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f2c29-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f2c29-106">Arguments</span></span>  
  
|<span data-ttu-id="f2c29-107">Termín</span><span class="sxs-lookup"><span data-stu-id="f2c29-107">Term</span></span>|<span data-ttu-id="f2c29-108">Definice</span><span class="sxs-lookup"><span data-stu-id="f2c29-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="f2c29-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f2c29-109">Required.</span></span> <span data-ttu-id="f2c29-110">Název souboru prostředků, který má být vložen do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="f2c29-110">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="f2c29-111">Ve výchozím nastavení je `filename` veřejné v sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2c29-111">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="f2c29-112">Uzavřete název souboru do uvozovek (""), pokud obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="f2c29-112">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="f2c29-113">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="f2c29-113">Optional.</span></span> <span data-ttu-id="f2c29-114">Logický název prostředku; název, který se používá k načtení.</span><span class="sxs-lookup"><span data-stu-id="f2c29-114">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="f2c29-115">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="f2c29-115">The default is the name of the file.</span></span> <span data-ttu-id="f2c29-116">Volitelně můžete určit, zda je prostředek v manifestu sestavení veřejný nebo privátní, jak je uvedeno níže: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="f2c29-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2c29-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2c29-117">Remarks</span></span>  
 <span data-ttu-id="f2c29-118">Použijte `-linkresource` k propojení prostředku se sestavením bez umístění souboru prostředků do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="f2c29-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="f2c29-119">Je-li `filename` je vytvořen .NET Framework soubor prostředků, například pomocí nástroje [Resgen. exe (generátor zdrojového souboru)](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu získat pøístup pomocí členů v oboru názvů <xref:System.Resources> (Další informace naleznete v <xref:System.Resources.ResourceManager>.</span><span class="sxs-lookup"><span data-stu-id="f2c29-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="f2c29-120">Chcete-li získat přístup ke všem dalším prostředkům v době běhu, použijte jednu z následujících metod: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>nebo <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="f2c29-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="f2c29-121">Krátká forma `-resource` je `-res`.</span><span class="sxs-lookup"><span data-stu-id="f2c29-121">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="f2c29-122">Informace o tom, jak nastavit `-resource` v integrovaném vývojovém prostředí sady Visual Studio, najdete v tématu [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="f2c29-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2c29-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2c29-123">Example</span></span>  
 <span data-ttu-id="f2c29-124">Následující kód zkompiluje `In.vb` a připojí soubor prostředků `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="f2c29-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f2c29-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2c29-125">See also</span></span>

- [<span data-ttu-id="f2c29-126">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="f2c29-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f2c29-127">-win32resource</span><span class="sxs-lookup"><span data-stu-id="f2c29-127">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [<span data-ttu-id="f2c29-128">-linkresource – (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2c29-128">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [<span data-ttu-id="f2c29-129">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2c29-129">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="f2c29-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="f2c29-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
