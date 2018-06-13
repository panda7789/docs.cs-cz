---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 240058a534456ae20c9c129a068bae575ac45eda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596005"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="bc97a-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc97a-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="bc97a-103">Určuje, že jeden nebo více deklarované členské proměnné odkazovat na instanci třídy, který může vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="bc97a-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc97a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc97a-104">Remarks</span></span>  
 <span data-ttu-id="bc97a-105">Když je proměnná definovaná pomocí `WithEvents`, deklarativně můžete určit, že metoda zpracovává události proměnné pomocí `Handles` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="bc97a-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="bc97a-106">Můžete použít `WithEvents` jenom na úrovni třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="bc97a-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="bc97a-107">To znamená kontext deklarace `WithEvents` proměnná musí být třída nebo modul a nemůže být zdrojový soubor, obor názvů, struktura nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="bc97a-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="bc97a-108">Nemůžete použít `WithEvents` na struktura člena.</span><span class="sxs-lookup"><span data-stu-id="bc97a-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="bc97a-109">Lze deklarovat pouze jednotlivé proměnné – není maticových – s `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="bc97a-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="bc97a-110">Pravidla</span><span class="sxs-lookup"><span data-stu-id="bc97a-110">Rules</span></span>  
  
-   <span data-ttu-id="bc97a-111">**Typy elementů.**</span><span class="sxs-lookup"><span data-stu-id="bc97a-111">**Element Types.**</span></span> <span data-ttu-id="bc97a-112">Je potřeba deklarovat `WithEvents` instancí třídy proměnné, které chcete být proměnné objektu tak, aby se může přijmout.</span><span class="sxs-lookup"><span data-stu-id="bc97a-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="bc97a-113">Však nelze deklarovat je jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="bc97a-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="bc97a-114">Je třeba deklarovat jako určité třídy, který může vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="bc97a-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="bc97a-115">`WithEvents` Modifikátor lze použít v tomto kontextu: [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="bc97a-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc97a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc97a-116">See Also</span></span>  
 [<span data-ttu-id="bc97a-117">Obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="bc97a-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="bc97a-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="bc97a-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="bc97a-119">Události</span><span class="sxs-lookup"><span data-stu-id="bc97a-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
