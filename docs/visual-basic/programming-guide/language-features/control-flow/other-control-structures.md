---
title: Ostatní řídicí struktury
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c6d80b237c7c3512c2904547842fdeb3c69bef68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402015"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="4922f-102">Ostatní řídicí struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4922f-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="4922f-103">Visual Basic poskytuje řídicí struktury, které vám pomůžou uvolnit prostředek nebo snížit počet pokusů o opakování odkazu na objekt.</span><span class="sxs-lookup"><span data-stu-id="4922f-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="4922f-104">Pomocí... Konec používání konstrukce</span><span class="sxs-lookup"><span data-stu-id="4922f-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="4922f-105">`Using...End Using`Konstrukce vytvoří blok příkazů, ve kterém budete používat prostředek, jako je třeba připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="4922f-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="4922f-106">Volitelně můžete získat prostředek pomocí `Using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="4922f-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="4922f-107">Po ukončení `Using` bloku Visual Basic automaticky odstraní prostředek, aby byl k dispozici pro použití pro jiný kód.</span><span class="sxs-lookup"><span data-stu-id="4922f-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="4922f-108">Prostředek musí být místní a na jedno použití.</span><span class="sxs-lookup"><span data-stu-id="4922f-108">The resource must be local and disposable.</span></span> <span data-ttu-id="4922f-109">Další informace naleznete v tématu [using – příkaz](../../../language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4922f-109">For more information, see [Using Statement](../../../language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="4922f-110">S... Ukončit se konstrukcí</span><span class="sxs-lookup"><span data-stu-id="4922f-110">With...End With Construction</span></span>  
 <span data-ttu-id="4922f-111">`With...End With`Konstrukce umožňuje zadat odkaz na objekt jednou a potom spustit sérii příkazů, které přistupují k jeho členům.</span><span class="sxs-lookup"><span data-stu-id="4922f-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="4922f-112">To může zjednodušit váš kód a zvýšit výkon, protože Visual Basic není nutné znovu vytvořit odkaz pro každý příkaz, který k němu přistupuje.</span><span class="sxs-lookup"><span data-stu-id="4922f-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="4922f-113">Další informace najdete v tématu [s... Příkaz end with](../../../language-reference/statements/with-end-with-statement.md)</span><span class="sxs-lookup"><span data-stu-id="4922f-113">For more information, see [With...End With Statement](../../../language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4922f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4922f-114">See also</span></span>

- [<span data-ttu-id="4922f-115">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="4922f-115">Control Flow</span></span>](index.md)
- [<span data-ttu-id="4922f-116">Struktury rozhodování</span><span class="sxs-lookup"><span data-stu-id="4922f-116">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="4922f-117">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="4922f-117">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="4922f-118">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="4922f-118">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="4922f-119">Using – příkaz</span><span class="sxs-lookup"><span data-stu-id="4922f-119">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
- [<span data-ttu-id="4922f-120">With...End With – příkaz</span><span class="sxs-lookup"><span data-stu-id="4922f-120">With...End With Statement</span></span>](../../../language-reference/statements/with-end-with-statement.md)
