---
title: virtual (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 384cc442e51ec96cafe9b44ef945bb913b0e65f6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659603"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="389f0-102">virtual (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="389f0-102">virtual (C# Reference)</span></span>
<span data-ttu-id="389f0-103">`virtual` – Klíčové slovo se používá k úpravě deklarace metody, vlastnost, indexer nebo událost a povolit pro přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="389f0-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="389f0-104">Například tato metoda může být přepsána všechny třídy, která dědí ho:</span><span class="sxs-lookup"><span data-stu-id="389f0-104">For example, this method can be overridden by any class that inherits it:</span></span>  
  
```csharp  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 <span data-ttu-id="389f0-105">Implementace virtuální člen může změnit [přepsáním členu](../../../csharp/language-reference/keywords/override.md) v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="389f0-105">The implementation of a virtual member can be changed by an [overriding member](../../../csharp/language-reference/keywords/override.md) in a derived class.</span></span> <span data-ttu-id="389f0-106">Další informace o tom, jak používat `virtual` – klíčové slovo, naleznete v tématu [Správa verzí pomocí nových klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [vědět, když pomocí přepsání a nových klíčových slov](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="389f0-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="389f0-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="389f0-107">Remarks</span></span>  
 <span data-ttu-id="389f0-108">Při vyvolání virtuální metody run-time typu objektu se kontroluje u přepsáním členu.</span><span class="sxs-lookup"><span data-stu-id="389f0-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="389f0-109">Přepsáním členu v nejvíce odvozená třída je voláno, původní člen, který může být žádný odvozená třída má potlačenou člena.</span><span class="sxs-lookup"><span data-stu-id="389f0-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>  
  
 <span data-ttu-id="389f0-110">Ve výchozím nastavení jsou nevirtuální metody.</span><span class="sxs-lookup"><span data-stu-id="389f0-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="389f0-111">Nevirtuální metoda nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="389f0-111">You cannot override a non-virtual method.</span></span>  
  
 <span data-ttu-id="389f0-112">Nelze použít `virtual` modifikátor `static`, `abstract`, `private`, nebo `override` modifikátory.</span><span class="sxs-lookup"><span data-stu-id="389f0-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="389f0-113">Následující příklad ukazuje virtuální vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="389f0-113">The following example shows a virtual property:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 <span data-ttu-id="389f0-114">Virtuální vlastnosti se chovají stejně jako abstraktní metody, s výjimkou rozdílů v syntaxi deklarace a volání.</span><span class="sxs-lookup"><span data-stu-id="389f0-114">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="389f0-115">Jedná se o chybu používat `virtual` modifikátor statickou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="389f0-115">It is an error to use the `virtual` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="389f0-116">Virtuální zděděnou vlastnost možné přepsat v odvozené třídě včetně, která používá deklarace vlastnosti `override` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="389f0-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="389f0-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="389f0-117">Example</span></span>  
 <span data-ttu-id="389f0-118">V tomto příkladu `Shape` třída obsahuje dvě souřadnice `x`, `y`a `Area()` virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="389f0-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="389f0-119">Jiný tvar třídy, jako například `Circle`, `Cylinder`, a `Sphere` dědit `Shape` třídy a útoku na počítá pro každý obrázek.</span><span class="sxs-lookup"><span data-stu-id="389f0-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="389f0-120">Každá odvozená třída má svůj vlastní implementaci přepsání `Area()`.</span><span class="sxs-lookup"><span data-stu-id="389f0-120">Each derived class has its own override implementation of `Area()`.</span></span>  
  
 <span data-ttu-id="389f0-121">Všimněte si, že zděděné třídy `Circle`, `Sphere`, a `Cylinder` používat konstruktory, které inicializuje základní třídu, jak je znázorněno v následující deklaraci.</span><span class="sxs-lookup"><span data-stu-id="389f0-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>  
  
```csharp  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 <span data-ttu-id="389f0-122">Následující program vypočítá a zobrazí příslušné oblasti pro každý obrázek vyvoláním vhodné implementaci pro `Area()` metoda podle objektu, který je přidružený k metodě.</span><span class="sxs-lookup"><span data-stu-id="389f0-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="389f0-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="389f0-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="389f0-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="389f0-124">See Also</span></span>

- [<span data-ttu-id="389f0-125">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="389f0-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="389f0-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="389f0-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="389f0-127">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="389f0-127">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="389f0-128">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="389f0-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="389f0-129">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="389f0-129">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
- [<span data-ttu-id="389f0-130">abstract</span><span class="sxs-lookup"><span data-stu-id="389f0-130">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
- [<span data-ttu-id="389f0-131">override</span><span class="sxs-lookup"><span data-stu-id="389f0-131">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
- [<span data-ttu-id="389f0-132">new</span><span class="sxs-lookup"><span data-stu-id="389f0-132">new</span></span>](../../../csharp/language-reference/keywords/new.md)
