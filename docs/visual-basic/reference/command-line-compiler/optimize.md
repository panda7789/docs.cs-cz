---
title: -Optimalizace
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 2f066835c5f864538f281d4c58772e0e60c132f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649942"
---
# <a name="-optimize"></a><span data-ttu-id="48076-102">-Optimalizace</span><span class="sxs-lookup"><span data-stu-id="48076-102">-optimize</span></span>
<span data-ttu-id="48076-103">Povolí nebo zakáže optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="48076-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48076-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48076-104">Syntax</span></span>  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="48076-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="48076-105">Arguments</span></span>  
  
|<span data-ttu-id="48076-106">Termín</span><span class="sxs-lookup"><span data-stu-id="48076-106">Term</span></span>|<span data-ttu-id="48076-107">Definice</span><span class="sxs-lookup"><span data-stu-id="48076-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="48076-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="48076-108">`+` &#124; `-`</span></span>|<span data-ttu-id="48076-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="48076-109">Optional.</span></span> <span data-ttu-id="48076-110">`-optimize-` Možnost zakáže optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="48076-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="48076-111">`-optimize+` Možnost umožňuje optimalizace.</span><span class="sxs-lookup"><span data-stu-id="48076-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="48076-112">Ve výchozím nastavení jsou zakázány optimalizace.</span><span class="sxs-lookup"><span data-stu-id="48076-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48076-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="48076-113">Remarks</span></span>  
 <span data-ttu-id="48076-114">Optimalizace kompilátoru byl výstupní soubor menší, rychlejší a efektivnější.</span><span class="sxs-lookup"><span data-stu-id="48076-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="48076-115">Nicméně, protože optimalizace mít za následek změny uspořádání kódu ve výstupním souboru `-optimize+` mohou ztížit ladění.</span><span class="sxs-lookup"><span data-stu-id="48076-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="48076-116">Všechny moduly, které vygeneroval s `-target:module` pro sestavení musíte použít stejné `-optimize` nastavení jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="48076-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="48076-117">Další informace najdete v tématu [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="48076-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="48076-118">Můžete kombinovat `-optimize` a `-debug` možnosti.</span><span class="sxs-lookup"><span data-stu-id="48076-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="48076-119">Chcete-li nastavit - Optimalizujte v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="48076-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="48076-120">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="48076-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="48076-121">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="48076-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="48076-122">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="48076-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="48076-123">3.  Klikněte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="48076-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="48076-124">4.  Změnit **povolit optimalizace** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="48076-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="48076-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="48076-125">Example</span></span>  
 <span data-ttu-id="48076-126">Následující kód zkompiluje `T2.vb` a umožňuje optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="48076-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="48076-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="48076-127">See Also</span></span>  
 [<span data-ttu-id="48076-128">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="48076-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="48076-129">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48076-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="48076-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="48076-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="48076-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48076-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
