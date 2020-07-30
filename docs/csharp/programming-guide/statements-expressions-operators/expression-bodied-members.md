---
title: Expression-těle Members – Průvodce programováním v C#
description: Přečtěte si o členech Expression-těle. Podívejte se na příklady kódu, které používají definici textu výrazu pro vlastnosti, konstruktory, finalizační metody a další.
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: e68e96e4aa3ff6a64590459a7197da1833e1a275
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381655"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="781c4-104">Expression-těle členové (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="781c4-104">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="781c4-105">Definice textu výrazu umožňují poskytovat implementaci člena ve velmi stručné a čitelné podobě.</span><span class="sxs-lookup"><span data-stu-id="781c4-105">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="781c4-106">Definici těla výrazu můžete použít vždy, když logika pro libovolný podporovaný člen, jako je například metoda nebo vlastnost, se skládá z jednoho výrazu.</span><span class="sxs-lookup"><span data-stu-id="781c4-106">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="781c4-107">Definice těla výrazu má následující obecnou syntaxi:</span><span class="sxs-lookup"><span data-stu-id="781c4-107">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="781c4-108">*výraz* WHERE je platný výraz.</span><span class="sxs-lookup"><span data-stu-id="781c4-108">where *expression* is a valid expression.</span></span>

<span data-ttu-id="781c4-109">Pro metody a vlastnosti jen pro čtení v C# 6 byly zavedeny podpory pro definice těla výrazu a rozšířily se v C# 7,0.</span><span class="sxs-lookup"><span data-stu-id="781c4-109">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="781c4-110">Definice textu výrazu lze použít s členy typu uvedenými v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="781c4-110">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="781c4-111">Člen</span><span class="sxs-lookup"><span data-stu-id="781c4-111">Member</span></span>  |<span data-ttu-id="781c4-112">Podporováno pro...</span><span class="sxs-lookup"><span data-stu-id="781c4-112">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="781c4-113">Metoda</span><span class="sxs-lookup"><span data-stu-id="781c4-113">Method</span></span>](#methods)  |<span data-ttu-id="781c4-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="781c4-114">C# 6</span></span> |
|[<span data-ttu-id="781c4-115">Vlastnost jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="781c4-115">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="781c4-116">C# 6</span><span class="sxs-lookup"><span data-stu-id="781c4-116">C# 6</span></span>  |
|[<span data-ttu-id="781c4-117">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="781c4-117">Property</span></span>](#properties)  |<span data-ttu-id="781c4-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="781c4-118">C# 7.0</span></span> |
|[<span data-ttu-id="781c4-119">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="781c4-119">Constructor</span></span>](#constructors)   |<span data-ttu-id="781c4-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="781c4-120">C# 7.0</span></span> |
|[<span data-ttu-id="781c4-121">Finalizační metodu</span><span class="sxs-lookup"><span data-stu-id="781c4-121">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="781c4-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="781c4-122">C# 7.0</span></span> |
|[<span data-ttu-id="781c4-123">Indexer</span><span class="sxs-lookup"><span data-stu-id="781c4-123">Indexer</span></span>](#indexers)       |<span data-ttu-id="781c4-124">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="781c4-124">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="781c4-125">Metody</span><span class="sxs-lookup"><span data-stu-id="781c4-125">Methods</span></span>

<span data-ttu-id="781c4-126">Metoda těle výrazu se skládá z jednoho výrazu, který vrací hodnotu, jejíž typ odpovídá návratového typu metody, nebo pro metody, které vracejí `void` , které provádí určitou operaci.</span><span class="sxs-lookup"><span data-stu-id="781c4-126">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="781c4-127">Například typy, které přepisují <xref:System.Object.ToString%2A> metodu obvykle zahrnují jeden výraz, který vrací řetězcovou reprezentaci aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="781c4-127">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="781c4-128">Následující příklad definuje `Person` třídu, která přepisuje <xref:System.Object.ToString%2A> metodu pomocí definice těla výrazu.</span><span class="sxs-lookup"><span data-stu-id="781c4-128">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="781c4-129">Definuje také `DisplayName` metodu, která zobrazí název konzole.</span><span class="sxs-lookup"><span data-stu-id="781c4-129">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="781c4-130">Všimněte si, že `return` klíčové slovo se v `ToString` definici těla výrazu nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="781c4-130">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="781c4-131">Další informace naleznete v tématu [metody (Průvodce programováním v C#)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="781c4-131">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="781c4-132">Vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="781c4-132">Read-only properties</span></span>

<span data-ttu-id="781c4-133">Počínaje jazykem C# 6 můžete použít definici textu výrazu k implementaci vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="781c4-133">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="781c4-134">K tomu použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="781c4-134">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="781c4-135">Následující příklad definuje `Location` třídu, jejíž vlastnost jen pro čtení `Name` je implementována jako definice těla výrazu, která vrací hodnotu soukromého `locationName` pole:</span><span class="sxs-lookup"><span data-stu-id="781c4-135">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="781c4-136">Další informace o vlastnostech naleznete v tématu [Properties (Průvodce programováním v C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="781c4-136">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="781c4-137">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="781c4-137">Properties</span></span>

<span data-ttu-id="781c4-138">Počínaje jazykem C# 7,0 můžete použít definice těla výrazu k implementaci vlastností `get` a `set` přístupových objektů.</span><span class="sxs-lookup"><span data-stu-id="781c4-138">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="781c4-139">Následující příklad ukazuje, jak to provést:</span><span class="sxs-lookup"><span data-stu-id="781c4-139">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="781c4-140">Další informace o vlastnostech naleznete v tématu [Properties (Průvodce programováním v C#)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="781c4-140">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="781c4-141">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="781c4-141">Constructors</span></span>

<span data-ttu-id="781c4-142">Definice těla výrazu pro konstruktor se obvykle skládá z jednoho výrazu přiřazení nebo volání metody, které zpracovává argumenty konstruktoru nebo inicializuje stav instance.</span><span class="sxs-lookup"><span data-stu-id="781c4-142">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="781c4-143">Následující příklad definuje třídu, `Location` jejíž konstruktor má jeden řetězcový parametr s názvem *Name*.</span><span class="sxs-lookup"><span data-stu-id="781c4-143">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="781c4-144">Definice těla výrazu přiřadí argument `Name` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="781c4-144">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="781c4-145">Další informace naleznete v tématu [konstruktory (Průvodce programováním v C#)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="781c4-145">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="781c4-146">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="781c4-146">Finalizers</span></span>

<span data-ttu-id="781c4-147">Definice těla výrazu pro finalizační metodu obvykle obsahuje příkazy vyčištění, například příkazy, které uvolní nespravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="781c4-147">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="781c4-148">Následující příklad definuje finalizační metodu, která používá definici těla výrazu k označení toho, že finalizační metoda byla volána.</span><span class="sxs-lookup"><span data-stu-id="781c4-148">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="781c4-149">Další informace naleznete v tématu [finalizační metody (Průvodce programováním v C#)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="781c4-149">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="781c4-150">Indexery</span><span class="sxs-lookup"><span data-stu-id="781c4-150">Indexers</span></span>

<span data-ttu-id="781c4-151">Podobně jako u vlastností jsou indexery `get` a `set` přistupující objekty tvořeny definicemi těla výrazu `get` , pokud se přistupující objekt skládá z jediného výrazu, který vrací hodnotu nebo `set` přistupující objekt provádí jednoduché přiřazení.</span><span class="sxs-lookup"><span data-stu-id="781c4-151">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="781c4-152">Následující příklad definuje třídu s názvem `Sports` , která obsahuje interní <xref:System.String> pole, které obsahuje názvy pro řadu sportovních.</span><span class="sxs-lookup"><span data-stu-id="781c4-152">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="781c4-153">Indexer `get` i `set` přistupující objekty jsou implementovány jako definice textu výrazu.</span><span class="sxs-lookup"><span data-stu-id="781c4-153">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="781c4-154">Další informace najdete v tématu [indexery (Průvodce programováním v C#)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="781c4-154">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
