---
title: Omezení parametrů typu – C# Průvodce programováním
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: 3ce68ecc1f0740fdb43ccf22b636dcd4bc05ea0a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712231"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Omezení parametrů typu (C# Průvodce programováním)

Omezení informují kompilátor o možnostech, které musí mít argument typu. Bez omezení může být argumentem typu libovolný typ. Kompilátor může předpokládat pouze členy <xref:System.Object?displayProperty=nameWithType>, což je maximální základní třída pro libovolný typ rozhraní .NET. Další informace najdete v tématu [Proč použít omezení](#why-use-constraints). Pokud se klientský kód pokusí vytvořit instanci vaší třídy pomocí typu, který není povolen omezením, výsledkem je chyba při kompilaci. Omezení jsou určena pomocí klíčového slova `where` kontextové. V následující tabulce jsou uvedeny sedm typů omezení:

|Jedinečn|Popis|
|----------------|-----------------|
|`where T : struct`|Argument typu musí být typ hodnoty, která není null. Informace o typech hodnot s možnou hodnotou null naleznete v tématu [hodnoty s možnou hodnotou null](../../language-reference/builtin-types/nullable-value-types.md). Vzhledem k tomu, že všechny typy hodnot mají přístupný konstruktor bez parametrů, omezení `struct` implikuje omezení `new()` a nelze je kombinovat s omezením `new()`. Omezení `struct` také nelze kombinovat s omezením `unmanaged`.|
|`where T : class`|Argument typu musí být typ odkazu. Toto omezení platí také pro libovolnou třídu, rozhraní, delegáta nebo typ pole.|
|`where T : notnull`|Argument typu musí být typ, který nemůže mít hodnotu null. Argumentem může být typ odkazu, který neumožňuje hodnotu C# null, v 8,0 nebo novějším, nebo typ hodnoty, která není null. Toto omezení platí také pro libovolnou třídu, rozhraní, delegáta nebo typ pole.|
|`where T : unmanaged`|Argument typu musí být [nespravovaný typ](../../language-reference/builtin-types/unmanaged-types.md), který nemůže mít hodnotu null. Omezení `unmanaged` implikuje omezení `struct` a nelze je kombinovat s omezeními `struct` ani `new()`.|
|`where T : new()`|Argument typu musí mít veřejný konstruktor bez parametrů. Při použití společně s jinými omezeními je nutné zadat omezení `new()` jako poslední. Omezení `new()` nelze kombinovat s omezeními `struct` a `unmanaged`.|
|*název základní třídy `where T :`\<*|Argument typu musí být nebo odvozen ze zadané základní třídy.|
|*název rozhraní `where T :`\<*|Argument typu musí být nebo implementovat zadané rozhraní. Je možné zadat více omezení rozhraní. Omezení rozhraní může být také obecné.|
|`where T : U`|Argument typu zadaný pro T musí být nebo odvozen od argumentu zadaného pro U.|

## <a name="why-use-constraints"></a>Proč použít omezení

Omezením parametru typu zvýšíte počet povolených operací a volání metod do těch, které jsou podporovány typem omezení a všemi typy v její hierarchii dědičnosti. Pokud navrhujete obecné třídy nebo metody, pokud budete provádět jakoukoli operaci u obecných členů nad rámec jednoduchého přiřazení nebo volání jakékoli metody, které <xref:System.Object?displayProperty=nameWithType>nepodporuje, budete muset použít omezení pro parametr typu. Například omezení základní třídy říká kompilátoru, že jako argumenty typu budou použity pouze objekty tohoto typu nebo odvozené z tohoto typu. Jakmile má kompilátor tuto záruku, může dovolit volání metod tohoto typu v obecné třídě. Následující příklad kódu ukazuje funkce, které lze přidat do `GenericList<T>` třídy (v [úvodu k obecným](../../../standard/generics/index.md)) pomocí omezení základní třídy.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Omezení umožňuje, aby obecná třída používala vlastnost `Employee.Name`. Omezení určuje, že všechny položky typu `T` jsou zaručeny buď objekt `Employee` nebo objekt, který dědí z `Employee`.

U stejného parametru typu lze použít více omezení a samotné omezení mohou být obecné typy, a to takto:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Při použití omezení `where T : class` Vyhněte se operátorům `==` a `!=` na parametru typu, protože tyto operátory budou testovány pouze pro referenční identitu, nikoli pro rovnost hodnot. K tomuto chování dochází, i když jsou tyto operátory přetíženy v typu, který se používá jako argument. Následující kód ilustruje tento bod; výstup je false, i když <xref:System.String> třída přetěžuje operátor `==`.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Kompilátor ví pouze, že `T` je odkazový typ v době kompilace a musí používat výchozí operátory, které jsou platné pro všechny typy odkazů. Pokud je nutné testovat rovnost hodnot, doporučuje se použít také omezení `where T : IEquatable<T>` nebo `where T : IComparable<T>` a implementovat rozhraní v jakékoli třídě, která bude použita k vytvoření obecné třídy.

## <a name="constraining-multiple-parameters"></a>Omezení více parametrů

Můžete použít omezení na více parametrů a více omezení na jeden parametr, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Neohraničené parametry typu

 Parametry typu bez omezení, jako například T ve veřejné třídě `SampleClass<T>{}`, se nazývají neohraničené parametry typu. Neohraničené parametry typu mají následující pravidla:

- Operátory `!=` a `==` nelze použít, protože není nijak zaručeno, že konkrétní argument typu bude podporovat tyto operátory.
- Lze je převést na nebo z `System.Object` nebo explicitně převést na libovolný typ rozhraní.
- Můžete je porovnat s [hodnotou null](../../language-reference/keywords/null.md). Pokud je nevázaný parametr porovnán s `null`, porovnávání vždy vrátí hodnotu false, pokud je argumentem typu hodnotový typ.

## <a name="type-parameters-as-constraints"></a>Parametry typu jako omezení

Použití parametru obecného typu jako omezení je užitečné, pokud členská funkce s vlastním parametrem typu musí omezit tento parametr na parametr typu nadřazeného typu, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

V předchozím příkladu `T` je omezení typu v kontextu metody `Add` a neohraničený parametr typu v kontextu třídy `List`.

Parametry typu lze také použít jako omezení v definicích obecných tříd. Parametr typu musí být deklarovaný v lomených závorkách spolu s jinými parametry typu:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Užitečnost parametrů typu jako omezení s obecnými třídami je omezená, protože kompilátor nemůže předpokládat nic o parametru typu s tím rozdílem, že je odvozen od `System.Object`. Použijte parametry typu jako omezení pro obecné třídy ve scénářích, ve kterých chcete vynutit vztah dědičnosti mezi dvěma parametry typu.

## <a name="notnull-constraint"></a>Omezení NotNull

Počínaje C# 8,0 můžete použít omezení `notnull` k určení, že argument typu musí být typ hodnoty, která není null, nebo odkaz na typ, který nepovoluje hodnotu null. Omezení `notnull` lze použít pouze v kontextu `nullable enable`. Kompilátor vygeneruje upozornění, pokud přidáte omezení `notnull` v oblivious kontextu s možnou hodnotou null. 

Na rozdíl od jiných omezení, pokud argument typu narušuje omezení `notnull`, kompilátor vygeneruje upozornění, když je tento kód zkompilován v kontextu `nullable enable`. Pokud je kód zkompilován v oblivious kontextu s možnou hodnotou null, kompilátor negeneruje žádná upozornění ani chyby.

## <a name="unmanaged-constraint"></a>Nespravované omezení

Počínaje C# 7,3 můžete pomocí omezení `unmanaged` určit, že parametr typu musí být [nespravovaný typ](../../language-reference/builtin-types/unmanaged-types.md), který není null. Omezení `unmanaged` umožňuje psát opakovaně použitelné rutiny pro práci s typy, které mohou být manipulovány jako bloky paměti, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Předchozí metoda musí být zkompilována v kontextu `unsafe`, protože používá operátor `sizeof` u typu, který není známý jako vestavěný typ. Bez omezení `unmanaged` není operátor `sizeof` k dispozici.

Omezení `unmanaged` implikuje omezení `struct` a nedá se s ním kombinovat. Vzhledem k tomu, že omezení `struct` implikuje omezení `new()`, nelze omezení `unmanaged` kombinovat i s omezením `new()`.

## <a name="delegate-constraints"></a>Omezení delegování

Počínaje C# 7,3 můžete také použít <xref:System.Delegate?displayProperty=nameWithType> nebo <xref:System.MulticastDelegate?displayProperty=nameWithType> jako omezení základní třídy. CLR vždy povoluje toto omezení, ale C# jazyk ho nepovolil. Omezení `System.Delegate` umožňuje napsat kód, který spolupracuje s delegáty způsobem, který je typově bezpečný. Následující kód definuje metodu rozšíření, která kombinuje dva delegáty, pokud jsou stejného typu:

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

K kombinování delegátů, kteří mají stejný typ, můžete použít výše uvedenou metodu:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Pokud Odkomentujete poslední řádek, nebude zkompilován. `first` i `test` jsou typy delegátů, ale jedná se o různé typy delegátů.

## <a name="enum-constraints"></a>Omezení výčtu

Počínaje C# 7,3 můžete také zadat typ <xref:System.Enum?displayProperty=nameWithType> jako omezení základní třídy. CLR vždy povoluje toto omezení, ale C# jazyk ho nepovolil. Obecné typy pomocí `System.Enum` poskytují programové programování pro ukládání výsledků do mezipaměti pomocí statických metod v `System.Enum`. Následující ukázka vyhledá všechny platné hodnoty pro typ výčtu a potom vytvoří slovník, který tyto hodnoty mapuje na jeho řetězcovou reprezentaci.

[!code-csharp[using the enum constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Metody použité k použití reflexe, který má dopad na výkon. Tuto metodu lze zavolat pro sestavení kolekce, která je uložena v mezipaměti a znovu použita, nikoli volání, která vyžadují reflexi.

Můžete ji použít, jak je znázorněno v následujícím příkladu, pro vytvoření výčtu a sestavení slovníku jeho hodnot a názvů:

[!code-csharp[enum definition](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the enum constrained method](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Obecné třídy](./generic-classes.md)
- [new – omezení](../../language-reference/keywords/new-constraint.md)
