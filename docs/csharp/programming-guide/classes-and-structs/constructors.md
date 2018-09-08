---
title: Konstruktory (Průvodce programováním v C#)
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 3d07fe5f6164885a994838376887edccc260e291
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185334"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="45bf3-102">Konstruktory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="45bf3-102">Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="45bf3-103">Pokaždé, když se [třídy](../../../csharp/language-reference/keywords/class.md) nebo [– struktura](../../../csharp/language-reference/keywords/struct.md) je vytvořen, se nazývá konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="45bf3-103">Whenever a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="45bf3-104">Třídy nebo struktury může mít více konstruktorů, které přijímají různé argumenty.</span><span class="sxs-lookup"><span data-stu-id="45bf3-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="45bf3-105">Konstruktory povolit programátorovi, aby nastavení výchozích hodnot, omezení vytváření instancí a napsat kód, který je flexibilní a snadno čitelný.</span><span class="sxs-lookup"><span data-stu-id="45bf3-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="45bf3-106">Další informace a příklady najdete v tématu [pomocí konstruktorů](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) a [konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="45bf3-106">For more information and examples, see [Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) and [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="default-constructors"></a><span data-ttu-id="45bf3-107">Výchozí konstruktory</span><span class="sxs-lookup"><span data-stu-id="45bf3-107">Default constructors</span></span>
  
<span data-ttu-id="45bf3-108">Pokud nezadáte konstruktor pro třídu, C# vytvoří ve výchozím nastavení vytvoří instanci objektu, který nastaví proměnné členů na výchozí hodnoty, jak je uvedeno v [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="45bf3-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="45bf3-109">Pokud nezadáte konstruktor pro vaše struktura, C# spoléhá na *implicitní výchozí konstruktor* automaticky inicializovat každé pole typu hodnota na výchozí hodnotu, jak je uvedeno v [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="45bf3-109">If you don't provide a constructor for your struct, C# relies on an *implicit default constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="45bf3-110">Další informace a příklady najdete v tématu [konstruktory instancí](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="45bf3-110">For more information and examples, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="45bf3-111">Syntaxe konstruktoru</span><span class="sxs-lookup"><span data-stu-id="45bf3-111">Constructor syntax</span></span>

<span data-ttu-id="45bf3-112">Konstruktor je metoda, jejíž název je stejný jako název jeho typu.</span><span class="sxs-lookup"><span data-stu-id="45bf3-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="45bf3-113">Jeho podpis metody zahrnuje pouze název metody a jejího seznamu parametrů; Návratový typ neobsahuje.</span><span class="sxs-lookup"><span data-stu-id="45bf3-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="45bf3-114">Následující příklad ukazuje konstruktor pro třídu s názvem `Person`.</span><span class="sxs-lookup"><span data-stu-id="45bf3-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="45bf3-115">Pokud konstruktor je možné implementovat jako jeden příkaz, můžete použít [definice těla výrazu](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="45bf3-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="45bf3-116">Následující příklad definuje `Location` třídy, jejíž konstruktor má jeden řetězcový parametr s názvem *název*.</span><span class="sxs-lookup"><span data-stu-id="45bf3-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="45bf3-117">Definice textu výrazu přiřadí argument `locationName` pole.</span><span class="sxs-lookup"><span data-stu-id="45bf3-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="45bf3-118">Statické konstruktory</span><span class="sxs-lookup"><span data-stu-id="45bf3-118">Static constructors</span></span>

<span data-ttu-id="45bf3-119">V předchozích příkladech mají všechny zobrazené instančních konstruktorech, které vytvoří nový objekt.</span><span class="sxs-lookup"><span data-stu-id="45bf3-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="45bf3-120">Statický konstruktor, který inicializuje statické členy typu může mít také třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="45bf3-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="45bf3-121">Statické konstruktory jsou konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="45bf3-121">Static constructors are parameterless.</span></span> <span data-ttu-id="45bf3-122">Pokud nezadáte statický konstruktor k inicializaci statická pole, kompilátor jazyka C# poskytne výchozí statický konstruktor, který inicializuje statická pole na výchozí hodnoty, jak je uvedeno v [tabulka výchozích hodnot](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="45bf3-122">If you don't provide a static constructor to initialize static fields, the C# compiler will supply a default static constructor that initializes static fields to their default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> 

<span data-ttu-id="45bf3-123">Následující příklad používá statický konstruktor k inicializaci statické pole.</span><span class="sxs-lookup"><span data-stu-id="45bf3-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="45bf3-124">Můžete také definovat statický konstruktor s definici tělo výrazu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="45bf3-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="45bf3-125">Další informace a příklady najdete v tématu [statické konstruktory](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="45bf3-125">For more information and examples, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45bf3-126">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="45bf3-126">In This Section</span></span>  
 [<span data-ttu-id="45bf3-127">Použití konstruktorů</span><span class="sxs-lookup"><span data-stu-id="45bf3-127">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [<span data-ttu-id="45bf3-128">Konstruktory instancí</span><span class="sxs-lookup"><span data-stu-id="45bf3-128">Instance Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [<span data-ttu-id="45bf3-129">Soukromé konstruktory</span><span class="sxs-lookup"><span data-stu-id="45bf3-129">Private Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [<span data-ttu-id="45bf3-130">Statické konstruktory</span><span class="sxs-lookup"><span data-stu-id="45bf3-130">Static Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [<span data-ttu-id="45bf3-131">Postupy: Zápis kopírovacího konstruktoru</span><span class="sxs-lookup"><span data-stu-id="45bf3-131">How to: Write a Copy Constructor</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="45bf3-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="45bf3-132">See Also</span></span>

- [<span data-ttu-id="45bf3-133">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="45bf3-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="45bf3-134">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="45bf3-134">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="45bf3-135">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="45bf3-135">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [<span data-ttu-id="45bf3-136">static</span><span class="sxs-lookup"><span data-stu-id="45bf3-136">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
- [<span data-ttu-id="45bf3-137">Proč inicializátory spustit v opačném pořadí jako konstruktory? První část</span><span class="sxs-lookup"><span data-stu-id="45bf3-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
