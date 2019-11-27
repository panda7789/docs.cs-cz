---
title: Ostatní řídicí struktury
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 758df361f421684655147ae288af3f350e53c4d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348136"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="ed010-102">Ostatní řídicí struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed010-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="ed010-103">Visual Basic poskytuje řídicí struktury, které vám pomůžou uvolnit prostředek nebo snížit počet pokusů o opakování odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="ed010-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="ed010-104">Pomocí... Konec používání konstrukce</span><span class="sxs-lookup"><span data-stu-id="ed010-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="ed010-105">Konstrukce `Using...End Using` vytvoří blok příkazů, ve kterém budete používat prostředek, jako je třeba připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="ed010-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="ed010-106">Volitelně můžete získat prostředek pomocí příkazu `Using`.</span><span class="sxs-lookup"><span data-stu-id="ed010-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="ed010-107">Když ukončíte blok `Using`, Visual Basic automaticky odstraní prostředek, aby byl k dispozici pro použití pro jiný kód.</span><span class="sxs-lookup"><span data-stu-id="ed010-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="ed010-108">Prostředek musí být místní a na jedno použití.</span><span class="sxs-lookup"><span data-stu-id="ed010-108">The resource must be local and disposable.</span></span> <span data-ttu-id="ed010-109">Další informace naleznete v tématu [using – příkaz](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ed010-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="ed010-110">S... Ukončit se konstrukcí</span><span class="sxs-lookup"><span data-stu-id="ed010-110">With...End With Construction</span></span>  
 <span data-ttu-id="ed010-111">Konstrukce `With...End With` umožňuje zadat odkaz na objekt jednou a potom spustit sérii příkazů, které přistupují k jeho členům.</span><span class="sxs-lookup"><span data-stu-id="ed010-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="ed010-112">To může zjednodušit váš kód a zvýšit výkon, protože Visual Basic není nutné znovu vytvořit odkaz pro každý příkaz, který k němu přistupuje.</span><span class="sxs-lookup"><span data-stu-id="ed010-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="ed010-113">Další informace najdete v tématu [s... Příkaz end with](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)</span><span class="sxs-lookup"><span data-stu-id="ed010-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed010-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed010-114">See also</span></span>

- [<span data-ttu-id="ed010-115">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="ed010-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="ed010-116">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="ed010-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="ed010-117">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="ed010-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="ed010-118">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="ed010-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="ed010-119">Příkaz Using</span><span class="sxs-lookup"><span data-stu-id="ed010-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
- [<span data-ttu-id="ed010-120">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="ed010-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
