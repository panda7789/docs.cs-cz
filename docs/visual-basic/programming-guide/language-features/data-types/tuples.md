---
title: Řazené kolekce členů v jazyce Visual Basic
ms.date: 04/23/2017
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
ms.openlocfilehash: 146e9c2360cea153d2f487769d5b983516861e8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663294"
---
# <a name="tuples-visual-basic"></a>Řazené kolekce členů (Visual Basic)

Počínaje rokem 2017 jazyka Visual Basic, jazyka Visual Basic nabízí vestavěnou podporu pro řazené kolekce členů, díky vytváření řazených kolekcí členů a přístupu k prvkům jednodušší řazených kolekcí členů. Řazená kolekce členů je odlehčené datová struktura, která má určitý počet a pořadí hodnot. Při vytváření instance řazené kolekce členů, můžete definovat počtu a typu dat každé hodnoty (nebo element). Například 2 řazené kolekce členů (nebo dvojice) obsahuje dva elementy. Může být první `Boolean` hodnoty, zatímco druhá je `String`. Protože řazených kolekcí členů usnadňují uložení více hodnot v jednom objektu, často se používají jako jednoduchý způsob, jak vrátit více hodnot z metody.

> [!IMPORTANT]
> Podpora řazené kolekce členů vyžaduje <xref:System.ValueTuple> typu. Pokud není nainstalované rozhraní .NET Framework 4.7, je nutné přidat balíček NuGet `System.ValueTuple`, která je dostupná v galerii NuGet. Bez tohoto balíčku můžete obdržet chybu kompilace podobný "Předdefinovaný typ 'ValueTuple(Of,,,)' není definován ani importován."

## <a name="instantiating-and-using-a-tuple"></a>Vytváření instancí a použití řazené kolekce členů

Řazená kolekce členů instance uzavřením jeho závorky zasílání rychlých zpráv hodnot oddělených čárkami. Každá z těchto hodnot se pak stane polem řazené kolekce členů. Například následující kód definuje triple (nebo 3 řazené kolekce členů) s `Date` jako první hodnota, `String` jako jeho druhé a `Boolean` jako jeho třetí.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

Ve výchozím nastavení, název každé pole v řazené kolekce členů se skládá z řetězce `Item` spolu s pole založen na jedničce pozici v řazené kolekci členů. Pro tento 3-řazené kolekce členů `Date` pole je `Item1`, `String` pole je `Item2`a `Boolean` pole je `Item3`. Následující příklad zobrazí hodnoty polí řazené kolekce členů v předchozí řádek kódu

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

Čtení a zápis; jsou pole řazená kolekce členů jazyka Visual Basic poté, co jste se vytvořit instanci řazené kolekce členů, můžete její hodnoty upravit. Následující příklad upraví dva ze tří polí řazené kolekce členů v předchozím příkladu vytvoří a zobrazí výsledek.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a>Vytváření instancí a použití pojmenované řazené kolekce členů

Místo používání výchozích názvů polí se řazená kolekce členů, můžete vytvořit instanci *řazené kolekce členů s názvem* přiřazením vlastní názvy prvků řazené. Řazené pole lze poté přistupovat podle jejich přiřazené názvů *nebo* podle jejich výchozími názvy. Následující příklad vytvoří instanci stejného 3-řazené kolekce členů jako dříve, s tím rozdílem, že explicitně názvy první pole `EventDate`, druhý `Name`a třetí `IsHoliday`. Potom zobrazí hodnoty polí, upraví je a znovu zobrazí hodnoty polí.

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a>Názvy elementů řazené kolekce členů odvozeného

Od verze 15.3 jazyka Visual Basic, Visual Basic lze odvodit názvy prvků řazené kolekce členů. není nutné je explicitně přiřadit. Názvy odvozené řazené kolekce členů jsou užitečné při inicializaci řazenou kolekci členů ze skupiny proměnných, a chcete, aby název elementu řazené kolekce členů bude stejný jako název proměnné. 

Následující příklad vytvoří `stateInfo` řazené kolekce členů, která obsahuje tři explicitně pojmenované elementy, `state`, `stateName`, a `capital`. Všimněte si, že názvů elementů, příkaz inicializace řazené kolekce členů jednoduše přiřadí pojmenované elementy hodnoty proměnných identicky pojmenovanou.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
Protože elementy a proměnné mají stejný název, Visual Basic kompilátor může odvodit názvy polí, jak ukazuje následující příklad.

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

Povolit názvy elementů řazené kolekce členů odvozené, je nutné definovat verzi kompilátoru jazyka Visual Basic pro použití v projektu jazyka Visual Basic (\*.vbproj) souboru: 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 
```

Číslo verze může být jakékoli verzi kompilátoru jazyka Visual Basic od verze 15.3. Místo pevného kódování specifické verzi kompilátoru, můžete také zadat "Poslední zálohy" jako hodnotu `LangVersion` ke kompilaci v nejnovější verzi kompilátoru jazyka Visual Basic, který je nainstalovaný ve vašem systému.

Další informace najdete v tématu [nastavení verze jazyka Visual Basic](../../../language-reference/configure-language-version.md).

V některých případech kompilátor jazyka Visual Basic nelze odvodit název elementu řazené kolekce členů z názvu Release candidate a pole řazené kolekce členů může být odkazováno pouze pomocí jeho výchozí název, například `Item1`, `Item2`atd. Zde jsou některé z nich:

- Název Release candidate je stejný jako název člena řazené kolekce členů jako `Item3`, `Rest`, nebo `ToString`.

- Název Release candidate je duplicitní v řazené kolekci členů.
 
Po odvození název pole selže, Visual Basic nevygeneruje chybu kompilátoru, ani je výjimka vyvolána v době běhu. Místo toho pole řazené kolekce členů musí být referencován předdefinované názvy, například `Item1` a `Item2`. 
  
## <a name="tuples-versus-structures"></a>Řazených kolekcí členů a struktury

Řazená kolekce členů jazyka Visual Basic je hodnotový typ, který je instance jednoho z **System.ValueTuple** obecných typů. Například `holiday` řazené kolekce členů definované v předchozím příkladu je instance <xref:System.ValueTuple%603> struktury. To je navržena jako jednoduchý kontejner pro data. Protože řazené kolekce členů, zaměřuje na snadno vytvořit objekt s více datovými položkami, chybí některé z funkcí, které může mít vlastní struktury. Zde jsou některé z nich:

- Vlastní členy. Nelze definovat vlastní vlastnosti, metody nebo události pro řazené kolekce členů.

- Ověření. Nelze ověřit data přiřazeny k polím.

- Neměnnost. Řazené kolekce členů jazyka Visual Basic jsou měnitelné. Naproti tomu vlastní struktury umožňuje řídit, jestli je instance proměnlivé nebo neměnné.

Pokud vlastními členy, vlastnost a pole ověření nebo neměnnosti jsou důležité, abyste používali jazyka Visual Basic [struktura](../../../language-reference/statements/structure-statement.md) příkaz k definování vlastní hodnotového typu.

Řazená kolekce členů jazyka Visual Basic dědí členy jeho **typu ValueTuple** typu. Kromě polí patří mezi ně následující metody:

| Člen | Popis |
| ---|---|
| CompareTo | Porovná aktuální řazenou kolekci členů na jiné řazené kolekce členů se stejný počet prvků. |
| Je rovno | Určuje, zda se k jinému řazené kolekce členů nebo objekt rovná aktuální řazenou kolekci členů. |
| GetHashCode | Vypočítá kód hash pro aktuální instanci. |
| ToString | Vrátí řetězcovou reprezentaci této řazené kolekce členů, který má podobu `(Item1, Item2...)`, kde `Item1` a `Item2` představují hodnoty řazené pole. |

Kromě toho **typu ValueTuple** typy implementovat <xref:System.Collections.IStructuralComparable> a <xref:System.Collections.IStructuralEquatable> rozhraní, které umožňují definovat komparátory zákazníka.

## <a name="assignment-and-tuples"></a>Přiřazení a řazené kolekce členů

Visual Basic podporuje přiřazení mezi typy řazené kolekce členů, které mají stejný počet polí. Typy pole lze převést, pokud platí jedna z následujících akcí:

- Zdrojové a cílové pole je stejného typu.

- Rozšiřující (nebo implicitní) převod zdrojového typu na cílový typ je definován. 

- `Option Strict` je `On`, a převod zužující (nebo explicitní) typem zdroje na cílový typ je definován. Tento převod může vyvolat výjimku, pokud zdrojová hodnota je mimo rozsah cílového typu.

Ostatní převody, které nejsou považované za pro přiřazení. Pojďme se podívat na typy přiřazení, které jsou povolené mezi typy řazené kolekce členů.

Vezměte v úvahu tyto proměnné, používat v následujících příkladech:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

První dvě proměnné `unnamed` a `anonymous`, nemají sémantické názvy, které jsou k dispozici pro pole. Jejich názvy polí jsou výchozí `Item1` a `Item2`. Poslední dvě proměnné, `named` a `differentName` mají názvy sémantické pole. Všimněte si, že tyto dvě řazené kolekce členů mají různé názvy polí.

Všechny čtyři tyto řazených kolekcí členů mají stejný počet polí (dále jako "Arita") a typy těchto polí jsou identické. Proto všechny tato přiřazení práce:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Všimněte si, že nejsou přiřazeny názvy řazené kolekce členů. Hodnoty polí jsou přiřazeny následující pořadí polí v řazené kolekci členů.

Konečně si všimněte, že můžeme přiřadit `named` řazená kolekce členů k `conversion` řazené kolekce členů, i v případě, první pole `named` je `Integer`a na první pole `conversion` je `Long`. Toto přiřazení bude úspěšné, protože převod `Integer` k `Long` je rozšiřující převod.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Řazené kolekce členů s různými počty polí nejsou přiřadit:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a>Řazené kolekce členů jako návratové hodnoty metod

Metoda může vrátit pouze jednu hodnotu. Často ale chcete volání metody vrátí více hodnot. Toto omezení vyřešit několika způsoby:

- Můžete vytvořit vlastní třídu nebo strukturu, jejíž vlastnosti nebo pole představují hodnoty vrácený metodou. Proto je těžký řešení; vyžaduje, že definujete vlastní typ, jehož jediným účelem je k načtení hodnoty z volání metody.

- Můžete vracet jedinou hodnotu z metody a vrátit zbývající hodnoty byly předány podle odkazu na metodu. To zahrnuje vytvoření instance proměnné a rizika nechtěném přepsání hodnotu proměnné, která se předávají odkazem režii.

- Můžete použít řazenou kolekci členů, které poskytuje jednoduché řešení, které načítají více návratových hodnot.

Například **TryParse** metody v rozhraní .NET vrátit `Boolean` hodnotu, která určuje, zda operace analýzy proběhla úspěšně. Výsledek operace analýzy je vrácen do proměnné předány podle odkazu na metodu. Za normálních okolností volání metody analýzy jako <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> vypadá podobně jako následující:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

My jsme zabalte volání do vrátit řazené kolekce členů z operace analýzy <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metoda v naší metodě. V následujícím příkladu `NumericLibrary.ParseInteger` volání <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodu a vrátí pojmenované řazené kolekce členů se dvěma elementy. 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

Pak můžete volat metodu s kódem, jako je následující:

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a>Visual Basic řazených kolekcí členů a řazenými kolekcemi členů v rozhraní .NET Framework

Řazená kolekce členů jazyka Visual Basic je instance jednoho z **System.ValueTuple** obecné typy, které byly zavedeny v rozhraní .NET Framework 4.7. Rozhraní .NET Framework obsahuje také sadu obecného **System.Tuple** třídy. Tyto třídy, ale liší od řazených kolekcí členů jazyka Visual Basic a **System.ValueTuple** obecné typy v několika způsoby:

- Prvky **řazené kolekce členů** třídy jsou vlastnosti s názvem `Item1`, `Item2`, a tak dále. V jazyce Visual Basic řazených kolekcí členů a **typu ValueTuple** typy elementů řazené kolekce členů jsou pole.

- Elementy nelze přiřadit smysluplné názvy **řazené kolekce členů** instance nebo **typu ValueTuple** instance. Visual Basic umožňuje přiřadit názvy, které sdělit význam pole.

- Vlastnosti **řazené kolekce členů** instance jsou jen pro čtení; řazené kolekce členů jsou neměnné. V jazyce Visual Basic řazených kolekcí členů a **typu ValueTuple** typy, pole řazené kolekce členů jsou pro čtení i zápis; řazené kolekce členů jsou měnitelné.

- Obecné **řazené kolekce členů** typy jsou typy odkazů. Použití těchto **řazené kolekce členů** typy znamená, že přidělování objektů. V horké cesty to může být měřitelný dopad na výkon vaší aplikace. Visual Basic řazených kolekcí členů a **typu ValueTuple** typy jsou typy hodnot.

Rozšiřující metody v <xref:System.TupleExtensions> třídy usnadňují převod mezi řazenými kolekcemi členů jazyka Visual Basic a .NET **řazené kolekce členů** objekty. **ToTuple** metoda převede řazené kolekce členů jazyka Visual Basic .NET **řazené kolekce členů** objektu a **ToValueTuple** metoda převede .NET **řazené kolekce členů** objekt řazené kolekce členů jazyka Visual Basic.

Následující příklad vytvoří řazenou kolekci členů, převede ho na .NET **řazené kolekce členů** objektu a převede ho zpátky do jazyka Visual Basic řazené kolekce členů. Příklad poté porovnává této řazené kolekce členů s původní, abyste zajistili, že jsou shodné.

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a>Viz také:

- [Referenční příručka jazyka Visual Basic](index.md)
