---
title: /noconfig
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94d13ccf0168027f4560b980c41e2a001ff503fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="noconfig"></a><span data-ttu-id="e0bc5-102">/noconfig</span><span class="sxs-lookup"><span data-stu-id="e0bc5-102">/noconfig</span></span>
<span data-ttu-id="e0bc5-103">Určuje, že kompilátor nesmí odkazovat na automaticky běžně používané [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení nebo import `System` a `Microsoft.VisualBasic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e0bc5-103">Specifies that the compiler should not automatically reference the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0bc5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0bc5-104">Syntax</span></span>  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="e0bc5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0bc5-105">Remarks</span></span>  
 <span data-ttu-id="e0bc5-106">`/noconfig` Říká kompilátoru nechcete kompilovat s Vbc.rsp souboru, který se nachází ve stejném adresáři jako soubor Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="e0bc5-106">The `/noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="e0bc5-107">Soubor Vbc.rsp odkazuje běžně používané [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sestavení a importy `System` a `Microsoft.VisualBasic` obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e0bc5-107">The Vbc.rsp file references the commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="e0bc5-108">Kompilátor implicitně odkazuje na sestavení System.dll, pokud `/nostdlib` je zadána možnost.</span><span class="sxs-lookup"><span data-stu-id="e0bc5-108">The compiler implicitly references the System.dll assembly unless the `/nostdlib` option is specified.</span></span> <span data-ttu-id="e0bc5-109">`/nostdlib` Říká kompilátoru nechcete kompilovat s Vbc.rsp nebo automaticky odkazovat System.dll sestavení.</span><span class="sxs-lookup"><span data-stu-id="e0bc5-109">The `/nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0bc5-110">Sestavení Mscorlib.dll a souboru Microsoft.VisualBasic.dll jsou vždy odkazovat.</span><span class="sxs-lookup"><span data-stu-id="e0bc5-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="e0bc5-111">Můžete upravit soubor Vbc.rsp můžete určit další kompilátoru možnosti, které mají být zahrnuty v každé Vbc.exe kompilaci (s výjimkou při zadávání `/noconfig` možnost).</span><span class="sxs-lookup"><span data-stu-id="e0bc5-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `/noconfig` option).</span></span> <span data-ttu-id="e0bc5-112">Další informace najdete v tématu [@ (určení souboru odezvy)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="e0bc5-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="e0bc5-113">Kompilátor zpracovává možnosti předaný `vbc` poslední příkaz.</span><span class="sxs-lookup"><span data-stu-id="e0bc5-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="e0bc5-114">Jakákoliv možnost, na příkazovém řádku proto přepíše nastavení stejné možnosti v souboru Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="e0bc5-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0bc5-115">`/noconfig` Možnost není k dispozici ve vývojovém prostředí sady Visual Studio, je k dispozici pouze při kompilaci z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e0bc5-115">The `/noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0bc5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0bc5-116">See Also</span></span>  
 [<span data-ttu-id="e0bc5-117">/ nostdlib (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0bc5-117">/nostdlib (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/nostdlib.md)  
 [<span data-ttu-id="e0bc5-118">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="e0bc5-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e0bc5-119">@ (Určení souboru odezvy)</span><span class="sxs-lookup"><span data-stu-id="e0bc5-119">@ (Specify Response File)</span></span>](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)  
 [<span data-ttu-id="e0bc5-120">/ Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0bc5-120">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)
