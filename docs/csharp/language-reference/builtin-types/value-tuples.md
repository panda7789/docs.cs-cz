---
title: Tuple – typy – reference jazyka C#
description: 'Další informace o řazených kolekcích členů jazyka C#: zjednodušené datové struktury, které lze použít k seskupení volně souvisejících datových prvků'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: 3d79ab19117847e2364b154db33a1521416bb3f4
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174987"
---
# <a name="tuple-types-c-reference"></a>Tuple – typy (Referenční dokumentace jazyka C#)

K dispozici v C# 7,0 a novějších funkce *řazené kolekce členů* poskytuje stručnou syntaxi pro seskupení více datových elementů ve zjednodušené datové struktuře. Následující příklad ukazuje, jak lze deklarovat proměnnou řazené kolekce členů, inicializovat ji a přistupovat k jejím datovým členům:

[!code-csharp-interactive[tuple intro](snippets/ValueTuples.cs#Introduction)]

Jak ukazuje předchozí příklad, pro definování typu řazené kolekce členů, zadáte typy všech datových členů a volitelně také [názvy polí](#tuple-field-names). Nemůžete definovat metody v typu řazené kolekce členů, ale můžete použít metody poskytované rozhraním .NET, jak ukazuje následující příklad:

[!code-csharp-interactive[tuple methods](snippets/ValueTuples.cs#MethodOnTuples)]

Počínaje jazykem C# 7,3 typy řazené kolekce členů podporují [operátory rovnosti](../operators/equality-operators.md) `==` a `!=` . Další informace najdete v oddílu [rovnosti řazené kolekce členů](#tuple-equality) .

Typy řazené kolekce členů jsou [typy hodnot](value-types.md); prvky řazené kolekce členů jsou veřejné pole. Který zpřístupňuje řazené kolekce členů *proměnlivých* hodnotových typů.

> [!NOTE]
> Funkce řazené kolekce členů vyžaduje <xref:System.ValueTuple?displayProperty=nameWithType> typ a související obecné typy (například <xref:System.ValueTuple%602?displayProperty=nameWithType> ), které jsou k dispozici v rozhraní .NET Core a .NET Framework 4,7 a novější. Chcete-li použít řazené kolekce členů v projektu, který se zaměřuje na .NET Framework 4.6.2 nebo dříve, přidejte [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) do projektu balíček NuGet.

Můžete definovat řazené kolekce členů s libovolným velkým počtem prvků:

[!code-csharp-interactive[large tuple](snippets/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a>Použití případů řazených kolekcí členů

Jedním z nejběžnějších případů použití řazených kolekcí členů je jako návratový typ metody. To znamená, že namísto definování [ `out` parametrů metody](../keywords/out-parameter-modifier.md)lze seskupit metodu do návratového typu řazené kolekce členů, jak ukazuje následující příklad:

[!code-csharp-interactive[multiple method outputs](snippets/ValueTuples.cs#MultipleReturns)]

Jak ukazuje předchozí příklad, můžete pracovat s vrácenou instancí řazené kolekce členů přímo nebo ji [dekonstruovat](#tuple-assignment-and-deconstruction) v samostatných proměnných.

Namísto [anonymních typů](../../programming-guide/classes-and-structs/anonymous-types.md)lze také použít typy řazené kolekce členů; například v dotazech LINQ. Další informace najdete v tématu [Volba mezi anonymními a řazenými kolekcemi členů](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).

Obvykle používáte řazené kolekce členů k seskupení volně souvisejících datových prvků. To je obvykle užitečné v rámci privátních a interních nástrojů. V případě veřejného rozhraní API zvažte definování [třídy](../keywords/class.md) nebo typu [struktury](struct.md) .

## <a name="tuple-field-names"></a>Názvy polí řazené kolekce členů

Můžete explicitně zadat názvy polí řazené kolekce členů buď v inicializačním výrazu řazené kolekce členů, nebo v definici typu řazené kolekce členů, jak ukazuje následující příklad:

[!code-csharp-interactive[explicit field names](snippets/ValueTuples.cs#ExplicitFieldNames)]

Počínaje jazykem C# 7,1, pokud nezadáte název pole, může být odvozen z názvu odpovídající proměnné v inicializačním výrazu řazené kolekce členů, jak ukazuje následující příklad:

[!code-csharp-interactive[inferred field names](snippets/ValueTuples.cs#InferFieldNames)]

Označuje se jako Inicializátory řazené kolekce členů. Název proměnné není v následujících případech promítnut do pole řazené kolekce členů:

- Kandidátský název je název členu typu řazené kolekce členů, například, `Item3` , `ToString` nebo `Rest` .
- Název kandidáta je duplikátem jiného názvu pole řazené kolekce členů, ať už explicitního, nebo implicitního.

V těchto případech buď explicitně zadáte název pole, nebo přístup k poli s jeho výchozím názvem.

Výchozí názvy polí řazené kolekce členů `Item1` jsou `Item2` , `Item3` a tak dále. Můžete vždy použít výchozí název pole, a to i v případě, že je název pole zadán explicitně nebo odvozený, jak ukazuje následující příklad:

[!code-csharp-interactive[default field names](snippets/ValueTuples.cs#DefaultFieldNames)]

[Přiřazení řazené kolekce členů](#tuple-assignment-and-deconstruction) a [porovnání rovnosti řazené kolekce členů](#tuple-equality) nevezmou názvy polí v účtu.

V době kompilace kompilátor nahrazuje názvy polí, které nejsou výchozí, odpovídajícími výchozími názvy. V důsledku toho nejsou explicitně zadané nebo odvozené názvy polí k dispozici v době běhu.

## <a name="tuple-assignment-and-deconstruction"></a>Přiřazení a dekonstrukce řazené kolekce členů

Jazyk C# podporuje přiřazení mezi typy řazené kolekce členů, které splní obě následující podmínky:

- Oba typy řazené kolekce členů mají stejný počet elementů.
- u každé pozice řazené kolekce členů je typ prvku řazené kolekce členů stejný jako nebo implicitně převoditelné na typ odpovídajícího elementu řazené kolekce členů na levé straně.

Hodnoty prvků řazené kolekce členů jsou přiřazeny za pořadí prvků řazené kolekce členů. Názvy polí řazené kolekce členů jsou ignorovány a nejsou přiřazeny, jak ukazuje následující příklad:

[!code-csharp-interactive[tuple assignment](snippets/ValueTuples.cs#Assignment)]

Můžete také použít operátor přiřazení `=` k *dekonstrukci* instance řazené kolekce členů v samostatných proměnných. Můžete to udělat jedním z následujících způsobů:

- Explicitně deklarovat typ každé proměnné uvnitř závorek:

  [!code-csharp-interactive[specify types of variables](snippets/ValueTuples.cs#DeconstructExplicit)]

- Použijte `var` klíčové slovo mimo závorky k deklaraci implicitně typových proměnných a nechejte kompilátor odvodit své typy:

  [!code-csharp-interactive[implicitly typed variables](snippets/ValueTuples.cs#DeconstructVar)]

- Použít existující proměnné:

  [!code-csharp-interactive[existing variables](snippets/ValueTuples.cs#DeconstructExisting)]

Další informace o dekonstrukci řazených kolekcí členů a dalších typů naleznete v tématu [dekonstrukce řazených kolekcí členů a dalších typů](../../deconstruct.md).

## <a name="tuple-equality"></a>Rovnost řazené kolekce členů

Počínaje jazykem C# 7,3 typy řazené kolekce členů `==` podporují `!=` operátory a. Tyto operátory porovnávají členy operandu na levé straně s odpovídajícími členy pravého operandu po pořadí prvků řazené kolekce členů.

[!code-csharp-interactive[tuple equality](snippets/ValueTuples.cs#TupleEquality)]

Jak ukazuje předchozí příklad, `==` `!=` operace a neberou v úvahu názvy polí řazené kolekce členů.

Dvě řazené kolekce členů jsou srovnatelné, pokud jsou splněny obě následující podmínky:

- Obě řazené kolekce členů mají stejný počet elementů. Například `t1 != t2` není zkompilován, pokud `t1` a `t2` má různý počet prvků.
- Pro každou pozici řazené kolekce členů jsou odpovídající prvky z operandů řazené kolekce na levé straně a na pravé straně porovnatelné s `==` `!=` operátory a. Například není `(1, (2, 3)) == ((1, 2), 3)` zkompilován, protože není `1` porovnatelný s `(1, 2)` .

`==`Operátory a `!=` porovnávají řazené kolekce členů v podobě krátkodobého okruhu. To znamená, že operace se zastaví, jakmile splní pár nerovných prvků nebo dosáhne konců řazených kolekcí členů. Před jakýmkoli porovnáním však jsou vyhodnocovány *všechny* prvky řazené kolekce členů, jak ukazuje následující příklad:

[!code-csharp-interactive[tuple element evaluation](snippets/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a>Řazené kolekce členů jako výstupní parametry

Obvykle refaktorujte metodu, která má [ `out` parametry](../keywords/out-parameter-modifier.md) do metody, která vrací řazenou kolekci členů. Existují však případy, ve kterých `out` parametr může být typu řazené kolekce členů. Následující příklad ukazuje, jak pracovat s řazenými kolekcemi členů jako `out` parametry:

[!code-csharp-interactive[tuple as out parameter](snippets/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a>Řazené kolekce členů vs`System.Tuple`

Řazené kolekce členů jazyka C#, které jsou zálohovány <xref:System.ValueTuple?displayProperty=nameWithType> typy, se liší od řazených kolekcí členů, které jsou zastoupeny <xref:System.Tuple?displayProperty=nameWithType> typy. Hlavní rozdíly jsou následující:

- `ValueTuple`typy jsou [typy hodnot](value-types.md). `Tuple`typy jsou [odkazové typy](../keywords/reference-types.md).
- `ValueTuple`typy jsou proměnlivé. `Tuple`typy jsou neměnné.
- Datové členy `ValueTuple` typů jsou pole. Datové členy `Tuple` typů jsou vlastnosti.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v těchto poznámkách k návrhu funkcí:

- [Odvodit názvy řazených kolekcí členů (neboli inicializátorů řazené kolekce členů)](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [Podpora pro `==` `!=` typy řazené kolekce členů a](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Typy hodnot](value-types.md)
- [Volba mezi anonymními a řazenými typy řazených kolekcí členů](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>
