---
title: Členové s výrazem - Programovací příručka Jazyka C#
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: f212bb707d3dd2d4a7cc917d335a83cff01ed0cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711984"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="71803-102">Členové s výrazem (průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="71803-102">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="71803-103">Definice těla výrazu umožňují poskytnout implementaci člena ve velmi stručné a čitelné podobě.</span><span class="sxs-lookup"><span data-stu-id="71803-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="71803-104">Definici těla výrazu můžete použít vždy, když se logika pro libovolný podporovaný člen, například metoda nebo vlastnost, skládá z jednoho výrazu.</span><span class="sxs-lookup"><span data-stu-id="71803-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="71803-105">Definice těla výrazu má následující obecnou syntaxi:</span><span class="sxs-lookup"><span data-stu-id="71803-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="71803-106">kde *výraz* je platný výraz.</span><span class="sxs-lookup"><span data-stu-id="71803-106">where *expression* is a valid expression.</span></span>

<span data-ttu-id="71803-107">Podpora pro definice těla výrazu byla zavedena pro metody a vlastnosti jen pro čtení v C# 6 a byla rozšířena v C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="71803-107">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="71803-108">Definice těla výrazu lze použít s členy typu uvedenými v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="71803-108">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="71803-109">Člen</span><span class="sxs-lookup"><span data-stu-id="71803-109">Member</span></span>  |<span data-ttu-id="71803-110">Podporováno od...</span><span class="sxs-lookup"><span data-stu-id="71803-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="71803-111">Metoda</span><span class="sxs-lookup"><span data-stu-id="71803-111">Method</span></span>](#methods)  |<span data-ttu-id="71803-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="71803-112">C# 6</span></span> |
|[<span data-ttu-id="71803-113">Vlastnost jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="71803-113">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="71803-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="71803-114">C# 6</span></span>  |
|[<span data-ttu-id="71803-115">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="71803-115">Property</span></span>](#properties)  |<span data-ttu-id="71803-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="71803-116">C# 7.0</span></span> |
|[<span data-ttu-id="71803-117">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="71803-117">Constructor</span></span>](#constructors)   |<span data-ttu-id="71803-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="71803-118">C# 7.0</span></span> |
|[<span data-ttu-id="71803-119">Finalizační metoda</span><span class="sxs-lookup"><span data-stu-id="71803-119">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="71803-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="71803-120">C# 7.0</span></span> |
|[<span data-ttu-id="71803-121">Indexer</span><span class="sxs-lookup"><span data-stu-id="71803-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="71803-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="71803-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="71803-123">Metody</span><span class="sxs-lookup"><span data-stu-id="71803-123">Methods</span></span>

<span data-ttu-id="71803-124">Metoda s tělovým výrazem se skládá z jednoho výrazu, který vrací hodnotu, jejíž `void`typ odpovídá návratovému typu metody, nebo pro metody, které vracejí , které provádějí některé operace.</span><span class="sxs-lookup"><span data-stu-id="71803-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="71803-125">Například typy, které <xref:System.Object.ToString%2A> přepíší metodu obvykle obsahují jeden výraz, který vrací řetězcovou reprezentaci aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="71803-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="71803-126">Následující příklad definuje `Person` třídu, která <xref:System.Object.ToString%2A> přepíše metodu s definicí těla výrazu.</span><span class="sxs-lookup"><span data-stu-id="71803-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="71803-127">Definuje také metodu, `DisplayName` která zobrazuje název konzoly.</span><span class="sxs-lookup"><span data-stu-id="71803-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="71803-128">Všimněte `return` si, že klíčové `ToString` slovo se nepoužívá v definici těla výrazu.</span><span class="sxs-lookup"><span data-stu-id="71803-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="71803-129">Další informace naleznete [v tématu Metody (C# Programming Guide)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="71803-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="71803-130">Vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="71803-130">Read-only properties</span></span>

<span data-ttu-id="71803-131">Počínaje C# 6, můžete použít definici těla výrazu k implementaci vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="71803-131">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="71803-132">Chcete-li to provést, použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="71803-132">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="71803-133">Následující příklad definuje `Location` třídu, jejíž vlastnost jen pro `Name` čtení je implementována `locationName` jako definice těla výrazu, která vrací hodnotu soukromého pole:</span><span class="sxs-lookup"><span data-stu-id="71803-133">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="71803-134">Další informace o vlastnostech naleznete v [tématu Vlastnosti (C# Programming Guide)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="71803-134">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="71803-135">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="71803-135">Properties</span></span>

<span data-ttu-id="71803-136">Počínaje C# 7.0, můžete použít definice těla `get` `set` výrazu k implementaci vlastnosti a přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="71803-136">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="71803-137">Následující příklad ukazuje, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="71803-137">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="71803-138">Další informace o vlastnostech naleznete v [tématu Vlastnosti (C# Programming Guide)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="71803-138">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="71803-139">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="71803-139">Constructors</span></span>

<span data-ttu-id="71803-140">Definice těla výrazu pro konstruktor se obvykle skládá z jednoho výrazu přiřazení nebo volání metody, které zpracovává argumenty konstruktoru nebo inicializuje stav instance.</span><span class="sxs-lookup"><span data-stu-id="71803-140">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="71803-141">Následující příklad definuje `Location` třídu, jejíž konstruktor má jeden parametr řetězce s názvem *name*.</span><span class="sxs-lookup"><span data-stu-id="71803-141">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="71803-142">Definice těla výrazu přiřadí `Name` argument vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="71803-142">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="71803-143">Další informace naleznete v [tématu Konstruktory (C# Programovací průvodce)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="71803-143">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="71803-144">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="71803-144">Finalizers</span></span>

<span data-ttu-id="71803-145">Definice těla výrazu pro finalizační metodu obvykle obsahuje příkazy vyčištění, jako jsou například příkazy, které vydávají nespravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="71803-145">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="71803-146">Následující příklad definuje finalizační metodu, která používá definici těla výrazu k označení, že byla volána finalizační metoda.</span><span class="sxs-lookup"><span data-stu-id="71803-146">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="71803-147">Další informace naleznete v tématu [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="71803-147">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="71803-148">Indexery</span><span class="sxs-lookup"><span data-stu-id="71803-148">Indexers</span></span>

<span data-ttu-id="71803-149">Stejně jako s `get` `set` vlastnostmi, indexer a přístupové `get` objekty se skládají z definice těla výrazu, pokud se přistupující objekt skládá z jednoho výrazu, který vrací hodnotu nebo `set` přistupující objekt provádí jednoduché přiřazení.</span><span class="sxs-lookup"><span data-stu-id="71803-149">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="71803-150">Následující příklad definuje třídu `Sports` s názvem, která obsahuje vnitřní <xref:System.String> pole, které obsahuje názvy několika sportů.</span><span class="sxs-lookup"><span data-stu-id="71803-150">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="71803-151">Indexer `get` a `set` přistupující servery jsou implementovány jako definice těla výrazu.</span><span class="sxs-lookup"><span data-stu-id="71803-151">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="71803-152">Další informace naleznete v tématu [Indexery (C# Programming Guide)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="71803-152">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
