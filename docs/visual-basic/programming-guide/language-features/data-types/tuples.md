---
title: "Řazené kolekce členů v jazyce Visual Basic"
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2653b9dc8a6ecbcb718c20be8bd6275edf4cfb6e
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="tuples-visual-basic"></a>Řazené kolekce členů (Visual Basic)

Počínaje 2017 Visual Basic, jazyka Visual Basic má integrovanou podporu pro řazené kolekce členů, která umožňuje vytváření řazených kolekcí členů a přístup k elementům jednodušší řazené kolekce členů. Řazené kolekce členů je šedé – datová struktura, která má specifické číslo a pořadí hodnot. Pokud instanci můžete vytvořit řazenou kolekci členů, můžete definovat číslo a datový typ jednotlivých hodnota (nebo element). Například 2 řazené kolekce členů (nebo dvojici) má dva elementy. Může být první `Boolean` hodnotu, zatímco druhý `String`. Protože řazených kolekcí členů usnadňují ukládat víc hodnot v jednom objektu, se často používají jako lehký způsob, jak vrátit více hodnot z metody.

> [!IMPORTANT]
> Vyžaduje podporu řazené kolekce členů <xref:System.ValueTuple> typu. Pokud není nainstalovaná rozhraní .NET Framework 4.7, je nutné přidat balíček NuGet `System.ValueTuple`, která je k dispozici v galerii NuGet. Bez tohoto balíčku může se zobrazit chyba kompilace podobná "Předdefinované type 'ValueTuple(Of,,,)' není definované nebo importovat."

## <a name="instantiating-and-using-a-tuple"></a>Vytváření instancí a použití řazené kolekce členů

Řazené kolekce členů instance uzavřením závorkách zasílání rychlých zpráv hodnot oddělených čárkami. Každý z těchto hodnot se pak stane pole řazenou kolekci členů. Například následující kód definuje triple (nebo 3 řazené kolekce členů) `Date` jako svou první hodnotu `String` jako jeho sekundu a `Boolean` jako jeho třetí.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Ve výchozím nastavení, název každého pole v řazené kolekce členů se skládá z řetězce `Item` společně s tohoto pole na základě jedné pozice v řazené kolekci členů. Pro tento 3-řazené kolekce členů `Date` pole je `Item1`, `String` pole je `Item2`a `Boolean` pole je `Item3`. Tento příklad zobrazuje hodnoty polí řazené kolekce členů instanci v předchozím řádku kódu

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Čtení a zápis; jsou tato pole řazené kolekce členů jazyka Visual Basic poté, co jste instanci řazené kolekce členů, můžete její hodnoty upravit. Následující příklad změní dvě ze tří polí řazené kolekce členů vytvořili v předchozím příkladu a zobrazí výsledek.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Vytváření instancí a použití pojmenovaného řazené kolekce členů

Místo použití výchozí názvy polí řazené kolekce členů, můžete vytvořit instanci *s názvem řazené kolekce členů* přiřazením vlastní názvy elementů řazené kolekce členů. Pole řazené kolekce členů lze přistupovat pomocí jejich přiřazené názvy *nebo* jejich výchozí názvy. Následující příklad vytvoří stejné 3-n-tice jako dříve, s tím rozdílem, že ji explicitně názvy první pole `EventDate`, druhý `Name`a třetí `IsHoliday`. Pak zobrazí hodnoty polí, upraví je a znovu zobrazuje hodnoty polí.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Názvy elementů odvozené řazené kolekce členů

Počínaje 15.3 jazyka Visual Basic, Visual Basic můžete odvození názvy elementů řazené kolekce členů; není nutné explicitně přiřadit. Odvozené řazené kolekce členů názvy jsou užitečné při inicializaci řazenou kolekci členů ze sady proměnných a chcete, aby název elementu řazené kolekce členů být stejný jako název proměnné. 

Následující příklad vytvoří `stateInfo` řazené kolekce členů, která obsahuje tři explicitně s názvem elementů `state`, `stateName`, a `capital`. Všimněte si, že v pojmenování elementy, příkaz inicializace řazené kolekce členů jednoduše přiřadí pojmenované elementy hodnoty proměnných stejně jako s názvem.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
Protože elementy a proměnné mají stejný název, Visual Basic – kompilátor můžete odvození názvy polí, jak ukazuje následující příklad.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

Pokud chcete povolit názvy elementů interred řazené kolekce členů, je nutné zadat verzi kompilátoru jazyka Visual Basic pro použití v projektu jazyka Visual Basic (\*.vbproj) souboru: 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 

The version number can be any version of the Visual Basic compiler starting with 15.3. Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.

In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:

- The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.

- The candidate name is duplicated in the tuple.
 
When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime. Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`. 
  
## Tuples versus structures

A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types. For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure. It is designed to be a lightweight container for data. Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have. These include:

- Customer members. You cannot define your own properties, methods, or events for a tuple.

- Validation. You cannot validate the data assigned to fields.

- Immutability. Visual Basic tuples are mutable. In contrast, a custom structure allows you to control whether an instance is mutable or immutable.

If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.

A Visual Basic tuple does inherit the members of its **ValueTuple** type. In addition to its fields, these include the following methods:

| Member | Description |
| ---|---|
| CompareTo | Compares the current tuple to another tuple with the same number of elements. |
| Equals | Determines whether the current tuple is equal to another tuple or object. |
| GetHashCode | Calculates the hash code for the current instance. |
| ToString | Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields. |

In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.

## Assignment and tuples

Visual Basic supports assignment between tuple types that have the same number of fields. The field types can be converted if one of the following is true:

- The source and target field are of the same type.

- A widening (or implicit) conversion of the source type to the target type is defined. 

- `Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined. This conversion can throw an exception if the source value is outside the range of the target type.

Other conversions are not considered for assignments. Let's look at the kinds of assignments that are allowed between tuple types.

Consider these variables used in the following examples:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields. Their field names are the default `Item1` and `Item2`. The last two variables, `named` and `differentName` have semantic field names. Note that these two tuples have different names for the fields.

All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical. Therefore, all of these assignments work:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notice that the names of the tuples are not assigned. The values of the fields are assigned following the order of the fields in the tuple.

Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`. This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuples with different numbers of fields are not assignable:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Řazené kolekce členů jako metodu návratové hodnoty

Metoda může vrátit pouze jednu hodnotu. Často ale chcete volání metoda vrátí více hodnot. Toto omezení obejít několika způsoby:

- Můžete vytvořit vlastní třídu nebo strukturu, jehož vlastnosti nebo pole představují hodnoty vrácené metodou. Proto je těžké řešení; To vyžaduje, aby definujete vlastní typ, jehož jediným účelem je načítání hodnot z volání metody.

- Můžete vrátit jednu hodnotu z metody a vrátit zbývající hodnoty předáním odkazu na metodu. To zahrnuje režií při vytváření instance proměnné a rizika nechtěném přepsání hodnotu proměnné, kterou předáte odkazem.

- Můžete použít řazenou kolekci členů, která poskytuje jednoduché řešení pro načítání více vrácených hodnot.

Například **TryParse** metody v rozhraní .NET vrátit `Boolean` hodnotu, která určuje, zda analýza operace byla úspěšně dokončena. Výsledek analýzy operace se vrátí do proměnné předaná odkazu na metodu. Za normálních okolností volání metoda analýzy, jako <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> vypadá podobně jako následující:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

Se jsme zabalení volání vrací řazenou kolekci členů z analýzy operace <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metoda vlastní metoda. V následujícím příkladu `NumericLibrary.ParseInteger` volání <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodu a vrátí pojmenované řazené kolekce členů s dva elementy. 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Pak můžete volat metodu s kódem podobně jako tento:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Řazené kolekce členů jazyka Visual Basic a řazených kolekcí členů v rozhraní .NET Framework

Visual Basic řazené kolekce členů je instance jednoho **System.ValueTuple** obecné typy, které byly zavedeny v 4.7 rozhraní .NET Framework. Rozhraní .NET Framework také obsahuje sadu obecného **System.Tuple** třídy. Tyto třídy, ale liší od řazených kolekcí členů jazyka Visual Basic a **System.ValueTuple** obecné typy v mnoha různými způsoby:

- Elementy **řazené kolekce členů** třídy jsou vlastnosti s názvem `Item1`, `Item2`a tak dále. V jazyce Visual Basic řazených kolekcí členů a **ValueTuple** pole jsou typy, elementy řazené kolekce členů.

- Nelze přiřadit řádkům elementy **řazené kolekce členů** instance nebo **ValueTuple** instance. Visual Basic umožňuje přiřadit názvy, které komunikují význam pole.

- Vlastnosti **řazené kolekce členů** instance jsou jen pro čtení, jsou neměnné řazené kolekce členů. V jazyce Visual Basic řazených kolekcí členů a **ValueTuple** typy, jsou řazené kolekce členů pole pro čtení a zápis; jsou měnitelný řazené kolekce členů.

- Obecná **řazené kolekce členů** typy jsou odkazové typy. Použití těchto **řazené kolekce členů** typy znamená přidělování objektů. V aktivní cesty to může být měřitelný dopad na výkon vaší aplikace. Řazené kolekce členů jazyka Visual Basic a **ValueTuple** typy jsou typy hodnot.

Rozšiřující metody v <xref:System.TupleExtensions> třída usnadňují převod mezi řazených kolekcí členů jazyka Visual Basic a .NET **řazené kolekce členů** objekty. **ToTuple** metoda převede řazené kolekce členů jazyka Visual Basic .NET **řazené kolekce členů** objekt a **ToValueTuple** metoda převede .NET **řazené kolekce členů** objekt řazené kolekce členů jazyka Visual Basic.

Následující příklad vytvoří řazenou kolekci členů, převede ji na .NET **řazené kolekce členů** objekt a převede ji zpět do Visual Basic řazené kolekce členů. V příkladu pak porovná tato řazené kolekce členů s původní, abyste zajistili, že jsou stejné.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka Visual Basic](index.md)  
