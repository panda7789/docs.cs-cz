---
title: Overridable
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
ms.openlocfilehash: 9c639665fd92a56de6fb6e5147cda873ef457b45
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351390"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="43b65-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43b65-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="43b65-103">Určuje, že vlastnost nebo procedura může být přepsána identicky pojmenovanou vlastností nebo procedurou v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="43b65-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43b65-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43b65-104">Remarks</span></span>  
 <span data-ttu-id="43b65-105">Modifikátor `Overridable` umožňuje přepsání vlastnosti nebo metody ve třídě v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="43b65-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="43b65-106">Modifikátor [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) zabrání v přepsání vlastnosti nebo metody v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="43b65-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="43b65-107">Další informace najdete v tématu [základy dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="43b65-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="43b65-108">Pokud není zadán modifikátor `Overridable` nebo `NotOverridable`, bude výchozí nastavení záviset na tom, zda vlastnost nebo metoda přepisuje vlastnost nebo metodu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="43b65-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="43b65-109">Pokud vlastnost nebo metoda přepíše vlastnost nebo metodu základní třídy, výchozí nastavení je `Overridable`; v opačném případě je `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="43b65-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="43b65-110">Můžete předefinovat zděděný element stínem nebo přepsáním, ale existují významné rozdíly mezi těmito dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="43b65-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="43b65-111">Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="43b65-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="43b65-112">Element, který lze přepsat, je někdy označován jako *virtuální* prvek.</span><span class="sxs-lookup"><span data-stu-id="43b65-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="43b65-113">Pokud je možné ji přepsat, ale nemusí být, někdy se také označuje jako *konkrétní* prvek.</span><span class="sxs-lookup"><span data-stu-id="43b65-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="43b65-114">`Overridable` lze použít pouze v příkazu deklarace vlastnosti nebo procedury.</span><span class="sxs-lookup"><span data-stu-id="43b65-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="43b65-115">Kombinované modifikátory</span><span class="sxs-lookup"><span data-stu-id="43b65-115">Combined Modifiers</span></span>  
 <span data-ttu-id="43b65-116">Pro metodu `Private` nelze zadat `Overridable` ani `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="43b65-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="43b65-117">V rámci stejné deklarace nelze zadat `Overridable` společně s `MustOverride`, `NotOverridable`nebo `Shared`.</span><span class="sxs-lookup"><span data-stu-id="43b65-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="43b65-118">Vzhledem k tomu, že přepsání elementu je implicitně přepsatelné, nelze kombinovat `Overridable` s `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="43b65-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="43b65-119">Využití</span><span class="sxs-lookup"><span data-stu-id="43b65-119">Usage</span></span>  
 <span data-ttu-id="43b65-120">V těchto kontextech lze použít modifikátor `Overridable`:</span><span class="sxs-lookup"><span data-stu-id="43b65-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="43b65-121">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="43b65-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="43b65-122">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="43b65-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="43b65-123">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="43b65-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="43b65-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43b65-124">See also</span></span>

- [<span data-ttu-id="43b65-125">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="43b65-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="43b65-126">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="43b65-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="43b65-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="43b65-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="43b65-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="43b65-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [<span data-ttu-id="43b65-129">Overrides</span><span class="sxs-lookup"><span data-stu-id="43b65-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="43b65-130">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="43b65-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="43b65-131">Stínování v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="43b65-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
