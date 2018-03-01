---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68a58fd130c04f2ed0cb1f2e5b9250f6c85f120d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="2b741-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b741-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="2b741-103">Určuje, že jeden nebo více deklarované členské proměnné odkazovat na instanci třídy, který může vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="2b741-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b741-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b741-104">Remarks</span></span>  
 <span data-ttu-id="2b741-105">Když je proměnná definovaná pomocí `WithEvents`, deklarativně můžete určit, že metoda zpracovává události proměnné pomocí `Handles` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="2b741-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="2b741-106">Můžete použít `WithEvents` jenom na úrovni třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="2b741-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="2b741-107">To znamená kontext deklarace `WithEvents` proměnná musí být třída nebo modul a nemůže být zdrojový soubor, obor názvů, struktura nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="2b741-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="2b741-108">Nemůžete použít `WithEvents` na struktura člena.</span><span class="sxs-lookup"><span data-stu-id="2b741-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="2b741-109">Lze deklarovat pouze jednotlivé proměnné – není maticových – s `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="2b741-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2b741-110">Pravidla</span><span class="sxs-lookup"><span data-stu-id="2b741-110">Rules</span></span>  
  
-   <span data-ttu-id="2b741-111">**Typy elementů.**</span><span class="sxs-lookup"><span data-stu-id="2b741-111">**Element Types.**</span></span> <span data-ttu-id="2b741-112">Je potřeba deklarovat `WithEvents` instancí třídy proměnné, které chcete být proměnné objektu tak, aby se může přijmout.</span><span class="sxs-lookup"><span data-stu-id="2b741-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="2b741-113">Však nelze deklarovat je jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="2b741-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="2b741-114">Je třeba deklarovat jako určité třídy, který může vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="2b741-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="2b741-115">`WithEvents` Modifikátor lze použít v tomto kontextu: [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="2b741-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b741-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b741-116">See Also</span></span>  
 [<span data-ttu-id="2b741-117">Obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="2b741-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="2b741-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2b741-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="2b741-119">Události</span><span class="sxs-lookup"><span data-stu-id="2b741-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
