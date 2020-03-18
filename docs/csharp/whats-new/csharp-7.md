---
title: Co je nového v C# 7.0 - C# Průvodce
description: Získejte přehled o nových funkcích ve verzi 7.0 jazyka C#.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: a6ac5c00ceb2ce8e5e56e2a86a8cde937d5108e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399691"
---
# <a name="whats-new-in-c-70"></a>Co je nového v jazyce C# 7.0

C# 7.0 přidá do jazyka C# řadu nových funkcí:

- [`out`Proměnné](#out-variables)
  - Hodnoty vuvedené jako argumenty můžete deklarovat `out` jako argumenty pro metodu, kde se používají.
- [Záznamů](#tuples)
  - Můžete vytvořit zjednodušené, nepojmenované typy, které obsahují více veřejných polí. Kompilátory a nástroje IDE pochopit sémantiku těchto typů.
- [Zahození](#discards)
  - Zahození jsou dočasné proměnné pouze pro zápis používané v přiřazeních, pokud se nestaráte o přiřazenou hodnotu. Jsou nejužitečnější při deconstructing řazené kolekce členů a uživatelem definované typy, stejně jako při volání metody s `out` parametry.
- [Porovnávání](#pattern-matching)
  - Můžete vytvořit logiku větvení na základě libovolných typů a hodnot členů těchto typů.
- [`ref`místní obyvatelé a vrací](#ref-locals-and-returns)
  - Metoda místní proměnné a vrácené hodnoty mohou být odkazy na jiné úložiště.
- [Místní funkce](#local-functions)
  - Můžete vnořit funkce uvnitř jiných funkcí omezit jejich rozsah a viditelnost.
- [Více členů s výrazovým tělem](#more-expression-bodied-members)
  - Seznam členů, které lze vytvářet pomocí výrazů, se rozrostl.
- [`throw`Výrazy](#throw-expressions)
  - Můžete vyvolat výjimky v konstrukcích kódu, které `throw` dříve nebyly povoleny, protože byl příkaz.
- [Generalizované asynchronní návratové typy](#generalized-async-return-types)
  - Metody deklarované pomocí modifikátoru `async` mohou kromě `Task` a `Task<T>`.
- [Číselná vylepšení syntaxe literálu](#numeric-literal-syntax-improvements)
  - Nové tokeny zlepšují čitelnost pro číselné konstanty.

Zbývající část tohoto článku obsahuje přehled jednotlivých funkcí. U každé funkce se dozvíte důvody, které za ní stojí. Naučíte se syntaxi. Tyto funkce můžete prozkoumat ve `dotnet try` vašem prostředí pomocí globálního nástroje:

1. Nainstalujte globální nástroj [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)
1. Klonovat úložiště [dotnet/try-samples.](https://github.com/dotnet/try-samples)
1. Nastavte aktuální adresář do podadresáře *csharp7* pro úložiště *try-samples.*
1. Spusťte `dotnet try`.

## <a name="out-variables"></a>`out`Proměnné

V této verzi `out` byla vylepšena existující syntaxe, která podporuje parametry. Nyní můžete `out` deklarovat proměnné v seznamu argumentů volání metody, spíše než psát prohlášení samostatné deklarace:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Můžete chtít zadat typ `out` proměnné pro přehlednost, jak je znázorněno výše. Jazyk však podporuje použití implicitně zadané místní proměnné:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- Kód je čitelnější.
  - Deklarujete out proměnnou tam, kde ji používáte, nikoli na jiném výše uvedeném řádku.
- Není třeba přiřazovat počáteční hodnotu.
  - Deklarováním `out` proměnné, kde se používá ve volání metody, nelze omylem použít před přiřazením.

## <a name="tuples"></a>N-tice

C# poskytuje bohatou syntaxi pro třídy a struktury, který se používá k vysvětlení záměru návrhu. Ale někdy, že bohatá syntaxe vyžaduje další práci s minimálním přínosem. Často může psát metody, které potřebují jednoduchou strukturu obsahující více než jeden datový prvek. Pro podporu těchto scénářů byly přidány *řazené kolekce členů* do jazyka C#. Řazené kolekce členů jsou zjednodušené datové struktury, které obsahují více polí představujících datové členy.
Pole nejsou ověřena a nelze definovat vlastní metody.

> [!NOTE]
> Řazené kolekce členů byly k dispozici před C# 7.0, ale byly neefektivní a neměl žádnou jazykovou podporu.
> To znamenalo, že prvky řazené kolekce členů lze odkazovat pouze jako `Item1`, `Item2` a tak dále. C# 7.0 zavádí jazykovou podporu pro řazené kolekce členů, který umožňuje sémantické názvy pro pole řazené kolekce členů pomocí nové, efektivnější řazené kolekce členů.

Řazenou skupinu členů můžete vytvořit přiřazením hodnoty každému členovi a volitelně poskytnutím sémantických názvů každému členovi řazené kolekce členů:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

Řazená `namedLetters` kolekce členů `Alpha` `Beta`obsahuje pole označovaná jako a . Tyto názvy existují pouze v době kompilace a nejsou zachovány, například při kontrole řazené kolekce členů pomocí reflexe za běhu.

V přiřazení řazené kolekce členů můžete také zadat názvy polí na pravé straně přiřazení:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Může být časy, kdy chcete zrušit balíček členy řazené kolekce členů, které byly vráceny z metody.  Můžete to provést deklarováním samostatných proměnných pro každou z hodnot v řazené kolekce členů. Toto odbalování se nazývá *deconstructing* řazené kolekce členů:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Můžete také poskytnout podobnou dekonstrukci pro libovolný typ v rozhraní .NET. Napíšete `Deconstruct` metodu jako člen třídy. Tato `Deconstruct` metoda poskytuje `out` sadu argumentů pro každou z vlastností, které chcete extrahovat. Zvažte `Point` tuto třídu, která poskytuje deconstructor metoda, která extrahuje `X` a `Y` souřadnice:

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Jednotlivá pole můžete extrahovat `Point` přiřazením řazené kolekce členů:

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Další informace o řazených kolekcích členů se dozvíte podrobněji v [článku n-tic](../tuples.md).

## <a name="discards"></a>Zahození

Často při deconstructing řazené `out` kolekce členů nebo volání metody s parametry, jste nuceni definovat proměnnou, jejíž hodnotu nezajímáte a nemají v úmyslu použít. C# přidá podporu pro *zahození* pro zpracování tohoto scénáře. Zahození je proměnná pouze `_` pro zápis, jejíž název je (znak podtržítka); můžete přiřadit všechny hodnoty, které chcete zahodit k jedné proměnné. Výmět je jako nepřiřazená proměnná; kromě příkazu přiřazení nelze zahodit použít v kódu.

Zahození jsou podporovány v následujících scénářích:

- Při dekonstrukci řazené kolekce členů nebo uživatelem definované typy.
- Při volání metod s [out](../language-reference/keywords/out-parameter-modifier.md) parametry.
- V operaci porovnávání vzorů s příkazy [is](../language-reference/keywords/is.md) a [switch.](../language-reference/keywords/switch.md)
- Jako samostatný identifikátor, pokud chcete explicitně identifikovat hodnotu přiřazení jako zahození.

Následující příklad definuje `QueryCityDataForYears` metodu, která vrací 6 řazené kolekce členů, která obsahuje data pro město pro dva různé roky. Volání metody v příkladu se týká pouze dvě hodnoty základního souboru vrácené metodou a tak zachází zbývající hodnoty v řazené kolekce členů jako zahodí při deconstructs řazené kolekce členů.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Další informace naleznete [v tématu Discards](../discards.md).

## <a name="pattern-matching"></a>Porovnávání vzorů

*Porovnávání vzorů* je funkce, která umožňuje implementovat odeslání metody na vlastnosti než typ objektu. Pravděpodobně jste již obeznámeni s odesláním metody na základě typu objektu. V objektově orientovaném programování poskytují metody virtual a override syntaxi pro implementaci dispečerské metody založené na typu objektu. Základní a odvozené třídy poskytují různé implementace.
Vzor odpovídající výrazy rozšířit tento koncept tak, aby můžete snadno implementovat podobné vzorky odeslání pro typy a datové prvky, které nesouvisejí prostřednictvím hierarchie dědičnosti.

Porovnávání `is` vzorů podporuje `switch` výrazy a výrazy. Každý umožňuje kontrolu objektu a jeho vlastnosti k určení, pokud tento objekt splňuje požadovaný vzor. `when` Klíčové slovo slouží k určení dalších pravidel vzoru.

Výraz `is` vzoru rozšiřuje známý [ `is` operátor](../language-reference/keywords/is.md#pattern-matching-with-is) k dotazování objektu o jeho typu a přiřazení výsledku v jedné instrukci. Následující kód zkontroluje, zda `int`je proměnná , a pokud ano, přidá ji k aktuálnímu součtu:

```csharp
if (input is int count)
    sum += count;
```

Předchozí malý příklad ukazuje vylepšení výrazu. `is` Můžete testovat proti typy hodnot, jakož i typy odkazů a můžete přiřadit úspěšný výsledek nové proměnné správného typu.

Výraz shody přepínače má známou `switch` syntaxi založenou na příkazu, který je již součástí jazyka C#. Příkaz aktualizovaný přepínač má několik nových konstrukcí:

- Řídící typ výrazu `switch` již není omezen na `Enum` integrální typy, `string`typy nebo typ s možnou hodnotou null odpovídající jednomu z těchto typů. Lze použít libovolný typ.
- Můžete otestovat typ `switch` výrazu `case` v každém popisku. Stejně `is` jako u výrazu můžete tomuto typu přiřadit novou proměnnou.
- Můžete přidat `when` klauzuli k dalšímu testování podmínek na tuto proměnnou.
- Pořadí štítků `case` je nyní důležité. První větev, která má odpovídat, je spuštěna; ostatní jsou přeskočeny.

Následující kód ukazuje tyto nové funkce:

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
- `case int n when n > 0:`je vzor typu s `when` další podmínkou.
- `case null:`je vzor null.
- `default:`je známé výchozí případ.

Další informace o porovnávání vzorů v [porovnání vzorů v c#](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Ref místní obyvatelé a vrací

Tato funkce umožňuje algoritmy, které používají a vracejí odkazy na proměnné definované jinde. Jedním z příkladů je práce s velkými maticemi a nalezení jednoho místa s určitými vlastnostmi. Následující metoda vrátí **odkaz** na toto úložiště v matici:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Můžete deklarovat vrácenou `ref` hodnotu jako a upravit tuto hodnotu v matici, jak je znázorněno v následujícím kódu:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

Jazyk C# má několik pravidel, která vás `ref` chrání před zneužitím místních obyvatel a vrátí:

- Klíčové `ref` slovo je nutné přidat k `return` podpisu metody a ke všem příkazům v metodě.
  - To jasně ukazuje, metoda vrátí odkazem v celé metodě.
- A `ref return` může být přiřazena k `ref` proměnné hodnoty nebo proměnné.
  - Volající určuje, zda je vrácená hodnota zkopírována nebo ne. Vynechání modifikátor při `ref` přiřazování vrácená hodnota označuje, že volající chce kopii hodnoty, nikoli odkaz na úložiště.
- Standardní metodu nelze přiřadit `ref` k místní proměnné.
  - Že zamítá prohlášení jako`ref int i = sequence.Count();`
- Nelze vrátit `ref` proměnné, jejíž životnost nepřesahuje provádění metody.
  - To znamená, že nelze vrátit odkaz na místní proměnnou nebo proměnnou s podobným rozsahem.
- `ref`místní a vrácení nelze použít s asynchronní metody.
  - Kompilátor nemůže vědět, pokud byla odkazovaná proměnná nastavena na konečnou hodnotu, když se vrátí asynchronní metoda.

Přidání ref locals a ref vrátí umožňuje algoritmy, které jsou efektivnější tím, že zabrání kopírování hodnot nebo provádění dereferencing operace vícekrát.

Přidání `ref` k vrácené hodnotě je [změna kompatibilní se zdrojem](version-update-considerations.md#source-compatible-changes). Existující kód se zkompiluje, ale vrácená hodnota ref je zkopírována při přiřazení. Volající musí aktualizovat úložiště pro vrácenou `ref` hodnotu na místní proměnnou, aby bylo vráceno jako odkaz.

Další informace naleznete v článku [klíčového slova ref.](../language-reference/keywords/ref.md)

## <a name="local-functions"></a>Lokální funkce

Mnoho návrhů pro třídy obsahuje metody, které jsou volány pouze z jednoho umístění. Tyto další soukromé metody udržují každou metodu malou a zaměřenou. *Místní funkce* umožňují deklarovat metody v kontextu jiné metody. Místní funkce usnadňují čtenářům třídy vidět, že místní metoda je volána pouze z kontextu, ve kterém je deklarována.

Existují dva běžné případy použití pro místní funkce: metody veřejného iterátoru a veřejné asynchronní metody. Oba typy metod generují kód, který hlásí chyby později, než mohou programátoři očekávat. V metodách iterátoru jsou všechny výjimky pozorovány pouze při volání kódu, který vyjmenovává vrácenou sekvenci. V asynchronních metodách jsou všechny výjimky pozorovány pouze v případě, že je očekáváno vrácené. `Task` Následující příklad ukazuje oddělení ověření parametru od implementace iterátoru pomocí místní funkce:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Stejnou techniku lze `async` použít s metodami, které zajišťují, že výjimky vyplývající z ověření argumentu jsou vyvolány před zahájením asynchronní práce:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Některé návrhy, které jsou podporovány místními funkcemi, lze také provést pomocí *výrazů lambda*. Další informace naleznete [v tématu Místní funkce vs. lambda výrazy](../local-functions-vs-lambdas.md).

## <a name="more-expression-bodied-members"></a>Více členů s výrazovým tělem

C# 6 představil [výraz tělo členy](csharp-6.md#expression-bodied-function-members) pro členské funkce a vlastnosti jen pro čtení. C# 7.0 rozbalí povolené členy, které mohou být implementovány jako výrazy. V c# 7.0 můžete implementovat *konstruktory*, `get` `set` *finalizační metody*a přístupové objekty na *vlastnosti* a *indexery*. Následující kód ukazuje příklady každého z nich:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Tento příklad nepotřebuje finalizační metodu, ale je zobrazen k předvedení syntaxe. Ve své třídě byste neměli implementovat finalizační metodu, pokud není nutné uvolnit nespravované prostředky. Měli byste také <xref:System.Runtime.InteropServices.SafeHandle> zvážit použití třídy namísto přímé správy nespravovaných prostředků.

Tato nová umístění pro členy s výrazem představují důležitý milník pro jazyk C#: Tyto funkce byly implementovány členy komunity pracujícími na projektu [Roslyn](https://github.com/dotnet/Roslyn) s otevřeným zdrojovým kódem.

Změna metody na člen výrazu je [binární kompatibilní změna](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Výrazy throw

V C#, `throw` byl vždy prohlášení. Protože `throw` je příkaz, nikoli výraz, byly c# konstrukce, kde nelze použít. Mezi ně patřily podmíněné výrazy, nulové slučující výrazy a některé výrazy lambda. Přidání členů s výrazem přidá další `throw` umístění, kde výrazy by bylo užitečné. Tak, že můžete napsat některý z těchto konstrukcí, C# 7.0 zavádí [*vyvolat výrazy*](../language-reference/keywords/throw.md#the-throw-expression).

Toto přidání usnadňuje psaní kódu založeného na výrazu. Nepotřebujete další příkazy pro kontrolu chyb.

## <a name="generalized-async-return-types"></a>Generalizované asynchronní návratové typy

Vrácení objektu `Task` z asynchronních metod může zavést kritické body výkonu v určitých cestách. `Task`je typ odkazu, takže jeho použití znamená přidělení objektu. V případech, kdy metoda `async` deklarovaná s modifikátorem vrátí výsledek v mezipaměti nebo dokončí synchronně, může se mimořádná přidělení stát významnými časovými náklady v částech kódu kritických pro výkon. Může být nákladné, pokud se tyto alokace vyskytují v těsných smyčkách.

Nová funkce jazyka znamená, že návratové typy `Task`asynchronní metody nejsou omezeny na , `Task<T>`a `void`. Vrácený typ musí stále splňovat asynchronní vzorek, což znamená, že `GetAwaiter` metoda musí být přístupná. Jako jeden konkrétní `ValueTask` příklad byl typ přidán do rozhraní .NET, aby bylo dosaženo této nové funkce jazyka:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> Je třeba přidat Balíček [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet, <xref:System.Threading.Tasks.ValueTask%601> aby bylo možné použít typ.

Toto vylepšení je nejužitečnější pro autory `Task` knihovny, aby se zabránilo přidělení v kritickém výkonu kódu.

## <a name="numeric-literal-syntax-improvements"></a>Číselná vylepšení syntaxe literálu

Nesprávné čtení číselných konstant může ztížit pochopení kódu při prvním čtení. Bitové masky nebo jiné symbolické hodnoty jsou náchylné k nedorozumění. C# 7.0 obsahuje dvě nové funkce pro zápis čísel nejčitelnějším způsobem pro zamýšlené použití: *binární literály*a *oddělovače číslic*.

Pro ty časy, kdy vytváříte bitové masky nebo kdykoli binární reprezentace čísla vytvoří nejčitelnější kód, napište toto číslo do binárního souboru:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

Na `0b` začátku konstanty označuje, že číslo je zapsáno jako binární číslo. Binární čísla mohou být dlouhá, takže je často snazší vidět `_` bitové vzory zavedením oddělovače číslic, jak je znázorněno výše v binární konstantě. Oddělovač číslic se může objevit kdekoli v konstantě. Pro základní 10 čísel, je běžné použít jako oddělovač tisíců:

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Oddělovač číslic lze `decimal`použít `float`také `double` s , a typy:

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Dohromady můžete deklarovat číselné konstanty s mnohem větší čitelností.
