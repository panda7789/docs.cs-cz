---
title: Expression – těle členové – C# Průvodce programováním
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
ms.openlocfilehash: f212bb707d3dd2d4a7cc917d335a83cff01ed0cf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711984"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="ea5a4-102">Výrazy – těle členové (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="ea5a4-102">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="ea5a4-103">Definice textu výrazu umožňují poskytovat implementaci člena ve velmi stručné a čitelné podobě.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="ea5a4-104">Definici těla výrazu můžete použít vždy, když logika pro libovolný podporovaný člen, jako je například metoda nebo vlastnost, se skládá z jednoho výrazu.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="ea5a4-105">Definice těla výrazu má následující obecnou syntaxi:</span><span class="sxs-lookup"><span data-stu-id="ea5a4-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="ea5a4-106">*výraz* WHERE je platný výraz.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-106">where *expression* is a valid expression.</span></span>

<span data-ttu-id="ea5a4-107">Pro metody a vlastnosti jen pro čtení v C# 6 byly zavedeny podpory definic těla výrazů a v C# 7,0 byly rozbaleny.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-107">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="ea5a4-108">Definice textu výrazu lze použít s členy typu uvedenými v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="ea5a4-108">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="ea5a4-109">Člen</span><span class="sxs-lookup"><span data-stu-id="ea5a4-109">Member</span></span>  |<span data-ttu-id="ea5a4-110">Podporováno pro...</span><span class="sxs-lookup"><span data-stu-id="ea5a4-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="ea5a4-111">– Metoda</span><span class="sxs-lookup"><span data-stu-id="ea5a4-111">Method</span></span>](#methods)  |<span data-ttu-id="ea5a4-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="ea5a4-112">C# 6</span></span> |
|[<span data-ttu-id="ea5a4-113">Vlastnost jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ea5a4-113">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="ea5a4-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="ea5a4-114">C# 6</span></span>  |
|[<span data-ttu-id="ea5a4-115">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ea5a4-115">Property</span></span>](#properties)  |<span data-ttu-id="ea5a4-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="ea5a4-116">C# 7.0</span></span> |
|[<span data-ttu-id="ea5a4-117">BeginRequestEventArgs</span><span class="sxs-lookup"><span data-stu-id="ea5a4-117">Constructor</span></span>](#constructors)   |<span data-ttu-id="ea5a4-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="ea5a4-118">C# 7.0</span></span> |
|[<span data-ttu-id="ea5a4-119">Finalizační metodu</span><span class="sxs-lookup"><span data-stu-id="ea5a4-119">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="ea5a4-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="ea5a4-120">C# 7.0</span></span> |
|[<span data-ttu-id="ea5a4-121">Indexer</span><span class="sxs-lookup"><span data-stu-id="ea5a4-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="ea5a4-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="ea5a4-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="ea5a4-123">Metody</span><span class="sxs-lookup"><span data-stu-id="ea5a4-123">Methods</span></span>

<span data-ttu-id="ea5a4-124">Metoda těle výrazu se skládá z jednoho výrazu, který vrací hodnotu, jejíž typ odpovídá návratový typ metody, nebo, pro metody, které vracejí `void`, které provádí určitou operaci.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="ea5a4-125">Například typy, které přepisují metodu <xref:System.Object.ToString%2A> obvykle zahrnují jeden výraz, který vrací řetězcovou reprezentaci aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="ea5a4-126">Následující příklad definuje třídu `Person`, která přepisuje metodu <xref:System.Object.ToString%2A> pomocí definice těla výrazu.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="ea5a4-127">Definuje také metodu `DisplayName`, která zobrazuje název konzoly.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="ea5a4-128">Všimněte si, že klíčové slovo `return` se v definici těla výrazu `ToString` nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="ea5a4-129">Další informace naleznete v tématu [metody (C# Průvodce programováním)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="ea5a4-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="ea5a4-130">Vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ea5a4-130">Read-only properties</span></span>

<span data-ttu-id="ea5a4-131">Počínaje C# 6 můžete použít definici textu výrazu k implementaci vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-131">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="ea5a4-132">K tomu použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="ea5a4-132">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="ea5a4-133">Následující příklad definuje třídu `Location`, jejíž vlastnost `Name` jen pro čtení je implementována jako definice těla výrazu, která vrací hodnotu soukromého `locationName` pole:</span><span class="sxs-lookup"><span data-stu-id="ea5a4-133">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="ea5a4-134">Další informace o vlastnostech naleznete v tématu [vlastnosti (C# Průvodce programováním)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="ea5a4-134">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="ea5a4-135">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ea5a4-135">Properties</span></span>

<span data-ttu-id="ea5a4-136">Počínaje verzí C# 7,0 můžete použít definice těla výrazu k implementaci `get` vlastností a přístupových objektů `set`.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-136">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="ea5a4-137">Následující příklad ukazuje, jak to provést:</span><span class="sxs-lookup"><span data-stu-id="ea5a4-137">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="ea5a4-138">Další informace o vlastnostech naleznete v tématu [vlastnosti (C# Průvodce programováním)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="ea5a4-138">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="ea5a4-139">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="ea5a4-139">Constructors</span></span>

<span data-ttu-id="ea5a4-140">Definice těla výrazu pro konstruktor se obvykle skládá z jednoho výrazu přiřazení nebo volání metody, které zpracovává argumenty konstruktoru nebo inicializuje stav instance.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-140">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="ea5a4-141">Následující příklad definuje třídu `Location`, jejíž konstruktor má jeden řetězcový parametr s názvem *Name*.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-141">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="ea5a4-142">Definice těla výrazu přiřadí argument vlastnosti `Name`.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-142">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="ea5a4-143">Další informace naleznete v tématu [konstruktory (C# Průvodce programováním)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="ea5a4-143">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="ea5a4-144">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="ea5a4-144">Finalizers</span></span>

<span data-ttu-id="ea5a4-145">Definice těla výrazu pro finalizační metodu obvykle obsahuje příkazy vyčištění, například příkazy, které uvolní nespravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-145">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="ea5a4-146">Následující příklad definuje finalizační metodu, která používá definici těla výrazu k označení toho, že finalizační metoda byla volána.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-146">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="ea5a4-147">Další informace naleznete v tématu [finalizační metody (C# Průvodce programováním)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="ea5a4-147">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="ea5a4-148">Indexery</span><span class="sxs-lookup"><span data-stu-id="ea5a4-148">Indexers</span></span>

<span data-ttu-id="ea5a4-149">Podobně jako u vlastností, indexerů `get` a přistupujících objektů `set` se skládají z definic textu výrazu, pokud se `get` přistupující objekt skládá z jediného výrazu, který vrací hodnotu nebo objekt pro přístup k `set` provádí jednoduché přiřazení.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-149">Like with properties, indexer `get` and `set` accessors consist of expression body definitions if the `get` accessor consists of a single expression that returns a value or the `set` accessor performs a simple assignment.</span></span>

<span data-ttu-id="ea5a4-150">Následující příklad definuje třídu s názvem `Sports`, která obsahuje interní <xref:System.String> pole, které obsahuje názvy pro řadu sportovních.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-150">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="ea5a4-151">Indexer `get` i přistupující objekty `set` jsou implementovány jako definice textu výrazu.</span><span class="sxs-lookup"><span data-stu-id="ea5a4-151">Both the indexer `get` and `set` accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="ea5a4-152">Další informace najdete v tématu [indexery (C# Průvodce programováním)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="ea5a4-152">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
