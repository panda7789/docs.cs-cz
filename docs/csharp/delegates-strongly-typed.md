---
title: Delegáty se silnými typy
description: Naučte se používat obecné typy delegátů k deklaraci vlastních typů při vytváření funkce vyžadující delegáty.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: efdbef39d0e6bf2f07cde2c9621cec173e921752
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037360"
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="c5052-103">Delegáty se silnými typy</span><span class="sxs-lookup"><span data-stu-id="c5052-103">Strongly Typed Delegates</span></span>

[<span data-ttu-id="c5052-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="c5052-104">Previous</span></span>](delegate-class.md)

<span data-ttu-id="c5052-105">V předchozím článku jste viděli, že vytvoříte konkrétní typy delegátů pomocí klíčového slova `delegate`.</span><span class="sxs-lookup"><span data-stu-id="c5052-105">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="c5052-106">Abstraktní třída delegáta poskytuje infrastrukturu pro volné spojování a volání.</span><span class="sxs-lookup"><span data-stu-id="c5052-106">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="c5052-107">Konkrétní typy delegátů jsou mnohem užitečnější přechodu a vynucování bezpečnosti typů pro metody, které jsou přidány do seznamu vyvolání pro objekt delegáta.</span><span class="sxs-lookup"><span data-stu-id="c5052-107">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="c5052-108">Při použití klíčového slova `delegate` a definování konkrétního typu delegáta kompilátor vygeneruje tyto metody.</span><span class="sxs-lookup"><span data-stu-id="c5052-108">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="c5052-109">V praxi by to vedlo k vytváření nových typů delegátů, kdykoli potřebujete jiný podpis metody.</span><span class="sxs-lookup"><span data-stu-id="c5052-109">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="c5052-110">Tato práce může po čase obdržet únavné.</span><span class="sxs-lookup"><span data-stu-id="c5052-110">This work could get tedious after a time.</span></span> <span data-ttu-id="c5052-111">Každá nová funkce vyžaduje nové typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="c5052-111">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="c5052-112">Naštěstí to není nutné.</span><span class="sxs-lookup"><span data-stu-id="c5052-112">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="c5052-113">Rozhraní .NET Core Framework obsahuje několik typů, které můžete opakovaně používat, kdykoli potřebujete typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="c5052-113">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="c5052-114">Jedná se o [Obecné](programming-guide/generics/index.md) definice, abyste mohli deklarovat vlastní nastavení, když budete potřebovat nové deklarace metod.</span><span class="sxs-lookup"><span data-stu-id="c5052-114">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="c5052-115">První z těchto typů je <xref:System.Action> typ a několik variant:</span><span class="sxs-lookup"><span data-stu-id="c5052-115">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="c5052-116">Modifikátor `in` v argumentu obecného typu je popsaný v článku o kovarianci.</span><span class="sxs-lookup"><span data-stu-id="c5052-116">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="c5052-117">Existují varianty `Action` delegáta, které obsahují až 16 argumentů, jako je například <xref:System.Action%6016>.</span><span class="sxs-lookup"><span data-stu-id="c5052-117">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="c5052-118">Je důležité, aby tyto definice pro každý z argumentů delegáta používaly různé obecné argumenty: to zajišťuje maximální flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="c5052-118">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="c5052-119">Argumenty metody nemusí být, ale mohou být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="c5052-119">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="c5052-120">Použijte jeden z `Action` typů pro libovolný typ delegáta, který má typ vrácené hodnoty void.</span><span class="sxs-lookup"><span data-stu-id="c5052-120">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="c5052-121">Rozhraní zahrnuje také několik generických typů delegátů, které lze použít pro typy delegátů, které vracejí hodnoty:</span><span class="sxs-lookup"><span data-stu-id="c5052-121">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="c5052-122">Modifikátor `out` v argumentu výsledek obecného typu je popsaný v článku o kovarianci.</span><span class="sxs-lookup"><span data-stu-id="c5052-122">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="c5052-123">Existují odchylky `Func` delegáta s až 16 vstupními argumenty, jako je například <xref:System.Func%6017>.</span><span class="sxs-lookup"><span data-stu-id="c5052-123">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="c5052-124">Typ výsledku je vždy parametr posledního typu ve všech deklaracích `Func` podle konvence.</span><span class="sxs-lookup"><span data-stu-id="c5052-124">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="c5052-125">Pro libovolný typ delegáta, který vrací hodnotu, použijte jeden z `Func` typů.</span><span class="sxs-lookup"><span data-stu-id="c5052-125">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="c5052-126">K dispozici je také specializované <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="c5052-126">There's also a specialized <xref:System.Predicate%601></span></span> 
<span data-ttu-id="c5052-127">typ pro delegáta, který vrátí test na jednu hodnotu:</span><span class="sxs-lookup"><span data-stu-id="c5052-127">type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="c5052-128">Můžete si všimnout, že u jakéhokoli typu `Predicate` existuje strukturální ekvivalentní `Func` typ například:</span><span class="sxs-lookup"><span data-stu-id="c5052-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="c5052-129">Možná si myslíte, že tyto dva typy jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="c5052-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="c5052-130">Nejsou.</span><span class="sxs-lookup"><span data-stu-id="c5052-130">They are not.</span></span>
<span data-ttu-id="c5052-131">Tyto dvě proměnné nelze použít zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="c5052-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="c5052-132">Proměnné jednoho typu se nedá přiřadit jiný typ.</span><span class="sxs-lookup"><span data-stu-id="c5052-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="c5052-133">Systém C# typů používá názvy definovaných typů, nikoli strukturu.</span><span class="sxs-lookup"><span data-stu-id="c5052-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="c5052-134">Všechny tyto definice typů delegátů v knihovně .NET Core by měly znamenat, že nemusíte definovat nový typ delegáta pro každou nově vytvořenou funkci, která vyžaduje delegáty.</span><span class="sxs-lookup"><span data-stu-id="c5052-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="c5052-135">Tyto obecné definice by měly ve většině případů poskytovat všechny typy delegátů, které potřebujete.</span><span class="sxs-lookup"><span data-stu-id="c5052-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="c5052-136">Můžete jednoduše vytvořit instanci jednoho z těchto typů s požadovanými parametry typu.</span><span class="sxs-lookup"><span data-stu-id="c5052-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="c5052-137">V případě algoritmů, které lze nastavit jako obecné, lze tyto delegáty použít jako obecné typy.</span><span class="sxs-lookup"><span data-stu-id="c5052-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="c5052-138">To by mělo ušetřit čas a minimalizovat počet nových typů, které je třeba vytvořit, aby bylo možné pracovat s delegáty.</span><span class="sxs-lookup"><span data-stu-id="c5052-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="c5052-139">V dalším článku uvidíte několik běžných vzorů pro práci s delegáty v praxi.</span><span class="sxs-lookup"><span data-stu-id="c5052-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="c5052-140">Next</span><span class="sxs-lookup"><span data-stu-id="c5052-140">Next</span></span>](delegates-patterns.md)
