---
title: Omezení parametrů typů (Průvodce programováním v C#)
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: df5a509296f3fb9e8e77a273a0636c74a6f86da3
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711282"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a>Omezení parametrů typů (C# Programming Guide)

Omezení kompilátoru informuje o možnosti, které argument typu musí mít. Bez jakýchkoliv omezení typu argument může být libovolného typu. Kompilátor může převzít jenom jako objekty její členové <xref:System.Object?displayPropety=nameWithType>, což je základní třídy ultimate pro jakýkoli typ .NET. Další informace najdete v tématu [Proč používat omezení](#why-use-constraints). Pokud klientský kód se pokusí vytvořit instanci své třídy pomocí typu, který není povolen omezením, výsledkem je chyba kompilace. Omezení je určené vlastností `where` kontextové klíčové slovo. V následující tabulce jsou uvedeny sedm typy omezujících podmínek:

|Omezení|Popis|
|----------------|-----------------|
|`where T : struct`|Argument typu musí být typem hodnoty. Některá hodnota typu s výjimkou <xref:System.Nullable%601> lze zadat. Další informace o typech s povolenou hodnotou Null, naleznete v tématu [typy připouštějící hodnotu Null](../nullable-types/index.md).|
|`where T : class`|Argument typu musí být typ odkazu. Toto omezení platí také pro třídy, rozhraní, delegáta nebo typ pole.|
|`where T : unmanaged`|Argument typu nemůže být odkazovým typem a nesmí obsahovat žádné členy typu odkazu na libovolné úrovni vnoření.|
|`where T : new()`|Argument typu musí mít veřejný konstruktor bez parametrů. Při použití s dalšími omezeními `new()` omezení musí být uvedený jako poslední.|
|`where T :` *\<Název základní třídy >*|Argument typu musí být nebo odvozen od zadané základní třídy.|
|`where T :` *\<Název rozhraní >*|Argument typu musí být nebo implementovat rozhraní zadané. Je možné zadat více omezením rozhraní. Omezující rozhraní může být obecný.|
|`where T : U`|Argument typu zadaný pro T musí být nebo odvozené z argument zadaný pro U.|

Některá omezení se vzájemně vylučují. Všechny hodnotové typy musí mít dostupný konstruktor bez parametrů. `struct` Znamená omezení `new()` omezení a `new()` omezení nelze kombinovat s `struct` omezení. `unmanaged` Omezení znamená, `struct` omezení. `unmanaged` Omezení nelze kombinovat s buď `struct` nebo `new()` omezení.

## <a name="why-use-constraints"></a>Proč používat omezení

Pomocí omezení parametru typu, zvyšte počet povolených operací a volání metody, které jsou podporovány omezující typ a všechny typy v hierarchii dědičnosti. Při návrhu obecných tříd nebo metod, pokud jste se všechny operace na obecné členy nad rámec jednoduché přiřazení nebo voláním jakékoli metody, které nepodporují <xref:System.Object?displayProperty=nameWithType>, budete muset použít omezení parametru typu. Například omezení základní třídy instruuje kompilátor, že pouze objekty tohoto typu nebo odvozený z tohoto typu se použije jako argumenty typu. Jakmile kompilátor této záruky, můžete povolit metody tohoto typu k volání v obecné třídě. Následující příklad kódu ukazuje funkce, můžete přidat `GenericList<T>` třídy (v [Úvod do obecných typů](introduction-to-generics.md)) s použitím omezení základní třídy.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

Omezení umožňuje použití obecné třídy `Employee.Name` vlastnost. Omezení, která určuje všechny položky typu `T` je zaručeno, že se buď `Employee` objektu nebo objekt, který dědí z `Employee`.

Více omezení můžete použít pro stejný parametr typu a omezení sami může být obecné typy, následujícím způsobem:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

Při použití `where T : class` omezení, vyhněte `==` a `!=` operátory u parametru typu vzhledem k tomu, že tyto operátory testovat odkaz identity jenom, ne pro rovnost hodnot. K tomuto chování dochází i v případě, že jsou tyto operátory přetíženy v typu, který se používá jako argument. Následující kód znázorňuje tento bod; i když má hodnotu false výstup <xref:System.String> třídy přetížení `==` operátor.

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

Kompilátor ví pouze, že T je typ odkazu v době kompilace a musí používat výchozí operátory, které jsou platné pro všechny typy odkazů. Pokud musíte otestovat pro hodnotu rovnosti, doporučený postup je také použít `where T : IEquatable<T>` nebo `where T : IComparable<T>` omezení a implementovat rozhraní do třídy, která se použije k vytvoření obecné třídy.

## <a name="constraining-multiple-parameters"></a>Omezení více parametrů

Více parametrů a více omezení na jeden parametr, můžete použít omezení, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a>Parametry typu bez vazby

 Zadejte parametry, které obsahují bez omezení, jako je například T v veřejnou třídu `SampleClass<T>{}`, jsou označované jako parametry typu bez vazby. Parametry typu bez vazby mají následující pravidla:

- `!=` a `==` operátory nelze použít, protože neexistuje žádná záruka, že argument typu implementujícího typ bude podporovat tyto operátory.
- Může být převeden do a z `System.Object` nebo explicitně převést na libovolný typ rozhraní.
- Můžete porovnat jim [null](../../language-reference/keywords/null.md). Pokud bez vazby parametru je ve srovnání s `null`, porovnání vždy vrátí hodnotu false, pokud typ argumentu je typ hodnoty.

## <a name="type-parameters-as-constraints"></a>Parametry typu jako omezení

Použití parametru obecného typu je užitečné, když členské funkce s vlastním parametrem typu omezení má omezení parametru pro parametr typu nadřazeného typu, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

V předchozím příkladu `T` se omezení typu v kontextu `Add` metoda a parametr typu bez vazby v kontextu `List` třídy.

Parametry typu lze také použít jako omezení pro definice obecných tříd. Parametr typu musí být deklarována v lomených závorkách společně s další parametry typu:

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

Užitečnost parametry typu jako omezení pomocí obecných tříd je omezený, protože kompilátor může převzít nic neříká o parametr typu s tím rozdílem, že se odvozuje od `System.Object`. Parametry typu použijte jako omezení u obecných tříd ve scénářích, ve kterých chcete vynutit vztah dědičnosti mezi dvěma parametry typu.

## <a name="unmanaged-constraint"></a>Nespravované omezení

Od verze C# 7.3, můžete použít `unmanaged` omezení, které chcete určit, že musí být parametr typu **nespravovaný typ**. **Nespravovaný typ** je typ, který není typem odkazu a neobsahuje pole typu odkazu na libovolné úrovni vnoření. `unmanaged` Omezení umožňuje zapisovat opakovaně použitelných rutin pro práci s typy, které lze manipulovat jako bloky paměti, jak je znázorněno v následujícím příkladu:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

Předchozí metoda musí být zkompilovány do `unsafe` kontextu protože používá `sizeof` operátor pro typ není známé jako předdefinovaný typ. Bez `unmanaged` omezení, `sizeof` operátor není k dispozici.

## <a name="delegate-constraints"></a>Omezení delegáta

Také od verze C# 7.3, můžete použít <xref:System.Delegate?displayProperty=nameWithType> nebo <xref:System.MulticastDelegate?displayProperty=nameWithType> jako základní třída omezení. Modul CLR je vždycky povolená omezení, ale jazyk C# je zakázané. `System.Delegate` Omezení umožňuje napsat kód, který funguje s delegáty způsobem typově bezpečné. Následující kód definuje metodu rozšíření, která kombinuje dva delegáty předpokladu, že jsou stejného typu:

[!code-csharp[using the delegate constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

Výše uvedené metody můžete kombinovat delegáty, kteří jsou stejného typu:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

Pokud můžete zrušit komentář na posledním řádku, nebude kompilovat. Obě `first` a `test` jsou typy delegátů, ale jsou typy různých delegáta.

## <a name="enum-constraints"></a>Omezení enum

Od C# 7.3, můžete také určit <xref:System.Enum?displayProperty=nameWithType> typ jako základní třída omezení. Modul CLR je vždycky povolená omezení, ale jazyk C# je zakázané. Použití obecných typů `System.Enum` poskytují zajišťující bezpečnost typů programování výsledky do mezipaměti pomocí statické metody v `System.Enum`. Následující příklad vyhledá všechny platné hodnoty pro typ výčtu a poté sestaví slovník, který mapuje tyto hodnoty na řetězcové vyjádření.

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

Ujistěte se, metod používaných využívání reflection, což má vliv na výkon. Můžete volat tuto metodu za účelem vytvoření kolekce, která je do mezipaměti a znovu použít namísto opakování volání, které vyžadují reflexe.

Můžete ji třeba použít jak je znázorněno v následujícím příkladu vytvořit výčet a vytvářet slovník jeho hodnoty a názvy:

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Generic>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [Obecné třídy](../../../csharp/programming-guide/generics/generic-classes.md)  
- [new – omezení](../../../csharp/language-reference/keywords/new-constraint.md)  
