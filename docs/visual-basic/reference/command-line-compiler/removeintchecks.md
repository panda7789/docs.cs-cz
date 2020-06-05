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
ms.openlocfilehash: ec4722cb7088819dae95ca1b7cbc1469d957a7aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400471"
---
# <a name="-removeintchecks"></a><span data-ttu-id="f3e8c-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="f3e8c-102">-removeintchecks</span></span>
<span data-ttu-id="f3e8c-103">Zapne nebo vypne kontrolu chyb pro celočíselné operace.</span><span class="sxs-lookup"><span data-stu-id="f3e8c-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e8c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3e8c-104">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f3e8c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f3e8c-105">Arguments</span></span>  
  
|<span data-ttu-id="f3e8c-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="f3e8c-106">Term</span></span>|<span data-ttu-id="f3e8c-107">Definice</span><span class="sxs-lookup"><span data-stu-id="f3e8c-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="f3e8c-108">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="f3e8c-108">`+` &#124; `-`</span></span>|<span data-ttu-id="f3e8c-109">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f3e8c-109">Optional.</span></span> <span data-ttu-id="f3e8c-110">`-removeintchecks-`Možnost způsobí, že kompilátor zkontroluje všechny celočíselné výpočty pro chyby přetečení.</span><span class="sxs-lookup"><span data-stu-id="f3e8c-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="f3e8c-111">Výchozí formát je `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="f3e8c-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="f3e8c-112">Určení `-removeintchecks` nebo `-removeintchecks+` zabránění v kontrole chyb a rychlejší provádění výpočtů v celých číslech</span><span class="sxs-lookup"><span data-stu-id="f3e8c-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="f3e8c-113">Bez kontroly chyb a v případě, že dojde k přetečení kapacit datových typů, mohou být uloženy nesprávné výsledky bez vyvolání chyby.</span><span class="sxs-lookup"><span data-stu-id="f3e8c-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="f3e8c-114">Nastavení-removeintchecks – v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f3e8c-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="f3e8c-115">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="f3e8c-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f3e8c-116">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="f3e8c-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="f3e8c-117">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="f3e8c-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="f3e8c-118">3. klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="f3e8c-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="f3e8c-119">4. Změňte hodnotu pole **Odebrat kontroly přetečení celých čísel** .</span><span class="sxs-lookup"><span data-stu-id="f3e8c-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f3e8c-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3e8c-120">Example</span></span>  
 <span data-ttu-id="f3e8c-121">Následující kód zkompiluje `Test.vb` a vypne přetečení celého čísla – kontrola chyb.</span><span class="sxs-lookup"><span data-stu-id="f3e8c-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3e8c-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3e8c-122">See also</span></span>

- [<span data-ttu-id="f3e8c-123">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="f3e8c-123">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="f3e8c-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="f3e8c-124">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
