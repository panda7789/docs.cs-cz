---
title: Omezení parametrů typu – Průvodce programováním v C#
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: 376befe4c969ac653e234479c8946d7fd4242999
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442212"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Omezení parametrů typu (Průvodce programováním v C#)

Omezení informují kompilátor o možnostech, které musí mít argument typu. Bez omezení může být argumentem typu libovolný typ. Kompilátor může předpokládat pouze členy <xref:System.Object?displayProperty=nameWithType> , což je maximální základní třída pro libovolný typ rozhraní .NET. Další informace najdete v tématu [Proč použít omezení](#why-use-constraints). Pokud klientský kód používá typ, který nesplňuje omezení, kompilátor vyvolá chybu. Omezení jsou určena pomocí `where` klíčového slova kontextové. V následující tabulce jsou uvedeny sedm typů omezení:

|Jedinečn|Popis|
|----------------|-----------------|
|`where T : struct`|Argument typu musí být typ hodnoty, která není null. Informace o typech hodnot s možnou hodnotou null naleznete v tématu [hodnoty s možnou hodnotou null](../../language-reference/builtin-types/nullable-value-types.md). Vzhledem k tomu, že všechny typy hodnot mají přístupný konstruktor bez parametrů, `struct` omezení implikuje `new()` omezení a nelze je kombinovat s `new()` omezením. Omezení nelze kombinovat `struct` s `unmanaged` omezením.|
|`where T : class`|Argument typu musí být typ odkazu. Toto omezení platí také pro libovolnou třídu, rozhraní, delegáta nebo typ pole. V kontextu s možnou hodnotou null v jazyce C# 8,0 nebo vyšší `T` musí být odkazový typ, který není null. |
|`where T : class?`|Argument typu musí být typ odkazu, který může mít hodnotu null nebo nemůže mít hodnotu null. Toto omezení platí také pro libovolnou třídu, rozhraní, delegáta nebo typ pole.|
|`where T : notnull`|Argument typu musí být typ, který nemůže mít hodnotu null. Argument může být odkazový typ, který neumožňuje hodnotu null v C# 8,0 nebo novější, nebo typ hodnoty, která není null. |
|`where T : unmanaged`|Argument typu musí být [nespravovaný typ](../../language-reference/builtin-types/unmanaged-types.md), který nemůže mít hodnotu null. `unmanaged`Omezení implikuje `struct` omezení a nelze ho kombinovat s `struct` `new()` omezeními or.|
|`where T : new()`|Argument typu musí mít veřejný konstruktor bez parametrů. Při použití společně s jinými omezeními je `new()` třeba omezení zadat jako poslední. `new()`Omezení nelze kombinovat s `struct` `unmanaged` omezeními a.|
|`where T :`* \< název základní třídy>*|Argument typu musí být nebo odvozen ze zadané základní třídy. V kontextu s možnou hodnotou null v C# 8,0 a novějším `T` musí být odkazový typ, který je odvozen od zadané základní třídy, nepovoluje hodnotu null. |
|`where T :`* \< název základní třídy>?*|Argument typu musí být nebo odvozen ze zadané základní třídy. V kontextu s možnou hodnotou null v C# 8,0 a novější `T` může být buď typ s možnou hodnotou null, nebo typ, který nemůže mít hodnotu null odvozený ze zadané základní třídy. |
|`where T :`* \< název rozhraní>*|Argument typu musí být nebo implementovat zadané rozhraní. Je možné zadat více omezení rozhraní. Omezení rozhraní může být také obecné. V kontextu s možnou hodnotou null v jazyce C# 8,0 a novějším `T` musí být typ bez hodnoty null, který implementuje zadané rozhraní.|
|`where T :`* \<> název rozhraní?*|Argument typu musí být nebo implementovat zadané rozhraní. Je možné zadat více omezení rozhraní. Omezení rozhraní může být také obecné. V kontextu s možnou hodnotou null v jazyce C# 8,0 `T` může být odkazový typ s možnou hodnotou null, odkazem, který nepovoluje hodnotu null nebo typ hodnoty. `T`nesmí se jednat o typ hodnoty s možnou hodnotou null.|
|`where T : U`|Argument typu zadaný pro `T` musí být nebo odvozen od argumentu zadaného pro `U` . V kontextu s možnou hodnotou null, pokud `U` je odkazový typ, který nepovoluje hodnotu null, `T` musí být odkazový typ, který není null. Pokud `U` je odkazový typ s možnou hodnotou null, `T` může mít buď hodnotu null, nebo nemůže být null. |

## <a name="why-use-constraints"></a>Proč použít omezení

Omezení určují schopnosti a očekávání parametru typu. Deklarace těchto omezení znamená, že můžete použít volání operací a metody omezení typu. Pokud vaše obecná třída nebo metoda používá jakoukoli operaci u obecných členů nad rámec jednoduchého přiřazení nebo volání jakékoli metody, kterou nepodporuje <xref:System.Object?displayProperty=nameWithType> , budete muset použít omezení na parametr typu. Například omezení základní třídy říká kompilátoru, že jako argumenty typu budou použity pouze objekty tohoto typu nebo odvozené z tohoto typu. Jakmile má kompilátor tuto záruku, může dovolit volání metod tohoto typu v obecné třídě. Následující příklad kódu ukazuje funkce, které lze přidat do `GenericList<T>` třídy (v části [Úvod do obecných](../../../standard/generics/index.md)) pomocí omezení základní třídy.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Omezení umožňuje, aby obecná třída používala `Employee.Name` vlastnost. Omezení určuje, že všechny položky typu `T` jsou zaručeny buď `Employee` objekt, nebo objekt, který dědí z `Employee` .

U stejného parametru typu lze použít více omezení a samotné omezení mohou být obecné typy, a to takto:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Při použití `where T : class` omezení se vyhněte `==` `!=` operátorům a v parametru typu, protože tyto operátory budou testovat pouze referenční identitu, nikoli pro rovnost hodnot. K tomuto chování dochází, i když jsou tyto operátory přetíženy v typu, který se používá jako argument. Následující kód ilustruje tento bod; výstup je false, i když <xref:System.String> Třída přetěžuje `==` operátor.

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Kompilátor zná pouze `T` odkazový typ v době kompilace a musí používat výchozí operátory, které jsou platné pro všechny typy odkazů. Pokud je nutné testovat rovnost hodnot, doporučuje se také použít `where T : IEquatable<T>` `where T : IComparable<T>` omezení nebo a implementovat rozhraní v jakékoli třídě, která bude použita k vytvoření obecné třídy.

## <a name="constraining-multiple-parameters"></a>Omezení více parametrů

Můžete použít omezení na více parametrů a více omezení na jeden parametr, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Neohraničené parametry typu

 Parametry typu, které nemají žádná omezení, jako je například T ve veřejné třídě `SampleClass<T>{}` , se nazývají neohraničené parametry typu. Neohraničené parametry typu mají následující pravidla:

- `!=`Operátory a `==` nelze použít, protože není nijak zaručeno, že konkrétní argument typu bude podporovat tyto operátory.
- Lze je převést na `System.Object` nebo z nebo explicitně převést na libovolný typ rozhraní.
- Můžete je porovnat s [hodnotou null](../../language-reference/keywords/null.md). Pokud je neohraničený parametr porovnán `null` , porovnávání vždy vrátí hodnotu false, pokud je argumentem typu hodnotový typ.

## <a name="type-parameters-as-constraints"></a>Parametry typu jako omezení

Použití parametru obecného typu jako omezení je užitečné, pokud členská funkce s vlastním parametrem typu musí omezit tento parametr na parametr typu nadřazeného typu, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

V předchozím příkladu `T` je omezení typu v kontextu `Add` metody a parametr nevázaného typu v kontextu `List` třídy.

Parametry typu lze také použít jako omezení v definicích obecných tříd. Parametr typu musí být deklarovaný v lomených závorkách spolu s jinými parametry typu:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Užitečnost parametrů typu jako omezení s obecnými třídami je omezená, protože kompilátor může předpokládat nic o parametru typu s výjimkou toho, že je odvozen z `System.Object` . Použijte parametry typu jako omezení pro obecné třídy ve scénářích, ve kterých chcete vynutit vztah dědičnosti mezi dvěma parametry typu.

## <a name="notnull-constraint"></a>Omezení NotNull

Počínaje jazykem C# 8,0 v kontextu s možnou hodnotou null můžete použít `notnull` omezení, chcete-li určit, že argument typu musí být typ hodnoty, která není null, nebo odkaz na typ, který nepovoluje hodnotu null. `notnull`Omezení lze použít pouze v `nullable enable` kontextu. Kompilátor vygeneruje upozornění, pokud přidáte `notnull` omezení do oblivious kontextu s možnou hodnotou null.

Na rozdíl od jiných omezení, pokud argument typu narušuje `notnull` omezení, kompilátor vygeneruje upozornění, když je tento kód zkompilován v `nullable enable` kontextu. Pokud je kód zkompilován v oblivious kontextu s možnou hodnotou null, kompilátor negeneruje žádná upozornění ani chyby.

Počínaje jazykem C# 8,0 v kontextu s možnou hodnotou null `class` Určuje omezení, že argument typu musí být odkazový typ, který není null. V kontextu s možnou hodnotou null, pokud je parametr typu odkazem s možnou hodnotou null, kompilátor vygeneruje upozornění.

## <a name="unmanaged-constraint"></a>Nespravované omezení

Počínaje jazykem C# 7,3 můžete použít `unmanaged` omezení, chcete-li určit, že parametr typu musí být [nespravovaný typ](../../language-reference/builtin-types/unmanaged-types.md), který nemůže mít hodnotu null. `unmanaged`Omezení umožňuje napsat opakovaně použitelné rutiny pro práci s typy, které mohou být manipulovány jako bloky paměti, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Předchozí metoda musí být zkompilována v `unsafe` kontextu, protože používá `sizeof` operátor u typu, který není známý jako vestavěný typ. Bez `unmanaged` omezení `sizeof` není operátor k dispozici.

`unmanaged`Omezení implikuje `struct` omezení a nelze je kombinovat s ním. Vzhledem k tomu `struct` , že omezení implikuje omezení `new()` , `unmanaged` nelze omezení kombinovat `new()` i s omezením.

## <a name="delegate-constraints"></a>Omezení delegování

Počínaje jazykem C# 7,3 můžete také použít <xref:System.Delegate?displayProperty=nameWithType> <xref:System.MulticastDelegate?displayProperty=nameWithType> omezení základní třídy nebo. CLR vždy povoluje toto omezení, ale jazyk C# ho nepovolil. `System.Delegate`Omezení umožňuje napsat kód, který pracuje s delegáty způsobem bezpečným pro typ. Následující kód definuje metodu rozšíření, která kombinuje dva delegáty, pokud jsou stejného typu:

[!code-csharp[using the delegate constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

K kombinování delegátů, kteří mají stejný typ, můžete použít výše uvedenou metodu:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Pokud Odkomentujete poslední řádek, nebude zkompilován. `first`A `test` jsou typy delegátů, ale jsou různými typy delegátů.

## <a name="enum-constraints"></a>Omezení výčtu

Počínaje jazykem C# 7,3 můžete také zadat <xref:System.Enum?displayProperty=nameWithType> typ jako omezení základní třídy. CLR vždy povoluje toto omezení, ale jazyk C# ho nepovolil. Obecné typy pomocí `System.Enum` poskytují programování zajišťující bezpečnost typů pro ukládání výsledků z použití statických metod v `System.Enum` . Následující ukázka vyhledá všechny platné hodnoty pro typ výčtu a potom vytvoří slovník, který tyto hodnoty mapuje na jeho řetězcovou reprezentaci.

[!code-csharp[using the enum constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

`Enum.GetValues`a `Enum.GetName` používejte reflexi, který má dopad na výkon. Můžete zavolat `EnumNamedValues` k sestavení kolekce, která je uložena v mezipaměti a znovu použita, nikoli volání, která vyžadují reflexi.

Můžete ji použít, jak je znázorněno v následujícím příkladu, pro vytvoření výčtu a sestavení slovníku jeho hodnot a názvů:

[!code-csharp[enum definition](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the enum constrained method](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- [Průvodce programováním v C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Obecné třídy](./generic-classes.md)
- [nové omezení](../../language-reference/keywords/new-constraint.md)
