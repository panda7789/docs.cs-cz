---
title: Typy řazené kolekce členů – Průvodce C#
description: 'Seznamte se s nepojmenovanými a pojmenovanými typy řazené kolekce členů v jazyce C #'
ms.date: 05/15/2018
ms.technology: csharp-fundamentals
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 0fb6f043857a9932b7a86f773cce812e0fd49dcb
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051854"
---
# <a name="c-tuple-types"></a>Typy řazené kolekce členů jazyka C#

Řazené kolekce členů jazyka C# jsou typy, které definujete pomocí prosté syntaxe. Výhody zahrnují jednodušší syntaxi, pravidla pro převody na základě počtu (označovaného jako mohutnost) a typy prvků a konzistentní pravidla pro kopie, testy rovnosti a přiřazení. V rámci kompromisů nepodporují řazené kolekce členů některé objekty orientované na objekt idiomy přidružené k dědičnosti. Přehled v části o [řazených kolekcích členů najdete v článku Co je nového v jazyce C# 7,0](whats-new/csharp-7.md#tuples) .

V tomto článku se naučíte jazykové pravidla upravující řazené kolekce členů v C# 7,0 a novějších verzích, různých způsobech jejich použití a úvodní doprovodné materiály k práci s řazenými kolekcemi členů.

> [!NOTE]
> Nové funkce řazené kolekce členů vyžadují <xref:System.ValueTuple> typy.
> Je nutné přidat balíček NuGet, [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) aby jej bylo možné použít na platformách, které neobsahují tyto typy.
>
> To je podobné jako u jiných funkcí jazyka, které závisí na typech dodaných v rámci rozhraní. Příklady zahrnují `async` a `await` spoléhají na `INotifyCompletion` rozhraní a LINQ spoléhají na `IEnumerable<T>` . Mechanismus doručování se ale mění, protože .NET se stane nezávisle na platformě. .NET Framework nemusí vždy dodávat do stejného tempo jako kompilátor jazyka. Když nové funkce jazyka spoléhají na nové typy, budou tyto typy k dispozici jako balíčky NuGet, když se funkce jazyka dodávají. Jelikož se tyto nové typy přidají do rozhraní .NET Standard API a doručují se jako součást architektury, požadavek na balíček NuGet se odebere.

Pojďme začít s důvody pro přidání nové podpory řazené kolekce členů. Metody vrací jeden objekt. Řazené kolekce členů umožňují snadněji zabalit více hodnot v jednom objektu.

.NET Framework již obsahuje obecné `Tuple` třídy. Tyto třídy však měly dvě hlavní omezení. Pro jednu `Tuple` třídu s názvem jejich vlastnosti `Item1` , `Item2` a tak dále. Tyto názvy nenesou žádné sémantické informace. Použití těchto `Tuple` typů neumožňuje komunikaci významu jednotlivých vlastností. Nové funkce jazyka umožňují deklarovat a používat sémanticky smysluplné názvy pro prvky v řazené kolekci členů.

`Tuple`Třídy způsobují větší vliv na výkon, protože se jedná o odkazové typy. Použití jednoho z `Tuple` typů znamená přidělení objektů. V případě aktivních cest může mít přidělení mnoha malých objektů měřitelný dopad na výkon aplikace. Proto jazyková podpora pro řazené kolekce členů využívá nové `ValueTuple` struktury.

Chcete-li se těmto nedostatkům vyhnout, můžete vytvořit `class` nebo a `struct` převést více prvků. Bohužel to více funguje za vás a zakrývá váš záměr návrhu. Vytvoření `struct` nebo `class` znamená, že definujete typ s daty a chováním. Mnohokrát stačí uložit více hodnot do jednoho objektu.

Jazykové funkce a `ValueTuple` obecné struktury vynutily pravidlo, že nemůžete přidat žádné chování (metody) k těmto typům řazené kolekce členů.
Všechny `ValueTuple` typy jsou *proměnlivé struktury*. Každé pole člena je veřejné pole. Díky tomu jsou velmi odlehčené. To ale znamená, že by se neměly používat řazené kolekce členů tam, kde je neměnnosti důležité.

Řazené kolekce členů jsou jednodušší a pružnější datové kontejnery než `class` a `struct` typy. Pojďme tyto rozdíly prozkoumat.

## <a name="named-and-unnamed-tuples"></a>Pojmenované a nepojmenované řazené kolekce členů

`ValueTuple`Struktura obsahuje pole s názvy `Item1` , `Item2` , `Item3` a tak dále, podobně jako vlastnosti definované v existujících `Tuple` typech.
Tyto názvy jsou jedinými názvy, které můžete použít pro *nepojmenované řazené kolekce členů*. Pokud neposkytnete žádné alternativní názvy polí do řazené kolekce členů, vytvořili jste nepojmenované řazené kolekce členů:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Řazená kolekce členů v předchozím příkladu byla inicializována pomocí literálových konstant a v jazyce C# 7,1 nebudou vytvořeny názvy elementů pomocí *projekce názvů polí řazené kolekce členů* .

Při inicializaci řazené kolekce členů ale můžete použít nové funkce jazyka, které každému poli přidávají lepší názvy. Tím dojde k vytvoření *pojmenované řazené kolekce členů*.
Pojmenované řazené kolekce členů mají stále prvky s názvem `Item1` ,, `Item2` `Item3` a tak dále.
Mají však také synonyma pro libovolný z těchto elementů, které máte pojmenovány.
Pojmenovanou řazenou kolekci členů vytvoříte zadáním názvů pro každý prvek. Jedním ze způsobů, jak zadat názvy v rámci inicializace řazené kolekce členů:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/program.cs#02_NamedTuple "Named tuple")]

Tato synonyma jsou zpracovávána kompilátorem a jazykem, aby bylo možné používat pojmenované řazené kolekce členů efektivně. IDEs a editory můžou tyto sémantické názvy číst pomocí rozhraní Roslyn API. Na prvky pojmenované řazené kolekce členů můžete odkazovat pomocí těchto sémantických názvů kdekoli ve stejném sestavení. Kompilátor nahradí názvy, které jste definovali, `Item*` ekvivalenty při generování zkompilovaného výstupu. Kompilovaný jazyk MSIL (Microsoft Intermediate Language) neobsahuje názvy, které jste těmto prvkům zadali.

Počínaje jazykem C# 7,1 mohou být názvy polí pro řazené kolekce členů poskytnuty z proměnných používaných k inicializaci řazené kolekce členů. Poskytování názvů polí pro řazené kolekce členů je označováno jako **[Inicializátory projekce řazené kolekce členů](#tuple-projection-initializers)**. Následující kód vytvoří řazenou kolekci členů s názvem `accumulation` s prvky `count` (celé číslo) a `sum` (Double).

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Kompilátor musí komunikovat s názvy, které jste vytvořili pro řazené kolekce členů, které jsou vráceny z veřejných metod nebo vlastností. V těchto případech kompilátor přidá <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> atribut metody. Tento atribut obsahuje <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> vlastnost seznamu, která obsahuje názvy zadané pro každý prvek v řazené kolekci členů.

> [!NOTE]
> Nástroje pro vývoj, jako je třeba Visual Studio, čtou tato metadata a poskytují IntelliSense a další funkce pomocí názvů polí metadat.

Je důležité pochopit tyto základní základy nových řazených kolekcí členů a typ, aby `ValueTuple` bylo možné pochopit pravidla pro přiřazování pojmenovaných řazených kolekcí členů.

## <a name="tuple-projection-initializers"></a>Inicializátory řazené kolekce členů

Obecně se Inicializátory řazené kolekce členů pracují pomocí názvů proměnných nebo polí z pravé strany příkazu inicializace řazené kolekce členů.
Pokud je zadán explicitní název, který má přednost před libovolným názvem projektu. Například v následujícím inicializátoru jsou prvky `explicitFieldOne` a `explicitFieldTwo` , nikoli `localVariableOne` a `localVariableTwo` :

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Pro jakékoli pole, kde není zadáno explicitní jméno, je projekt použit s implicitním názvem. Neexistuje žádný požadavek na poskytování sémantických názvů buď explicitně, nebo implicitně. Následující inicializátor má názvy polí `Item1` , jejichž hodnota je `42` a `stringContent` , jejíž hodnota je "odpověď na vše":

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/program.cs#MixedTuple "mixed tuple")]

Existují dvě podmínky, kdy názvy polí kandidátů nejsou promítnuty do pole řazené kolekce členů:

1. Pokud je kandidátem název vyhrazený název řazené kolekce členů. Příklady zahrnují `Item3` , `ToString` nebo `Rest` .
1. Pokud je název kandidáta duplicitní s jiným názvem pole řazené kolekce členů, buď explicitní, nebo implicitní.

Tyto podmínky zabraňují nejednoznačnosti. Tyto názvy by způsobily nejednoznačnost, pokud byly použity jako názvy polí v řazené kolekci členů. Ani jedna z těchto podmínek nezpůsobí chyby při kompilaci. Místo toho pro prvky bez projektových názvů nejsou pro ně sémanticky pojmenovány.  Následující příklady znázorňují tyto podmínky:

[!code-csharp-interactive[Ambiguity](../../samples/snippets/csharp/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Tyto situace nezpůsobují chyby kompilátoru, protože by se jednalo o zásadní změnu kódu napsaného v jazyce C# 7,0, pokud nejsou k dispozici žádné projekce názvu pole řazené kolekce členů.

## <a name="equality-and-tuples"></a>Rovnost a řazené kolekce členů

Počínaje jazykem C# 7,3 typy řazené kolekce členů `==` podporují `!=` operátory a. Tyto operátory pracují pomocí porovnání jednotlivých členů levého argumentu s každým členem pravého argumentu v daném pořadí. Tyto porovnávací krátkodobé okruhy. Přestanou vyhodnocovat členy, jakmile se jeden pár nerovná. Následující příklady kódu používají `==` , ale pravidla porovnání platí pro `!=` . Následující příklad kódu ukazuje porovnání rovnosti pro dvě páry celých čísel:

[!code-csharp-interactive[TupleEquality](../../samples/snippets/csharp/tuples/program.cs#Equality "Testing tuples for equality")]

Existuje několik pravidel, která umožňují pohodlnější testy rovnosti řazené kolekce členů. Rovnost řazené kolekce členů provádí převedené [převody](~/_csharplang/spec/conversions.md#lifted-conversion-operators) , pokud je jedna z řazených kolekcí členů s možnou hodnotou null, jak je znázorněno v následujícím kódu:

[!code-csharp-interactive[NullableTupleEquality](../../samples/snippets/csharp/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

Rovnost řazené kolekce členů také provádí implicitní převody na každého členu obou řazených kolekcí členů. Patří mezi ně zrušené převody, rozšiřující převody nebo jiné implicitní převody. Následující příklady ukazují, že celočíselná hodnota 2 – řazená kolekce členů může být porovnána s dlouhou meziřazenou kolekcí členů z důvodu implicitního převodu z celého čísla na Long:

[!code-csharp-interactive[SnippetMemberConversions](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Názvy členů řazené kolekce členů se neúčastní testů pro rovnost. Pokud je však jeden z operandů literál řazené kolekce členů s explicitními názvy, kompilátor vygeneruje upozornění CS8383, pokud tyto názvy neodpovídají názvům jiného operandu.
V případě, kdy jsou oba operandy literály řazené kolekce členů, je upozornění na pravém operandu, jak je znázorněno v následujícím příkladu:

[!code-csharp-interactive[MemberNames](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

A konečně, řazené kolekce členů můžou obsahovat vnořené řazené kolekce členů. Rovnost řazené kolekce členů porovnává "tvar" každého operandu prostřednictvím vnořených řazených kolekcí členů, jak je znázorněno v následujícím příkladu:

[!code-csharp-interactive[NestedTuples](../../samples/snippets/csharp/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

Jedná se o chybu při kompilaci pro porovnání dvou řazených kolekcí členů s rovností (nebo nerovnosti), pokud mají různé tvary. Kompilátor se nebude pokoušet o žádné dekonstrukci vnořených řazených kolekcí členů, aby je bylo možné porovnat.

## <a name="assignment-and-tuples"></a>Přiřazení a řazené kolekce členů

Jazyk podporuje přiřazení mezi typy řazené kolekce členů, které mají stejný počet prvků, kde každý prvek na pravé straně lze implicitně převést na odpovídající element na levé straně. Jiné převody nejsou považovány za přiřazení. Jedná se o chybu při kompilaci k přiřazení jedné řazené kolekce členů k druhému, pokud mají různé tvary. Kompilátor se nebude pokoušet o žádné dekonstrukci vnořených řazených kolekcí členů, aby je bylo možné přiřadit.
Pojďme se podívat na typy přiřazení, která jsou povolená mezi typy řazené kolekce členů.

Vezměte v úvahu tyto proměnné, které se používají v následujících příkladech:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/program.cs#03_VariableCreation "Variable creation")]

První dvě proměnné a nemají `unnamed` `anonymous` pro prvky k dispozici sémantické názvy. Názvy polí jsou `Item1` a `Item2` .
Poslední dvě proměnné `named` a `differentName` mají pro prvky zadány sémantické názvy. Tyto dvě řazené kolekce členů mají různé názvy pro prvky.

Všechny čtyři tyto řazené kolekce členů mají stejný počet elementů (označovaných jako mohutnost) a typy těchto elementů jsou identické. Proto všechna tato přiřazení fungují:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Všimněte si, že názvy řazených kolekcí členů nejsou přiřazeny. Hodnoty prvků jsou přiřazeny podle pořadí prvků v řazené kolekci členů.

Řazené kolekce členů různých typů nebo čísel prvků nelze přiřadit:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Řazené kolekce členů jako návratové hodnoty metody

Jedním z nejběžnějších použití pro řazené kolekce členů je jako návratová hodnota metody. Pojďme si projít jeden příklad. Zvažte tuto metodu, která vypočítá směrodatnou odchylku pro posloupnost čísel:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Tyto příklady vypočítají nesprávnou směrodatnou odchylku vzorků.
> Opravený Vzorec směrodatné odchylky (standardní vzorek) rozdělí součet kvadratických rozdílů od střední hodnoty (N-1) namísto N, jako `Average` metoda rozšíření.

Předchozí kód následuje vzorec Textbook pro směrodatnou odchylku. Vytváří správnou odpověď, ale jedná se o neefektivní implementaci. Tato metoda sestaví sekvenci dvakrát: jednou pro vytvoření průměru a jednou pro vytvoření průměru z čtverce rozdílu v průměru.
(Nezapomeňte, že dotazy LINQ jsou vyhodnoceny jako laxně vytvářená, takže výpočet rozdílů od střední hodnoty a průměr těchto rozdílů činí pouze jeden výčet.)

Existuje alternativní vzorec, který počítá směrodatnou odchylku pomocí pouze jednoho výčtu sekvence.  Tento výpočet vytvoří dvě hodnoty, protože sestaví sekvenci: součet všech položek v sekvenci a součet každé hodnoty čtverce:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Tato verze sestaví sekvenci přesně jednou. Nejedná se ale o opakovaně použitelný kód. Jak budete pracovat, zjistíte, že mnoho různých statistických výpočtů používá počet položek v sekvenci, součet sekvence a součet čtverců sekvence. Pojďme tuto metodu Refaktorovat a napsat metodu nástroje, která vytvoří všechny tři tyto hodnoty. Všechny tři hodnoty mohou být vráceny jako řazené kolekce členů.

Pojďme tuto metodu aktualizovat tak, aby tři hodnoty vypočítané během výčtu byly uloženy v řazené kolekci členů. Vytváří tuto verzi:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Podpora refaktoringu sady Visual Studio usnadňuje extrakci funkcí základních statistik do privátní metody. Poskytuje `private static` metodu, která vrací typ řazené kolekce členů se třemi hodnotami `Sum` , `SumOfSquares` a `Count` :

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]

Jazyk umožňuje několik dalších možností, které můžete použít, pokud chcete udělat několik rychlých úprav ručně. Nejprve můžete použít `var` deklaraci k inicializaci výsledku řazené kolekce členů z `ComputeSumAndSumOfSquares` volání metody. V rámci metody můžete také vytvořit tři diskrétní proměnné `ComputeSumAndSumOfSquares` . Finální verze je zobrazená v následujícím kódu:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Tato konečná verze se dá použít pro libovolnou metodu, která potřebuje tyto tři hodnoty, nebo jakoukoli její podmnožinu.

Jazyk podporuje další možnosti správy názvů prvků v těchto metodách vracejících řazené kolekce členů.

Můžete odebrat názvy polí z deklarace návratové hodnoty a vrátit nepojmenované řazené kolekce členů:

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

Pole této řazené kolekce členů jsou pojmenovány `Item1` , `Item2` a `Item3` .
Doporučuje se poskytnout sémantické názvy prvků řazených kolekcí členů vrácených z metod.

Další idiom v případě, že řazené kolekce členů mohou být užitečné, je při vytváření dotazů LINQ. Konečný plánovaný výsledek často obsahuje některé z vlastností objektů, které jsou vybrány, ale ne všechny.

Výsledky dotazu byste měli zamítnout do posloupnosti objektů, které byly anonymního typu. , Který prezentuje mnoho omezení, hlavně proto, že anonymní typy nelze pohodlně pojmenovat v návratovém typu pro metodu. Alternativy použití `object` nebo `dynamic` jako typ výsledku byly v důsledku značných nákladů na výkon.

Vrácení sekvence typu řazené kolekce členů je jednoduché a názvy a typy prvků jsou k dispozici v době kompilace a prostřednictvím nástrojů IDE.
Zvažte například aplikaci ToDo. Můžete definovat třídu podobnou následující, aby představovala jedinou položku v seznamu ToDo:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Vaše mobilní aplikace mohou podporovat kompaktní formu aktuálních položek ToDo, které zobrazují pouze nadpis. Tento dotaz LINQ by provedl projekci, která obsahuje pouze ID a název. Metoda, která vrací sekvenci řazených kolekcí členů vyjadřuje tento návrh dobře:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> V C# 7,1, projekce v rámci řazené kolekce členů umožňují vytvářet pojmenované řazené kolekce členů pomocí prvků podobně jako vlastnost pojmenování v anonymních typech. Ve výše uvedeném kódu `select` příkaz v projekci dotazu vytvoří řazenou kolekci členů, která obsahuje prvky `ID` a `Title` .

Pojmenovaná řazená kolekce členů může být součástí signatury. Umožňuje kompilátoru a nástrojům IDE poskytovat statickou kontrolu, že výsledek používáte správně. Pojmenované řazené kolekce členů také přenáší informace o statickém typu, takže není nutné používat nákladné funkce běhu jako reflexe nebo dynamická vazba pro práci s výsledky.

## <a name="deconstruction"></a>Dekonstrukce

Můžete odbalit všechny položky v řazené kolekci členů tím, že *dekonstruujete* řazenou kolekci členů vrácenou metodou. Existují tři různé přístupy k dekonstrukci řazených kolekcí členů.  Nejprve můžete explicitně deklarovat typ každého pole uvnitř závorek a vytvořit tak diskrétní proměnné pro každý prvek řazené kolekce členů:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Můžete také deklarovat implicitně typové proměnné pro každé pole v řazené kolekci členů pomocí `var` klíčového slova vně závorek:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Také je právní použití `var` klíčového slova s libovolnou nebo všemi deklaracemi proměnných uvnitř závorek.

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Nemůžete použít konkrétní typ mimo závorky, a to ani v případě, že každé pole v řazené kolekci členů má stejný typ.

Můžete dekonstruovat řazené kolekce členů i s existujícími deklaracemi:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
> V závorkách nelze kombinovat existující deklarace s deklaracemi. Následující není například povoleno: `(var x, y) = MyMethod();` . Tím se vytvoří chyba CS8184, protože *x* je deklarované uvnitř závorek a *y* je dřív deklarovaný jinde.

### <a name="deconstructing-user-defined-types"></a>Dekonstrukce uživatelem definovaných typů

Libovolný typ řazené kolekce členů lze dekonstruovat, jak je uvedeno výše. Je také snadné povolit dekonstrukci u libovolného uživatelsky definovaného typu (třídy, struktury nebo dokonce rozhraní).

Autor typu může definovat jednu nebo více `Deconstruct` metod, které přiřazují hodnoty k libovolnému počtu [ `out` proměnných](language-reference/keywords/out-parameter-modifier.md) reprezentujícím datové prvky, které tvoří typ. Například následující `Person` typ definuje `Deconstruct` metodu, která dekonstruuje objekt Person do prvků představujících křestní jméno a příjmení:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

Metoda dekonstrukce umožňuje přiřazení z a `Person` do dvou řetězců, které představují `FirstName` vlastnosti a `LastName` :

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Můžete povolit dekonstrukci i pro typy, které jste nevytvořili.
`Deconstruct`Metoda může být metoda rozšíření, která odbalí přístupné datové členy objektu. Níže uvedený příklad ukazuje `Student` typ, odvozený z `Person` typu, a metodu rozšíření, která dekonstruujee `Student` do tří proměnných, reprezentující `FirstName` , `LastName` a `GPA` :

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

`Student`Objekt má nyní dvě dostupné `Deconstruct` metody: metodu rozšíření deklarovanou pro `Student` typy a člena `Person` typu. Obě jsou v oboru, což umožňuje, `Student` aby bylo možné ho rozdělit do dvou proměnných nebo tří.
Pokud každému studentovi přiřadíte tři proměnné, vrátí se všechna jeho křestní jméno, příjmení a GPA. Pokud do dvou proměnných přiřadíte studenta, vrátí se pouze jméno a příjmení.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Měli byste pečlivě definovat více `Deconstruct` metod ve třídě nebo hierarchii tříd. Více `Deconstruct` metod, které mají stejný počet `out` parametrů, může rychle způsobit nejednoznačnosti. Volající nemusí být schopni snadno volat požadovanou `Deconstruct` metodu.

V tomto příkladu je minimální pravděpodobnost pro dvojznačné volání `Deconstruct` , protože metoda pro `Person` má dva výstupní parametry a `Deconstruct` metoda pro `Student` má tři.

Operátory dekonstrukce se nepodílejí na testování rovnosti. Následující příklad generuje chybu kompilátoru CS0019:

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

`Deconstruct`Metoda by mohla převést `Person` objekt `p` na řazenou kolekci členů, která obsahuje dva řetězce, ale není platná v kontextu testů rovnosti.

## <a name="tuples-as-out-parameters"></a>Řazené kolekce členů jako výstupní parametry

Řazené kolekce členů lze použít jako *samotné* [ `out` parametry](language-reference/keywords/out-parameter-modifier.md) . Nepleťte si se bez jakýchkoli nejednoznačnosti dříve zmíněných v části [dekonstrukce](#deconstruction) . Ve volání metody potřebujete pouze popsat tvar řazené kolekce členů:

[!code-csharp[TuplesAsOutParameters](~/samples/snippets/csharp/tuples/program.cs#01_TupleAsOutVariable "Tuples as out parameters")]

Alternativně můžete použít [_nepojmenované_](#named-and-unnamed-tuples) řazené kolekce členů a odkazovat na své pole `Item1` jako `Item2` a:

```csharp
dict.TryGetValue(2, out (int, string) pair);
// ...
Console.WriteLine($"{pair.Item1}: {pair.Item2}");
```

## <a name="conclusion"></a>Závěr

Podpora nového jazyka a knihovny pro pojmenované řazené kolekce členů usnadňuje práci s návrhy, které používají datové struktury, které ukládají více elementů, ale nedefinují chování, jako třídy a struktury. Použití řazených kolekcí členů pro tyto typy je jednoduché a stručné. Získáte všechny výhody kontroly statického typu, aniž byste museli vytvářet typy pomocí podrobnějšího `class` `struct` příkazu nebo syntaxe. I tak je nejužitečnější pro obslužné metody, které jsou `private` nebo `internal` . Vytvořte uživatelsky definované typy, buď `class` nebo `struct` typy, pokud vaše veřejné metody vrací hodnotu, která má více prvků.
