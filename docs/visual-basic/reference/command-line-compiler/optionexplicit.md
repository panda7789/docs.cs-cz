---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 072a816f189a772543fbbd63e7202441469c0177
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653595"
---
# <a name="-optionexplicit"></a><span data-ttu-id="e7eb5-102">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="e7eb5-102">-optionexplicit</span></span>
<span data-ttu-id="e7eb5-103">Pokud nejsou proměnné deklarovány před použitím způsobí, že kompilátor zprávy o chybách.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7eb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7eb5-104">Syntax</span></span>  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="e7eb5-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e7eb5-105">Arguments</span></span>  
 <span data-ttu-id="e7eb5-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="e7eb5-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="e7eb5-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-107">Optional.</span></span> <span data-ttu-id="e7eb5-108">Zadejte `-optionexplicit+` tak, aby vyžadovala explicitní deklarace proměnné.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-108">Specify `-optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="e7eb5-109">`-optionexplicit+` Možnost je výchozí a je stejná jako `-optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-109">The `-optionexplicit+` option is the default and is the same as `-optionexplicit`.</span></span> <span data-ttu-id="e7eb5-110">`-optionexplicit-` Možnost umožňuje implicitní deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-110">The `-optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7eb5-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7eb5-111">Remarks</span></span>  
 <span data-ttu-id="e7eb5-112">Pokud obsahuje souboru se zdrojovým kódem [příkazu Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), přepíše příkaz `-optionexplicit` nastavení kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-112">If the source code file contains an [Option Explicit statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `-optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="e7eb5-113">Chcete-li nastavit - optionexplicit v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e7eb5-113">To set -optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="e7eb5-114">Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e7eb5-115">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-115">On the **Project** menu, click **Properties**.</span></span>   
  
2.  <span data-ttu-id="e7eb5-116">Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-116">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="e7eb5-117">Změňte hodnotu v **Option Explicit** pole.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-117">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7eb5-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7eb5-118">Example</span></span>  
 <span data-ttu-id="e7eb5-119">Následující kód zkompiluje při `-optionexplicit-` se používá.</span><span class="sxs-lookup"><span data-stu-id="e7eb5-119">The following code compiles when `-optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e7eb5-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7eb5-120">See Also</span></span>  
 [<span data-ttu-id="e7eb5-121">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="e7eb5-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e7eb5-122">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="e7eb5-122">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="e7eb5-123">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="e7eb5-123">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="e7eb5-124">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="e7eb5-124">-optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="e7eb5-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="e7eb5-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="e7eb5-126">Příkaz Option Explicit</span><span class="sxs-lookup"><span data-stu-id="e7eb5-126">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="e7eb5-127">Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7eb5-127">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
