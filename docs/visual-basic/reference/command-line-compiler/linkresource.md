---
title: -linkresource
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 0315645eccdc899ac9cf4d0be105297e1fa2a4c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335483"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="727d8-102">-linkresource – (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="727d8-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="727d8-103">Vytvoří odkaz na spravovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="727d8-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="727d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="727d8-104">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="727d8-105">– nebo –</span><span class="sxs-lookup"><span data-stu-id="727d8-105">or</span></span>  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="727d8-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="727d8-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="727d8-107">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="727d8-107">Required.</span></span> <span data-ttu-id="727d8-108">Soubor prostředků, který má být propojen se sestavením.</span><span class="sxs-lookup"><span data-stu-id="727d8-108">The resource file to link to the assembly.</span></span> <span data-ttu-id="727d8-109">Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="727d8-109">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="727d8-110">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="727d8-110">Optional.</span></span> <span data-ttu-id="727d8-111">Logický název prostředku.</span><span class="sxs-lookup"><span data-stu-id="727d8-111">The logical name for the resource.</span></span> <span data-ttu-id="727d8-112">Název, který se použije k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="727d8-112">The name that is used to load the resource.</span></span> <span data-ttu-id="727d8-113">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="727d8-113">The default is the name of the file.</span></span> <span data-ttu-id="727d8-114">Volitelně můžete určit, zda je soubor v manifestu sestavení veřejný nebo soukromý, například: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="727d8-114">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="727d8-115">Ve výchozím nastavení `filename` je v sestavení veřejné.</span><span class="sxs-lookup"><span data-stu-id="727d8-115">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="727d8-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="727d8-116">Remarks</span></span>  
 <span data-ttu-id="727d8-117">`-linkresource` Možnost nevloží soubor prostředků do výstupního souboru; tuto `-resource` možnost použijte k tomu.</span><span class="sxs-lookup"><span data-stu-id="727d8-117">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="727d8-118">`-linkresource` Možnost vyžaduje jednu z `-target` možností kromě `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="727d8-118">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="727d8-119">Pokud `filename` je vytvořen soubor prostředků .NET Framework, například pomocí nástroje [Resgen. exe (generátor zdrojového souboru)](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat pomocí členů v <xref:System.Resources> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="727d8-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="727d8-120">(Další informace najdete v tématu <xref:System.Resources.ResourceManager>.) Pro přístup ke všem dalším prostředkům v době běhu použijte metody, které začínají `GetManifestResource` ve <xref:System.Reflection.Assembly> třídě.</span><span class="sxs-lookup"><span data-stu-id="727d8-120">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="727d8-121">Název souboru může být libovolný formát souboru.</span><span class="sxs-lookup"><span data-stu-id="727d8-121">The file name can be any file format.</span></span> <span data-ttu-id="727d8-122">Například můžete chtít vytvořit nativní knihovnu DLL součásti sestavení, aby mohla být nainstalována do globální mezipaměti sestavení (GAC) a zpřístupněna ze spravovaného kódu v sestavení.</span><span class="sxs-lookup"><span data-stu-id="727d8-122">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="727d8-123">Krátká forma `-linkresource` je `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="727d8-123">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="727d8-124">Tato `-linkresource` možnost není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="727d8-124">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="727d8-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="727d8-125">Example</span></span>  
 <span data-ttu-id="727d8-126">Následující kód zkompiluje `in.vb` a vytvoří odkazy na soubor `rf.resource`prostředků.</span><span class="sxs-lookup"><span data-stu-id="727d8-126">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="727d8-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="727d8-127">See also</span></span>

- [<span data-ttu-id="727d8-128">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="727d8-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="727d8-129">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="727d8-129">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="727d8-130">-Resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="727d8-130">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)
- [<span data-ttu-id="727d8-131">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="727d8-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
