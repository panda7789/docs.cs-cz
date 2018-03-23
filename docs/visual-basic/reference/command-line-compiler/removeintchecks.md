---
title: -removeintchecks
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- -removeintchecks
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25a14ffaca6e61c6e3306f8ff58de441e2ba2ade
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="-removeintchecks"></a><span data-ttu-id="f7df6-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="f7df6-102">-removeintchecks</span></span>
<span data-ttu-id="f7df6-103">Změní chybu přetečení kontrola celočíselné operace zapnutí nebo vypnutí.</span><span class="sxs-lookup"><span data-stu-id="f7df6-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7df6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7df6-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f7df6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f7df6-105">Arguments</span></span>  
  
|<span data-ttu-id="f7df6-106">Termín</span><span class="sxs-lookup"><span data-stu-id="f7df6-106">Term</span></span>|<span data-ttu-id="f7df6-107">Definice</span><span class="sxs-lookup"><span data-stu-id="f7df6-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="f7df6-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="f7df6-108">`+` &#124; `-`</span></span>|<span data-ttu-id="f7df6-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f7df6-109">Optional.</span></span> <span data-ttu-id="f7df6-110">`-removeintchecks-` Způsobí, že kompilátor ke kontrole všech výpočtů celé číslo chyby přetečení.</span><span class="sxs-lookup"><span data-stu-id="f7df6-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="f7df6-111">Výchozí hodnota je `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="f7df6-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="f7df6-112">Určení `-removeintchecks` nebo `-removeintchecks+` zabraňuje Kontrola chyb a provádět výpočty celé číslo rychlejší.</span><span class="sxs-lookup"><span data-stu-id="f7df6-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="f7df6-113">Ale bez chyby kontroly, a pokud jsou k přetečení datového typu kapacity, nesprávné výsledky mohou být uloženy bez vyvolání k chybě.</span><span class="sxs-lookup"><span data-stu-id="f7df6-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="f7df6-114">Chcete-li nastavit - removeintchecks v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f7df6-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="f7df6-115">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="f7df6-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f7df6-116">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f7df6-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="f7df6-117">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="f7df6-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="f7df6-118">3.  Klikněte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f7df6-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="f7df6-119">4.  Změnit hodnotu **odebrat kontroly přetečení celých** pole.</span><span class="sxs-lookup"><span data-stu-id="f7df6-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f7df6-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7df6-120">Example</span></span>  
 <span data-ttu-id="f7df6-121">Následující kód zkompiluje `Test.vb` a vypne kontrolu chybu přetečení celé číslo.</span><span class="sxs-lookup"><span data-stu-id="f7df6-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f7df6-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7df6-122">See Also</span></span>  
 [<span data-ttu-id="f7df6-123">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="f7df6-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="f7df6-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="f7df6-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
