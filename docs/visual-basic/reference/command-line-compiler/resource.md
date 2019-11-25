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
# <a name="-resource-visual-basic"></a><span data-ttu-id="5139f-102">-resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5139f-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="5139f-103">Embeds a managed resource in an assembly.</span><span class="sxs-lookup"><span data-stu-id="5139f-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5139f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5139f-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="5139f-105">or</span><span class="sxs-lookup"><span data-stu-id="5139f-105">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5139f-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="5139f-106">Arguments</span></span>  
  
|<span data-ttu-id="5139f-107">Termín</span><span class="sxs-lookup"><span data-stu-id="5139f-107">Term</span></span>|<span data-ttu-id="5139f-108">Definice</span><span class="sxs-lookup"><span data-stu-id="5139f-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="5139f-109">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="5139f-109">Required.</span></span> <span data-ttu-id="5139f-110">The name of the resource file to embed in the output file.</span><span class="sxs-lookup"><span data-stu-id="5139f-110">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="5139f-111">By default, `filename` is public in the assembly.</span><span class="sxs-lookup"><span data-stu-id="5139f-111">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="5139f-112">Enclose the file name in quotation marks (" ") if it contains a space.</span><span class="sxs-lookup"><span data-stu-id="5139f-112">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="5139f-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="5139f-113">Optional.</span></span> <span data-ttu-id="5139f-114">The logical name for the resource; the name used to load it.</span><span class="sxs-lookup"><span data-stu-id="5139f-114">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="5139f-115">The default is the name of the file.</span><span class="sxs-lookup"><span data-stu-id="5139f-115">The default is the name of the file.</span></span> <span data-ttu-id="5139f-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="5139f-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5139f-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5139f-117">Remarks</span></span>  
 <span data-ttu-id="5139f-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span><span class="sxs-lookup"><span data-stu-id="5139f-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="5139f-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span><span class="sxs-lookup"><span data-stu-id="5139f-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="5139f-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="5139f-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="5139f-121">The short form of `-resource` is `-res`.</span><span class="sxs-lookup"><span data-stu-id="5139f-121">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="5139f-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="5139f-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5139f-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="5139f-123">Example</span></span>  
 <span data-ttu-id="5139f-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="5139f-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="5139f-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5139f-125">See also</span></span>

- [<span data-ttu-id="5139f-126">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="5139f-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="5139f-127">-win32resource</span><span class="sxs-lookup"><span data-stu-id="5139f-127">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [<span data-ttu-id="5139f-128">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5139f-128">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [<span data-ttu-id="5139f-129">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5139f-129">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="5139f-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="5139f-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
