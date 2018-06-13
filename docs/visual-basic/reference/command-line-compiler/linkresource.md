---
title: -linkresource (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 38740ed7ab7904feb2ca95eb70c916fbdbaef71e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654340"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="398f1-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="398f1-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="398f1-103">Vytvoří odkaz na spravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="398f1-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="398f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="398f1-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="398f1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="398f1-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="398f1-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="398f1-106">Required.</span></span> <span data-ttu-id="398f1-107">Soubor prostředků pro odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="398f1-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="398f1-108">Pokud název souboru obsahuje mezery, uzavřete název v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="398f1-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="398f1-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="398f1-109">Optional.</span></span> <span data-ttu-id="398f1-110">Logický název prostředku.</span><span class="sxs-lookup"><span data-stu-id="398f1-110">The logical name for the resource.</span></span> <span data-ttu-id="398f1-111">Název, který se používá k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="398f1-111">The name that is used to load the resource.</span></span> <span data-ttu-id="398f1-112">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="398f1-112">The default is the name of the file.</span></span> <span data-ttu-id="398f1-113">Volitelně můžete zadat, zda se soubor nachází veřejných nebo privátních v manifestu sestavení, například: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="398f1-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="398f1-114">Ve výchozím nastavení `filename` je veřejný v sestavení.</span><span class="sxs-lookup"><span data-stu-id="398f1-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="398f1-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="398f1-115">Remarks</span></span>  
 <span data-ttu-id="398f1-116">`-linkresource` Možnost nevloží souboru prostředků ve výstupním souboru, pomocí `-resource` možnost to udělat.</span><span class="sxs-lookup"><span data-stu-id="398f1-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="398f1-117">`-linkresource` Možnost vyžaduje jednu z `-target` možnosti jiné než `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="398f1-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="398f1-118">Pokud `filename` je [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků vytvořili, například pomocí [Resgen.exe (Generátor zdrojových souborů)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) nebo ve vývojovém prostředí k němu se členy v <xref:System.Resources> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="398f1-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="398f1-119">(Další informace najdete v tématu <xref:System.Resources.ResourceManager>.) Pro přístup k jiným prostředkům v době běhu, použít metody, které začínají `GetManifestResource` v <xref:System.Reflection.Assembly> třídy.</span><span class="sxs-lookup"><span data-stu-id="398f1-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="398f1-120">Název souboru může být jakékoli formát souboru.</span><span class="sxs-lookup"><span data-stu-id="398f1-120">The file name can be any file format.</span></span> <span data-ttu-id="398f1-121">Například můžete chtít nativní knihovny DLL součástí sestavení, ujistěte se, aby mohli být nainstalován do globální mezipaměti sestavení a získat přístup ze spravovaného kódu v sestavení.</span><span class="sxs-lookup"><span data-stu-id="398f1-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="398f1-122">Zkratka pro `-linkresource` je `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="398f1-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="398f1-123">`-linkresource` Možnost není k dispozici z vývojovém prostředí sady Visual Studio, je k dispozici, pouze při sestavování z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="398f1-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="398f1-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="398f1-124">Example</span></span>  
 <span data-ttu-id="398f1-125">Následující kód zkompiluje `in.vb` a odkazy na soubor prostředků `rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="398f1-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="398f1-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="398f1-126">See Also</span></span>  
 [<span data-ttu-id="398f1-127">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="398f1-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="398f1-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="398f1-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="398f1-129">-prostředku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="398f1-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [<span data-ttu-id="398f1-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="398f1-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
