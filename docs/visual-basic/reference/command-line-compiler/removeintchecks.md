---
title: -removeintchecks
ms.date: 03/13/2018
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
ms.openlocfilehash: 26485fe2ba3f5647266147744cbe53f978694a9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656123"
---
# <a name="-removeintchecks"></a><span data-ttu-id="7397a-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="7397a-102">-removeintchecks</span></span>
<span data-ttu-id="7397a-103">Změní chybu přetečení kontrola celočíselné operace zapnutí nebo vypnutí.</span><span class="sxs-lookup"><span data-stu-id="7397a-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7397a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7397a-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7397a-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7397a-105">Arguments</span></span>  
  
|<span data-ttu-id="7397a-106">Termín</span><span class="sxs-lookup"><span data-stu-id="7397a-106">Term</span></span>|<span data-ttu-id="7397a-107">Definice</span><span class="sxs-lookup"><span data-stu-id="7397a-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="7397a-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="7397a-108">`+` &#124; `-`</span></span>|<span data-ttu-id="7397a-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="7397a-109">Optional.</span></span> <span data-ttu-id="7397a-110">`-removeintchecks-` Způsobí, že kompilátor ke kontrole všech výpočtů celé číslo chyby přetečení.</span><span class="sxs-lookup"><span data-stu-id="7397a-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="7397a-111">Výchozí hodnota je `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="7397a-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="7397a-112">Určení `-removeintchecks` nebo `-removeintchecks+` zabraňuje Kontrola chyb a provádět výpočty celé číslo rychlejší.</span><span class="sxs-lookup"><span data-stu-id="7397a-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="7397a-113">Ale bez chyby kontroly, a pokud jsou k přetečení datového typu kapacity, nesprávné výsledky mohou být uloženy bez vyvolání k chybě.</span><span class="sxs-lookup"><span data-stu-id="7397a-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="7397a-114">Chcete-li nastavit - removeintchecks v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7397a-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="7397a-115">1.  Máte projekt vybraný v **Průzkumníku řešení**.</span><span class="sxs-lookup"><span data-stu-id="7397a-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7397a-116">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7397a-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="7397a-117">2.  Klikněte **zkompilovat** kartě.</span><span class="sxs-lookup"><span data-stu-id="7397a-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="7397a-118">3.  Klikněte **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7397a-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="7397a-119">4.  Změnit hodnotu **odebrat kontroly přetečení celých** pole.</span><span class="sxs-lookup"><span data-stu-id="7397a-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7397a-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="7397a-120">Example</span></span>  
 <span data-ttu-id="7397a-121">Následující kód zkompiluje `Test.vb` a vypne kontrolu chybu přetečení celé číslo.</span><span class="sxs-lookup"><span data-stu-id="7397a-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7397a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="7397a-122">See Also</span></span>  
 [<span data-ttu-id="7397a-123">Visual Basic – kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="7397a-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="7397a-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="7397a-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
