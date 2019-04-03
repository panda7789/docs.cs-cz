---
title: Overridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 91a1cedc66fd66e336b6e7976ad87ad638cb43c3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816875"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="56a03-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56a03-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="56a03-103">Určuje, že se vlastnost nebo procedura lze přepsat identicky pojmenovanou vlastnost nebo procedura v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="56a03-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56a03-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56a03-104">Remarks</span></span>  
 <span data-ttu-id="56a03-105">`Overridable` Modifikátor umožňuje vlastnosti nebo metody ve třídě k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="56a03-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="56a03-106">[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifikátor zabraňuje vlastnosti nebo metody přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="56a03-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="56a03-107">Další informace najdete v tématu [základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="56a03-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="56a03-108">Pokud `Overridable` nebo `NotOverridable` modifikátor není zadán, výchozí nastavení závisí na tom, zda vlastnosti nebo metody přepíše vlastnost základní třídy nebo metody.</span><span class="sxs-lookup"><span data-stu-id="56a03-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="56a03-109">Pokud vlastnost nebo metoda přepíše vlastnost základní třídy nebo metody, ve výchozím nastavení je `Overridable`; v opačném případě je `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="56a03-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="56a03-110">Můžete stínové nebo přepsání nastavení za účelem znovu definovat element zděděné, ale existují významné rozdíly mezi dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="56a03-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="56a03-111">Další informace najdete v tématu [stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="56a03-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="56a03-112">Element, který se dá přepsat se někdy označuje jako *virtuální* elementu.</span><span class="sxs-lookup"><span data-stu-id="56a03-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="56a03-113">Pokud se dá přepsat, ale nemusí být, někdy nazývá se také *konkrétní* elementu.</span><span class="sxs-lookup"><span data-stu-id="56a03-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="56a03-114">Můžete použít `Overridable` pouze v příkazu deklarace vlastnost nebo procedura.</span><span class="sxs-lookup"><span data-stu-id="56a03-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="56a03-115">Kombinované modifikátory</span><span class="sxs-lookup"><span data-stu-id="56a03-115">Combined Modifiers</span></span>  
 <span data-ttu-id="56a03-116">Nelze zadat `Overridable` nebo `NotOverridable` pro `Private` metoda.</span><span class="sxs-lookup"><span data-stu-id="56a03-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="56a03-117">Nelze zadat `Overridable` spolu s `MustOverride`, `NotOverridable`, nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="56a03-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="56a03-118">Vzhledem k tomu, že element přepsání přepsatelné, nelze kombinovat `Overridable` s `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="56a03-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="56a03-119">Použití</span><span class="sxs-lookup"><span data-stu-id="56a03-119">Usage</span></span>  
 <span data-ttu-id="56a03-120">`Overridable` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="56a03-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="56a03-121">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="56a03-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="56a03-122">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="56a03-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="56a03-123">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="56a03-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="56a03-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56a03-124">See also</span></span>

- [<span data-ttu-id="56a03-125">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="56a03-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="56a03-126">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="56a03-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="56a03-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="56a03-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="56a03-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="56a03-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="56a03-129">Overrides</span><span class="sxs-lookup"><span data-stu-id="56a03-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="56a03-130">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="56a03-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="56a03-131">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56a03-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
