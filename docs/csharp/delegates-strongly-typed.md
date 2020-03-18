---
title: Delegáty se silnými typy
description: Zjistěte, jak používat obecné typy delegátů k deklarování vlastních typů při vytváření funkce vyžadující delegáty.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 798e8b597389bc99d10e587ec417a4e717f28abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146200"
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="e34c5-103">Delegáty se silnými typy</span><span class="sxs-lookup"><span data-stu-id="e34c5-103">Strongly Typed Delegates</span></span>

[<span data-ttu-id="e34c5-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="e34c5-104">Previous</span></span>](delegate-class.md)

<span data-ttu-id="e34c5-105">V předchozím článku jste viděli, že pomocí `delegate` klíčového slova vytvoříte konkrétní typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="e34c5-105">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span>

<span data-ttu-id="e34c5-106">Abstraktní Delegate třídy poskytují infrastrukturu pro volné párování a vyvolání.</span><span class="sxs-lookup"><span data-stu-id="e34c5-106">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="e34c5-107">Konkrétní Delegate typy mnohem užitečnější tím, že zahrnuje a vynucuje bezpečnost typů pro metody, které jsou přidány do seznamu vyvolání pro objekt delegáta.</span><span class="sxs-lookup"><span data-stu-id="e34c5-107">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="e34c5-108">Při použití `delegate` klíčového slova a definovat konkrétní typ delegáta, kompilátor generuje tyto metody.</span><span class="sxs-lookup"><span data-stu-id="e34c5-108">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="e34c5-109">V praxi by to vedlo k vytvoření nových typů delegátů, kdykoli potřebujete podpis jiné metody.</span><span class="sxs-lookup"><span data-stu-id="e34c5-109">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="e34c5-110">Tato práce by mohla dostat únavné po čase.</span><span class="sxs-lookup"><span data-stu-id="e34c5-110">This work could get tedious after a time.</span></span> <span data-ttu-id="e34c5-111">Každá nová funkce vyžaduje nové typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="e34c5-111">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="e34c5-112">Naštěstí to není nutné.</span><span class="sxs-lookup"><span data-stu-id="e34c5-112">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="e34c5-113">Rozhraní .NET Core framework obsahuje několik typů, které můžete znovu použít vždy, když potřebujete typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="e34c5-113">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="e34c5-114">Jedná [se o obecné](programming-guide/generics/index.md) definice, takže můžete deklarovat vlastní nastavení, když potřebujete nové deklarace metody.</span><span class="sxs-lookup"><span data-stu-id="e34c5-114">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span>

<span data-ttu-id="e34c5-115">První z těchto typů <xref:System.Action> je typ a několik variant:</span><span class="sxs-lookup"><span data-stu-id="e34c5-115">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="e34c5-116">Modifikátor `in` na argument obecného typu je popsán v článku o kovariance.</span><span class="sxs-lookup"><span data-stu-id="e34c5-116">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="e34c5-117">Existují varianty delegáta, `Action` které obsahují až 16 <xref:System.Action%6016>argumentů, například .</span><span class="sxs-lookup"><span data-stu-id="e34c5-117">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="e34c5-118">Je důležité, aby tyto definice používat různé obecné argumenty pro každý z delegáta argumenty: To vám dává maximální flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="e34c5-118">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="e34c5-119">Argumenty metody nemusí být, ale může být stejný typ.</span><span class="sxs-lookup"><span data-stu-id="e34c5-119">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="e34c5-120">Použijte jeden `Action` z typů pro všechny typy delegáta, který má prázdný návratový typ.</span><span class="sxs-lookup"><span data-stu-id="e34c5-120">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="e34c5-121">Rámec také obsahuje několik obecných typů delegátů, které můžete použít pro typy delegátů, které vracejí hodnoty:</span><span class="sxs-lookup"><span data-stu-id="e34c5-121">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="e34c5-122">Modifikátor `out` argumentu typu typu výsledek je popsán v článku o kovariance.</span><span class="sxs-lookup"><span data-stu-id="e34c5-122">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="e34c5-123">Existují varianty delegáta `Func` s až 16 vstupní <xref:System.Func%6017>argumenty, jako je například .</span><span class="sxs-lookup"><span data-stu-id="e34c5-123">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="e34c5-124">Typ výsledku je vždy poslední parametr typu `Func` ve všech deklaracích podle konvence.</span><span class="sxs-lookup"><span data-stu-id="e34c5-124">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="e34c5-125">Použijte jeden `Func` z typů pro libovolný typ delegáta, který vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e34c5-125">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="e34c5-126">K dispozici je také specializovaný<xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="e34c5-126">There's also a specialized <xref:System.Predicate%601></span></span>
<span data-ttu-id="e34c5-127">zadejte delegáta, který vrátí test na jednu hodnotu:</span><span class="sxs-lookup"><span data-stu-id="e34c5-127">type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="e34c5-128">Můžete si všimnout, že pro `Predicate` `Func` jakýkoli typ existuje strukturálně ekvivalentní typ Například:</span><span class="sxs-lookup"><span data-stu-id="e34c5-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="e34c5-129">Možná si myslíte, že tyto dva typy jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="e34c5-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="e34c5-130">Nejsou.</span><span class="sxs-lookup"><span data-stu-id="e34c5-130">They are not.</span></span>
<span data-ttu-id="e34c5-131">Tyto dvě proměnné nelze zaměnit.</span><span class="sxs-lookup"><span data-stu-id="e34c5-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="e34c5-132">Proměnné jednoho typu nelze přiřadit jiný typ.</span><span class="sxs-lookup"><span data-stu-id="e34c5-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="e34c5-133">Systém typu C# používá názvy definovaných typů, nikoli strukturu.</span><span class="sxs-lookup"><span data-stu-id="e34c5-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="e34c5-134">Všechny tyto definice typu delegáta v základní knihovně .NET by měly znamenat, že není nutné definovat nový typ delegáta pro žádnou novou funkci, kterou vytvoříte a která vyžaduje delegáty.</span><span class="sxs-lookup"><span data-stu-id="e34c5-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="e34c5-135">Tyto obecné definice by měly poskytovat všechny typy delegátů, které potřebujete ve většině situací.</span><span class="sxs-lookup"><span data-stu-id="e34c5-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="e34c5-136">Můžete jednoduše vytvořit konkretizovat jeden z těchto typů s požadovanými parametry typu.</span><span class="sxs-lookup"><span data-stu-id="e34c5-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="e34c5-137">V případě algoritmů, které mohou být obecné, tyto delegáty lze použít jako obecné typy.</span><span class="sxs-lookup"><span data-stu-id="e34c5-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span>

<span data-ttu-id="e34c5-138">To by mělo ušetřit čas a minimalizovat počet nových typů, které je třeba vytvořit, aby bylo možné pracovat s delegáty.</span><span class="sxs-lookup"><span data-stu-id="e34c5-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="e34c5-139">V dalším článku uvidíte několik běžných vzorů pro práci s delegáty v praxi.</span><span class="sxs-lookup"><span data-stu-id="e34c5-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="e34c5-140">Další</span><span class="sxs-lookup"><span data-stu-id="e34c5-140">Next</span></span>](delegates-patterns.md)
