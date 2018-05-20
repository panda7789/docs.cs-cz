---
title: Typy řazené kolekce členů – Průvodce C#
description: Další informace o typech pojmenované a nepojmenované řazené kolekce členů v jazyce C#
ms.date: 05/15/2018
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 5ef8d89f62a30d3d64f7377972e31d9c4d93d41e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="c-tuple-types"></a>Řazené kolekce členů typy C# #

C# řazených kolekcí členů jsou typy, které definujete pomocí jednoduché syntaxe. Výhody zahrnují jednodušší syntaxe, pravidla pro převody na základě číslo (označované jako mohutnost) a typy elementů a konzistentní pravidla pro kopie, rovnosti testy a přiřazení. Jako kompromis řazené kolekce členů nepodporují některé objektově orientované idioms, přidružené dědičnosti. V části můžete získat přehled [řazených kolekcí členů v co je nového v C# 7.0](whats-new/csharp-7.md#tuples) článku.

V tomto článku se dozvíte jazyk pravidla pro řazených kolekcí členů v C# 7.0 a novější verze, různé způsoby použití je a počáteční pokyny o práci s řazenými kolekcemi členů.

> [!NOTE]
> Vyžadovat nové funkce řazených kolekcí členů <xref:System.ValueTuple> typy.
> Je nutné přidat balíček NuGet [ `System.ValueTuple` ](https://www.nuget.org/packages/System.ValueTuple/) odborných na platformách, které neobsahují typy.
>
> Toto je podobná jiné jazykové funkce, které závisí na typech doručit v rámci. Mezi příklady patří `async` a `await` spoléhat na `INotifyCompletion` rozhraní a LINQ spoléhat na `IEnumerable<T>`. Jak .NET se stává stále další platformy, které jsou nezávislé, mechanismus doručování mění. Rozhraní .NET Framework nemusí vždy dodávat na stejné cadence jako kompilátor jazyka. Nové jazykové funkce využívají nové typy, tyto typy nebudou mít k dispozici jako balíčků NuGet při odeslání funkce jazyka. Tyto nové typy získat přidávají do rozhraní API .NET standardní a dodávána jako součást rozhraní, požadavek na balíček NuGet se odeberou.

Začněme důvody pro přidání nové podpory řazené kolekce členů. Metody vrací jeden objekt. Řazené kolekce členů umožňují snadněji balíček více hodnot v jednom objektu.

Rozhraní .NET Framework již má obecný `Tuple` třídy. Tyto třídy, ale měl dvě hlavní omezení. Pro jeden `Tuple` třídy s názvem jejich vlastnosti `Item1`, `Item2`a tak dále. Tyto názvy provádění žádné sémantické informace. Použití těchto `Tuple` typy neumožňuje komunikaci význam každé z vlastností. Mezi nové jazykové funkce umožňují deklarování a použití sémanticky smysluplné názvy pro elementy v řazené kolekce členů.

`Tuple` Třídy způsobit další nedostatečnému výkonu, protože jsou odkazové typy. Pomocí jedné z `Tuple` typy znamená přidělování objektů. V aktivní cesty přidělování mnoho malých objektů může být měřitelný dopad na výkon vaší aplikace. Proto využívá nové jazyková podpora pro řazené kolekce členů `ValueTuple` struktury.

Abyste se vyhnuli tyto nedostatky, můžete vytvořit `class` nebo `struct` k provedení více elementů. Bohužel se více práce pro uživatele a zakrývá vašich představ návrhu. Vytváření `struct` nebo `class` znamená, že definujete typu s daty a chování. Kolikrát jednoduše chcete uložit více hodnot v jednom objektu.

Funkce jazyka a `ValueTuple` obecné struktury vynutit pravidla, že není možné přidat žádné chování (metody) pro tyto typy řazené kolekce členů.
Všechny `ValueTuple` typy jsou *měnitelný struktury*. Každý člen pole je veřejná pole. Který umožní jejich velmi jednoduché. Ale, to znamená, že by se neměla používat řazených kolekcí členů kde neměnitelnosti je důležité.

Řazené kolekce členů jsou obě kontejnery data jednodušší a flexibilnější než `class` a `struct` typy. Podíváme se na tyto rozdíly.

## <a name="named-and-unnamed-tuples"></a>Pojmenované a nepojmenované řazených kolekcí členů

`ValueTuple` Struktura má pole s názvem `Item1`, `Item2`, `Item3`a tak dále podobná vlastnosti definované ve stávající `Tuple` typy.
Tyto názvy jsou pouze názvy, které můžete použít pro *nepojmenované řazených kolekcí členů*. Pokud nezadáte žádné pole alternativní názvy pro řazené kolekce členů, jste vytvořili nepojmenované řazené kolekce členů:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Řazené kolekce členů v předchozím příkladu byla inicializována pomocí literálu konstanty a nebude mít názvy elementů vytvořený *řazené kolekce členů pole Název projekce* v C# 7.1.

Při inicializaci řazené kolekce členů, ale můžete použít nové jazykové funkce, která umožňují lepší názvy pro každé pole. Tím vytvoříte *s názvem řazené kolekce členů*.
Pojmenované řazených kolekcí členů ještě elementů s názvem `Item1`, `Item2`, `Item3` a tak dále.
Ale mají také synonyma pro některý z těchto elementů, které mají pojmenované.
Vytvoříte tak, že zadáte názvy pro každý prvek s názvem řazené kolekce členů. Jedním ze způsobů je zadejte názvy během inicializace řazené kolekce členů:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Named tuple")]

Tyto synonyma jsou zpracovávány kompilátoru a jazyk, aby můžete použít název řazených kolekcí členů efektivně. Názvy těchto sémantického pomocí rozhraní API Roslyn může číst integrovaného vývojového prostředí a editory. Tyto názvy sémantického kdekoli ve stejném sestavení, můžete odkazovat elementů s názvem řazené kolekce členů. Kompilátor nahradí názvy, které jste definovali s `Item*` ekvivalenty při generování kompilovaný výstup. Kompilované Microsoft zprostředkující jazyk (MSIL) nezahrnuje názvy dali těchto elementů.

Od verze 7.1 C#, mohou být poskytovány názvy polí pro řazené kolekce členů z proměnných, které slouží k chybě při inicializaci řazenou kolekci členů. Tento proces se označuje jako  **[řazené kolekce členů projekce inicializátory](#tuple-projection-initializers)**. Následující kód vytvoří řazené kolekce členů s názvem `accumulation` elementy `count` (celé číslo), a `sum` (dvojitou).

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Kompilátor musí komunikovat tyto názvy, který jste vytvořili pro řazené kolekce členů, které jsou vráceny z veřejné metody nebo vlastnosti. V takových případech přidá kompilátor <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> atribut na metodu. Tento atribut obsahuje <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> seznamu vlastnost, která obsahuje názvy zadané pro jednotlivé elementy v řazené kolekci členů.

> [!NOTE]
> Vývojářské nástroje, jako je například Visual Studio, taky číst aby metadata a poskytnout IntelliSense a další funkce pomocí názvů polí metadat.

Je důležité si uvědomit, tyto základní základní informace o nové řazené kolekce členů a `ValueTuple` typu, chcete-li pochopit pravidla pro přiřazování s názvem řazených kolekcí členů k sobě navzájem.

## <a name="tuple-projection-initializers"></a>Inicializátory projekce řazené kolekce členů

Obecně platí řazené kolekce členů projekce inicializátory fungovat pomocí názvů pole nebo proměnné z pravé strany příkaz inicializace řazené kolekce členů.
Pokud je zadána explicitní název, který má přednost před libovolný předpokládané název. Například v následujícím inicializátoru jsou elementy `explicitFieldOne` a `explicitFieldTwo`, nikoli `localVariableOne` a `localVariableTwo`:

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Pro každé pole, kde není zadaný název explicitní se promítá implicitní název použít. Je nutné poskytnout sémantického názvy explicitně nebo implicitně. Názvy polí má následující inicializátoru `Item1`, jehož hodnota je `42` a `StringContent`, jehož hodnota je "Odpověď na všechno":

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#MixedTuple "mixed tuple")]

Existují dvě podmínky, které nejsou názvy polí candidate promítnuta na pole řazené kolekce členů:

1. Pokud název candidate je název vyhrazené řazené kolekce členů. Mezi příklady patří `Item3`, `ToString`. nebo `Rest`.
1. Pokud je název candidate duplicitní jiný název pole řazené kolekce členů, explicitní nebo implicitní.

Tyto podmínky zabránilo nejednoznačnosti. Tyto názvy by způsobilo to nejednoznačnost, pokud byly použity jako názvy polí pro pole v řazené kolekce členů. Ani jeden z těchto podmínek způsobit chyby při kompilaci. Místo toho elementy bez předpokládané názvy nemají sémantického názvy pro ně k projekci.  Následující příklady ukazují tyto podmínky:

[!code-csharp[Ambiguity](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

V takových situacích nezpůsobí chyby kompilátoru, protože který by byl narušující změně kódu, které jsou napsané v C# 7.0, když řazené kolekce členů pole Název projekce nebyly dostupné.

## <a name="equality-and-tuples"></a>Rovnost a řazených kolekcí členů

Počínaje 7.3 C#, řazené kolekce členů typy podpory `==` a `!=` operátory. Tyto operátory fungovat tak, že porovnáte každý člen levý argument pro každého člena pravý argument v pořadí. Krátká smyčka tyto porovnání. `==` Operátor zastaví, jakmile jednu dvojici se nerovná vyhodnocení členů. `!=` Operátor zastaví také jednu dvojici rovná vyhodnocení členů. Následující příklady kódu používají `==`, ale pravidla porovnání všechny týkají `!=`. Následující příklad kódu ukazuje porovnání rovnosti pro dvě dvojice celých čísel:

[!code-csharp[TupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#Equality "Testing tuples for equality")]

Existuje několik pravidel, která pohodlnější provádění testů rovnosti řazené kolekce členů. Provede řazené kolekce členů rovnosti [zrušeno převody](/dotnet/csharp/language-reference/language-specification/conversions.md#lifted-conversion-operators) Pokud jeden z řazené kolekce členů je s možnou hodnotou Null řazené kolekce členů, jak je znázorněno v následujícím kódu:

[!code-csharp[NullableTupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

Implicitní převody řazené kolekce členů rovnosti provádí taky v každém členovi obou řazené kolekce členů. Mezi ně patří zdvižené převody, rozšiřující převody nebo jiných implicitní převody. Následující příklady ukazují, že celé číslo 2-řazené kolekce členů je možné charakterizovat dlouhý 2-řazené kolekce členů z důvodu implicitní převod z celého dlouhé:

[!code-csharp[SnippetMemberConversions](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Názvy členů řazené kolekce členů neúčastnit testování rovnosti. Ale pokud jeden z operandy je literál s explicitní názvy řazené kolekce členů, kompilátor vygeneruje upozornění CS8383 Pokud tyto názvy neshodují názvy jiných operand.
V případě, kde jsou oba operandy literály řazené kolekce členů je upozornění na pravý operand, jak je znázorněno v následujícím příkladu:

[!code-csharp[MemberNames](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

Nakonec řazených kolekcí členů může obsahovat vnořené řazené kolekce členů. Porovná rovnost řazené kolekce členů "obrazec" každý operand prostřednictvím vnořené řazených kolekcí členů jako v následujícím příkladu:

[!code-csharp[NestedTuples](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

## <a name="assignment-and-tuples"></a>Přiřazení a řazených kolekcí členů

Jazyk podporuje přiřazení mezi typy řazené kolekce členů, které mají stejný počet elementů, kde každý element pravé straně může být implicitně převedena na jeho odpovídající element na levé straně. Jiné převody nejsou považovány za přiřazení. Podívejme se na druhy přiřazení, které jsou povoleny mezi typy řazené kolekce členů.

Vezměte v úvahu tyto proměnné použít v následujících příkladech:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Variable creation")]

První dvě proměnné, `unnamed` a `anonymous` nemají sémantického názvy zadané pro elementy. Názvy polí jsou `Item1` a `Item2`.
Poslední dvě proměnné, `named` a `differentName` sémantického názvy zadané pro elementy. Tyto dvě řazené kolekce členů mít odlišné názvy pro elementy.

Všechny čtyři tyto řazené kolekce členů mají stejný počet elementů (označované jako 'mohutnost') a jsou identické typy těchto elementů. Proto všechny tyto přiřazení fungovat:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Všimněte si, že nejsou přiřazeny názvy řazené kolekce členů. Hodnoty elementů jsou přiřazeny následující pořadí prvků v řazené kolekci členů.

Řazené kolekce členů různé typy nebo počtem elementů nejsou přiřadit:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Řazené kolekce členů jako metodu návratové hodnoty

Jednou z nejběžnějších použití řazených kolekcí členů je jako návratová hodnota metody. Projděme jedním z příkladů. Vezměte v úvahu tuto metodu, která vypočítá směrodatnou odchylku sekvenci čísla:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Tyto příklady výpočetní směrodatná odchylka neopravené vzorku.
> Vzorec směrodatné odchylky vzorku opravené by rozdělení součet kvadratických odchylek od střední podle (N-1) namísto N, jako `Average` rozšíření metoda nepodporuje. Další informace o rozdílech mezi tyto vzorce pro směrodatnou odchylku najdete statistiky text.

Předchozí kód následuje učebnice vzorec směrodatné odchylky. Vyvolá správnou odpověď, ale je neefektivní implementace. Tato metoda vytvoří výčet sekvenci dvakrát: jednou k vytvoření průměr a jednou k vytvoření průměr druhou mocninu rozdíl průměru.
(Nezapomeňte, že dotazů LINQ vyhodnocují líné, tak výpočet rozdíl oproti střední a průměr těchto rozdílů je pouze jeden výčet.)

Neexistuje alternativní vzorec, která vypočítá směrodatnou odchylku pomocí pouze jeden výčet pořadí.  Tento výpočet vytvoří dvě hodnoty při výčtu sekvenci: součet všechny položky v pořadí a součet každá hodnota spolehlivosti:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Tato verze zobrazí sekvenci právě jednou. Ale není opakovaně použitelný kód. Jak můžete pokračovat v práci, zjistíte, že mnoho různých statistické výpočty používat počet položek v sekvenci, součet pořadí a součet kvadratických pořadí. Pojďme Refaktorovat tuto metodu a zápis nástroj metoda, která vytváří všechny tři tyto hodnoty. Všechny tři hodnoty mohou být vrácena jako řazené kolekce členů.

Umožňuje aktualizovat tuto metodu tak tři hodnoty počítaný během výčtu jsou uloženy v řazené kolekce členů. Tato verze vytvářející:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Visual Studio Refactoring podpora snadno rozbalte funkce pro základní statistiky do soukromá metoda. Toto vám `private static` metodu, která vrátí typ řazené kolekce členů s tři hodnoty `Sum`, `SumOfSquares`, a `Count`:

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
Jazyk umožňuje několik další možnosti, které můžete použít, pokud chcete, aby několik rychlé úpravy ručně. První, můžete použít `var` deklarace k chybě při inicializaci výsledek řazené kolekce členů z `ComputeSumAndSumOfSquares` volání metody. Můžete také vytvořit tři proměnné diskrétní uvnitř `ComputeSumAndSumOfSquares` metoda. Finální verzi je znázorněno v následujícím kódu:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Tento poslední verze slouží pro libovolné metody, která vyžaduje tyto tři hodnoty, nebo jakékoli některé z nich.

Jazyk podporuje další možnosti ve správě názvy elementů v těchto metod vrací řazené kolekce členů.

Můžete odebrat z návratovou hodnotu deklarace názvy polí a vrátit nepojmenované řazené kolekce členů:

```csharp
private static (double, double, int) ComputeSumAndSumOfSquares(IEnumerable<double> sequence)
{
    double sum = 0;
    double sumOfSquares = 0;
    int count = 0;

    foreach (var item in sequence)
    {
        count++;
        sum += item;
        sumOfSquares += item * item;
    }

    return (sum, sumOfSquares, count);
}
```

Pole tento řazené kolekce členů jsou pojmenované `Item1`, `Item2`, a `Item3`.
Doporučujeme zadat sémantického názvy elementů vrátila z metody řazené kolekce členů.

Jiné stylu, kde může být užitečné řazených kolekcí členů je při vytváření dotazů LINQ. Konečný výsledek předpokládané často obsahuje některé, ale ne všechny vlastnosti objektů vybrat.

Výsledky dotazu by tradičně projektu do pořadí objektů, které byly anonymního typu. Mnoho omezení, který zobrazí, primárně, protože anonymní typy nelze pojmenovat pohodlně v návratový typ pro metodu. Alternativy pomocí `object` nebo `dynamic` jako typ výsledku byly dodány s náklady na významně zvýšit výkon.

Vrácení pořadí řazené kolekce členů typ je snadné a názvy a typy elementy jsou k dispozici, v době kompilace a nástrojích IDE.
Představte si třeba aplikace ToDo. Můžete třeba definovat třídu podobný následujícímu představují jednu položku v seznamu úkolů:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Mobilní aplikace může podporovat aktuální položek ToDo compact formulář, který se zobrazí jenom název. Bude dotaz LINQ vytvořili projekci, obsahuje pouze ID a název. Metoda, která vrátí pořadí řazené kolekce členů dobře vyjadřoval tohoto návrhu:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> V jazyce C# 7.1 řazené kolekce členů projekce umožňují vytvořit pojmenovaný řazených kolekcí členů pomocí elementů, podobně jako u vlastnosti názvu v anonymní typy způsobem. Ve výše uvedeném kódu `select` příkaz v projekce dotazu vytvoří řazenou kolekci členů, která má elementy `ID` a `Title`.

Pojmenované řazené kolekce členů můžou být součástí podpis. Umožňuje kompilátor a nástroje pro IDE poskytují statické kontroluje, že výsledek používáte správně. Pojmenované řazené kolekce členů také přenáší informace statického typu, takže není nutné používat funkce nákladné běhu jako reflexe nebo dynamické vazby pro práci s výsledky.

## <a name="deconstruction"></a>Deconstruction

Můžete rozbalit všechny položky v řazené kolekce členů podle *deconstructing* řazené kolekce členů vrácená metodou. Existují tři různé přístupy k deconstructing řazené kolekce členů.  Nejprve je možné deklarovat explicitně typ každé pole v závorkách vytváření diskrétní proměnných pro jednotlivé elementy v řazené kolekci členů:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Můžete také deklarovat implicitně typovaná proměnných pro každé pole v řazené kolekce členů s použitím `var` – klíčové slovo mimo závorkách:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Je také možné použít `var` – klíčové slovo pomocí některého nebo všech deklarace proměnných v závorkách. 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Konkrétní typ mimo závorky, nelze použít, i když každé pole v řazené kolekci členů má stejný typ.

Můžete deconstruct řazené kolekce členů s existující deklarace také:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
>  Není možné kombinovat existující deklarace s deklaracemi v závorkách. Například následující nepovolené: `(var x, y) = MyMethod();`. To vytváří chyba CS8184, protože *x* je deklarovaná do závorek a *y* je dříve deklarované jinde.

### <a name="deconstructing-user-defined-types"></a>Deconstructing uživatelem definované typy

Jakýkoli typ řazené kolekce členů můžete deconstructed, jak je uvedeno výše. Je také snadno povolit deconstruction na libovolného typu uživatelem definované (třídy, struktury nebo i rozhraní).

Typ Autor můžete definovat jeden nebo více `Deconstruct` metody, které hodnoty přiřadit libovolný počet `out` představující datové prvky, které tvoří typ proměnné. Například následující `Person` definuje typ `Deconstruct` metoda, která deconstructs objekt osoba do elementů představující křestní jméno a příjmení:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

Metoda deconstruct umožňuje přiřazení z `Person` na dva řetězce, představující `FirstName` a `LastName` vlastnosti:

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Můžete povolit deconstruction i pro typy, které není vytváříte.
`Deconstruct` Metoda může být metody rozšíření, který rozbalí dat dostupný členům v objektu. V příkladu níže znázorňuje `Student` typ odvozený z `Person` typu a metody rozšíření, která deconstructs `Student` do tří proměnných, představující `FirstName`, `LastName`a `GPA`:

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

A `Student` objekt teď má dva přístupné `Deconstruct` metody: Metoda přípona deklarovaným pro `Student` typy a členem `Person` typu. Obě jsou v oboru a která umožňuje `Student` k být deconstructed do proměnné dva nebo tři.
Chcete-li přiřadit student tří proměnných, křestní jméno, poslední název a GPA se všechny vrátí. Pokud přiřadíte student dvě proměnné, vrátí se pouze křestní jméno a příjmení.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Je třeba pečlivě definování více `Deconstruct` metody ve třídě nebo hierarchie tříd. Více `Deconstruct` metody, které mají stejný počet `out` parametry může způsobit rychle nejednoznačnosti. Volající nemusí být možné snadno volání požadovanou `Deconstruct` metoda.

V tomto příkladu, existuje minimální pravděpodobnost pro nejednoznačné volání protože `Deconstruct` metodu pro `Person` má dva výstup parametrů a `Deconstruct` metodu pro `Student` má tři.

Operátory deconstruction neúčastnit testování rovnosti. Následující příklad generuje chyba kompilátoru CS0019:

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

`Deconstruct` Metoda může převést `Person` objekt `p` řazené kolekce členů obsahující dva řetězce, ale není použít v kontextu testování rovnosti.

## <a name="conclusion"></a>Závěr 

Nová podpora jazyka a knihovny s názvem řazených kolekcí členů je mnohem jednodušší pro práci s návrhy, které používají datové struktury, které uložit více elementů, ale nejsou definovány chování, stejně jako třídy a struktury. Je snadné a stručným použijte pro tyto typy řazených kolekcí členů. Získáte všechny výhody Kontrola statické typu, aniž by museli vytvářet typy pomocí více podrobné `class` nebo `struct` syntaxe. I tak se nejvíc hodí pro pomocné metody, které jsou `private`, nebo `internal`. Buď vytvořit uživatelem definované typy `class` nebo `struct` typy při veřejné metody vrátit hodnotu, která má více elementů.
