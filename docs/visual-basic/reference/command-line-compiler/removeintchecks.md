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
# <a name="-removeintchecks"></a><span data-ttu-id="8cdd9-102">-removeintchecks</span><span class="sxs-lookup"><span data-stu-id="8cdd9-102">-removeintchecks</span></span>
<span data-ttu-id="8cdd9-103">Zapne nebo vypne kontrolu chyb pro celočíselné operace.</span><span class="sxs-lookup"><span data-stu-id="8cdd9-103">Turns overflow-error checking for integer operations on or off.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cdd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cdd9-104">Syntax</span></span>  
  
```console  
-removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8cdd9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="8cdd9-105">Arguments</span></span>  
  
|<span data-ttu-id="8cdd9-106">Termín</span><span class="sxs-lookup"><span data-stu-id="8cdd9-106">Term</span></span>|<span data-ttu-id="8cdd9-107">Definice</span><span class="sxs-lookup"><span data-stu-id="8cdd9-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="8cdd9-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="8cdd9-108">`+` &#124; `-`</span></span>|<span data-ttu-id="8cdd9-109">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="8cdd9-109">Optional.</span></span> <span data-ttu-id="8cdd9-110">Možnost `-removeintchecks-` způsobí, že kompilátor zkontroluje všechny celočíselné výpočty pro chyby přetečení.</span><span class="sxs-lookup"><span data-stu-id="8cdd9-110">The `-removeintchecks-` option causes the compiler to check all integer calculations for overflow errors.</span></span> <span data-ttu-id="8cdd9-111">Výchozí hodnota je `-removeintchecks-`.</span><span class="sxs-lookup"><span data-stu-id="8cdd9-111">The default is `-removeintchecks-`.</span></span><br /><br /> <span data-ttu-id="8cdd9-112">Zadáním `-removeintchecks` nebo `-removeintchecks+` zabráníte kontrole chyb a rychleji můžete provádět výpočty celých čísel.</span><span class="sxs-lookup"><span data-stu-id="8cdd9-112">Specifying `-removeintchecks` or `-removeintchecks+` prevents error checking and can make integer calculations faster.</span></span> <span data-ttu-id="8cdd9-113">Bez kontroly chyb a v případě, že dojde k přetečení kapacit datových typů, mohou být uloženy nesprávné výsledky bez vyvolání chyby.</span><span class="sxs-lookup"><span data-stu-id="8cdd9-113">However, without error checking, and if data type capacities are overflowed, incorrect results may be stored without raising an error.</span></span>|  
  
|<span data-ttu-id="8cdd9-114">Nastavení-removeintchecks – v integrovaném vývojovém prostředí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8cdd9-114">To set -removeintchecks in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="8cdd9-115">1. v **Průzkumník řešení**mít vybraný projekt.</span><span class="sxs-lookup"><span data-stu-id="8cdd9-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="8cdd9-116">V nabídce **projekt** klikněte na příkaz **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="8cdd9-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="8cdd9-117">2. klikněte na kartu **kompilovat** .</span><span class="sxs-lookup"><span data-stu-id="8cdd9-117">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="8cdd9-118">3. klikněte na tlačítko **Upřesnit** .</span><span class="sxs-lookup"><span data-stu-id="8cdd9-118">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="8cdd9-119">4. Změňte hodnotu pole **Odebrat kontroly přetečení celých čísel** .</span><span class="sxs-lookup"><span data-stu-id="8cdd9-119">4.  Modify the value of the **Remove integer overflow checks** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8cdd9-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="8cdd9-120">Example</span></span>  
 <span data-ttu-id="8cdd9-121">Následující kód zkompiluje `Test.vb` a vypne přetečení celého čísla – kontrola chyb.</span><span class="sxs-lookup"><span data-stu-id="8cdd9-121">The following code compiles `Test.vb` and turns off integer overflow-error checking.</span></span>  
  
```console
vbc -removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="8cdd9-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8cdd9-122">See also</span></span>

- [<span data-ttu-id="8cdd9-123">Visual Basic Kompilátor příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="8cdd9-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="8cdd9-124">Příkazové řádky ukázkové kompilace</span><span class="sxs-lookup"><span data-stu-id="8cdd9-124">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
