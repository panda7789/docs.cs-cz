---
title: MustOverride
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
ms.openlocfilehash: dc6a153a604fd0e5cee9d7d46ebcd63294f33628
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351481"
---
# <a name="mustoverride-visual-basic"></a><span data-ttu-id="38219-102">MustOverride (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38219-102">MustOverride (Visual Basic)</span></span>
<span data-ttu-id="38219-103">Určuje, že vlastnost nebo procedura není v této třídě implementována a musí být přepsána v odvozené třídě předtím, než je možné ji použít.</span><span class="sxs-lookup"><span data-stu-id="38219-103">Specifies that a property or procedure is not implemented in this class and must be overridden in a derived class before it can be used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38219-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38219-104">Remarks</span></span>  
 <span data-ttu-id="38219-105">`MustOverride` lze použít pouze v příkazu deklarace vlastnosti nebo procedury.</span><span class="sxs-lookup"><span data-stu-id="38219-105">You can use `MustOverride` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="38219-106">Vlastnost nebo procedura určující `MustOverride` musí být členem třídy a třída musí být označena jako [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span><span class="sxs-lookup"><span data-stu-id="38219-106">The property or procedure that specifies `MustOverride` must be a member of a class, and the class must be marked [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="38219-107">Pravidla</span><span class="sxs-lookup"><span data-stu-id="38219-107">Rules</span></span>  
  
- <span data-ttu-id="38219-108">**Neúplná deklarace**</span><span class="sxs-lookup"><span data-stu-id="38219-108">**Incomplete Declaration.**</span></span> <span data-ttu-id="38219-109">Pokud zadáte `MustOverride`, neposkytnete žádné další řádky kódu pro vlastnost nebo proceduru, ani příkaz `End Function`, `End Property`nebo `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="38219-109">When you specify `MustOverride`, you do not supply any additional lines of code for the property or procedure, not even the `End Function`, `End Property`, or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="38219-110">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="38219-110">**Combined Modifiers.**</span></span> <span data-ttu-id="38219-111">V rámci stejné deklarace nelze zadat `MustOverride` společně s `NotOverridable`, `Overridable`nebo `Shared`.</span><span class="sxs-lookup"><span data-stu-id="38219-111">You cannot specify `MustOverride` together with `NotOverridable`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
- <span data-ttu-id="38219-112">**Nastínování a přepisování.**</span><span class="sxs-lookup"><span data-stu-id="38219-112">**Shadowing and Overriding.**</span></span> <span data-ttu-id="38219-113">Jak Stínová, tak i přepsání předefinují zděděný element, ale existují významné rozdíly mezi těmito dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="38219-113">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="38219-114">Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="38219-114">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
- <span data-ttu-id="38219-115">**Alternativní výrazy.**</span><span class="sxs-lookup"><span data-stu-id="38219-115">**Alternate Terms.**</span></span> <span data-ttu-id="38219-116">Element, který nelze použít s výjimkou v přepsání, se někdy označuje jako *čistě virtuální* prvek.</span><span class="sxs-lookup"><span data-stu-id="38219-116">An element that cannot be used except in an override is sometimes called a *pure virtual* element.</span></span>  
  
 <span data-ttu-id="38219-117">V těchto kontextech lze použít modifikátor `MustOverride`:</span><span class="sxs-lookup"><span data-stu-id="38219-117">The `MustOverride` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="38219-118">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="38219-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="38219-119">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="38219-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="38219-120">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="38219-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="38219-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38219-121">See also</span></span>

- [<span data-ttu-id="38219-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="38219-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="38219-123">Overridable</span><span class="sxs-lookup"><span data-stu-id="38219-123">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="38219-124">Overrides</span><span class="sxs-lookup"><span data-stu-id="38219-124">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="38219-125">MustInherit</span><span class="sxs-lookup"><span data-stu-id="38219-125">MustInherit</span></span>](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [<span data-ttu-id="38219-126">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="38219-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="38219-127">Stínování v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38219-127">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
