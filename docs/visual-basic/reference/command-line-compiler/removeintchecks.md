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
ms.openlocfilehash: 4c1be34cf76cfb12ea1e3b3246e9e0bc26199c24
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687957"
---
# <a name="-removeintchecks"></a><span data-ttu-id="7a964-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="7a964-102">-removeintchecks</span></span>
<span data-ttu-id="7a964-103">Zapne přetečení-Chyba při kontrole celočíselné operace zapnutí nebo vypnutí.</span><span class="sxs-lookup"><span data-stu-id="7a964-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a964-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a964-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7a964-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7a964-105">Arguments</span></span>  
  
|<span data-ttu-id="7a964-106">Termín</span><span class="sxs-lookup"><span data-stu-id="7a964-106">Term</span></span>|<span data-ttu-id="7a964-107">Definice</span><span class="sxs-lookup"><span data-stu-id="7a964-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="7a964-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="7a964-108">`+` &#124; `-`</span></span>|<span data-ttu-id="7a964-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="7a964-109">Optional.</span></span> <span data-ttu-id="7a964-110">`-removeintchecks-` Možnost způsobí, že kompilátoru, aby všechny výpočty celé číslo chyby přetečení.</span><span class="sxs-lookup"><span data-stu-id="7a964-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="7a964-111">Výchozí hodnota je `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="7a964-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="7a964-112">Určení `-removeintchecks` nebo `-removeintchecks+` brání kontroly chyb a rychlejší kvůli výpočtům celé číslo.</span><span class="sxs-lookup"><span data-stu-id="7a964-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="7a964-113">Ale bez kontroly chyb, a pokud jsou datové kapacity. typ došlo k přetečení, nesprávné výsledky mohou být uložena bez vyvolání k chybě.</span><span class="sxs-lookup"><span data-stu-id="7a964-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="7a964-114">Chcete-li nastavit - removeintchecks v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7a964-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="7a964-115">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="7a964-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7a964-116">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7a964-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="7a964-117">2.  Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="7a964-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="7a964-118">3.  Klikněte na tlačítko **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="7a964-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="7a964-119">4.  Změnit hodnotu **odebrat kontroly přetečení celých čísel** pole.</span><span class="sxs-lookup"><span data-stu-id="7a964-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7a964-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a964-120">Example</span></span>  
 <span data-ttu-id="7a964-121">Následující kód zkompiluje `Test.vb` a vypne kontrolu chyb přetečení celého čísla.</span><span class="sxs-lookup"><span data-stu-id="7a964-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a964-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a964-122">See also</span></span>
- [<span data-ttu-id="7a964-123">Visual Basic Command-Line Compiler</span><span class="sxs-lookup"><span data-stu-id="7a964-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7a964-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="7a964-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
