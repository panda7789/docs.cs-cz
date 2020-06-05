---
title: NotOverridable
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: 463dd2454aafebf11554fb7bacdb73724c3130d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392155"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="ccbdf-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ccbdf-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="ccbdf-103">Určuje, že vlastnost nebo procedura nemůže být přepsána v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="ccbdf-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccbdf-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccbdf-104">Remarks</span></span>  
 <span data-ttu-id="ccbdf-105">`NotOverridable`Modifikátor zabraňuje přepsání vlastnosti nebo metody v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="ccbdf-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="ccbdf-106">Modifikátor [overridable](overridable.md) umožňuje přepsat vlastnost nebo metodu ve třídě v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="ccbdf-106">The [Overridable](overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="ccbdf-107">Další informace najdete v tématu [základy dědičnosti](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="ccbdf-107">For more information, see [Inheritance Basics](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="ccbdf-108">Pokud není `Overridable` `NotOverridable` zadán modifikátor nebo, výchozí nastavení závisí na tom, zda vlastnost nebo metoda přepisuje vlastnost nebo metodu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ccbdf-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="ccbdf-109">Pokud vlastnost nebo metoda přepíše vlastnost nebo metodu základní třídy, výchozí nastavení je `Overridable` . v opačném případě je `NotOverridable` .</span><span class="sxs-lookup"><span data-stu-id="ccbdf-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="ccbdf-110">Element, který nelze přepsat, se někdy označuje jako *zapečetěný* element.</span><span class="sxs-lookup"><span data-stu-id="ccbdf-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="ccbdf-111">Můžete použít `NotOverridable` pouze v příkazu deklarace vlastnosti nebo procedury.</span><span class="sxs-lookup"><span data-stu-id="ccbdf-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="ccbdf-112">Můžete zadat `NotOverridable` pouze vlastnost nebo proceduru, která přepisuje jinou vlastnost nebo proceduru, tedy pouze v kombinaci s `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="ccbdf-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="ccbdf-113">Kombinované modifikátory</span><span class="sxs-lookup"><span data-stu-id="ccbdf-113">Combined Modifiers</span></span>  
 <span data-ttu-id="ccbdf-114">Nemůžete zadat `Overridable` ani `NotOverridable` pro `Private` metodu.</span><span class="sxs-lookup"><span data-stu-id="ccbdf-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="ccbdf-115">Nelze zadat `NotOverridable` společně s `MustOverride` , `Overridable` nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="ccbdf-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="ccbdf-116">Využití</span><span class="sxs-lookup"><span data-stu-id="ccbdf-116">Usage</span></span>  
 <span data-ttu-id="ccbdf-117">`NotOverridable`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="ccbdf-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="ccbdf-118">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="ccbdf-118">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="ccbdf-119">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="ccbdf-119">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="ccbdf-120">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="ccbdf-120">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="ccbdf-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccbdf-121">See also</span></span>

- [<span data-ttu-id="ccbdf-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="ccbdf-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="ccbdf-123">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="ccbdf-123">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="ccbdf-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="ccbdf-124">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="ccbdf-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="ccbdf-125">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="ccbdf-126">Přepsání</span><span class="sxs-lookup"><span data-stu-id="ccbdf-126">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="ccbdf-127">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ccbdf-127">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="ccbdf-128">Stínění v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ccbdf-128">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
