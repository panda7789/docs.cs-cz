---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: eb84e0a7038e7ff8cb399ac7222b6ac1661b5bc1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788970"
---
# <a name="-optimize"></a><span data-ttu-id="0b622-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="0b622-102">-optimize</span></span>
<span data-ttu-id="0b622-103">Povolí nebo zakáže optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0b622-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b622-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b622-104">Syntax</span></span>  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0b622-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0b622-105">Arguments</span></span>  
  
|<span data-ttu-id="0b622-106">Termín</span><span class="sxs-lookup"><span data-stu-id="0b622-106">Term</span></span>|<span data-ttu-id="0b622-107">Definice</span><span class="sxs-lookup"><span data-stu-id="0b622-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="0b622-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="0b622-108">`+` &#124; `-`</span></span>|<span data-ttu-id="0b622-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0b622-109">Optional.</span></span> <span data-ttu-id="0b622-110">`-optimize-` Možnost zakáže optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0b622-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="0b622-111">`-optimize+` Možnost povolí optimalizace.</span><span class="sxs-lookup"><span data-stu-id="0b622-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="0b622-112">Ve výchozím nastavení jsou zakázané optimalizace.</span><span class="sxs-lookup"><span data-stu-id="0b622-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b622-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b622-113">Remarks</span></span>  
 <span data-ttu-id="0b622-114">Optimalizace kompilátoru zkontrolujte výstupní soubor menší, rychlejší a efektivnější.</span><span class="sxs-lookup"><span data-stu-id="0b622-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="0b622-115">Nicméně, protože optimalizace změnou kódu ve výstupním souboru `-optimize+` mohou ztížit ladění.</span><span class="sxs-lookup"><span data-stu-id="0b622-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="0b622-116">Všechny moduly, které generuje s použitím `-target:module` pro sestavení musíte použít stejné `-optimize` nastavení jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="0b622-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="0b622-117">Další informace najdete v tématu [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="0b622-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="0b622-118">Můžete kombinovat `-optimize` a `-debug` možnosti.</span><span class="sxs-lookup"><span data-stu-id="0b622-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="0b622-119">Chcete-li nastavit – optimalizace v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0b622-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0b622-120">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="0b622-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0b622-121">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0b622-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="0b622-122">2.  Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="0b622-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="0b622-123">3.  Klikněte na tlačítko **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0b622-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="0b622-124">4.  Upravit **povolit optimalizace** zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="0b622-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0b622-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b622-125">Example</span></span>  
 <span data-ttu-id="0b622-126">Následující kód zkompiluje `T2.vb` a povolí optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="0b622-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b622-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b622-127">See also</span></span>

- [<span data-ttu-id="0b622-128">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="0b622-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0b622-129">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b622-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="0b622-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="0b622-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="0b622-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b622-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
