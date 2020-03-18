---
title: Omezení parametrů typu - Průvodce programováním jazyka C#
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: 76cd00b9c84f128d2a181115293df910d8deb6cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399796"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Omezení parametrů typu (Průvodce programováním jazyka C#)

Omezení informují kompilátor o schopnostech, které musí mít argument typu. Bez omezení může být argument typu libovolný typ. Kompilátor může převzít <xref:System.Object?displayProperty=nameWithType>pouze členy , což je konečná základní třída pro libovolný typ .NET. Další informace naleznete v tématu [Why use constraints](#why-use-constraints). Pokud se klientský kód pokusí vytvořit instanci vaší třídy pomocí typu, který není povolen omezením, výsledkem je chyba v době kompilace. Omezení jsou určena pomocí `where` kontextového klíčového slova. V následující tabulce je uvedeno sedm typů omezení:

|Omezení|Popis|
|----------------|-----------------|
|`where T : struct`|Argument typu musí být typ hodnoty s hodnotou, kterou nelze utnout. Informace o typech hodnot s možnou hodnotou s možnou hodnotou null naleznete v tématu [Nullable typy hodnot](../../language-reference/builtin-types/nullable-value-types.md). Vzhledem k tomu, že všechny typy `struct` hodnot `new()` mají přístupný konstruktor bez parametrů, omezení znamená omezení a nelze je kombinovat s omezením. `new()` Omezení také nelze `struct` kombinovat `unmanaged` s omezením.|
|`where T : class`|Argument typu musí být typ odkazu. Toto omezení platí také pro všechny třídy, rozhraní, delegáta nebo typu pole.|
|`where T : notnull`|Argument typu musí být typ, který nelze utnout. Argument může být typ odkazu s možnou hodnotou neshodnou v c# 8.0 nebo novějším nebo typ hodnoty, který nelze s nulovou hodnotou. Toto omezení platí také pro všechny třídy, rozhraní, delegáta nebo typu pole.|
|`where T : unmanaged`|Argument typu musí být [nespravovaný typ,](../../language-reference/builtin-types/unmanaged-types.md)který nelze utnout. Omezení `unmanaged` znamená `struct` omezení a nelze kombinovat s `struct` omezeními `new()` nebo.|
|`where T : new()`|Argument typu musí mít veřejný konstruktor bez parametrů. Při použití společně s jinými `new()` omezeními musí být omezení zadáno jako poslední. Omezení `new()` nelze kombinovat s `struct` a `unmanaged` omezení.|
|`where T :`*název základní třídy>\<*|Argument typu musí být nebo odvozen ze zadané základní třídy.|
|`where T :`>názvu rozhraní * \<*|Argument typu musí být nebo implementovat zadané rozhraní. Lze zadat více omezení rozhraní. Omezující rozhraní může být také obecné.|
|`where T : U`|Argument typu zadaný pro T musí být nebo odvozen z argumentu poskytnutého pro U.|

## <a name="why-use-constraints"></a>Proč používat omezení

Omezením parametru typu zvýšíte počet povolených operací a volání metod na ty, které jsou podporovány omezujícím typem a všemi typy v hierarchii dědičnosti. Při návrhu obecných tříd nebo metod, pokud budete provádět jakoukoli operaci na obecné členy <xref:System.Object?displayProperty=nameWithType>mimo jednoduché přiřazení nebo volání všechny metody, které nejsou podporovány , budete muset použít omezení parametru typu. Například omezení základní třídy říká kompilátoru, že jako argumenty typu budou použity pouze objekty tohoto typu nebo odvozené z tohoto typu. Jakmile kompilátor má tuto záruku, může povolit metody tohoto typu, které mají být volány v obecné třídě. Následující příklad kódu ukazuje funkce, které můžete `GenericList<T>` přidat do třídy (v [úvodu k obecným typům](../../../standard/generics/index.md)) použitím omezení základní třídy.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Omezení umožňuje obecné třídy `Employee.Name` používat vlastnost. Omezení určuje, že všechny `T` položky typu jsou `Employee` zaručeně objekt nebo `Employee`objekt, který dědí z .

Více omezení lze použít na stejný parametr typu a omezení sami mohou být obecné typy, takto:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Při použití `where T : class` omezení, `==` vyhnout `!=` a operátory na parametr typu, protože tyto operátory budou testovat pouze referenční identitu, nikoli pro rovnost hodnot. K tomuto chování dochází i v případě, že tyto operátory jsou přetíženy v typu, který se používá jako argument. Následující kód ilustruje tento bod; výstup je false i <xref:System.String> v případě, že třída přetížení `==` operátor.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Kompilátor pouze `T` ví, že je typ odkazu v době kompilace a musí používat výchozí operátory, které jsou platné pro všechny typy odkazů. Pokud je nutné otestovat rovnost hodnot, doporučeným `where T : IEquatable<T>` způsobem `where T : IComparable<T>` je také použít nebo omezení a implementovat rozhraní v libovolné třídě, která bude použita k vytvoření obecné třídy.

## <a name="constraining-multiple-parameters"></a>Omezení více parametrů

Omezení můžete použít na více parametrů a více omezení na jeden parametr, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Parametry neohraničeného typu

 Parametry typu, které nemají žádná omezení, `SampleClass<T>{}`například T ve veřejné třídě , se nazývají parametry neohraničeného typu. Parametry neohraničeného typu mají následující pravidla:

- A `!=` `==` operátory nelze použít, protože neexistuje žádná záruka, že konkrétní argument typu bude podporovat tyto operátory.
- Mohou být převedeny do `System.Object` a z nebo explicitně převedeny na libovolný typ rozhraní.
- Můžete je porovnat s [hodnotou null](../../language-reference/keywords/null.md). Pokud je porovnán s neohraničeným parametrem `null`, porovnání vždy vrátí false, pokud je argumentem typu typ typ.

## <a name="type-parameters-as-constraints"></a>Parametry typu jako omezení

Použití parametru obecného typu jako omezení je užitečné, pokud členská funkce s vlastním parametrem typu musí tento parametr omezit na parametr typu obsahujícího typu, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

V předchozím příkladu `T` je omezení typu v `Add` kontextu metody a neomezený parametr typu v `List` kontextu třídy.

Parametry typu lze také použít jako omezení v definicích obecných tříd. Parametr typu musí být deklarován v rámci úhlových závorek spolu s dalšími parametry typu:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Užitečnost parametrů typu jako omezení s obecnými třídami je omezena, protože kompilátor nemůže `System.Object`předpokládat nic o parametru typu s tím rozdílem, že je odvozen z . Parametry typu použijte jako omezení obecných tříd ve scénářích, ve kterých chcete vynutit vztah dědičnosti mezi dvěma parametry typu.

## <a name="notnull-constraint"></a>Omezení notnull

Počínaje C# 8.0, můžete `notnull` použít omezení určit, že argument typu musí být typ nenulové hodnoty typu nebo non-nullable typ odkazu. Omezení `notnull` lze použít pouze `nullable enable` v kontextu. Kompilátor vygeneruje upozornění, `notnull` pokud přidáte omezení v kontextu, který je nenutelný, s hodnotou null.

Na rozdíl od jiných omezení, když `notnull` argument typu porušuje omezení, kompilátor generuje upozornění, když je tento kód kompilován v `nullable enable` kontextu. Pokud je kód zkompilován v kontextu, který nelze upustit od nuly, kompilátor negeneruje žádná upozornění nebo chyby.

## <a name="unmanaged-constraint"></a>Nespravované omezení

Počínaje C# 7.3, můžete `unmanaged` použít omezení určit, že parametr typu musí být [nenulelný nespravovaný typ](../../language-reference/builtin-types/unmanaged-types.md). Omezení `unmanaged` umožňuje psát opakovaně použitelné rutiny pro práci s typy, které lze manipulovat jako bloky paměti, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Předchozí metoda musí být zkompilován v `unsafe` `sizeof` kontextu, protože používá operátor na typ není známo, že je vestavěný typ. Bez `unmanaged` omezení `sizeof` operátor není k dispozici.

Omezení `unmanaged` znamená `struct` omezení a nelze s ním kombinovat. Vzhledem `struct` k `new()` tomu, `unmanaged` že omezení znamená omezení, `new()` omezení nelze kombinovat s omezením také.

## <a name="delegate-constraints"></a>Omezení delegáta

Také počínaje C# 7.3, <xref:System.Delegate?displayProperty=nameWithType> můžete <xref:System.MulticastDelegate?displayProperty=nameWithType> použít nebo jako omezení základní třídy. CLR vždy povoleno toto omezení, ale jazyk Jazyka C# zakázáno. Omezení `System.Delegate` umožňuje psát kód, který pracuje s delegáty způsobem bezpečné ho typu. Následující kód definuje metodu rozšíření, která kombinuje dva delegáty za předpokladu, že jsou stejného typu:

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Výše uvedenou metodu můžete použít ke sloučení delegátů, které jsou stejného typu:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Pokud odkomentujete poslední řádek, nebude kompilovat. Oba `first` `test` a jsou typy delegátů, ale jsou různé typy delegátů.

## <a name="enum-constraints"></a>Omezení výčtu

Počínaje C# 7.3, můžete také <xref:System.Enum?displayProperty=nameWithType> zadat typ jako omezení základní třídy. CLR vždy povoleno toto omezení, ale jazyk Jazyka C# zakázáno. Obecné typy `System.Enum` používající poskytují programování bezpečné pro typ `System.Enum`pro ukládání výsledků do mezipaměti pomocí statických metod v . Následující ukázka vyhledá všechny platné hodnoty pro typ výčtu a potom vytvoří slovník, který tyto hodnoty mapuje na jeho řetězcovou reprezentaci.

[!code-csharp[using the enum constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Metody používané k použití reflexe, která má vliv na výkon. Tuto metodu můžete volat k vytvoření kolekce, která je uložena do mezipaměti a znovu použita, nikoli opakování volání, která vyžadují reflexi.

Můžete jej použít, jak je znázorněno v následující ukázce k vytvoření výčtu a vytvoření slovníku jeho hodnot a názvů:

[!code-csharp[enum definition](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the enum constrained method](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- [Programovací příručka jazyka C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Obecné třídy](./generic-classes.md)
- [nové omezení](../../language-reference/keywords/new-constraint.md)
