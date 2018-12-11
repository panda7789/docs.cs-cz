---
title: Členové tvoření - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- expression-bodied members[C#]
- C# language, expresion-bodied members
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36f71352dca584c107af4f45850ce21bb016ba01
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238114"
---
# <a name="expression-bodied-members-c-programming-guide"></a><span data-ttu-id="e9dc0-102">Členové tvoření (C# programovací příručka)</span><span class="sxs-lookup"><span data-stu-id="e9dc0-102">Expression-bodied members (C# programming guide)</span></span>
<span data-ttu-id="e9dc0-103">Definice těla výrazu umožňují poskytovat implementace člena ve velmi stručným čitelné formy.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-103">Expression body definitions let you provide a member's implementation in a very concise, readable form.</span></span> <span data-ttu-id="e9dc0-104">Definice těla výrazu můžete použít pokaždé, když se logika pro všechny podporované členu, například metody nebo vlastnosti, se skládá z jednoho výrazu.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-104">You can use an expression body definition whenever the logic for any supported member, such as a method or property, consists of a single expression.</span></span> <span data-ttu-id="e9dc0-105">Definice těla výrazu má následující obecnou syntaxi:</span><span class="sxs-lookup"><span data-stu-id="e9dc0-105">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="e9dc0-106">kde *výraz* je platný výraz.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-106">where *expression* is a valid expression.</span></span> 

<span data-ttu-id="e9dc0-107">Podpora pro definice těla výrazu byla zavedená pro metody a vlastnosti získat přístupové objekty v jazyce C# 6 a se rozbalil v jazyce C# 7.0.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-107">Support for expression body definitions was introduced for methods and property get accessors in C# 6 and was expanded in C# 7.0.</span></span> <span data-ttu-id="e9dc0-108">Definice těla výrazu jde použít s členy typu uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="e9dc0-108">Expression body definitions can be used with the type members listed in the following table:</span></span> 

|<span data-ttu-id="e9dc0-109">Člen</span><span class="sxs-lookup"><span data-stu-id="e9dc0-109">Member</span></span>  |<span data-ttu-id="e9dc0-110">Podporované od systému...</span><span class="sxs-lookup"><span data-stu-id="e9dc0-110">Supported as of...</span></span> |
|---------|---------|
|[<span data-ttu-id="e9dc0-111">– Metoda</span><span class="sxs-lookup"><span data-stu-id="e9dc0-111">Method</span></span>](#methods)  |<span data-ttu-id="e9dc0-112">C# 6</span><span class="sxs-lookup"><span data-stu-id="e9dc0-112">C# 6</span></span> |
|[<span data-ttu-id="e9dc0-113">Konstruktor</span><span class="sxs-lookup"><span data-stu-id="e9dc0-113">Constructor</span></span>](#constructors)   |<span data-ttu-id="e9dc0-114">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="e9dc0-114">C# 7.0</span></span> |
|[<span data-ttu-id="e9dc0-115">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="e9dc0-115">Finalizer</span></span>](#finalizers)     |<span data-ttu-id="e9dc0-116">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="e9dc0-116">C# 7.0</span></span> |
|[<span data-ttu-id="e9dc0-117">Property Get</span><span class="sxs-lookup"><span data-stu-id="e9dc0-117">Property Get</span></span>](#property-get-statements)  |<span data-ttu-id="e9dc0-118">C# 6</span><span class="sxs-lookup"><span data-stu-id="e9dc0-118">C# 6</span></span> |
|[<span data-ttu-id="e9dc0-119">Sada vlastností</span><span class="sxs-lookup"><span data-stu-id="e9dc0-119">Property Set</span></span>](#property-set-statements)  |<span data-ttu-id="e9dc0-120">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="e9dc0-120">C# 7.0</span></span> |
|[<span data-ttu-id="e9dc0-121">Indexer</span><span class="sxs-lookup"><span data-stu-id="e9dc0-121">Indexer</span></span>](#indexers)       |<span data-ttu-id="e9dc0-122">C# 7.0</span><span class="sxs-lookup"><span data-stu-id="e9dc0-122">C# 7.0</span></span> |

## <a name="methods"></a><span data-ttu-id="e9dc0-123">Metody</span><span class="sxs-lookup"><span data-stu-id="e9dc0-123">Methods</span></span>

<span data-ttu-id="e9dc0-124">S výrazem v těle metody obsahuje jediný výraz, který vrací hodnotu, jehož typ odpovídá návratový typ metody nebo pro metody, které vracejí `void`, který provede některé operace.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-124">An expression-bodied method consists of a single expression that returns a value whose type matches the method's return type, or, for methods that return `void`, that performs some operation.</span></span> <span data-ttu-id="e9dc0-125">Například typy toto přepsání <xref:System.Object.ToString%2A> metoda obvykle zahrnují jeden výraz, který vrátí řetězcovou reprezentaci aktuálního objektu.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-125">For example, types that override the <xref:System.Object.ToString%2A> method typically include a single expression that returns the string representation of the current object.</span></span> 

<span data-ttu-id="e9dc0-126">Následující příklad definuje `Person` třídu, která přepíše <xref:System.Object.ToString%2A> metodu s definici tělo výrazu.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-126">The following example defines a `Person` class that overrides the <xref:System.Object.ToString%2A> method with an expression body definition.</span></span> <span data-ttu-id="e9dc0-127">Definuje také `DisplayName` metodu, která zobrazuje název do konzoly.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-127">It also defines a `DisplayName` method that displays a name to the console.</span></span> <span data-ttu-id="e9dc0-128">Všimněte si, že `return` – klíčové slovo se nepoužívá `ToString` definice těla výrazu.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-128">Note that the `return` keyword is not used in the `ToString` expression body definition.</span></span>

[!code-csharp[expression-bodied-methods](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-methods.cs)]  

<span data-ttu-id="e9dc0-129">Další informace najdete v tématu [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="e9dc0-129">For more information, see [Methods (C# Programming Guide)](../classes-and-structs/methods.md).</span></span>
 
## <a name="constructors"></a><span data-ttu-id="e9dc0-130">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="e9dc0-130">Constructors</span></span>

<span data-ttu-id="e9dc0-131">Definice těla výrazu pro konstruktor se obvykle skládá z výrazu přiřazení jednoho nebo volání metody, která zpracuje argumenty konstruktoru nebo inicializuje stav instance.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-131">An expression body definition for a constructor typically consists of a single assignment expression or a method call that handles the constructor's arguments or initializes instance state.</span></span> 

<span data-ttu-id="e9dc0-132">Následující příklad definuje `Location` třídy, jejíž konstruktor má jeden řetězcový parametr s názvem *název*.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-132">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="e9dc0-133">Definice textu výrazu přiřadí argument `Name` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-133">The expression body definition assigns the argument to the `Name` property.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="e9dc0-134">Další informace najdete v tématu [konstruktory (C# Programming Guide)](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="e9dc0-134">For more information, see [Constructors (C# Programming Guide)](../classes-and-structs/constructors.md).</span></span>

## <a name="finalizers"></a><span data-ttu-id="e9dc0-135">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="e9dc0-135">Finalizers</span></span>

<span data-ttu-id="e9dc0-136">Definice těla výrazu pro finalizační metodu obvykle obsahuje příkazy vyčištění, jako je například příkazy, které uvolnění nespravovaných prostředků.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-136">An expression body definition for a finalizer typically contains cleanup statements, such as statements that release unmanaged resources.</span></span>

<span data-ttu-id="e9dc0-137">Následující příklad definuje finalizační metodu, která používá definici tělo výrazu k označení, že byla zavolána finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-137">The following example defines a finalizer that uses an expression body definition to indicate that the finalizer has been called.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  

<span data-ttu-id="e9dc0-138">Další informace najdete v tématu [finalizační metody (C# Programming Guide)](../classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="e9dc0-138">For more information, see [Finalizers (C# Programming Guide)](../classes-and-structs/destructors.md).</span></span>

## <a name="property-get-statements"></a><span data-ttu-id="e9dc0-139">Příkazy get vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e9dc0-139">Property get statements</span></span>

<span data-ttu-id="e9dc0-140">Pokud se rozhodnete implementovat vlastnost načtení přístupového objektu sami, můžete použít definici tělo výrazu pro jeden výrazy, které jednoduše vrátí hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-140">If you choose to implement a property get accessor yourself, you can use an expression body definition for single expressions that simply return the property value.</span></span> <span data-ttu-id="e9dc0-141">Všimněte si, že `return` příkazu se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-141">Note that the `return` statement isn't used.</span></span>

<span data-ttu-id="e9dc0-142">Následující příklad definuje `Location.Name` vlastnost, jejíž vlastnost načtení přístupového objektu vrací hodnotu privátní `locationName` pole, která zálohuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-142">The following example defines a `Location.Name` property whose property get accessor returns the value of the private `locationName` field that backs the property.</span></span> 

[!code-csharp[expression-bodied-property-getter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="e9dc0-143">Vlastnosti jen pro čtení, které používají definici tělo výrazu je možné implementovat bez explicitního `set` příkazu.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-143">Read-only properties that use an expression body definition can be implemented without an explicit `set` statement.</span></span> <span data-ttu-id="e9dc0-144">Syntaxe je následující:</span><span class="sxs-lookup"><span data-stu-id="e9dc0-144">The syntax is:</span></span>

```csharp
PropertyName => returnValue;
```

<span data-ttu-id="e9dc0-145">Následující příklad definuje `Location` třídy, jejichž jen pro čtení `Name` vlastnost je implementovaný jako definici tělo výrazu, který vrací hodnotu privátní `locationName` pole.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-145">The following example defines a `Location` class whose read-only `Name` property is implemented as an expression body definition that returns the value of the private `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-readonly.cs#1)]  

<span data-ttu-id="e9dc0-146">Další informace najdete v tématu [vlastnosti (C# Programming Guide)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="e9dc0-146">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="property-set-statements"></a><span data-ttu-id="e9dc0-147">Příkazy set vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e9dc0-147">Property set statements</span></span>

<span data-ttu-id="e9dc0-148">Pokud se rozhodnete implementovat přistupující objekt množiny vlastností sami, můžete pro výraz jeden řádek, který přiřazuje hodnotu pole, která zálohuje vlastnost definici tělo výrazu.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-148">If you choose to implement a property set accessor yourself, you can use an expression body definition for a single-line expression that assigns a value to the field that backs the property.</span></span>

<span data-ttu-id="e9dc0-149">Následující příklad definuje `Location.Name` vlastnost, jejíž vlastnost nastavení příkazu přiřadí privátní vstupní argument `locationName` pole, která zálohuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-149">The following example defines a `Location.Name` property whose property set statement assigns its input argument to the private `locationName` field that backs the property.</span></span>

[!code-csharp[expression-bodied-property-setter](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

<span data-ttu-id="e9dc0-150">Další informace najdete v tématu [vlastnosti (C# Programming Guide)](../classes-and-structs/properties.md).</span><span class="sxs-lookup"><span data-stu-id="e9dc0-150">For more information, see [Properties (C# Programming Guide)](../classes-and-structs/properties.md).</span></span>

## <a name="indexers"></a><span data-ttu-id="e9dc0-151">Indexery</span><span class="sxs-lookup"><span data-stu-id="e9dc0-151">Indexers</span></span>

<span data-ttu-id="e9dc0-152">Jako jsou vlastnosti indexeru pro operace get a přístupové objekty set se skládají z definice těla výrazu Pokud přistupující objekt get se skládá z jednoho příkazu, který vrací hodnotu, nebo přístupový objekt set provádí jednoduché přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-152">Like properties, an indexer's get and set accessors consist of expression body definitions if the get accessor consists of a single statement that returns a value or the set accessor performs a simple assignment.</span></span>

<span data-ttu-id="e9dc0-153">Následující příklad definuje třídu s názvem `Sports` , který obsahuje interní <xref:System.String> pole, které obsahuje názvy počet sportu.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-153">The following example defines a class named `Sports` that includes an internal <xref:System.String> array that contains the names of a number of sports.</span></span> <span data-ttu-id="e9dc0-154">Get indexeru a přístupové objekty set jsou implementovány jako definice těla výrazu.</span><span class="sxs-lookup"><span data-stu-id="e9dc0-154">Both the indexer's get and set accessors are implemented as expression body definitions.</span></span>

[!code-csharp[expression-bodied-indexer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-indexers.cs#1)] 

<span data-ttu-id="e9dc0-155">Další informace najdete v tématu [indexery (C# Programming Guide)](../indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="e9dc0-155">For more information, see [Indexers (C# Programming Guide)](../indexers/index.md).</span></span>

