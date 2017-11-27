---
title: "Delegáti silného typu"
description: "Naučte se používat delegáty obecných typů deklarovat vlastních typů, při vytváření funkce, které vyžadují delegáti."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 467ba18f8e032b9b3b8f480d4b10c92d0d7ba3b9
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="c3172-104">Delegáti silného typu</span><span class="sxs-lookup"><span data-stu-id="c3172-104">Strongly Typed Delegates</span></span>

[<span data-ttu-id="c3172-105">Předchozí</span><span class="sxs-lookup"><span data-stu-id="c3172-105">Previous</span></span>](delegate-class.md)

<span data-ttu-id="c3172-106">V předchozím článku jste viděli, vytvořit konkrétní delegáta typy pomocí `delegate` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c3172-106">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="c3172-107">Abstraktní třída delegáta poskytují infrastrukturu pro volné párování a volání.</span><span class="sxs-lookup"><span data-stu-id="c3172-107">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="c3172-108">Konkrétní typy delegáta stát mnohem užitečnější přijetí a vynucování bezpečnost typů pro metody, které jsou přidány do seznamu vyvolání delegáta objektu.</span><span class="sxs-lookup"><span data-stu-id="c3172-108">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="c3172-109">Při použití `delegate` – klíčové slovo a definice typu konkrétní delegáta, kompilátor vygeneruje těchto metod.</span><span class="sxs-lookup"><span data-stu-id="c3172-109">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="c3172-110">V praxi by docházelo k vytvoření nového delegáta typy kdykoli budete potřebovat podpis jinou metodu.</span><span class="sxs-lookup"><span data-stu-id="c3172-110">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="c3172-111">Tento pracovní může získat zdlouhavé po uplynutí určité doby.</span><span class="sxs-lookup"><span data-stu-id="c3172-111">This work could get tedious after a time.</span></span> <span data-ttu-id="c3172-112">Všechny nové funkce, které vyžaduje nové typy delegáta.</span><span class="sxs-lookup"><span data-stu-id="c3172-112">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="c3172-113">Naštěstí to není nutné.</span><span class="sxs-lookup"><span data-stu-id="c3172-113">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="c3172-114">Rozhraní .NET Core obsahuje několik typů, které můžete opakovaně použít vždy, když potřebují delegovat typy.</span><span class="sxs-lookup"><span data-stu-id="c3172-114">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="c3172-115">Jedná se o [Obecné](programming-guide/generics/index.md) definice tak můžou deklarovat přizpůsobení, pokud budete potřebovat nové metoda deklarace.</span><span class="sxs-lookup"><span data-stu-id="c3172-115">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="c3172-116">První z těchto typů je <xref:System.Action> typ a více změn:</span><span class="sxs-lookup"><span data-stu-id="c3172-116">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="c3172-117">`in` Modifikátor na argument obecného typu je popsaná v článku na kovariance.</span><span class="sxs-lookup"><span data-stu-id="c3172-117">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="c3172-118">Existují variace `Action` delegáta, který obsahovat až 16 argumenty, jako například <xref:System.Action%6016>.</span><span class="sxs-lookup"><span data-stu-id="c3172-118">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="c3172-119">Je důležité, aby tyto definice použít jiné obecné argumenty pro každou z argumentů delegáta: který poskytuje maximální flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="c3172-119">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="c3172-120">Metoda argumenty, které nemusí být, ale může být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="c3172-120">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="c3172-121">Použijte jednu z `Action` typy pro jakýkoli typ delegáta, který má typ vrácené hodnoty void.</span><span class="sxs-lookup"><span data-stu-id="c3172-121">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="c3172-122">Rozhraní framework také obsahuje několik typů obecný delegát, které jsou vhodné pro typy delegáta, které vrací hodnoty:</span><span class="sxs-lookup"><span data-stu-id="c3172-122">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="c3172-123">`out` Modifikátor na argument obecného typu výsledek je popsaná v článku na kovariance.</span><span class="sxs-lookup"><span data-stu-id="c3172-123">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="c3172-124">Existují variace `Func` delegovat s až 16 vstupní argumenty, jako <xref:System.Func%6017>.</span><span class="sxs-lookup"><span data-stu-id="c3172-124">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="c3172-125">Typ výsledku je vždy poslední parametr typu ve všech `Func` deklarace podle konvence.</span><span class="sxs-lookup"><span data-stu-id="c3172-125">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="c3172-126">Použijte jednu z `Func` typy pro jakýkoli typ delegáta, který vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c3172-126">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="c3172-127">Je taky speciální <xref:System.Predicate%601> typ pro delegáta, který vrátí testu na jednu hodnotu:</span><span class="sxs-lookup"><span data-stu-id="c3172-127">There's also a specialized <xref:System.Predicate%601> type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="c3172-128">Můžete si všimnout, pro žádné `Predicate` typu, strukturálně ekvivalentní `Func` typ existuje třeba:</span><span class="sxs-lookup"><span data-stu-id="c3172-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="c3172-129">Může si myslíte, že jsou tyto dva typy ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="c3172-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="c3172-130">Nejsou.</span><span class="sxs-lookup"><span data-stu-id="c3172-130">They are not.</span></span>
<span data-ttu-id="c3172-131">Tyto dvě proměnné nelze použít zcela zaměnitelným významem.</span><span class="sxs-lookup"><span data-stu-id="c3172-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="c3172-132">Proměnná jeden typ nelze přiřadit, v případě druhého typu.</span><span class="sxs-lookup"><span data-stu-id="c3172-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="c3172-133">Systém typů jazyka C# používá názvy definovaných typů, není strukturu.</span><span class="sxs-lookup"><span data-stu-id="c3172-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="c3172-134">Všechny tyto typ delegáta, který definice v základní knihovny .NET by měl znamenat, že není nutné definovat nový typ delegáta pro jakékoli nové funkce vytvoříte, které vyžaduje delegáti.</span><span class="sxs-lookup"><span data-stu-id="c3172-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="c3172-135">Tyto obecné definice by měl poskytovat všechny delegát typy, které je nutné v části většině případů.</span><span class="sxs-lookup"><span data-stu-id="c3172-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="c3172-136">Můžete jednoduše vytvořit instanci jedním z těchto typů s požadovaný typ parametry.</span><span class="sxs-lookup"><span data-stu-id="c3172-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="c3172-137">V případě algoritmy, které můžete provést obecný můžete využít tyto delegáti jako obecné typy.</span><span class="sxs-lookup"><span data-stu-id="c3172-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="c3172-138">To by měl ušetřit čas a minimalizovat počet nových typů, které je potřeba vytvořit za účelem práce s delegáti.</span><span class="sxs-lookup"><span data-stu-id="c3172-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="c3172-139">V další článek zobrazí se několik běžných vzorů pro práci s Delegáti v praxi.</span><span class="sxs-lookup"><span data-stu-id="c3172-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="c3172-140">Další</span><span class="sxs-lookup"><span data-stu-id="c3172-140">Next</span></span>](delegates-patterns.md)
