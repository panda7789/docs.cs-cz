---
title: abstraktní C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: a6c0ac86689c5d095fc077beb39d6281f77aab24
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422945"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="a1bcb-102">abstract (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a1bcb-102">abstract (C# Reference)</span></span>
<span data-ttu-id="a1bcb-103">Modifikátor `abstract` označuje, že upravená věc má chybějící nebo nekompletní implementaci.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="a1bcb-104">Modifikátor abstract lze použít se třídami, metodami, vlastnostmi, indexery a událostmi.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="a1bcb-105">Použijte modifikátor `abstract` v deklaraci třídy k označení toho, že třída je určena pouze pro základní třídu jiných tříd, nikoli na vlastní instanci.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="a1bcb-106">Členy označené jako abstraktní musí být implementovány neabstraktními třídami odvozenými z abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-106">Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="a1bcb-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1bcb-107">Example</span></span>  
 <span data-ttu-id="a1bcb-108">V tomto příkladu musí třída `Square` poskytovat implementaci `GetArea`, protože je odvozena z `Shape`:</span><span class="sxs-lookup"><span data-stu-id="a1bcb-108">In this example, the class `Square` must provide an implementation of `GetArea` because it derives from `Shape`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="a1bcb-109">Abstraktní třídy mají následující funkce:</span><span class="sxs-lookup"><span data-stu-id="a1bcb-109">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="a1bcb-110">Nelze vytvořit instanci abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-110">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="a1bcb-111">Abstraktní třída může obsahovat abstraktní metody a přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="a1bcb-112">Není možné změnit abstraktní třídu s [zapečetěným](./sealed.md) modifikátorem, protože dva modifikátory mají opačné významy.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-112">It is not possible to modify an abstract class with the [sealed](./sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="a1bcb-113">Modifikátor `sealed` zabraňuje dědění třídy a modifikátor `abstract` vyžaduje dědění třídy.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="a1bcb-114">Neabstraktní třída odvozená z abstraktní třídy musí zahrnovat skutečné implementace všech zděděných abstraktních metod a přístupových objektů.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="a1bcb-115">Použijte modifikátor `abstract` v deklaraci metody nebo vlastnosti, abyste označili, že metoda nebo vlastnost neobsahuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="a1bcb-116">Abstraktní metody mají následující funkce:</span><span class="sxs-lookup"><span data-stu-id="a1bcb-116">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="a1bcb-117">Abstraktní metoda je implicitně virtuální metodou.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-117">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="a1bcb-118">Deklarace abstraktní metody jsou povolené jenom v abstraktních třídách.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="a1bcb-119">Vzhledem k tomu, že deklarace abstraktní metody neposkytuje žádnou skutečnou implementaci, neexistuje tělo metody; deklarace metody jednoduše končí středníkem a za signaturou neexistují žádné složené závorky ({}).</span><span class="sxs-lookup"><span data-stu-id="a1bcb-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="a1bcb-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a1bcb-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="a1bcb-121">Implementace je poskytována [přepsáním](./override.md)metody, která je členem neabstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-121">The implementation is provided by a method [override](./override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="a1bcb-122">Použití [statických](./static.md) nebo [virtuálních](./virtual.md) modifikátorů v deklaraci abstraktní metody je chyba.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-122">It is an error to use the [static](./static.md) or [virtual](./virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="a1bcb-123">Abstraktní vlastnosti se chovají jako abstraktní metody, s výjimkou rozdílů v deklaraci a syntaxi vyvolání.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="a1bcb-124">Použití modifikátoru `abstract` pro statickou vlastnost je chybné.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="a1bcb-125">Abstraktní zděděná vlastnost může být přepsána v odvozené třídě zahrnutím deklarace vlastnosti, která používá modifikátor [přepsání](./override.md) .</span><span class="sxs-lookup"><span data-stu-id="a1bcb-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](./override.md) modifier.</span></span>  
  
 <span data-ttu-id="a1bcb-126">Další informace o abstraktních třídách naleznete v tématu [abstraktní a zapečetěné třídy a členy třídy](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="a1bcb-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="a1bcb-127">Abstraktní třída musí poskytovat implementaci pro všechny členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="a1bcb-128">Abstraktní třída, která implementuje rozhraní, může mapovat metody rozhraní na abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="a1bcb-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a1bcb-129">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="a1bcb-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1bcb-130">Example</span></span>  
 <span data-ttu-id="a1bcb-131">V tomto příkladu je třída `DerivedClass` odvozena od `BaseClass`abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="a1bcb-132">Abstraktní třída obsahuje abstraktní metodu, `AbstractMethod`a dvě abstraktní vlastnosti, `X` a `Y`.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="a1bcb-133">Pokud se v předchozím příkladu pokusíte vytvořit instanci abstraktní třídy pomocí příkazu podobného tomuto:</span><span class="sxs-lookup"><span data-stu-id="a1bcb-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="a1bcb-134">Zobrazí se chyba oznamující, že kompilátor nemůže vytvořit instanci abstraktní třídy ' BaseClass '.</span><span class="sxs-lookup"><span data-stu-id="a1bcb-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="a1bcb-135">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a1bcb-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1bcb-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a1bcb-136">See also</span></span>

- [<span data-ttu-id="a1bcb-137">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="a1bcb-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a1bcb-138">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a1bcb-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a1bcb-139">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="a1bcb-139">Modifiers</span></span>](index.md)
- [<span data-ttu-id="a1bcb-140">virtual</span><span class="sxs-lookup"><span data-stu-id="a1bcb-140">virtual</span></span>](./virtual.md)
- [<span data-ttu-id="a1bcb-141">override</span><span class="sxs-lookup"><span data-stu-id="a1bcb-141">override</span></span>](./override.md)
- [<span data-ttu-id="a1bcb-142">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a1bcb-142">C# Keywords</span></span>](./index.md)
