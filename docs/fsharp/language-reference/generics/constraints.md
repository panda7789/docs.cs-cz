---
title: Omezení
description: Přečtěte F# si o omezeních, která se vztahují na parametry obecného typu k určení požadavků pro argument typu v obecném typu nebo funkci.
ms.date: 05/16/2016
ms.openlocfilehash: 70a8bec1ad67d7e814cb7a96b1876bb22399c5e7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425019"
---
# <a name="constraints"></a><span data-ttu-id="bf2ca-103">Omezení</span><span class="sxs-lookup"><span data-stu-id="bf2ca-103">Constraints</span></span>

<span data-ttu-id="bf2ca-104">Toto téma popisuje omezení, která lze použít na parametry obecného typu k určení požadavků pro argument typu v obecném typu nebo funkci.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf2ca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf2ca-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="bf2ca-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf2ca-106">Remarks</span></span>

<span data-ttu-id="bf2ca-107">Existuje několik různých omezení, která lze použít pro omezení typů, které lze použít v obecném typu.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="bf2ca-108">Následující tabulka uvádí a popisuje tato omezení.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="bf2ca-109">Jedinečn</span><span class="sxs-lookup"><span data-stu-id="bf2ca-109">Constraint</span></span>|<span data-ttu-id="bf2ca-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf2ca-110">Syntax</span></span>|<span data-ttu-id="bf2ca-111">Popis</span><span class="sxs-lookup"><span data-stu-id="bf2ca-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="bf2ca-112">Omezení typu</span><span class="sxs-lookup"><span data-stu-id="bf2ca-112">Type Constraint</span></span>|<span data-ttu-id="bf2ca-113">*typ-parametr* :&gt; *typ*</span><span class="sxs-lookup"><span data-stu-id="bf2ca-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="bf2ca-114">Poskytnutý typ musí být roven nebo odvozen od zadaného typu, nebo, pokud je typ rozhraní, poskytnutý typ musí implementovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="bf2ca-115">Omezení hodnoty null</span><span class="sxs-lookup"><span data-stu-id="bf2ca-115">Null Constraint</span></span>|<span data-ttu-id="bf2ca-116">*parametr typu* : null</span><span class="sxs-lookup"><span data-stu-id="bf2ca-116">*type-parameter* : null</span></span>|<span data-ttu-id="bf2ca-117">Poskytnutý typ musí podporovat literál s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-117">The provided type must support the null literal.</span></span> <span data-ttu-id="bf2ca-118">To zahrnuje všechny typy objektů rozhraní .NET, F# ale ne seznam, řazené kolekce členů, funkce, třídy, záznam nebo sjednocení.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="bf2ca-119">Explicitní omezení členů</span><span class="sxs-lookup"><span data-stu-id="bf2ca-119">Explicit Member Constraint</span></span>|<span data-ttu-id="bf2ca-120">[(]*typ-parametr* [nebo... nebo *parametr typu*)]: (*Member-Signature*)</span><span class="sxs-lookup"><span data-stu-id="bf2ca-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="bf2ca-121">Aspoň jeden z poskytnutých argumentů typu musí mít člena, který má zadaný podpis. není určeno pro běžné použití.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="bf2ca-122">Členy musí být buď explicitně definovány pro typ nebo část rozšíření implicitního typu, aby byly platnými cíli pro explicitní omezení členů.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="bf2ca-123">Omezení konstruktoru</span><span class="sxs-lookup"><span data-stu-id="bf2ca-123">Constructor Constraint</span></span>|<span data-ttu-id="bf2ca-124">*parametr typu* : (New: unit-&gt; ' a)</span><span class="sxs-lookup"><span data-stu-id="bf2ca-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="bf2ca-125">Poskytnutý typ musí mít konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-125">The provided type must have a parameterless constructor.</span></span>|
|<span data-ttu-id="bf2ca-126">Omezení typu hodnoty</span><span class="sxs-lookup"><span data-stu-id="bf2ca-126">Value Type Constraint</span></span>|<span data-ttu-id="bf2ca-127">: struct</span><span class="sxs-lookup"><span data-stu-id="bf2ca-127">: struct</span></span>|<span data-ttu-id="bf2ca-128">Poskytnutý typ musí být typ hodnoty .NET.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="bf2ca-129">Omezení typu odkazu</span><span class="sxs-lookup"><span data-stu-id="bf2ca-129">Reference Type Constraint</span></span>|<span data-ttu-id="bf2ca-130">: not struct</span><span class="sxs-lookup"><span data-stu-id="bf2ca-130">: not struct</span></span>|<span data-ttu-id="bf2ca-131">Poskytnutý typ musí být typ odkazu .NET.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="bf2ca-132">Omezení typu výčtu</span><span class="sxs-lookup"><span data-stu-id="bf2ca-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="bf2ca-133">: enum&lt;*podkladového typu*&gt;</span><span class="sxs-lookup"><span data-stu-id="bf2ca-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="bf2ca-134">Poskytnutý typ musí být Výčtový typ, který má zadaný základní typ. není určeno pro běžné použití.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="bf2ca-135">Omezení delegování</span><span class="sxs-lookup"><span data-stu-id="bf2ca-135">Delegate Constraint</span></span>|<span data-ttu-id="bf2ca-136">: Delegate&lt;*řazené kolekce členů-typ parametru*, *návratový typ*&gt;</span><span class="sxs-lookup"><span data-stu-id="bf2ca-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="bf2ca-137">Poskytnutý typ musí být delegovaný typ, který má zadané argumenty a návratovou hodnotu. není určeno pro běžné použití.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="bf2ca-138">Omezení porovnání</span><span class="sxs-lookup"><span data-stu-id="bf2ca-138">Comparison Constraint</span></span>|<span data-ttu-id="bf2ca-139">: porovnání</span><span class="sxs-lookup"><span data-stu-id="bf2ca-139">: comparison</span></span>|<span data-ttu-id="bf2ca-140">Poskytnutý typ musí podporovat porovnání.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="bf2ca-141">Omezení rovnosti</span><span class="sxs-lookup"><span data-stu-id="bf2ca-141">Equality Constraint</span></span>|<span data-ttu-id="bf2ca-142">: rovnost</span><span class="sxs-lookup"><span data-stu-id="bf2ca-142">: equality</span></span>|<span data-ttu-id="bf2ca-143">Poskytnutý typ musí podporovat rovnost.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="bf2ca-144">Nespravované omezení</span><span class="sxs-lookup"><span data-stu-id="bf2ca-144">Unmanaged Constraint</span></span>|<span data-ttu-id="bf2ca-145">: nespravované</span><span class="sxs-lookup"><span data-stu-id="bf2ca-145">: unmanaged</span></span>|<span data-ttu-id="bf2ca-146">Poskytnutý typ musí být nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="bf2ca-147">Nespravované typy jsou buď určité primitivní typy (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`nebo `decimal`), výčtové typy, `nativeptr<_>`nebo neobecnou strukturu, jejíž pole jsou všechny nespravované typy.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr<_>`, or a non-generic structure whose fields are all unmanaged types.</span></span>|

<span data-ttu-id="bf2ca-148">Je nutné přidat omezení, pokud váš kód musí používat funkci, která je k dispozici pro typ omezení, ale ne pro obecné typy.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="bf2ca-149">Například pokud použijete omezení typu k určení typu třídy, můžete použít libovolnou z metod této třídy v obecné funkci nebo typu.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="bf2ca-150">Určení omezení se někdy vyžaduje při explicitním zápisu parametrů typu, protože bez omezení nemá kompilátor žádný způsob, jak ověřit, že funkce, které používáte, budou k dispozici pro libovolný typ, který může být dodán v době běhu pro daný typ. ukazatele.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="bf2ca-151">Nejběžnějšími omezeními, která používáte F# v kódu, jsou omezení typu, která určují základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="bf2ca-152">Ostatní omezení používá knihovna k implementaci určitých funkcí F# , jako je například explicitní omezení členů, které se používá k implementaci přetížení operátoru pro aritmetické operátory nebo jsou k dispozici hlavně z těchto důvodů F# . podporuje kompletní sadu omezení, která je podporována modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="bf2ca-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="bf2ca-153">Během procesu odvození typu je některá omezení odvozena automaticky kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="bf2ca-154">Například pokud použijete operátor `+` ve funkci, kompilátor odvodí explicitní omezení členů u typů proměnných, které se používají ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="bf2ca-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="bf2ca-155">Následující kód ilustruje některé deklarace omezení:</span><span class="sxs-lookup"><span data-stu-id="bf2ca-155">The following code illustrates some constraint declarations:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bf2ca-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bf2ca-156">See also</span></span>

- [<span data-ttu-id="bf2ca-157">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="bf2ca-157">Generics</span></span>](index.md)
- [<span data-ttu-id="bf2ca-158">Omezení</span><span class="sxs-lookup"><span data-stu-id="bf2ca-158">Constraints</span></span>](constraints.md)
