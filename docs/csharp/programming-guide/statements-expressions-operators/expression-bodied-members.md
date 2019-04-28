---
title: Členové tvoření - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 02/06/2019
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7c282157639a6a60270ce8dbebbc91dd0e0a3f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61709988"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="3d108-102">Členové tvoření (C# programovací příručka)</span><span class="sxs-lookup"><span data-stu-id="3d108-102">Expression-bodied members (C# programming guide)</span></span>

<span data-ttu-id="3d108-103">Definice těla výrazu umožňují poskytovat implementace člena ve velmi stručným čitelné formy.</span><span class="sxs-lookup"><span data-stu-id="3d108-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="3d108-104">Definice těla výrazu můžete použít pokaždé, když se logika pro všechny podporované členu, například metody nebo vlastnosti, se skládá z jednoho výrazu.</span><span class="sxs-lookup"><span data-stu-id="3d108-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="3d108-105">Definice těla výrazu má následující obecnou syntaxi:</span><span class="sxs-lookup"><span data-stu-id="3d108-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="3d108-106">kde *výraz* je platný výraz.</span><span class="sxs-lookup"><span data-stu-id="3d108-106">where *expression* is a valid expression.</span></span>

<span data-ttu-id="3d108-107">Podpora pro definice těla výrazu byla zavedená pro metody a vlastnosti jen pro čtení v C# 6 a se rozbalil v C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="3d108-107">Support for expression body definitions was introduced for methods and read-only properties in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="3d108-108">Definice těla výrazu jde použít s členy typu uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="3d108-108">Expression body definitions can be used with the type members listed in the following table:</span></span>

|<span data-ttu-id="3d108-109">Člen</span><span class="sxs-lookup"><span data-stu-id="3d108-109">Member</span></span>  |<span data-ttu-id="3d108-110">Podporované od systému...</span><span class="sxs-lookup"><span data-stu-id="3d108-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="3d108-111">– Metoda</span><span class="sxs-lookup"><span data-stu-id="3d108-111">Method</span></span>](#methods)  |<span data-ttu-id="3d108-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="3d108-112">C# 6</span></span> |
|[<span data-ttu-id="3d108-113">Vlastnost jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3d108-113">Read-only property</span></span>](#read-only-properties)   |<span data-ttu-id="3d108-114">C# 6</span><span class="sxs-lookup"><span data-stu-id="3d108-114">C# 6</span></span>  |
|[<span data-ttu-id="3d108-115">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="3d108-115">Property</span></span>](#properties)  |<span data-ttu-id="3d108-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="3d108-116">C# 7.0</span></span> |
|[<span data-ttu-id="3d108-117">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="3d108-117">Constructor</span></span>](#constructors)   |<span data-ttu-id="3d108-118">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="3d108-118">C# 7.0</span></span> |
|[<span data-ttu-id="3d108-119">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="3d108-119">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="3d108-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="3d108-120">C# 7.0</span></span> |
|[<span data-ttu-id="3d108-121">Indexer</span><span class="sxs-lookup"><span data-stu-id="3d108-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="3d108-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="3d108-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="3d108-123">Metody</span><span class="sxs-lookup"><span data-stu-id="3d108-123">Methods</span></span>

<span data-ttu-id="3d108-124">S výrazem v těle metody obsahuje jediný výraz, který vrací hodnotu, jehož typ odpovídá návratový typ metody nebo pro metody, které vracejí `void`, který provede některé operace.</span><span class="sxs-lookup"><span data-stu-id="3d108-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="3d108-125">Například typy toto přepsání <xref:System.Object.ToString%2A> metoda obvykle zahrnují jeden výraz, který vrátí řetězcovou reprezentaci aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="3d108-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span>

<span data-ttu-id="3d108-126">Následující příklad definuje `Person` třídu, která přepíše <xref:System.Object.ToString%2A> metodu s definici tělo výrazu.</span><span class="sxs-lookup"><span data-stu-id="3d108-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="3d108-127">Definuje také `DisplayName` metodu, která zobrazuje název do konzoly.</span><span class="sxs-lookup"><span data-stu-id="3d108-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="3d108-128">Všimněte si, že `return` – klíčové slovo se nepoužívá `ToString` definice těla výrazu.</span><span class="sxs-lookup"><span data-stu-id="3d108-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="3d108-129">Další informace najdete v tématu [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="3d108-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>

## <a name="read-only-properties"></a><span data-ttu-id="3d108-130">Vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3d108-130">Read-only properties</span></span>

<span data-ttu-id="3d108-131">Počínaje C# 6, definice těla výrazu můžete použít k implementaci vlastnost jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="3d108-131">Starting with C# 6, you can use expression body definition to implement a read-only property.</span></span> <span data-ttu-id="3d108-132">K tomuto účelu použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="3d108-132">To do that, use the following syntax:</span></span>

```csharp
PropertyType PropertyName => expression;
```

<span data-ttu-id="3d108-133">Následující příklad definuje `Location` třídy, jejichž jen pro čtení `Name` vlastnost je implementovaný jako definici tělo výrazu, který vrací hodnotu privátní `locationName` pole:</span><span class="sxs-lookup"><span data-stu-id="3d108-133">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field:</span></span>

[!code-csharp[expression-bodied-read-only-property](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="3d108-134">Další informace o vlastnostech najdete v tématu [vlastnosti (C# Programming Guide)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="3d108-134">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="properties"></a><span data-ttu-id="3d108-135">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3d108-135">Properties</span></span>

<span data-ttu-id="3d108-136">Počínaje C# 7.0, definice těla výrazu můžete použít k implementaci vlastnost `get` a `set` přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="3d108-136">Starting with C# 7.0, you can use expression body definitions to implement property `get` and `set` accessors.</span></span> <span data-ttu-id="3d108-137">Následující příklad ukazuje, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="3d108-137">The following example demonstrates how to do that:</span></span>

[!code-csharp[expression-bodied-property-get-set](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]

<span data-ttu-id="3d108-138">Další informace o vlastnostech najdete v tématu [vlastnosti (C# Programming Guide)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="3d108-138">For more information about properties, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="constructors"></a><span data-ttu-id="3d108-139">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="3d108-139">Constructors</span></span>

<span data-ttu-id="3d108-140">Definice těla výrazu pro konstruktor se obvykle skládá z výrazu přiřazení jednoho nebo volání metody, která zpracuje argumenty konstruktoru nebo inicializuje stav instance.</span><span class="sxs-lookup"><span data-stu-id="3d108-140">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span>

<span data-ttu-id="3d108-141">Následující příklad definuje `Location` třídy, jejíž konstruktor má jeden řetězcový parametr s názvem *název*.</span><span class="sxs-lookup"><span data-stu-id="3d108-141">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="3d108-142">Definice textu výrazu přiřadí argument `Name` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3d108-142">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="3d108-143">Další informace najdete v tématu [konstruktory (C# Programming Guide)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="3d108-143">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="3d108-144">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="3d108-144">Finalizers</span></span>

<span data-ttu-id="3d108-145">Definice těla výrazu pro finalizační metodu obvykle obsahuje příkazy vyčištění, jako je například příkazy, které uvolnění nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="3d108-145">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="3d108-146">Následující příklad definuje finalizační metodu, která používá definici tělo výrazu k označení, že byla zavolána finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="3d108-146">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="3d108-147">Další informace najdete v tématu [finalizační metody (C# Programming Guide)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="3d108-147">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="3d108-148">Indexery</span><span class="sxs-lookup"><span data-stu-id="3d108-148">Indexers</span></span>

<span data-ttu-id="3d108-149">Jako jsou vlastnosti indexeru pro operace get a přístupové objekty set se skládají z definice těla výrazu Pokud přistupující objekt get se skládá z jednoho příkazu, který vrací hodnotu, nebo přístupový objekt set provádí jednoduché přiřazení.</span><span class="sxs-lookup"><span data-stu-id="3d108-149">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="3d108-150">Následující příklad definuje třídu s názvem `Sports` , který obsahuje interní <xref:System.String> pole, které obsahuje názvy počet sportu.</span><span class="sxs-lookup"><span data-stu-id="3d108-150">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="3d108-151">Get indexeru a přístupové objekty set jsou implementovány jako definice těla výrazu.</span><span class="sxs-lookup"><span data-stu-id="3d108-151">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)]

<span data-ttu-id="3d108-152">Další informace najdete v tématu [indexery (C# Programming Guide)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="3d108-152">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>
