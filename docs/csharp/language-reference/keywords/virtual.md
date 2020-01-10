---
title: virtuální C# odkaz
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 47b77792fd3a2b2700ec0734851fdec534361596
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712868"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="15c80-102">virtual (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="15c80-102">virtual (C# Reference)</span></span>

<span data-ttu-id="15c80-103">Klíčové slovo `virtual` slouží k úpravě deklarace metody, vlastnosti, indexeru nebo události a umožňuje přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="15c80-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="15c80-104">Tuto metodu lze například přepsat libovolnou třídou, která ji dědí:</span><span class="sxs-lookup"><span data-stu-id="15c80-104">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area() 
{
    return x * y;
}
```

<span data-ttu-id="15c80-105">Implementaci virtuálního člena lze změnit [přepsáním členu](override.md) v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="15c80-105">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="15c80-106">Další informace o použití klíčového slova `virtual` naleznete v tématu [Správa verzí pomocí klíčových slov override a New](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít klíčová slova override a New](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="15c80-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="15c80-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15c80-107">Remarks</span></span>

<span data-ttu-id="15c80-108">Je-li vyvolána virtuální metoda, je typ běhu objektu zkontrolován pro přepisující člena.</span><span class="sxs-lookup"><span data-stu-id="15c80-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="15c80-109">Přepsání členu v největší odvozené třídě je volána, což může být původní člen, pokud žádná odvozená třída přepsala člena.</span><span class="sxs-lookup"><span data-stu-id="15c80-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="15c80-110">Ve výchozím nastavení jsou metody nevirtuální.</span><span class="sxs-lookup"><span data-stu-id="15c80-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="15c80-111">Nemůžete přepsat nevirtuální (non-Virtual) metodu.</span><span class="sxs-lookup"><span data-stu-id="15c80-111">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="15c80-112">Modifikátor `virtual` nelze použít u modifikátorů `static`, `abstract`, `private`nebo `override`.</span><span class="sxs-lookup"><span data-stu-id="15c80-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="15c80-113">Následující příklad ukazuje virtuální vlastnost:</span><span class="sxs-lookup"><span data-stu-id="15c80-113">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="15c80-114">Virtuální vlastnosti se chovají podobně jako virtuální metody, s výjimkou rozdílů v deklaraci a syntaxi vyvolání.</span><span class="sxs-lookup"><span data-stu-id="15c80-114">Virtual properties behave like virtual methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="15c80-115">Použití modifikátoru `virtual` pro statickou vlastnost je chybné.</span><span class="sxs-lookup"><span data-stu-id="15c80-115">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="15c80-116">Virtuální zděděnou vlastnost lze přepsat v odvozené třídě zahrnutím deklarace vlastnosti, která používá modifikátor `override`.</span><span class="sxs-lookup"><span data-stu-id="15c80-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="15c80-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="15c80-117">Example</span></span>

<span data-ttu-id="15c80-118">V tomto příkladu třída `Shape` obsahuje dvě souřadnice `x`, `y`a `Area()` virtuální metodu.</span><span class="sxs-lookup"><span data-stu-id="15c80-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="15c80-119">Různé třídy tvarů, například `Circle`, `Cylinder`a `Sphere` dědí třídu `Shape` a oblast plocha je vypočítána pro každý obrázek.</span><span class="sxs-lookup"><span data-stu-id="15c80-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="15c80-120">Každá odvozená třída má svou vlastní implementaci přepsání `Area()`.</span><span class="sxs-lookup"><span data-stu-id="15c80-120">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="15c80-121">Všimněte si, že zděděné třídy `Circle`, `Sphere`a `Cylinder` všechny používají konstruktory, které inicializují základní třídu, jak je znázorněno v následující deklaraci.</span><span class="sxs-lookup"><span data-stu-id="15c80-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="15c80-122">Následující program vypočítá a zobrazí příslušnou oblast pro každý obrázek vyvoláním příslušné implementace metody `Area()`, v závislosti na objektu, který je spojen s metodou.</span><span class="sxs-lookup"><span data-stu-id="15c80-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="15c80-123">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="15c80-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="15c80-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15c80-124">See also</span></span>

- [<span data-ttu-id="15c80-125">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="15c80-125">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="15c80-126">abstract</span><span class="sxs-lookup"><span data-stu-id="15c80-126">abstract</span></span>](abstract.md)
- [<span data-ttu-id="15c80-127">override</span><span class="sxs-lookup"><span data-stu-id="15c80-127">override</span></span>](override.md)
- [<span data-ttu-id="15c80-128">New (modifikátor)</span><span class="sxs-lookup"><span data-stu-id="15c80-128">new (modifier)</span></span>](new-modifier.md)
