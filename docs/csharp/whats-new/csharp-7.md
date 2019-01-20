---
title: Co je nového v jazyce C# 7.0 – průvodce v C#
description: Získejte přehled o nových funkcích v nadcházející verzi 7 jazyka C#.
ms.date: 12/21/2016
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 08e9b9d1a991c6dd18477214dec60fba95afc6c9
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415725"
---
# <a name="whats-new-in-c-70"></a>Co je nového v jazyce C# 7.0

C# 7.0 přidá několik nových funkcí jazyka C#:
* [`out` Proměnné](#out-variables)
    - Je možné deklarovat `out` hodnoty inline jako argumentů metody, kde jsou použity.
* [Řazené kolekce členů](#tuples)
    - Můžete vytvořit jednoduchý, Nepojmenované typy, které obsahují více veřejná pole. Kompilátory a nástroje pro prostředí IDE pochopit sémantiku z těchto typů.
* [Zahození](#discards)
    - Zahození jsou dočasné, jen pro zápis proměnné při nezáleží hodnota přiřazená v přiřazeních. Jsou zvláště užitečné při dekonstrukce řazených kolekcí členů a uživatelem definovaných typů, stejně jako při volání metody s `out` parametry.
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

Zbývající část tohoto tématu popisuje všechny funkce. Pro jednotlivé funkce dozvíte zdůvodnění. Dozvíte syntaxe. Zobrazí se vám několik ukázkových scénářů, ve kterém pomocí nové funkce se budete produktivnější jako vývojář. 

## <a name="out-variables"></a>`out` Proměnné

Existující syntaxi, která podporuje `out` v této verzi jsme vylepšili parametry.  

Dříve je třeba oddělit deklarace proměnné out a jeho inicializaci na dva různé příkazy:

[!code-csharp[OutVariableOldStyle](../../../samples/snippets/csharp/new-in-7/program.cs#03_OutVariableOldStyle "classic out variable declaration")]

Nyní můžete deklarovat `out` proměnných v seznamu argumentů volání metody místo psaní příkazu samostatné deklarace:

[!code-csharp[OutVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#01_OutVariableDeclarations "Out variable declarations")]

Možná budete chtít zadat typ `out` proměnné pro přehlednost, jak je znázorněno výše. Však jazyk podporuje použití implicitně typovaná lokální proměnná:

[!code-csharp[OutVarVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#02_OutVarVariableDeclarations "Implicitly typed Out variable")]

* Kód je lépe čitelný. 
    - Deklarujete proměnnou mimo, kde má být použito, ne na další řádek výše.
* Už není potřeba přiřadit počáteční hodnotu.
    - Deklarací `out` proměnné, kde se používá ve volání metody, nemůžete použít omylem ho dřív, než je přiřadí.

Nejběžnějším využitím této funkce bude `Try` vzor. V tomto vzoru, metoda vrátí `bool` udávající úspěch nebo neúspěch a `out` proměnné, která obsahuje výsledek, pokud metoda uspěje.

Při použití `out` deklarace proměnné deklarované proměnné "nevracení" do vnějšího rozsahu if – příkaz. Díky tomu můžete použít později:

```csharp
if (!int.TryParse(input, out int result))
{    
    return null;
}

return result;
```

## <a name="tuples"></a>Řazené kolekce členů

> [!NOTE]
> Vyžadovat nových funkcí řazených kolekcí členů <xref:System.ValueTuple> typy.
> Je nutné přidat balíček NuGet [ `System.ValueTuple` ](https://www.nuget.org/packages/System.ValueTuple/) aby bylo možné používat na platformách, které neobsahují typy.
>
> To se podobá další jazykové funkce, které využívají typy v rozhraní framework. Příklad zahrnují `async` a `await` spoléhat na `INotifyCompletion` rozhraní a LINQ spoléhat na `IEnumerable<T>`. Jak .NET se mění na další platformy, které jsou nezávislé, mechanismus doručování mění. Rozhraní .NET Framework nemusí vždy odeslání na stejném tempo jako kompilátor jazyka. Nové funkce jazyků využívají nové typy, typy nebudou mít k dispozici jako balíčků NuGet při dodávání funkcí jazyka. Tyto nové typy získat přidána do rozhraní API .NET Standard a dodávána jako součást rozhraní framework, odeberou se požadavek na balíček NuGet.

C# poskytuje bohaté syntaxi pro třídy a struktury, které slouží k vysvětlení máte v úmyslu návrhu. Ale někdy bohaté syntaxe vyžaduje další práci s minimálními výhodu. Často může zapisovat metody, které vyžadují jednoduchou strukturu obsahující více než jeden datový prvek. Pro podporu těchto scénářů *řazených kolekcí členů* byly přidány do jazyka C#. Řazené kolekce členů jsou jednoduché datové struktury, které obsahují více polí k reprezentaci datové členy.
Pole pořadí úloh se neověřuje, a nelze definovat vlastní metody

> [!NOTE]
> Řazené kolekce členů byly k dispozici před C# 7.0, ale bylo neefektivní a měl neexistuje jazyková podpora.
> To znamená, že elementů řazené kolekce členů mohou být odkazovány pouze jako `Item1`, `Item2` a tak dále. C# 7.0 zavádí podporu jazyka pro řazené kolekce členů, umožňující sémantické názvy polí pomocí nové, efektivnější řazené kolekce členů typy řazené kolekce členů.

Řazená kolekce členů můžete vytvořit tak, že přiřadíte hodnotu k jednotlivým členům:

[!code-csharp[UnnamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#04_UnnamedTuple "Unnamed tuple")]

Který vytvoří přiřazení řazené kolekce členů obsahující `Item1` a `Item2`, který můžete použít stejným způsobem jako <xref:System.Tuple> změníte syntaxe pro vytvoření n-tice, která poskytuje sémantické názvy pro každého člena řazené kolekce členů:

[!code-csharp[NamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#05_NamedTuple "Named tuple")]

`namedLetters` Řazené kolekce členů obsahuje pole, které jsou označovány jako `Alpha` a `Beta`. Tyto názvy existují pouze v době kompilace a není zachováno například při kontrole řazené kolekce členů v době běhu pomocí operace reflection.

V přiřazení řazené kolekce členů můžete také zadat názvy polí na pravé straně přiřazení:

[!code-csharp[ImplicitNamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#06_ImplicitNamedTuple "Implicitly named tuple")]

Na levé a pravé straně přiřazení je možné zadat názvy pro pole:

[!code-csharp[NamedTupleConflict](../../../samples/snippets/csharp/new-in-7/program.cs#07_NamedTupleConflict "Named tuple conflict")]

Řádek nad generuje upozornění, `CS8123`, o tom, že názvy na pravé straně přiřazení `Alpha` a `Beta` budou ignorováni, protože jsou v konfliktu s názvy na levé straně `First` a `Second`.

Výše uvedené příklady ukazují základní syntaxe pro deklaraci řazené kolekce členů. Řazené kolekce členů jsou nejužitečnější jako typy vracených hodnot pro `private` a `internal` metody. Řazené kolekce členů poskytují jednoduché syntaxi pro tyto metody k vrácení více diskrétní hodnoty: Uložit práci při vytváření `class` nebo `struct` , který definuje typ vrácený. Není nutné pro vytvoření nového typu.

Vytvoření řazené kolekce členů je efektivnější a zvýšit produktivitu práce.
Je jednodušší a jednoduché syntaxe pro definování datová struktura, která provede více než jednu hodnotu. Následující příklad metoda vrátí minimální a maximální hodnoty nalezené v posloupnost celých čísel:

[!code-csharp[TupleReturningMethod](../../../samples/snippets/csharp/new-in-7/program.cs#08_TupleReturningMethod "Tuple returning method")]

Použití řazených kolekcí členů tímto způsobem nabízí několik výhod:

* Uložit práci při vytváření `class` nebo `struct` , který definuje typ vrácený. 
* Chcete-li vytvořit nový typ nepotřebujete.
* Vylepšení jazyka eliminuje nutnost volání <xref:System.Tuple.Create``1(``0)> metody.

Deklarace metody poskytuje názvy pro pole řazená kolekce členů, která je vrácena. Při volání metody, vrácená hodnota je řazené kolekce členů, jejichž pole jsou `Max` a `Min`:

[!code-csharp[CallingTupleMethod](../../../samples/snippets/csharp/new-in-7/program.cs#09_CallingTupleMethod "Calling a tuple returning method")]

Může nastat situace, kdy budete chtít rozbalit členy řazené kolekce členů, které byly vráceny z metody.  Můžete to udělat deklarací samostatné proměnných pro všechny hodnoty řazené kolekce členů. Tento postup se nazývá *dekonstrukce* řazené kolekce členů:

[!code-csharp[CallingWithDeconstructor](../../../samples/snippets/csharp/new-in-7/program.cs#10_CallingWithDeconstructor "Deconstructing a tuple")]

Můžete také zadat podobné dekonstrukce pro jakýkoli typ v rozhraní .NET. Je to realizuje zápisem `Deconstruct` metoda jako člen třídy. Že `Deconstruct` metoda poskytuje sadu `out` argumenty pro každou z vlastností, které mají být extrahovány. Zvažte proto `Point` třída, která poskytuje deconstructor metodu, která extrahuje `X` a `Y` souřadnice:

[!code-csharp[PointWithDeconstruction](../../../samples/snippets/csharp/new-in-7/point.cs#11_PointWithDeconstruction "Point with deconstruction method")]
 
Můžete extrahovat jednotlivá pole pomocí přiřazení `Point` k řazené kolekce členů:

[!code-csharp[DeconstructPoint](../../../samples/snippets/csharp/new-in-7/program.cs#12_DeconstructPoint "Deconstruct a point")]

Názvy definované v nejsou vázány `Deconstruct` metody. Extrakce proměnné můžete přejmenovat jako součást přiřazení:  

[!code-csharp[DeconstructNames](../../../samples/snippets/csharp/new-in-7/program.cs#13_DeconstructNames "Deconstruct with new names")]

Další podrobnosti v o řazenými kolekcemi členů v [řazených kolekcí členů tématu](../tuples.md).

## <a name="discards"></a>Zahození

Při často dekonstrukce řazené kolekce členů nebo volání metody s `out` parametry, budete muset definovat proměnnou jehož hodnota nezáleží a používat. C# přidává podporu pro *zahodí* tohoto scénáře. Zahození je proměnná jen pro zápis, jehož název je `_` (podtržítko); můžete přiřadit všechny hodnoty, které máte v úmyslu zahodit do jedné proměnné. Zahození je stejná jako nepřiřazené proměnné. Kromě příkazu přiřazení nelze použít zahození v kódu.

Zahození jsou podporovány v následujících scénářích:

* Když dekonstrukce řazených kolekcí členů nebo uživatelem definované typy.

* Při volání metody s [si](../language-reference/keywords/out-parameter-modifier.md) parametry.

* Ve vzorku s odpovídajícím operaci s [je](../language-reference/keywords/is.md) a [přepnout](../language-reference/keywords/switch.md) příkazy.

* Pokud chcete explicitně Identifikujte jako samostatné identifikátor hodnotu přiřazení jako zahození.

Následující příklad definuje `QueryCityDataForYears` metodu, která vrátí 6-n-tice, která obsahuje data pro město pro dvě různé roky. Volání metody v příkladu se týká pouze s hodnotami dva naplnění vrácený metodou a proto zpracuje zbývající hodnoty řazené kolekce členů jako zahodí při deconstructs řazené kolekce členů.

[!code-csharp[Tuple-discard](../../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Další informace najdete v tématu [zahodí](../discards.md).

## <a name="pattern-matching"></a>Porovnávání vzorů

*Porovnávání vzorů* je funkce, která umožňuje implementovat metodu odeslání na vlastnosti jiné než typu objektu. Už pravděpodobně již znáte odesílání metodu na základě typu objektu. Objektově orientované programování, virtuální a přepsání metody poskytují syntaxe jazyka pro implementaci metody odesílání na základě typu objektu. Základní a odvozené třídy poskytují tak různé implementace. Výrazy odpovídající vzor rozšiřte tento koncept tak, že je možné snadno implementovat podobné vzory odeslání pro typy a data prvky, které spolu nesouvisí prostřednictvím hierarchie dědičnosti. 

Porovnávání vzorů podporuje `is` výrazy a `switch` výrazy. Každý umožňuje kontrolu objektu a vlastností určíte, pokud daný objekt splňuje hledané kombinaci vzoru. Můžete použít `when` – klíčové slovo lze určit další pravidla se vzorem.

### <a name="is-expression"></a>`is` Výraz

`is` Výraz vzoru rozšiřuje známé [ `is` operátor](../language-reference/keywords/is.md#pattern-matching-with-is) k dotazování nad rámec jeho typ objektu.

Začněme pomocí jednoduchého scénáře. Přidáme možnosti pro tento scénář, které ukazují, jak vytvořit odpovídající výrazy vzor algoritmy, které pracují s nesouvisejících typů jednoduché. Začneme s metodou, která vypočítá součet počtu kostka zobrazí:

[!code-csharp[SumDieRolls](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#14_SumDieRolls "Sum die rolls")]

Můžete rychle zjistit, že je potřeba najít součet kostka zobrazí část zobrazí po provedena s emulátorem dice více (dice je plural kostka). Část vstupní sekvence může být více výsledků namísto jedno číslo:

[!code-csharp[SumDieRollsWithGroups](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#15_SumDieRollsWithGroups "Sum die rolls with groups")]

`is` Výraz vzoru poměrně dobře funguje v tomto scénáři. Jako součást kontrolu typu můžete zapsat inicializaci proměnné. Tím se vytvoří novou proměnnou typu ověřené modulu runtime.

Jak zachovat rozšíření scénářů, může být pro vás vytvořit více `if` a `else if` příkazy. Po, který nepraktický, budete pravděpodobně chtít přepnout na `switch` vzorku výrazy.

### <a name="switch-statement-updates"></a>`switch` aktualizace – příkaz

*Odpovídat výrazu* má známou syntaxi, na základě `switch` příkaz již součástí jazyka C#. Umožňuje převést existující kód, který použije odpovídající výraz před přidáním nové případy: 

[!code-csharp[SumUsingSwitch](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#16_SumUsingSwitch "Sum using switch")]

Výrazy shody mají mírně odlišnou syntaxi než `is` výrazy, ve kterém je deklarovat typ a proměnné na začátku `case` výrazu.

Výrazy shody také podporují konstanty. To ušetřit čas tím, které budou zohledňovat si jednoduchý případy:

[!code-csharp[SwitchWithConstants](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#17_SwitchWithConstants "Switch with constants")]

Výše uvedený kód přidá případy `0` jako speciální případ `int`, a `null` ve speciálním případě pokud neexistuje žádný vstup. Tento příklad ukazuje jednu důležitou novou funkci ve výrazech vzor přepínač: pořadí `case` výrazy nyní věcech. `0` Případu musí být uvedena před Obecné `int` případ. V opačném případě by být první odpovídající vzor `int` případu, dokonce i když je hodnota `0`. Pokud omylem výrazech pořadí tak, aby novější případ již byla zpracována, kompilátor se příznak, který a vygenerují chybu.

Toto chování stejné umožňuje zvláštní případ pro prázdný vstupní sekvence.
Vidíte, že v případě `IEnumerable` položku, která má elementy se musí nacházet před Obecné `IEnumerable` případ.

Tato verze také přidal `default` případ. `default` Případ je vyhodnocen vždy poslední, bez ohledu na to, pořadí se zobrazí ve zdroji. Z tohoto důvodu je konvence vložit `default` případu poslední.

Nakonec přidáme jeden poslední `case` pro nový styl kostka. Některé hry pomocí percentilu dice představovat větší rozsah čísel. 

> [!NOTE]
> Dva oboustranný 10 percentilu dice může představovat všechna čísla od 0 do 99. Jedna kostka má strany označeny `00`, `10`, `20`,... `90`. Další kostka má strany s popiskem `0`, `1`, `2`,... `9`. Přidat hodnoty dvou kostka společně a získáte všechna čísla od 0 až 99.

Chcete-li přidat tento druh kostka do kolekce, nejprve definujte typů k vyjádření rozčlenění percentil. `TensDigit` Vlastnosti se ukládají hodnoty `0`, `10`, `20`, až `90`:

[!code-csharp[18_PercentileDice](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#18_PercentileDice "Percentile Die type")]

Pak přidejte `case` odpovídat výrazu pro nový typ:

[!code-csharp[SwitchWithNewTypes](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#19_SwitchWithNewTypes "Include Percentile Die type")]

Nová syntaxe výrazů pro porovnávání usnadňuje vytvoření odeslání algoritmů na základě typu objektu nebo dalších vlastností, pomocí jasné a stručné syntaxe. Vzor odpovídající výrazy umožňují tyto konstrukce pro datové typy, které jsou nesouvisející prostřednictvím dědičnosti.

Další informace o porovnávání vzorů v tématu vyhrazený pro [porovnávání vzorů v jazyce C#](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Místní referenční hodnoty a vrátí

Tato funkce umožňuje algoritmy, které používají a vrátit odkazy na proměnné definované jinde. Jedním z příkladů je práce s velké matice a hledání na jednom místě s určité vlastnosti. Jedna metoda vrátí dva indexy na jednom místě v matici:

[!code-csharp[FindReturningIndices](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#20_FindReturningIndices "Find returning indices")]

Existuje mnoho problémů s tímto kódem. Za prvé je veřejná metoda, která vrací řazenou kolekci členů. Jazyk podporuje, ale uživatelsky definované typy (třídy nebo struktury) jsou upřednostněny veřejných rozhraní API.

Za druhé tato metoda vrací indexy na položku v matici.
Který vede volajícím napsat kód, který používá tyto indexy přistoupit přes ukazatel matice a upravovat jeden element:

[!code-csharp[UpdateItemFromIndices](../../../samples/snippets/csharp/new-in-7/program.cs#21_UpdateItemFromIndices "Update Item From Indices")]

Měli byste spíše napsat metodu, která vrátí *odkaz* na prvek matrice, který chcete změnit. Může to provést pouze pomocí nezabezpečený kód a vrací ukazatel na `int` v předchozích verzích.

Projděme si prostřednictvím řady změn k předvedení funkcí místní ref a ukazují, jak vytvořit metodu, která vrátí odkaz na interní úložiště.
Na cestě se dozvíte pravidla vrácených hodnot ref a ref místní funkce, která chrání proti náhodnému zneužití.

Začněte tím, že změna `Find` deklarace metody tak, aby se `ref int` místo řazené kolekce členů. Potom upravte příkaz return tak, aby vracel hodnotu uloženou v matici místo dvou indexů:

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

Pokud deklarujete, metoda vrátí `ref` proměnné, je nutné přidat také `ref` – klíčové slovo pro každý příkaz return. Který označuje návrat podle odkazu a pomáhá vývojářům čtení kódu později mějte na paměti, že metoda vrací odkazem:

[!code-csharp[FindReturningRef](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#22_FindReturningRef "Find returning by reference")]

Teď, když metoda vrátí odkaz na celočíselnou hodnotu v matici, budete muset upravit, kde je volán.  `var` Prohlášení znamená, že `valItem` je teď `int` místo řazené kolekce členů:

[!code-csharp[AssignRefReturnToValue](../../../samples/snippets/csharp/new-in-7/program.cs#23_AssignRefReturnToValue "Assign ref return to value")]

Druhá `WriteLine` příkaz v předchozím příkladu vytiskne hodnotu `42`, nikoli `24`. Proměnná `valItem` je `int`, nikoli `ref int`. `var` – Klíčové slovo umožňuje kompilátoru k určení typu, ale nepřidá implicitně `ref` modifikátor. Místo toho hodnota odkazuje `ref return` je *zkopírovat* do proměnné na levé straně přiřazení. Proměnná není `ref` místní.

Aby bylo možné získat výsledek má, budete muset přidat `ref` modifikátoru deklarace lokální proměnné při vrácená hodnota je odkaz vytvořit odkaz proměnnou:

[!code-csharp[AssignRefReturn](../../../samples/snippets/csharp/new-in-7/program.cs#24_AssignRefReturn "Assign ref return")]

Nyní, druhý `WriteLine` příkaz v předchozím příkladu se vytiskne hodnotu `24`, označující, že byla změněna úložiště v matici. Lokální proměnná jsou deklarované v rámci `ref` modifikátor který bude trvat `ref` vrátit. Je nutné inicializovat `ref` proměnné při deklaraci, nelze rozdělit deklaraci a inicializaci.

Jazyk C# má tři další pravidla, které chrání vás před zneužitím `ref` místní hodnoty a vrátí:

* Nelze přiřadit standardní metoda návratovou hodnotu pro `ref` místní proměnné.
    - Který zakazuje příkazy jako `ref int i = sequence.Count();`
* Nelze vrátit `ref` do proměnné, jehož doba života nerozšiřuje nad rámec provádění metody.
    - To znamená, že nejde vrátit odkazem na místní proměnná nebo proměnná se podobně jako obor.
* `ref` místní hodnoty a vrátí nelze použít u asynchronních metod.
    - Kompilátor nemůže vědět, pokud odkazovaná proměnná je nastavená na jeho konečnou hodnotu po návratu asynchronní metody.

Přidání místní referenční hodnoty a ref vrátí povolit algoritmy, které jsou efektivnější se vyhnout kopírování hodnot nebo provádění operací přesměrování více než jednou.

Přidání `ref` návratová hodnota je [zdroj kompatibilní změnu](version-update-considerations.md#source-compatible-changes). Stávající kód zkompiluje, ale ref návratové hodnoty je zkopírován při přiřazení. Volající musí aktualizovat úložiště pro návratovou hodnotu `ref` místní proměnnou pro uložení vrácení jako odkaz.

Další informace najdete v tématu [ref – klíčové slovo](../language-reference/keywords/ref.md) článku.

## <a name="local-functions"></a>Lokální funkce

Řada návrhů pro třídy zahrnují metody, které se volají z jediného umístění. Tyto další metody privátní zachovat každá metoda malém rozsahu a zaměřeně. Však budou mít je těžší porozumět přečtením první třídy. Tyto metody musí být srozumitelný mimo kontext z jednoho místa volání.

Pro tyto návrhy *lokální funkce* umožňují deklarovat metody v kontextu jinou metodu. To usnadňuje pro čtenáře třídy zobrazíte, že místní metoda je volána pouze z kontextu, ve kterém je deklarována.

Existují dva velmi běžné případy použití pro lokální funkce: veřejné iterátory a veřejné asynchronní metody. Oba typy metod generování kódu, který bude hlásit chyby později, než se dalo očekávat programátory. V případě metody iterátoru, všechny výjimky, jsou dodržovány pouze při volání metody kód, který uvádí, že vrácená sekvence. V případě asynchronní metody, všechny výjimky jsou pouze dodržovat při vráceného `Task` je očekáváno.

Začněme iterační metodu:

[!code-csharp[IteratorMethod](../../../samples/snippets/csharp/new-in-7/Iterator.cs#25_IteratorMethod "Iterator method")]

Zkontrolujte následující kód, který zavolá metodu iterátoru nesprávně:

[!code-csharp[CallIteratorMethod](../../../samples/snippets/csharp/new-in-7/program.cs#26_CallIteratorMethod "Call iterator method")]

Výjimka je vyvolána, když `resultSet` provést iteraci, ne když `resultSet` se vytvoří.
V tomto příkladu omezením Většina vývojářů může rychle diagnostikovat problém. V větší základů kódu, kód, který vytvoří iterátor, často se podobají kódu, který se zobrazí výsledek. Možné Refaktorovat kód, tak, aby veřejné metody ověří všechny argumenty a generuje výčet privátní metodu:

[!code-csharp[IteratorMethodRefactored](../../../samples/snippets/csharp/new-in-7/Iterator.cs#27_IteratorMethodRefactored "Iterator method refactored")]

Tato verze refaktorovaný vyvolají výjimky okamžitě, protože není veřejná metoda metodu iterátoru; jenom privátní metoda používá `yield return` syntaxe. Existují však potenciální problémy s Tento refaktoring. Privátní metoda pouze lze volat z metodu veřejného rozhraní, protože jinak se přeskočí všechny ověřování argumentu.
Čtenáři třídy musí tuto skutečnost zjišťovat, že čtení celé třídy a vyhledáte všechny odkazy na `alphabetSubsetImplementation` metody.

Záměr tohoto návrhu můžete vytvořit více vymazat deklarací `alphabetSubsetImplementation` jako lokální funkce uvnitř metody veřejné rozhraní API:

[!code-csharp[22_IteratorMethodLocal](../../../samples/snippets/csharp/new-in-7/Iterator.cs#28_IteratorMethodLocal "Iterator method with local function")]

Výše uvedené verze je zřejmé, na který odkazuje místní metodu pouze v kontextu vnější metody. Pravidla pro lokální funkce také zajistěte, aby vývojář nesmí omylem z jiného umístění ve třídě zavolejte funkci Místní a obejít ověřování argumentu.

Stejným způsobem mohou být použity s `async` metody k zajištění, že výjimky vyplývající z ověřování argumentu jsou vyvolány před zahájením asynchronní práce:

[!code-csharp[TaskExample](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

> [!NOTE]
> Některé návrhy, které jsou podporovány lokální funkce také je možné dosáhnout použitím *výrazy lambda*. Tyto zúčastněné můžete [Další informace o rozdílech](../local-functions-vs-lambdas.md)

## <a name="more-expression-bodied-members"></a>Více členů s výrazem v těle

C# 6 zavedené [členové tvoření](csharp-6.md#expression-bodied-function-members) pro členské funkce a vlastnosti jen pro čtení. C# 7.0 rozšíří povolené členy, které je možné implementovat jako výrazy. V jazyce C# 7.0, můžete implementovat *konstruktory*, *finalizační metody*, a `get` a `set` přistupující objekty na *vlastnosti* a *indexerů* . Následující kód ukazuje příklady každé:

[!code-csharp[ExpressionBodiedMembers](../../../samples/snippets/csharp/new-in-7/expressionmembers.cs#36_ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> V tomto příkladu nemusí finalizační metodu, ale je zobrazena na ukazují syntaxi. Finalizační metody by neměla implementovat ve své třídě, pokud to není nutné k uvolnění nespravovaných prostředků. Měli byste také zvážit použití <xref:System.Runtime.InteropServices.SafeHandle> třídy místo správy nespravované prostředky přímo.

Tato nová umístění pro členy s výrazem v těle představuje důležitý milník pro C# jazyka: Tyto funkce byly implementované členy komunity open source pracovali [Roslyn](https://github.com/dotnet/Roslyn) projektu.

Změna metody na výrazu vozidlo člena je [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Vyvolání výrazů

V jazyce C# `throw` vždy bylo příkazu. Protože `throw` je příkaz, není výraz, že byly konstrukce jazyka C#, ve kterém nelze použít. Tyto uvedeny podmíněné výrazy, null slučovací výrazy a některé výrazy lambda. Přidání členů s výrazem v těle přidá více míst kde `throw` výrazů může být užitečné. Aby mohla zapisovat některý z těchto konstruktorů, C# 7.0 zavádí *vyvolání výrazů*.

Syntaxe je stejná jako vždy jste použili pro `throw` příkazy. Jediným rozdílem je, že teď můžete umístit je do nového umístění, například jako podmíněný výraz:

[!code-csharp[Throw_ExpressionExample](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#37_Throw_ExpressionExample "conditional throw expressions")]

Tato funkce umožňuje pomocí výrazů throw v výrazy inicializace:

[!code-csharp[ThrowInInitialization](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#38_ThrowInInitialization "conditional throw expressions")]

Tyto inicializace by dříve, musí být v konstruktoru, s příkazy throw v těle konstruktoru:


[!code-csharp[ThrowInConstructor](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#39_ThrowInConstructor "throw statements")]

> [!NOTE]
> Obě předchozí konstruktorů způsobí, že výjimky, která je vyvolána během konstrukce objektu. Ty je často obtížné provést obnovení.
> Z tohoto důvodu se nedoporučuje návrhy, které vyvolají výjimky během konstrukce.

## <a name="generalized-async-return-types"></a>Zobecněný asynchronní návratové typy

Vrácení `Task` objekt z asynchronní metody můžete zavést problémových míst výkonu v určitých cestách. `Task` je typem odkazu, takže ho pomocí znamená, že přidělování objektu. V případech, kde metoda deklarována s `async` modifikátor vrátí výsledky uložené v mezipaměti, nebo dokončí synchronně, navíc přidělení se může stát spoustu času náklady na kritické oddíly výkon kódu. Může být velmi náročná, pokud dojde k těmto přidělení v těsné smyčky.

Nové funkce jazyka znamená, že asynchronní metody může vrátit jiné typy kromě `Task`, `Task<T>` a `void`. Vrácený typ musí splňovat stále asynchronní vzorek, což znamená `GetAwaiter` metoda musí být přístupná. Jako konkrétní příklad `ValueTask` typ byl přidán do rozhraní .NET framework, aby pomocí této nové funkce jazyka: 

[!code-csharp[UsingValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#30_UsingValueTask "Using ValueTask")]

> [!NOTE]
> Je potřeba přidat balíček NuGet [ `System.Threading.Tasks.Extensions` ](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) Chcete-li použít <xref:System.Threading.Tasks.ValueTask%601> typu.

Jednoduché optimalizace může být použití `ValueTask` v místech, kde `Task` by se použily před. Ale pokud chcete provést další optimalizace ručně, můžete výsledky z asynchronní práce do mezipaměti a znovu použít výsledek v následných voláních. `ValueTask` Struktura obsahuje konstruktor s `Task` parametru tak, že můžete vytvořit `ValueTask` z existující asynchronní metody na návratový typ:

[!code-csharp[AsyncOptimizedValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#31_AsyncOptimizedValueTask "Return async result or cached value")]

Jak se všechna doporučení k výkonu, můžete by měl srovnávací testy obě verze před provedením velké škálování změny v kódu.

Pokud vrácená hodnota je cílem `await` příkaz změny rozhraní API z <xref:System.Threading.Tasks.Task%601> k <xref:System.Threading.Tasks.ValueTask%601> je [zdroj kompatibilní změnu](version-update-considerations.md#source-compatible-changes). Obecně platí, změna `ValueTask` není.

## <a name="numeric-literal-syntax-improvements"></a>Vylepšení číselný literál syntaxe

Číselné konstanty misreading může znesnadnit pochopení kódu při čtení poprvé. Tato situace často nastává, když těchto čísel se používají jako bitové masky nebo jiných symbolické namísto číselných hodnot. C# 7.0 obsahuje dvě nové funkce, které usnadňují zápis čísla způsobem nejvíce čitelné pro zamýšlené použití: *binární literály:*, a *oddělovače číslic:*.

Pro situace, při vytváření bitové masky, nebo když se binární vyjádření čísla je nejvíce čitelné kód zápis tohoto čísla v binárním souboru:

[!code-csharp[BinaryConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#32_BinaryConstants "Binary constants")]

`0b` Na začátku konstanty Určuje, že číslo je zapsán jako binární číslo.

Můžete získat tak, aby byl často snazší zjistit bitové vzory zavedením příliš dlouho, binárních čísel `_` jako oddělovač číslic:

[!code-csharp[ThousandSeparators](../../../samples/snippets/csharp/new-in-7/Program.cs#33_ThousandSeparators "Thousands separators")]

Oddělovač číslic může vyskytovat kdekoli v konstantě. Pro základní 10 čísel, bylo by běžné použití jako tisíců oddělovač:

[!code-csharp[LargeIntegers](../../../samples/snippets/csharp/new-in-7/Program.cs#34_LargeIntegers "Large integer")]

Oddělovač číslic jde použít s `decimal`, `float` a `double` typy a také:

[!code-csharp[OtherConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#35_OtherConstants "non-integral constants")]

Dohromady, je možné deklarovat číselné konstanty s mnohem více čitelnost.
