---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: e8daf4a49123623b6470bc3c6281869f1b9b3d0f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005368"
---
# <a name="-optimize"></a><span data-ttu-id="1e3b2-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="1e3b2-102">-optimize</span></span>
<span data-ttu-id="1e3b2-103">Povolí nebo zakáže optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1e3b2-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e3b2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e3b2-104">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e3b2-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1e3b2-105">Arguments</span></span>  
  
|<span data-ttu-id="1e3b2-106">Termín</span><span class="sxs-lookup"><span data-stu-id="1e3b2-106">Term</span></span>|<span data-ttu-id="1e3b2-107">Definice</span><span class="sxs-lookup"><span data-stu-id="1e3b2-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="1e3b2-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1e3b2-108">`+` &#124; `-`</span></span>|<span data-ttu-id="1e3b2-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1e3b2-109">Optional.</span></span> <span data-ttu-id="1e3b2-110">Možnost `-optimize-` zakáže optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1e3b2-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="1e3b2-111">Možnost `-optimize+` povoluje optimalizace.</span><span class="sxs-lookup"><span data-stu-id="1e3b2-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="1e3b2-112">Ve výchozím nastavení jsou optimalizace zakázané.</span><span class="sxs-lookup"><span data-stu-id="1e3b2-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e3b2-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e3b2-113">Remarks</span></span>  
 <span data-ttu-id="1e3b2-114">Optimalizace kompilátoru usnadňují, rychlejší a efektivnější výstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="1e3b2-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="1e3b2-115">Vzhledem k tomu, že optimalizace mají za následek změnu uspořádání kódu ve výstupním souboru, `-optimize+` může způsobit obtížné ladění.</span><span class="sxs-lookup"><span data-stu-id="1e3b2-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="1e3b2-116">Všechny moduly generované pomocí `-target:module` pro sestavení musí používat stejné nastavení `-optimize` jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="1e3b2-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="1e3b2-117">Další informace najdete v tématu [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="1e3b2-117">For more information, see [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="1e3b2-118">Můžete kombinovat možnosti `-optimize` a `-debug`.</span><span class="sxs-lookup"><span data-stu-id="1e3b2-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="1e3b2-119">Nastavení – optimalizace v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1e3b2-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1e3b2-120">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="1e3b2-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1e3b2-121">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="1e3b2-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="1e3b2-122">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="1e3b2-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1e3b2-123">3. klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="1e3b2-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="1e3b2-124">4. Upravte zaškrtávací políčko **Povolit optimalizace** .</span><span class="sxs-lookup"><span data-stu-id="1e3b2-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1e3b2-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e3b2-125">Example</span></span>  
 <span data-ttu-id="1e3b2-126">Následující kód zkompiluje `T2.vb` a povoluje optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1e3b2-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e3b2-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e3b2-127">See also</span></span>

- [<span data-ttu-id="1e3b2-128">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="1e3b2-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="1e3b2-129">-Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e3b2-129">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="1e3b2-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="1e3b2-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="1e3b2-131">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e3b2-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
