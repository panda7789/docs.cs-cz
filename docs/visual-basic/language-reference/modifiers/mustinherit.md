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
ms.openlocfilehash: 5d622c1cff77a45c8de7772af7efbb73586f4400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602837"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="6fdd2-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fdd2-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="6fdd2-103">Určuje, že třídu lze použít pouze jako základní třída a že nelze vytvořit objekt přímo z něj.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fdd2-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fdd2-104">Remarks</span></span>  
 <span data-ttu-id="6fdd2-105">Účel *základní třída* (také označované jako *abstraktní třída*) je určit funkce, které jsou společné pro všechny třídy z něj odvozenou.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="6fdd2-106">To umožňuje ušetřit odvozené třídy z museli znovu definovat běžných elementech.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="6fdd2-107">V některých případech tato běžné funkce není dostatečně dokončení, aby objekt použitelné a každý odvozené třídy definuje chybějící funkce.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="6fdd2-108">V takovém případě budete chtít kód náročné vytvořit objekty pouze z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="6fdd2-109">Používáte `MustInherit` na základní třídy, chcete-li vynutit.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="6fdd2-110">Další používání `MustInherit` třída je omezit proměnné na sadu související třídy.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="6fdd2-111">Můžete definovat základní třídy a všechny související třídy odvozena z něj.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="6fdd2-112">Není nutné poskytovat žádné funkce, které jsou společné pro všechny odvozené třídy základní třídy, ale může sloužit jako filtr pro přiřazení hodnoty k proměnné.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="6fdd2-113">Pokud náročné kód deklaruje proměnnou jako základní třída, Visual Basic umožňuje přiřadit pouze objekt z jednoho z odvozené třídy k této proměnné.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="6fdd2-114">Rozhraní .NET Framework definuje několik `MustInherit` třídy mezi nimi <xref:System.Array>, <xref:System.Enum>, a <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="6fdd2-115"><xref:System.ValueType> je příklad základní třídu, která omezuje proměnné.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="6fdd2-116">Všechny typy hodnot odvozena od <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="6fdd2-117">Pokud je deklarovat proměnnou jako <xref:System.ValueType>, tuto proměnnou můžete přiřadit pouze typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6fdd2-118">Pravidla</span><span class="sxs-lookup"><span data-stu-id="6fdd2-118">Rules</span></span>  
  
-   <span data-ttu-id="6fdd2-119">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="6fdd2-119">**Declaration Context.**</span></span> <span data-ttu-id="6fdd2-120">Můžete použít `MustInherit` pouze v `Class` příkaz.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
-   <span data-ttu-id="6fdd2-121">**Kombinovaná parametrů.**</span><span class="sxs-lookup"><span data-stu-id="6fdd2-121">**Combined Modifiers.**</span></span> <span data-ttu-id="6fdd2-122">Nelze zadat `MustInherit` společně s `NotInheritable` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fdd2-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="6fdd2-123">Example</span></span>  
 <span data-ttu-id="6fdd2-124">Následující příklad ilustruje vynucené dědičnosti a Vynucené přepsání.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="6fdd2-125">Základní třída `shape` definuje proměnnou `acrossLine`.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="6fdd2-126">Třídy `circle` a `square` odvozena od `shape`.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="6fdd2-127">Dědí definice `acrossLine`, ale jejich musí definovat funkce `area` vzhledem k tomu, že výpočet se liší pro jednotlivé typy tvaru.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 <span data-ttu-id="6fdd2-128">Je možné deklarovat `shape1` a `shape2` být typu `shape`.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="6fdd2-129">Však nelze vytvořit objekt z `shape` protože postrádá funkci funkce `area` a je označen jako `MustInherit`.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="6fdd2-130">Protože jsou deklarovány jako `shape`, proměnné `shape1` a `shape2` jsou omezené na objekty z odvozené třídy `circle` a `square`.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="6fdd2-131">Visual Basic neumožňuje jakýkoliv jiný objekt přiřadit tyto proměnné, která poskytuje vysokou úroveň zabezpečení typů.</span><span class="sxs-lookup"><span data-stu-id="6fdd2-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="6fdd2-132">Použití</span><span class="sxs-lookup"><span data-stu-id="6fdd2-132">Usage</span></span>  
 <span data-ttu-id="6fdd2-133">`MustInherit` Modifikátor můžete v tomto kontextu použít:</span><span class="sxs-lookup"><span data-stu-id="6fdd2-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="6fdd2-134">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="6fdd2-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6fdd2-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fdd2-135">See Also</span></span>  
 [<span data-ttu-id="6fdd2-136">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="6fdd2-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="6fdd2-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="6fdd2-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="6fdd2-138">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6fdd2-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="6fdd2-139">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="6fdd2-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
