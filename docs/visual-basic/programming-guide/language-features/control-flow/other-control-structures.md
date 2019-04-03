---
title: Ostatní řídicí struktury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: c42070ce2ea866e59e1b2e190f7c05e1ee7cc922
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819317"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="9b165-102">Ostatní řídicí struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b165-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="9b165-103">Visual Basic poskytuje řídicí struktury, které vám pomůžou odstranění prostředku nebo snižte počet, kolikrát je potřeba ji opakovat odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="9b165-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="9b165-104">Použití... End s využitím konstrukce</span><span class="sxs-lookup"><span data-stu-id="9b165-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="9b165-105">`Using...End Using` Konstrukce zavádí blok příkazů, ve kterém provedete využívání prostředků, jako je například připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="9b165-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="9b165-106">Volitelně můžete získat prostředek s `Using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9b165-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="9b165-107">Po ukončení `Using` bloku, Visual Basic automaticky objekt odstraní prostředek tak, aby se pro další kód, který použijete k dispozici.</span><span class="sxs-lookup"><span data-stu-id="9b165-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="9b165-108">Prostředek musí být místní a na jedno použití.</span><span class="sxs-lookup"><span data-stu-id="9b165-108">The resource must be local and disposable.</span></span> <span data-ttu-id="9b165-109">Další informace najdete v tématu [příkazu Using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9b165-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="9b165-110">S... Končit konstrukce</span><span class="sxs-lookup"><span data-stu-id="9b165-110">With...End With Construction</span></span>  
 <span data-ttu-id="9b165-111">`With...End With` Konstrukce umožňuje zadat odkaz na objekt jednou a potom spustit sérii příkazů, které přistupovat k jejím členům.</span><span class="sxs-lookup"><span data-stu-id="9b165-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="9b165-112">To můžete zjednodušit kód a zlepšit výkon, protože není potřeba znovu vytvořit referenční informace pro každý příkaz, který přistupuje k jeho jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9b165-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="9b165-113">Další informace najdete v tématu [s... End With – příkaz](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9b165-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b165-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b165-114">See also</span></span>

- [<span data-ttu-id="9b165-115">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="9b165-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="9b165-116">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="9b165-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="9b165-117">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="9b165-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="9b165-118">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="9b165-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="9b165-119">Příkaz Using</span><span class="sxs-lookup"><span data-stu-id="9b165-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
- [<span data-ttu-id="9b165-120">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="9b165-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
