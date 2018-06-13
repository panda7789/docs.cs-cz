---
title: MustOverride (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: 5dabd90d29bc41d017436876af24a67fa87e8e17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599867"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="1ad1f-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ad1f-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="1ad1f-103">Určuje, že vlastnost nebo postup není implementována v této třídě a musí být přepsána nastaveními v odvozené třídě před použitím.</span><span class="sxs-lookup"><span data-stu-id="1ad1f-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ad1f-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ad1f-104">Remarks</span></span>  
 <span data-ttu-id="1ad1f-105">Můžete použít `MustOverride` jenom v příkazu deklarace vlastnosti nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="1ad1f-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="1ad1f-106">Vlastnost nebo procedury, která určuje `MustOverride` musí být členem třídy, a musí být označen třída [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="1ad1f-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1ad1f-107">Pravidla</span><span class="sxs-lookup"><span data-stu-id="1ad1f-107">Rules</span></span>  
  
-   <span data-ttu-id="1ad1f-108">**Nedokončené deklarace.**</span><span class="sxs-lookup"><span data-stu-id="1ad1f-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="1ad1f-109">Pokud zadáte `MustOverride`, nezadáte není žádné další řádky kódu pro vlastnost nebo postupu, i na `End Function`, `End Property`, nebo `End Sub` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1ad1f-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="1ad1f-110">**Kombinovaná parametrů.**</span><span class="sxs-lookup"><span data-stu-id="1ad1f-110">**Combined Modifiers.**</span></span> <span data-ttu-id="1ad1f-111">Nelze zadat `MustOverride` společně s `NotOverridable`, `Overridable`, nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="1ad1f-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
-   <span data-ttu-id="1ad1f-112">**Stínováním a přepsáním.**</span><span class="sxs-lookup"><span data-stu-id="1ad1f-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="1ad1f-113">Jak stínováním a přepsáním znovu definovat zděděné elementu, ale existují významné rozdíly mezi dva přístupy.</span><span class="sxs-lookup"><span data-stu-id="1ad1f-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="1ad1f-114">Další informace najdete v tématu [stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="1ad1f-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
-   <span data-ttu-id="1ad1f-115">**Alternativní podmínky.**</span><span class="sxs-lookup"><span data-stu-id="1ad1f-115">**Alternate Terms.**</span></span> <span data-ttu-id="1ad1f-116">Element, který nelze použít s výjimkou v přepsání se někdy nazývá *čistý virtuální* elementu.</span><span class="sxs-lookup"><span data-stu-id="1ad1f-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="1ad1f-117">`MustOverride` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="1ad1f-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="1ad1f-118">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="1ad1f-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="1ad1f-119">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="1ad1f-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="1ad1f-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="1ad1f-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1ad1f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ad1f-121">See Also</span></span>  
 [<span data-ttu-id="1ad1f-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="1ad1f-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="1ad1f-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="1ad1f-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="1ad1f-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="1ad1f-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="1ad1f-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="1ad1f-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [<span data-ttu-id="1ad1f-126">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1ad1f-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="1ad1f-127">Stínový provoz v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ad1f-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
