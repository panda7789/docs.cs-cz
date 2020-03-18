---
title: Typy n-tice – průvodce C#
description: 'Informace o nepojmenovaných a pojmenovaných typech řazené kolekce členů v C #'
ms.date: 05/15/2018
ms.technology: csharp-fundamentals
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 9ce9e1d4395d1a75f36004384ec215c615cd9802
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156906"
---
# <a name="c-tuple-types"></a>C# řazené kolekce členů typy

Kolekce členů C# jsou typy, které definujete pomocí zjednodušené syntaxe. Mezi výhody patří jednodušší syntaxe, pravidla pro převody na základě čísla (označované jako mohutnost) a typy prvků a konzistentní pravidla pro kopie, testy rovnosti a přiřazení. Jako kompromis n-tic nepodporují některé objektově orientované idiomy spojené s dědičností. Přehled můžete získat v části [n-tic v článku Co je nového v c# 7.0.](whats-new/csharp-7.md#tuples)

V tomto článku se dozvíte jazyková pravidla, kterými se řídí řazené kolekce členů v jazyce C# 7.0 a novější verze, různé způsoby jejich použití a počáteční pokyny pro práci s řazenými kolekcemi členů.

> [!NOTE]
> Nové funkce řazené kolekce členů vyžadují <xref:System.ValueTuple> typy.
> Je nutné přidat Balíček [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) NuGet, aby bylo možné jej použít na platformách, které neobsahují typy.
>
> To je podobné jako jiné funkce jazyka, které spoléhají na typy dodané v rámci. Příklady `async` zahrnují `await` a spoléhání se na `INotifyCompletion` rozhraní `IEnumerable<T>`a LINQ spoléhání se na . Mechanismus doručování se však mění jako .NET je stále více nezávislé na platformě. Rozhraní .NET Framework nemusí být vždy dodáváno se stejnou kadenci jako kompilátor jazyka. Když nové funkce jazyka spoléhají na nové typy, tyto typy budou k dispozici jako balíčky NuGet při odeslání funkcí jazyka. Jako tyto nové typy získat přidány do rozhraní .NET Standard API a dodáno jako součást rámce, požadavek balíček NuGet budou odebrány.

Začněme s důvody pro přidání nové podpory n-tice. Metody vrátí jeden objekt. Řazené kolekce členů umožňují snadněji zabalit více hodnot v tomto jednom objektu.

Rozhraní .NET Framework `Tuple` již má obecné třídy. Tyto třídy však měly dvě hlavní omezení. Pro jednoho `Tuple` třídy s `Item1` `Item2`názvem jejich vlastnosti , a tak dále. Tato jména nenesou žádné sémantické informace. Použití `Tuple` těchto typů neumožňuje komunikaci význam u každé z vlastností. Nové funkce jazyka umožňují deklarovat a používat sémanticky smysluplné názvy prvků v n-tice.

Třídy `Tuple` způsobit další obavy o výkon, protože jsou typy odkazů. Použití jednoho `Tuple` z typů znamená alokace objektů. Na horké cesty přidělení mnoho malých objektů může mít měřitelný dopad na výkon vaší aplikace. Proto jazyková podpora pro řazené kolekce členů využívá nové `ValueTuple` struktury.

Chcete-li se těmto nedostatkům `class` vyhnout, můžete vytvořit a nebo a `struct` pro přenášení více prvků. Bohužel, to je více práce pro vás, a to zakrývá váš záměr návrhu. Vytvoření `struct` nebo `class` znamená, že definujete typ s daty i chování. Mnohokrát jednoduše chcete uložit více hodnot v jednom objektu.

Funkce jazyka a `ValueTuple` obecné struktury vynucují pravidlo, že nelze přidat žádné chování (metody) do těchto typů řazené kolekce členů.
Všechny `ValueTuple` typy jsou *proměnlivé struktury*. Každé členské pole je veřejné pole. To je dělá velmi lehkými. To však znamená, že n-tic by neměly být používány tam, kde je důležitá neměnnost.

Řazené kolekce členů jsou `class` jednodušší `struct` a flexibilnější kontejnery dat než typy. Pojďme prozkoumat tyto rozdíly.

## <a name="named-and-unnamed-tuples"></a>Pojmenované a nepojmenované řazené kolekce členů

`ValueTuple` Struktura má pole `Item1`s `Item2` `Item3`názvem , , a tak dále, `Tuple` podobná vlastnostem definovaným v existujících typech.
Tyto názvy jsou pouze názvy, které můžete použít pro *nepojmenované řazené kolekce členů*. Pokud nezadáte žádné alternativní názvy polí pro řazenou kolekce členů, vytvořili jste nepojmenovanou řazenou n-tice:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Řazená kolekce členů v předchozím příkladu byla inicializována pomocí literálových konstant a nebude mít názvy prvků vytvořené pomocí *projekce názvů polí řazené kolekce členů* v c# 7.1.

Však při inicializaci řazené kolekce členů, můžete použít nové funkce jazyka, které poskytují lepší názvy každé pole. Tím se vytvoří *pojmenovaná řazená kolekce členů*.
Pojmenované řazené `Item1`kolekce `Item2` `Item3` členů mají stále prvky s názvem , a tak dále.
Ale mají také synonyma pro některý z těchto prvků, které jste pojmenovali.
Pojmenovanou řazenou řazenou kolekce členů vytvoříte zadáním názvů pro každý prvek. Jedním ze způsobů je zadat názvy jako součást inicializace řazené kolekce členů:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/program.cs#02_NamedTuple "Named tuple")]

Tato synonyma jsou zpracovány kompilátoru a jazyk, takže můžete efektivně používat pojmenované řazené kolekce členů. IDE a editory můžete číst tyto sémantické názvy pomocí roslyn rozhraní API. Můžete odkazovat na prvky pojmenované řazené kolekce členů podle těchto sémantických názvů kdekoli ve stejném sestavení. Kompilátor nahradí názvy, které `Item*` jste definovali, ekvivalenty při generování kompilovaného výstupu. Kompilovaný microsoft intermediate language (MSIL) neobsahuje názvy, které jste zadali tyto prvky.

Počínaje C# 7.1, názvy polí pro řazenou kolekce členů mohou být poskytnuty z proměnných použitých k inicializaci n-tice. To se označuje jako **[inicializátory projekce řazené kolekce členů](#tuple-projection-initializers)**. Následující kód vytvoří řazenou `count` n-tice s `sum` názvem `accumulation` s prvky (celé číslo) a (double).

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Kompilátor musí sdělit ty názvy, které jste vytvořili pro řazené kolekce členů, které jsou vráceny z veřejných metod nebo vlastností. V těchto případech kompilátor <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> přidá atribut na metodu. Tento atribut <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> obsahuje vlastnost list, která obsahuje názvy dané pro každý z prvků v řazené kolekce členů.

> [!NOTE]
> Vývojové nástroje, jako je například Visual Studio, také číst tato metadata a poskytovat IntelliSense a další funkce pomocí názvů polí metadat.

Je důležité pochopit tyto základní základy nové řazené kolekce členů a `ValueTuple` typu, aby bylo možné pochopit pravidla pro přiřazení pojmenované řazené kolekce členů k sobě navzájem.

## <a name="tuple-projection-initializers"></a>Inicializátory projekce n-tuple

Inicializátory projekce řazené kolekce členů obecně fungují pomocí názvů proměnných nebo polí z pravé strany inicializačního příkazu řazené kolekce členů.
Pokud je uveden explicitní název, který má přednost před libovolným promítaným názvem. Například v následujícím `explicitFieldOne` inicializátoru `explicitFieldTwo`jsou `localVariableOne` `localVariableTwo`prvky a , not a :

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Pro každé pole, kde není poskytnut explicitní název, je promítnut příslušný implicitní název. Neexistuje žádný požadavek na poskytnutí sémantických názvů, explicitně nebo implicitně. Následující inicializátor `Item1`má názvy polí , jehož hodnota je `42` a `stringContent`, jehož hodnota je "Odpověď na všechno":

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/program.cs#MixedTuple "mixed tuple")]

Existují dvě podmínky, kde nejsou názvy kandidátských polí promítnuty do pole n-tice:

1. Pokud je název kandidáta vyhrazené řazené kolekce členů. Příklady `Item3`zahrnují `ToString`, `Rest`, nebo .
1. Pokud je název kandidáta duplikátem jiného názvu pole n-tice, explicitní nebo implicitní.

Tyto podmínky se vyhýbají nejednoznačnosti. Tyto názvy by způsobit nejednoznačnost, pokud byly použity jako názvy polí pro pole v n-tice. Ani jedna z těchto podmínek způsobit chyby v době kompilace. Místo toho prvky bez promítnuté názvy nemají sémantické názvy promítnuté pro ně.  Následující příklady ukazují tyto podmínky:

[!code-csharp-interactive[Ambiguity](../../samples/snippets/csharp/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Tyto situace nezpůsobí chyby kompilátoru, protože to by byla narušující změna pro kód napsaný s C# 7.0, kdy nebyly k dispozici projekce názvů polí řazené kolekce členů.

## <a name="equality-and-tuples"></a>Rovnost a řazené kolekce členů

Počínaje C# 7.3, řazená `!=` kolekce členů podporuje a operátory. `==` Tyto operátory pracovat porovnáním každý člen levé argument u každého člena pravé argument v pořadí. Tato srovnání zkrat. Přestanou hodnotit členy, jakmile jeden pár není stejný. Následující příklady kódu `==`používají , ale všechna `!=`pravidla porovnání platí pro . Následující příklad kódu ukazuje porovnání rovnosti pro dva páry celých čísel:

[!code-csharp-interactive[TupleEquality](../../samples/snippets/csharp/tuples/program.cs#Equality "Testing tuples for equality")]

Existuje několik pravidel, které zvýhodní testy rovnosti řazené kolekce členů. Rovnost řazené kolekce členů provede [zrušené převody,](~/_csharplang/spec/conversions.md#lifted-conversion-operators) pokud jeden z n-tic je nula n-tice, jak je znázorněno v následujícím kódu:

[!code-csharp-interactive[NullableTupleEquality](../../samples/snippets/csharp/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

N-tice rovnost také provádí implicitní převody na každý člen obou řazených kolekcí členů. Patří mezi ně zrušené převody, rozšiřující převody nebo jiné implicitní převody. Následující příklady ukazují, že celočíselné 2 řazené kolekce členů lze porovnat s dlouhou 2 řazenou n-tice z důvodu implicitní převod z celé číslo na dlouhé:

[!code-csharp-interactive[SnippetMemberConversions](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Názvy členů řazené kolekce členů neúčastní testů rovnosti. Však pokud jeden z operands je n-tice literálu s explicitní názvy, kompilátor generuje upozornění CS8383, pokud tyto názvy neodpovídají názvy jiného operandu.
V případě, že oba operandy jsou n-tice literály, upozornění je na pravé operand, jak je znázorněno v následujícím příkladu:

[!code-csharp-interactive[MemberNames](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

Nakonec n-tic může obsahovat vnořené řazené kolekce členů. N-tice rovnost porovnává "tvar" každého operandu prostřednictvím vnořené řazené kolekce členů, jak je znázorněno v následujícím příkladu:

[!code-csharp-interactive[NestedTuples](../../samples/snippets/csharp/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

Je chyba čas kompilace porovnat dva řazené kolekce členů pro rovnost (nebo nerovnost), pokud mají různé tvary. Kompilátor se nepokusí o dekonstrukci vnořených řazených kolekcí členů za účelem jejich porovnání.

## <a name="assignment-and-tuples"></a>Přiřazení a řazené kolekce členů

Jazyk podporuje přiřazení mezi typy řazené kolekce členů, které mají stejný počet prvků, kde každý prvek na pravé straně lze implicitně převést na odpovídající prvek na levé straně. U ostatních konverzí se u přiřazení neberou v úvahu. Je chyba čas kompilace přiřadit jednu řazenou kolekce členů do jiného, pokud mají různé tvary. Kompilátor se nepokusí o dekonstrukci vnořených řazených kolekcí členů, aby je mohl přiřadit.
Podívejme se na druhy přiřazení, které jsou povoleny mezi typy řazených kolekce členů.

Zvažte tyto proměnné použité v následujících příkladech:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/program.cs#03_VariableCreation "Variable creation")]

První dvě proměnné `unnamed` a `anonymous` nemají sémantické názvy k dispozici pro prvky. Názvy polí `Item1` `Item2`jsou a .
Poslední dvě proměnné `named` a `differentName` mají sémantické názvy pro prvky. Tyto dvě řazené kolekce členů mají různé názvy prvků.

Všechny čtyři tyto řazené kolekce členů mají stejný počet prvků (označované jako "mohutnost") a typy těchto prvků jsou identické. Proto všechny tyto úkoly práce:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Všimněte si, že názvy řazené kolekce členů nejsou přiřazeny. Hodnoty prvků jsou přiřazeny podle pořadí prvků v řazené kolekce členů.

Řazené kolekce členů různých typů nebo počty prvků nelze přiřadit:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Řazené kolekce členů jako vrácené hodnoty metody

Jedním z nejběžnějších použití pro řazené kolekce členů je jako vrácená hodnota metody. Projděme si jeden příklad. Zvažte tuto metodu, která vypočítá směrodatnou odchylku pro posloupnost čísel:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Tyto příklady vypočítat nekorigované vzorkovací směrodatná odchylka.
> Korigovaný vzorec směrodatné odchylky vzorku by vydělil součet kvadratických rozdílů `Average` od střední částky (N-1) namísto N, jako to dělá metoda rozšíření. Další podrobnosti o rozdílech mezi těmito vzorci pro směrodatnou odchylku naleznete v textu statistiky.

Předchozí kód se řídí učebnicovým vzorcem pro směrodatnou odchylku. Vytváří správnou odpověď, ale je to neefektivní implementace. Tato metoda vyjmenovává sekvenci dvakrát: Jednou k vytvoření průměru a jednou k vytvoření průměru druhé mocniny rozdílu průměru.
(Nezapomeňte, že dotazy LINQ jsou vyhodnocovány líně, takže výpočet rozdílů od střední a průměr těchto rozdílů činí pouze jeden výčet.)

Existuje alternativní vzorec, který vypočítá směrodatnou odchylku pomocí pouze jednoho výčtu sekvence.  Tento výpočt vytváří dvě hodnoty, jak se vytvoří sekvence: součet všech položek v sekvenci a součet každé hodnoty na druhou:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Tato verze vyjmenovává sekvenci přesně jednou. Ale není to opakovaně použitelný kód. Jak budete pokračovat v práci, zjistíte, že mnoho různých statistických výpočtů používá počet položek v sekvenci, součet sekvence a součet čtverců sekvence. Pojďme refaktorovat tuto metodu a napsat metodu nástroje, která vytváří všechny tři tyto hodnoty. Všechny tři hodnoty mohou být vráceny jako řazené kolekce členů.

Pojďme aktualizovat tuto metodu tak, aby tři hodnoty vypočítané během výčtu jsou uloženy v n-tice. To vytváří tuto verzi:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Podpora refaktoringu sady Visual Studio usnadňuje extrahování funkcí základních statistik do soukromé metody. To vám `private static` dává metodu, která vrací typ `Sum`řazené kolekce členů se třemi hodnotami , `SumOfSquares`a `Count`:

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]

Jazyk umožňuje několik dalších možností, které můžete použít, pokud chcete provést několik rychlých úprav ručně. Nejprve můžete použít `var` deklaraci k inicializaci `ComputeSumAndSumOfSquares` výsledku řazené kolekce členů z volání metody. Můžete také vytvořit tři diskrétní proměnné `ComputeSumAndSumOfSquares` uvnitř metody. Konečná verze je uvedena v následujícím kódu:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Tato konečná verze může být použita pro libovolnou metodu, která potřebuje tyto tři hodnoty nebo libovolnou jejich podmnožinu.

Jazyk podporuje další možnosti při správě názvy prvků v těchto metodách řazené kolekce členů.

Názvy polí můžete odebrat z deklarace vrácené hodnoty a vrátit nepojmenovanou řazenou n-tuto položku:

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

Pole této n-tice `Item1` `Item2`jsou `Item3`pojmenovány , a .
Doporučujeme zadat sémantické názvy prvků řazených kolekcí členů vrácených z metod.

Další idiom, kde n-tic může být užitečné je při vytváření linq dotazy. Konečný promítaný výsledek často obsahuje některé, ale ne všechny vlastnosti vybraných objektů.

Výsledky dotazu byste tradičně promítali do posloupnosti objektů, které byly anonymním typem. To představuje mnoho omezení, především proto, že anonymní typy nelze pohodlně pojmenovat v návratovém typu pro metodu. Alternativy, `object` `dynamic` které používají nebo jako typ výsledku, byly se značnými náklady na výkon.

Vrácení posloupnost řazené kolekce členů typu je snadné a názvy a typy prvků jsou k dispozici v době kompilace a prostřednictvím nástrojů IDE.
Zvažte například aplikaci ToDo. Můžete definovat třídu podobnou následující, která představuje jednu položku v seznamu úkolů:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Mobilní aplikace mohou podporovat kompaktní formu aktuálních položek todo, která zobrazuje pouze název. Tento dotaz LINQ by projekce, která obsahuje pouze ID a název. Metoda, která vrací posloupnost n-tic vyjadřuje, že návrh dobře:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> V C# 7.1 n-tice projekce umožňují vytvořit pojmenované řazené kolekce členů pomocí prvků, podobným způsobem jako pojmenování vlastností v anonymní typy. Ve výše uvedeném `select` kódu příkaz v projekci `ID` dotazu vytvoří řazenou n-tice, která má prvky a `Title`.

Pojmenované řazené kolekce členů mohou být součástí podpisu. Umožňuje kompilátoru a IDE nástroje poskytují statické kontroly, které používáte výsledek správně. Pojmenovaná řazená kolekce členů také nese informace statického typu, takže není nutné používat nákladné funkce běhu, jako je reflexe nebo dynamická vazba pro práci s výsledky.

## <a name="deconstruction"></a>Dekonstrukce

Můžete zrušit balíček všechny položky v řazené kolekce členů *deconstructing* řazené kolekce členů vrácené metodou. Existují tři různé přístupy k deconstructing řazené kolekce členů.  Nejprve můžete explicitně deklarovat typ každého pole uvnitř závorek a vytvořit diskrétní proměnné pro každý z prvků v řazené kolekce členů:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Můžete také deklarovat implicitně zadané proměnné pro každé `var` pole v n-tice pomocí klíčového slova mimo závorky:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Je také legální použít `var` klíčové slovo s libovolnou nebo všechny deklarace proměnných uvnitř závorek.

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Nelze použít určitý typ mimo závorky, i v případě, že každé pole v n-tice má stejný typ.

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
> Existující deklarace nelze kombinovat s deklaracemi uvnitř závorek. Například následující není povoleno: `(var x, y) = MyMethod();`. To způsobí chybu CS8184, protože *x* je deklarována uvnitř závorek a *y* je dříve deklarována jinde.

### <a name="deconstructing-user-defined-types"></a>Dekonstrukce uživatelem definovaných typů

Libovolný typ řazené kolekce členů lze dekonstruovat, jak je uvedeno výše. Je také snadné povolit dekonstrukci na libovolném uživatelem definovaném typu (třídy, struktury nebo dokonce rozhraní).

Autor typu můžete definovat `Deconstruct` jednu nebo více metod, které přiřazují hodnoty libovolný počet proměnných `out` představujících datové prvky, které tvoří typ. Například následující `Person` typ definuje `Deconstruct` metodu, která dekonstruuje objekt osoby do prvků představujících křestní jméno a příjmení:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

Metoda deconstruct umožňuje přiřazení `Person` od a do dvou `FirstName` `LastName` řetězců, představující vlastnosti a:

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Dekonstrukci můžete povolit i u typů, které jste nevytvořili.
Metoda `Deconstruct` může být metoda rozšíření, která unpackages přístupné datové členy objektu. Následující příklad ukazuje `Student` typ odvozený `Person` od typu a metodu rozšíření, `Student` která dekonstruuje `LastName`do tří `GPA`proměnných představujících `FirstName`, , a :

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

Objekt `Student` má nyní `Deconstruct` dvě přístupné metody: `Student` metoda rozšíření deklarovaná pro typy a člen `Person` typu. Oba jsou v oboru a `Student` to umožňuje dekonstruovat buď dvě proměnné nebo tři.
Pokud studenta přiřadíte ke třem proměnným, vrátí se křestní jméno, příjmení a gpa. Pokud studenta přiřadíte ke dvěma proměnným, bude vráceno pouze křestní jméno a příjmení.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Měli byste být opatrní `Deconstruct` definování více metod ve třídě nebo hierarchii třídy. Více `Deconstruct` metod, které mají `out` stejný počet parametrů může rychle způsobit nejasnosti. Volající nemusí být schopni snadno volat `Deconstruct` požadovanou metodu.

V tomto příkladu je minimální šance pro `Deconstruct` nejednoznačné volání, protože metoda pro `Person` má dva výstupní parametry a `Deconstruct` metoda pro `Student` má tři.

Dekonstrukční operátoři se nepodílejí na testování rovnosti. Následující příklad generuje chybu kompilátoru CS0019:

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

Metoda `Deconstruct` může převést `p` objekt na `Person` řazenou kolekce členů obsahující dva řetězce, ale není použitelná v kontextu testů rovnosti.

## <a name="tuples-as-out-parameters"></a>Řazené kolekce členů jako out parametry

Řazené kolekce členů lze použít jako out parametry *samy*. Nezaměňovat s jakoukoli nejednoznačností, která byla zmíněna v sekci [Deconstruction.](#deconstruction) Při volání metody stačí popsat tvar n-tice:

[!code-csharp[TuplesAsOutParameters](~/samples/snippets/csharp/tuples/program.cs#01_TupleAsOutVariable "Tuples as out parameters")]

Případně můžete použít [_nepojmenovanou_](#named-and-unnamed-tuples) řazenou n-tice a odkazovat na její pole jako `Item1` a `Item2`:

```csharp
dict.TryGetValue(2, out (int, string) pair);
// ...
Console.WriteLine($"{pair.Item1}: {pair.Item2}");
```

## <a name="conclusion"></a>Závěr

Nová podpora jazyka a knihovny pro pojmenované řazené kolekce členů usnadňuje práci s návrhy, které používají datové struktury, které ukládají více prvků, ale nedefinují chování, jako to dělají třídy a struktury. Je snadné a stručné použití řazených kolekcí členů pro tyto typy. Získáte všechny výhody statické kontroly typů, aniž byste museli vytvářet `class` typy `struct` pomocí podrobnější nebo syntaxe. I tak jsou nejužitečnější pro `private`metody `internal`užitkovosti, které jsou nebo . Vytvořte uživatelem definované `class` `struct` typy, nebo typy, pokud veřejné metody vrátí hodnotu, která má více prvků.
