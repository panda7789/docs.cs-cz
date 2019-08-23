---
title: -linkresource – (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: d92b0d08daf660880b648875c67c3b78069143d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924862"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="49f8f-102">-linkresource – (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49f8f-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="49f8f-103">Vytvoří odkaz na spravovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="49f8f-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49f8f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49f8f-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="49f8f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="49f8f-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="49f8f-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="49f8f-106">Required.</span></span> <span data-ttu-id="49f8f-107">Soubor prostředků, který má být propojen se sestavením.</span><span class="sxs-lookup"><span data-stu-id="49f8f-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="49f8f-108">Pokud název souboru obsahuje mezeru, uzavřete název do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="49f8f-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="49f8f-109">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="49f8f-109">Optional.</span></span> <span data-ttu-id="49f8f-110">Logický název prostředku.</span><span class="sxs-lookup"><span data-stu-id="49f8f-110">The logical name for the resource.</span></span> <span data-ttu-id="49f8f-111">Název, který se použije k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="49f8f-111">The name that is used to load the resource.</span></span> <span data-ttu-id="49f8f-112">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="49f8f-112">The default is the name of the file.</span></span> <span data-ttu-id="49f8f-113">Volitelně můžete určit, zda je soubor v manifestu sestavení veřejný nebo soukromý, například: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="49f8f-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="49f8f-114">Ve výchozím nastavení `filename` je v sestavení veřejné.</span><span class="sxs-lookup"><span data-stu-id="49f8f-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49f8f-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49f8f-115">Remarks</span></span>  
 <span data-ttu-id="49f8f-116">Možnost nevloží soubor prostředků do výstupního souboru. `-resource` použijte k tomu možnost. `-linkresource`</span><span class="sxs-lookup"><span data-stu-id="49f8f-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="49f8f-117">Možnost vyžaduje jednu `-target` z možností kromě `-target:module`. `-linkresource`</span><span class="sxs-lookup"><span data-stu-id="49f8f-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="49f8f-118">Pokud `filename` je vytvořen soubor prostředků .NET Framework, například pomocí nástroje [Resgen. exe (generátor zdrojového souboru)](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat <xref:System.Resources> pomocí členů v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="49f8f-118">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="49f8f-119">(Další informace najdete v tématu <xref:System.Resources.ResourceManager>.) Pro přístup ke všem dalším prostředkům v době běhu použijte metody, které začínají `GetManifestResource` <xref:System.Reflection.Assembly> ve třídě.</span><span class="sxs-lookup"><span data-stu-id="49f8f-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="49f8f-120">Název souboru může být libovolný formát souboru.</span><span class="sxs-lookup"><span data-stu-id="49f8f-120">The file name can be any file format.</span></span> <span data-ttu-id="49f8f-121">Například můžete chtít vytvořit nativní knihovnu DLL součásti sestavení, aby mohla být nainstalována do globální mezipaměti sestavení (GAC) a zpřístupněna ze spravovaného kódu v sestavení.</span><span class="sxs-lookup"><span data-stu-id="49f8f-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="49f8f-122">Krátká forma `-linkresource` je `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="49f8f-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49f8f-123">Tato `-linkresource` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="49f8f-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49f8f-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="49f8f-124">Example</span></span>  
 <span data-ttu-id="49f8f-125">Následující kód zkompiluje `in.vb` a vytvoří odkazy na soubor `rf.resource`prostředků.</span><span class="sxs-lookup"><span data-stu-id="49f8f-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="49f8f-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49f8f-126">See also</span></span>

- [<span data-ttu-id="49f8f-127">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="49f8f-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="49f8f-128">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49f8f-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="49f8f-129">-Resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49f8f-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)
- [<span data-ttu-id="49f8f-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="49f8f-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
