---
title: Vyhodnocení funkce je zakázáno, protože při vyhodnocování předchozí verze vypršel časový limit.
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 6231d48f3f90d8e436dc80bf4670886c1d030387
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587649"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="e5768-102">Vyhodnocení funkce je zakázáno, protože při vyhodnocování předchozí verze vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="e5768-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="e5768-103">Vyhodnocení funkce je zakázáno, protože vypršel časový limit předchozího vyhodnocení funkce. Znovu povolit vyhodnocení funkce, krok opakujte nebo restartujte ladění.</span><span class="sxs-lookup"><span data-stu-id="e5768-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="e5768-104">Výraz v ladicím programu sady Visual Studio určuje volání procedury, ale vypršel limit jiného vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="e5768-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="e5768-105">Možné příčiny vypršení časového limitu volání procedury patří nekonečné smyčce nebo *nekonečná smyčka*.</span><span class="sxs-lookup"><span data-stu-id="e5768-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="e5768-106">Další informace najdete v tématu [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5768-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="e5768-107">Je ve speciálním případě nekonečné smyčce *rekurze*.</span><span class="sxs-lookup"><span data-stu-id="e5768-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="e5768-108">Další informace najdete v tématu [rekurzivní procedury](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e5768-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="e5768-109">**ID chyby:** BC30957</span><span class="sxs-lookup"><span data-stu-id="e5768-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e5768-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e5768-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="e5768-111">Je-li to možné, určete, o jaké dřívější vyhodnocení funkce se jedná a co způsobilo vypršení jejího časového limitu. Jinak může k této chybě dojít znovu.</span><span class="sxs-lookup"><span data-stu-id="e5768-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2.  <span data-ttu-id="e5768-112">Proveďte krok ladicího programu znovu nebo ladění ukončete a znovu spusťte.</span><span class="sxs-lookup"><span data-stu-id="e5768-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5768-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5768-113">See Also</span></span>  
 [<span data-ttu-id="e5768-114">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e5768-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="e5768-115">Procházení kódu s ladicím programem</span><span class="sxs-lookup"><span data-stu-id="e5768-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
