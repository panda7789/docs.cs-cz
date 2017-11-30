---
title: "abstract (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- abstract
- abstract_CSharpKeyword
helpviewer_keywords: abstract keyword [C#]
ms.assetid: b0797770-c1f3-4b4d-9441-b9122602a6bb
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 785c23294abdbfa0684560a38fbd0279200a7d02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="abstract-c-reference"></a><span data-ttu-id="40a70-102">abstract (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="40a70-102">abstract (C# Reference)</span></span>
<span data-ttu-id="40a70-103">`abstract` Modifikátor znamená, že je věcí upravována má implementace chybí nebo jsou neúplné.</span><span class="sxs-lookup"><span data-stu-id="40a70-103">The `abstract` modifier indicates that the thing being modified has a missing or incomplete implementation.</span></span> <span data-ttu-id="40a70-104">Abstraktní modifikátor lze použít s tříd, metod, vlastností, indexery a události.</span><span class="sxs-lookup"><span data-stu-id="40a70-104">The abstract modifier can be used with classes, methods, properties, indexers, and events.</span></span> <span data-ttu-id="40a70-105">Použití `abstract` modifikátor v deklaraci třídy k označení, že třída je určen pouze k být základní třídy jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="40a70-105">Use the `abstract` modifier in a class declaration to indicate that a class is intended only to be a base class of other classes.</span></span> <span data-ttu-id="40a70-106">Členy označené jako abstraktní, nebo součástí abstraktní třídu, musí být implementované třídy, které jsou odvozeny od abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="40a70-106">Members marked as abstract, or included in an abstract class, must be implemented by classes that derive from the abstract class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40a70-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="40a70-107">Example</span></span>  
 <span data-ttu-id="40a70-108">V tomto příkladu třída `Square` musí poskytovat implementace `Area` protože je odvozen z `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="40a70-108">In this example, the class `Square` must provide an implementation of `Area` because it derives from `ShapesClass`:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_1.cs)]  
  
 <span data-ttu-id="40a70-109">Abstraktní třídy mají následující funkce:</span><span class="sxs-lookup"><span data-stu-id="40a70-109">Abstract classes have the following features:</span></span>  
  
-   <span data-ttu-id="40a70-110">Nelze vytvořit instanci abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="40a70-110">An abstract class cannot be instantiated.</span></span>  
  
-   <span data-ttu-id="40a70-111">Abstraktní třídy může obsahovat abstraktní metody a přístupové objekty.</span><span class="sxs-lookup"><span data-stu-id="40a70-111">An abstract class may contain abstract methods and accessors.</span></span>  
  
-   <span data-ttu-id="40a70-112">Není možné změnit abstraktní třídy [zapečetěné](../../../csharp/language-reference/keywords/sealed.md) modifikátor protože dvě modifers mají opačné významy.</span><span class="sxs-lookup"><span data-stu-id="40a70-112">It is not possible to modify an abstract class with the [sealed](../../../csharp/language-reference/keywords/sealed.md) modifier because the two modifers have opposite meanings.</span></span> <span data-ttu-id="40a70-113">`sealed` Modifikátor brání třídy dědí a `abstract` modifikátor vyžaduje zděděná třída.</span><span class="sxs-lookup"><span data-stu-id="40a70-113">The `sealed` modifier prevents a class from being inherited and the `abstract` modifier requires a class to be inherited.</span></span>  
  
-   <span data-ttu-id="40a70-114">Neabstraktní třídy odvozené od abstraktní třídy musí obsahovat Skutečná implementace všechny zděděné abstraktní metody a přístupové objekty.</span><span class="sxs-lookup"><span data-stu-id="40a70-114">A non-abstract class derived from an abstract class must include actual implementations of all inherited abstract methods and accessors.</span></span>  
  
 <span data-ttu-id="40a70-115">Použití `abstract` modifikátor v deklaraci metody nebo vlastnosti k označení metody nebo vlastnosti neobsahuje implementace.</span><span class="sxs-lookup"><span data-stu-id="40a70-115">Use the `abstract` modifier in a method or property declaration to indicate that the method or property does not contain implementation.</span></span>  
  
 <span data-ttu-id="40a70-116">Abstraktní metody mají následující funkce:</span><span class="sxs-lookup"><span data-stu-id="40a70-116">Abstract methods have the following features:</span></span>  
  
-   <span data-ttu-id="40a70-117">Abstraktní metodu je implicitně virtuální metoda.</span><span class="sxs-lookup"><span data-stu-id="40a70-117">An abstract method is implicitly a virtual method.</span></span>  
  
-   <span data-ttu-id="40a70-118">Abstraktní metodu deklarace jsou povolena pouze v abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="40a70-118">Abstract method declarations are only permitted in abstract classes.</span></span>  
  
-   <span data-ttu-id="40a70-119">Vzhledem k tomu, že deklarace abstraktní metody poskytuje žádný skutečný implementaci, není žádná metoda textu; deklarace metody jednoduše končí středníkem a neexistují žádné složené závorky ({}), následující podpis.</span><span class="sxs-lookup"><span data-stu-id="40a70-119">Because an abstract method declaration provides no actual implementation, there is no method body; the method declaration simply ends with a semicolon and there are no curly braces ({ }) following the signature.</span></span> <span data-ttu-id="40a70-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="40a70-120">For example:</span></span>  
  
    ```  
    public abstract void MyMethod();  
    ```  
  
     <span data-ttu-id="40a70-121">Poskytuje implementaci metodu přepsání[přepsat](../../../csharp/language-reference/keywords/override.md), který je členem jinou než abstraktní třídou.</span><span class="sxs-lookup"><span data-stu-id="40a70-121">The implementation is provided by an overriding method[override](../../../csharp/language-reference/keywords/override.md), which is a member of a non-abstract class.</span></span>  
  
-   <span data-ttu-id="40a70-122">Jedná se o chybu používat [statické](../../../csharp/language-reference/keywords/static.md) nebo [virtuální](../../../csharp/language-reference/keywords/virtual.md) modifikátory v deklarace abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="40a70-122">It is an error to use the [static](../../../csharp/language-reference/keywords/static.md) or [virtual](../../../csharp/language-reference/keywords/virtual.md) modifiers in an abstract method declaration.</span></span>  
  
 <span data-ttu-id="40a70-123">Abstraktní vlastnosti chovat jako abstraktní metody, s výjimkou rozdíly v syntaxi deklarace a volání.</span><span class="sxs-lookup"><span data-stu-id="40a70-123">Abstract properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>  
  
-   <span data-ttu-id="40a70-124">Jedná se o chybu používat `abstract` modifikátor na pomocí statické vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="40a70-124">It is an error to use the `abstract` modifier on a static property.</span></span>  
  
-   <span data-ttu-id="40a70-125">Abstraktní zděděnou vlastnost je možné přepsat v odvozené třídě včetně deklarace vlastnosti, která používá [přepsat](../../../csharp/language-reference/keywords/override.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="40a70-125">An abstract inherited property can be overridden in a derived class by including a property declaration that uses the [override](../../../csharp/language-reference/keywords/override.md) modifier.</span></span>  
  
 <span data-ttu-id="40a70-126">Další informace o abstraktní třídy najdete v tématu [abstraktní a zapečetěné třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="40a70-126">For more information about abstract classes, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
 <span data-ttu-id="40a70-127">Abstraktní třída musí poskytovat implementace pro všechny členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="40a70-127">An abstract class must provide implementation for all interface members.</span></span>  
  
 <span data-ttu-id="40a70-128">Abstraktní třída, která implementuje rozhraní může mapování metod rozhraní na abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="40a70-128">An abstract class that implements an interface might map the interface methods onto abstract methods.</span></span> <span data-ttu-id="40a70-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="40a70-129">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="40a70-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="40a70-130">Example</span></span>  
 <span data-ttu-id="40a70-131">V tomto příkladu třída `DerivedClass` je odvozený z abstraktní třídy `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="40a70-131">In this example, the class `DerivedClass` is derived from an abstract class `BaseClass`.</span></span> <span data-ttu-id="40a70-132">Abstraktní třída obsahuje metody abstraktní `AbstractMethod`a dvě abstraktní vlastnosti `X` a `Y`.</span><span class="sxs-lookup"><span data-stu-id="40a70-132">The abstract class contains an abstract method, `AbstractMethod`, and two abstract properties, `X` and `Y`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/abstract_3.cs)]  
  
 <span data-ttu-id="40a70-133">V předchozím příkladu, pokud se pokusíte vytvořit instanci abstraktní třídy za použití příkazu takto:</span><span class="sxs-lookup"><span data-stu-id="40a70-133">In the preceding example, if you attempt to instantiate the abstract class by using a statement like this:</span></span>  
  
```  
BaseClass bc = new BaseClass();   // Error  
```  
  
 <span data-ttu-id="40a70-134">Zobrazí se chyba s oznámením, že kompilátor nelze vytvořit instanci abstraktní třídy 'Baseclass –'.</span><span class="sxs-lookup"><span data-stu-id="40a70-134">you will get an error saying that the compiler cannot create an instance of the abstract class 'BaseClass'.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="40a70-135">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="40a70-135">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="40a70-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="40a70-136">See Also</span></span>  
 [<span data-ttu-id="40a70-137">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="40a70-137">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="40a70-138">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="40a70-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="40a70-139">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="40a70-139">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="40a70-140">virtuální</span><span class="sxs-lookup"><span data-stu-id="40a70-140">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="40a70-141">přepsání</span><span class="sxs-lookup"><span data-stu-id="40a70-141">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="40a70-142">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="40a70-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
