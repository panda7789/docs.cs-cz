---
title: /optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dead17435cd147bdcdf91bdc5b8e0aa651e9e9fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optimize"></a><span data-ttu-id="73763-102">/optimize</span><span class="sxs-lookup"><span data-stu-id="73763-102">/optimize</span></span>
<span data-ttu-id="73763-103">Povolí nebo zakáže optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="73763-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73763-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73763-104">Syntax</span></span>  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="73763-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="73763-105">Arguments</span></span>  
  
|<span data-ttu-id="73763-106">Termín</span><span class="sxs-lookup"><span data-stu-id="73763-106">Term</span></span>|<span data-ttu-id="73763-107">Definice</span><span class="sxs-lookup"><span data-stu-id="73763-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="73763-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="73763-108">`+` &#124; `-`</span></span>|<span data-ttu-id="73763-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="73763-109">Optional.</span></span> <span data-ttu-id="73763-110">`/optimize-` Možnost zakáže optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="73763-110">The `/optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="73763-111">`/optimize+` Možnost umožňuje optimalizace.</span><span class="sxs-lookup"><span data-stu-id="73763-111">The `/optimize+` option enables optimizations.</span></span> <span data-ttu-id="73763-112">Ve výchozím nastavení jsou zakázány optimalizace.</span><span class="sxs-lookup"><span data-stu-id="73763-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73763-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73763-113">Remarks</span></span>  
 <span data-ttu-id="73763-114">Optimalizace kompilátoru byl výstupní soubor menší, rychlejší a efektivnější.</span><span class="sxs-lookup"><span data-stu-id="73763-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="73763-115">Nicméně, protože optimalizace mít za následek změny uspořádání kódu ve výstupním souboru `/optimize+` mohou ztížit ladění.</span><span class="sxs-lookup"><span data-stu-id="73763-115">However, because optimizations result in code rearrangement in the output file, `/optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="73763-116">Všechny moduly, které vygeneroval s `/target:module` pro sestavení musíte použít stejné `/optimize` nastavení jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="73763-116">All modules generated with `/target:module` for an assembly must use the same `/optimize` settings as the assembly.</span></span> <span data-ttu-id="73763-117">Další informace najdete v tématu [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="73763-117">For more information, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="73763-118">Můžete kombinovat `/optimize` a `/debug` možnosti.</span><span class="sxs-lookup"><span data-stu-id="73763-118">You can combine the `/optimize` and `/debug` options.</span></span>  
  
|<span data-ttu-id="73763-119">Chcete-li nastavit / optimize v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="73763-119">To set /optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="73763-120">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="73763-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="73763-121">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="73763-121">On the **Project** menu, click **Properties**.</span></span><br />     <span data-ttu-id="73763-122">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="73763-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="73763-123">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="73763-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="73763-124">3.  Klikněte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="73763-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="73763-125">4.  Změnit **povolit optimalizace** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="73763-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="73763-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="73763-126">Example</span></span>  
 <span data-ttu-id="73763-127">Následující kód zkompiluje `T2.vb` a umožňuje optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="73763-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="73763-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="73763-128">See Also</span></span>  
 [<span data-ttu-id="73763-129">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="73763-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="73763-130">/ Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73763-130">/debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="73763-131">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="73763-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="73763-132">/ target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73763-132">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
