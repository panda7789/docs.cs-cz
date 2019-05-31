---
title: Omezení
description: Další informace o F# omezení, které se vztahují na parametry obecného typu k určení požadavků pro argument typu v obecném typu nebo funkce.
ms.date: 05/16/2016
ms.openlocfilehash: bb6625636f0465dd608ae2e8a8986d043b62b6e4
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378186"
---
# <a name="constraints"></a><span data-ttu-id="d695a-103">Omezení</span><span class="sxs-lookup"><span data-stu-id="d695a-103">Constraints</span></span>

<span data-ttu-id="d695a-104">Toto téma popisuje omezení, která můžete použít pro obecný typ parametry k určení požadavků pro argument typu v obecném typu nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="d695a-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="d695a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d695a-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="d695a-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d695a-106">Remarks</span></span>

<span data-ttu-id="d695a-107">Existuje několik jiná omezení, které lze použít k omezení typů, které je možné v obecném typu.</span><span class="sxs-lookup"><span data-stu-id="d695a-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="d695a-108">Následující tabulka uvádí a popisuje těchto omezení.</span><span class="sxs-lookup"><span data-stu-id="d695a-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="d695a-109">Omezení</span><span class="sxs-lookup"><span data-stu-id="d695a-109">Constraint</span></span>|<span data-ttu-id="d695a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d695a-110">Syntax</span></span>|<span data-ttu-id="d695a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="d695a-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="d695a-112">Omezení typu</span><span class="sxs-lookup"><span data-stu-id="d695a-112">Type Constraint</span></span>|<span data-ttu-id="d695a-113">*parametr typu* :&gt; *typu*</span><span class="sxs-lookup"><span data-stu-id="d695a-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="d695a-114">Zadaný typ musí být větší nebo odvozené od typu určeného nebo, pokud je typ rozhraní, zadaný typ musí implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d695a-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="d695a-115">Omezení s hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="d695a-115">Null Constraint</span></span>|<span data-ttu-id="d695a-116">*parametr typu* : null</span><span class="sxs-lookup"><span data-stu-id="d695a-116">*type-parameter* : null</span></span>|<span data-ttu-id="d695a-117">Zadaný typ musí podporovat literál s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="d695a-117">The provided type must support the null literal.</span></span> <span data-ttu-id="d695a-118">To zahrnuje všechny typy objektů .NET, ale ne F# seznamu, řazené kolekce členů, funkce, třídy, záznam nebo typy sjednocení.</span><span class="sxs-lookup"><span data-stu-id="d695a-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="d695a-119">Omezení explicitního člena</span><span class="sxs-lookup"><span data-stu-id="d695a-119">Explicit Member Constraint</span></span>|<span data-ttu-id="d695a-120">[(]*parametr typu* [nebo... nebo *parametr typu*)]: (*signatura člena*)</span><span class="sxs-lookup"><span data-stu-id="d695a-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="d695a-121">Nejméně jeden z argumentů typu, který je k dispozici musí mít člena, který má zadaný podpis; nejsou určené pro obecné použití.</span><span class="sxs-lookup"><span data-stu-id="d695a-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="d695a-122">Členy musí být buď explicitně definované u typu nebo součást rozšíření implicitních typů, bude platné cíle pro explicitní člen omezení.</span><span class="sxs-lookup"><span data-stu-id="d695a-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="d695a-123">Omezení konstruktoru</span><span class="sxs-lookup"><span data-stu-id="d695a-123">Constructor Constraint</span></span>|<span data-ttu-id="d695a-124">*parametr typu* : (nové: jednotka –&gt; :)</span><span class="sxs-lookup"><span data-stu-id="d695a-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="d695a-125">Zadaný typ musí mít výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d695a-125">The provided type must have a default constructor.</span></span>|
|<span data-ttu-id="d695a-126">Omezení typu hodnoty</span><span class="sxs-lookup"><span data-stu-id="d695a-126">Value Type Constraint</span></span>|<span data-ttu-id="d695a-127">: – struktura</span><span class="sxs-lookup"><span data-stu-id="d695a-127">: struct</span></span>|<span data-ttu-id="d695a-128">Zadaný typ musí být typem hodnoty .NET.</span><span class="sxs-lookup"><span data-stu-id="d695a-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="d695a-129">Omezení typu odkazu</span><span class="sxs-lookup"><span data-stu-id="d695a-129">Reference Type Constraint</span></span>|<span data-ttu-id="d695a-130">: není – struktura</span><span class="sxs-lookup"><span data-stu-id="d695a-130">: not struct</span></span>|<span data-ttu-id="d695a-131">Zadaný typ musí být odkazový typ .NET.</span><span class="sxs-lookup"><span data-stu-id="d695a-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="d695a-132">Omezení typu výčtu</span><span class="sxs-lookup"><span data-stu-id="d695a-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="d695a-133">: výčtu&lt;*základní typ*&gt;</span><span class="sxs-lookup"><span data-stu-id="d695a-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="d695a-134">Zadaný typ musí být výčtového typu, který má zadaný podkladový typ; nejsou určené pro obecné použití.</span><span class="sxs-lookup"><span data-stu-id="d695a-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="d695a-135">Omezení delegáta</span><span class="sxs-lookup"><span data-stu-id="d695a-135">Delegate Constraint</span></span>|<span data-ttu-id="d695a-136">: delegovat&lt;*typ řazené kolekce členů parametru*, *návratový typ*&gt;</span><span class="sxs-lookup"><span data-stu-id="d695a-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="d695a-137">Zadaný typ musí být typem delegáta, který má zadané argumenty a vrátí hodnotu; nejsou určené pro obecné použití.</span><span class="sxs-lookup"><span data-stu-id="d695a-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="d695a-138">Porovnání omezení</span><span class="sxs-lookup"><span data-stu-id="d695a-138">Comparison Constraint</span></span>|<span data-ttu-id="d695a-139">: porovnání</span><span class="sxs-lookup"><span data-stu-id="d695a-139">: comparison</span></span>|<span data-ttu-id="d695a-140">Zadaný typ musí podporovat porovnání.</span><span class="sxs-lookup"><span data-stu-id="d695a-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="d695a-141">Omezení rovnosti</span><span class="sxs-lookup"><span data-stu-id="d695a-141">Equality Constraint</span></span>|<span data-ttu-id="d695a-142">: rovnosti</span><span class="sxs-lookup"><span data-stu-id="d695a-142">: equality</span></span>|<span data-ttu-id="d695a-143">Zadaný typ musí podporovat rovnosti.</span><span class="sxs-lookup"><span data-stu-id="d695a-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="d695a-144">Nespravované omezení</span><span class="sxs-lookup"><span data-stu-id="d695a-144">Unmanaged Constraint</span></span>|<span data-ttu-id="d695a-145">: nespravovaných</span><span class="sxs-lookup"><span data-stu-id="d695a-145">: unmanaged</span></span>|<span data-ttu-id="d695a-146">Zadaný typ musí být nespravovaným typem.</span><span class="sxs-lookup"><span data-stu-id="d695a-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="d695a-147">Nespravované typy jsou určité primitivní typy (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, nebo `decimal`), výčtové typy `nativeptr<_>`, nebo strukturu neobecnou jehož pole jsou všechny nespravovaných typů.</span><span class="sxs-lookup"><span data-stu-id="d695a-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr<_>`, or a non-generic structure whose fields are all unmanaged types.</span></span>|

<span data-ttu-id="d695a-148">Je nutné přidat omezení, pokud má váš kód používat funkce, která je obecně dostupná v omezení typu, ale ne v typy.</span><span class="sxs-lookup"><span data-stu-id="d695a-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="d695a-149">Například pokud používáte omezení typu k určení typu třídy, můžete použít některou z metod této třídy v typu nebo obecné funkce.</span><span class="sxs-lookup"><span data-stu-id="d695a-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="d695a-150">Určení omezení je to někdy nezbytné při zápisu parametry typu explicitně, protože bez omezení, kompilátor neobsahuje nijak ověřit, že bude k dispozici na libovolný typ, který může být zadán v době běhu pro typ funkce, které používáte parametr.</span><span class="sxs-lookup"><span data-stu-id="d695a-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="d695a-151">Nejběžnější omezení použít v F# kódu se omezení typu, které určují základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d695a-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="d695a-152">Další omezení jsou používány buď F# knihovny implementovat určité funkce, jako je například omezení explicitního člena, který se používá k implementaci pro aritmetické operátory přetížení operátoru nebo hlavně, protože jsou k dispozici F# podporuje kompletní sadu omezení, která je podporována modulem common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d695a-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="d695a-153">Během procesu odvození typu jsou některá omezení vyvozena na základě kompilátor automaticky.</span><span class="sxs-lookup"><span data-stu-id="d695a-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="d695a-154">Například, pokud použijete `+` operátor ve funkci, kompilátor odvodí omezením explicitního člena na tyto typy proměnných, které se používají ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="d695a-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="d695a-155">Následující kód ukazuje některé deklarace omezení.</span><span class="sxs-lookup"><span data-stu-id="d695a-155">The following code illustrates some constraint declarations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d695a-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d695a-156">See also</span></span>

- [<span data-ttu-id="d695a-157">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="d695a-157">Generics</span></span>](index.md)
- [<span data-ttu-id="d695a-158">Omezení</span><span class="sxs-lookup"><span data-stu-id="d695a-158">Constraints</span></span>](constraints.md)
