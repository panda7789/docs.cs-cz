---
title: "Abstraktní a uzavřené třídy a jejich členové (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dac7570c018bd577faac4540e4d800cc11143578
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="ad02f-102">Abstraktní a uzavřené třídy a jejich členové (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ad02f-102">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="ad02f-103">[Abstraktní](../../../csharp/language-reference/keywords/abstract.md) – klíčové slovo lze vytvořit třídy a [třída](../../../csharp/language-reference/keywords/class.md) členy, kteří jsou neúplné a musí být implementován v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="ad02f-103">The [abstract](../../../csharp/language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../../csharp/language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="ad02f-104">[Zapečetěné](../../../csharp/language-reference/keywords/sealed.md) – klíčové slovo umožňuje zabránit dědičnosti třídy nebo členy určité třídy, které byly dříve označeny [virtuální](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="ad02f-104">The [sealed](../../../csharp/language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="ad02f-105">Abstraktní třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="ad02f-105">Abstract Classes and Class Members</span></span>  
 <span data-ttu-id="ad02f-106">Třídy lze deklarovat jako abstraktní umístěním klíčové slovo `abstract` před definici třídy.</span><span class="sxs-lookup"><span data-stu-id="ad02f-106">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="ad02f-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ad02f-107">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_1.cs)]  
  
 <span data-ttu-id="ad02f-108">Nelze vytvořit instanci abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="ad02f-108">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="ad02f-109">Účelem abstraktní třída je poskytnout společná definice, můžete sdílet více odvozené třídy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ad02f-109">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="ad02f-110">Knihovny tříd může například definovat abstraktní třída, která se používá jako parametr pro řadu její funkce a vyžadují programátory použití této knihovny a zadejte vlastní implementaci třídy vytvořením odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ad02f-110">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="ad02f-111">Abstraktní třídy může také definovat abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="ad02f-111">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="ad02f-112">To je možné udělat přidáním klíčové slovo `abstract` před návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="ad02f-112">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="ad02f-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ad02f-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_2.cs)]  
  
 <span data-ttu-id="ad02f-114">Abstraktní metody nemají implementaci, tak definici metody následuje středníkem místo normální metoda blok.</span><span class="sxs-lookup"><span data-stu-id="ad02f-114">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="ad02f-115">Abstraktní třídy odvozené třídy musí implementovat všechny abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="ad02f-115">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="ad02f-116">Když abstraktní třídy dědí virtuální metoda ze základní třídy, abstraktní třídu můžete přepsat virtuální metodu s abstraktní metodu.</span><span class="sxs-lookup"><span data-stu-id="ad02f-116">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="ad02f-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ad02f-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_3.cs)]  
  
 <span data-ttu-id="ad02f-118">Pokud `virtual` je deklarovaná metoda `abstract`, je stále virtuální všechny třídy, která dědí z abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="ad02f-118">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="ad02f-119">Dědění metodu pro abstraktní třídu nelze získat přístup k původní implementace metody – v předchozím příkladu `DoWork` na třídu, nelze volat F `DoWork` na D. – Třída Tímto způsobem můžete vynutit abstraktní třídy odvozené třídy zajistit nové implementace metody pro virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="ad02f-119">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="ad02f-120">Zapečetěné třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="ad02f-120">Sealed Classes and Class Members</span></span>  
 <span data-ttu-id="ad02f-121">Třídy lze deklarovat jako [zapečetěné](../../../csharp/language-reference/keywords/sealed.md) umístěním klíčové slovo `sealed` před definici třídy.</span><span class="sxs-lookup"><span data-stu-id="ad02f-121">Classes can be declared as [sealed](../../../csharp/language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="ad02f-122">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ad02f-122">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_4.cs)]  
  
 <span data-ttu-id="ad02f-123">Zapečetěné třídy nelze použít jako základní třída.</span><span class="sxs-lookup"><span data-stu-id="ad02f-123">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="ad02f-124">Z tohoto důvodu je také nemůže být abstraktní třídu.</span><span class="sxs-lookup"><span data-stu-id="ad02f-124">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="ad02f-125">Zapečetěné třídy zabránit odvození.</span><span class="sxs-lookup"><span data-stu-id="ad02f-125">Sealed classes prevent derivation.</span></span> <span data-ttu-id="ad02f-126">Protože nikdy je možné použít jako základní třída, můžete provést některé optimalizace běhu volání členy zapečetěné třídy mírně rychlejší.</span><span class="sxs-lookup"><span data-stu-id="ad02f-126">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="ad02f-127">Metoda, indexer, vlastnost nebo událost v odvozené třídě, která přepisují člena virtuální základní třídy lze deklarovat jako zapečetěné tohoto člena.</span><span class="sxs-lookup"><span data-stu-id="ad02f-127">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="ad02f-128">To Neguje virtuální aspekt člena pro všechny další odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ad02f-128">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="ad02f-129">To lze provést vložení `sealed` – klíčové slovo před [přepsat](../../../csharp/language-reference/keywords/override.md) – klíčové slovo v deklarace člena třídy.</span><span class="sxs-lookup"><span data-stu-id="ad02f-129">This is accomplished by putting the `sealed` keyword before the [override](../../../csharp/language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="ad02f-130">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ad02f-130">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/abstract-and-sealed-classes-and-class-members_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ad02f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad02f-131">See Also</span></span>  
 [<span data-ttu-id="ad02f-132">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ad02f-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ad02f-133">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="ad02f-133">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="ad02f-134">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="ad02f-134">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [<span data-ttu-id="ad02f-135">Metody</span><span class="sxs-lookup"><span data-stu-id="ad02f-135">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [<span data-ttu-id="ad02f-136">Pole</span><span class="sxs-lookup"><span data-stu-id="ad02f-136">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)  
 [<span data-ttu-id="ad02f-137">Postupy: definování abstraktních a vlastností</span><span class="sxs-lookup"><span data-stu-id="ad02f-137">How to: Define Abstract Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-define-abstract-properties.md)
