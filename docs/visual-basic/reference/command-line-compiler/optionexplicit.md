---
title: /optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1cfdb94ebafa7d6a14253aeb59ab98b3a953fe4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optionexplicit"></a><span data-ttu-id="5a405-102">/optionexplicit</span><span class="sxs-lookup"><span data-stu-id="5a405-102">/optionexplicit</span></span>
<span data-ttu-id="5a405-103">Pokud nejsou proměnné deklarovány před použitím způsobí, že kompilátor zprávy o chybách.</span><span class="sxs-lookup"><span data-stu-id="5a405-103">Causes the compiler to report errors if variables are not declared before they are used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a405-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a405-104">Syntax</span></span>  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="5a405-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="5a405-105">Arguments</span></span>  
 <span data-ttu-id="5a405-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="5a405-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="5a405-107">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="5a405-107">Optional.</span></span> <span data-ttu-id="5a405-108">Zadejte `/optionexplicit+` tak, aby vyžadovala explicitní deklarace proměnné.</span><span class="sxs-lookup"><span data-stu-id="5a405-108">Specify `/optionexplicit+` to require explicit declaration of variables.</span></span> <span data-ttu-id="5a405-109">`/optionexplicit+` Možnost je výchozí a je stejná jako `/optionexplicit`.</span><span class="sxs-lookup"><span data-stu-id="5a405-109">The `/optionexplicit+` option is the default and is the same as `/optionexplicit`.</span></span> <span data-ttu-id="5a405-110">`/optionexplicit-` Možnost umožňuje implicitní deklarace proměnných.</span><span class="sxs-lookup"><span data-stu-id="5a405-110">The `/optionexplicit-` option enables implicit declaration of variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a405-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a405-111">Remarks</span></span>  
 <span data-ttu-id="5a405-112">Pokud obsahuje souboru se zdrojovým kódem [Option Explicit – příkaz](../../../visual-basic/language-reference/statements/option-explicit-statement.md), přepíše příkaz `/optionexplicit` nastavení kompilátoru příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="5a405-112">If the source code file contains an [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md), the statement overrides the `/optionexplicit` command-line compiler setting.</span></span>  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a><span data-ttu-id="5a405-113">Chcete-li nastavit/optionexplicit v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5a405-113">To set /optionexplicit in the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="5a405-114">Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="5a405-114">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5a405-115">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5a405-115">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="5a405-116">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="5a405-116">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="5a405-117">Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="5a405-117">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="5a405-118">Změňte hodnotu v **Option Explicit** pole.</span><span class="sxs-lookup"><span data-stu-id="5a405-118">Modify the value in the **Option Explicit** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a405-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a405-119">Example</span></span>  
 <span data-ttu-id="5a405-120">Následující kód zkompiluje při `/optionexplicit-` se používá.</span><span class="sxs-lookup"><span data-stu-id="5a405-120">The following code compiles when `/optionexplicit-` is used.</span></span>  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5a405-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a405-121">See Also</span></span>  
 [<span data-ttu-id="5a405-122">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="5a405-122">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="5a405-123">/ optioncompare</span><span class="sxs-lookup"><span data-stu-id="5a405-123">/optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [<span data-ttu-id="5a405-124">/ optionstrict</span><span class="sxs-lookup"><span data-stu-id="5a405-124">/optionstrict</span></span>](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [<span data-ttu-id="5a405-125">/ optioninfer</span><span class="sxs-lookup"><span data-stu-id="5a405-125">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="5a405-126">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="5a405-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="5a405-127">Option Explicit – příkaz</span><span class="sxs-lookup"><span data-stu-id="5a405-127">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="5a405-128">Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a405-128">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
