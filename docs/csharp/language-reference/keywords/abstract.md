---
title: abstraktní - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords:
- abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
ms.openlocfilehash: 3a4d29ae4814ccceb7b405d9c1749150059a24a0
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859595"
---
# <a name="abstract-c-reference"></a><span data-ttu-id="c27e2-102">abstract (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c27e2-102">abstract (C# Reference)</span></span>
<span data-ttu-id="c27e2-103">`abstract` Modifikátor znamená, že věc, kterou právě upravuje má chybějící či neúplné implementace.</span><span class="sxs-lookup"><span data-stu-id="c27e2-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="c27e2-104">Modifikátor abstract jde použít s třídy, metody, vlastnosti, indexery a události.</span><span class="sxs-lookup"><span data-stu-id="c27e2-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="c27e2-105">Použití `abstract` modifikátor v deklaraci třídy k označení, že třída je určen pouze k být základní třídou jiné třídy, není vytvořena instance samostatně.</span><span class="sxs-lookup"><span data-stu-id="c27e2-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes, not instantiated on its own.</span></span> <span data-ttu-id="c27e2-106">Členy označené jako abstraktní musí být implementované neabstraktní třídy, které jsou odvozeny od abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="c27e2-106">Members marked as abstract must be implemented by non-abstract classes that derive from the abstract class.</span></span>
  
## <a name="example"></a><span data-ttu-id="c27e2-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="c27e2-107">Example</span></span>  
 <span data-ttu-id="c27e2-108">V tomto příkladu třída `Square` musí zajišťovat implementaci rozhraní `GetArea` protože se odvozuje od `Shape`:</span><span class="sxs-lookup"><span data-stu-id="c27e2-108">In this example, the class `Square` must provide an implementation of `GetArea` because it derives from `Shape`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]
  
 <span data-ttu-id="c27e2-109">Abstraktní třídy mají následující funkce:</span><span class="sxs-lookup"><span data-stu-id="c27e2-109">Abstract classes have the following features:</span></span>  
  
- <span data-ttu-id="c27e2-110">Nelze vytvořit instanci abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="c27e2-110">An abstract class cannot be instantiated.</span></span>  
  
- <span data-ttu-id="c27e2-111">Abstraktní třída může obsahovat abstraktní metody a přístupové objekty.</span><span class="sxs-lookup"><span data-stu-id="c27e2-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
- <span data-ttu-id="c27e2-112">Není možné změnit abstraktní třídy [zapečetěné](../../../csharp/language-reference/keywords/sealed.md) modifikátor protože dva Modifikátory mají opačné význam.</span><span class="sxs-lookup"><span data-stu-id="c27e2-112">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifiers have opposite meanings.</span></span> <span data-ttu-id="c27e2-113">`sealed` Modifikátor zabraňuje třídy děděny a `abstract` vyžaduje Modifikátor třídy odvozeny.</span><span class="sxs-lookup"><span data-stu-id="c27e2-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
- <span data-ttu-id="c27e2-114">Neabstraktní třídy odvozené od abstraktní třídy musí obsahovat Skutečná implementace všechny zděděné abstraktní metody a přístupové objekty.</span><span class="sxs-lookup"><span data-stu-id="c27e2-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="c27e2-115">Použití `abstract` modifikátor v deklaraci metody nebo vlastnosti k označení, že metoda nebo vlastnost neobsahuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="c27e2-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="c27e2-116">Abstraktní metody nemají následující funkce:</span><span class="sxs-lookup"><span data-stu-id="c27e2-116">Abstract methods have the following features:</span></span>  
  
- <span data-ttu-id="c27e2-117">Abstraktní metoda je implicitně virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="c27e2-117">An abstract method is implicitly a virtual method.</span></span>  
  
- <span data-ttu-id="c27e2-118">Deklarace abstraktní metody jsou povolené jenom v abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="c27e2-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
- <span data-ttu-id="c27e2-119">Protože deklarací abstraktní metody poskytuje skutečné implementaci, neexistuje žádné tělo metody; deklarace metody jednoduše končí středníkem a neexistují žádné složených závorek ({}) po podpisu.</span><span class="sxs-lookup"><span data-stu-id="c27e2-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="c27e2-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c27e2-120">For example:</span></span>  
  
    ```csharp  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="c27e2-121">Poskytuje implementaci metody [přepsat](../../../csharp/language-reference/keywords/override.md), který je členem skupiny jinou než abstraktní třídou.</span><span class="sxs-lookup"><span data-stu-id="c27e2-121">The implementation is provided by a method [override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
- <span data-ttu-id="c27e2-122">Jedná se o chybu používat [statické](../../../csharp/language-reference/keywords/static.md) nebo [virtuální](../../../csharp/language-reference/keywords/virtual.md) modifikátorů v deklarací abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="c27e2-122">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="c27e2-123">Abstraktní vlastnosti se chovají stejně jako abstraktní metody, s výjimkou rozdílů v syntaxi deklarace a volání.</span><span class="sxs-lookup"><span data-stu-id="c27e2-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
- <span data-ttu-id="c27e2-124">Jedná se o chybu používat `abstract` modifikátor statickou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c27e2-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
- <span data-ttu-id="c27e2-125">Zděděný abstraktní vlastnost možné přepsat v odvozené třídě včetně, která používá deklarace vlastnosti [přepsat](../../../csharp/language-reference/keywords/override.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="c27e2-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="c27e2-126">Další informace o abstraktních tříd naleznete v tématu [abstraktní a zapečetěné třídy a členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="c27e2-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="c27e2-127">Abstraktní třídy musí poskytnout implementaci pro všechny členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c27e2-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="c27e2-128">Abstraktní třídu, která implementuje rozhraní namapovat metody rozhraní na abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="c27e2-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="c27e2-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c27e2-129">For example:</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#2)]
  
## <a name="example"></a><span data-ttu-id="c27e2-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="c27e2-130">Example</span></span>  
 <span data-ttu-id="c27e2-131">V tomto příkladu třída `DerivedClass` je odvozen z abstraktní třídy `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="c27e2-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="c27e2-132">Abstraktní třída obsahuje abstraktní metoda `AbstractMethod`a dvě abstraktních a vlastností, `X` a `Y`.</span><span class="sxs-lookup"><span data-stu-id="c27e2-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#3)]
  
 <span data-ttu-id="c27e2-133">V předchozím příkladu, pokud se pokusíte vytvořit instanci abstraktní třídy za použití příkazu takto:</span><span class="sxs-lookup"><span data-stu-id="c27e2-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```csharp
BaseClass bc = new BaseClass();   // Error  
```  
  
<span data-ttu-id="c27e2-134">Zobrazí se chyba s oznámením, že kompilátor nelze vytvořit instanci abstraktní třídy "BaseClass".</span><span class="sxs-lookup"><span data-stu-id="c27e2-134">You will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c27e2-135">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c27e2-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c27e2-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c27e2-136">See also</span></span>

- [<span data-ttu-id="c27e2-137">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c27e2-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="c27e2-138">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c27e2-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c27e2-139">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="c27e2-139">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
- [<span data-ttu-id="c27e2-140">virtual</span><span class="sxs-lookup"><span data-stu-id="c27e2-140">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)
- [<span data-ttu-id="c27e2-141">override</span><span class="sxs-lookup"><span data-stu-id="c27e2-141">override</span></span>](../../../csharp/language-reference/keywords/override.md)
- [<span data-ttu-id="c27e2-142">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c27e2-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
