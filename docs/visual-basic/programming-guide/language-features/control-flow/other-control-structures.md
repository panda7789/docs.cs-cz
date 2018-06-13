---
title: Ostatní řídicí struktury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
ms.openlocfilehash: 272ebcf0639b83a51e87de5ebbf93d7e750c03a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654106"
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="5b2ac-102">Ostatní řídicí struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b2ac-102">Other Control Structures (Visual Basic)</span></span>
<span data-ttu-id="5b2ac-103">Visual Basic poskytuje řídicí struktury, které vám pomůžou odstranění prostředku nebo snižte počet, kolikrát je nutné zopakovat odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="5b2ac-103">Visual Basic provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="5b2ac-104">Pomocí... Ukončení pomocí konstrukce</span><span class="sxs-lookup"><span data-stu-id="5b2ac-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="5b2ac-105">`Using...End Using` Konstrukce vytvoří blok příkaz, ve kterém provedete využití prostředků, jako je připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="5b2ac-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="5b2ac-106">Volitelně můžete získat prostředek s `Using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="5b2ac-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="5b2ac-107">Po ukončení `Using` bloku jazyka Visual Basic automaticky uvolní prostředku, aby bylo k dispozici pro ostatní kódu pro použití.</span><span class="sxs-lookup"><span data-stu-id="5b2ac-107">When you exit the `Using` block, Visual Basic automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="5b2ac-108">Prostředek musí být místní a na jedno použití.</span><span class="sxs-lookup"><span data-stu-id="5b2ac-108">The resource must be local and disposable.</span></span> <span data-ttu-id="5b2ac-109">Další informace najdete v tématu [pomocí příkazu](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5b2ac-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="5b2ac-110">S... Končit konstrukce</span><span class="sxs-lookup"><span data-stu-id="5b2ac-110">With...End With Construction</span></span>  
 <span data-ttu-id="5b2ac-111">`With...End With` Konstrukce umožňuje zadat odkaz na objekt jednou a poté spusťte řadu příkazů, které přístup k její členy.</span><span class="sxs-lookup"><span data-stu-id="5b2ac-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="5b2ac-112">To můžete zjednodušit kód a zlepšit výkon, protože není nutné znovu vytvořit referenční informace pro každý příkaz, který přistupuje k jeho jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5b2ac-112">This can simplify your code and improve performance because Visual Basic does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="5b2ac-113">Další informace najdete v tématu [s... End With – příkaz](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5b2ac-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b2ac-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b2ac-114">See Also</span></span>  
 [<span data-ttu-id="5b2ac-115">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="5b2ac-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="5b2ac-116">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="5b2ac-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="5b2ac-117">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="5b2ac-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="5b2ac-118">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="5b2ac-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="5b2ac-119">Příkaz Using</span><span class="sxs-lookup"><span data-stu-id="5b2ac-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [<span data-ttu-id="5b2ac-120">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="5b2ac-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
