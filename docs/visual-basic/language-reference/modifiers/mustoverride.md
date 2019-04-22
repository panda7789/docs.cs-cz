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
ms.openlocfilehash: 0ddd7d0d2a57afc02aa7483ba5e83b65c48af534
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822814"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="46b0d-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46b0d-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="46b0d-103">Určuje, že se vlastnost nebo procedura není implementovaná v této třídě a předtím, než je možné, musí se přepsat v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="46b0d-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46b0d-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46b0d-104">Remarks</span></span>  
 <span data-ttu-id="46b0d-105">Můžete použít `MustOverride` pouze v příkazu deklarace vlastnost nebo procedura.</span><span class="sxs-lookup"><span data-stu-id="46b0d-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="46b0d-106">Vlastnost nebo proceduru, která určuje `MustOverride` musíte být členem třídy, a musí být třída označena [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="46b0d-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="46b0d-107">pravidla</span><span class="sxs-lookup"><span data-stu-id="46b0d-107">Rules</span></span>  
  
-   <span data-ttu-id="46b0d-108">**Neúplné deklarace.**</span><span class="sxs-lookup"><span data-stu-id="46b0d-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="46b0d-109">Pokud zadáte `MustOverride`, nezadáte nejsou žádné další řádky kódu pro vlastnost nebo procedura, dokonce i pomocí `End Function`, `End Property`, nebo `End Sub` příkazu.</span><span class="sxs-lookup"><span data-stu-id="46b0d-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="46b0d-110">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="46b0d-110">**Combined Modifiers.**</span></span> <span data-ttu-id="46b0d-111">Nelze zadat `MustOverride` spolu s `NotOverridable`, `Overridable`, nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="46b0d-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
-   <span data-ttu-id="46b0d-112">**Stínováním a přepsáním.**</span><span class="sxs-lookup"><span data-stu-id="46b0d-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="46b0d-113">Jak stínováním a přepsáním znovu definovat element zděděné, ale existují významné rozdíly mezi dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="46b0d-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="46b0d-114">Další informace najdete v tématu [stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="46b0d-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
-   <span data-ttu-id="46b0d-115">**Alternativní podmínky.**</span><span class="sxs-lookup"><span data-stu-id="46b0d-115">**Alternate Terms.**</span></span> <span data-ttu-id="46b0d-116">Někdy se označuje jako element, který nelze použít s výjimkou v přepsání *čistě virtuální* elementu.</span><span class="sxs-lookup"><span data-stu-id="46b0d-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="46b0d-117">`MustOverride` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="46b0d-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="46b0d-118">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="46b0d-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="46b0d-119">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="46b0d-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="46b0d-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="46b0d-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="46b0d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46b0d-121">See also</span></span>

- [<span data-ttu-id="46b0d-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="46b0d-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="46b0d-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="46b0d-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="46b0d-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="46b0d-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="46b0d-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="46b0d-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="46b0d-126">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="46b0d-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="46b0d-127">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="46b0d-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
