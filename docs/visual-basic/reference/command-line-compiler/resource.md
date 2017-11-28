---
title: /resource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 858a216873ad9999722388e45d5de28398b27fbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="resource-visual-basic"></a><span data-ttu-id="10162-102">/resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10162-102">/resource (Visual Basic)</span></span>
<span data-ttu-id="10162-103">Vloží spravovaných prostředků v sestavení.</span><span class="sxs-lookup"><span data-stu-id="10162-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10162-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10162-104">Syntax</span></span>  
  
```  
/resource:filename[,identifier[,public|private]]  
' -or-  
/res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="10162-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="10162-105">Arguments</span></span>  
  
|<span data-ttu-id="10162-106">Termín</span><span class="sxs-lookup"><span data-stu-id="10162-106">Term</span></span>|<span data-ttu-id="10162-107">Definice</span><span class="sxs-lookup"><span data-stu-id="10162-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="10162-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="10162-108">Required.</span></span> <span data-ttu-id="10162-109">Název souboru prostředků pro vložení do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="10162-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="10162-110">Ve výchozím nastavení `filename` je veřejný v sestavení.</span><span class="sxs-lookup"><span data-stu-id="10162-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="10162-111">Uzavřete název souboru v uvozovkách ("") Pokud obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="10162-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="10162-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="10162-112">Optional.</span></span> <span data-ttu-id="10162-113">Logický název prostředku; název, který ho načíst.</span><span class="sxs-lookup"><span data-stu-id="10162-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="10162-114">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="10162-114">The default is the name of the file.</span></span> <span data-ttu-id="10162-115">Volitelně můžete zadat, zda je prostředek veřejné nebo soukromé v manifestu sestavení, stejně jako u následující: `/res:``filename.res`,`myname.res`,`public`</span><span class="sxs-lookup"><span data-stu-id="10162-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `/res:``filename.res`,`myname.res`,`public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10162-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10162-116">Remarks</span></span>  
 <span data-ttu-id="10162-117">Použití `/linkresource` propojení prostředek k sestavení bez umístění souboru prostředků ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="10162-117">Use `/linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="10162-118">Pokud `filename` je [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků vytvořili, například pomocí [Resgen.exe (Generátor zdrojových souborů)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) nebo ve vývojovém prostředí k němu se členy v <xref:System.Resources> obor názvů (viz <xref:System.Resources.ResourceManager> informace).</span><span class="sxs-lookup"><span data-stu-id="10162-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="10162-119">Pro přístup k jiným prostředkům v době běhu, použijte jednu z následujících metod: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, nebo <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="10162-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="10162-120">Zkratka pro `/resource` je `/res`.</span><span class="sxs-lookup"><span data-stu-id="10162-120">The short form of `/resource` is `/res`.</span></span>  
  
 <span data-ttu-id="10162-121">Informace o tom, jak nastavit `/resource` v prostředí Visual Studio IDE, naleznete v části [Správa prostředků aplikace (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="10162-121">For information about how to set `/resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="10162-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="10162-122">Example</span></span>  
 <span data-ttu-id="10162-123">Následující kód zkompiluje `In.vb` a připojí zdrojového souboru `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="10162-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```  
vbc /res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="10162-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="10162-124">See Also</span></span>  
 [<span data-ttu-id="10162-125">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="10162-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="10162-126">/ win32resource</span><span class="sxs-lookup"><span data-stu-id="10162-126">/win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [<span data-ttu-id="10162-127">/ linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10162-127">/linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [<span data-ttu-id="10162-128">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10162-128">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="10162-129">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="10162-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
