---
title: /removeintchecks
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e765f0007eea8e196b1a1b3b55b969c5b074b52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="removeintchecks"></a><span data-ttu-id="2bc60-102">/removeintchecks</span><span class="sxs-lookup"><span data-stu-id="2bc60-102">/removeintchecks</span></span>
<span data-ttu-id="2bc60-103">Změní chybu přetečení kontrola celočíselné operace zapnutí nebo vypnutí.</span><span class="sxs-lookup"><span data-stu-id="2bc60-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc60-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bc60-104">Syntax</span></span>  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2bc60-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2bc60-105">Arguments</span></span>  
  
|<span data-ttu-id="2bc60-106">Termín</span><span class="sxs-lookup"><span data-stu-id="2bc60-106">Term</span></span>|<span data-ttu-id="2bc60-107">Definice</span><span class="sxs-lookup"><span data-stu-id="2bc60-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="2bc60-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="2bc60-108">`+` &#124; `-`</span></span>|<span data-ttu-id="2bc60-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2bc60-109">Optional.</span></span> <span data-ttu-id="2bc60-110">`/removeintchecks-` Způsobí, že kompilátor ke kontrole všech výpočtů celé číslo chyby přetečení.</span><span class="sxs-lookup"><span data-stu-id="2bc60-110">The `/removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="2bc60-111">Výchozí hodnota je `/removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="2bc60-111">The default is `/removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="2bc60-112">Určení `/removeintchecks` nebo `/removeintchecks+` zabraňuje Kontrola chyb a provádět výpočty celé číslo rychlejší.</span><span class="sxs-lookup"><span data-stu-id="2bc60-112">Specifying `/removeintchecks` or `/removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="2bc60-113">Ale bez chyby kontroly, a pokud jsou k přetečení datového typu kapacity, nesprávné výsledky mohou být uloženy bez vyvolání k chybě.</span><span class="sxs-lookup"><span data-stu-id="2bc60-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="2bc60-114">Chcete-li nastavit/removeintchecks v sadě Visual Studio integrované vývojové prostředí</span><span class="sxs-lookup"><span data-stu-id="2bc60-114">To set /removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="2bc60-115">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="2bc60-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="2bc60-116">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="2bc60-116">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="2bc60-117">Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="2bc60-117">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="2bc60-118">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="2bc60-118">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="2bc60-119">3.  Klikněte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2bc60-119">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="2bc60-120">4.  Změnit hodnotu **odebrat kontroly přetečení celých** pole.</span><span class="sxs-lookup"><span data-stu-id="2bc60-120">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2bc60-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="2bc60-121">Example</span></span>  
 <span data-ttu-id="2bc60-122">Následující kód zkompiluje `Test.vb` a vypne kontrolu chybu přetečení celé číslo.</span><span class="sxs-lookup"><span data-stu-id="2bc60-122">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2bc60-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bc60-123">See Also</span></span>  
 [<span data-ttu-id="2bc60-124">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2bc60-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="2bc60-125">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="2bc60-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
