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
ms.openlocfilehash: dcbabde8464dd8a0ce5fad24d7d72b1e780270d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392116"
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="e9113-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9113-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="e9113-103">Určuje, že vlastnost nebo procedura může být přepsána identicky pojmenovanou vlastností nebo procedurou v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="e9113-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9113-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9113-104">Remarks</span></span>  
 <span data-ttu-id="e9113-105">`Overridable`Modifikátor umožňuje přepsat vlastnost nebo metodu ve třídě v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="e9113-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="e9113-106">Modifikátor [NotOverridable](notoverridable.md) zabrání v přepsání vlastnosti nebo metody v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="e9113-106">The [NotOverridable](notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="e9113-107">Další informace najdete v tématu [základy dědičnosti](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="e9113-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="e9113-108">Pokud není `Overridable` `NotOverridable` zadán modifikátor nebo, výchozí nastavení závisí na tom, zda vlastnost nebo metoda přepisuje vlastnost nebo metodu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e9113-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="e9113-109">Pokud vlastnost nebo metoda přepíše vlastnost nebo metodu základní třídy, výchozí nastavení je `Overridable` . v opačném případě je `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="e9113-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="e9113-110">Můžete předefinovat zděděný element stínem nebo přepsáním, ale existují významné rozdíly mezi těmito dvěma přístupy.</span><span class="sxs-lookup"><span data-stu-id="e9113-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="e9113-111">Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="e9113-111">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="e9113-112">Element, který lze přepsat, je někdy označován jako *virtuální* prvek.</span><span class="sxs-lookup"><span data-stu-id="e9113-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="e9113-113">Pokud je možné ji přepsat, ale nemusí být, někdy se také označuje jako *konkrétní* prvek.</span><span class="sxs-lookup"><span data-stu-id="e9113-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="e9113-114">Můžete použít `Overridable` pouze v příkazu deklarace vlastnosti nebo procedury.</span><span class="sxs-lookup"><span data-stu-id="e9113-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="e9113-115">Kombinované modifikátory</span><span class="sxs-lookup"><span data-stu-id="e9113-115">Combined Modifiers</span></span>  
 <span data-ttu-id="e9113-116">Nemůžete zadat `Overridable` ani `NotOverridable` pro `Private` metodu.</span><span class="sxs-lookup"><span data-stu-id="e9113-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="e9113-117">Nelze zadat `Overridable` společně s `MustOverride` , `NotOverridable` nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="e9113-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="e9113-118">Vzhledem k tomu, že přepsání elementu je implicitně přepsatelné, nelze kombinovat `Overridable` s `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="e9113-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="e9113-119">Využití</span><span class="sxs-lookup"><span data-stu-id="e9113-119">Usage</span></span>  
 <span data-ttu-id="e9113-120">`Overridable`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="e9113-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="e9113-121">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="e9113-121">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="e9113-122">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="e9113-122">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="e9113-123">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="e9113-123">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e9113-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9113-124">See also</span></span>

- [<span data-ttu-id="e9113-125">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="e9113-125">Modifiers</span></span>](index.md)
- [<span data-ttu-id="e9113-126">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="e9113-126">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="e9113-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="e9113-127">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="e9113-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="e9113-128">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="e9113-129">Přepsání</span><span class="sxs-lookup"><span data-stu-id="e9113-129">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="e9113-130">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e9113-130">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="e9113-131">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e9113-131">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
