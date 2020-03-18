---
title: abstraktní - C# Reference
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 96e8bbce2e67c316d5cd1cd78e3e2506dabead25
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713855"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="e5b06-102">abstract (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e5b06-102">abstract (C# Reference)</span></span>
<span data-ttu-id="e5b06-103">Modifikátor `abstract` označuje, že upravovaná věc má chybějící nebo neúplnou implementaci.</span><span class="sxs-lookup"><span data-stu-id="e5b06-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="e5b06-104">Abstraktní modifikátor lze použít s třídami, metodami, vlastnostmi, indexery a událostmi.</span><span class="sxs-lookup"><span data-stu-id="e5b06-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="e5b06-105">`abstract` Modifikátor v deklaraci třídy označuje, že třída je určena pouze jako základní třída jiných tříd, není vytvořena sama.</span><span class="sxs-lookup"><span data-stu-id="e5b06-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="e5b06-106">Členy označené jako abstraktní musí být implementovány neabstraktní třídy, které jsou odvozeny z abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="e5b06-106">Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="e5b06-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5b06-107">Example</span></span>  
 <span data-ttu-id="e5b06-108">V tomto příkladu `Square` musí třída `GetArea` poskytnout implementaci, `Shape`protože je odvozena z :</span><span class="sxs-lookup"><span data-stu-id="e5b06-108">In this example, the class `Square` must provide an implementation of `GetArea` because it derives from `Shape`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="e5b06-109">Abstraktní třídy mají následující funkce:</span><span class="sxs-lookup"><span data-stu-id="e5b06-109">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="e5b06-110">Abstraktní třídu nelze vytvořit instanci.</span><span class="sxs-lookup"><span data-stu-id="e5b06-110">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="e5b06-111">Abstraktní třída může obsahovat abstraktní metody a přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="e5b06-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="e5b06-112">Není možné upravit abstraktní třídu s [uzavřeným](./sealed.md) modifikátorem, protože dva modifikátory mají opačný význam.</span><span class="sxs-lookup"><span data-stu-id="e5b06-112">It is not possible to modify an abstract class with the [sealed](./sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="e5b06-113">Modifikátor `sealed` zabraňuje zdědění třídy a `abstract` modifikátor vyžaduje, aby byla třída zděděna.</span><span class="sxs-lookup"><span data-stu-id="e5b06-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="e5b06-114">Neabstraktní třída odvozená z abstraktní třídy musí obsahovat skutečné implementace všech zděděných abstraktních metod a přistupujících objektů.</span><span class="sxs-lookup"><span data-stu-id="e5b06-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="e5b06-115">`abstract` Modifikátor v deklaraci metody nebo vlastnosti označte, že metoda nebo vlastnost neobsahuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="e5b06-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="e5b06-116">Abstraktní metody mají následující funkce:</span><span class="sxs-lookup"><span data-stu-id="e5b06-116">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="e5b06-117">Abstraktní metoda je implicitně virtuální metoda.</span><span class="sxs-lookup"><span data-stu-id="e5b06-117">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="e5b06-118">Deklarace abstraktní metody jsou povoleny pouze v abstraktních třídách.</span><span class="sxs-lookup"><span data-stu-id="e5b06-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="e5b06-119">Vzhledem k tomu, že deklarace abstraktní metody neposkytuje žádnou skutečnou implementaci, neexistuje žádné tělo metody; Deklarace metody jednoduše končí středníkem a neexistují žádné složené závorky ({ }) za podpisem.</span><span class="sxs-lookup"><span data-stu-id="e5b06-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="e5b06-120">Například:</span><span class="sxs-lookup"><span data-stu-id="e5b06-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="e5b06-121">Implementace je poskytována [přepsáním](./override.md)metody , která je členem neabstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="e5b06-121">The implementation is provided by a method [override](./override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="e5b06-122">Je chyba použít [statické](./static.md) nebo [virtuální](./virtual.md) modifikátory v deklaraci abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="e5b06-122">It is an error to use the [static](./static.md) or [virtual](./virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="e5b06-123">Abstraktní vlastnosti se chovají jako abstraktní metody, s výjimkou rozdílů v syntaxi deklarace a vyvolání.</span><span class="sxs-lookup"><span data-stu-id="e5b06-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="e5b06-124">Je chyba použít `abstract` modifikátor na statickou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e5b06-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="e5b06-125">Abstraktní zděděná vlastnost může být přepsána v odvozené třídě zahrnutím deklarace vlastnosti, která používá modifikátor [přepsání.](./override.md)</span><span class="sxs-lookup"><span data-stu-id="e5b06-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](./override.md) modifier.</span></span>  
  
 <span data-ttu-id="e5b06-126">Další informace o abstraktních třídách naleznete v [tématu Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="e5b06-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="e5b06-127">Abstraktní třída musí poskytovat implementaci pro všechny členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e5b06-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="e5b06-128">Abstraktní třída, která implementuje rozhraní může mapovat metody rozhraní na abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="e5b06-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="e5b06-129">Například:</span><span class="sxs-lookup"><span data-stu-id="e5b06-129">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="e5b06-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5b06-130">Example</span></span>  
 <span data-ttu-id="e5b06-131">V tomto příkladu `DerivedClass` je třída odvozena `BaseClass`z abstraktní třídy .</span><span class="sxs-lookup"><span data-stu-id="e5b06-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="e5b06-132">Abstraktní třída obsahuje abstraktní `AbstractMethod`metodu a dvě `X` `Y`abstraktní vlastnosti a .</span><span class="sxs-lookup"><span data-stu-id="e5b06-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="e5b06-133">V předchozím příkladu pokud se pokusíte vytvořit instanci abstraktní třídy pomocí příkazu, jako je tento:</span><span class="sxs-lookup"><span data-stu-id="e5b06-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="e5b06-134">Zobrazí se chyba, že kompilátor nemůže vytvořit instanci abstraktní třídy BaseClass.</span><span class="sxs-lookup"><span data-stu-id="e5b06-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e5b06-135">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e5b06-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e5b06-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5b06-136">See also</span></span>

- [<span data-ttu-id="e5b06-137">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e5b06-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e5b06-138">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e5b06-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e5b06-139">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="e5b06-139">Modifiers</span></span>](index.md)
- [<span data-ttu-id="e5b06-140">virtual</span><span class="sxs-lookup"><span data-stu-id="e5b06-140">virtual</span></span>](./virtual.md)
- [<span data-ttu-id="e5b06-141">override</span><span class="sxs-lookup"><span data-stu-id="e5b06-141">override</span></span>](./override.md)
- [<span data-ttu-id="e5b06-142">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e5b06-142">C# Keywords</span></span>](./index.md)
