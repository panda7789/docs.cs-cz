---
title: Vyhodnocení funkce je zakázáno, protože při vyhodnocování předchozí verze vypršel časový limit.
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 7b0113e9c1018772da6dc180f7fc5beb0e922917
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402950"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="473c9-102">Vyhodnocení funkce je zakázáno, protože při vyhodnocování předchozí verze vypršel časový limit.</span><span class="sxs-lookup"><span data-stu-id="473c9-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="473c9-103">Vyhodnocení funkce je zakázáno, protože vypršel časový limit pro předchozí vyhodnocení funkce. Chcete-li znovu povolit vyhodnocení funkce, proveďte krok znovu nebo znovu spusťte ladění.</span><span class="sxs-lookup"><span data-stu-id="473c9-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="473c9-104">Výraz v ladicím programu sady Visual Studio určuje volání procedury, ale vypršel limit jiného vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="473c9-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="473c9-105">Možné příčiny vypršení časového limitu volání procedury zahrnují nekonečnou smyčku nebo *nekonečné smyčky*.</span><span class="sxs-lookup"><span data-stu-id="473c9-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="473c9-106">Další informace najdete v tématu [... Další příkaz](../statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="473c9-106">For more information, see [For...Next Statement](../statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="473c9-107">Zvláštní případ nekonečné smyčky je *rekurze*.</span><span class="sxs-lookup"><span data-stu-id="473c9-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="473c9-108">Další informace naleznete v tématu [rekurzivní procedury](../../programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="473c9-108">For more information, see [Recursive Procedures](../../programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="473c9-109">**ID chyby:** BC30957</span><span class="sxs-lookup"><span data-stu-id="473c9-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="473c9-110">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="473c9-110">To correct this error</span></span>  
  
1. <span data-ttu-id="473c9-111">Pokud je to možné, určete, co bylo předchozí vyhodnocení funkce a co způsobilo vypršení časového limitu. V opačném případě se tato chyba může zobrazit znovu.</span><span class="sxs-lookup"><span data-stu-id="473c9-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2. <span data-ttu-id="473c9-112">Proveďte krok ladicího programu znovu nebo ladění ukončete a znovu spusťte.</span><span class="sxs-lookup"><span data-stu-id="473c9-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473c9-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="473c9-113">See also</span></span>

- [<span data-ttu-id="473c9-114">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="473c9-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="473c9-115">Procházení kódu s ladicím programem</span><span class="sxs-lookup"><span data-stu-id="473c9-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
