---
title: Omezení
description: Přečtěte F# si o omezeních, která se vztahují na parametry obecného typu k určení požadavků pro argument typu v obecném typu nebo funkci.
ms.date: 05/16/2016
ms.openlocfilehash: 9912ba63138d893a7c616661dd2b1cbdbe51916c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736794"
---
# <a name="constraints"></a>Omezení

Toto téma popisuje omezení, která lze použít na parametry obecného typu k určení požadavků pro argument typu v obecném typu nebo funkci.

## <a name="syntax"></a>Syntaxe

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Poznámky

Existuje několik různých omezení, která lze použít pro omezení typů, které lze použít v obecném typu. Následující tabulka uvádí a popisuje tato omezení.

|Jedinečn|Syntaxe|Popis|
|----------|------|-----------|
|Omezení typu|*typ-parametr* : &gt; *typ*|Poskytnutý typ musí být roven nebo odvozen od zadaného typu, nebo, pokud je typ rozhraní, poskytnutý typ musí implementovat rozhraní.|
|Omezení hodnoty null|*parametr typu* : null|Poskytnutý typ musí podporovat literál s hodnotou null. To zahrnuje všechny typy objektů rozhraní .NET, F# ale ne seznam, řazené kolekce členů, funkce, třídy, záznam nebo sjednocení.|
|Explicitní omezení členů|[(]*typ-parametr* [nebo... nebo *parametr typu*)]: (*Member-Signature*)|Aspoň jeden z poskytnutých argumentů typu musí mít člena, který má zadaný podpis. není určeno pro běžné použití. Členy musí být buď explicitně definovány pro typ nebo část rozšíření implicitního typu, aby byly platnými cíli pro explicitní omezení členů.|
|Omezení konstruktoru|*parametr typu* : (New: unit-&gt; ' a)|Poskytnutý typ musí mít konstruktor bez parametrů.|
|Omezení typu hodnoty|: struct|Poskytnutý typ musí být typ hodnoty .NET.|
|Omezení typu odkazu|: not struct|Poskytnutý typ musí být typ odkazu .NET.|
|Omezení typu výčtu|: enum @ no__t-0*podkladového typu*&gt;|Poskytnutý typ musí být Výčtový typ, který má zadaný základní typ. není určeno pro běžné použití.|
|Omezení delegování|: Delegate @ no__t-0*řazené kolekce členů – typ parametru*, *návratový typ*&gt;|Poskytnutý typ musí být delegovaný typ, který má zadané argumenty a návratovou hodnotu. není určeno pro běžné použití.|
|Omezení porovnání|: porovnání|Poskytnutý typ musí podporovat porovnání.|
|Omezení rovnosti|: rovnost|Poskytnutý typ musí podporovat rovnost.|
|Nespravované omezení|: nespravované|Poskytnutý typ musí být nespravovaný typ. Nespravované typy jsou buď některé primitivní typy (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, 0, 1, 2 nebo 3), výčtové typy, 4 nebo neobecné. struktura, jejíž pole jsou všechny nespravované typy.|

Je nutné přidat omezení, pokud váš kód musí používat funkci, která je k dispozici pro typ omezení, ale ne pro obecné typy. Například pokud použijete omezení typu k určení typu třídy, můžete použít libovolnou z metod této třídy v obecné funkci nebo typu.

Určení omezení se někdy vyžaduje při explicitním zápisu parametrů typu, protože bez omezení nemá kompilátor žádný způsob, jak ověřit, že funkce, které používáte, budou k dispozici pro libovolný typ, který může být dodán v době běhu pro daný typ. ukazatele.

Nejběžnějšími omezeními, která používáte F# v kódu, jsou omezení typu, která určují základní třídy nebo rozhraní. Ostatní omezení používá knihovna k implementaci určitých funkcí F# , jako je například explicitní omezení členů, které se používá k implementaci přetížení operátoru pro aritmetické operátory nebo jsou k dispozici hlavně z těchto důvodů F# . podporuje kompletní sadu omezení, která je podporována modulem CLR (Common Language Runtime).

Během procesu odvození typu je některá omezení odvozena automaticky kompilátorem. Například pokud použijete operátor `+` ve funkci, kompilátor odvodí explicitní omezení členů u typů proměnných, které se používají ve výrazu.

Následující kód ilustruje některé deklarace omezení:

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

## <a name="see-also"></a>Další informace najdete v tématech

- [Obecné typy](index.md)
- [Jednotlivým](constraints.md)
