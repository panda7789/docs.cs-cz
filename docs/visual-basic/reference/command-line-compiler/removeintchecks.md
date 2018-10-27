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
ms.openlocfilehash: f061497083dc23fd07f61108938a4129c0af5f3a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188524"
---
# <a name="-removeintchecks"></a><span data-ttu-id="c4d02-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="c4d02-102">-removeintchecks</span></span>
<span data-ttu-id="c4d02-103">Zapne přetečení-Chyba při kontrole celočíselné operace zapnutí nebo vypnutí.</span><span class="sxs-lookup"><span data-stu-id="c4d02-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4d02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4d02-104">Syntax</span></span>  
  
```  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="c4d02-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c4d02-105">Arguments</span></span>  
  
|<span data-ttu-id="c4d02-106">Termín</span><span class="sxs-lookup"><span data-stu-id="c4d02-106">Term</span></span>|<span data-ttu-id="c4d02-107">Definice</span><span class="sxs-lookup"><span data-stu-id="c4d02-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="c4d02-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="c4d02-108">`+` &#124; `-`</span></span>|<span data-ttu-id="c4d02-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c4d02-109">Optional.</span></span> <span data-ttu-id="c4d02-110">`-removeintchecks-` Možnost způsobí, že kompilátoru, aby všechny výpočty celé číslo chyby přetečení.</span><span class="sxs-lookup"><span data-stu-id="c4d02-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="c4d02-111">Výchozí hodnota je `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="c4d02-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="c4d02-112">Určení `-removeintchecks` nebo `-removeintchecks+` brání kontroly chyb a rychlejší kvůli výpočtům celé číslo.</span><span class="sxs-lookup"><span data-stu-id="c4d02-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="c4d02-113">Ale bez kontroly chyb, a pokud jsou datové kapacity. typ došlo k přetečení, nesprávné výsledky mohou být uložena bez vyvolání k chybě.</span><span class="sxs-lookup"><span data-stu-id="c4d02-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="c4d02-114">Chcete-li nastavit - removeintchecks v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c4d02-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="c4d02-115">1.  Mají projekt vybraný v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="c4d02-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c4d02-116">Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="c4d02-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="c4d02-117">2.  Klikněte na tlačítko **kompilaci** kartu.</span><span class="sxs-lookup"><span data-stu-id="c4d02-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="c4d02-118">3.  Klikněte na tlačítko **Upřesnit** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c4d02-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="c4d02-119">4.  Změnit hodnotu **odebrat kontroly přetečení celých čísel** pole.</span><span class="sxs-lookup"><span data-stu-id="c4d02-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c4d02-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4d02-120">Example</span></span>  
 <span data-ttu-id="c4d02-121">Následující kód zkompiluje `Test.vb` a vypne kontrolu chyb přetečení celého čísla.</span><span class="sxs-lookup"><span data-stu-id="c4d02-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="c4d02-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4d02-122">See Also</span></span>  
 [<span data-ttu-id="c4d02-123">Kompilátor příkazového řádku jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4d02-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="c4d02-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="c4d02-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
