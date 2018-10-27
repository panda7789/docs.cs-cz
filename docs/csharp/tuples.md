---
title: Typy řazené kolekce členů – průvodce v C#
description: Další informace o typech pojmenované a nepojmenované řazené kolekce členů v C#
ms.date: 05/15/2018
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 572e926b6345fc27278f78d1faf2e3b27f017f2e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50186028"
---
# <a name="c-tuple-types"></a>Typy řazené kolekce členů v C# #

C# řazené kolekce členů jsou typy, které definujete pomocí jednoduché syntaxe. Mezi výhody patří jednodušší syntaxí, pravidla pro převody na základě čísla (označované jako Kardinalita) a typy prvků a konzistentní pravidla pro kopie, testování rovnosti a přiřazení. Jako kompromis řazených kolekcí členů nepodporuje některé objektově orientované idiomy přidružené dědičnosti. V části můžete získat přehled [řazenými kolekcemi členů v co je nového v jazyce C# 7.0](whats-new/csharp-7.md#tuples) článku.

V tomto článku se dozvíte jazyka pravidla řazených kolekcí členů v C# 7.0 a novějších verzích, různé způsoby použití je a počáteční pokyny pro práci s řazenými kolekcemi členů.

> [!NOTE]
> Vyžadovat nových funkcí řazených kolekcí členů <xref:System.ValueTuple> typy.
> Je nutné přidat balíček NuGet [ `System.ValueTuple` ](https://www.nuget.org/packages/System.ValueTuple/) aby bylo možné používat na platformách, které neobsahují typy.
>
> To se podobá další jazykové funkce, které využívají typy v rozhraní framework. Mezi příklady patří `async` a `await` spoléhat na `INotifyCompletion` rozhraní a LINQ spoléhat na `IEnumerable<T>`. Jak .NET se mění na další platformy, které jsou nezávislé, mechanismus doručování mění. Rozhraní .NET Framework nemusí vždy odeslání na stejném tempo jako kompilátor jazyka. Nové funkce jazyků využívají nové typy, typy nebudou mít k dispozici jako balíčků NuGet při dodávání funkcí jazyka. Tyto nové typy získat přidána do rozhraní API .NET Standard a dodávána jako součást rozhraní framework, odeberou se požadavek na balíček NuGet.

Začněme s důvody pro přidání nové podpory řazené kolekce členů. Metody vrátí jeden objekt. Řazené kolekce členů umožňují snadněji balíček více hodnot v tomto jednoho objektu.

Rozhraní .NET Framework již má obecný `Tuple` třídy. Tyto třídy, ale má dvě hlavní omezení. Za prvé `Tuple` třídy s názvem jejich vlastnosti `Item1`, `Item2`, a tak dále. Tyto názvy nesou žádné sémantické informace. Použití těchto `Tuple` typy neumožňuje komunikaci význam jednotlivých vlastností. Nové funkce jazyků umožňují deklarování a použití sémanticky smysluplné názvy prvků v řazené kolekce členů.

`Tuple` Třídy způsobit dopadům na výkon, protože jsou odkazové typy. Pomocí jednoho z `Tuple` typy znamená, že přidělování objektů. V horké cesty přidělování mnoha malých objektů může být měřitelný dopad na výkon vaší aplikace. Proto se využívá novou jazykovou podporu pro řazené kolekce členů `ValueTuple` struktury.

Aby se zabránilo tyto nedostatky, můžete vytvořit `class` nebo `struct` provádět několik elementů. Bohužel to je další práci za vás a skryje máte v úmyslu návrhu. Vytváření `struct` nebo `class` znamená, že definujete typ s daty a chování. V mnoha případech chcete jednoduše uložení více hodnot do jednoho objektu.

Funkce jazyka a `ValueTuple` obecné struktury vynutit pravidlo, že nemůžete přidat žádné chování (metody) pro tyto typy řazené kolekce členů.
Všechny `ValueTuple` typy jsou *proměnlivé struktury*. Každý člen pole je veřejné pole. Díky tomu je velmi jednoduché. Nicméně to znamená, že řazené kolekce členů by neměl být použít, kde je důležité neměnnosti.

Řazené kolekce členů jsou kontejnery obou data jednodušší a flexibilnější než `class` a `struct` typy. Podíváme se na tyto rozdíly.

## <a name="named-and-unnamed-tuples"></a>Pojmenované a nepojmenované řazené kolekce členů

`ValueTuple` Struktura obsahuje pole s názvem `Item1`, `Item2`, `Item3`, a tak dále, podobně jako vlastnosti definované v existujícím `Tuple` typy.
Tyto názvy jsou pouze názvy, můžete použít pro *nepojmenované řazených kolekcí členů*. Pokud nezadáte žádné pole alternativní názvy pro n-tice, co vytvoříte nepojmenované řazené kolekce členů:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Řazené kolekce členů v předchozím příkladu byl inicializován pomocí literálu konstanty a nebude mít názvy elementů vytvořit pomocí *řazené kolekce členů pole Název projekce* v jazyce C# 7.1.

Při inicializaci řazené kolekce členů, ale můžete použít nové funkce jazyků, které poskytnou lepší názvy k jednotlivým polím. Tím se vytvoří *s názvem řazené kolekce členů*.
Pojmenované řazených kolekcí členů, ještě elementů s názvem `Item1`, `Item2`, `Item3` a tak dále.
Ale mají také synonyma pro některý z těchto prvků, které mají s názvem.
Vytvořit pojmenovaný řazené kolekce členů tak, že zadáte názvy pro každý prvek. První způsob je zadat názvy jako součást inicializace řazené kolekce členů:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Named tuple")]

Tato synonyma jsou zpracovány v kompilátoru a jazyk tak, aby vám s názvem řazených kolekcí členů efektivně. Editory a integrovanými vývojovými prostředími můžete číst tyto sémantické názvy pomocí rozhraní Roslyn API. Prvky pojmenované řazené kolekce členů můžete odkazovat na tyto sémantické názvy kdekoli ve stejném sestavení. Kompilátor nahradí názvy, které jste definovali s `Item*` ekvivalenty při generování kompilovaný výstup. Kompilované Microsoft Intermediate Language (MSIL) nezahrnuje názvy jste dali tyto prvky.

Od verze C# 7.1, může být poskytnuta názvy polí pro řazené kolekce členů z proměnných, které slouží k inicializaci řazené kolekce členů. To se označuje jako  **[řazené kolekce členů projekce inicializátory](#tuple-projection-initializers)**. Následující kód vytvoří řazenou kolekci členů s názvem `accumulation` s prvky `count` (celé číslo), a `sum` (typ double).

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Kompilátor musí komunikovat tyto názvy, které jste vytvořili pro řazené kolekce členů, které jsou vráceny z veřejné metody nebo vlastnosti. V těchto případech kompilátor přidá <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> atributu v metodě. Tento atribut obsahuje <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> seznamu vlastností, které obsahují názvy na každý prvek v řazené kolekci členů.

> [!NOTE]
> Vývojářské nástroje, jako je Visual Studio také čtení těchto metadat a poskytují technologie IntelliSense a dalších funkcí pomocí názvů polí metadat.

Je důležité pochopit tyto základní principy nové řazených kolekcí členů a `ValueTuple` typ, chcete-li pochopit pravidla pro přiřazení s názvem řazené kolekce členů k sobě navzájem.

## <a name="tuple-projection-initializers"></a>Inicializátory projekce řazené kolekce členů

Inicializátory projekce řazené kolekce členů obecně fungovat pomocí názvů pole nebo proměnné z pravá strana výrazu inicializace řazené kolekce členů.
-Li zadána explicitní název, který má přednost před jakékoli předpokládané název. Například v následujícím inicializátoru, jsou prvky `explicitFieldOne` a `explicitFieldTwo`, nikoli `localVariableOne` a `localVariableTwo`:

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Pro všechna pole, pokud není poskytnut jasný název je použít implicitní název očekávaná. Není nutné zadat sémantické názvy, explicitně nebo implicitně. Následující inicializátor s názvy polí `Item1`, jehož hodnota je `42` a `stringContent`, jehož hodnota je "Odpověď na všechno, co":

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#MixedTuple "mixed tuple")]

Existují dvě podmínky. Pokud nejsou názvy polí Release candidate plánovaných na pole řazené kolekce členů:

1. Pokud název Release candidate je název vyhrazené řazené kolekce členů. Mezi příklady patří `Item3`, `ToString`. nebo `Rest`.
1. Pokud název Release candidate je duplicitní jiného názvu pole řazené kolekce členů, explicitní nebo implicitní.

Tyto podmínky-li předejít nejednoznačnosti. Tyto názvy by způsobit nejednoznačnost, pokud byly použity jako názvy polí pro pole řazená kolekce členů. Žádná z těchto podmínek způsobit chyby kompilace. Místo toho elementy bez předpokládané názvů nemají sémantické názvy plánovaných pro ně.  Následující příklady ukazují tyto podmínky:

[!code-csharp[Ambiguity](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Těmito situacemi nezpůsobí chyby kompilátoru, protože, která by byla k zásadní změně kódu napsané v jazyce C# 7.0, když řazené kolekce členů pole Název projekce nebyly k dispozici.

## <a name="equality-and-tuples"></a>Rovnost a řazené kolekce členů

Od verze C# 7.3, typy řazené kolekce členů podpory `==` a `!=` operátory. Tyto operátory pracují na základě porovnání každý člen levý argument pro každého člena pravý argument v pořadí. Tato porovnání zkrácenou. `==` Operátor zastaví jako jednu dvojici se nerovná vyhodnocování členů. `!=` Operátor zastaví ihned poté, co se rovná jednu dvojici vyhodnocování členů. Následující příklady kódu používají `==`, ale pravidla porovnání všech platí pro `!=`. Následující příklad kódu ukazuje porovnání rovnosti pro dvě dvojice celých čísel:

[!code-csharp[TupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#Equality "Testing tuples for equality")]

Existuje několik pravidel, která pohodlnější provádění testů rovnost řazené kolekce členů. Rovnost řazené kolekce členů provádí [zrušeno vs. převody](~/_csharplang/spec/conversions.md#lifted-conversion-operators) Pokud jeden ze záznamů je s možnou hodnotou Null řazené kolekce členů, jak je znázorněno v následujícím kódu:


[!code-csharp[NullableTupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

Rovnost řazené kolekce členů také provádí implicitní převody v každém členovi obou řazených kolekcí členů. Patří mezi ně zdvižené převody rozšiřující převody a jiných implicitních převodů. Následující příklady ukazují, že celé číslo 2-řazené kolekce členů je možné porovnat s dlouhou 2-řazené kolekce členů z důvodu implicitní převod z celého čísla na dlouhé:

[!code-csharp[SnippetMemberConversions](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Názvy členů řazené kolekce členů nejsou součástí testy pro rovnost. Ale pokud jeden z operandů je literál s explicitní názvy řazené kolekce členů, kompilátor vygeneruje upozornění CS8383 Pokud tyto názvy se neshodují s názvy je druhý operand.
V případě, pokud jsou oba operandy literálech řazené kolekce členů se upozornění na pravý operand, jak je znázorněno v následujícím příkladu:

[!code-csharp[MemberNames](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

Nakonec řazené kolekce členů může obsahovat vnořené řazené kolekce členů. Porovná rovnost řazené kolekce členů "tvar" operandem prostřednictvím vnořené řazených kolekcí členů, jako je znázorněno v následujícím příkladu:

[!code-csharp[NestedTuples](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

## <a name="assignment-and-tuples"></a>Přiřazení a řazené kolekce členů

Jazyk podporuje mezi typy řazené kolekce členů, které mají stejný počet prvků, kde každý prvek na pravé straně lze implicitně převést na odpovídající prvek levá strana příkazu přiřazení. Ostatní převody, které nejsou považované za pro přiřazení. Pojďme se podívat na typy přiřazení, které jsou povolené mezi typy řazené kolekce členů.

Vezměte v úvahu tyto proměnné, používat v následujících příkladech:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Variable creation")]

První dvě proměnné `unnamed` a `anonymous` nemají sémantické názvy, které jsou k dispozici pro elementy. Názvy polí jsou `Item1` a `Item2`.
Poslední dvě proměnné, `named` a `differentName` sémantické názvy pro elementy. Tyto dvě řazené kolekce členů mají různé názvy prvků.

Všechny čtyři tyto řazených kolekcí členů mají stejný počet prvků (dále jako "Kardinalita") a typy tyto prvky jsou identické. Proto všechny tato přiřazení práce:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Všimněte si, že nejsou přiřazeny názvy řazené kolekce členů. Hodnoty elementů jsou přiřazeny následující pořadí prvků řazené kolekce členů.

N-tice různé typy nebo počtem elementů nejsou přiřadit:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Řazené kolekce členů jako návratové hodnoty metod

Jedním z nejběžnějších používá pro řazené kolekce členů je jako návratovou hodnotu metody. Projděme si jedním z příkladů. Vezměte v úvahu tuto metodu, která vypočítá směrodatnou odchylku pro sekvenci čísel:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Tyto příklady výpočetní směrodatná odchylka neopraveno vzorku.
> Vzorec směrodatné odchylky opravený ukázka by rozdělit součet kvadratických odchylek od střední hodnoty podle (N-1) namísto N, jako `Average` metodu rozšíření. Statistiky textu najdete podrobné informace o rozdílech mezi tyto vzorce pro směrodatnou odchylku.

Předchozí kód se řídí učebnice vzorec směrodatné odchylky. Vytvoří správnou odpověď, ale je neefektivní implementace. Tato metoda vytvoří výčet sekvence dvakrát: jednou k vytvoření průměr a jednou pro vytvoření průměr druhou mocninu rozdíl průměr.
(Mějte na paměti, že LINQ dotazů jsou vyhodnocovány laxně, tak výpočet rozdíl oproti průměr a průměr těchto rozdílů je pouze jeden výčet.)

Existuje alternativní vzorec, který vypočítá směrodatnou odchylku pomocí pouze jeden výčet pořadí.  Tento výpočet vytváří dvě hodnoty při výčtu sekvence: součet všech položek v sekvenci a součet jednotlivých hodnot spolehlivosti:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Tato verze vytvoří výčet sekvence přesně jednou. Ale to není opakovaně použitelný kód. Jak budete pokračovat v práci, zjistíte, že mnoho různých statistické výpočty pomocí počet položek v sekvenci, součet pořadí a součet druhých mocnin pořadí. Pojďme Refaktorovat tuto metodu a napíše metoda nástroj, který vytváří všechny tři z těchto hodnot. Všechny tři hodnoty mohou být vráceny jako řazené kolekce členů.

Umožňuje aktualizovat tuto metodu tak tři hodnoty vypočítané během výčtu jsou uloženy v řazené kolekce členů. Který vytváří tato verze:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Podpora Refactoring sady Visual Studio umožňuje snadno extrahovat funkci pro základní statistiky do privátní metodu. Který vám `private static` metodu, která vrací typ řazené kolekce členů s použitím tří hodnot `Sum`, `SumOfSquares`, a `Count`:

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
Jazyk umožňuje několik další možnosti, které můžete použít, pokud chcete, aby několik rychlé úpravy ručně. Nejprve, můžete použít `var` prohlášení k inicializaci výsledkem řazené kolekce členů `ComputeSumAndSumOfSquares` volání metody. Můžete také vytvořit tři samostatná proměnných uvnitř `ComputeSumAndSumOfSquares` metody. Konečná verze můžete vidět v následujícím kódu:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Pro jakoukoli metodu, která potřebuje tyto tři hodnoty nebo jakékoli některé z nich je možné tuto poslední verzi.

Jazyk podporuje další možnosti při správě názvy prvků v těchto metodách, které vracejí řazené kolekce členů.

Můžete odebrat názvy polí z deklarace návratovou hodnotu a vrátí nepojmenované řazené kolekce členů:

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

Pole této řazené kolekce členů jsou pojmenovány `Item1`, `Item2`, a `Item3`.
Doporučuje se, že zadáte sémantické názvy elementů řazené kolekce členů vracené z metod.

Jiné idiom, kde může být užitečné řazené kolekce členů je při vytváření dotazů LINQ. Konečný výsledek předpokládané často obsahuje některé, ale ne všechny vlastnosti objektů výběru.

Výsledky dotazu by tradičně projektu na sekvenci objektů, které byly anonymního typu. Který zobrazí mnoho omezení, především proto anonymní typy nelze jednoduše pojmenované v návratovém typu pro metodu. Alternativy pomocí `object` nebo `dynamic` jako typ výsledku dodán jako součást výkonu náklady.

Vrací posloupnost řazené kolekce členů typu je snadné a názvy a typy elementů jsou k dispozici, v době kompilace a integrovaného vývojového prostředí pomocí nástrojů.
Zvažte například aplikaci seznamu úkolů. Můžete třeba definovat třídu podobný následujícímu pro reprezentaci jedna položka v seznamu úkolů:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Mobilní aplikace může podporovat kompaktní podobě aktuální položky seznamu úkolů, který zobrazuje pouze název. Že dotazů LINQ s žádným projekci, která obsahuje pouze ID a název. Metodu, která vrátí sekvenci řazených kolekcí členů vyjadřuje tento návrh kontejneru:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> V jazyce C# 7.1 řazené kolekce členů projekce umožňují vytvářet pojmenované řazených kolekcí členů, pomocí elementů, názvy vlastností anonymních typů podobným způsobem. Ve výše uvedeném kódu `select` příkaz v projekci dotaz vytvoří řazenou kolekci členů, který má prvky `ID` a `Title`.

Pojmenované řazené kolekce členů může být součást podpisu. Umožňuje kompilátoru a integrovaného vývojového prostředí nástroje poskytují statické kontroluje se, že výsledek používáte správně. Pojmenované řazené kolekce členů také přenáší informace statického typu, takže není nutné používat drahé běhu funkcí, jako je odraz nebo dynamické vazby pro práci s výsledky.

## <a name="deconstruction"></a>Dekonstrukce

Můžete rozbalit všechny položky v řazené kolekce členů podle *dekonstrukce* řazené kolekce členů, vrací metoda. Existují tři různé přístupy k dekonstrukce řazených kolekcí členů.  Nejprve lze explicitně deklarovat typ každého pole uvnitř závorek vytváření diskrétního proměnných pro každý prvek v řazené kolekci členů:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Implicitně typované proměnné pro každé pole v řazené kolekci členů můžete také deklarovat s použitím `var` – klíčové slovo mimo závorek:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Je také možné použít `var` – klíčové slovo se některé nebo všechny deklarace proměnných v závorkách. 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Konkrétní typ mimo závorky, nelze použít, i v případě každé pole v n-tice stejného typu.

Možné dekonstruovat řazené kolekce členů s také existující deklarace:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
>  Nejde kombinovat existující deklarace s deklaracemi v závorkách. Například následující není povoleno: `(var x, y) = MyMethod();`. Výsledkem chyba CS8184, protože *x* je deklarována uvnitř závorek a *y* se dřív deklaroval jinde.

### <a name="deconstructing-user-defined-types"></a>Dekonstrukce uživatelem definované typy

Jakýkoli typ řazené kolekce členů je možné dekonstruovat. jak je znázorněno výše. Je také snadné povolení dekonstrukce na libovolný typ definovaný uživatelem (třídy, struktury nebo dokonce rozhraní).

Autor typu můžete definovat jeden nebo více `Deconstruct` metody, které přiřazují hodnoty do libovolného počtu `out` představující datové prvky, které tvoří typ proměnné. Například následující `Person` definuje typ `Deconstruct` metodu, která deconstructs osoba do prvků, která představuje křestní jméno a příjmení:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

Metoda deconstruct umožňuje přiřazení `Person` na dva řetězce představující `FirstName` a `LastName` vlastnosti:

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Můžete povolit dekonstrukce i pro typy, které nelze vytvářet.
`Deconstruct` Metoda může být metodu rozšíření, který rozbalí dostupné datové členy objektu. V příkladu níže ukazuje `Student` typu odvozeného z `Person` typ a metodu rozšíření, která deconstructs `Student` do tří proměnných, představující `FirstName`, `LastName`a `GPA`:

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

A `Student` objektu má teď dostupné dvě `Deconstruct` metody: metodu rozšíření deklarovat pro `Student` typů a členů z `Person` typu. Obě jsou v oboru a, která umožňuje `Student` k možné dekonstruovat na proměnné dvě nebo tři.
Pokud přiřadíte student tří proměnných, křestní jméno, poslední název a GPA jsou všechny vrácené. Pokud přiřadíte student dvě proměnné, budou vráceny pouze křestní jméno a příjmení.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Měli byste být opatrní definování více `Deconstruct` metody ve třídě nebo hierarchie tříd. Více `Deconstruct` metody, které mají stejný počet `out` parametry rychle mohou způsobit nejednoznačnost. Volající není možné snadno volání požadovaný `Deconstruct` metody.

V tomto příkladu, existuje minimální pravděpodobnost pro nejednoznačné volání protože `Deconstruct` metodu `Person` má dvě výstupních parametrů a `Deconstruct` metodu pro `Student` má tři.

Operátory dekonstrukce nejsou součástí testování rovnosti. Následující příklad vygeneruje Chyba kompilátoru CS0019:

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

`Deconstruct` Metodu se nepovedlo převést `Person` objektu `p` pro n-tici obsahující dva řetězce, ale se nedá použít v kontextu rovnosti testy.

## <a name="conclusion"></a>Závěr 

Novou podporu jazyka a knihovny pro pojmenované řazených kolekcí členů výrazně usnadňuje práci s návrhy, které používají datové struktury, ukládání více prvků, které nedefinují chování, stejně jako třídy a struktury. Je snadné a stručné použijte pro tyto typy řazené kolekce členů. Získáte všechny výhody statický typ kontroly, aniž byste museli vytváření typů pomocí více podrobné `class` nebo `struct` syntaxe. I tak jsou nejvhodnější pro pomocné metody, které jsou `private`, nebo `internal`. Vytvoření uživatelem definovaných typů, buď `class` nebo `struct` zadává při veřejné metody vrací hodnotu, která má více elementů.
