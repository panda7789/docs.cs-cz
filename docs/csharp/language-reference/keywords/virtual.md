---
title: virtuální - C# Reference
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 883e0a7f833c15d2c1cce6b3d52d16aad01a5cd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173455"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="22f59-102">virtual (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="22f59-102">virtual (C# Reference)</span></span>

<span data-ttu-id="22f59-103">Klíčové `virtual` slovo se používá k úpravě metody, vlastnosti, indexeru nebo deklarace události a umožňuje, aby byla přepsána v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="22f59-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="22f59-104">Například tato metoda může být přepsána libovolnou třídou, která ji dědí:</span><span class="sxs-lookup"><span data-stu-id="22f59-104">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area()
{
    return x * y;
}
```

<span data-ttu-id="22f59-105">Implementace virtuálního člena může být změněna [přepsáním člena](override.md) v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="22f59-105">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="22f59-106">Další informace o použití `virtual` klíčového slova naleznete v [tématu Správa verzí s přepsáním a novými klíčovými slovy](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [Informace o tom, kdy použít přepsání a Nová klíčová slova](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="22f59-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="22f59-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22f59-107">Remarks</span></span>

<span data-ttu-id="22f59-108">Při vyvolání virtuální metody je typ za běhu objektu zkontrolován pro přepsání člena.</span><span class="sxs-lookup"><span data-stu-id="22f59-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="22f59-109">Je volán přepsání členu v nejvíce odvozené třídě, což může být původní člen, pokud žádná odvozená třída nepřepsala člen.</span><span class="sxs-lookup"><span data-stu-id="22f59-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="22f59-110">Ve výchozím nastavení jsou metody nevirtuální.</span><span class="sxs-lookup"><span data-stu-id="22f59-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="22f59-111">Nelze přepsat nevirtuální metodu.</span><span class="sxs-lookup"><span data-stu-id="22f59-111">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="22f59-112">`virtual` Modifikátor nelze použít `static` `abstract`s `private`modifikátory , , nebo `override` modifikátory.</span><span class="sxs-lookup"><span data-stu-id="22f59-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="22f59-113">Následující příklad ukazuje virtuální vlastnost:</span><span class="sxs-lookup"><span data-stu-id="22f59-113">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="22f59-114">Virtuální vlastnosti se chovají jako virtuální metody, s výjimkou rozdílů v syntaxi deklarace a vyvolání.</span><span class="sxs-lookup"><span data-stu-id="22f59-114">Virtual properties behave like virtual methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="22f59-115">Je chyba použít `virtual` modifikátor na statickou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="22f59-115">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="22f59-116">Virtuální zděděná vlastnost může být přepsána v odvozené `override` třídě zahrnutím deklarace vlastnosti, která používá modifikátor.</span><span class="sxs-lookup"><span data-stu-id="22f59-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="22f59-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="22f59-117">Example</span></span>

<span data-ttu-id="22f59-118">V tomto `Shape` příkladu třída obsahuje `x`dvě `y`souřadnice , a `Area()` virtuální metoda.</span><span class="sxs-lookup"><span data-stu-id="22f59-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="22f59-119">Různé třídy `Circle`tvarů, například , `Cylinder`a `Sphere` dědí třídu `Shape` a plocha povrchu se vypočítá pro každý obrázek.</span><span class="sxs-lookup"><span data-stu-id="22f59-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="22f59-120">Každá odvozená třída má vlastní `Area()`implementaci přepsání .</span><span class="sxs-lookup"><span data-stu-id="22f59-120">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="22f59-121">Všimněte si, `Circle`že `Sphere`zděděné třídy , a `Cylinder` všechny používají konstruktory, které inicializují základní třídu, jak je znázorněno v následující deklaraci.</span><span class="sxs-lookup"><span data-stu-id="22f59-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="22f59-122">Následující program vypočítá a zobrazí příslušnou oblast pro každý obrázek vyvoláním `Area()` příslušné implementace metody podle objektu, který je přidružen k metodě.</span><span class="sxs-lookup"><span data-stu-id="22f59-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="22f59-123">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="22f59-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="22f59-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="22f59-124">See also</span></span>

- [<span data-ttu-id="22f59-125">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="22f59-125">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="22f59-126">Abstraktní</span><span class="sxs-lookup"><span data-stu-id="22f59-126">abstract</span></span>](abstract.md)
- [<span data-ttu-id="22f59-127">override</span><span class="sxs-lookup"><span data-stu-id="22f59-127">override</span></span>](override.md)
- [<span data-ttu-id="22f59-128">nový (modifikátor)</span><span class="sxs-lookup"><span data-stu-id="22f59-128">new (modifier)</span></span>](new-modifier.md)
