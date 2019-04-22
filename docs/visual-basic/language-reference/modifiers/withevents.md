---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 75d118ee2bd4918c3a936cb341864ddc5315726b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826610"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="b3bd8-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3bd8-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="b3bd8-103">Určuje, že nejméně jedna deklarovaná členská proměnná odkazuje na instanci třídy, která může vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="b3bd8-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3bd8-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3bd8-104">Remarks</span></span>  
 <span data-ttu-id="b3bd8-105">Pokud je proměnná definována pomocí `WithEvents`, pomocí deklarace můžete určit, že metoda zpracovává události proměnné pomocí `Handles` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b3bd8-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="b3bd8-106">Můžete použít `WithEvents` pouze na úrovni třídy nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="b3bd8-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="b3bd8-107">To znamená, že deklarace kontext `WithEvents` proměnná musí být třídu nebo modul a nemůže být zdrojový soubor, obor názvů, struktury nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="b3bd8-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="b3bd8-108">Nemůžete použít `WithEvents` na člena struktury.</span><span class="sxs-lookup"><span data-stu-id="b3bd8-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="b3bd8-109">Můžete deklarovat pouze proměnné, jednotlivým – není pole – s `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="b3bd8-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b3bd8-110">pravidla</span><span class="sxs-lookup"><span data-stu-id="b3bd8-110">Rules</span></span>  
  
-   <span data-ttu-id="b3bd8-111">**Typy elementů.**</span><span class="sxs-lookup"><span data-stu-id="b3bd8-111">**Element Types.**</span></span> <span data-ttu-id="b3bd8-112">Je třeba deklarovat `WithEvents` proměnné na proměnné objektu tak, aby může přijmout třídu instance.</span><span class="sxs-lookup"><span data-stu-id="b3bd8-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="b3bd8-113">Však nelze deklarovat jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="b3bd8-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="b3bd8-114">Je třeba je deklarovat jako konkrétní třídy, která může vyvolat události.</span><span class="sxs-lookup"><span data-stu-id="b3bd8-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="b3bd8-115">`WithEvents` Modifikátor lze použít v tomto kontextu: [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="b3bd8-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3bd8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3bd8-116">See also</span></span>

- [<span data-ttu-id="b3bd8-117">Obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="b3bd8-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="b3bd8-118">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b3bd8-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="b3bd8-119">Události</span><span class="sxs-lookup"><span data-stu-id="b3bd8-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
