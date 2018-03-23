---
title: -win32resource
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e210d88d32ac7341ab881ca6ff0e44961469a31
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-win32resource"></a><span data-ttu-id="c7062-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="c7062-102">-win32resource</span></span>
<span data-ttu-id="c7062-103">Vloží zdrojového souboru Win32 ve výstupním souboru.</span><span class="sxs-lookup"><span data-stu-id="c7062-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7062-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7062-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="c7062-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c7062-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="c7062-106">Název souboru prostředků pro přidání do výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="c7062-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="c7062-107">Uzavřete název souboru v uvozovkách ("") Pokud obsahuje mezeru.</span><span class="sxs-lookup"><span data-stu-id="c7062-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7062-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7062-108">Remarks</span></span>  
 <span data-ttu-id="c7062-109">Můžete vytvořit zdrojového souboru Win32 s Microsoft Windows prostředků kompilátoru (RC).</span><span class="sxs-lookup"><span data-stu-id="c7062-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="c7062-110">Win32 prostředků může obsahovat verzi nebo informace o bitové mapy (ikona), která pomáhá identifikovat aplikace v **Průzkumníka souborů**.</span><span class="sxs-lookup"><span data-stu-id="c7062-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="c7062-111">Pokud nezadáte `-win32resource`, kompilátor vygeneruje informace o verzi na základě verze sestavení.</span><span class="sxs-lookup"><span data-stu-id="c7062-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="c7062-112">`-win32resource` a `-win32icon` možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="c7062-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="c7062-113">Najdete v části [- linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) k odkazu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků, nebo [-prostředku (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) připojit [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] souboru prostředků.</span><span class="sxs-lookup"><span data-stu-id="c7062-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7062-114">`-win32resource` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c7062-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7062-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7062-115">Example</span></span>  
 <span data-ttu-id="c7062-116">Následující kód zkompiluje `In.vb` a připojí zdrojového souboru Win32 `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="c7062-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7062-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7062-117">See Also</span></span>  
 [<span data-ttu-id="c7062-118">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="c7062-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="c7062-119">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="c7062-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
