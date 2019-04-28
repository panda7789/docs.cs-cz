---
title: Delegáty se silnými typy
description: Další informace o použití obecné typy delegátů pro deklaraci vlastní typy při vytváření funkce vyžadující delegátů.
ms.date: 06/20/2016
ms.assetid: 564a683d-352b-4e57-8bac-b466529daf6b
ms.openlocfilehash: 2e4cc1c7bfa0aaa90f3aaefa0da64c5486a9d10f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646654"
---
# <a name="strongly-typed-delegates"></a><span data-ttu-id="72ebd-103">Delegáty se silnými typy</span><span class="sxs-lookup"><span data-stu-id="72ebd-103">Strongly Typed Delegates</span></span>

[<span data-ttu-id="72ebd-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="72ebd-104">Previous</span></span>](delegate-class.md)

<span data-ttu-id="72ebd-105">V předchozím článku jste viděli, vytvořit konkrétní delegáta typů pomocí `delegate` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="72ebd-105">In the previous article, you saw that you create specific delegate types using the `delegate` keyword.</span></span> 

<span data-ttu-id="72ebd-106">Abstraktní třída delegáta poskytování infrastruktury pro volné párování a vyvolání.</span><span class="sxs-lookup"><span data-stu-id="72ebd-106">The abstract Delegate class provide the infrastructure for loose coupling and invocation.</span></span> <span data-ttu-id="72ebd-107">Ve středu a bezpečnost typů pro metody, které se přidají do seznamu vyvolání pro objekt delegáta vynucování stane mnohem užitečnější konkrétní typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="72ebd-107">Concrete Delegate types become much more useful by embracing and enforcing type safety for the methods that are added to the invocation list for a delegate object.</span></span> <span data-ttu-id="72ebd-108">Při použití `delegate` – klíčové slovo a definovat delegáta konkrétní typ, kompilátor vygeneruje tyto metody.</span><span class="sxs-lookup"><span data-stu-id="72ebd-108">When you use the `delegate` keyword and define a concrete delegate type, the compiler generates those methods.</span></span>

<span data-ttu-id="72ebd-109">V praxi to vede k vytváření nového delegáta typů pokaždé, když potřebujete podpis jinou metodu.</span><span class="sxs-lookup"><span data-stu-id="72ebd-109">In practice, this would lead to creating new delegate types whenever you need a different method signature.</span></span> <span data-ttu-id="72ebd-110">Tato práce může únavné po uplynutí určité doby.</span><span class="sxs-lookup"><span data-stu-id="72ebd-110">This work could get tedious after a time.</span></span> <span data-ttu-id="72ebd-111">Všechny nové funkce, které vyžaduje nové typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="72ebd-111">Every new feature requires new delegate types.</span></span>

<span data-ttu-id="72ebd-112">Naštěstí to není nutné.</span><span class="sxs-lookup"><span data-stu-id="72ebd-112">Thankfully, this isn't necessary.</span></span> <span data-ttu-id="72ebd-113">.NET Core framework obsahuje několik typů, které můžete znovu použít pokaždé, když potřebujete typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="72ebd-113">The .NET Core framework contains several types that you can reuse whenever you need delegate types.</span></span> <span data-ttu-id="72ebd-114">Jedná se o [obecný](programming-guide/generics/index.md) definice, takže je možné deklarovat vlastní nastavení, když budete potřebovat nové deklarace metody.</span><span class="sxs-lookup"><span data-stu-id="72ebd-114">These are [generic](programming-guide/generics/index.md) definitions so you can declare customizations when you need new method declarations.</span></span> 

<span data-ttu-id="72ebd-115">První z těchto typů je <xref:System.Action> typu a používat několik variant:</span><span class="sxs-lookup"><span data-stu-id="72ebd-115">The first of these types is the <xref:System.Action> type, and several variations:</span></span>

```csharp
public delegate void Action();
public delegate void Action<in T>(T arg);
public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
// Other variations removed for brevity.
```

<span data-ttu-id="72ebd-116">`in` Modifikátor argument obecného typu je popsaná v článku na kovariance.</span><span class="sxs-lookup"><span data-stu-id="72ebd-116">The `in` modifier on the generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="72ebd-117">Existují variace `Action` delegáta, který obsahuje až 16 argumenty, jako <xref:System.Action%6016>.</span><span class="sxs-lookup"><span data-stu-id="72ebd-117">There are variations of the `Action` delegate that contain up to 16 arguments such as <xref:System.Action%6016>.</span></span>
<span data-ttu-id="72ebd-118">Je důležité, že tyto definice pomocí různých obecných argumentů pro jednotlivé argumenty delegáta: Který poskytuje maximální flexibilitu.</span><span class="sxs-lookup"><span data-stu-id="72ebd-118">It's important that these definitions use different generic arguments for each of the delegate arguments: That gives you maximum flexibility.</span></span> <span data-ttu-id="72ebd-119">Argumenty metody nemusí být, ale může být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="72ebd-119">The method arguments need not be, but may be, the same type.</span></span>

<span data-ttu-id="72ebd-120">Použijte jednu z `Action` typy pro libovolný typ delegáta, který má typ vrácené hodnoty void.</span><span class="sxs-lookup"><span data-stu-id="72ebd-120">Use one of the `Action` types for any delegate type that has a void return type.</span></span>

<span data-ttu-id="72ebd-121">Rozhraní také obsahuje několik typů obecného delegátu, které můžete použít pro typy delegátů, které vracejí hodnoty:</span><span class="sxs-lookup"><span data-stu-id="72ebd-121">The framework also includes several generic delegate types that you can use for delegate types that return values:</span></span>

```csharp
public delegate TResult Func<out TResult>();
public delegate TResult Func<in T1, out TResult>(T1 arg);
public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
// Other variations removed for brevity
```

<span data-ttu-id="72ebd-122">`out` Modifikátor argument obecného typu výsledku je popsaná v článku na kovariance.</span><span class="sxs-lookup"><span data-stu-id="72ebd-122">The `out` modifier on the result generic type argument is covered in the article on covariance.</span></span>

<span data-ttu-id="72ebd-123">Existují variace `Func` delegáta s až 16 vstupní argumenty, jako <xref:System.Func%6017>.</span><span class="sxs-lookup"><span data-stu-id="72ebd-123">There are variations of the `Func` delegate with up to 16 input arguments such as <xref:System.Func%6017>.</span></span>
<span data-ttu-id="72ebd-124">Typ výsledku je vždy poslední parametr typu ve všech `Func` deklarace podle konvence.</span><span class="sxs-lookup"><span data-stu-id="72ebd-124">The type of the result is always the last type parameter in all the `Func` declarations, by convention.</span></span>

<span data-ttu-id="72ebd-125">Použijte jednu z `Func` typy pro jakýkoli typ delegáta, který vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72ebd-125">Use one of the `Func` types for any delegate type that returns a value.</span></span>

<span data-ttu-id="72ebd-126">Je také specializované <xref:System.Predicate%601></span><span class="sxs-lookup"><span data-stu-id="72ebd-126">There's also a specialized <xref:System.Predicate%601></span></span> 
<span data-ttu-id="72ebd-127">typ delegáta, který vrací test na jednu hodnotu:</span><span class="sxs-lookup"><span data-stu-id="72ebd-127">type for a delegate that returns a test on a single value:</span></span>

```csharp
public delegate bool Predicate<in T>(T obj);
```

<span data-ttu-id="72ebd-128">Můžete si všimnout, které pro všechny `Predicate` typ, strukturálně ekvivalentní `Func` typ existuje. například:</span><span class="sxs-lookup"><span data-stu-id="72ebd-128">You may notice that for any `Predicate` type, a structurally equivalent `Func` type exists For example:</span></span>

```csharp
Func<string, bool> TestForString;
Predicate<string> AnotherTestForString;
```

<span data-ttu-id="72ebd-129">Možná myslíte, že tyto dva typy jsou ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="72ebd-129">You might think these two types are equivalent.</span></span> <span data-ttu-id="72ebd-130">Nejsou.</span><span class="sxs-lookup"><span data-stu-id="72ebd-130">They are not.</span></span>
<span data-ttu-id="72ebd-131">Tyto dvě proměnné nelze používat Zaměnitelně.</span><span class="sxs-lookup"><span data-stu-id="72ebd-131">These two variables cannot be used interchangeably.</span></span> <span data-ttu-id="72ebd-132">Jiný typ nelze přiřadit proměnné typu jeden.</span><span class="sxs-lookup"><span data-stu-id="72ebd-132">A variable of one type cannot be assigned the other type.</span></span> <span data-ttu-id="72ebd-133">C# Názvy definované typy, nikoli struktura používá systém typů.</span><span class="sxs-lookup"><span data-stu-id="72ebd-133">The C# type system uses the names of the defined types, not the structure.</span></span>

<span data-ttu-id="72ebd-134">Všechny tyto typ delegáta, který by měl definice v základní knihovně .NET znamená, že není potřeba definovat nový typ delegáta pro jakékoli nové funkce můžete vytvořit, které vyžaduje delegátů.</span><span class="sxs-lookup"><span data-stu-id="72ebd-134">All these delegate type definitions in the .NET Core Library should mean that you do not need to define a new delegate type for any new feature you create that requires delegates.</span></span> <span data-ttu-id="72ebd-135">Tyto obecné definice by měly poskytnout všechny delegáta typy, které je třeba v části většinu situací.</span><span class="sxs-lookup"><span data-stu-id="72ebd-135">These generic definitions should provide all the delegate types you need under most situations.</span></span> <span data-ttu-id="72ebd-136">Můžete jednoduše vytvořit instanci jednoho z těchto typů s parametry požadovaného typu.</span><span class="sxs-lookup"><span data-stu-id="72ebd-136">You can simply instantiate one of these types with the required type parameters.</span></span> <span data-ttu-id="72ebd-137">V případě algoritmů, které mohou být provedeny obecný tyto delegáty slouží jako obecné typy.</span><span class="sxs-lookup"><span data-stu-id="72ebd-137">In the case of algorithms that can be made generic, these delegates can be used as generic types.</span></span> 

<span data-ttu-id="72ebd-138">To by měl šetří čas a minimalizovat počet nových typů, které je potřeba vytvořit za účelem práce s delegátů.</span><span class="sxs-lookup"><span data-stu-id="72ebd-138">This should save time, and minimize the number of new types that you need to create in order to work with delegates.</span></span>

<span data-ttu-id="72ebd-139">V následujícím článku uvidíte několik běžných vzorů pro práci s Delegáti v praxi.</span><span class="sxs-lookup"><span data-stu-id="72ebd-139">In the next article, you'll see several common patterns for working with delegates in practice.</span></span>

[<span data-ttu-id="72ebd-140">Next</span><span class="sxs-lookup"><span data-stu-id="72ebd-140">Next</span></span>](delegates-patterns.md)
