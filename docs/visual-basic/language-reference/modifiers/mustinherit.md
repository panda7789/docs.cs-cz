---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 7a246e2565ec6d96e828654fef74500c4cf896b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627665"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="f2d54-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f2d54-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="f2d54-103">Určuje, že třídu lze použít pouze jako základní třídu a objekt nelze vytvořit přímo z ní.</span><span class="sxs-lookup"><span data-stu-id="f2d54-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2d54-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2d54-104">Remarks</span></span>  
 <span data-ttu-id="f2d54-105">Účel *základní třída* (označované také jako *abstraktní třídu*) je definování funkcí, které jsou společné pro všechny třídy odvozené z něj.</span><span class="sxs-lookup"><span data-stu-id="f2d54-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="f2d54-106">To museli znovu definovat společné prvky uloží odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="f2d54-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="f2d54-107">V některých případech tato běžné funkce není dostatečně kompletní, chcete-li použít objekt a Každá odvozená třída definuje chybějící funkce.</span><span class="sxs-lookup"><span data-stu-id="f2d54-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="f2d54-108">V takovém případě má časově náročný kód k vytvoření objektů pouze z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="f2d54-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="f2d54-109">Použijete `MustInherit` na základní třídu, pokud to chcete vynutit.</span><span class="sxs-lookup"><span data-stu-id="f2d54-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="f2d54-110">Další používání `MustInherit` třída je omezit proměnnou na sadu souvisejících tříd.</span><span class="sxs-lookup"><span data-stu-id="f2d54-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="f2d54-111">Můžete definovat základní třídy a z něj odvodit všechny související třídy.</span><span class="sxs-lookup"><span data-stu-id="f2d54-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="f2d54-112">Není potřeba poskytují všechny funkce, které jsou společné pro všechny odvozené třídy základní třídy, ale může sloužit jako filtr pro přiřazení hodnoty proměnné.</span><span class="sxs-lookup"><span data-stu-id="f2d54-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="f2d54-113">Pokud váš náročný kód deklaruje proměnnou jako základní třída, Visual Basic umožňuje přiřadit pouze objekt z jedné z odvozených tříd na tuto proměnnou.</span><span class="sxs-lookup"><span data-stu-id="f2d54-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="f2d54-114">Rozhraní .NET Framework definuje několik `MustInherit` tříd, mezi nimi <xref:System.Array>, <xref:System.Enum>, a <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="f2d54-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="f2d54-115"><xref:System.ValueType> je příklad základní třídu, která omezuje proměnné.</span><span class="sxs-lookup"><span data-stu-id="f2d54-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="f2d54-116">Všechny typy hodnot jsou odvozeny z <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="f2d54-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="f2d54-117">Pokud deklarujete proměnnou jako <xref:System.ValueType>, k této proměnné můžete přiřadit jenom typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="f2d54-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f2d54-118">pravidla</span><span class="sxs-lookup"><span data-stu-id="f2d54-118">Rules</span></span>  
  
-   <span data-ttu-id="f2d54-119">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="f2d54-119">**Declaration Context.**</span></span> <span data-ttu-id="f2d54-120">Můžete použít `MustInherit` pouze v `Class` příkazu.</span><span class="sxs-lookup"><span data-stu-id="f2d54-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
-   <span data-ttu-id="f2d54-121">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="f2d54-121">**Combined Modifiers.**</span></span> <span data-ttu-id="f2d54-122">Nelze zadat `MustInherit` spolu s `NotInheritable` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="f2d54-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2d54-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2d54-123">Example</span></span>  
 <span data-ttu-id="f2d54-124">Následující příklad ukazuje vynucené dědičnosti a Vynucené přepsání.</span><span class="sxs-lookup"><span data-stu-id="f2d54-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="f2d54-125">Základní třída `shape` definuje proměnnou `acrossLine`.</span><span class="sxs-lookup"><span data-stu-id="f2d54-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="f2d54-126">Třídy `circle` a `square` odvozovat `shape`.</span><span class="sxs-lookup"><span data-stu-id="f2d54-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="f2d54-127">Dědí definici `acrossLine`, ale jejich musí definovat funkci `area` protože výpočtu se liší pro každý druh tvaru.</span><span class="sxs-lookup"><span data-stu-id="f2d54-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 <span data-ttu-id="f2d54-128">Je možné deklarovat `shape1` a `shape2` typu `shape`.</span><span class="sxs-lookup"><span data-stu-id="f2d54-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="f2d54-129">Však nelze vytvořit objekt `shape` protože postrádá funkčnost funkce `area` a je označen `MustInherit`.</span><span class="sxs-lookup"><span data-stu-id="f2d54-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="f2d54-130">Protože jsou deklarovány jako `shape`, proměnné `shape1` a `shape2` je omezena na objekty z odvozených tříd `circle` a `square`.</span><span class="sxs-lookup"><span data-stu-id="f2d54-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="f2d54-131">Visual Basic neumožňuje jakýkoli jiný objekt přiřadit tyto proměnné, která poskytuje vysoký stupeň bezpečnost typů.</span><span class="sxs-lookup"><span data-stu-id="f2d54-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="f2d54-132">Použití</span><span class="sxs-lookup"><span data-stu-id="f2d54-132">Usage</span></span>  
 <span data-ttu-id="f2d54-133">`MustInherit` Modifikátor lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="f2d54-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="f2d54-134">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="f2d54-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f2d54-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2d54-135">See also</span></span>
- [<span data-ttu-id="f2d54-136">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="f2d54-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="f2d54-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="f2d54-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="f2d54-138">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f2d54-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="f2d54-139">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="f2d54-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
