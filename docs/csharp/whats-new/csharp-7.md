---
title: Co je nového v C# 7,0 – C# příručka
description: Získejte přehled o nových funkcích v C# jazyce verze 7,0.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 148ecdf7a3a99ac73132593272ecff3a5bb4195e
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105718"
---
# <a name="whats-new-in-c-70"></a>Co je nového v C# 7,0

C#7,0 přidání řady nových funkcí do C# jazyka:
- [`out`proměnné](#out-variables)
  - Můžete deklarovat `out` hodnoty vložené jako argumenty pro metodu, kde se používají.
- [Řazené kolekce členů](#tuples)
  - Můžete vytvořit odlehčené nejmenované typy, které obsahují více veřejných polí. Kompilátory a nástroje IDE, které porozuměl sémantikě těchto typů.
- [Zahození](#discards)
  - Zahození jsou dočasné a proměnné jen pro zápis použité v přiřazeních, když se nemusíte starat o přiřazenou hodnotu. Jsou nejužitečnější při dekonstrukci řazených kolekcí členů a uživatelsky definovaných typů a také při volání metod s `out` parametry.
- [Porovnávání vzorů](#pattern-matching)
  - Můžete vytvořit logiku větvení na základě libovolných typů a hodnot členů těchto typů.
- [`ref`místní hodnoty a vrátí](#ref-locals-and-returns)
  - Místní proměnné metody a návratové hodnoty mohou být odkazy na jiné úložiště.
- [Místní funkce](#local-functions)
  - Funkce můžete vnořit do jiných funkcí a omezit tak jejich rozsah a viditelnost.
- [Další členové Expression-těle](#more-expression-bodied-members)
  - Seznam členů, které mohou být vytvořeny pomocí výrazů, byl vypěstován.
- [`throw`Expression](#throw-expressions)
  - Můžete vyvolat výjimky v konstrukcích kódu, které nebyly dřív povoleny, `throw` protože se jednalo o příkaz.
- [Generalizované asynchronní návratové typy](#generalized-async-return-types)
  - Metody deklarované s `async` modifikátorem mohou vracet další typy `Task` kromě a `Task<T>`.
- [Vylepšení syntaxe numerického literálu](#numeric-literal-syntax-improvements)
  - Nové tokeny zlepšují čitelnost pro číselné konstanty.

Zbývající část tohoto článku poskytuje přehled jednotlivých funkcí. U každé funkce se dozvíte, co je důvod na pozadí. Naučíte se syntaxí. Pomocí `dotnet try` globálního nástroje můžete prozkoumat tyto funkce ve vašem prostředí:

1. Nainstalujte nástroj [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Naklonujte úložiště [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *Try-Samples* .
1. Spusťte `dotnet try`.

## <a name="out-variables"></a>`out`proměnné

V této verzi byla vylepšena existující syntaxe, která podporuje `out` parametry. Nyní můžete deklarovat `out` proměnné v seznamu argumentů volání metody, namísto psaní samostatného příkazu deklarace:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Možná budete chtít zadat typ `out` proměnné pro přehlednost, jak je uvedeno výše. Jazyk však podporuje použití implicitně typované lokální proměnné:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- Čtení kódu je snazší.
  - Deklarujete proměnnou, kde ji používáte, nikoli na jiném řádku výše.
- Není nutné přiřazovat počáteční hodnotu.
  - Deklarováním `out` proměnné, kde se používá ve volání metody, nemůžete ji omylně použít před přiřazením.

## <a name="tuples"></a>N-tice

C#poskytuje bohatou syntaxi pro třídy a struktury, které slouží k vysvětlení záměru návrhu. V některých případech však bohatá syntaxe vyžaduje dodatečnou práci s minimální výhodou. Můžete často napsat metody, které vyžadují jednoduchou strukturu obsahující více než jeden datový prvek. Pro podporu těchto scénářů byly přidány řazené C# *kolekce členů* do. Řazené kolekce členů jsou jednoduché datové struktury, které obsahují více polí představujících datové členy.
Pole se neověřují a nemůžete definovat vlastní metody.

> [!NOTE]
> Řazené kolekce členů byly C# k dispozici před 7,0, ale byly neefektivní a nemají žádnou jazykovou podporu.
> To znamenalo, že prvky řazené kolekce členů `Item1`mohou `Item2` být odkazovány pouze jako a tak dále. C#7,0 zavádí jazykovou podporu pro řazené kolekce členů, která umožňuje sémantické názvy polí řazené kolekce členů pomocí nových, efektivnějších typů řazených kolekcí členů.

Můžete vytvořit řazenou kolekci členů tak, že každému členovi přiřadíte hodnotu a volitelně zadáte sémantické názvy každé z členů řazené kolekce členů:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

Řazená kolekce členů obsahuje pole, `Alpha` která jsou uvedena jako a `Beta`. `namedLetters` Tyto názvy existují pouze v době kompilace a nejsou zachovány, například při kontrole řazené kolekce členů pomocí reflexe za běhu.

V přiřazení řazené kolekce členů můžete také zadat názvy polí na pravé straně přiřazení:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Mohou nastat situace, kdy budete chtít odbalit členy řazené kolekce členů, které byly vráceny metodou.  To můžete provést deklarováním samostatných proměnných pro každou z hodnot v řazené kolekci členů. Toto rozbalení se označuje jako dekonstrukce řazené kolekce členů:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Můžete také poskytnout podobný dekonstrukci pro libovolný typ v rozhraní .NET. `Deconstruct` Metodu můžete napsat jako člena třídy. Tato `Deconstruct` metoda poskytuje `out` sadu argumentů pro každou z vlastností, které chcete extrahovat. Zvažte tuto `Point` třídu, která poskytuje metodu dekonstruktoru, která `X` extrahuje `Y` souřadnice a:

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Jednotlivá pole můžete extrahovat přiřazením `Point` k řazené kolekci členů:

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Podrobnější informace o řazených kolekcích členů najdete v [článku o řazených kolekcích členů](../tuples.md).

## <a name="discards"></a>Zahození

Často při dekonstrukci řazené kolekce členů nebo volání metody s `out` parametry jste nuceni definovat proměnnou, jejíž hodnotu nezáleží na a nehodláte ji používat. C#Přidá podporu pro zahození pro zpracování tohoto scénáře. Zrušení je proměnná pouze pro zápis, jejíž název je `_` (podtržítko). můžete přiřadit všechny hodnoty, které chcete zahodit do jedné proměnné. Zahození je jako Nepřiřazená proměnná; Kromě příkazu přiřazení nelze zrušit použití v kódu.

Zahození jsou podporovaná v následujících scénářích:

- Při dekonstrukci řazených kolekcí členů nebo uživatelsky definovaných typů.
- Při volání metod s [výstupními](../language-reference/keywords/out-parameter-modifier.md) parametry.
- V operaci porovnávání vzorů s příkazy [is](../language-reference/keywords/is.md) a [Switch](../language-reference/keywords/switch.md) .
- Jako samostatný identifikátor, pokud chcete explicitně identifikovat hodnotu přiřazení jako zahození.

Následující příklad definuje `QueryCityDataForYears` metodu, která vrátí 6 – řazenou kolekci členů, která obsahuje data pro město dvou různých roků. Volání metody v příkladu se týká pouze dvou hodnot naplnění vrácených metodou, takže poběží zbývající hodnoty v řazené kolekci členů jako zahození při dekonstrukci řazené kolekce členů.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Další informace najdete v tématu [](../discards.md)zahození.

## <a name="pattern-matching"></a>Porovnávání vzorů

*Porovnávání vzorů* je funkce, která umožňuje implementovat odeslání metody pro jiné vlastnosti než typ objektu. V závislosti na typu objektu již pravděpodobně znáte způsob odeslání metody. V objektově orientovaném programování metody Virtual a override poskytují jazykovou syntaxi pro implementaci metody odeslání na základě typu objektu. Základní a odvozené třídy poskytují různé implementace.
Výrazy pro porovnávání vzorů přesahují tento koncept, takže můžete snadno implementovat podobné vzory odeslání pro typy a datové prvky, které nesouvisí s hierarchií dědičnosti.

Porovnávání vzorů `is` podporuje výrazy `switch` a výrazy. Každá z nich umožňuje kontrolu objektu a jeho vlastností, aby bylo možné určit, zda tento objekt splňuje požadovaný vzor. `when` Klíčové slovo můžete použít k určení dalších pravidel pro vzor.

Výraz Pattern rozšiřuje známý [ `is` operátor](../language-reference/keywords/is.md#pattern-matching-with-is) pro dotazování objektu o jeho typu a přiřazení výsledku do jedné instrukce. `is` Následující kód zkontroluje `int`, zda je proměnná, a pokud ano, přidá ji do aktuálního součtu:

```csharp
if (input is int count)
    sum += count;
```

Předchozí malý příklad ukazuje vylepšení `is` výrazu. Můžete testovat proti typům hodnot i odkazovým typům a k nové proměnné správného typu můžete přiřadit úspěšný výsledek.

Výraz porovnávání přepínačů má známou syntaxi na základě `switch` příkazu, který už je součástí C# jazyka. Aktualizovaný příkaz switch má několik nových konstrukcí:

- Typ `switch` řízení výrazu již není omezen na celočíselné typy, typy, `string`ani `Enum` typ s možnou hodnotou null, který odpovídá jednomu z těchto typů. Může být použit libovolný typ.
- Můžete testovat typ `switch` výrazu v každém `case` popisku. Stejně jako u `is` výrazu můžete k tomuto typu přiřadit novou proměnnou.
- Můžete přidat `when` klauzuli pro další podmínky testování v této proměnné.
- Pořadí `case` popisků je teď důležité. První větev, která se má porovnat, se spustí; ostatní se přeskočí.

Následující kód demonstruje tyto nové funkce:

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0:
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0:
                sum += n;
                break;
            case null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- `case 0:`je známý konstantní vzor.
- `case IEnumerable<int> childSequence:`je vzor typu.
- `case int n when n > 0:`je vzor typu s další `when` podmínkou.
- `case null:`je vzor null.
- `default:`je známý výchozí případ.

Další informace o porovnávání vzorů najdete ve vzorovém [porovnávání C#v ](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Místní a návratové hodnoty REF

Tato funkce umožňuje algoritmy, které používají a vracejí odkazy na proměnné definované jinde. Jeden příklad pracuje s velkými maticemi a hledá jedno umístění s určitými charakteristikami. Následující metoda vrátí **odkaz** na toto úložiště v matici:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Můžete deklarovat návratovou hodnotu jako `ref` a upravit tuto hodnotu v matici, jak je znázorněno v následujícím kódu:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

C# Jazyk obsahuje několik pravidel, která vás chrání před nepoužitím `ref` místních hodnot a vrátí:

- `ref` Klíčové slovo je nutné přidat do podpisu metody a do všech `return` příkazů v metodě.
  - Tím se vymaže metoda, kterou vrátí odkaz v rámci této metody.
- Může být přiřazená k proměnné hodnoty `ref` nebo proměnné. `ref return`
  - Volající řídí, zda je vrácená hodnota zkopírována nebo ne. Vynechání `ref` modifikátoru při přiřazování návratové hodnoty znamená, že volající chce kopii hodnoty, nikoli odkaz na úložiště.
- Nemůžete přiřadit návratovou hodnotu `ref` standardní metody místní proměnné.
  - Která nepovoluje příkazy jako`ref int i = sequence.Count();`
- Nemůžete vrátit `ref` do proměnné, jejíž doba života nepřesahuje po provedení metody.
  - To znamená, že nemůžete vrátit odkaz na místní proměnnou nebo proměnnou s podobným oborem.
- `ref`lokální hodnoty a vrácení nelze použít s asynchronními metodami.
  - Kompilátor nemůže zjistit, zda se odkazovaná proměnná nastavila na konečnou hodnotu, když vrátí asynchronní metoda.

Přidání místních a návratových odkazů umožňuje algoritmy, které jsou efektivnější, protože se vyhnete kopírování hodnot nebo provádění operací zrušení odkazování vícekrát.

Přidání `ref` do návratové hodnoty je [Změna kompatibilní se zdrojem](version-update-considerations.md#source-compatible-changes). Existující kód je zkompilován, ale návratová hodnota REF je při přiřazení zkopírována. Volající musí aktualizovat úložiště pro návratovou hodnotu na `ref` lokální proměnnou, aby se vrácení vrátilo jako odkaz.

Další informace najdete v článku věnovaném [klíčovému slovu ref](../language-reference/keywords/ref.md) .

## <a name="local-functions"></a>Lokální funkce

Mnoho návrhů pro třídy obsahuje metody, které jsou volány pouze z jednoho umístění. Tyto další privátní metody udržují jednotlivé metody malé a prioritní. *Místní funkce* umožňují deklarovat metody v kontextu jiné metody. Místní funkce usnadňují čtenářům třídy, aby bylo vidět, že místní metoda je volána pouze z kontextu, ve kterém je deklarována.

Existují dva běžné případy použití pro místní funkce: veřejné metody iterátoru a veřejné asynchronní metody. Oba typy metod generují kód, který hlásí chyby později než programátoři mohou očekávat. V metodách iterátoru jsou všechny výjimky pozorovány pouze při volání kódu, který vytvoří výčet vrácené sekvence. V asynchronních metodách jsou jakékoli výjimky pozorovány pouze v `Task` případě, že je očekáváno vrácení. Následující příklad ukazuje oddělení ověřování parametrů z implementace iterátoru pomocí místní funkce:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Stejný postup lze použít s `async` metodami, aby bylo zajištěno, že výjimky vznikající z ověřování argumentu jsou vyvolány před zahájením asynchronní práce:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Některé z návrhů, které jsou podporovány místními funkcemi, by mohly být také provedeny pomocí *výrazů lambda*. O rozdílech, které mají zájem [, si můžete přečíst další informace](../local-functions-vs-lambdas.md) .

## <a name="more-expression-bodied-members"></a>Další členové Expression-těle

C#6 zavedlo [členy Expression-těle](csharp-6.md#expression-bodied-function-members) pro členské funkce a vlastnosti jen pro čtení. C#7,0 rozšíří povolené členy, které mohou být implementovány jako výrazy. V C# 7,0 můžete implementovat konstruktory, *finalizační metody*a `get` `set` přístupové objekty do *vlastností* a *indexerů*. Následující kód ukazuje příklady jednotlivých:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Tento příklad nepotřebuje finalizační metodu, ale je zobrazený k předvedení syntaxe. V třídě byste neměli implementovat finalizační metodu, pokud není nutné vydávat nespravované prostředky. Měli byste také zvážit použití <xref:System.Runtime.InteropServices.SafeHandle> třídy namísto přímého spravování nespravovaných prostředků.

Tato nová umístění pro členy Expression-těle reprezentují důležitý milník pro C# jazyk: Tyto funkce byly implementovány členy komunity, kteří pracují na open source projektu [Roslyn](https://github.com/dotnet/Roslyn) .

Změna metody na člen výrazu těle je [binární kompatibilní změna](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Výrazy throw

V C# příkaz.`throw` Vzhledem `throw` k tomu, že je příkaz, nikoli výraz, C# byly konstrukce, kde jste ho nemohli použít. Tyto zahrnuté podmíněné výrazy, null slučovací výrazy a některé lambda výrazy. Přidání členů Expression-těle přidá více míst, kde `throw` by bylo užitečné výrazy. Takže můžete napsat libovolný z těchto konstrukcí, C# 7,0 zavádí [výrazy throw](../language-reference/keywords/throw.md#the-throw-expression).

Díky tomu je snazší psát další kód založený na výrazu. Pro kontrolu chyb nepotřebujete další příkazy.

## <a name="generalized-async-return-types"></a>Generalizované asynchronní návratové typy

`Task` Vrácení objektu z asynchronních metod může způsobit kritické body výkonu v určitých cestách. `Task`je odkazový typ, takže jeho použití znamená přidělení objektu. V případech, kdy metoda deklarovaná s `async` modifikátorem vrací výsledek uložený v mezipaměti, nebo je dokončena synchronně, se další přidělení můžou stát značnými náklady v částech kritického výkonu v kódu. Pokud dojde k přidělení v těsných smyčkách, může to být nákladné.

Nová funkce jazyka znamená, že návratové typy asynchronní metody nejsou omezeny `Task<T>`na `Task`, `void`a. Vrácený typ musí stále splňovat asynchronní vzorek, což znamená, že `GetAwaiter` metoda musí být přístupná. Jako jeden konkrétní příklad byl `ValueTask` typ přidán do rozhraní .NET Framework, aby bylo možné používat tuto novou jazykovou funkci:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> Aby bylo možné <xref:System.Threading.Tasks.ValueTask%601> typ použít, je [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) nutné přidat balíček NuGet.

Toto vylepšení je nejužitečnější pro autory knihovny, aby `Task` nedošlo k přidělení v kritickém kódu výkonu.

## <a name="numeric-literal-syntax-improvements"></a>Vylepšení syntaxe numerického literálu

Nepřečtené číselné konstanty mohou ztížit pochopení kódu při prvním čtení. Bitové masky nebo jiné symbolické hodnoty jsou náchylné k nepochopení. C#7,0 obsahuje dvě nové funkce pro zápis čísel v nejčitelnějším způsobu pro zamýšlené použití: *binární literály*a oddělovače *číslic*.

V případech, kdy vytváříte bitové masky, nebo pokaždé, když binární reprezentace čísla provede Nejčitelnější kód, zapište toto číslo v binárním formátu:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

Na `0b` začátku konstanty označuje, že číslo je zapsáno jako binární číslo. Binární čísla mohou být dlouhá, takže je často snazší zobrazit bitové vzory tím, že zavedete `_` jako oddělovač číslic, jak je uvedeno výše v binární konstantě. Oddělovač číslic se může objevit kdekoli v konstantě. U základních 10 čísel je běžné ji použít jako oddělovač tisíců:

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Oddělovač číslic lze použít s `decimal`typy, `float`a `double` také:

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Společně můžete deklarovat číselné konstanty s mnohem větší čitelností.
