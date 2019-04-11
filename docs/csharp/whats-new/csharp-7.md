---
title: Co je nového v jazyce C# 7.0 – průvodce v C#
description: Získejte přehled o nové funkce ve verzi 7.0 C# jazyka.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 69e32bf6aae0da15c23e8f08da8c2bb9e3d3456e
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481298"
---
# <a name="whats-new-in-c-70"></a>Co je nového v jazyce C# 7.0

C# 7.0 přidá několik nových funkcí jazyka C#:
* [`out` proměnné](#out-variables)
  - Je možné deklarovat `out` hodnoty inline jako argumentů metody, které používají.
* [N-tice](#tuples)
  - Můžete vytvořit jednoduchý, Nepojmenované typy, které obsahují více veřejná pole. Kompilátory a nástroje pro prostředí IDE pochopit sémantiku z těchto typů.
* [Zahození](#discards)
  - Zahození jsou dočasné, jen pro zápis proměnné při nezáleží hodnota přiřazená v přiřazeních. Jsou nejužitečnější tehdy, když dekonstrukce řazených kolekcí členů a uživatelem definovaných typů, stejně jako při volání metody s `out` parametry.
* [Porovnávání vzorů](#pattern-matching)
  - Můžete vytvořit na základě libovolné typy a hodnoty členů z těchto typů logiky větvení.
* [`ref` místní hodnoty a vrátí](#ref-locals-and-returns)
  - Metoda lokálních proměnných a návratovými hodnotami může být odkazy na další úložiště.
* [Lokální funkce](#local-functions)
  - Je možné vnořovat funkce do jiných funkcí a omezit jejich rozsah a viditelnost.
* [Více členů s výrazem v těle](#more-expression-bodied-members)
  - Seznam členů, které mohou být vytvořeny pomocí výrazů zvětšil na velikost.
* [`throw` Výrazy](#throw-expressions)
  - Může vyvolat výjimky v konstruktorech kódu, které dříve nebyly povoleny, protože `throw` byl příkaz.
* [Zobecněný asynchronní návratové typy](#generalized-async-return-types)
  - Metody deklarované s `async` modifikátor může vrátit jiné typy kromě `Task` a `Task<T>`.
* [Vylepšení číselný literál syntaxe](#numeric-literal-syntax-improvements)
  - Nové tokeny zlepšit čitelnost pro číselné konstanty.

Zbývající část tohoto článku poskytuje přehled o jednotlivých funkcí. Pro jednotlivé funkce dozvíte zdůvodnění. Dozvíte syntaxe. Můžete prozkoumat tyto funkce v naší [interaktivní zkoumání](../tutorials/exploration/csharp-7.yml) z těchto funkcí.

## <a name="out-variables"></a>`out` Proměnné

Existující syntaxi, která podporuje `out` v této verzi jsme vylepšili parametry. Nyní můžete deklarovat `out` proměnných v seznamu argumentů volání metody místo psaní příkazu samostatné deklarace:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Možná budete chtít zadat typ `out` proměnné pro přehlednost, jak je znázorněno výše. Však jazyk podporuje použití implicitně typovaná lokální proměnná:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

* Kód je lépe čitelný.
  - Deklarujete proměnnou mimo, kde má být použito, ne na další řádek výše.
* Už není potřeba přiřadit počáteční hodnotu.
  - Deklarací `out` proměnné, kde se používá ve volání metody, nemůžete použít omylem ho dřív, než je přiřadí.

## <a name="tuples"></a>N-tice

C# poskytuje bohaté syntaxi pro třídy a struktury, které slouží k vysvětlení máte v úmyslu návrhu. Ale někdy bohaté syntaxe vyžaduje další práci s minimálními výhodu. Často může zapisovat metody, které vyžadují jednoduchou strukturu obsahující více než jeden datový prvek. Pro podporu těchto scénářů *řazených kolekcí členů* byly přidány do jazyka C#. Řazené kolekce členů jsou jednoduché datové struktury, které obsahují více polí k reprezentaci datové členy.
Pole pořadí úloh se neověřuje, a nelze definovat vlastní metody

> [!NOTE]
> Řazené kolekce členů byly k dispozici před C# 7.0, ale bylo neefektivní a měl neexistuje jazyková podpora.
> To znamená, že elementů řazené kolekce členů mohou být odkazovány pouze jako `Item1`, `Item2` a tak dále. C# 7.0 zavádí podporu jazyka pro řazené kolekce členů, umožňující sémantické názvy polí pomocí nové, efektivnější řazené kolekce členů typy řazené kolekce členů.

Řazená kolekce členů můžete vytvořit přiřazení hodnoty k jednotlivým členům a volitelně poskytuje sémantické názvy pro každého člena řazené kolekce členů:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

`namedLetters` Řazené kolekce členů obsahuje pole, které jsou označovány jako `Alpha` a `Beta`. Tyto názvy existují pouze v době kompilace a nejsou zachovány, například při kontrole řazené kolekce členů v době běhu pomocí operace reflection.

V přiřazení řazené kolekce členů můžete také zadat názvy polí na pravé straně přiřazení:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Může nastat situace, kdy budete chtít rozbalit členy řazené kolekce členů, které byly vráceny z metody.  Můžete to udělat deklarací samostatné proměnných pro všechny hodnoty řazené kolekce členů. Tato rozbalení se nazývá *dekonstrukce* řazené kolekce členů:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Můžete také zadat podobné dekonstrukce pro jakýkoli typ v rozhraní .NET. Při psaní `Deconstruct` metoda jako člen třídy. Že `Deconstruct` metoda poskytuje sadu `out` argumenty pro každou z vlastností, které mají být extrahovány. Zvažte proto `Point` třída, která poskytuje deconstructor metodu, která extrahuje `X` a `Y` souřadnice:

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Můžete extrahovat jednotlivá pole pomocí přiřazení `Point` k řazené kolekce členů:

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Další podrobnosti v o řazenými kolekcemi členů v [řazených kolekcí členů článku](../tuples.md).

## <a name="discards"></a>Zahození

Při často dekonstrukce řazené kolekce členů nebo volání metody s `out` parametry, budete muset definovat proměnnou jehož hodnota nezáleží a používat. C# přidává podporu pro *zahodí* tohoto scénáře. Zahození je proměnná jen pro zápis, jehož název je `_` (podtržítko); můžete přiřadit všechny hodnoty, které máte v úmyslu zahodit do jedné proměnné. Zahození je stejná jako nepřiřazené proměnné. Kromě příkazu přiřazení nelze použít zahození v kódu.

Zahození jsou podporovány v následujících scénářích:

* Když dekonstrukce řazených kolekcí členů nebo uživatelem definované typy.
* Při volání metody s [si](../language-reference/keywords/out-parameter-modifier.md) parametry.
* Ve vzorku s odpovídajícím operaci s [je](../language-reference/keywords/is.md) a [přepnout](../language-reference/keywords/switch.md) příkazy.
* Pokud chcete explicitně Identifikujte jako samostatné identifikátor hodnotu přiřazení jako zahození.

Následující příklad definuje `QueryCityDataForYears` metodu, která vrátí 6-n-tice, která obsahuje data pro město pro dvě různé roky. Volání metody v příkladu se týká pouze s hodnotami dva naplnění vrácený metodou a proto zpracuje zbývající hodnoty řazené kolekce členů jako zahodí při deconstructs řazené kolekce členů.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Další informace najdete v tématu [zahodí](../discards.md).

## <a name="pattern-matching"></a>Porovnávání vzorů

*Porovnávání vzorů* je funkce, která umožňuje implementovat metodu odeslání na vlastnosti jiné než typu objektu. Už pravděpodobně již znáte odesílání metodu na základě typu objektu. Objektově orientované programování, virtuální a přepsání metody poskytují syntaxe jazyka pro implementaci metody odesílání na základě typu objektu. Základní a odvozené třídy poskytují tak různé implementace.
Výrazy odpovídající vzor rozšiřte tento koncept tak, že je možné snadno implementovat podobné vzory odeslání pro typy a datové prvky, které spolu nesouvisí prostřednictvím hierarchie dědičnosti.

Porovnávání vzorů podporuje `is` výrazy a `switch` výrazy. Každý umožňuje kontrolu objektu a vlastností určíte, pokud daný objekt splňuje hledané kombinaci vzoru. Můžete použít `when` – klíčové slovo lze určit další pravidla se vzorem.

`is` Výraz vzoru rozšiřuje známé [ `is` operátor](../language-reference/keywords/is.md#pattern-matching-with-is) pro dotazování objekt o její typ a přiřadit výsledek v jedné instrukce. Následující kód ověří, zda proměnná `int`a pokud ano, přidá jej do aktuálního součet:

```csharp
if (input is int count)
    sum += count;
```

Ukazuje předchozí příklad malá vylepšení `is` výrazu. Můžete otestovat s typy hodnot, jakož i typy odkazů a přiřadíte úspěšný výsledek do nové proměnné nesprávného typu.

Má známou syntaxi, na základě shody výraz přepínače `switch` příkaz již součástí C# jazyka. Příkaz aktualizované switch má několik nové konstruktory:

- Celopodnikové typu `switch` výrazu už není omezené na integrální typy `Enum` typy, `string`, nebo typ připouštějící hodnotu Null odpovídá jedné z těchto typů. Libovolný typ může použít.
- Můžete otestovat typu `switch` výrazu v každém `case` popisek. Stejně jako u `is` výrazu, může přiřadit novou proměnnou typu.
- Můžete přidat `when` klauzuli pro další testování podmínek na tuto proměnnou.
- Pořadí `case` popisků je důležité. První větev tak, aby odpovídaly je spuštěn; ostatní se přeskočí.

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

- `case 0:` je známé konstantní vzorek.
- `case IEnumerable<int> childSequence:` je typ modelu.
- `case int n when n > 0:` je typu vzorec ještě `when` podmínku.
- `case null:` je vzor null.
- `default:` je známé výchozí případ.

Další informace o porovnávání vzorů v [vzor odpovídající v C# ](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Místní referenční hodnoty a vrátí

Tato funkce umožňuje algoritmy, které používají a vrátit odkazy na proměnné definované jinde. Jedním z příkladů je práce s velké matice a hledání na jednom místě s určité vlastnosti. Vrátí následující metodu **odkaz** do tohoto úložiště v matici:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Je možné deklarovat jako návratovou hodnotu `ref` a upravte tuto hodnotu v matici, jak je znázorněno v následujícím kódu:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

C# Jazyk má několik pravidel, které chrání vás před zneužitím `ref` místní hodnoty a vrátí:

* Je nutné přidat `ref` – klíčové slovo do podpisu metody a do všech `return` příkazy v metodě.
  - Díky tomu se vymazat metoda vrací odkazem v rámci metody.
* A `ref return` možné přiřadit hodnotu proměnné nebo `ref` proměnné.
  - Volající Určuje, zda je návratová hodnota zkopírován nebo ne. Vynechání `ref` modifikátor při přiřazování návratová hodnota označuje, že volající vyžaduje kopii hodnoty, ne odkaz na úložiště.
* Nelze přiřadit standardní metoda návratovou hodnotu pro `ref` místní proměnné.
  - Který zakazuje příkazy jako `ref int i = sequence.Count();`
* Nelze vrátit `ref` do proměnné, jehož doba života nerozšiřuje nad rámec provádění metody.
  - To znamená, že nejde vrátit odkazem na místní proměnná nebo proměnná se podobně jako obor.
* `ref` místní hodnoty a vrátí nelze použít u asynchronních metod.
  - Kompilátor nemůže vědět, pokud odkazovaná proměnná je nastavená na jeho konečnou hodnotu po návratu asynchronní metody.

Přidání místní referenční hodnoty a ref vrátí umožňuje algoritmy, které jsou efektivnější se vyhnout kopírování hodnot nebo provádění operací přesměrování více než jednou.

Přidání `ref` návratová hodnota je [zdroj kompatibilní změnu](version-update-considerations.md#source-compatible-changes). Stávající kód zkompiluje, ale ref návratové hodnoty je zkopírován při přiřazení. Volající musí aktualizovat úložiště pro návratovou hodnotu `ref` místní proměnnou pro uložení vrácení jako odkaz.

Další informace najdete v tématu [ref – klíčové slovo](../language-reference/keywords/ref.md) článku.

## <a name="local-functions"></a>Lokální funkce

Řada návrhů pro třídy zahrnují metody, které se volají z jediného umístění. Tyto další metody privátní zachovat každá metoda malém rozsahu a zaměřeně. *Lokální funkce* umožňují deklarovat metody v kontextu jinou metodu. Lokální funkce usnadnění pro čtenáře třídy zobrazíte, že místní metoda je volána pouze z kontextu, ve kterém je deklarována.

Existují dva běžné případy použití pro lokální funkce: veřejné iterátory a veřejné asynchronní metody. Oba typy metod generování kódu, který bude hlásit chyby později, než se dalo očekávat programátory. V metodách iterátoru, všechny výjimky, jsou dodržovány pouze při volání metody kód, který uvádí, že vrácená sekvence. V asynchronních metodách, všechny výjimky jsou pouze dodržovat při vráceného `Task` je očekáváno. Následující příklad ukazuje dělicí ověření parametru od implementace rozhraní iterátoru pomocí lokální funkce:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Stejným způsobem mohou být použity s `async` metody k zajištění, že výjimky vyplývající z ověřování argumentu jsou vyvolány před zahájením asynchronní práce:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Některé návrhy, které jsou podporovány lokální funkce také je možné dosáhnout použitím *výrazy lambda*. Tyto zúčastněné můžete [Další informace o rozdílech](../local-functions-vs-lambdas.md)

## <a name="more-expression-bodied-members"></a>Více členů s výrazem v těle

C# 6 zavedené [členové tvoření](csharp-6.md#expression-bodied-function-members) pro členské funkce a vlastnosti jen pro čtení. C# 7.0 rozšíří povolené členy, které je možné implementovat jako výrazy. V jazyce C# 7.0, můžete implementovat *konstruktory*, *finalizační metody*, a `get` a `set` přistupující objekty na *vlastnosti* a *indexerů* . Následující kód ukazuje příklady každé:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> V tomto příkladu nemusí finalizační metodu, ale je zobrazena na ukazují syntaxi. Finalizační metody by neměla implementovat ve své třídě, pokud to není nutné k uvolnění nespravovaných prostředků. Měli byste také zvážit použití <xref:System.Runtime.InteropServices.SafeHandle> třídy místo správy nespravované prostředky přímo.

Tato nová umístění pro členy s výrazem v těle představuje důležitý milník pro C# jazyka: Tyto funkce byly implementované členy komunity open source pracovali [Roslyn](https://github.com/dotnet/Roslyn) projektu.

Změna metody na výrazu vozidlo člena je [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Výrazy throw

V jazyce C# `throw` vždy bylo příkazu. Protože `throw` je příkaz, není výraz bylo C# konstrukce, které nelze použít. Tyto uvedeny podmíněné výrazy, null slučovací výrazy a některé výrazy lambda. Přidání členů s výrazem v těle přidá více míst kde `throw` výrazů může být užitečné. Aby mohla zapisovat některý z těchto konstruktorů, C# 7.0 zavádí *vyvolání výrazů*.

Toto přidání je snazší psát další kód založené na výrazu. Není nutné další příkazy pro kontrolu chyb.

## <a name="generalized-async-return-types"></a>Zobecněný asynchronní návratové typy

Vrácení `Task` objekt z asynchronní metody můžete zavést problémových míst výkonu v určitých cestách. `Task` je typem odkazu, takže ho pomocí znamená, že přidělování objektu. V případech, kde metoda deklarována s `async` modifikátor vrátí výsledky uložené v mezipaměti, nebo dokončí synchronně, navíc přidělení se může stát spoustu času náklady na kritické oddíly výkon kódu. Může být nákladná, pokud dojde k těmto přidělení v těsné smyčky.

Nové funkce jazyka znamená, že asynchronní metody nejsou omezeny na návratové typy `Task`, `Task<T>`, a `void`. Vrácený typ musí splňovat stále asynchronní vzorek, což znamená `GetAwaiter` metoda musí být přístupná. Jako konkrétní příklad `ValueTask` typ byl přidán do rozhraní .NET framework, aby pomocí této nové funkce jazyka:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> Je potřeba přidat balíček NuGet [ `System.Threading.Tasks.Extensions` ](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) Chcete-li použít <xref:System.Threading.Tasks.ValueTask%601> typu.

Toto vylepšení je zvláště užitečná pro autory knihoven, aby se vyhnul přidělování `Task` v výkonu kritický kód.

## <a name="numeric-literal-syntax-improvements"></a>Vylepšení číselný literál syntaxe

Číselné konstanty misreading může znesnadnit pochopení kódu při čtení poprvé. Bitové masky nebo jiné symbolické hodnoty jsou náchylné k neporozumění. C#7.0 obsahuje dvě nové funkce pro zápis čísla způsobem nejvíce čitelné pro zamýšlené použití: *binární literály:*, a *oddělovače číslic:*.

Pro situace, při vytváření bitové masky, nebo když se binární vyjádření čísla je nejvíce čitelné kód zápis tohoto čísla v binárním souboru:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

`0b` Na začátku konstanty Určuje, že číslo je zapsán jako binární číslo. Můžete získat tak, aby byl často snazší zjistit bitové vzory zavedením dlouhý, binárních čísel `_` jako oddělovač číslic, jak je znázorněno výše binární – konstanta. Oddělovač číslic může vyskytovat kdekoli v konstantě. Pro základní 10 čísel, je běžné použití jako tisíců oddělovač:

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Oddělovač číslic jde použít s `decimal`, `float`, a `double` typy a také:

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Dohromady, je možné deklarovat číselné konstanty s mnohem více čitelnost.
