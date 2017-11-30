---
title: "Výraz vozidlo členové (C# programování průvodce)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ead1e474fe87bd9fbd0f972bc0f2fc4fefc12ecf
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="95fb8-102">Výraz vozidlo členové (C# programovací průvodce)</span><span class="sxs-lookup"><span data-stu-id="95fb8-102">Expression-bodied members (C# programming guide)</span></span>
<span data-ttu-id="95fb8-103">Výraz definice textu umožňují poskytovat implementace člena ve formuláři velmi stručným a čitelné.</span><span class="sxs-lookup"><span data-stu-id="95fb8-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="95fb8-104">Definici výraz text můžete použít vždy, když logiku pro všechny podporované člena, jako je například metody nebo vlastnosti, se skládá z jednoho výrazu.</span><span class="sxs-lookup"><span data-stu-id="95fb8-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="95fb8-105">Definici výraz text má následující obecné syntaxi:</span><span class="sxs-lookup"><span data-stu-id="95fb8-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="95fb8-106">kde *výraz* je platný výraz.</span><span class="sxs-lookup"><span data-stu-id="95fb8-106">where *expression* is a valid expression.</span></span> 

<span data-ttu-id="95fb8-107">Podpora pro výraz text definice byla zavedená pro metody a vlastnosti získat přístupové objekty v C# 6 a byla rozšířena v C# 7.</span><span class="sxs-lookup"><span data-stu-id="95fb8-107">Support for expression body definitions was introduced for methods and property get accessors in C# 6 and was expanded in C# 7.</span></span> <span data-ttu-id="95fb8-108">Výraz definice textu lze použít s členy typu uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="95fb8-108">Expression body definitions can be used with the type members listed in the following table:</span></span> 

|<span data-ttu-id="95fb8-109">Člen</span><span class="sxs-lookup"><span data-stu-id="95fb8-109">Member</span></span>  |<span data-ttu-id="95fb8-110">Podporované od systému...</span><span class="sxs-lookup"><span data-stu-id="95fb8-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="95fb8-111">– Metoda</span><span class="sxs-lookup"><span data-stu-id="95fb8-111">Method</span></span>](#methods)  |<span data-ttu-id="95fb8-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="95fb8-112">C# 6</span></span> |
|[<span data-ttu-id="95fb8-113">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="95fb8-113">Constructor</span></span>](#constructors)   |<span data-ttu-id="95fb8-114">C# 7</span><span class="sxs-lookup"><span data-stu-id="95fb8-114">C# 7</span></span> |
|[<span data-ttu-id="95fb8-115">Finalizační metodu</span><span class="sxs-lookup"><span data-stu-id="95fb8-115">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="95fb8-116">C# 7</span><span class="sxs-lookup"><span data-stu-id="95fb8-116">C# 7</span></span> |
|[<span data-ttu-id="95fb8-117">Vlastnost Get</span><span class="sxs-lookup"><span data-stu-id="95fb8-117">Property Get</span></span>](#property-get-statements)  |<span data-ttu-id="95fb8-118">C# 6</span><span class="sxs-lookup"><span data-stu-id="95fb8-118">C# 6</span></span> |
|[<span data-ttu-id="95fb8-119">Sada vlastností</span><span class="sxs-lookup"><span data-stu-id="95fb8-119">Property Set</span></span>](#property-set-statements)  |<span data-ttu-id="95fb8-120">C# 7</span><span class="sxs-lookup"><span data-stu-id="95fb8-120">C# 7</span></span> |
|[<span data-ttu-id="95fb8-121">Indexer</span><span class="sxs-lookup"><span data-stu-id="95fb8-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="95fb8-122">C# 7</span><span class="sxs-lookup"><span data-stu-id="95fb8-122">C# 7</span></span> |

## <a name="methods"></a><span data-ttu-id="95fb8-123">Metody</span><span class="sxs-lookup"><span data-stu-id="95fb8-123">Methods</span></span>

<span data-ttu-id="95fb8-124">Výraz vozidlo metoda se skládá z jediného výrazu, která vrátí hodnotu, jejíž typ odpovídá návratový typ metody, nebo pro metody, které vracejí `void`, který provede nějaké operace.</span><span class="sxs-lookup"><span data-stu-id="95fb8-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="95fb8-125">Například, že přepsání typy <xref:System.Object.ToString%2A> metoda obvykle obsahují jeden výraz, který vrátí řetězcovou reprezentaci aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="95fb8-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span> 

<span data-ttu-id="95fb8-126">V následujícím příkladu definuje `Person` třídu, která přepisuje <xref:System.Object.ToString%2A> metoda k definici textu výraz.</span><span class="sxs-lookup"><span data-stu-id="95fb8-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="95fb8-127">Také definuje `Show` metoda, která zobrazí název ke konzole.</span><span class="sxs-lookup"><span data-stu-id="95fb8-127">It also defines a `Show` method that displays a name to the console.</span></span> <span data-ttu-id="95fb8-128">Všimněte si, že `return` – klíčové slovo není používáno ve `ToString` definice textu výrazu.</span><span class="sxs-lookup"><span data-stu-id="95fb8-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="95fb8-129">Další informace najdete v tématu [metody (C# programování průvodce)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="95fb8-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>
 
## <a name="constructors"></a><span data-ttu-id="95fb8-130">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="95fb8-130">Constructors</span></span>

<span data-ttu-id="95fb8-131">Definici výraz text pro konstruktor se obvykle skládá z jedné přiřazení výraz nebo volání metody, která zpracuje argumenty v konstruktoru nebo inicializuje stav instance.</span><span class="sxs-lookup"><span data-stu-id="95fb8-131">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span> 

<span data-ttu-id="95fb8-132">V následujícím příkladu definuje `Location` třídu, jejíž konstruktor má jednoho řetězce parametr s názvem *název*.</span><span class="sxs-lookup"><span data-stu-id="95fb8-132">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="95fb8-133">Definice textu výraz přiřadí argument `Name` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="95fb8-133">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="95fb8-134">Další informace najdete v tématu [konstruktory (C# programování průvodce)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="95fb8-134">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="95fb8-135">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="95fb8-135">Finalizers</span></span>

<span data-ttu-id="95fb8-136">Definici výraz text finalizační metody obvykle obsahuje čištění příkazy, jako je například příkazy, které uvolnění nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="95fb8-136">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="95fb8-137">V následujícím příkladu definuje finalizační metodu, který používá definici textu výraz k označení, že byla volána finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="95fb8-137">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="95fb8-138">Další informace najdete v tématu [finalizační metody (C# Průvodce programováním)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="95fb8-138">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="property-get-statements"></a><span data-ttu-id="95fb8-139">Property get – příkazy</span><span class="sxs-lookup"><span data-stu-id="95fb8-139">Property get statements</span></span>

<span data-ttu-id="95fb8-140">Pokud chcete implementovat vlastnost načtení přístupového objektu sami, můžete použít definici textu výraz pro jeden výrazy, které jednoduše vrátit hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="95fb8-140">If you choose to implement a property get accessor yourself, you can use an expression body definition for single expressions that simply return the property value.</span></span> <span data-ttu-id="95fb8-141">Všimněte si, že `return` příkaz nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="95fb8-141">Note that the `return` statement isn't used.</span></span>

<span data-ttu-id="95fb8-142">V následujícím příkladu definuje `Location.Name` vlastnost, jejichž vlastnost načtení přístupového objektu vrací hodnotu privátní `locationName` pole, která zálohuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="95fb8-142">The following example defines a `Location.Name` property whose property get accessor returns the value of the private `locationName` field that backs the property.</span></span> 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="95fb8-143">Vlastnosti jen pro čtení, které použijte definici textu výraz lze provést bez explicitního `set` příkaz.</span><span class="sxs-lookup"><span data-stu-id="95fb8-143">Read-only properties that use an expression body definition can be implemented without an explicit `set` statement.</span></span> <span data-ttu-id="95fb8-144">Syntaxe je následující:</span><span class="sxs-lookup"><span data-stu-id="95fb8-144">The syntax is:</span></span>

```csharp
PropertyName => returnValue;
```

<span data-ttu-id="95fb8-145">V následujícím příkladu definuje `Location` třídy jehož jen pro čtení `Name` vlastnost je implementovaný jako definice textu výraz, který vrací hodnotu privátní `locationName` pole.</span><span class="sxs-lookup"><span data-stu-id="95fb8-145">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="95fb8-146">Další informace najdete v tématu [vlastnosti (C# Průvodce programováním)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="95fb8-146">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="property-set-statements"></a><span data-ttu-id="95fb8-147">Vlastnost set – příkazy</span><span class="sxs-lookup"><span data-stu-id="95fb8-147">Property set statements</span></span>

<span data-ttu-id="95fb8-148">Pokud zvolíte možnost implementovat vlastnosti sami, můžete použít definici textu výraz pro výraz jeden řádek, který přiřazuje hodnotu pole, která zálohuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="95fb8-148">If you choose to implement a property set accessor yourself, you can use an expression body definition for a single-line expression that assigns a value to the field that backs the property.</span></span>

<span data-ttu-id="95fb8-149">V následujícím příkladu definuje `Location.Name` vlastnost, jehož vlastnost nastavena příkaz přiřadí privátní jeho vstupní argument `locationName` pole, která zálohuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="95fb8-149">The following example defines a `Location.Name` property whose property set statement assigns its input argument to the private `locationName` field that backs the property.</span></span>

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="95fb8-150">Další informace najdete v tématu [vlastnosti (C# Průvodce programováním)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="95fb8-150">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="95fb8-151">Indexery</span><span class="sxs-lookup"><span data-stu-id="95fb8-151">Indexers</span></span>

<span data-ttu-id="95fb8-152">Jako vlastnosti indexer get a přístupových objektů sady obsahovat definice textu výraz Pokud přistupující objekt get se skládá z jednoho příkazu, který vrátí hodnotu, nebo přistupující objekt set provede jednoduché přiřazení.</span><span class="sxs-lookup"><span data-stu-id="95fb8-152">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="95fb8-153">Následující příklad definuje třídu s názvem `Sports` , který obsahuje interní <xref:System.String> pole, které obsahuje názvy počtu sportu.</span><span class="sxs-lookup"><span data-stu-id="95fb8-153">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="95fb8-154">Get indexeru a přístupových objektů sady jsou implementované jako výraz text definice.</span><span class="sxs-lookup"><span data-stu-id="95fb8-154">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

<span data-ttu-id="95fb8-155">Další informace najdete v tématu [indexery (C# Průvodce programováním)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="95fb8-155">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>

