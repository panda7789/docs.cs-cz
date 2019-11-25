---
title: Abstraktní a zapečetěné třídy a členy třídy C# – Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- abstract classes [C#]
- sealed classes [C#]
- C# language, abstract classes
- C# language, sealed
ms.assetid: 99aa52f7-b435-43f9-936e-2470af734c4e
ms.openlocfilehash: 97b367b5c3d09087541ee206a2899a7aefd95305
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971353"
---
# <a name="abstract-and-sealed-classes-and-class-members-c-programming-guide"></a><span data-ttu-id="fdf89-102">Abstraktní a uzavřené třídy a jejich členové (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="fdf89-102">Abstract and Sealed Classes and Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="fdf89-103">Klíčové slovo [abstract](../../language-reference/keywords/abstract.md) umožňuje vytvářet třídy a členy [třídy](../../language-reference/keywords/class.md) , které jsou neúplné a které musí být implementovány v odvozené třídě.</span><span class="sxs-lookup"><span data-stu-id="fdf89-103">The [abstract](../../language-reference/keywords/abstract.md) keyword enables you to create classes and [class](../../language-reference/keywords/class.md) members that are incomplete and must be implemented in a derived class.</span></span>  
  
 <span data-ttu-id="fdf89-104">Klíčové slovo [sealed](../../language-reference/keywords/sealed.md) umožňuje zabránit dědění třídy nebo určitých členů třídy, které byly dříve označeny jako [virtuální](../../language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="fdf89-104">The [sealed](../../language-reference/keywords/sealed.md) keyword enables you to prevent the inheritance of a class or certain class members that were previously marked [virtual](../../language-reference/keywords/virtual.md).</span></span>  
  
## <a name="abstract-classes-and-class-members"></a><span data-ttu-id="fdf89-105">Abstraktní třídy a členy třídy</span><span class="sxs-lookup"><span data-stu-id="fdf89-105">Abstract Classes and Class Members</span></span>  
 <span data-ttu-id="fdf89-106">Třídy lze deklarovat jako abstraktní vložením klíčového slova `abstract` před definici třídy.</span><span class="sxs-lookup"><span data-stu-id="fdf89-106">Classes can be declared as abstract by putting the keyword `abstract` before the class definition.</span></span> <span data-ttu-id="fdf89-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fdf89-107">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#13)]  
  
 <span data-ttu-id="fdf89-108">Nelze vytvořit instanci abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="fdf89-108">An abstract class cannot be instantiated.</span></span> <span data-ttu-id="fdf89-109">Účelem abstraktní třídy je poskytnutí společné definice základní třídy, kterou může sdílet více odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="fdf89-109">The purpose of an abstract class is to provide a common definition of a base class that multiple derived classes can share.</span></span> <span data-ttu-id="fdf89-110">Knihovna tříd může například definovat abstraktní třídu, která se používá jako parametr pro mnoho jeho funkcí, a vyžadovat programátory, kteří používají tuto knihovnu k poskytnutí vlastní implementace třídy vytvořením odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="fdf89-110">For example, a class library may define an abstract class that is used as a parameter to many of its functions, and require programmers using that library to provide their own implementation of the class by creating a derived class.</span></span>  
  
 <span data-ttu-id="fdf89-111">Abstraktní třídy mohou také definovat abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="fdf89-111">Abstract classes may also define abstract methods.</span></span> <span data-ttu-id="fdf89-112">To je dosaženo přidáním klíčového slova `abstract` před návratový typ metody.</span><span class="sxs-lookup"><span data-stu-id="fdf89-112">This is accomplished by adding the keyword `abstract` before the return type of the method.</span></span> <span data-ttu-id="fdf89-113">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fdf89-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#14)]  
  
 <span data-ttu-id="fdf89-114">Abstraktní metody nemají žádnou implementaci, proto je jako definice metody následován středníkem namísto bloku normální metody.</span><span class="sxs-lookup"><span data-stu-id="fdf89-114">Abstract methods have no implementation, so the method definition is followed by a semicolon instead of a normal method block.</span></span> <span data-ttu-id="fdf89-115">Odvozené třídy abstraktní třídy musí implementovat všechny abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="fdf89-115">Derived classes of the abstract class must implement all abstract methods.</span></span> <span data-ttu-id="fdf89-116">Pokud abstraktní třída dědí virtuální metodu ze základní třídy, abstraktní třída může přepsat virtuální metodu abstraktní metodou.</span><span class="sxs-lookup"><span data-stu-id="fdf89-116">When an abstract class inherits a virtual method from a base class, the abstract class can override the virtual method with an abstract method.</span></span> <span data-ttu-id="fdf89-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fdf89-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#15)]  
  
 <span data-ttu-id="fdf89-118">Je-li metoda `virtual` deklarována `abstract`, je stále virtuální pro jakoukoliv třídu, která dědí z abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="fdf89-118">If a `virtual` method is declared `abstract`, it is still virtual to any class inheriting from the abstract class.</span></span> <span data-ttu-id="fdf89-119">Třída, která dědí abstraktní metodu, nemůže získat přístup k původní implementaci metody – v předchozím příkladu `DoWork` ve třídě F nemůže volat `DoWork` na třídu D. Tímto způsobem abstraktní třída může vynutit odvozené třídy, aby poskytovala nové implementace metod pro virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="fdf89-119">A class inheriting an abstract method cannot access the original implementation of the method—in the previous example, `DoWork` on class F cannot call `DoWork` on class D. In this way, an abstract class can force derived classes to provide new method implementations for virtual methods.</span></span>  
  
## <a name="sealed-classes-and-class-members"></a><span data-ttu-id="fdf89-120">Zapečetěné třídy a členy třídy</span><span class="sxs-lookup"><span data-stu-id="fdf89-120">Sealed Classes and Class Members</span></span>  
 <span data-ttu-id="fdf89-121">Třídy lze deklarovat jako [zapečetěné](../../language-reference/keywords/sealed.md) vložením klíčového slova `sealed` před definici třídy.</span><span class="sxs-lookup"><span data-stu-id="fdf89-121">Classes can be declared as [sealed](../../language-reference/keywords/sealed.md) by putting the keyword `sealed` before the class definition.</span></span> <span data-ttu-id="fdf89-122">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fdf89-122">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#16)]  
  
 <span data-ttu-id="fdf89-123">Zapečetěná třída se nedá použít jako základní třída.</span><span class="sxs-lookup"><span data-stu-id="fdf89-123">A sealed class cannot be used as a base class.</span></span> <span data-ttu-id="fdf89-124">Z tohoto důvodu nemůže být zároveň abstraktní třídou.</span><span class="sxs-lookup"><span data-stu-id="fdf89-124">For this reason, it cannot also be an abstract class.</span></span> <span data-ttu-id="fdf89-125">Zapečetěné třídy brání odvození.</span><span class="sxs-lookup"><span data-stu-id="fdf89-125">Sealed classes prevent derivation.</span></span> <span data-ttu-id="fdf89-126">Vzhledem k tomu, že je nelze nikdy použít jako základní třídu, mohou některé optimalizace za běhu volat členy zapečetěné třídy trochu rychleji.</span><span class="sxs-lookup"><span data-stu-id="fdf89-126">Because they can never be used as a base class, some run-time optimizations can make calling sealed class members slightly faster.</span></span>  
  
 <span data-ttu-id="fdf89-127">Metoda, indexer, vlastnost nebo událost v odvozené třídě, která přepisuje virtuální člen základní třídy, může deklarovat tento člen jako zapečetěný.</span><span class="sxs-lookup"><span data-stu-id="fdf89-127">A method, indexer, property, or event, on a derived class that is overriding a virtual member of the base class can declare that member as sealed.</span></span> <span data-ttu-id="fdf89-128">Tato negace je virtuální aspekt člena pro jakoukoliv další odvozenou třídu.</span><span class="sxs-lookup"><span data-stu-id="fdf89-128">This negates the virtual aspect of the member for any further derived class.</span></span> <span data-ttu-id="fdf89-129">To je dosaženo vložením klíčového slova `sealed` před klíčové slovo [override](../../language-reference/keywords/override.md) v deklaraci člena třídy.</span><span class="sxs-lookup"><span data-stu-id="fdf89-129">This is accomplished by putting the `sealed` keyword before the [override](../../language-reference/keywords/override.md) keyword in the class member declaration.</span></span> <span data-ttu-id="fdf89-130">Příklad:</span><span class="sxs-lookup"><span data-stu-id="fdf89-130">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="fdf89-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdf89-131">See also</span></span>

- [<span data-ttu-id="fdf89-132">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fdf89-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fdf89-133">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="fdf89-133">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="fdf89-134">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="fdf89-134">Inheritance</span></span>](./inheritance.md)
- [<span data-ttu-id="fdf89-135">Metody</span><span class="sxs-lookup"><span data-stu-id="fdf89-135">Methods</span></span>](./methods.md)
- [<span data-ttu-id="fdf89-136">Pole</span><span class="sxs-lookup"><span data-stu-id="fdf89-136">Fields</span></span>](./fields.md)
- [<span data-ttu-id="fdf89-137">Definování abstraktních vlastností</span><span class="sxs-lookup"><span data-stu-id="fdf89-137">How to define abstract properties</span></span>](./how-to-define-abstract-properties.md)
