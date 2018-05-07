---
title: Co je nového v jazyce C# 6 – Průvodce v C#
description: Informace o nových funkcích v C# verze 6
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: 00aeb3ed940acfca748a1a9eb876fd0133baf6c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-c-6"></a>Co je nového v jazyce C# 6

6.0 verze jazyka C# obsahuje řadu funkcí, které zvýšení produktivity pro vývojáře. Funkce v této verzi patří:

* [Auto vlastnosti jen pro čtení](#read-only-auto-properties):
    - Můžete vytvořit jen pro čtení automaticky – vlastnosti, které lze nastavit pouze v konstruktory.
* [Inicializátory automaticky vlastnost](#auto-property-initializers):
    - Můžete napsat inicializace výrazy pro nastavení počáteční hodnota auto vlastnosti.
* [Výraz vozidlo funkce členy](#expression-bodied-function-members):
    - Můžete vytvořit metody jednořádkové použití výrazů lambda.
* [pomocí statické](#using-static):
    - Všechny metody jedné třídy můžete importovat do aktuální obor názvů.
* [Null – podmíněné operátory](#null-conditional-operators):
    - Můžete výstižně a bezpečně přistupovat členům v objektu při kontrole stále null s podmíněný operátor s hodnotou null.
* [Řetězec interpolace](#string-interpolation):
    - Můžete napsat řetězec formátování výrazy pomocí vložené výrazy místo poziční argumenty.
* [Filtry výjimek](#exception-filters):
    - Můžete zachytit výrazy na základě vlastností výjimku nebo jiný stav programu. 
* [nameof výrazy](#nameof-expressions):
    - Můžete je nechat kompilátoru generovat řetězcové vyjádření symbolů.
* [await v catch a nakonec blokuje](#await-in-catch-and-finally-blocks):
    - Můžete použít `await` výrazy v umístění, které dříve je zakázána.
* [index inicializátory](#index-initializers):
    - Můžete vytvářet inicializace výrazy pro asociativní kontejnery, jakož i kontejnery pořadí.
* [Rozšiřující metody pro Inicializátory kolekcí](#extension-add-methods-in-collection-initializers):
    - Inicializátory kolekcí může se spoléhat na dostupné rozšiřující metody, kromě metod člen.
* [Vylepšené rozlišení přetížení](#improved-overload-resolution):
    - Některé konstruktory, které dříve generovány volání metod nejednoznačný nyní správně přeložit.

Celkový efekt těchto funkcí je psaní přesnější kód, který je také lépe čitelný. Syntaxe obsahuje menší procedury pro mnoho běžné postupy. Je snazší zjistit záměr návrh s menší procedury. Tyto funkce a další a budete zvýšit produktivitu, napsat srozumitelnější kód a více soustředit na základní funkce, než na konstrukce jazyka.

Zbývající část tohoto tématu poskytuje podrobné informace o jednotlivých funkcí.

## <a name="auto-property-enhancements"></a>Vylepšení automatického – vlastnost 

Syntaxe automaticky implementované vlastnosti (obvykle označuje jako 'auto vlastnosti') provedené velmi snadné vytváření vlastnosti, které měl jednoduché get a nastavení přístupových objektů:

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

Tento jednoduchý syntaktický však omezenou druhy vzorů, které může podporovat použití automatického vlastnosti. C# 6 vylepšuje možnosti automatického vlastnosti tak, aby je mohli používat další způsoby. Nebudete muset přejít na podrobnější syntaxe deklarace a manipulace s nimi pole Základní ručně tak často.

Nové syntaxe adresy scénáře vlastnosti jen pro čtení a inicializace proměnné úložiště za auto vlastnost.

### <a name="read-only-auto-properties"></a>Auto vlastnosti jen pro čtení

*Auto vlastnosti jen pro čtení* poskytnout přesnější syntaxe k vytvoření nedá změnit typy. Na nejbližší, které může dojít k neměnné typy v dřívějších verzích systému C# byla deklarovat privátní setter:

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
Pomocí této syntaxe, kompilátor není zajistěte, aby byl typ skutečně neměnné. Pouze vynucuje, který `FirstName` a `LastName` vlastnosti nejsou změnit tak, že žádný kód mimo třídu.

Hodnota true, jen pro čtení chování povolit automatické – vlastnosti jen pro čtení. Je s pouze přistupující deklarovat vlastnost automaticky:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

`FirstName` a `LastName` vlastnosti lze nastavit pouze v těle konstruktor:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Při operaci set `LastName` v jiné metody generuje `CS0200` došlo k chybě kompilace:

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

Tato funkce umožňuje true jazyková podpora pro vytváření neměnné typy a pomocí syntaxe zkracují a pohodlný vlastnost automaticky.

### <a name="auto-property-initializers"></a>Inicializátory automaticky – vlastnost

*Inicializátory automaticky vlastnost* umožňují deklarovat počáteční hodnota auto-vlastnosti jako součást deklarace vlastnosti.  V dřívějších verzích tyto vlastnosti třeba, aby měl setter a museli byste se inicializovat úložiště dat používá pole zálohování pomocí tohoto nastavení. Vezměte v úvahu tato třída pro studenty, který obsahuje název a seznam tříd Studentova:

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
S růstem této třídy může zahrnovat další konstruktory. Každý konstruktor musí inicializovat toto pole, nebo budete zavádět chyby.

C# 6 umožňuje přiřadit počáteční hodnotu pro úložiště používá vlastnost automaticky v deklaraci automaticky vlastnost:

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` Člen je inicializován, kde je deklarován. Který usnadňuje provést inicializaci právě jednou. Inicializace je součástí deklarace vlastnosti, což usnadňuje označení rovnosti přidělení úložiště s veřejné rozhraní pro `Student` objekty.

Inicializátory vlastnost lze použít s vlastností čtení/zápisu a také vlastnosti jen pro čtení, jak je uvedené v tomto poli.

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a>Výraz vozidlo funkce členy

Tělo mnoho členů, které jsme zapsat obsahovat pouze jeden příkaz, který může být reprezentován jako výraz. Zápisem člena výraz vozidlo místo toho můžete snížit této syntaxe. Funguje pro metody a vlastnosti jen pro čtení. Například přepsání `ToString()` je často skvělé kandidátem:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

V také vlastnosti jen pro čtení můžete použít také výraz vozidlo členy:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a>pomocí statické

*Pomocí statické* vylepšení umožňuje importovat statické metody třídy jednu třídu. Dříve `using` příkaz naimportovány všechny typy v oboru názvů. 

Statické metody třídy se často používáme v našem kódu. Opakovaně zadáním názvu třídy mohou skrývat význam kódu. Běžným příkladem jsou při psaní třídy, které provádějí mnoho číselné výpočty.
Váš kód podestlána <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> a další volání různé metody v <xref:System.Math> třídy. Nové `using static` syntaxe provádět tyto třídy mnohem čisticí ke čtení. Zadejte třídu, kterou používáte:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

A teď můžete použít libovolnou statickou metodu v <xref:System.Math> třída bez kvalifikace <xref:System.Math> třídy. <xref:System.Math> Třída je případ skvělé použití pro tuto funkci, protože neobsahuje žádné instance metody. Můžete také použít `using static` k importu třída statické metody pro třídu, která má statické a instance metody. Jedním z příkladů je nejvhodnější je <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Je nutné použít plně kvalifikovaný název, `System.String` v statického pomocí příkazu. Nelze použít `string` – klíčové slovo místo. 

Nyní můžete volat statické metody definované v <xref:System.String> třída bez kvalifikace tyto metody jako členy této třídy:

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

`static using` Funkce a rozšíření metody pracovat zajímavými způsoby a jazyk návrhu zahrnuté některá pravidla, které konkrétně řeší tyto interakce. Cílem je, chcete-li minimalizovat žádné pravděpodobnost nejnovější změny v existující základy kódu, včetně vašeho.

Rozšiřující metody jsou pouze v oboru při volání pomocí syntaxe volání metody rozšíření, ne v případě, že se říká statickou metodu.
To se často zobrazí v dotazech LINQ. Můžete importovat vzoru LINQ importováním <xref:System.Linq.Enumerable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

To importuje všechny metody v <xref:System.Linq.Enumerable> třídy.
Rozšiřující metody jsou však pouze v oboru při volání jako rozšiřující metody. Nejsou v oboru Pokud jsou volány pomocí syntaxe statickou metodu:

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

Toto rozhodnutí totiž rozšiřující metody jsou obvykle nazývá pomocí výrazů volání metody rozšíření. Ve výjimečných případu, kdy jsou volány pomocí statickou metodu volejte syntaxe je vyřešit nejednoznačnosti.
Vyžadování název třídy jako součást volání zdá se, že vhodné.

Je poslední funkce z `static using`. `static using` – Direktiva také importuje všechny vnořené typy. Můžete odkazovat všechny vnořené typy bez kvalifikace.

## <a name="null-conditional-operators"></a>Podmíněné operátory s Null

Hodnoty Null zkomplikovat kódu. Je potřeba zkontrolovat každých přístup proměnných zajistit nejsou vyhodnocení `null`. *Null podmíněný operátor* díky ty kontroly mnohem snazší a plynulá práce.

Jednoduše nahradit přístup ke členu `.` s `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

V předchozím příkladu, proměnná `first` je přiřazen `null` Pokud je objekt osoba `null`. Jinak, získá přiřadí hodnota `FirstName` vlastnost. Co je nejdůležitější `?.` znamená, že tento řádek kódu negeneruje `NullReferenceException` při `person` proměnná `null`. Místo toho zkratům a vytváří `null`.

Také Upozorňujeme, že tento výraz vrátí `string`, bez ohledu na to hodnota `person`.
V případě krátké circuiting `null` hodnota vrácená je zadán tak, aby odpovídaly úplné výraz.

Často můžete použít tento konstrukce s *null slučování* operátor přiřadit výchozí hodnoty, když jedna z vlastností `null`:

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Operand pravé straně `?.` operátor není omezen na vlastnosti nebo pole.
Můžete ji použít i podmíněně volat metody. Se nejčastěji používá členských funkcí s hodnotou null podmíněný operátor bezpečně volat delegáti (nebo obslužné rutiny událostí), může být `null`.  Můžete to udělat pomocí volání metody delegáta `Invoke` metoda pomocí `?.` operátor pro přístup k členovi. Můžete zobrazit příklad v  
[Delegovat vzory](../delegates-patterns.md#handling-null-delegates) tématu.

Pravidla `?.` operátor Ujistěte se, že je na levé straně operátoru vyhodnotit pouze jednou. To je důležité a umožňuje mnoho idioms, včetně příklad pomocí obslužných rutin událostí. Začněme využití obslužná rutina události. V předchozích verzích jazyka C# byli vyzváni k zápisu kódu takto:

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

To se upřednostňované přes jednodušší syntaxe:

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> V předchozím příkladu představuje časování. `SomethingHappened` Událost může mít Odběratelé, kteří v případě zaškrtnutí proti `null`, a tyto odběratele byl odebrán předtím, než se vyvolá událost. By to způsobilo <xref:System.NullReferenceException> vyvolání.

V této verzi druhý `SomethingHappened` obslužné rutiny události může obsahovat hodnotu null při testování, ale pokud jiný kód odebere obslužnou rutinu, ho může mít hodnotu null při volání obslužné rutiny události.

Generuje kód pro kompilátor `?.` operátor, který zajišťuje na levé straně (`this.SomethingHappened`) z `?.` výraz vyhodnocen jednou a výsledek je uložený v mezipaměti:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Zajištění, že je na levé straně vyhodnotit pouze jednou můžete také použít libovolný výraz, včetně volání metod, na levé straně `?.` i v případě, že musí vedlejší účinky, jsou vyhodnocovány jednou, takže vedlejší účinky nastane jenom jednou. Můžete zobrazit příklad v našem obsahu na [události](../events-overview.md#language-support-for-events).

## <a name="string-interpolation"></a>Řetězec interpolace

C# 6 obsahuje nové syntaxe pro sestavování řetězců z formátovacího řetězce a výrazy, které se vyhodnocují k vytvoření dalších řetězcové hodnoty.

Tradičně, je potřeba k použití poziční parametry v metodě jako `string.Format`:

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

S C# 6 nové [řetězec interpolace](../language-reference/tokens/interpolated.md) funkce umožňuje vložení výrazů do řetězce formátu. Jednoduše adresa řetězec s `$`:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Tento počáteční příklad používá vlastnost výrazy pro nahrazovanou výrazy. Můžete rozbalit na tuto syntaxi použít jakýkoli výraz. Například může výpočetní Studentova průměr studijních jako součást interpolace:

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

Spuštěný v předchozím příkladu, by zjistíte, že výstup `Grades.Average()` může mít většího počtu desetinných míst, než byste chtěli. Syntaxe interpolace řetězec podporuje všechny na formát řetězce k dispozici pomocí dříve formátování metody. Můžete přidat řetězce formátu uvnitř složené závorky. Přidat `:` následující výraz, který se formátu:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Naformátuje hodnotu pro předchozí řádek kódu `Grades.Average()` jako číslo s plovoucí desetinnou čárkou se dvěma desetinnými místy.

`:` Vždy interpretována jako oddělovač mezi výraz, který je formátován a řetězec formátu. To může nastat problémy při výraz používá `:` jiným způsobem, jako je například podmíněný operátor:

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

V předchozím příkladu `:` je analyzovat jako začátek řetězec formátu, nejsou součástí podmíněný operátor. Ve všech případech, kdy k tomu dojde je nutné uvést výrazu v závorkách vynutit kompilátoru interpretovat výraz jako, který chcete:

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

Nejsou k dispozici žádné omezení na výrazy, které můžete umístit mezi složenými závorkami. Můžete provést komplexní dotaz LINQ uvnitř řetězec interpolované k provádění výpočtů a zobrazit výsledek:

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

Zobrazí se od této ukázky můžete dokonce vkládat řetězcového výrazu interpolace uvnitř jiného výrazu interpolace řetězec. V tomto příkladu je velmi pravděpodobné, by měly být složitější než jste v produkčním kódu.
Místo toho je ilustrativní šířky funkci. Jakýkoli výraz jazyka C# mohou být umístěny ve složených závorkách interpolované řetězce.

### <a name="string-interpolation-and-specific-cultures"></a>Řetězec interpolace a konkrétní jazykové verze

Všechny příklady uvedené v předchozí části formátu řetězce pomocí aktuální jazykovou verzi a jazyka v počítači kde kód spustí. Potřebujete často řetězec vytvořeného pomocí konkrétní jazykové verze formátu.
Pokud chcete provést, použijte ke skutečnosti, že objekt vyprodukované interpolace řetězec může být implicitně převedena na <xref:System.FormattableString>.

<xref:System.FormattableString> Instance obsahuje řetězec formátu a výsledky vyhodnocení výrazů před jejich převádění na řetězce. Můžete použít veřejné metody třídy <xref:System.FormattableString> zadat jazykovou verzi, při formátování řetězce. Například následující příklad vytvoří řetězec s využitím německé jazykové verze. (Používá znak ',' oddělovač desetinných míst a '.' tisíce znak oddělovače.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Další informace najdete v tématu [řetězec interpolace](../language-reference/tokens/interpolated.md) tématu.

## <a name="exception-filters"></a>Filtry výjimek

Další novou funkcí v C# 6 je *filtry výjimek*. Filtry výjimek jsou klauzule, které určují, kdy se má použít klauzuli dané catch.
Pokud se používá pro filtr výjimek vyhodnocen jako `true`, klauzuli catch provádí běžného zpracování výjimku. Pokud je výsledkem výrazu `false`, pak se `catch` klauzule bylo přeskočeno.

Je jedno použití zjistit informace o výjimce k určení, zda `catch` klauzule může zpracovat výjimku:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

Kód vygenerovaný filtry výjimek poskytuje lepší informace o výjimku, která je vyvolána a nebyl zpracován. Před filtry výjimek byly přidány do jazyka, museli byste vytvořit kód takto:

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

Bod, kde je vyvolána výjimka změny mezi tyto dva příklady.
V předchozí kód, kde `throw` klauzule, všechny analýzu trasování zásobníku nebo zkoumání výpisy stavu systému se zobrazí, zda byla výjimka vydána z `throw` příkaz v klauzuli vaší catch. Objekt skutečné výjimky bude obsahovat původní zásobníku volání, ale všechny ostatní informace o všech proměnných v zásobníku volání mezi tento bod throw a umístění původního bodu throw bylo ztraceno. 

Rozdíl oproti, zpracování kód pomocí filtru výjimek: výjimka výraz filtru se vyhodnocuje `false`. Proto nikdy zadá provádění `catch` klauzule. Protože `catch` klauzule nepracuje, bez uvolnění zásobníku probíhá. Pro všechny ladění aktivity, které by proběhnout později je zachovaná, throw znamená původní umístění.

Kdykoli budete potřebovat k vyhodnocení, pole nebo vlastnosti výjimky, aniž byste museli spoléhat výhradně na typ výjimky, použijte filtr výjimek pro zachování Další informace o ladění.

Další doporučené vzor s filtry výjimek je používat pro rutiny protokolování. Toto použití také využívá způsobem, ve kterém je zachová bodem throw výjimky, i když se vyhodnocuje filtru výjimek `false`.

Metoda protokolování by metodou, jehož argumentem je výjimka, která bezpodmínečně vrací `false`:

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

Vždy, když chcete k přihlášení k výjimce, můžete přidat klauzuli catch a použít tuto metodu jako filtr výjimek:

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

Výjimky jsou nikdy zachycena, protože `LogException` metoda vždy vrátí hodnotu `false`. Tento filtr výjimek vždy false znamená, že můžete umístit této obslužné rutiny protokolování před všechny ostatní obslužné rutiny výjimek:

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

V předchozím příkladu zvýrazňuje důležité omezující vlastnosti výjimky filtrů.
Filtry výjimek povolit scénáře, kde může před více některou zobrazí další obecné klauzule catch výjimky. Je také možné, že se zobrazí v více klauzulí catch stejného typu Výjimka:

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

Další doporučené vzor pomáhá zabránit klauzule catch – zpracování výjimek, pokud je připojen ladicí program. Tento postup umožňuje spuštění aplikace s ladicím programem a zastavit provádění, když je vyvolána výjimka.

V kódu přidejte filtr výjimek tak, aby všechny kód pro obnovení se provádí jenom v případě, že není připojen ladicí program:

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

Po přidání tohoto v kódu, můžete nastavit ladicí program na přerušení na všechny neošetřené výjimky. Ladicí program konce kdykoli a spusťte program v ladicím programu `PerformFailingOperation()` vyvolá `RecoverableException`.
Ladicí program dělí program, protože klauzule catch nebudou provedeny z důvodu výjimky filtr vrací hodnotu false.

## <a name="nameof-expressions"></a>`nameof` Výrazy

`nameof` Výraz vyhodnocen jako název symbolu. Je skvělým způsobem, jak získat nástroje práce kdykoli budete potřebovat název proměnné, vlastnost nebo pole členů.

Mezi nejběžnější používá pro `nameof` je poskytnout název symbol, který způsobil výjimku:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Použití jiné je XAML na základě aplikací, které implementují `INotifyPropertyChanged` rozhraní:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

Výhodou použití `nameof` operátor přes konstantní řetězec je, že nástroje můžete porozumět symbolu. Používáte-li přejmenovat symbol refaktoringu nástroje, můžete ho přejmenuje ho `nameof` výraz. Konstantní řetězce nemají této výhody. Vyzkoušejte si to ve svém oblíbeném editoru: Přejmenovat proměnnou a všechna `nameof` výrazy se aktualizuje také.

`nameof` Výraz vytvoří nekvalifikované název její argument (`LastName` v předchozích příkladech) i v případě, že používáte plně kvalifikovaný název pro argument:

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

To `nameof` výraz vytváří `FirstName`, nikoli `UXComponents.ViewModel.FirstName`.

## <a name="await-in-catch-and-finally-blocks"></a>Await v Catch a nakonec blokuje.

C# 5 měl několik omezení kolem kam může být `await` výrazy.
Jeden z nich byla odebrána v C# 6. Teď můžete použít `await` v `catch` nebo `finally` výrazy. 

Přidání await výrazy v catch a nakonec bloky zdánlivě zkomplikovat ty zpracování. Přidejme příklad diskutovat o tom, jak se zobrazuje. V žádné asynchronní metody, můžete použít výraz await v a nakonec klauzule.

S C# 6 může také await ve výrazech catch. Tato možnost se nejčastěji používá s scénáře protokolování:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Podrobnosti implementace pro přidání `await` podporu uvnitř `catch` a `finally` klauzule zajistí, že její chování je konzistentní s chování synchronní kódu. Při provedení kódu `catch` nebo `finally` vyvolá klauzule, provádění hledá vhodný `catch` klauzuli v další blok okolního. Došlo k výjimce aktuální, dojde ke ztrátě této výjimky. Stejné se stane s očekávaná výrazy v `catch` a `finally` klauzule: vhodný `catch` je hledán, a aktuální výjimky, pokud existuje, bude ztracena.  

> [!NOTE]
> Toto chování je z důvodu se doporučuje pro zápis `catch` a `finally` klauzule pečlivě, aby nedošlo k zavedení nových výjimek.

## <a name="index-initializers"></a>Inicializátory indexu

*Inicializátory index* je jednou ze dvou funkcí, které byly víc konzistentní Inicializátory kolekcí. V dřívějších verzích jazyka C#, můžete použít *Inicializátory kolekcí* pouze s kolekcemi styl pořadí:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

Teď můžete také použít je s <xref:System.Collections.Generic.Dictionary%602> kolekce a podobné typy:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Tato funkce znamená, že asociativní kontejnery můžete inicializovat pomocí syntaxe podobná co bylo nastavené pro kontejnery pořadí pro několik verzí.

### <a name="extension-add-methods-in-collection-initializers"></a>Rozšíření `Add` metody v Inicializátory kolekcí

Další funkce, která usnadňuje inicializace kolekce je schopnost používat *metoda rozšíření* pro `Add` metoda. Tato funkce byla přidána parita s jazykem Visual Basic. 

Tato funkce je velmi užitečné, když máte třídy vlastní kolekce, která má metoda s jiným názvem sémanticky přidávat nové položky.

Zvažte například kolekce studenty takto:

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

`Enroll` Metoda přidá student. Ale není pomocí `Add` vzor.
V předchozích verzích jazyka C#, nelze používat Inicializátory kolekcí s `Enrollment` objektu:

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

Teď můžete, ale jenom v případě, že vytvoříte metody rozšíření, která mapuje `Add` k `Enroll`:

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

Co dělají pomocí této funkce je k mapování libovolné metody přidá položky do kolekce na metodu s názvem `Add` vytvořením metody rozšíření: 

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]
[!code-csharp[ExtensionAddSample](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAddSample)]

## <a name="improved-overload-resolution"></a>Vylepšené přetížení řešení

Tato funkce poslední je jednou z pravděpodobně nebude zjistíte. Nebyly konstrukce kde předchozí verzi kompilátor jazyka C# může našli některé volání metody zahrnující nejednoznačné výrazy lambda. Vezměte v úvahu tuto metodu:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

Voláním této metody pomocí syntaxe skupiny metoda skončí v dřívějších verzích jazyka C# s chybou:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
Starší kompilátoru nelze správně mezi rozlišit `Task.Run(Action)` a `Task.Run(Func<Task>())`. V předchozích verzích je třeba použít jako argument výraz lambda:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

Kompilátor jazyka C# 6 správně zjistí, `Task.Run(Func<Task>())` je lepší volbou.
