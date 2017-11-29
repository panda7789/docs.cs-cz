---
title: "Omezení (F#)"
description: "Další informace o F # omezení, které se vztahují na parametry obecného typu k určení požadavků pro typ argument obecného typu nebo funkce."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 2f232a3a-9486-48fb-9759-f23404ed4b52
ms.openlocfilehash: 91854fd2f692688e0f1c27aba1422eff64156048
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="constraints"></a><span data-ttu-id="9ad2a-104">Omezení</span><span class="sxs-lookup"><span data-stu-id="9ad2a-104">Constraints</span></span>

<span data-ttu-id="9ad2a-105">Toto téma popisuje omezení, která můžete použít pro obecný typ parametry k určení požadavků pro typ argument obecného typu nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-105">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>


## <a name="syntax"></a><span data-ttu-id="9ad2a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ad2a-106">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="9ad2a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9ad2a-107">Remarks</span></span>
<span data-ttu-id="9ad2a-108">Existuje několik různých omezení, která můžete použít k omezení typy, které mohou být používány obecného typu.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-108">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="9ad2a-109">Následující tabulka uvádí a popisuje těchto omezení.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-109">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="9ad2a-110">Omezení</span><span class="sxs-lookup"><span data-stu-id="9ad2a-110">Constraint</span></span>|<span data-ttu-id="9ad2a-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ad2a-111">Syntax</span></span>|<span data-ttu-id="9ad2a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9ad2a-112">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="9ad2a-113">Omezení typu.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-113">Type Constraint</span></span>|<span data-ttu-id="9ad2a-114">*parametr typu* :&gt; *typu*</span><span class="sxs-lookup"><span data-stu-id="9ad2a-114">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="9ad2a-115">Zadaný typ musí být rovna nebo odvozené od zadaný typ, nebo, pokud je typ rozhraní, zadaný typ musí implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-115">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="9ad2a-116">Omezení hodnotu Null.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-116">Null Constraint</span></span>|<span data-ttu-id="9ad2a-117">*parametr typu* : hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-117">*type-parameter* : null</span></span>|<span data-ttu-id="9ad2a-118">Zadaný typ musí podporovat literál null.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-118">The provided type must support the null literal.</span></span> <span data-ttu-id="9ad2a-119">To zahrnuje všechny typy objektů .NET, ale není F # seznamu, řazené kolekce členů, funkce, – třída, záznamu nebo typy union.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-119">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="9ad2a-120">Omezení explicitního člena</span><span class="sxs-lookup"><span data-stu-id="9ad2a-120">Explicit Member Constraint</span></span>|<span data-ttu-id="9ad2a-121">[()]*parametr typu* [nebo... nebo *parametr typu*)]: (* člen podpis *)</span><span class="sxs-lookup"><span data-stu-id="9ad2a-121">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature *)</span></span>|<span data-ttu-id="9ad2a-122">Alespoň jeden ze zadaných argumentů typ musí mít člena, který má zadaný podpis; není určena pro běžné.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-122">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="9ad2a-123">Členové v musí být buď explicitně definován typ nebo součástí rozšíření implicitní typ jako platné cíle explicitní člen omezení.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-123">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="9ad2a-124">Omezení – konstruktor</span><span class="sxs-lookup"><span data-stu-id="9ad2a-124">Constructor Constraint</span></span>|<span data-ttu-id="9ad2a-125">*parametr typu* : (nové: jednotka -&gt; se)</span><span class="sxs-lookup"><span data-stu-id="9ad2a-125">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="9ad2a-126">Zadaný typ musí mít výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-126">The provided type must have a default constructor.</span></span>|
|<span data-ttu-id="9ad2a-127">Omezení typu hodnoty</span><span class="sxs-lookup"><span data-stu-id="9ad2a-127">Value Type Constraint</span></span>|<span data-ttu-id="9ad2a-128">: – struktura</span><span class="sxs-lookup"><span data-stu-id="9ad2a-128">: struct</span></span>|<span data-ttu-id="9ad2a-129">Zadaný typ musí být typu .NET hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-129">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="9ad2a-130">Omezení typu odkazu</span><span class="sxs-lookup"><span data-stu-id="9ad2a-130">Reference Type Constraint</span></span>|<span data-ttu-id="9ad2a-131">: není – struktura</span><span class="sxs-lookup"><span data-stu-id="9ad2a-131">: not struct</span></span>|<span data-ttu-id="9ad2a-132">Zadaný typ musí být odkazového typu .NET.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-132">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="9ad2a-133">Omezení typu – výčet</span><span class="sxs-lookup"><span data-stu-id="9ad2a-133">Enumeration Type Constraint</span></span>|<span data-ttu-id="9ad2a-134">: výčtu&lt;*základní typ*&gt;</span><span class="sxs-lookup"><span data-stu-id="9ad2a-134">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="9ad2a-135">Zadaný typ musí být výčtového typu, který má zadaný základní typ; není určena pro běžné.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-135">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="9ad2a-136">Delegát omezení</span><span class="sxs-lookup"><span data-stu-id="9ad2a-136">Delegate Constraint</span></span>|<span data-ttu-id="9ad2a-137">: delegovat&lt;*typ parametru řazené kolekce členů*, *návratový typ*&gt;</span><span class="sxs-lookup"><span data-stu-id="9ad2a-137">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="9ad2a-138">Zadaný typ musí být typu delegáta, který má zadané argumenty a vrátit hodnotu; není určena pro běžné.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-138">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="9ad2a-139">Porovnání omezení</span><span class="sxs-lookup"><span data-stu-id="9ad2a-139">Comparison Constraint</span></span>|<span data-ttu-id="9ad2a-140">: porovnání</span><span class="sxs-lookup"><span data-stu-id="9ad2a-140">: comparison</span></span>|<span data-ttu-id="9ad2a-141">Zadaný typ musí podporovat porovnání.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-141">The provided type must support comparison.</span></span>|
|<span data-ttu-id="9ad2a-142">Omezení rovnosti</span><span class="sxs-lookup"><span data-stu-id="9ad2a-142">Equality Constraint</span></span>|<span data-ttu-id="9ad2a-143">: rovnosti</span><span class="sxs-lookup"><span data-stu-id="9ad2a-143">: equality</span></span>|<span data-ttu-id="9ad2a-144">Zadaný typ musí podporovat rovnosti.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-144">The provided type must support equality.</span></span>|
|<span data-ttu-id="9ad2a-145">Nespravované omezení</span><span class="sxs-lookup"><span data-stu-id="9ad2a-145">Unmanaged Constraint</span></span>|<span data-ttu-id="9ad2a-146">: nespravované</span><span class="sxs-lookup"><span data-stu-id="9ad2a-146">: unmanaged</span></span>|<span data-ttu-id="9ad2a-147">Zadaný typ musí být typ nespravované.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-147">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="9ad2a-148">Nespravované typy jsou buď určité primitivní typy (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, nebo `decimal`), výčtové typy `nativeptr&lt;_&gt;`, nebo neobecné strukturu, jejichž pole jsou všechny nespravované typy.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-148">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr&lt;_&gt;`, or a non-generic structure whose fields are all unmanaged types.</span></span>|
<span data-ttu-id="9ad2a-149">Budete muset přidat omezení při použití funkce, která je k dispozici na typ omezení, ale ne v typy obecně má váš kód.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-149">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="9ad2a-150">Například pokud omezení typu se používá k určení typu třídy, můžete použít jednu z metod této třídy v obecné funkce nebo typu.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-150">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="9ad2a-151">Určení omezení je to někdy nezbytné při zápisu parametry typu explicitně, protože bez omezení, kompilátor nemá možnost nijak ověřit, že funkce, které používáte, bude k dispozici na žádné typu, který může být v době běhu pro typ parametr.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-151">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="9ad2a-152">Nejběžnější omezení, která používáte v F # – kód jsou omezení typu, které určují základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-152">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="9ad2a-153">Jiná omezení jsou buď používaný knihovnou F # implementovat určité funkce, například omezení explicitního člena, který se používá k implementaci pro aritmetické operátory přetížení operátoru nebo jsou k dispozici především, protože F # podporuje kompletní sadu omezení, která podporuje modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-153">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="9ad2a-154">Během procesu odvození typu jsou některá omezení vyvozena na základě kompilátor automaticky.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-154">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="9ad2a-155">Například pokud použijete `+` operátor ve funkci, kompilátor odvodí omezení explicitního člena na typy proměnných, které se používají ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-155">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="9ad2a-156">Následující kód ukazuje některé deklarace omezení.</span><span class="sxs-lookup"><span data-stu-id="9ad2a-156">The following code illustrates some constraint declarations.</span></span>

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a><span data-ttu-id="9ad2a-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ad2a-157">See Also</span></span>
[<span data-ttu-id="9ad2a-158">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="9ad2a-158">Generics</span></span>](index.md)

[<span data-ttu-id="9ad2a-159">Omezení</span><span class="sxs-lookup"><span data-stu-id="9ad2a-159">Constraints</span></span>](constraints.md)
