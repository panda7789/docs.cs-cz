---
title: "Řazené kolekce členů v jazyce Visual Basic"
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be50b22e9acca9ff8cfbde798d78869ee1c72634
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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

## <a name="tuples-versus-structures"></a>Řazené kolekce členů a struktury

Visual Basic řazené kolekce členů je typ hodnoty, která je instance jednoho z **System.ValueTuple** obecné typy. Například `holiday` řazené kolekce členů definované v předchozím příkladu představuje instanci <xref:System.ValueTuple%603> struktura. Je určený jako lightweight kontejner pro data. Vzhledem k tomu, že řazenou kolekci členů cílem je usnadnit práci pro vytvoření objektu s více datovými položkami, chybí některé funkce, které by mohly mít do vlastní struktury. Mezi ně patří:

- Členy zákazníka. Nelze definovat vlastní vlastnosti, metody nebo události pro řazené kolekce členů.

- Ověření. Nelze ověřit data přiřazené pole.

- Neměnitelnosti. Měnitelný jsou řazené kolekce členů jazyka Visual Basic. Naproti tomu do vlastní struktury umožňuje určit informaci, jestli instance měnitelný nebo neměnné.

Pokud vlastní členy, vlastnost a pole ověření nebo neměnitelnosti jsou důležité, abyste používali Visual Basicu [struktura](../../../language-reference/statements/structure-statement.md) příkaz k definování typu vlastní hodnoty.

Visual Basic řazené kolekce členů dědění členů jeho **ValueTuple** typu. Kromě jeho polí mezi ně patří následující metody:

| Člen | Popis |
| ---|---|
| CompareTo | Porovná aktuální řazenou kolekci členů do jiné řazené kolekce členů s stejný počet elementů. |
| Rovná se | Určuje, zda aktuální řazenou kolekci členů je rovno jiné řazené kolekce členů nebo objekt. |
| GetHashCode | Vypočítá kód hash pro aktuální instanci. |
| ToString | Vrátí řetězcovou reprezentaci této řazené kolekce členů, která má tvar `(Item1, Item2...)`, kde `Item1` a `Item2` představují hodnoty polí řazené kolekce členů. |

Kromě toho **ValueTuple** typy implementovat <xref:System.Collections.IStructuralComparable> a <xref:System.Collections.IStructuralEquatable> rozhraní, které umožňují definovat komparátory zákazníka.

## <a name="assignment-and-tuples"></a>Přiřazení a řazených kolekcí členů

Visual Basic podporuje přiřazení mezi typy řazené kolekce členů, které mají stejný počet polí. Typy polí lze převést, pokud platí jedna z následujících akcí:

- Zdrojové a cílové pole jsou stejného typu.

- Rozšiřující (nebo implicitní) převodu typ zdroje pro cílový typ je definována. 

- `Option Strict`je `On`, a narrowing (nebo explicitní) převodu typ zdroje pro cílový typ je definovaná. Tento převod může vyvolat výjimku, pokud je zdroj hodnota mimo rozsah typu cíle.

Jiné převody nejsou považovány za přiřazení. Podívejme se na druhy přiřazení, které jsou povoleny mezi typy řazené kolekce členů.

Vezměte v úvahu tyto proměnné použít v následujících příkladech:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

První dvě proměnné, `unnamed` a `anonymous`, nemají sémantického názvy zadaná pro pole. Jejich názvy polí jsou výchozí `Item1` a `Item2`. Poslední dvě proměnné, `named` a `differentName` mít názvy sémantického pole. Všimněte si, že tyto dvě řazené kolekce členů mají odlišné názvy polí.

Všechny čtyři tyto řazené kolekce členů mít stejný počet polí (označované jako "Arita") a typy těchto polí jsou identické. Proto všechny tyto přiřazení fungovat:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Všimněte si, že nejsou přiřazeny názvy řazené kolekce členů. Hodnoty polí jsou přiřazeny následující pořadí polí v řazené kolekci členů.

Všimněte si, že jsme můžete přiřadit `named` řazené kolekce členů k `conversion` řazené kolekce členů, i když první pole `named` je `Integer`a první pole `conversion` je `Long`. Toto přiřazení se podaří, protože převod `Integer` k `Long` je rozšiřující převod.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Řazené kolekce členů s odlišný počet polí nejsou přiřadit:

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
