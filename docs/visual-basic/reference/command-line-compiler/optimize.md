---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 337cb794ef9a405a178f1998cbe27b5da7709382
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397438"
---
# <a name="-optimize"></a><span data-ttu-id="df0ae-102">-optimize</span><span class="sxs-lookup"><span data-stu-id="df0ae-102">-optimize</span></span>
<span data-ttu-id="df0ae-103">Povolí nebo zakáže optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="df0ae-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df0ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df0ae-104">Syntax</span></span>  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="df0ae-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="df0ae-105">Arguments</span></span>  
  
|<span data-ttu-id="df0ae-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="df0ae-106">Term</span></span>|<span data-ttu-id="df0ae-107">Definice</span><span class="sxs-lookup"><span data-stu-id="df0ae-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="df0ae-108">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="df0ae-108">`+` &#124; `-`</span></span>|<span data-ttu-id="df0ae-109">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="df0ae-109">Optional.</span></span> <span data-ttu-id="df0ae-110">`-optimize-`Možnost zakáže optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="df0ae-110">The `-optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="df0ae-111">`-optimize+`Možnost povoluje optimalizace.</span><span class="sxs-lookup"><span data-stu-id="df0ae-111">The `-optimize+` option enables optimizations.</span></span> <span data-ttu-id="df0ae-112">Ve výchozím nastavení jsou optimalizace zakázané.</span><span class="sxs-lookup"><span data-stu-id="df0ae-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df0ae-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df0ae-113">Remarks</span></span>  
 <span data-ttu-id="df0ae-114">Optimalizace kompilátoru usnadňují, rychlejší a efektivnější výstupní soubor.</span><span class="sxs-lookup"><span data-stu-id="df0ae-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="df0ae-115">Vzhledem k tomu, že optimalizace mají za následek změnu uspořádání kódu ve výstupním souboru, `-optimize+` může být ladění obtížné.</span><span class="sxs-lookup"><span data-stu-id="df0ae-115">However, because optimizations result in code rearrangement in the output file, `-optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="df0ae-116">Všechny moduly generované v `-target:module` pro sestavení musí používat stejné `-optimize` nastavení jako sestavení.</span><span class="sxs-lookup"><span data-stu-id="df0ae-116">All modules generated with `-target:module` for an assembly must use the same `-optimize` settings as the assembly.</span></span> <span data-ttu-id="df0ae-117">Další informace najdete v tématu [-target (Visual Basic)](target.md).</span><span class="sxs-lookup"><span data-stu-id="df0ae-117">For more information, see [-target (Visual Basic)](target.md).</span></span>  
  
 <span data-ttu-id="df0ae-118">Můžete kombinovat `-optimize` `-debug` Možnosti a.</span><span class="sxs-lookup"><span data-stu-id="df0ae-118">You can combine the `-optimize` and `-debug` options.</span></span>  
  
|<span data-ttu-id="df0ae-119">Nastavení – optimalizace v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="df0ae-119">To set -optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="df0ae-120">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="df0ae-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="df0ae-121">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="df0ae-121">On the **Project** menu, click **Properties**.</span></span><br />     <br /><span data-ttu-id="df0ae-122">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="df0ae-122">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="df0ae-123">3. klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="df0ae-123">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="df0ae-124">4. Upravte zaškrtávací políčko **Povolit optimalizace** .</span><span class="sxs-lookup"><span data-stu-id="df0ae-124">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="df0ae-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="df0ae-125">Example</span></span>  
 <span data-ttu-id="df0ae-126">Následující kód zkompiluje `T2.vb` a povolí optimalizace kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="df0ae-126">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="df0ae-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="df0ae-127">See also</span></span>

- [<span data-ttu-id="df0ae-128">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="df0ae-128">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="df0ae-129">-Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df0ae-129">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="df0ae-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="df0ae-130">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="df0ae-131">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df0ae-131">-target (Visual Basic)</span></span>](target.md)
