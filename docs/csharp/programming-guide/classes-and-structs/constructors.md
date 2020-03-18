---
title: Konstruktory – programovací příručka Jazyka C#
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 8eedfaed111f01cc2ec55a2f42df66d4588bd42f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399789"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="996ad-102">Konstruktory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="996ad-102">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="996ad-103">Vždy, když je vytvořena [třída](../../language-reference/keywords/class.md) nebo [struktura,](../../language-reference/builtin-types/struct.md) jeho konstruktor se nazývá.</span><span class="sxs-lookup"><span data-stu-id="996ad-103">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="996ad-104">Třída nebo struktura může mít více konstruktorů, které berou různé argumenty.</span><span class="sxs-lookup"><span data-stu-id="996ad-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="996ad-105">Konstruktory umožňují programátorovi nastavit výchozí hodnoty, omezit vytváření instancí a psát kód, který je flexibilní a snadno čitelný.</span><span class="sxs-lookup"><span data-stu-id="996ad-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="996ad-106">Další informace a příklady naleznete [v tématu Použití konstruktorů](./using-constructors.md) a [konstruktorů instancí](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="996ad-106">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="996ad-107">Konstruktory bez parametrů</span><span class="sxs-lookup"><span data-stu-id="996ad-107">Parameterless constructors</span></span>
  
<span data-ttu-id="996ad-108">Pokud nezadáte konstruktor pro vaši třídu, C# vytvoří jeden ve výchozím nastavení, který konkretizuje objekt a nastaví členské proměnné na výchozí hodnoty uvedené v [výchozím hodnotách c# typy](../../language-reference/builtin-types/default-values.md) článku.</span><span class="sxs-lookup"><span data-stu-id="996ad-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span> <span data-ttu-id="996ad-109">Pokud nezadáte konstruktor pro strukturu, C# spoléhá na *implicitní konstruktor bez parametrů* automaticky inicializovat každé pole na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="996ad-109">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field to its default value.</span></span> <span data-ttu-id="996ad-110">Další informace a příklady naleznete v tématu [Instance konstruktory](instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="996ad-110">For more information and examples, see [Instance constructors](instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="996ad-111">Syntaxe konstruktoru</span><span class="sxs-lookup"><span data-stu-id="996ad-111">Constructor syntax</span></span>

<span data-ttu-id="996ad-112">Konstruktor je metoda, jejíž název je stejný jako název jeho typu.</span><span class="sxs-lookup"><span data-stu-id="996ad-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="996ad-113">Jeho podpis metody zahrnuje pouze název metody a seznam parametrů; neobsahuje návratový typ.</span><span class="sxs-lookup"><span data-stu-id="996ad-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="996ad-114">Následující příklad ukazuje konstruktor pro `Person`třídu s názvem .</span><span class="sxs-lookup"><span data-stu-id="996ad-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="996ad-115">Pokud konstruktor lze implementovat jako jeden příkaz, můžete použít [definici těla výrazu](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="996ad-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="996ad-116">Následující příklad definuje `Location` třídu, jejíž konstruktor má jeden parametr řetězce s názvem *name*.</span><span class="sxs-lookup"><span data-stu-id="996ad-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="996ad-117">Definice těla výrazu přiřadí `locationName` argument k poli.</span><span class="sxs-lookup"><span data-stu-id="996ad-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="996ad-118">Statické konstruktory</span><span class="sxs-lookup"><span data-stu-id="996ad-118">Static constructors</span></span>

<span data-ttu-id="996ad-119">V předchozích příkladech jsou zobrazeny všechny konstruktory instancí, které vytvářejí nový objekt.</span><span class="sxs-lookup"><span data-stu-id="996ad-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="996ad-120">Třída nebo struktura může mít také statický konstruktor, který inicializuje statické členy typu.</span><span class="sxs-lookup"><span data-stu-id="996ad-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="996ad-121">Statické konstruktory jsou bezparametrické.</span><span class="sxs-lookup"><span data-stu-id="996ad-121">Static constructors are parameterless.</span></span> <span data-ttu-id="996ad-122">Pokud nezadáte statický konstruktor pro inicializaci statických polí, kompilátor Jazyka C# inicializuje statická pole na výchozí hodnotu uvedenou v článku [Výchozí hodnoty c# typů.](../../language-reference/builtin-types/default-values.md)</span><span class="sxs-lookup"><span data-stu-id="996ad-122">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span>

<span data-ttu-id="996ad-123">Následující příklad používá statický konstruktor k inicializaci statického pole.</span><span class="sxs-lookup"><span data-stu-id="996ad-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="996ad-124">Můžete také definovat statický konstruktor s definicí těla výrazu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="996ad-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="996ad-125">Další informace a příklady naleznete [v tématu Statické konstruktory](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="996ad-125">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="996ad-126">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="996ad-126">In This Section</span></span>  
 [<span data-ttu-id="996ad-127">Použití konstruktorů</span><span class="sxs-lookup"><span data-stu-id="996ad-127">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="996ad-128">Konstruktory instancí</span><span class="sxs-lookup"><span data-stu-id="996ad-128">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="996ad-129">Soukromé konstruktory</span><span class="sxs-lookup"><span data-stu-id="996ad-129">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="996ad-130">Statické konstruktory</span><span class="sxs-lookup"><span data-stu-id="996ad-130">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="996ad-131">Jak napsat konstruktor kopie</span><span class="sxs-lookup"><span data-stu-id="996ad-131">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="996ad-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="996ad-132">See also</span></span>

- [<span data-ttu-id="996ad-133">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="996ad-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="996ad-134">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="996ad-134">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="996ad-135">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="996ad-135">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="996ad-136">Statické</span><span class="sxs-lookup"><span data-stu-id="996ad-136">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="996ad-137">Proč inicializační spustit v opačném pořadí jako konstruktory? První část</span><span class="sxs-lookup"><span data-stu-id="996ad-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
