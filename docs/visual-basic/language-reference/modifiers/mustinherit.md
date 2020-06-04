---
title: MustInherit
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
ms.openlocfilehash: 84df7a5cfdad3b5bc6764675725a5d0cb402b0b7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396204"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="2d997-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d997-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="2d997-103">Určuje, že třídu lze použít pouze jako základní třídu a že přímo z ní nelze vytvořit objekt.</span><span class="sxs-lookup"><span data-stu-id="2d997-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d997-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d997-104">Remarks</span></span>  
 <span data-ttu-id="2d997-105">Účelem *základní třídy* (označované také jako *abstraktní třída*) je definování funkcionality, která je společná pro všechny třídy odvozené od ní.</span><span class="sxs-lookup"><span data-stu-id="2d997-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="2d997-106">Tím se uloží odvozené třídy, abyste museli předefinovat společné prvky.</span><span class="sxs-lookup"><span data-stu-id="2d997-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="2d997-107">V některých případech není tato společná funkce dostatečně dokončena, aby provedla použitelný objekt a každá odvozená třída definuje chybějící funkce.</span><span class="sxs-lookup"><span data-stu-id="2d997-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="2d997-108">V takovém případě chcete, aby kód vytvářel objekty pouze z odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="2d997-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="2d997-109">Použijete `MustInherit` na základní třídě k vykonání této zásady.</span><span class="sxs-lookup"><span data-stu-id="2d997-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="2d997-110">Dalším použitím `MustInherit` třídy je omezit proměnnou na sadu souvisejících tříd.</span><span class="sxs-lookup"><span data-stu-id="2d997-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="2d997-111">Můžete definovat základní třídu a odvodit z ní všechny tyto související třídy.</span><span class="sxs-lookup"><span data-stu-id="2d997-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="2d997-112">Základní třída nemusí poskytovat žádné funkce společné pro všechny odvozené třídy, ale může sloužit jako filtr pro přiřazení hodnot proměnným.</span><span class="sxs-lookup"><span data-stu-id="2d997-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="2d997-113">Pokud váš nenáročný kód deklaruje proměnnou jako základní třídu, Visual Basic umožňuje přiřadit pouze objekt z jedné z odvozených tříd do této proměnné.</span><span class="sxs-lookup"><span data-stu-id="2d997-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="2d997-114">.NET Framework definuje několik `MustInherit` tříd, mezi nimi, <xref:System.Array> <xref:System.Enum> a <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="2d997-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="2d997-115"><xref:System.ValueType>je příklad základní třídy, která omezuje proměnnou.</span><span class="sxs-lookup"><span data-stu-id="2d997-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="2d997-116">Všechny typy hodnot jsou odvozeny z <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="2d997-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="2d997-117">Pokud deklarujete proměnnou jako <xref:System.ValueType> , můžete k této proměnné přiřadit pouze typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="2d997-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2d997-118">Pravidla</span><span class="sxs-lookup"><span data-stu-id="2d997-118">Rules</span></span>  
  
- <span data-ttu-id="2d997-119">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="2d997-119">**Declaration Context.**</span></span> <span data-ttu-id="2d997-120">Můžete použít `MustInherit` pouze v `Class` příkazu.</span><span class="sxs-lookup"><span data-stu-id="2d997-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
- <span data-ttu-id="2d997-121">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="2d997-121">**Combined Modifiers.**</span></span> <span data-ttu-id="2d997-122">Nelze zadat `MustInherit` společně s `NotInheritable` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="2d997-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d997-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d997-123">Example</span></span>  
 <span data-ttu-id="2d997-124">Následující příklad znázorňuje vynucenou dědičnost a vynucené přepsání.</span><span class="sxs-lookup"><span data-stu-id="2d997-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="2d997-125">Základní třída `shape` definuje proměnnou `acrossLine` .</span><span class="sxs-lookup"><span data-stu-id="2d997-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="2d997-126">Třídy `circle` a `square` odvozují z `shape` .</span><span class="sxs-lookup"><span data-stu-id="2d997-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="2d997-127">Dědí definici `acrossLine` , ale musí definovat funkci, `area` protože tento výpočet se liší pro každý druh obrazce.</span><span class="sxs-lookup"><span data-stu-id="2d997-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="2d997-128">Můžete deklarovat `shape1` a `shape2` být typu `shape` .</span><span class="sxs-lookup"><span data-stu-id="2d997-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="2d997-129">Nemůžete však vytvořit objekt z, `shape` protože nemá funkci `area` a je označen `MustInherit` .</span><span class="sxs-lookup"><span data-stu-id="2d997-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="2d997-130">Vzhledem k tomu, že jsou deklarovány jako `shape` , proměnné `shape1` a `shape2` jsou omezeny na objekty z odvozených tříd `circle` a `square` .</span><span class="sxs-lookup"><span data-stu-id="2d997-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="2d997-131">Visual Basic neumožňuje přiřadit žádné další objekty k těmto proměnným, což poskytuje vysokou úroveň bezpečnosti typů.</span><span class="sxs-lookup"><span data-stu-id="2d997-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="2d997-132">Využití</span><span class="sxs-lookup"><span data-stu-id="2d997-132">Usage</span></span>  
 <span data-ttu-id="2d997-133">`MustInherit`V tomto kontextu lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="2d997-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="2d997-134">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="2d997-134">Class Statement</span></span>](../statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2d997-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d997-135">See also</span></span>

- [<span data-ttu-id="2d997-136">Inherits – příkaz</span><span class="sxs-lookup"><span data-stu-id="2d997-136">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="2d997-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="2d997-137">NotInheritable</span></span>](notinheritable.md)
- [<span data-ttu-id="2d997-138">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2d997-138">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="2d997-139">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="2d997-139">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
