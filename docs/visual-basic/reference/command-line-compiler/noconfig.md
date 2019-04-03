---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: 44bc619c489fdff36f0b595f7d8934689b859adb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819428"
---
# <a name="-noconfig"></a><span data-ttu-id="e16b1-102">-noconfig</span><span class="sxs-lookup"><span data-stu-id="e16b1-102">-noconfig</span></span>
<span data-ttu-id="e16b1-103">Určuje, že kompilátor by neměl odkazovat automaticky běžně používaných [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení nebo import `System` a `Microsoft.VisualBasic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e16b1-103">Specifies that the compiler should not automatically reference the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e16b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e16b1-104">Syntax</span></span>  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="e16b1-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e16b1-105">Remarks</span></span>  
 <span data-ttu-id="e16b1-106">`-noconfig` Přikáže kompilátoru, aby kompilovat s soubor Vbc.rsp, který je umístěn ve stejném adresáři jako soubor Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="e16b1-106">The `-noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="e16b1-107">Odkazuje na soubor Vbc.rsp běžně používaných [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení a importuje `System` a `Microsoft.VisualBasic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e16b1-107">The Vbc.rsp file references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="e16b1-108">Kompilátor implicitně odkazuje na sestavení System.dll, není-li `-nostdlib` je zadána možnost.</span><span class="sxs-lookup"><span data-stu-id="e16b1-108">The compiler implicitly references the System.dll assembly unless the `-nostdlib` option is specified.</span></span> <span data-ttu-id="e16b1-109">`-nostdlib` Přikáže kompilátoru, aby kompilovat s Vbc.rsp nebo automaticky odkazují na toto sestavení System.dll.</span><span class="sxs-lookup"><span data-stu-id="e16b1-109">The `-nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e16b1-110">Vždy je odkazováno na sestavení Mscorlib.dll a Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="e16b1-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="e16b1-111">Můžete upravit soubor Vbc.rsp zadat další možnosti kompilátoru, které by měl být součástí každé Vbc.exe kompilaci (s výjimkou při zadávání `-noconfig` možnost).</span><span class="sxs-lookup"><span data-stu-id="e16b1-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `-noconfig` option).</span></span> <span data-ttu-id="e16b1-112">Další informace najdete v tématu [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="e16b1-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="e16b1-113">Kompilátor zpracovává možnosti předané `vbc` poslední příkaz.</span><span class="sxs-lookup"><span data-stu-id="e16b1-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="e16b1-114">Proto všechny možnost na příkazovém řádku přepíše nastavení stejná možnost v soubor Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="e16b1-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e16b1-115">`-noconfig` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e16b1-115">The `-noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e16b1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e16b1-116">See also</span></span>

- [<span data-ttu-id="e16b1-117">-nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e16b1-117">-nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [<span data-ttu-id="e16b1-118">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="e16b1-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="e16b1-119">@ (určení souboru odezvy)</span><span class="sxs-lookup"><span data-stu-id="e16b1-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [<span data-ttu-id="e16b1-120">– referenční dokumentace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e16b1-120">-reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
