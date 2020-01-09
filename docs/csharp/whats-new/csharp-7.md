---
title: Co je nového v C# 7,0 – C# příručka
description: Získejte přehled o nových funkcích v C# jazyce verze 7,0.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 73563a04dea04c942a6326d6a04ddd54bb80b0ed
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694579"
---
# <a name="whats-new-in-c-70"></a>Co je nového v C# 7,0

C#7,0 přidání řady nových funkcí do C# jazyka:

- [proměnné `out`](#out-variables)
  - Můžete deklarovat `out` hodnoty vložené jako argumenty metodě, kde se používají.
- [Řazené kolekce členů](#tuples)
  - Můžete vytvořit odlehčené nejmenované typy, které obsahují více veřejných polí. Kompilátory a nástroje IDE, které porozuměl sémantikě těchto typů.
- [Zahození](#discards)
  - Zahození jsou dočasné a proměnné jen pro zápis použité v přiřazeních, když se nemusíte starat o přiřazenou hodnotu. Jsou nejužitečnější při dekonstrukci řazených kolekcí členů a uživatelsky definovaných typů a také při volání metod s parametry `out`.
- [Porovnávání vzorů](#pattern-matching)
  - Můžete vytvořit logiku větvení na základě libovolných typů a hodnot členů těchto typů.
- [`ref` místní hodnoty a vrátí](#ref-locals-and-returns)
  - Místní proměnné metody a návratové hodnoty mohou být odkazy na jiné úložiště.
- [Místní funkce](#local-functions)
  - Funkce můžete vnořit do jiných funkcí a omezit tak jejich rozsah a viditelnost.
- [Další členové Expression-těle](#more-expression-bodied-members)
  - Seznam členů, které mohou být vytvořeny pomocí výrazů, byl vypěstován.
- [Výrazy `throw`](#throw-expressions)
  - Můžete vyvolat výjimky v konstrukcích kódu, které dříve nebyly povoleny, protože `throw` byl příkaz.
- [Generalizované asynchronní návratové typy](#generalized-async-return-types)
  - Metody deklarované s modifikátorem `async` mohou kromě `Task` a `Task<T>`vracet jiné typy.
- [Vylepšení syntaxe numerického literálu](#numeric-literal-syntax-improvements)
  - Nové tokeny zlepšují čitelnost pro číselné konstanty.

Zbývající část tohoto článku poskytuje přehled jednotlivých funkcí. U každé funkce se dozvíte, co je důvod na pozadí. Naučíte se syntaxí. Tyto funkce můžete ve svém prostředí prozkoumat pomocí globálního nástroje `dotnet try`:

1. Nainstalujte nástroj [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Naklonujte úložiště [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *Try-Samples* .
1. Spusťte `dotnet try`.

## <a name="out-variables"></a>proměnné `out`

V této verzi se vylepšila existující syntaxe, která podporuje parametry `out`. Nyní můžete deklarovat proměnné `out` v seznamu argumentů volání metody, místo psaní samostatného příkazu deklarace:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Možná budete chtít zadat typ proměnné `out` pro přehlednost, jak je uvedeno výše. Jazyk však podporuje použití implicitně typované lokální proměnné:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- Čtení kódu je snazší.
  - Deklarujete proměnnou, kde ji používáte, nikoli na jiném řádku výše.
- Není nutné přiřazovat počáteční hodnotu.
  - Deklarováním `out` proměnné, kde se používá ve volání metody, nemůžete ji omylně použít před přiřazením.

## <a name="tuples"></a>N-tice

C#poskytuje bohatou syntaxi pro třídy a struktury, které slouží k vysvětlení záměru návrhu. V některých případech však bohatá syntaxe vyžaduje dodatečnou práci s minimální výhodou. Můžete často napsat metody, které vyžadují jednoduchou strukturu obsahující více než jeden datový prvek. Pro podporu těchto scénářů byly přidány *řazené kolekce členů* do C#. Řazené kolekce členů jsou jednoduché datové struktury, které obsahují více polí představujících datové členy.
Pole se neověřují a nemůžete definovat vlastní metody.

> [!NOTE]
> Řazené kolekce členů byly C# k dispozici před 7,0, ale byly neefektivní a nemají žádnou jazykovou podporu.
> To znamenalo, že prvky řazené kolekce členů mohou být pouze odkazovány jako `Item1`, `Item2` a tak dále. C#7,0 zavádí jazykovou podporu pro řazené kolekce členů, která umožňuje sémantické názvy polí řazené kolekce členů pomocí nových, efektivnějších typů řazených kolekcí členů.

Můžete vytvořit řazenou kolekci členů tak, že každému členovi přiřadíte hodnotu a volitelně zadáte sémantické názvy každé z členů řazené kolekce členů:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

Řazená kolekce členů `namedLetters` obsahuje pole, která jsou uváděna jako `Alpha` a `Beta`. Tyto názvy existují pouze v době kompilace a nejsou zachovány, například při kontrole řazené kolekce členů pomocí reflexe za běhu.

V přiřazení řazené kolekce členů můžete také zadat názvy polí na pravé straně přiřazení:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Mohou nastat situace, kdy budete chtít odbalit členy řazené kolekce členů, které byly vráceny metodou.  To můžete provést deklarováním samostatných proměnných pro každou z hodnot v řazené kolekci členů. Toto rozbalení se označuje jako *dekonstrukce* řazené kolekce členů:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Můžete také poskytnout podobný dekonstrukci pro libovolný typ v rozhraní .NET. Napíšete metodu `Deconstruct` jako člena třídy. Tato metoda `Deconstruct` poskytuje sadu `out` argumentů pro každou z vlastností, které chcete extrahovat. Zvažte tuto `Point` třídu, která poskytuje metodu dekonstruktoru, která extrahuje souřadnice `X` a `Y`:

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Jednotlivá pole můžete extrahovat přiřazením `Point` k řazené kolekci členů:

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Podrobnější informace o řazených kolekcích členů najdete v [článku o řazených kolekcích členů](../tuples.md).

## <a name="discards"></a>Zahození

Často při dekonstrukci řazené kolekce členů nebo volání metody s parametry `out` jste nuceni definovat proměnnou, jejíž hodnotu nezáleží na a nehodláte ji používat. C#Přidá podporu pro *zahození* pro zpracování tohoto scénáře. Zahození je proměnná, která je jen pro zápis, jejíž název je `_` (znak podtržítka); můžete přiřadit všechny hodnoty, které mají být zahozeny do jedné proměnné. Zahození je jako Nepřiřazená proměnná; Kromě příkazu přiřazení nelze zrušit použití v kódu.

Zahození jsou podporovaná v následujících scénářích:

- Při dekonstrukci řazených kolekcí členů nebo uživatelsky definovaných typů.
- Při volání metod s [výstupními](../language-reference/keywords/out-parameter-modifier.md) parametry.
- V operaci porovnávání vzorů s příkazy [is](../language-reference/keywords/is.md) a [Switch](../language-reference/keywords/switch.md) .
- Jako samostatný identifikátor, pokud chcete explicitně identifikovat hodnotu přiřazení jako zahození.

Následující příklad definuje metodu `QueryCityDataForYears`, která vrací 6 – řazenou kolekci členů obsahující data města pro dva různé roky. Volání metody v příkladu se týká pouze dvou hodnot naplnění vrácených metodou, takže poběží zbývající hodnoty v řazené kolekci členů jako zahození při dekonstrukci řazené kolekce členů.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Další informace najdete v tématu [zahození](../discards.md).

## <a name="pattern-matching"></a>Porovnávání vzorů

*Porovnávání vzorů* je funkce, která umožňuje implementovat odeslání metody pro jiné vlastnosti než typ objektu. V závislosti na typu objektu již pravděpodobně znáte způsob odeslání metody. V objektově orientovaném programování metody Virtual a override poskytují jazykovou syntaxi pro implementaci metody odeslání na základě typu objektu. Základní a odvozené třídy poskytují různé implementace.
Výrazy pro porovnávání vzorů přesahují tento koncept, takže můžete snadno implementovat podobné vzory odeslání pro typy a datové prvky, které nesouvisí s hierarchií dědičnosti.

Porovnávání vzorů podporuje `is` výrazy a `switch` výrazy. Každá z nich umožňuje kontrolu objektu a jeho vlastností, aby bylo možné určit, zda tento objekt splňuje požadovaný vzor. Pomocí klíčového slova `when` můžete určit další pravidla pro vzor.

Výraz `is` Pattern rozšiřuje známý [`is` operátor](../language-reference/keywords/is.md#pattern-matching-with-is) pro dotazování objektu na jeho typ a přiřazení výsledku do jedné instrukce. Následující kód zkontroluje, zda je proměnná `int`a v případě potřeby ji přidá k aktuálnímu součtu:

```csharp
if (input is int count)
    sum += count;
```

Předchozí malý příklad ukazuje vylepšení výrazu `is`. Můžete testovat proti typům hodnot i odkazovým typům a k nové proměnné správného typu můžete přiřadit úspěšný výsledek.

Výraz porovnávání přepínačů má známou syntaxi na základě příkazu `switch`, který již je C# součástí jazyka. Aktualizovaný příkaz switch má několik nových konstrukcí:

- Typ řízení výrazu `switch` již není omezen na celočíselné typy, `Enum` typy, `string`nebo typ s možnou hodnotou null, který odpovídá jednomu z těchto typů. Může být použit libovolný typ.
- Můžete testovat typ `switch` výraz v každém `case` popisku. Stejně jako u výrazu `is` lze k tomuto typu přiřadit novou proměnnou.
- Můžete přidat klauzuli `when` pro další podmínky testování v této proměnné.
- Pořadí popisků `case` je teď důležité. První větev, která se má porovnat, se spustí; ostatní se přeskočí.

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

- `case 0:` je známý konstantní vzor.
- `case IEnumerable<int> childSequence:` je vzor typu.
- `case int n when n > 0:` je vzor typu s další podmínkou `when`.
- `case null:` je vzor hodnoty null.
- `default:` je známý výchozí případ.

Další informace o porovnávání vzorů najdete ve vzorovém [porovnávání C#v ](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Místní a návratové hodnoty REF

Tato funkce umožňuje algoritmy, které používají a vracejí odkazy na proměnné definované jinde. Jeden příklad pracuje s velkými maticemi a hledá jedno umístění s určitými charakteristikami. Následující metoda vrátí **odkaz** na toto úložiště v matici:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Můžete deklarovat návratovou hodnotu jako `ref` a upravit tuto hodnotu v matici, jak je znázorněno v následujícím kódu:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

C# Jazyk obsahuje několik pravidel, která vás chrání před nepoužitými `ref` místními a vrací:

- Do signatury metody a do všech příkazů `return` v metodě je nutné přidat klíčové slovo `ref`.
  - Tím se vymaže metoda, kterou vrátí odkaz v rámci této metody.
- `ref return` může být přiřazena proměnné hodnot nebo proměnné `ref`.
  - Volající řídí, zda je vrácená hodnota zkopírována nebo ne. Vynechání modifikátoru `ref` při přiřazování návratové hodnoty znamená, že volající chce kopii hodnoty, nikoli odkaz na úložiště.
- Nemůžete přiřadit návratovou hodnotu standardní metody k `ref` místní proměnné.
  - Která nepovoluje příkazy jako `ref int i = sequence.Count();`
- Nemůžete vrátit `ref` proměnné, jejíž doba života nepřesahuje po provedení metody.
  - To znamená, že nemůžete vrátit odkaz na místní proměnnou nebo proměnnou s podobným oborem.
- `ref` lokální hodnoty a vrácení nelze použít s asynchronními metodami.
  - Kompilátor nemůže zjistit, zda se odkazovaná proměnná nastavila na konečnou hodnotu, když vrátí asynchronní metoda.

Přidání místních a návratových odkazů umožňuje algoritmy, které jsou efektivnější, protože se vyhnete kopírování hodnot nebo provádění operací zrušení odkazování vícekrát.

Přidání `ref` do návratové hodnoty je [Změna kompatibilní se zdrojem](version-update-considerations.md#source-compatible-changes). Existující kód je zkompilován, ale návratová hodnota REF je při přiřazení zkopírována. Volající musí aktualizovat úložiště pro návratovou hodnotu na `ref` místní proměnná pro uložení návratu jako odkazu.

Další informace najdete v článku věnovaném [klíčovému slovu ref](../language-reference/keywords/ref.md) .

## <a name="local-functions"></a>Lokální funkce

Mnoho návrhů pro třídy obsahuje metody, které jsou volány pouze z jednoho umístění. Tyto další privátní metody udržují jednotlivé metody malé a prioritní. *Místní funkce* umožňují deklarovat metody v kontextu jiné metody. Místní funkce usnadňují čtenářům třídy, aby bylo vidět, že místní metoda je volána pouze z kontextu, ve kterém je deklarována.

Existují dva běžné případy použití pro místní funkce: veřejné metody iterátoru a veřejné asynchronní metody. Oba typy metod generují kód, který hlásí chyby později než programátoři mohou očekávat. V metodách iterátoru jsou všechny výjimky pozorovány pouze při volání kódu, který vytvoří výčet vrácené sekvence. V asynchronních metodách jsou jakékoli výjimky pozorovány pouze v případě, že je očekáváno vrácení `Task`. Následující příklad ukazuje oddělení ověřování parametrů z implementace iterátoru pomocí místní funkce:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Stejný postup lze použít s metodami `async`, aby bylo zajištěno, že výjimky vznikající z ověřování argumentu jsou vyvolány před zahájením asynchronní práce:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Některé z návrhů, které jsou podporovány místními funkcemi, by mohly být také provedeny pomocí *výrazů lambda*. Další informace naleznete v tématu [místní funkce vs. výrazy lambda](../local-functions-vs-lambdas.md).

## <a name="more-expression-bodied-members"></a>Další členové Expression-těle

C#6 zavedlo [členy Expression-těle](csharp-6.md#expression-bodied-function-members) pro členské funkce a vlastnosti jen pro čtení. C#7,0 rozšíří povolené členy, které mohou být implementovány jako výrazy. V C# 7,0 můžete implementovat *konstruktory*, *finalizační metody*a `get` a `set` přistupující objekty do *vlastností* a *indexerů*. Následující kód ukazuje příklady jednotlivých:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Tento příklad nepotřebuje finalizační metodu, ale je zobrazený k předvedení syntaxe. V třídě byste neměli implementovat finalizační metodu, pokud není nutné vydávat nespravované prostředky. Měli byste také zvážit použití třídy <xref:System.Runtime.InteropServices.SafeHandle> namísto přímého spravování nespravovaných prostředků.

Tato nová umístění pro členy Expression-těle reprezentují důležitý milník pro C# jazyk: tyto funkce byly implementovány členy komunity, kteří pracují na open source projektu [Roslyn](https://github.com/dotnet/Roslyn) .

Změna metody na člen výrazu těle je [binární kompatibilní změna](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Výrazy throw

V C#`throw` byl vždy příkaz. Vzhledem k tomu, že `throw` je příkaz, nikoli výraz, C# byly zde konstrukce, kde je nemůžete použít. Tyto zahrnuté podmíněné výrazy, null slučovací výrazy a některé lambda výrazy. Přidání členů Expression-těle přidá více míst, kde by mohly být užitečné `throw` výrazy. Takže můžete napsat libovolný z těchto konstrukcí, C# 7,0 zavádí [*výrazy throw*](../language-reference/keywords/throw.md#the-throw-expression).

Díky tomu je snazší psát další kód založený na výrazu. Pro kontrolu chyb nepotřebujete další příkazy.

## <a name="generalized-async-return-types"></a>Generalizované asynchronní návratové typy

Vrácení `Task` objektu z asynchronních metod může způsobit kritické body výkonu v určitých cestách. `Task` je odkazový typ, takže jeho použití znamená přidělení objektu. V případech, kdy metoda deklarovaná s modifikátorem `async` vrací výsledek uložený v mezipaměti nebo je dokončena synchronně, se další přidělení můžou stát značnými náklady v částech kritického výkonu v kódu. Pokud dojde k přidělení v těsných smyčkách, může to být nákladné.

Nová funkce jazyka znamená, že návratové typy asynchronní metody nejsou omezeny na `Task`, `Task<T>`a `void`. Vrácený typ musí stále splňovat asynchronní vzorek, což znamená, že metoda `GetAwaiter` musí být přístupná. Jako jeden konkrétní příklad byl do rozhraní .NET Framework přidán `ValueTask` typ, aby bylo možné používat tuto novou jazykovou funkci:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> Chcete-li použít typ <xref:System.Threading.Tasks.ValueTask%601>, je nutné přidat balíček NuGet [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) .

Toto vylepšení je nejužitečnější pro autory knihovny, aby nedošlo k přidělení `Task` v kódu kritickém pro výkon.

## <a name="numeric-literal-syntax-improvements"></a>Vylepšení syntaxe numerického literálu

Nepřečtené číselné konstanty mohou ztížit pochopení kódu při prvním čtení. Bitové masky nebo jiné symbolické hodnoty jsou náchylné k nepochopení. C#7,0 obsahuje dvě nové funkce pro zápis čísel v nejčitelnějším způsobu pro zamýšlené použití: *binární literály*a *oddělovače číslic*.

V případech, kdy vytváříte bitové masky, nebo pokaždé, když binární reprezentace čísla provede Nejčitelnější kód, zapište toto číslo v binárním formátu:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

`0b` na začátku konstanty označuje, že číslo je zapsáno jako binární číslo. Binární čísla mohou být dlouhá, takže je často snazší zobrazit bitové vzory pomocí `_` jako oddělovač číslic, jak je uvedeno výše v binární konstantě. Oddělovač číslic se může objevit kdekoli v konstantě. U základních 10 čísel je běžné ji použít jako oddělovač tisíců:

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Oddělovač číslic lze použít s typy `decimal`, `float`a `double`:

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Společně můžete deklarovat číselné konstanty s mnohem větší čitelností.
