---
title: /optioninfer
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optioninfer
helpviewer_keywords:
- -optioninfer compiler option [Visual Basic]
- /optioninfer compiler option [Visual Basic]
- optioninfer compiler option [Visual Basic]
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4400ee58214c8f9990d4b123e17ef0f6553a5a69
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optioninfer"></a><span data-ttu-id="7d23e-102">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="7d23e-102">/optioninfer</span></span>
<span data-ttu-id="7d23e-103">Umožňuje použití odvození místního typu v deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="7d23e-103">Enables the use of local type inference in variable declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d23e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d23e-104">Syntax</span></span>  
  
```  
/optioninfer[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7d23e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7d23e-105">Arguments</span></span>  
  
|<span data-ttu-id="7d23e-106">Termín</span><span class="sxs-lookup"><span data-stu-id="7d23e-106">Term</span></span>|<span data-ttu-id="7d23e-107">Definice</span><span class="sxs-lookup"><span data-stu-id="7d23e-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="7d23e-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="7d23e-108">`+` &#124; `-`</span></span>|<span data-ttu-id="7d23e-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="7d23e-109">Optional.</span></span> <span data-ttu-id="7d23e-110">Zadejte `/optioninfer+` povolit odvození místního typu nebo `/optioninfer-` zablokujete jeho.</span><span class="sxs-lookup"><span data-stu-id="7d23e-110">Specify `/optioninfer+` to enable local type inference, or `/optioninfer-` to block it.</span></span> <span data-ttu-id="7d23e-111">`/optioninfer` Možnost s žádná hodnota zadána, je stejný jako `/optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="7d23e-111">The `/optioninfer` option, with no value specified, is the same as `/optioninfer+`.</span></span> <span data-ttu-id="7d23e-112">Výchozí hodnotu v případě `/optioninfer` přepínač není k dispozici je také `/optioninfer+`.</span><span class="sxs-lookup"><span data-stu-id="7d23e-112">The default value when the `/optioninfer` switch is not present is also `/optioninfer+`.</span></span> <span data-ttu-id="7d23e-113">Výchozí hodnota je nastavena v souboru odpovědí, Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="7d23e-113">The default value is set in the Vbc.rsp response file.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="7d23e-114">Můžete použít `/noconfig` možnost zachování interní výchozí nastavení kompilátoru místo platformám zadaným v vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="7d23e-114">You can use the `/noconfig` option to retain the compiler's internal defaults instead of those specified in vbc.rsp.</span></span> <span data-ttu-id="7d23e-115">Tato možnost je výchozí hodnotou kompilátoru `/optioninfer-`.</span><span class="sxs-lookup"><span data-stu-id="7d23e-115">The compiler default for this option is `/optioninfer-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d23e-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d23e-116">Remarks</span></span>  
 <span data-ttu-id="7d23e-117">Pokud obsahuje souboru se zdrojovým kódem [Option Infer – příkaz](../../../visual-basic/language-reference/statements/option-infer-statement.md), přepíše příkaz `/optioninfer` nastavení kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7d23e-117">If the source code file contains an [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md), the statement overrides the `/optioninfer` command-line compiler setting.</span></span>  
  
### <a name="to-set-optioninfer-in-the-visual-studio-ide"></a><span data-ttu-id="7d23e-118">Chcete-li nastavit/optioninfer v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7d23e-118">To set /optioninfer in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="7d23e-119">Vyberte projekt v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="7d23e-119">Select a project in **Solution Explorer**.</span></span> <span data-ttu-id="7d23e-120">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7d23e-120">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="7d23e-121">Další informace najdete v tématu [NIB: Správa vlastností projektu s Návrhář projektu](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="7d23e-121">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="7d23e-122">Na **zkompilovat** kartě, změňte hodnotu v **Option infer –** pole.</span><span class="sxs-lookup"><span data-stu-id="7d23e-122">On the **Compile** tab, modify the value in the **Option infer** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d23e-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d23e-123">Example</span></span>  
 <span data-ttu-id="7d23e-124">Následující kód zkompiluje `test.vb` s odvození místního typu povolen.</span><span class="sxs-lookup"><span data-stu-id="7d23e-124">The following code compiles `test.vb` with local type inference enabled.</span></span>  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7d23e-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d23e-125">See Also</span></span>  
 [<span data-ttu-id="7d23e-126">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="7d23e-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="7d23e-127">/ optioncompare</span><span class="sxs-lookup"><span data-stu-id="7d23e-127">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="7d23e-128">/ optionexplicit</span><span class="sxs-lookup"><span data-stu-id="7d23e-128">/optionexplicit</span></span>](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [<span data-ttu-id="7d23e-129">/ optionstrict</span><span class="sxs-lookup"><span data-stu-id="7d23e-129">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="7d23e-130">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="7d23e-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="7d23e-131">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="7d23e-131">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="7d23e-132">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="7d23e-132">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="7d23e-133">Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d23e-133">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="7d23e-134">Stránka kompilovat, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d23e-134">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [<span data-ttu-id="7d23e-135">/ noconfig</span><span class="sxs-lookup"><span data-stu-id="7d23e-135">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="7d23e-136">Sestavování z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="7d23e-136">Building from the Command Line</span></span>](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)
