---
title: -optioninfer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df01fccd7276f0ec759065306ad3614d735f89ef
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-optioninfer"></a><span data-ttu-id="a5563-102">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="a5563-102">-optioninfer</span></span>
<span data-ttu-id="a5563-103">Umožňuje použití odvození místního typu v deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="a5563-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5563-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5563-104">Syntax</span></span>  
  
```  
-optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="a5563-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="a5563-105">Arguments</span></span>  
  
|<span data-ttu-id="a5563-106">Termín</span><span class="sxs-lookup"><span data-stu-id="a5563-106">Term</span></span>|<span data-ttu-id="a5563-107">Definice</span><span class="sxs-lookup"><span data-stu-id="a5563-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="a5563-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="a5563-108">`+` &#124; `-`</span></span>|<span data-ttu-id="a5563-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="a5563-109">Optional.</span></span> <span data-ttu-id="a5563-110">Zadejte `-optioninfer+` povolit odvození místního typu nebo `-optioninfer-` zablokujete jeho.</span><span class="sxs-lookup"><span data-stu-id="a5563-110">Specify `-optioninfer+` to enable local type inference, or `-optioninfer-` to block it.</span></span> <span data-ttu-id="a5563-111">`-optioninfer` Možnost s žádná hodnota zadána, je stejný jako `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="a5563-111">The `-optioninfer` option, with no value specified, is the same as `-optioninfer+`.</span></span> <span data-ttu-id="a5563-112">Výchozí hodnotu v případě `-optioninfer` přepínač není k dispozici je také `-optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="a5563-112">The default value when the `-optioninfer` switch is not present is also `-optioninfer+`.</span></span> <span data-ttu-id="a5563-113">Výchozí hodnota je nastavena v souboru odpovědí, Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="a5563-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a5563-114">Můžete použít `-noconfig` možnost zachování interní výchozí nastavení kompilátoru místo platformám zadaným v vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="a5563-114">You can use the `-noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="a5563-115">Tato možnost je výchozí hodnotou kompilátoru `-optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="a5563-115">The compiler default for this option is `-optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5563-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5563-116">Remarks</span></span>  
 <span data-ttu-id="a5563-117">Pokud obsahuje souboru se zdrojovým kódem [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md), přepíše příkaz `-optioninfer` nastavení kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a5563-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `-optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set--optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="a5563-118">Chcete-li nastavit - optioninfer v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a5563-118">To set -optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="a5563-119">Vyberte projekt v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="a5563-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="a5563-120">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a5563-120">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="a5563-121">Na **zkompilovat** kartě, změňte hodnotu v **Option infer –** pole.</span><span class="sxs-lookup"><span data-stu-id="a5563-121">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5563-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5563-122">Example</span></span>  
 <span data-ttu-id="a5563-123">Následující kód zkompiluje `test.vb` s odvození místního typu povolen.</span><span class="sxs-lookup"><span data-stu-id="a5563-123">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```console
vbc -optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5563-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5563-124">See Also</span></span>  
 [<span data-ttu-id="a5563-125">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="a5563-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a5563-126">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="a5563-126">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="a5563-127">-optionexplicit</span><span class="sxs-lookup"><span data-stu-id="a5563-127">-optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="a5563-128">-optionstrict</span><span class="sxs-lookup"><span data-stu-id="a5563-128">-optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="a5563-129">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="a5563-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="a5563-130">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="a5563-130">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="a5563-131">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="a5563-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="a5563-132">Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5563-132">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="a5563-133">Stránka Kompilovat, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5563-133">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="a5563-134">/noconfig</span><span class="sxs-lookup"><span data-stu-id="a5563-134">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="a5563-135">Sestavení z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="a5563-135">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
