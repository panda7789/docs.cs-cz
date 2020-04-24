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
ms.openlocfilehash: bea6ca24ea6da9000267e754d52fe0ca152f7d7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005224"
---
# <a name="-removeintchecks"></a><span data-ttu-id="9a936-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="9a936-102">-removeintchecks</span></span>
<span data-ttu-id="9a936-103">Zapne nebo vypne kontrolu chyb pro celočíselné operace.</span><span class="sxs-lookup"><span data-stu-id="9a936-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a936-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a936-104">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9a936-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9a936-105">Arguments</span></span>  
  
|<span data-ttu-id="9a936-106">Označení</span><span class="sxs-lookup"><span data-stu-id="9a936-106">Term</span></span>|<span data-ttu-id="9a936-107">Definice</span><span class="sxs-lookup"><span data-stu-id="9a936-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="9a936-108">`+`&#124;`-`</span><span class="sxs-lookup"><span data-stu-id="9a936-108">`+` &#124; `-`</span></span>|<span data-ttu-id="9a936-109">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9a936-109">Optional.</span></span> <span data-ttu-id="9a936-110">`-removeintchecks-` Možnost způsobí, že kompilátor zkontroluje všechny celočíselné výpočty pro chyby přetečení.</span><span class="sxs-lookup"><span data-stu-id="9a936-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="9a936-111">Výchozí formát je `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="9a936-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="9a936-112">Určení `-removeintchecks` nebo `-removeintchecks+` zabránění v kontrole chyb a rychlejší provádění výpočtů v celých číslech</span><span class="sxs-lookup"><span data-stu-id="9a936-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="9a936-113">Bez kontroly chyb a v případě, že dojde k přetečení kapacit datových typů, mohou být uloženy nesprávné výsledky bez vyvolání chyby.</span><span class="sxs-lookup"><span data-stu-id="9a936-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="9a936-114">Nastavení-removeintchecks – v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9a936-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="9a936-115">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="9a936-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="9a936-116">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="9a936-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="9a936-117">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="9a936-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="9a936-118">3. klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="9a936-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="9a936-119">4. Změňte hodnotu pole **Odebrat kontroly přetečení celých čísel** .</span><span class="sxs-lookup"><span data-stu-id="9a936-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9a936-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a936-120">Example</span></span>  
 <span data-ttu-id="9a936-121">Následující kód zkompiluje `Test.vb` a vypne přetečení celého čísla – kontrola chyb.</span><span class="sxs-lookup"><span data-stu-id="9a936-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9a936-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a936-122">See also</span></span>

- [<span data-ttu-id="9a936-123">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="9a936-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="9a936-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="9a936-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
