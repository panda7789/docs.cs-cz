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
# <a name="constraints"></a>Omezení

Toto téma popisuje omezení, která můžete použít pro obecný typ parametry k určení požadavků pro typ argument obecného typu nebo funkce.


## <a name="syntax"></a>Syntaxe

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Poznámky
Existuje několik různých omezení, která můžete použít k omezení typy, které mohou být používány obecného typu. Následující tabulka uvádí a popisuje těchto omezení.

|Omezení|Syntaxe|Popis|
|----------|------|-----------|
|Omezení typu.|*parametr typu* :&gt; *typu*|Zadaný typ musí být rovna nebo odvozené od zadaný typ, nebo, pokud je typ rozhraní, zadaný typ musí implementovat rozhraní.|
|Omezení hodnotu Null.|*parametr typu* : hodnotu null.|Zadaný typ musí podporovat literál null. To zahrnuje všechny typy objektů .NET, ale není F # seznamu, řazené kolekce členů, funkce, – třída, záznamu nebo typy union.|
|Omezení explicitního člena|[()]*parametr typu* [nebo... nebo *parametr typu*)]: (* člen podpis *)|Alespoň jeden ze zadaných argumentů typ musí mít člena, který má zadaný podpis; není určena pro běžné. Členové v musí být buď explicitně definován typ nebo součástí rozšíření implicitní typ jako platné cíle explicitní člen omezení.|
|Omezení – konstruktor|*parametr typu* : (nové: jednotka -&gt; se)|Zadaný typ musí mít výchozí konstruktor.|
|Omezení typu hodnoty|: – struktura|Zadaný typ musí být typu .NET hodnoty.|
|Omezení typu odkazu|: není – struktura|Zadaný typ musí být odkazového typu .NET.|
|Omezení typu – výčet|: výčtu&lt;*základní typ*&gt;|Zadaný typ musí být výčtového typu, který má zadaný základní typ; není určena pro běžné.|
|Delegát omezení|: delegovat&lt;*typ parametru řazené kolekce členů*, *návratový typ*&gt;|Zadaný typ musí být typu delegáta, který má zadané argumenty a vrátit hodnotu; není určena pro běžné.|
|Porovnání omezení|: porovnání|Zadaný typ musí podporovat porovnání.|
|Omezení rovnosti|: rovnosti|Zadaný typ musí podporovat rovnosti.|
|Nespravované omezení|: nespravované|Zadaný typ musí být typ nespravované. Nespravované typy jsou buď určité primitivní typy (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, nebo `decimal`), výčtové typy `nativeptr&lt;_&gt;`, nebo neobecné strukturu, jejichž pole jsou všechny nespravované typy.|
Budete muset přidat omezení při použití funkce, která je k dispozici na typ omezení, ale ne v typy obecně má váš kód. Například pokud omezení typu se používá k určení typu třídy, můžete použít jednu z metod této třídy v obecné funkce nebo typu.

Určení omezení je to někdy nezbytné při zápisu parametry typu explicitně, protože bez omezení, kompilátor nemá možnost nijak ověřit, že funkce, které používáte, bude k dispozici na žádné typu, který může být v době běhu pro typ parametr.

Nejběžnější omezení, která používáte v F # – kód jsou omezení typu, které určují základní třídy nebo rozhraní. Jiná omezení jsou buď používaný knihovnou F # implementovat určité funkce, například omezení explicitního člena, který se používá k implementaci pro aritmetické operátory přetížení operátoru nebo jsou k dispozici především, protože F # podporuje kompletní sadu omezení, která podporuje modul common language runtime.

Během procesu odvození typu jsou některá omezení vyvozena na základě kompilátor automaticky. Například pokud použijete `+` operátor ve funkci, kompilátor odvodí omezení explicitního člena na typy proměnných, které se používají ve výrazu.

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

## <a name="see-also"></a>Viz také
[Obecné typy](index.md)

[Omezení](constraints.md)
