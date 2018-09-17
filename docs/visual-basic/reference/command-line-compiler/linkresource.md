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
ms.openlocfilehash: 97e0ccd46f413cc05b659731436bb141ee178419
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746189"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="2e59e-102">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e59e-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="2e59e-103">Vytvoří odkaz na spravovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="2e59e-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e59e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e59e-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2e59e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2e59e-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="2e59e-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2e59e-106">Required.</span></span> <span data-ttu-id="2e59e-107">Soubor prostředků odkaz na sestavení.</span><span class="sxs-lookup"><span data-stu-id="2e59e-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="2e59e-108">Pokud název souboru obsahuje mezery, uzavřete název do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="2e59e-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="2e59e-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2e59e-109">Optional.</span></span> <span data-ttu-id="2e59e-110">Logický název prostředku.</span><span class="sxs-lookup"><span data-stu-id="2e59e-110">The logical name for the resource.</span></span> <span data-ttu-id="2e59e-111">Název, který se používá k načtení prostředku.</span><span class="sxs-lookup"><span data-stu-id="2e59e-111">The name that is used to load the resource.</span></span> <span data-ttu-id="2e59e-112">Výchozí hodnota je název souboru.</span><span class="sxs-lookup"><span data-stu-id="2e59e-112">The default is the name of the file.</span></span> <span data-ttu-id="2e59e-113">Volitelně můžete určit, zda soubor je třeba veřejných nebo privátních v manifestu sestavení: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="2e59e-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="2e59e-114">Ve výchozím nastavení `filename` veřejnou v sestavení.</span><span class="sxs-lookup"><span data-stu-id="2e59e-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e59e-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e59e-115">Remarks</span></span>  
 <span data-ttu-id="2e59e-116">`-linkresource` Možnost nelze vložit soubor prostředků do výstupního souboru; použijte `-resource` možnost to udělat.</span><span class="sxs-lookup"><span data-stu-id="2e59e-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="2e59e-117">`-linkresource` Možnost vyžaduje jednu z `-target` možností jiných než `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="2e59e-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="2e59e-118">Pokud `filename` je [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] soubor prostředků vytvořený, například podle [Resgen.exe (Generátor zdrojových souborů)](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, můžete přistupovat pomocí členů z <xref:System.Resources> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2e59e-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="2e59e-119">(Další informace najdete v tématu <xref:System.Resources.ResourceManager>.) Pro přístup k dalším prostředkům v době běhu, použijte metody, které začínají `GetManifestResource` v <xref:System.Reflection.Assembly> třídy.</span><span class="sxs-lookup"><span data-stu-id="2e59e-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="2e59e-120">Název souboru může být libovolný formát souboru.</span><span class="sxs-lookup"><span data-stu-id="2e59e-120">The file name can be any file format.</span></span> <span data-ttu-id="2e59e-121">Můžete například vytvořit nativní knihovna DLL stane součástí sestavení, takže může být nainstalováno do globální mezipaměti sestavení a získat přístup ze spravovaného kódu v sestavení.</span><span class="sxs-lookup"><span data-stu-id="2e59e-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="2e59e-122">Krátký tvar `-linkresource` je `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="2e59e-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e59e-123">`-linkresource` Možnost není k dispozici z vývojového prostředí sady Visual Studio; je k dispozici, pouze pokud kompilujete z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2e59e-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e59e-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e59e-124">Example</span></span>  
 <span data-ttu-id="2e59e-125">Následující kód zkompiluje `in.vb` a odkazy na soubor prostředků `rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="2e59e-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e59e-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e59e-126">See also</span></span>

- [<span data-ttu-id="2e59e-127">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e59e-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
- [<span data-ttu-id="2e59e-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e59e-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
- [<span data-ttu-id="2e59e-129">-prostředku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e59e-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)  
- [<span data-ttu-id="2e59e-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="2e59e-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
