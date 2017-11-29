---
title: "Ostatní řídicí struktury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09e59d25b3b2fc89026295e8500c30dad7b75086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="6e9f2-102">Ostatní řídicí struktury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e9f2-102">Other Control Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="6e9f2-103">poskytuje řídicí struktury, které vám pomůžou odstranění prostředku nebo snižte počet, kolikrát je nutné zopakovat odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="6e9f2-103"> provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="6e9f2-104">Pomocí... Ukončení pomocí konstrukce</span><span class="sxs-lookup"><span data-stu-id="6e9f2-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="6e9f2-105">`Using...End Using` Konstrukce vytvoří blok příkaz, ve kterém provedete využití prostředků, jako je připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="6e9f2-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="6e9f2-106">Volitelně můžete získat prostředek s `Using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6e9f2-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="6e9f2-107">Po ukončení `Using` bloku [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automaticky uvolní prostředku, aby byla dostupná pro ostatní kódu pro použití.</span><span class="sxs-lookup"><span data-stu-id="6e9f2-107">When you exit the `Using` block, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="6e9f2-108">Prostředek musí být místní a na jedno použití.</span><span class="sxs-lookup"><span data-stu-id="6e9f2-108">The resource must be local and disposable.</span></span> <span data-ttu-id="6e9f2-109">Další informace najdete v tématu [pomocí příkazu](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6e9f2-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="6e9f2-110">S... Končit konstrukce</span><span class="sxs-lookup"><span data-stu-id="6e9f2-110">With...End With Construction</span></span>  
 <span data-ttu-id="6e9f2-111">`With...End With` Konstrukce umožňuje zadat odkaz na objekt jednou a poté spusťte řadu příkazů, které přístup k její členy.</span><span class="sxs-lookup"><span data-stu-id="6e9f2-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="6e9f2-112">To můžete zjednodušit kód a zlepšit výkon, protože [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] není nutné znovu vytvořit referenční informace pro každý příkaz, který přistupuje k ho.</span><span class="sxs-lookup"><span data-stu-id="6e9f2-112">This can simplify your code and improve performance because [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="6e9f2-113">Další informace najdete v tématu [s... End With – příkaz](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6e9f2-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e9f2-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e9f2-114">See Also</span></span>  
 [<span data-ttu-id="6e9f2-115">Tok řízení</span><span class="sxs-lookup"><span data-stu-id="6e9f2-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="6e9f2-116">Rozhodovací struktury</span><span class="sxs-lookup"><span data-stu-id="6e9f2-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="6e9f2-117">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="6e9f2-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="6e9f2-118">Vnořené řídicí struktury</span><span class="sxs-lookup"><span data-stu-id="6e9f2-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="6e9f2-119">Using – příkaz</span><span class="sxs-lookup"><span data-stu-id="6e9f2-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [<span data-ttu-id="6e9f2-120">S... End With – příkaz</span><span class="sxs-lookup"><span data-stu-id="6e9f2-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
