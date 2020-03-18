---
title: Abstraktní a zapečetěné třídy a členové třídy - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 07738031f1dec05424f7c3756f49a8f1f9a2c44b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714998"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="d50fe-102">Abstraktní a uzavřené třídy a jejich členové (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d50fe-102">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="d50fe-103">Klíčové slovo [abstract](../../language-reference/keywords/abstract.md) umožňuje vytvářet třídy a členy [třídy,](../../language-reference/keywords/class.md) které jsou neúplné a musí být implementovány v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="d50fe-103">The [abstract](../../language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="d50fe-104">Klíčové slovo [sealed](../../language-reference/keywords/sealed.md) umožňuje zabránit dědičnosti třídy nebo určitých členů třídy, které byly dříve označeny [jako virtuální](../../language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="d50fe-104">The [sealed](../../language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="d50fe-105">Abstraktní třídy a členové třídy</span><span class="sxs-lookup"><span data-stu-id="d50fe-105">Abstract Classes and Class Members</span></span>  
 <span data-ttu-id="d50fe-106">Třídy mohou být deklarovány jako abstraktní umístěním klíčového slova `abstract` před definici třídy.</span><span class="sxs-lookup"><span data-stu-id="d50fe-106">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="d50fe-107">Například:</span><span class="sxs-lookup"><span data-stu-id="d50fe-107">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 <span data-ttu-id="d50fe-108">Abstraktní třídu nelze vytvořit instanci.</span><span class="sxs-lookup"><span data-stu-id="d50fe-108">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="d50fe-109">Účelem abstraktní třídy je poskytnout společnou definici základní třídy, kterou může sdílet více odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="d50fe-109">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="d50fe-110">Knihovna tříd může například definovat abstraktní třídu, která se používá jako parametr pro mnoho jeho funkcí a vyžadovat, aby programátoři používající tuto knihovnu poskytovali vlastní implementaci třídy vytvořením odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="d50fe-110">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="d50fe-111">Abstraktní třídy mohou také definovat abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="d50fe-111">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="d50fe-112">Toho lze dosáhnout přidáním `abstract` klíčového slova před návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="d50fe-112">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="d50fe-113">Například:</span><span class="sxs-lookup"><span data-stu-id="d50fe-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 <span data-ttu-id="d50fe-114">Abstraktní metody nemají žádnou implementaci, takže za definicí metody následuje středník namísto bloku normální metody.</span><span class="sxs-lookup"><span data-stu-id="d50fe-114">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="d50fe-115">Odvozené třídy abstraktní třídy musí implementovat všechny abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="d50fe-115">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="d50fe-116">Když abstraktní třída zdědí virtuální metodu ze základní třídy, abstraktní třída může přepsat virtuální metodu abstraktní metodou.</span><span class="sxs-lookup"><span data-stu-id="d50fe-116">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="d50fe-117">Například:</span><span class="sxs-lookup"><span data-stu-id="d50fe-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 <span data-ttu-id="d50fe-118">Pokud `virtual` je deklarována `abstract`metoda , je stále virtuální pro všechny třídy dědí z abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="d50fe-118">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="d50fe-119">Třída dědění abstraktní metody nemůže získat přístup k původní implementaci `DoWork` metody – `DoWork` v předchozím příkladu ve třídě F nelze volat třídu D. Tímto způsobem abstraktní třídy můžete vynutit odvozené třídy poskytnout nové implementace metody pro virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="d50fe-119">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="d50fe-120">Zapečetěné třídy a členové třídy</span><span class="sxs-lookup"><span data-stu-id="d50fe-120">Sealed Classes and Class Members</span></span>  
 <span data-ttu-id="d50fe-121">Třídy mohou být deklarovány jako [zapečetěné](../../language-reference/keywords/sealed.md) umístěním klíčového slova `sealed` před definici třídy.</span><span class="sxs-lookup"><span data-stu-id="d50fe-121">Classes can be declared as [sealed](../../language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="d50fe-122">Například:</span><span class="sxs-lookup"><span data-stu-id="d50fe-122">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 <span data-ttu-id="d50fe-123">Zapečetěnou třídu nelze použít jako základní třídu.</span><span class="sxs-lookup"><span data-stu-id="d50fe-123">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="d50fe-124">Z tohoto důvodu nemůže být také abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="d50fe-124">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="d50fe-125">Uzavřené třídy zabraňují odvození.</span><span class="sxs-lookup"><span data-stu-id="d50fe-125">Sealed classes prevent derivation.</span></span> <span data-ttu-id="d50fe-126">Vzhledem k tomu, že je nelze nikdy použít jako základní třídu, některé optimalizace běhu mohou volat členy zapečetěné třídy o něco rychleji.</span><span class="sxs-lookup"><span data-stu-id="d50fe-126">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="d50fe-127">Metoda, indexer, vlastnost nebo událost na odvozené třídy, která je přepsání virtuální člen základní třídy můžete deklarovat, že člen jako zapečetěné.</span><span class="sxs-lookup"><span data-stu-id="d50fe-127">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="d50fe-128">To neguje virtuální aspekt člena pro všechny další odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="d50fe-128">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="d50fe-129">Toho lze dosáhnout umístěním klíčového `sealed` slova před klíčové slovo [přepsání](../../language-reference/keywords/override.md) v deklaraci člena třídy.</span><span class="sxs-lookup"><span data-stu-id="d50fe-129">This is accomplished by putting the `sealed` keyword before the [override](../../language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="d50fe-130">Například:</span><span class="sxs-lookup"><span data-stu-id="d50fe-130">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="d50fe-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="d50fe-131">See also</span></span>

- [<span data-ttu-id="d50fe-132">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d50fe-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d50fe-133">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="d50fe-133">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="d50fe-134">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="d50fe-134">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="d50fe-135">Metody</span><span class="sxs-lookup"><span data-stu-id="d50fe-135">Methods</span></span>](./methods.md)
- [<span data-ttu-id="d50fe-136">Pole</span><span class="sxs-lookup"><span data-stu-id="d50fe-136">Fields</span></span>](./fields.md)
- [<span data-ttu-id="d50fe-137">Jak definovat abstraktní vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d50fe-137">How to define abstract properties</span></span>](./how-to-define-abstract-properties.md)
