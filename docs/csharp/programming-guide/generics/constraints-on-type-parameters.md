---
title: Omezení parametrů typu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: f09f93f27aa4f50cfb7e09b9d6d4f98f22e1ac9a
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433558"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Omezení parametrů typu (C# Průvodce programováním)

Omezení informují kompilátor o možnostech, které musí mít argument typu. Bez omezení může být argumentem typu libovolný typ. Kompilátor může předpokládat pouze členy <xref:System.Object?displayProperty=nameWithType>, což je maximální základní třída pro libovolný typ rozhraní .NET. Další informace najdete v tématu [Proč použít omezení](#why-use-constraints). Pokud se klientský kód pokusí vytvořit instanci vaší třídy pomocí typu, který není povolen omezením, výsledkem je chyba při kompilaci. Omezení jsou určena pomocí `where` klíčového slova kontextové. V následující tabulce jsou uvedeny sedm typů omezení:

|Jedinečn|Popis|
|----------------|-----------------|
|`where T : struct`|Argument typu musí být typ hodnoty. Jakýkoli typ hodnoty s <xref:System.Nullable%601> výjimkou lze zadat. Další informace o typech Nullable naleznete v tématu [typy s možnou hodnotou null](../nullable-types/index.md).|
|`where T : class`|Argument typu musí být typ odkazu. Toto omezení platí také pro libovolnou třídu, rozhraní, delegáta nebo typ pole.|
|`where T : unmanaged`|Argument typu musí být nespravovaný [typ](../../language-reference/builtin-types/unmanaged-types.md).|
|`where T : new()`|Argument typu musí mít veřejný konstruktor bez parametrů. Při použití společně s jinými omezeními je `new()` třeba omezení zadat jako poslední.|
|`where T :`název základní třídy >  *\<*|Argument typu musí být nebo odvozen ze zadané základní třídy.|
|`where T :` *názevrozhraní\<>*|Argument typu musí být nebo implementovat zadané rozhraní. Je možné zadat více omezení rozhraní. Omezení rozhraní může být také obecné.|
|`where T : U`|Argument typu zadaný pro T musí být nebo odvozen od argumentu zadaného pro U.|

Některá omezení se vzájemně vylučují. Všechny typy hodnot musí mít přístupný konstruktor bez parametrů. Omezení implikuje `new()`omezenía omezení nelze kombinovat s `struct` omezením. `new()` `struct` `unmanaged` Omezení implikuje omezení. `struct` Omezení nelze kombinovat s `struct` omezeními nebo `new()`. `unmanaged`

## <a name="why-use-constraints"></a>Proč použít omezení

Omezením parametru typu zvýšíte počet povolených operací a volání metod do těch, které jsou podporovány typem omezení a všemi typy v její hierarchii dědičnosti. Pokud navrhujete obecné třídy nebo metody, pokud budete provádět jakoukoli operaci u obecných členů nad rámec jednoduchého přiřazení nebo volání jakékoli metody <xref:System.Object?displayProperty=nameWithType>, kterou nepodporuje, budete muset použít omezení na parametr typu. Například omezení základní třídy říká kompilátoru, že jako argumenty typu budou použity pouze objekty tohoto typu nebo odvozené z tohoto typu. Jakmile má kompilátor tuto záruku, může dovolit volání metod tohoto typu v obecné třídě. Následující příklad kódu ukazuje funkce, které lze přidat do `GenericList<T>` třídy (v části [Úvod do obecných](introduction-to-generics.md)) pomocí omezení základní třídy.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Omezení umožňuje, aby obecná třída používala `Employee.Name` vlastnost. Omezení určuje, že všechny položky typu `T` jsou zaručeny `Employee` buď objekt, nebo objekt, který dědí z `Employee`.

U stejného parametru typu lze použít více omezení a samotné omezení mohou být obecné typy, a to takto:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Při použití `where T : class` omezení se `==` Vyhněte operátorům `!=` a v parametru typu, protože tyto operátory budou testovat pouze referenční identitu, nikoli pro rovnost hodnot. K tomuto chování dochází, i když jsou tyto operátory přetíženy v typu, který se používá jako argument. Následující kód ilustruje tento bod; výstup je false, i když <xref:System.String> třída přetěžuje `==` operátor.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Kompilátor ví pouze, že T je odkazový typ v době kompilace a musí používat výchozí operátory, které jsou platné pro všechny typy odkazů. Pokud je nutné testovat rovnost hodnot, doporučuje se také použít `where T : IEquatable<T>` omezení nebo `where T : IComparable<T>` a implementovat rozhraní v jakékoli třídě, která bude použita k vytvoření obecné třídy.

## <a name="constraining-multiple-parameters"></a>Omezení více parametrů

Můžete použít omezení na více parametrů a více omezení na jeden parametr, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Neohraničené parametry typu

 Parametry typu, které nemají žádná omezení, jako je například T ve `SampleClass<T>{}`veřejné třídě, se nazývají neohraničené parametry typu. Neohraničené parametry typu mají následující pravidla:

- Operátory `!=` a`==` nelze použít, protože není nijak zaručeno, že konkrétní argument typu bude podporovat tyto operátory.
- Lze je převést na nebo z `System.Object` nebo explicitně převést na libovolný typ rozhraní.
- Můžete je porovnat s [hodnotou null](../../language-reference/keywords/null.md). Pokud je neohraničený parametr porovnán `null`, porovnávání vždy vrátí hodnotu false, pokud je argumentem typu hodnotový typ.

## <a name="type-parameters-as-constraints"></a>Parametry typu jako omezení

Použití parametru obecného typu jako omezení je užitečné, pokud členská funkce s vlastním parametrem typu musí omezit tento parametr na parametr typu nadřazeného typu, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

V předchozím příkladu `T` je omezení typu v kontextu `Add` metody a parametr nevázaného typu `List` v kontextu třídy.

Parametry typu lze také použít jako omezení v definicích obecných tříd. Parametr typu musí být deklarovaný v lomených závorkách spolu s jinými parametry typu:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Užitečnost parametrů typu jako omezení s obecnými třídami je omezená, protože kompilátor může předpokládat nic o parametru typu s výjimkou toho, že je `System.Object`odvozen z. Použijte parametry typu jako omezení pro obecné třídy ve scénářích, ve kterých chcete vynutit vztah dědičnosti mezi dvěma parametry typu.

## <a name="unmanaged-constraint"></a>Nespravované omezení

Počínaje C# 7,3 můžete `unmanaged` omezení použít k určení, že parametr typu musí být nespravovaného [typu](../../language-reference/builtin-types/unmanaged-types.md). `unmanaged` Omezení umožňuje napsat opakovaně použitelné rutiny pro práci s typy, které mohou být manipulovány jako bloky paměti, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Předchozí metoda musí být zkompilována v `unsafe` kontextu, protože `sizeof` používá operátor u typu, který není známý jako vestavěný typ. `unmanaged` Bez omezení`sizeof` není operátor k dispozici.

## <a name="delegate-constraints"></a>Omezení delegování

Počínaje C# 7,3 můžete také použít <xref:System.Delegate?displayProperty=nameWithType> nebo <xref:System.MulticastDelegate?displayProperty=nameWithType> jako omezení základní třídy. CLR vždy povoluje toto omezení, ale C# jazyk ho nepovolil. `System.Delegate` Omezení umožňuje napsat kód, který pracuje s delegáty způsobem bezpečným pro typ. Následující kód definuje metodu rozšíření, která kombinuje dva delegáty, pokud jsou stejného typu:

[!code-csharp[using the delegate constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

K kombinování delegátů, kteří mají stejný typ, můžete použít výše uvedenou metodu:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Pokud Odkomentujete poslední řádek, nebude zkompilován. `first` A`test` jsou typy delegátů, ale jsou různými typy delegátů.

## <a name="enum-constraints"></a>Omezení výčtu

Počínaje C# 7,3 můžete také zadat <xref:System.Enum?displayProperty=nameWithType> typ jako omezení základní třídy. CLR vždy povoluje toto omezení, ale C# jazyk ho nepovolil. Obecné typy pomocí `System.Enum` poskytují programování zajišťující bezpečnost typů pro ukládání výsledků z použití statických metod v `System.Enum`. Následující ukázka vyhledá všechny platné hodnoty pro typ výčtu a potom vytvoří slovník, který tyto hodnoty mapuje na jeho řetězcovou reprezentaci.

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Používané metody využívají reflexi, což má dopad na výkon. Tuto metodu lze zavolat pro sestavení kolekce, která je uložena v mezipaměti a znovu použita, nikoli volání, která vyžadují reflexi.

Můžete ji použít, jak je znázorněno v následujícím příkladu, pro vytvoření výčtu a sestavení slovníku jeho hodnot a názvů:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Úvod do obecných typů](../../../csharp/programming-guide/generics/index.md)
- [Obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md)
- [new – omezení](../../../csharp/language-reference/keywords/new-constraint.md)
