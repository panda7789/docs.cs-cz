---
title: "Co je nového v jazyce C# 7 – průvodce v C#"
description: "Přehled nových funkcí, bude v příštích verzí 7 jazyka C#."
keywords: "C#, .NET, .NET Core, nejnovější funkce, co je nového"
author: BillWagner
ms.author: wiwagn
ms.date: 12/21/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: f98039404789e8886154e04c4b97a21741c4d885
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2017
---
# <a name="whats-new-in-c-7"></a>Co je nového v C# 7

C# 7 přidá řadu nových funkcí jazyka C#:
* [`out`proměnné](#out-variables)
    - Je možné deklarovat `out` hodnoty vložené jako argumenty pro metodu, kdy se používá.
* [Řazené kolekce členů](#tuples)
    - Můžete vytvořit jednoduché, Nepojmenované typy, které obsahují více veřejná pole. Kompilátory a nástroje IDE pochopit sémantika tyto typy.
* [Zahození](#discards)
    - Zahození jsou dočasné, jen pro zápis proměnné používané v přiřazení, pokud vám nezáleží hodnotu přiřazenou. Jsou užitečné, když deconstructing řazených kolekcí členů a uživatelem definované typy, jakož i při volání metody s `out` parametry.
* [Shoda vzoru](#pattern-matching)
    - Můžete vytvořit na základě náhodné typy a hodnoty členů tyto typy logiky větvení.
* [`ref`lokální a vrátí](#ref-locals-and-returns)
    - Metoda argumentů a místní proměnné může být odkazy na další úložiště.
* [Lokální funkce](#local-functions)
    - Funkce uvnitř jiných funkcí omezit jejich rozsah a viditelnost lze vnořit.
* [Další výraz vozidlo členy](#more-expression-bodied-members)
    - Seznam členů, které mohou být vytvořeny pomocí výrazů se zvětšil.
* [`throw`Výrazy](#throw-expressions)
    - Můžete vyvolat výjimky v konstrukce kódu, které předtím nebyly povoleny, protože `throw` byl příkaz. 
* [Zobecněný asynchronní návratové typy](#generalized-async-return-types)
    - Metody deklarovat s `async` modifikátoru může vrátit jiné typy kromě `Task` a `Task<T>`.
* [Vylepšení číselný literál syntaxe](#numeric-literal-syntax-improvements)
    - Nové tokeny zlepšení čitelnosti pro číselné konstanty.

Zbývající část tohoto tématu popisuje každou funkci. Pro každou funkci dozvíte jejich zdůvodnění. Dozvíte syntaxe. Zobrazí se několik ukázkových scénářů, kde pomocí nové funkce mohou zvýšit vaši produktivitu jako vývojář. 

## <a name="out-variables"></a>`out`proměnné

Existující syntaxi, která podporuje `out` parametry vylepšeno v této verzi.  

Dříve museli byste oddělit deklaraci mimo proměnnou a její inicializace do dvou různých příkazů:

[!code-csharp[OutVariableOldStyle](../../../samples/snippets/csharp/new-in-7/program.cs#03_OutVariableOldStyle "classic out variable declaration")]

Nyní můžete deklarovat `out` proměnných v seznamu argumentů volání metody místo psaní příkazů samostatné prohlášení:

[!code-csharp[OutVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#01_OutVariableDeclarations "Out variable declarations")]

Můžete chtít zadat typ `out` proměnná pro přehlednost, jak je uvedeno výše. Však jazyk podporuje použití implicitně typované lokální proměnnou:

[!code-csharp[OutVarVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#02_OutVarVariableDeclarations "Implicitly typed Out variable")]

* Kód je snadnější čtení. 
    - Je deklarovat proměnnou mimo, kde má být použito, není na dalším řádku výše.
* Není potřeba přiřadit počáteční hodnotu.
    - Deklarováním `out` proměnné, kde se používá při volání metody, nemůžete je využít omylem předtím, než je přiřazen.

Nejčastěji používá pro tuto funkci bude `Try` vzor. V tomto vzoru, metoda vrátí `bool` označující úspěch nebo neúspěch a `out` proměnné, která poskytuje výsledek, pokud metoda bude úspěšná.

Při použití `out` deklarace proměnné deklarované proměnná "nevracení" do vnějšího oboru, pokud příkaz. To umožňuje používat proměnné později:

```csharp
if (!int.TryParse(input, out int result))
{    
    return null;
}

return result;
```

## <a name="tuples"></a>Řazené kolekce členů

> [!NOTE]
> Vyžadovat nové funkce řazených kolekcí členů <xref:System.ValueTuple> typy.
> Je nutné přidat balíček NuGet [ `System.ValueTuple` ](https://www.nuget.org/packages/System.ValueTuple/) odborných na platformách, které neobsahují typy.
>
> Toto je podobná jiné jazykové funkce, které závisí na typech doručit v rámci. Příklad zahrnují `async` a `await` spoléhat na `INotifyCompletion` rozhraní a LINQ spoléhat na `IEnumerable<T>`. Jak .NET se stává stále další platformy, které jsou nezávislé, mechanismus doručování mění. Rozhraní .NET Framework nemusí vždy dodávat na stejné cadence jako kompilátor jazyka. Nové jazykové funkce využívají nové typy, tyto typy nebudou mít k dispozici jako balíčků NuGet při odeslání funkce jazyka. Tyto nové typy získat přidávají do rozhraní API .NET standardní a dodávána jako součást rozhraní, požadavek na balíček NuGet se odeberou.

C# poskytuje bohaté syntaxe pro tříd a struktur, který používá k popisu vašich představ návrhu. Ale někdy této bohaté syntaxe vyžaduje další práci s minimálním výhody. Často může zapisovat metody, které je třeba jednoduchá struktura obsahující více než jeden element data. Chcete-li tyto scénáře podporovat *řazených kolekcí členů* byly přidány do jazyka C#. Řazené kolekce členů jsou jednoduché datové struktury, které obsahují několik polí k reprezentaci datových členů.
Nelze ověřit pole a nelze definovat vlastní metody

> [!NOTE]
> Řazené kolekce členů byly k dispozici před C# 7, ale měla neefektivní a měl neexistuje jazyková podpora.
> Vynutila si, že prvky n-tice může být odkazováno pouze jako `Item1`, `Item2` a tak dále. C# 7 zavádí jazyková podpora pro řazené kolekce členů, která umožňuje sémantického názvy polí pomocí nové, efektivnější řazené kolekce členů typů řazené kolekce členů.

Můžete vytvořit řazené kolekce členů přiřazením každého člena na hodnotu:

[!code-csharp[UnnamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#04_UnnamedTuple "Unnamed tuple")]

Aby přiřazení vytvoří řazenou kolekci členů, jejíž členové jsou `Item1` a `Item2`, který můžete použít stejným způsobem jako <xref:System.Tuple> syntaxe k vytvoření řazené kolekce členů, která poskytuje sémantického názvy na každý ze členů řazené kolekce členů, můžete změnit:

[!code-csharp[NamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#05_NamedTuple "Named tuple")]

`namedLetters` Řazené kolekce členů obsahuje pole, které jsou označovány jako `Alpha` a `Beta`. Názvy v rámci existují pouze v době kompilace a nejsou zachována např. při kontrole řazené kolekce členů v době běhu pomocí reflexe.

V přiřazení řazené kolekce členů můžete také zadat názvy polí na pravé straně přiřazení:

[!code-csharp[ImplicitNamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#06_ImplicitNamedTuple "Implicitly named tuple")]

Můžete zadat názvy polí na levé a pravé straně přiřazení:

[!code-csharp[NamedTupleConflict](../../../samples/snippets/csharp/new-in-7/program.cs#07_NamedTupleConflict "Named tuple conflict")]

Výše uvedené řádku generuje upozornění, `CS8123`, o tom, že názvy na pravé straně přiřazení, `Alpha` a `Beta` jsou ignorovány, protože jsou v konfliktu s názvy na levé straně, `First` a `Second`.

Výše uvedených příkladech základní syntaxe deklarovat řazené kolekce členů. Řazené kolekce členů jsou velmi užitečné jako návratové typy pro `private` a `internal` metody. Řazené kolekce členů poskytují jednoduché syntaxi pro tyto metody vrátit více diskrétních hodnot: uložit práci při vytváření `class` nebo `struct` , který definuje typ vrácený. Není potřeba pro vytvoření nového typu.

Vytvoření řazené kolekce členů je efektivnější a zvýšit produktivitu.
Je jednodušší, lightweight syntaxe definovat datová struktura, která představuje více než jednu hodnotu. Následující příklad metoda vrátí na minimální a maximální hodnoty zjištěné v posloupnost celých čísel:

[!code-csharp[TupleReturningMethod](../../../samples/snippets/csharp/new-in-7/program.cs#08_TupleReturningMethod "Tuple returning method")]

Použití řazených kolekcí členů tímto způsobem nabízí několik výhod:

* Uložit práci při vytváření `class` nebo `struct` , který definuje typ vrácený. 
* Není nutné k vytvoření nového typu.
* Rozšíření pro jazyk eliminuje nutnost volání < xref:System.Tuple.Create``1(``0) > metody.

Deklarace pro metodu poskytuje názvy pro pole řazené kolekce členů, která je vrácena. Při volání metody vrácená hodnota je řazené kolekce členů, jejichž pole jsou `Max` a `Min`:

[!code-csharp[CallingTupleMethod](../../../samples/snippets/csharp/new-in-7/program.cs#09_CallingTupleMethod "Calling a tuple returning method")]

Může nastat situace, kdy budete chtít rozbalit členy řazené kolekce členů, kteří byly vráceny z metody.  Můžete to udělat pomocí deklarování samostatné proměnných pro každou z hodnot v řazené kolekci členů. To se označuje jako *deconstructing* řazenou kolekci členů:

[!code-csharp[CallingWithDeconstructor](../../../samples/snippets/csharp/new-in-7/program.cs#10_CallingWithDeconstructor "Deconstructing a tuple")]

<!-- Add wildcards here, if they are in C# 7
-->

Můžete zadat taky podobné deconstruction pro libovolného typu v rozhraní .NET. To se provádí zápis `Deconstruct` jako člena třídy metodu. Aby `Deconstruct` metoda poskytuje sadu `out` argumenty pro každé z vlastností, které mají být extrahovány. Zvažte proto `Point` třídu, která poskytuje deconstructor metodu, která extrahuje `X` a `Y` souřadnice:

[!code-csharp[PointWithDeconstruction](../../../samples/snippets/csharp/new-in-7/point.cs#11_PointWithDeconstruction "Point with deconstruction method")]
 
Můžete rozbalit přiřazením řazené kolekce členů do jednotlivých polí `Point`:

[!code-csharp[DeconstructPoint](../../../samples/snippets/csharp/new-in-7/program.cs#12_DeconstructPoint "Deconstruct a point")]

Názvy definované v nejsou vázány `Deconstruct` metoda. Extrakce proměnné můžete přejmenovat jako součást přiřazení:  

[!code-csharp[DeconstructNames](../../../samples/snippets/csharp/new-in-7/program.cs#13_DeconstructNames "Deconstruct with new names")]

Dozvíte se v podrobněji řazených kolekcí členů v [řazených kolekcí členů tématu](../tuples.md).

## <a name="discards"></a>Zahození

Často, když deconstructing řazené kolekce členů nebo volání metody s `out` parametry, se musí k definování proměnné jehož hodnota nezáleží a nemáte v úmyslu použít. C# přidává podporu pro *zahodí* tohoto scénáře. Zahození je proměnná jen pro zápis, jehož název je `_` (podtržítko); můžete přiřadit všechny hodnoty, které chcete zahodit do jedné proměnné. Zahození je stejná jako nepřiřazené proměnné. Kromě příkaz přiřazení nelze použít zahození v kódu.

Zahození jsou podporovány v následujících scénářích:

* Když deconstructing řazené kolekce členů nebo uživatelem definované typy.

* Při volání metody s [out](../language-reference/keywords/out.md) parametry.

* V porovnávání operaci s [je](../language-reference/keywords/is.md) a [přepínač](../language-reference/keywords/switch.md) příkazy.

* Pokud chcete explicitně Identifikujte jako samostatné identifikátor hodnota přiřazení jako zahození.

V následujícím příkladu definuje `QueryCityDataForYears` metodu, která vrátí 6-n-tice obsahující data pro město pro dva různé roky. Volání metody v příkladu se týká pouze dva naplnění hodnoty vrácené metodou a proto považuje zbývající hodnoty v řazené kolekci členů jako zahodí, pokud ji deconstructs řazenou kolekci členů.

[!code-csharp[Tuple-discard](../../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Další informace najdete v tématu [zahodí](../discards.md).
 
## <a name="pattern-matching"></a>Shoda vzoru

*Shoda vzoru* je funkce, která umožňuje implementovat metodu odesílání na vlastnosti než typ objektu. Pravděpodobně už jste obeznámeni s odesílání metoda na základě typu objektu. V objektově orientované programování virtuální a přepsání metody poskytují syntaxe jazyka pro implementaci metoda odeslání založený na typu objektu. Základní a odvozené třídy poskytovat různé implementace. Vzor odpovídající výrazy rozšířit tento koncept proto, že můžete snadno implementovat podobné odesílání vzory pro typy a data elementy, které nejsou v relaci prostřednictvím hierarchie dědičnosti. 

Porovnávání se podporuje `is` výrazy a `switch` výrazy. Každý umožňuje zkontrolujete objektu a jeho vlastnosti k určení, pokud objekt splňuje hledané kombinaci vzoru. Můžete použít `when` – klíčové slovo lze určit další pravidla, se vzorem.

### <a name="is-expression"></a>`is`výraz

`is` Vzor výrazu rozšiřuje známé `is` operátor dotazovat objekt nad rámec jeho typu.

Začněme pomocí jednoduchého scénáře. Do tohoto scénáře, které ukazují, jak vytvořit vzor odpovídající výrazy algoritmy, které pracují s nesouvisejícími typy snadno přidáme možnosti. Začneme s metodu, která vypočítá součet počtu zobrazí souhrn die:

[!code-csharp[SumDieRolls](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#14_SumDieRolls "Sum die rolls")]

Můžete rychle zjistit, budete muset najít že součet die vrátí, kde některé zobrazí souhrn se provedou více počátku. Součást vstupní pořadí může být více výsledků místo jedno číslo:

[!code-csharp[SumDieRollsWithGroups](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#15_SumDieRollsWithGroups "Sum die rolls with groups")]

`is` Vzor výrazu velmi dobře funguje v tomto scénáři. Jako součást kontrola typu zapisovat proměnné inicializace. Tím se vytvoří novou proměnnou typu ověřené runtime.

Tyto scénáře zachovat rozšíření, můžete zjistit sestavení více `if` a `else if` příkazy. Po který bude nepraktické, budete pravděpodobně chtít přepnout na `switch` vzor výrazy.

### <a name="switch-statement-updates"></a>`switch`aktualizace – příkaz

*Odpovídat výrazu* má známé syntaxe, na základě `switch` příkaz již součástí jazyka C#. Umožňuje překlad stávajícího kódu pro použití výrazu shody před přidáním nové případy: 

[!code-csharp[SumUsingSwitch](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#16_SumUsingSwitch "Sum using switch")]

Výrazy shody mají mírně odlišné syntaxi než `is` výrazy, kde deklarace typu a proměnné na začátku `case` výraz.

Výrazy shody také podporují konstanty. Tím ušetřit čas tím řešení se jednoduchých případech:

[!code-csharp[SwitchWithConstants](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#17_SwitchWithConstants "Switch with constants")]

Výše uvedený kód přidá případů pro `0` jako zvláštní případ `int`, a `null` ve speciálním případě při žádný vstup. Tento příklad ukazuje jeden důležité nové funkce ve výrazech vzor přepínač: pořadí `case` výrazy nyní záleží. `0` Případu musí být před Obecné `int` případu. Jinak, by první vzor tak, aby odpovídala `int` případu, i když je hodnota `0`. Pokud omylem výrazy shody pořadí tak, že již byla zpracována novější případu, bude kompilátor příznak, který a generuje chybu.

Toto stejné chování umožňuje zvláštní případ prázdnou sekvencí vstupní.
Uvidíte, že případ `IEnumerable` položku, která obsahuje elementy musí být před Obecné `IEnumerable` případu.

Tato verze taky přidala `default` případu. `default` Případ vždy vyhodnocena poslední, bez ohledu na pořadí zobrazí se ve zdroji. Z tohoto důvodu je konvence uvést `default` případu poslední.

Nakonec přidejme jednu poslední `case` nového stylu die. Některé hry pomocí percentilu rozčlenění znázornit větší rozsah čísel. 

> [!NOTE]
> Dva rozčlenění 10 zachytávání percentilu může představovat každé číslo od 0 do 99. Počátku má strany, které jsou označené jako `00`, `10`, `20`,... `90`. Další die má strany s názvem bez přípony `0`, `1`, `2`,... `9`. Přidejte dva die hodnot společně a získáte každé číslo od 0 až 99.

Pokud chcete tento druh die přidat do kolekce, nejprve definujte typ představují die percentilu:

[!code-csharp[18_PercentileDie](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#18_PercentileDie "Percentile Die type")]

Potom přidat `case` odpovídat výrazu pro nový typ:

[!code-csharp[SwitchWithNewTypes](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#19_SwitchWithNewTypes "Include Percentile Die type")]

Nové syntaxe pro výrazy porovnávání vzorů usnadňuje vytvoření odesílání algoritmů na základě typ objektu, nebo jiné vlastnosti pomocí syntaxe jasným a přesným metrikám. Vzor odpovídající výrazy povolte tyto konstrukce pro datové typy, které jsou nesouvisející podle dědičnosti.

Další informace o porovnávání se v tomto tématu vyhrazený pro [v jazyce C# porovnávání vzorů](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Místní hodnoty REF a vrátí

Tato funkce umožňuje algoritmy, které používají a vrátí odkazy na proměnné definované jinde. Jedním z příkladů je práce s velké matic a hledání jedno umístění s určité charakteristické vlastnosti. Jedna metoda vrátí dva indexy na jednom místě v matici:

[!code-csharp[FindReturningIndices](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#20_FindReturningIndices "Find returning indices")]

Existuje mnoho problémů s tímto kódem. První řadě je veřejná metoda, která vrací řazenou kolekci členů. Tento jazyk podporuje, ale uživatelem definované typy (třídy nebo struktury) jsou upřednostněny veřejná rozhraní API.

Druhý tato metoda vrací indexy na položku v matici.
Který vede volající napsat kód, který používá tyto indexy dereference matice a upravovat jeden element:

[!code-csharp[UpdateItemFromIndices](../../../samples/snippets/csharp/new-in-7/program.cs#21_UpdateItemFromIndices "Update Item From Indices")]

By místo napíše metoda, která vrátí *odkaz* na prvek přehled, který chcete změnit. Může to provést pouze pomocí nezabezpečený kód a vrací ukazatel na `int` v předchozích verzích.

Projděme řadu změny k předvedení funkcí místní ref a znázorňují postup vytvoření metody, která vrátí odkaz na interní úložiště.
Cestou se dozvíte pravidla ref vrátit a ref místní funkce, která chrání před omylem zneužití ho.

Spustit změnou `Find` deklarace metody, které se vrátí `ref int` místo řazené kolekce členů. Potom upravte příkaz return tak, aby vracel s hodnotou uloženou v matici místo dvou indexy:

```csharp
// Note that this won't compile. 
// Method declaration indicates ref return,
// but return statement specifies a value return.
public static ref int Find2(int[,] matrix, Func<int, bool> predicate)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
        for (int j = 0; j < matrix.GetLength(1); j++)
            if (predicate(matrix[i, j]))
                return matrix[i, j];
    throw new InvalidOperationException("Not found");
}
```

Když je deklarovat, metoda vrátí `ref` proměnné, musíte taky přidat `ref` – klíčové slovo pro každý příkaz return. Určující vrátit odkazem a pomáhá vývojářům čtení kódu později mějte na paměti, že metoda vrátí odkazem:

[!code-csharp[FindReturningRef](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#22_FindReturningRef "Find returning by reference")]

Teď, když metoda vrátí odkaz na celé číslo v matici, budete muset upravit, kde je volán.  `var` Prohlášení znamená, že `valItem` je nyní `int` místo řazené kolekce členů:

[!code-csharp[AssignRefReturnToValue](../../../samples/snippets/csharp/new-in-7/program.cs#23_AssignRefReturnToValue "Assign ref return to value")]

Druhý `WriteLine` příkaz v předchozím příkladu vytiskne hodnota `42`, nikoli `24`. Proměnná `valItem` je `int`, nikoli `ref int`. `var` – Klíčové slovo umožňuje kompilátoru k určení typu, ale nepřidá implicitně `ref` modifikátor. Místo toho hodnota odkazuje `ref return` je *zkopírovat* do proměnné na levé straně přiřazení. Proměnná není `ref` místní.

Chcete-li získat výsledek, který chcete, je nutné přidat `ref` modifikátor na místní deklarace proměnné při vrácená hodnota je odkaz vytvořit odkaz na proměnnou:

[!code-csharp[AssignRefReturn](../../../samples/snippets/csharp/new-in-7/program.cs#24_AssignRefReturn "Assign ref return")]

Nyní, druhý `WriteLine` příkaz v předchozím příkladu bude vytisknout hodnotu `24`, indikující, že byl upraven úložiště v matici. Místní proměnná bylo deklarováno s `ref` modifikátor a bude trvat `ref` vrátit. Je třeba inicializovat `ref` proměnná při deklaraci, nelze rozdělit deklarace a inicializace.

Jazyk C# má tři další pravidla, která ochranu proti zneužití `ref` lokální a vrátí:

* Nelze přiřadit standardní metoda návratovou hodnotu pro `ref` místní proměnné.
    - Která zakáže příkazy jako`ref int i = sequence.Count();`
* Nelze vrátit `ref` do proměnné, jejichž doba platnosti nepřesahuje provádění metody.
    - To znamená, že nemůže vrátit odkaz na místní proměnná nebo proměnná se podobně jako obor.
* `ref`lokální a vrátí nelze použít u asynchronních metod.
    - Kompilátor nemůže vědět, pokud odkazovaná proměnná byla nastavena na jeho konečná hodnota při návratu asynchronní metody.

Přidání místní hodnoty ref a ref vrátí povolit algoritmy, které jsou efektivnější vyhnout kopírování hodnot nebo provádění operací při přesměrování vícekrát. 

## <a name="local-functions"></a>Lokální funkce

Řada návrhů pro třídy zahrnují metody, které se nazývají z pouze jedno umístění. Tyto další metody privátní zachovat každá metoda malé a zaměřují se. Však budou může ztížit pochopit třídu při čtení ji poprvé. Tyto metody, je třeba chápat mimo kontext jednoho volání umístění.

Pro tyto návrhy *lokální funkce* vám umožní deklarovat metody uvnitř kontextu jinou metodu. To usnadňuje čtečky třídy zobrazíte, že místní metoda je volána pouze z kontextu, ve kterém je deklarovaná.

Existují dvě velmi běžné případy použití pro místní funkce: metody veřejné iterator a veřejné asynchronní metody. Oba typy metod generovat kód, který později, než by se dalo očekávat programátory sestavy chyb. V případě metody iterator jakékoli výjimky jsou dodržovány pouze při volání metody kód, který vytvoří výčet vrácený pořadí. V případě asynchronní metody jakékoli výjimky jsou pouze dodržovány při vrácený `Task` je očekáváno.

Začneme metodu iterator:

[!code-csharp[IteratorMethod](../../../samples/snippets/csharp/new-in-7/Iterator.cs#25_IteratorMethod "Iterator method")]

Zkontrolujte následující kód, který volá metodu iterator nesprávně:

[!code-csharp[CallIteratorMethod](../../../samples/snippets/csharp/new-in-7/program.cs#26_CallIteratorMethod "Call iterator method")]

Když je vyvolána výjimka `resultSet` vstupní, nejsou při `resultSet` je vytvořena.
V tomto příkladu obsažené Většina vývojářů může rychle diagnostikovat problém. V větší základy kódu, kód, který vytvoří iterovat často není co nejblíže kód, který zobrazí výsledek. Kód můžete Refaktorovat tak, že veřejná metoda ověří všechny argumenty a soukromá metoda generuje výčtu:

[!code-csharp[IteratorMethodRefactored](../../../samples/snippets/csharp/new-in-7/Iterator.cs#27_IteratorMethodRefactored "Iterator method refactored")]

Tato verze refactored vyvolá výjimku výjimky okamžitě, protože veřejná metoda není metodou iterator; pouze privátní metoda používá `yield return` syntaxe. Existují však potenciální problémy s Tento refaktoring. Soukromá metoda by měla být volána metoda veřejné rozhraní pouze, protože jinak se všemi ověřovacími argument přeskočí.
Čtečky třídy musí tuto skutečnost zjistit čtení celou třídu a vyhledáním všechny odkazy na `alphabetSubsetImplementation` metoda.

Tento návrh záměr můžete vytvořit více zrušte pomocí deklarace `alphabetSubsetImplementation` jako místní funkce uvnitř metody veřejné rozhraní API:

[!code-csharp[22_IteratorMethodLocal](../../../samples/snippets/csharp/new-in-7/Iterator.cs#28_IteratorMethodLocal "Iterator method with local function")]

Výše uvedené verze umožňuje vymazat odkazovaný místní metoda pouze v kontextu vnější metody. Pravidla pro lokální funkce také zajistěte, aby vývojář nelze omylem volání místní funkce z jiného umístění v třídě a ověření argument obejít.

Stejným způsobem je možné použít s `async` zajistit, že vzniklých argument ověření je vyvolána před zahájením práce asynchronní metody:

[!code-csharp[TaskExample](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

> [!NOTE]
> Některé návrhů, které jsou podporovány pomocí místní také je možné dosáhnout pomocí *výrazy lambda*. Můžete tyto zúčastněným [Další informace o rozdílech](../local-functions-vs-lambdas.md)

## <a name="more-expression-bodied-members"></a>Další výraz vozidlo členy

C# 6 zavedená [výraz vozidlo členy](csharp-6.md#expression-bodied-function-members) pro členské funkce a vlastnosti jen pro čtení. C# 7 rozšíří povolené členy, u nichž může být implementováno jako výrazy. V jazyce C# 7, můžete implementovat *konstruktory*, *finalizační metody*, a `get` a `set` přístupových objektů na *vlastnosti* a *indexery* . Následující kód ukazuje příklady jednotlivých:

[!code-csharp[ExpressionBodiedMembers](../../../samples/snippets/csharp/new-in-7/expressionmembers.cs#36_ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Tento příklad nemusí finalizační metody, ale je zobrazen k předvedení syntaxe. Finalizační metody by neměla implementovat v třídě, pokud to není nutné k uvolnění nespravovaných prostředků. Měli byste také zvážit použití <xref:System.Runtime.InteropServices.SafeHandle> třída místo přímo Správa nespravovaných prostředků.

Tato nová umístění pro výraz vozidlo členy představují důležité milník pro jazyk C#: tyto funkce, které byly implementovány členové komunity pracující na open-source [Roslyn](https://github.com/dotnet/Roslyn) projektu.

## <a name="throw-expressions"></a>Throw – výrazy

V jazyce C# `throw` byla vždy příkaz. Protože `throw` je prohlášení, není výrazu, že byly konstrukce jazyka C#, kde nelze použít. Tyto zahrnuty podmíněné výrazy, null slučování výrazy a některé výrazy lambda. Přidání členů výraz vozidlo přidá další umístění kde `throw` výrazy mohla být užitečná. Tak, aby bylo možné napsat některé z těchto konstrukce, C# 7 zavádí *throw výrazy*.

Syntaxe je stejný, jako jste používali vždy pro `throw` příkazy. Jediným rozdílem je, že teď můžete umístit je nová umístění, jako třeba podmíněného výrazu:

[!code-csharp[Throw_ExpressionExample](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#37_Throw_ExpressionExample "conditional throw expressions")]

Tato funkce umožňuje pomocí throw výrazů ve výrazech inicializace:

[!code-csharp[ThrowInInitialization](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#38_ThrowInInitialization "conditional throw expressions")]

Tyto inicializacích by dříve, musí být v konstruktoru, s příkazech throw v těle konstruktoru:


[!code-csharp[ThrowInConstructor](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#39_ThrowInConstructor "throw statements")]

> [!NOTE]
> Obě předchozí konstrukce způsobí, že výjimky vyvolání během vytváření objektu. Ty jsou často obtížné zotavit.
> Z tohoto důvodu se nedoporučuje návrhů generující výjimky během vytváření.

## <a name="generalized-async-return-types"></a>Zobecněný asynchronní návratové typy

Vrácení `Task` objekt z asynchronní metody můžou představovat kritické body v určité cesty. `Task`je typu odkazu, takže ho pomocí znamená přidělování objekt. V případech, kde metodu deklarovat s `async` modifikátor vrátí výsledky uložené v mezipaměti, nebo dokončí synchronně, navíc přidělení se může stát déle náklady v kritické oddíly výkon kódu. Může být velmi náročná, pokud tyto přidělení, ke kterým došlo v úzkou smyčky.

Nová funkce jazyka znamená, že asynchronní metody může vrátit jiné typy kromě `Task`, `Task<T>` a `void`. Vrácený typ stále musí vyhovovat vzoru async znamená `GetAwaiter` metoda musí být přístupné. Například jeden konkrétní `ValueTask` do rozhraní .NET framework, aby se přidal typ využívají tato nová funkce jazyka: 

[!code-csharp[UsingValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#30_UsingValueTask "Using ValueTask")]

> [!NOTE]
> Je nutné přidat balíček NuGet [ `System.Threading.Tasks.Extensions` ](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) Chcete-li použít <xref:System.Threading.Tasks.ValueTask%601> typu.

Může být jednoduchý optimalizace použití `ValueTask` v místech, kde `Task` se použije před. Ale pokud chcete provést další optimalizace ručně, můžete mezipaměti výsledky z asynchronní pracovní a znovu použít výsledek v následných volání. `ValueTask` Struktura neobsahuje konstruktor s `Task` parametr tak, že můžete vytvořit `ValueTask` z návratová hodnota všechny existující asynchronní metody:

[!code-csharp[AsyncOptimizedValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#31_AsyncOptimizedValueTask "Return async result or cached value")]
 
Jak se všechna doporučení výkonu by měla otestovat obě verze před provedením velké škálování změny kódu.

## <a name="numeric-literal-syntax-improvements"></a>Vylepšení číselný literál syntaxe

Číselné konstanty misreading může ztížit zjistit kód při čtení poprvé. To často dochází, pokud tato čísla se používají jako bitové masky nebo jiných symbolický místo číselné hodnoty. C# 7 obsahuje dvě nové funkce, aby bylo snazší zápis čísla způsobem nejvíce čitelný pro zamýšlené použití: *binární literály*, a *číslice oddělovačů*.

Při vytváření bitové masky nebo kdykoli binární reprezentace číslo neposkytuje pro tyto časy kód nejvíce čtení, zápisu toto číslo v binárním:

[!code-csharp[BinaryConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#32_BinaryConstants "Binary constants")]

`0b` Na začátku konstanta označuje, zda číslo je zapsána jako binární číslo.

Binární čísla můžete získat tak často je snazší zjistit vzory bit zavedením velmi náročná `_` jako oddělovač číslic:

[!code-csharp[ThousandSeparators](../../../samples/snippets/csharp/new-in-7/Program.cs#33_ThousandSeparators "Thousands separators")]

Oddělovač číslice může vyskytovat kdekoli v konstanta. Pro základní 10 čísel, by se běžné můžete použít jako tisíců oddělovače:

[!code-csharp[LargeIntegers](../../../samples/snippets/csharp/new-in-7/Program.cs#34_LargeIntegers "Large integer")]

Oddělovač číslice lze použít s `decimal`, `float` a `double` také typy:

[!code-csharp[OtherConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#35_OtherConstants "non-integral constants")]

Dohromady, můžou deklarovat číselné konstanty s lepší čitelnost.
