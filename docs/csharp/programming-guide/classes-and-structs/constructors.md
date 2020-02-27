---
title: Konstruktory – C# Průvodce programováním
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 8eedfaed111f01cc2ec55a2f42df66d4588bd42f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626734"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="129be-102">Konstruktory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="129be-102">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="129be-103">Pokaždé, když se vytvoří [Třída](../../language-reference/keywords/class.md) nebo [Struktura](../../language-reference/builtin-types/struct.md) , zavolá se její konstruktor.</span><span class="sxs-lookup"><span data-stu-id="129be-103">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="129be-104">Třída nebo struktura může mít více konstruktorů, které přijímají různé argumenty.</span><span class="sxs-lookup"><span data-stu-id="129be-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="129be-105">Konstruktory umožňují programátorovi nastavit výchozí hodnoty, omezit vytváření instancí a napsat kód, který je flexibilní a snadno čitelný.</span><span class="sxs-lookup"><span data-stu-id="129be-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="129be-106">Další informace a příklady naleznete v tématu [using](./using-constructors.md) a [konstruktory instancí](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="129be-106">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="129be-107">Konstruktory bez parametrů</span><span class="sxs-lookup"><span data-stu-id="129be-107">Parameterless constructors</span></span>
  
<span data-ttu-id="129be-108">Pokud neposkytnete konstruktor pro třídu, C# vytvoří jeden ve výchozím nastavení, který vytvoří instanci objektu a nastaví proměnné členů na výchozí hodnoty, jak je uvedeno v článku [výchozí hodnoty C# typů](../../language-reference/builtin-types/default-values.md) .</span><span class="sxs-lookup"><span data-stu-id="129be-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span> <span data-ttu-id="129be-109">Pokud neposkytnete konstruktor pro vaši strukturu, C# spoléhá na *implicitní konstruktor bez parametrů* k automatickému inicializaci každého pole na jeho výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="129be-109">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field to its default value.</span></span> <span data-ttu-id="129be-110">Další informace a příklady naleznete v tématu [konstruktory instancí](instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="129be-110">For more information and examples, see [Instance constructors](instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="129be-111">Syntaxe konstruktoru</span><span class="sxs-lookup"><span data-stu-id="129be-111">Constructor syntax</span></span>

<span data-ttu-id="129be-112">Konstruktor je metoda, jejíž název je stejný jako název jeho typu.</span><span class="sxs-lookup"><span data-stu-id="129be-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="129be-113">Signatura metody obsahuje pouze název metody a její seznam parametrů; nezahrnuje návratový typ.</span><span class="sxs-lookup"><span data-stu-id="129be-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="129be-114">Následující příklad ukazuje konstruktor pro třídu s názvem `Person`.</span><span class="sxs-lookup"><span data-stu-id="129be-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="129be-115">Pokud konstruktor může být implementován jako jediný příkaz, můžete použít [definici těla výrazu](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="129be-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="129be-116">Následující příklad definuje třídu `Location`, jejíž konstruktor má jeden řetězcový parametr s názvem *Name*.</span><span class="sxs-lookup"><span data-stu-id="129be-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="129be-117">Definice těla výrazu přiřadí argument poli `locationName`.</span><span class="sxs-lookup"><span data-stu-id="129be-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="129be-118">Statické konstruktory</span><span class="sxs-lookup"><span data-stu-id="129be-118">Static constructors</span></span>

<span data-ttu-id="129be-119">Předchozí příklady mají všechny zobrazené konstruktory instancí, které vytvoří nový objekt.</span><span class="sxs-lookup"><span data-stu-id="129be-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="129be-120">Třída nebo struktura může mít také statický konstruktor, který inicializuje statické členy typu.</span><span class="sxs-lookup"><span data-stu-id="129be-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="129be-121">Statické konstruktory jsou bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="129be-121">Static constructors are parameterless.</span></span> <span data-ttu-id="129be-122">Pokud neposkytnete statický konstruktor pro inicializaci statických polí, C# kompilátor inicializuje statická pole na jejich výchozí hodnotu, jak je uvedeno v článku [výchozí hodnoty C# typů](../../language-reference/builtin-types/default-values.md) .</span><span class="sxs-lookup"><span data-stu-id="129be-122">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span>

<span data-ttu-id="129be-123">Následující příklad používá statický konstruktor pro inicializaci statického pole.</span><span class="sxs-lookup"><span data-stu-id="129be-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="129be-124">Můžete také definovat statický konstruktor pomocí definice těla výrazu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="129be-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="129be-125">Další informace a příklady naleznete v tématu [statické konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="129be-125">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="129be-126">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="129be-126">In This Section</span></span>  
 [<span data-ttu-id="129be-127">Použití konstruktorů</span><span class="sxs-lookup"><span data-stu-id="129be-127">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="129be-128">Konstruktory instancí</span><span class="sxs-lookup"><span data-stu-id="129be-128">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="129be-129">Soukromé konstruktory</span><span class="sxs-lookup"><span data-stu-id="129be-129">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="129be-130">Statické konstruktory</span><span class="sxs-lookup"><span data-stu-id="129be-130">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="129be-131">Zápis kopírovacího konstruktoru</span><span class="sxs-lookup"><span data-stu-id="129be-131">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="129be-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="129be-132">See also</span></span>

- [<span data-ttu-id="129be-133">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="129be-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="129be-134">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="129be-134">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="129be-135">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="129be-135">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="129be-136">static</span><span class="sxs-lookup"><span data-stu-id="129be-136">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="129be-137">Proč jsou Inicializátory spouštěny v opačném pořadí jako konstruktory? První část</span><span class="sxs-lookup"><span data-stu-id="129be-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
