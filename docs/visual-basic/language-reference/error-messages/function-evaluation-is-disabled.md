---
title: Vyhodnocení funkce je zakázáno, protože při vyhodnocování předchozí verze vypršel časový limit.
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: bc4d05e52434cf62fa90671d29b407c83114b5d2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59315774"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="057be-102">Vyhodnocení funkce je zakázáno, protože při vyhodnocování předchozí verze vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="057be-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="057be-103">Vyhodnocení funkce je zakázaná, protože předchozímu vyhodnocení funkce vypršel. Chcete-li znovu povolit vyhodnocení funkce, proveďte krok znovu nebo restartujte ladění.</span><span class="sxs-lookup"><span data-stu-id="057be-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="057be-104">Výraz v ladicím programu sady Visual Studio určuje volání procedury, ale vypršel limit jiného vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="057be-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="057be-105">Možné příčiny vypršení časového limitu volání procedury patří nekonečná smyčka nebo *vznik nekonečné smyčky*.</span><span class="sxs-lookup"><span data-stu-id="057be-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="057be-106">Další informace najdete v tématu [pro... Další příkaz](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="057be-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="057be-107">Zvláštním případem nekonečné smyčky je *rekurze*.</span><span class="sxs-lookup"><span data-stu-id="057be-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="057be-108">Další informace najdete v tématu [rekurzivní procedury](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="057be-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="057be-109">**ID chyby:** BC30957</span><span class="sxs-lookup"><span data-stu-id="057be-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="057be-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="057be-110">To correct this error</span></span>  
  
1. <span data-ttu-id="057be-111">Je-li to možné, určete, o jaké dřívější vyhodnocení funkce se jedná a co způsobilo vypršení jejího časového limitu. Jinak může k této chybě dojít znovu.</span><span class="sxs-lookup"><span data-stu-id="057be-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2. <span data-ttu-id="057be-112">Proveďte krok ladicího programu znovu nebo ladění ukončete a znovu spusťte.</span><span class="sxs-lookup"><span data-stu-id="057be-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="057be-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="057be-113">See also</span></span>

- [<span data-ttu-id="057be-114">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="057be-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="057be-115">Procházení kódu s ladicím programem</span><span class="sxs-lookup"><span data-stu-id="057be-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
