---
title: Omezení (F#)
description: 'Další informace o F # omezení, které se vztahují na parametry obecného typu k určení požadavků pro argument typu v obecném typu nebo funkce.'
ms.date: 05/16/2016
ms.openlocfilehash: 9534db4ffd195022366af8c993658bd94f375f53
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "48837348"
---
# <a name="constraints"></a>Omezení

Toto téma popisuje omezení, která můžete použít pro obecný typ parametry k určení požadavků pro argument typu v obecném typu nebo funkce.

## <a name="syntax"></a>Syntaxe

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Poznámky

Existuje několik jiná omezení, které lze použít k omezení typů, které je možné v obecném typu. Následující tabulka uvádí a popisuje těchto omezení.

|Omezení|Syntaxe|Popis|
|----------|------|-----------|
|Omezení typu|*parametr typu* :&gt; *typu*|Zadaný typ musí být větší nebo odvozené od typu určeného nebo, pokud je typ rozhraní, zadaný typ musí implementovat rozhraní.|
|Omezení s hodnotou Null|*parametr typu* : null|Zadaný typ musí podporovat literál s hodnotou null. To zahrnuje všechny typy objektů .NET, ale není F # seznamu, řazené kolekce členů, funkce, třídy, záznamu nebo typy sjednocení.|
|Omezení explicitního člena|[(]*parametr typu* [nebo... nebo *parametr typu*)]: (*signatura člena*)|Nejméně jeden z argumentů typu, který je k dispozici musí mít člena, který má zadaný podpis; nejsou určené pro obecné použití. Členy musí být buď explicitně definované u typu nebo součást rozšíření implicitních typů, bude platné cíle pro explicitní člen omezení.|
|Omezení konstruktoru|*parametr typu* : (nové: jednotka –&gt; :)|Zadaný typ musí mít výchozí konstruktor.|
|Omezení typu hodnoty|: – struktura|Zadaný typ musí být typem hodnoty .NET.|
|Omezení typu odkazu|: není – struktura|Zadaný typ musí být odkazový typ .NET.|
|Omezení typu výčtu|: výčtu&lt;*základní typ*&gt;|Zadaný typ musí být výčtového typu, který má zadaný podkladový typ; nejsou určené pro obecné použití.|
|Omezení delegáta|: delegovat&lt;*typ řazené kolekce členů parametru*, *návratový typ*&gt;|Zadaný typ musí být typem delegáta, který má zadané argumenty a vrátí hodnotu; nejsou určené pro obecné použití.|
|Porovnání omezení|: porovnání|Zadaný typ musí podporovat porovnání.|
|Omezení rovnosti|: rovnosti|Zadaný typ musí podporovat rovnosti.|
|Nespravované omezení|: nespravovaných|Zadaný typ musí být nespravovaným typem. Nespravované typy jsou určité primitivní typy (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, nebo `decimal`), výčtové typy `nativeptr<_>`, nebo strukturu neobecnou jehož pole jsou všechny nespravovaných typů.|
Je nutné přidat omezení, pokud má váš kód používat funkce, která je obecně dostupná v omezení typu, ale ne v typy. Například pokud používáte omezení typu k určení typu třídy, můžete použít některou z metod této třídy v typu nebo obecné funkce.

Určení omezení je to někdy nezbytné při zápisu parametry typu explicitně, protože bez omezení, kompilátor neobsahuje nijak ověřit, že bude k dispozici na libovolný typ, který může být zadán v době běhu pro typ funkce, které používáte parametr.

Nejběžnější omezení, které můžete použít v kódu F # se omezení typu, které určují základní třídy nebo rozhraní. Další omezení buď používají knihovny F # pro některé funkce, jako je například omezení explicitního člena, který se používá k implementaci pro aritmetické operátory přetížení operátoru nebo jsou k dispozici zejména proto, že jazyk F # podporuje úplnou implementaci Sada omezení, která je podporována modulem common language runtime.

Během procesu odvození typu jsou některá omezení vyvozena na základě kompilátor automaticky. Například, pokud použijete `+` operátor ve funkci, kompilátor odvodí omezením explicitního člena na tyto typy proměnných, které se používají ve výrazu.

Následující kód ukazuje některé deklarace omezení.

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

## <a name="see-also"></a>Viz také:

- [Obecné typy](index.md)
- [Omezení](constraints.md)
