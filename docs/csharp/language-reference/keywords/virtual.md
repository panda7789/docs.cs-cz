---
title: virtual (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: af5b7e3efdc98910ebbe7e061eba250cbe2d0c50
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207346"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="127ee-102">virtual (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="127ee-102">virtual (C# Reference)</span></span>
<span data-ttu-id="127ee-103">`virtual` – Klíčové slovo slouží k úpravě deklaraci metoda, vlastnost, indexer nebo událostí a povolit pro ni k přepsání v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="127ee-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="127ee-104">Například tuto metodu je možné přepsat všechny třídy, která dědí ho:</span><span class="sxs-lookup"><span data-stu-id="127ee-104">For example, this method can be overridden by any class that inherits it:</span></span>  
  
```csharp  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 <span data-ttu-id="127ee-105">Implementace člena virtuální může změnit [přepsání člena](../../../csharp/language-reference/keywords/override.md) v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="127ee-105">The implementation of a virtual member can be changed by an [overriding member](../../../csharp/language-reference/keywords/override.md) in a derived class.</span></span> <span data-ttu-id="127ee-106">Další informace o tom, jak používat `virtual` – klíčové slovo, najdete v části [Správa verzí pomocí nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [zároveň budete vědět, když pomocí přepsání a nová klíčová slova](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="127ee-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="127ee-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="127ee-107">Remarks</span></span>  
 <span data-ttu-id="127ee-108">Když se virtuální metoda je volána, běhového typu objektu, se kontroluje přepsání člena.</span><span class="sxs-lookup"><span data-stu-id="127ee-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="127ee-109">Přepsání člena nejvíce odvozené třídy se nazývá, původní člena, který může být pokud žádné odvozené třídy přepsal člena.</span><span class="sxs-lookup"><span data-stu-id="127ee-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>  
  
 <span data-ttu-id="127ee-110">Ve výchozím nastavení jsou bez virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="127ee-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="127ee-111">Nejde přepsat bez virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="127ee-111">You cannot override a non-virtual method.</span></span>  
  
 <span data-ttu-id="127ee-112">Nelze použít `virtual` modifikátor s `static`, `abstract`, `private`, nebo `override` modifikátory.</span><span class="sxs-lookup"><span data-stu-id="127ee-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="127ee-113">Následující příklad ukazuje virtuální vlastnost:</span><span class="sxs-lookup"><span data-stu-id="127ee-113">The following example shows a virtual property:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 <span data-ttu-id="127ee-114">Vlastnosti virtuálního chovat jako abstraktní metody, s výjimkou rozdíly v syntaxi deklarace a volání.</span><span class="sxs-lookup"><span data-stu-id="127ee-114">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="127ee-115">Jedná se o chybu používat `virtual` modifikátor na pomocí statické vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="127ee-115">It is an error to use the `virtual` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="127ee-116">Virtuální zděděnou vlastnost je možné přepsat v odvozené třídě včetně deklarace vlastnosti, která používá `override` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="127ee-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="127ee-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="127ee-117">Example</span></span>  
 <span data-ttu-id="127ee-118">V tomto příkladu `Shape` třída obsahuje dvě souřadnice `x`, `y`a `Area()` virtuální metoda.</span><span class="sxs-lookup"><span data-stu-id="127ee-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="127ee-119">Různé tvar třídy, jako `Circle`, `Cylinder`, a `Sphere` dědění `Shape` třídy a možnosti útoku se počítá pro každý obrázek.</span><span class="sxs-lookup"><span data-stu-id="127ee-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="127ee-120">Každá odvozená třída má vlastní implementaci přepsání `Area()`.</span><span class="sxs-lookup"><span data-stu-id="127ee-120">Each derived class has its own override implementation of `Area()`.</span></span>  
  
 <span data-ttu-id="127ee-121">Všimněte si, že zděděné třídy `Circle`, `Sphere`, a `Cylinder` všichni používají konstruktory, které inicializaci základní třídy, jak je znázorněno v následující prohlášení.</span><span class="sxs-lookup"><span data-stu-id="127ee-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>  
  
```csharp  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 <span data-ttu-id="127ee-122">Následující program vypočítá a zobrazí příslušné oblasti pro každý obrázek vyvoláním příslušné implementace `Area()` metoda, podle objektu, která je přidružená metoda.</span><span class="sxs-lookup"><span data-stu-id="127ee-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="127ee-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="127ee-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="127ee-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="127ee-124">See Also</span></span>  
 [<span data-ttu-id="127ee-125">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="127ee-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="127ee-126">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="127ee-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="127ee-127">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="127ee-127">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="127ee-128">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="127ee-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="127ee-129">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="127ee-129">Polymorphism</span></span>](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [<span data-ttu-id="127ee-130">abstract</span><span class="sxs-lookup"><span data-stu-id="127ee-130">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
 [<span data-ttu-id="127ee-131">override</span><span class="sxs-lookup"><span data-stu-id="127ee-131">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="127ee-132">new</span><span class="sxs-lookup"><span data-stu-id="127ee-132">new</span></span>](../../../csharp/language-reference/keywords/new.md)
