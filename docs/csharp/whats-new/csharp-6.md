---
title: Co je nového v jazyce C# 6 – Průvodce v C#
description: Informace o nových funkcích v jazyce C# verze 6
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: f6f953eacc935d38cc7d45173109c96c52a5e2f3
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208182"
---
# <a name="whats-new-in-c-6"></a>Co je nového v jazyce C# 6

C# 6.0 vydání obsahovala řadu funkcí, které zvyšují produktivitu pro vývojáře. Funkce v této verzi patří:

* [Auto vlastnosti jen pro čtení](#read-only-auto-properties):
    - Můžete vytvořit jen pro čtení automatické vlastnosti, které lze nastavit pouze v konstruktorech.
* [Inicializátory automatickou vlastnost](#auto-property-initializers):
    - Můžete psát výrazy inicializace nastavit počáteční hodnotu Automatická vlastnost.
* [Členové s výrazem v těle funkce](#expression-bodied-function-members):
    - Můžete vytvářet metody jednořádkové použití výrazů lambda.
* [pomocí statické](#using-static):
    - Všechny metody jednu třídu můžete importovat do aktuálního oboru názvů.
* [Null – podmíněných operátorů](#null-conditional-operators):
    - Stručně a výstižně a bezpečně dostanete členy objektu při pořád ještě se hledají null s hodnotou null podmiňovací operátor.
* [Interpolace řetězců](#string-interpolation):
    - Můžete napsat řetězce formátování výrazů vložené výrazy místo poziční argumenty.
* [Filtry výjimek](#exception-filters):
    - Je možné zachytit výrazům založeným na vlastnosti výjimky nebo jiných stav programu. 
* [Výrazy nameof](#nameof-expressions):
    - Můžete nechat kompilátor generovat řetězcové reprezentace symboly.
* [operátor await v catch a finally blokuje](#await-in-catch-and-finally-blocks):
    - Můžete použít `await` výrazy v umístění, která dříve je zakázané.
* [Inicializátory indexů](#index-initializers):
    - Výrazy inicializace pro asociativní kontejnery, stejně jako kontejnery sekvence, můžete vytvářet.
* [Rozšiřující metody pro inicializátory kolekce](#extension-add-methods-in-collection-initializers):
    - Inicializátory kolekce můžete spolehnout na dostupné rozšiřující metody, kromě metod člena.
* [Vylepšené řešení přetížení](#improved-overload-resolution):
    - Některé konstrukce, které dříve vygenerovaný volání metody nejednoznačný nyní správně přeložit.
* [`deterministic` – možnost kompilátoru](#deterministic-compiler-output):
    - Možnost kompilátoru deterministické zajišťuje, následné kompilace se stejným zdrojem generovat stejný binární výstup.

Celkový efekt z těchto funkcí je, že napíšete stručnější kód, který je také lépe čitelný. Syntaxe obsahuje méně procedury pro mnoho běžných postupech. Je snazší zjistit záměr návrhu s méně procedury. Přečtěte si tyto funkce dobře a budete produktivnější, psát kód lépe čitelný a více se soustředit na základní funkce, než na konstrukce jazyka.

Zbývající část tohoto tématu poskytuje podrobné informace o každé z těchto funkcí.

## <a name="auto-property-enhancements"></a>Vylepšení automatickou vlastnost

Syntaxe pro automaticky implementované vlastnosti (obvykle označované jako automatické vlastnosti) provedené velmii snadné vytváření vlastnosti, které bylo jednoduché get a set přístupové objekty:

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

Tato jednoduchá syntaxe však omezenou druhy vzorů, které může podporovat použití automatických vlastností. C# 6 vylepšuje možnosti automatické vlastnosti tak, aby je mohli používat ve více scénářích. Nebudete se muset vrátit zpět na podrobnější syntaxi deklarace a manipulace s pomocným polem ručně tak často.

Nová syntaxe adresy scénáře pro vlastnosti jen pro čtení a pro inicializaci proměnné úložiště za automatickou vlastnost.

### <a name="read-only-auto-properties"></a>Auto vlastnosti jen pro čtení

*Auto vlastnosti jen pro čtení* poskytují stručnější syntaxi, vytvořte neměnný typy. Nejbližší, které můžete narazit na neměnné typy ve starších verzích jazyka C# došlo k deklaraci privátní metody setter:

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
Pomocí této syntaxe, kompilátor nebude zajistěte, aby byl typ skutečně neměnné. Pouze rozdělení promítá `FirstName` a `LastName` vlastnosti nezmění v žádném kódu mimo třídu.

True jen pro čtení chování povolit automatické – vlastnosti jen pro čtení. Deklarovat vlastnost automaticky s pouze přístupový objekt get:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

`FirstName` a `LastName` vlastnosti lze nastavit pouze v těle konstruktoru:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Pokoušíte se nastavit `LastName` v jiné metody generuje `CS0200` Chyba kompilace:

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

Tato funkce umožňuje true jazykovou podporu pro vytváření typů neměnných a pomocí syntaxe automatickou vlastnost stručnějším a pohodlné.

Pokud přidáte tuto syntaxi není neodebere dostupná metoda, je [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).

### <a name="auto-property-initializers"></a>Inicializátory automatickou vlastnost

*Inicializátory automatickou vlastnost* umožňuje deklarovat počáteční hodnotu pro automatickou vlastnost jako součást deklarace vlastností.  V dřívějších verzích byste potřebovali mít nastavení těchto vlastností a je třeba použít tuto metodu setter se inicializovat datové úložiště používané pomocným polem. Vezměte v úvahu tuto třídu pro student, který obsahuje název a seznam tříd studenta:

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
S růstem této třídy může obsahovat další konstruktory. Každý konstruktor musí inicializovat toto pole, nebo budete způsobit chyby.

C# 6 umožňuje přiřadit počáteční hodnotu pro úložiště využitá službou Automatické vlastnosti v deklaraci automatickou vlastnost:

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` Člen je inicializovaný, ve kterém je deklarována. Který usnadňuje provedení inicializace přesně jednou. Inicializace je součástí deklaraci vlastnosti, což usnadňuje odpovídá přidělení úložiště pomocí veřejného rozhraní pro `Student` objekty.

Vlastnosti lze použít s vlastností čtení/zápisu, jakož i vlastnosti jen pro čtení, jak je znázorněno zde.

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a>Členové tvoření výrazy – funkce

Tělo mnoho členů, které jsme napsali obsahovat pouze jeden příkaz, který může být reprezentována jako výraz. Syntaxe můžete snížit napsáním na člena s výrazem v těle. Funguje to pro metody a vlastnosti jen pro čtení. Například přepsání `ToString()` často je vynikající kandidát:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Můžete také použít s výrazem v těle členy v také vlastnosti jen pro čtení:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Změna existujícího člena pro člena vozidlo výrazu je [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).


## <a name="using-static"></a>Pomocí statické

*Pomocí statické* vylepšení umožňuje importovat statické metody jednu třídu. Dříve `using` příkaz naimportovány všechny typy v oboru názvů. 

Často používáme statické metody třídy v rámci našeho kódu. Opakovaně zadávat název třídy může ztížit odhalení zjevného význam kódu. Běžným příkladem jsou při psaní třídy, které provádějí mnoho číselné výpočty.
Váš kód podestlána <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> a jiných volání do různých metod v <xref:System.Math> třídy. Nové `using static` syntaxe můžete provádět tyto třídy mnohem čisticího modulu pro čtení. Můžete zadat třídu, kterou používáte:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

A teď můžete použít jakékoli statické metodě v <xref:System.Math> třídy bez kvalifikace <xref:System.Math> třídy. <xref:System.Math> Třída je případ vynikající možnosti využití pro tuto funkci, protože neobsahuje žádné metody instance. Můžete také použít `using static` importovat třídy statické metody pro třídu, která má statické a metody instance. Jedním z nejužitečnějších příkladů je <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Musíte použít plně kvalifikovaný název třídy, `System.String` v statický příkaz using. Nelze použít `string` – klíčové slovo místo. 

Nyní můžete volat statické metody definované v <xref:System.String> třídy bez kvalifikace tyto metody jako členy této třídy:

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

`static using` Metody funkce a rozšíření interagovali zajímavé a návrhu jazyka zahrnuté některá pravidla, které konkrétně řeší tyto interakce. Cílem je minimalizovat jakékoli riziko rozbíjející změny v existujícím základů kódu, včetně těch vašich.

Rozšiřující metody jsou pouze v oboru při volány pomocí syntaxe volání metody rozšíření, ne v případě, že volá jako statická metoda.
To se často zobrazí v dotazech LINQ. Vzor LINQ můžete importovat importováním <xref:System.Linq.Enumerable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Tento postup importuje všechny metody v <xref:System.Linq.Enumerable> třídy.
Rozšiřující metody jsou však jenom v oboru při volání jako metody rozšíření. Nejsou v oboru Pokud jsou volány pomocí syntaxe statickou metodu:

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

Toto rozhodnutí je vzhledem k tomu, že metody rozšíření jsou obvykle volány pomocí výrazy typu invocation – metoda rozšíření. Ve výjimečných případech, ve kterém jsou volány pomocí statické metody volání se vyřešit nejednoznačnost syntaxe.
Vyžadování názvu třídy jako součást volání zdá se, že z pohledu.

Existuje jeden poslední funkci `static using`. `static using` Direktiva také importuje všechny vnořené typy. Která umožňuje odkazovat na jakékoli vnořené typy bez kvalifikace.

## <a name="null-conditional-operators"></a>Podmíněné operátory s Null

Hodnoty Null zkomplikovat kódu. Je potřeba zkontrolovat každý přístup proměnné k zajištění nejsou přesměrování `null`. *Null podmiňovací operátor* díky kontrol mnohem jednodušší a plynulé.

Jednoduše nahradit přístup ke členu `.` s `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

V předchozím příkladu je proměnná `first` je přiřazena `null` Pokud objekt osoba `null`. V opačném případě získá přiřadí hodnota `FirstName` vlastnost. Co je nejdůležitější `?.` znamená, že negeneruje tento řádek kódu `NullReferenceException` při `person` proměnná je `null`. Místo toho zkratům a vytváří `null`.

Všimněte si také, že tento výraz vrátí `string`bez ohledu hodnotu `person`.
V případě krátký circuiting `null` vrácená hodnota je typu tak, aby odpovídaly úplného výrazu.

Můžete často použít tento konstruktor s *nulové sloučení* operátor přiřadit výchozí hodnoty, pokud jedna z vlastností jsou `null`:

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Pravý operand na straně aplikace `?.` operátor není omezena pouze na vlastnosti nebo pole.
Také vám pomůže ho podmíněně vyvolávat metody. Nejběžnější použití nástroje členské funkce s hodnotou null podmíněný operátor je pro bezpečné vyvolání delegátů (nebo obslužné rutiny událostí), které mohou být `null`.  Uděláte to pomocí volání delegáta `Invoke` pomocí metody `?.` operátor pro přístup k členu. Příklad v můžete vidět  
[delegování vzorce](../delegates-patterns.md#handling-null-delegates) tématu.

Pravidla `?.` operátor Ujistěte se, že levá strana operátoru je vyhodnocen pouze jednou. To je důležité a umožňuje mnoho idiomy, včetně příkladu pomocí obslužných rutin událostí. Začněme s využitím obslužné rutiny události. V předchozích verzích jazyka C# byla ukončena. doporučujeme psát kód následujícím způsobem:

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

To byla upřednostňované nad jednodušší syntaxí:

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> V předchozím příkladu představuje časování. `SomethingHappened` Událost může mít předplatitele, pokud je zaškrtnuto proti `null`, a tyto předplatitele byl odebrán předtím, než se vyvolá událost. Která by způsobila <xref:System.NullReferenceException> vyvolání.

V této verzi druhý `SomethingHappened` obslužná rutina události může být jiná než null při testování, ale pokud jiný kód odebere obslužnou rutinu, je stále možné null při byla volána obslužná rutina události.

Kompilátor generuje kód `?.` operátor, který zajistí na levé straně (`this.SomethingHappened`) z `?.` výraz se vyhodnotí jednou a výsledek je uložen do mezipaměti:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Zajištění, že na levé straně je vyhodnocen pouze jednou můžete také použít libovolný výraz, včetně volání metod na levé straně `?.` i v případě, že mají vedlejší účinky, jsou vyhodnocovány jednou, takže k vedlejším účinkům dochází pouze jednou. Můžete zobrazit příklad, v našem obsahu na [události](../events-overview.md#language-support-for-events).

## <a name="string-interpolation"></a>Interpolace řetězců

C# 6 obsahuje novou syntaxi pro vytvoření řetězce z formátovacího řetězce a výrazy, které jsou vyhodnocovány vytvoří další hodnoty řetězce.

Tradičně, museli jste pro použít poziční parametry v metodě, jako je `string.Format`:

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

Pomocí jazyka C# 6 nové [interpolace](../language-reference/tokens/interpolated.md) funkce vám umožní vložit výrazy ve formátovacím řetězci. Jednoduše začínat řetězec s `$`:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Tento první příklad používá vlastnost výrazy pro nahrazeny výrazy. Můžete rozšířit na tahle syntaxe použít libovolný výraz. Například může vypočítat průměr student získal na podnikové úrovni jako součást interpolace:

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

Spuštěný v předchozím příkladu, jehož ekvivalent byste našli, který ve výstupu `Grades.Average()` může mít více desetinných míst, než byste chtěli. Syntaxe interpolace řetězce podporuje všechny na formát řetězce k dispozici pomocí dříve formátování metod. Přidání formátovacích řetězců uvnitř složených závorek. Přidat `:` následující výraz, který má formát:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Naformátuje hodnotu pro předchozí řádek kódu `Grades.Average()` jako číslo s plovoucí desetinnou čárkou se dvěma desetinnými místy.

`:` Je vždy interpretováno jako oddělovač mezi výrazem formátovaného a formátovací řetězec. To může způsobit problémy při výraz používá `:` jiným způsobem, jako je například podmíněný operátor:

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

V předchozím příkladu `:` je analyzován jako začátek formátovací řetězec, podmiňovací operátor není součástí. Ve všech případech, kdy k tomu dojde je možné ohraničit výrazu v závorkách k vynucení Kompilátor interpretuje výraz jako určené pro instalaci:

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

Nejsou k dispozici žádné omezení na výrazy, které můžete umístit mezi závorkami. Můžete spustit složitého dotazu LINQ v interpolovaném řetězci provádět výpočty a zobrazí výsledek:

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

Zobrazí se od této ukázky můžete dokonce vnořit řetězcového výrazu interpolace uvnitř jiného výrazu interpolace řetězce. V tomto příkladu je velmi pravděpodobné, byste měli složitější než na kolik máte v produkčním kódu.
Místo toho je příkladem škálu funkci. Libovolný výraz C# je možné použít ve složených závorkách interpolovaného řetězce.

### <a name="string-interpolation-and-specific-cultures"></a>Interpolace řetězců a specifické jazykové verze

Všechny příkladů uvedených v předchozí části formátovací řetězce, pomocí aktuální jazykové verze a jazyk na počítači kde spustí kód. Často je potřeba formátovací řetězec vytvořený pomocí konkrétní jazykové verze.
Provedete to, které používají skutečnost, že objekt vytvořený testovaným interpolace řetězců lze implicitně převést na <xref:System.FormattableString>.

<xref:System.FormattableString> Instance obsahuje řetězec formátu a výsledky vyhodnocování výrazů před převedením na řetězce. Můžete použít veřejné metody <xref:System.FormattableString> zadat jazykovou verzi, při formátování řetězce. Například následující příklad vytvoří řetězec za použití Německá jazyková verze. (Jako oddělovač desetinných míst používá znak "," a "." znak jako tisíců oddělovač.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Další informace najdete v tématu [interpolace](../language-reference/tokens/interpolated.md) tématu.

## <a name="exception-filters"></a>Filtry výjimek

Další novou funkcí v jazyce C# 6 je *filtry výjimek*. Filtry výjimek jsou klauzule, které určují, kdy by použít klauzuli catch. daný.
Pokud výraz použitý pro filtr výjimek vyhodnocuje na `true`, klauzule catch provádí běžného zpracování při výskytu výjimky. Pokud je výraz vyhodnocen `false`, pak bude `catch` klauzule se přeskočí.

Zjistit informace o výjimce k určení, zda je jedno použití `catch` klauzule může zpracovat výjimku:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

Kód vygenerovaný filtry výjimek poskytuje lepší informace o výjimce, která je vyvolána a nebyl zpracován. Před filtry výjimek byly přidány do jazyka, je třeba vytvořit kód podobný tomuto:

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

Místo, kde je vyvolána výjimka změny mezi tyto dva příklady.
V předchozím kódu, kde `throw` klauzule, všechny analýzu trasování zásobníku nebo zkoumání výpisy při selhání se zobrazí, že byla vyvolána výjimka z `throw` klauzulí catch příkazu. Objekt výjimky skutečné obsahovala původní zásobník volání, ale všechny ostatní informace o proměnných v zásobníku volání od tohoto okamžiku throw umístění původního bodu throw bylo ztraceno. 

Rozdíl oproti, jak se zpracovávají kódu pomocí filtru výjimky: výraz filtru výjimky je vyhodnocen jako `false`. Proto nikdy zadá provádění `catch` klauzuli. Vzhledem k tomu, `catch` klauzule nespustí, žádné odvíjení zásobníku probíhá. Pro ladění činnosti, které by proběhnout později se zachovají, throw znamená, že původní umístění.

Kdykoli budete potřebovat k vyhodnocení, pole nebo vlastnosti výjimky, namísto spoléhání se výhradně na typ výjimky, použijte filtr výjimek pro zachování Další informace o ladění.

Další doporučené vzor s filtry výjimek je k jejich použití pro rutiny protokolování. Toto použití také využívá způsobem, ve kterém je zachová bodu vyvolání výjimky, i když filtr výjimek vyhodnocuje na `false`.

Metoda protokolování bude metodou, jehož argumentem je výjimka, která bezpodmínečně vrací hodnotu `false`:

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

Pokaždé, když se chcete přihlásit k výjimce, můžete přidat klauzuli catch a tuto metodu použít jako filtr výjimek:

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

Výjimky jsou nikdy zachycena, protože `LogException` metoda vždy vrátí `false`. Tento filtr výjimek vždy false znamená, že tato obslužná rutina protokolování před všechny ostatní obslužné rutiny výjimek můžete umístit:

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

V předchozím příkladu jsou zvýrazněné velmi důležitý aspekt filtry výjimek.
Filtry výjimek umožňují scénáře, ve kterém může obecnější klauzuli catch. výjimky vyskytovat před konkrétnější jeden. Je také možné mít stejný typ výjimky, se zobrazí ve více klauzulí catch:

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

Další doporučené vzor zabraňuje klauzule catch zpracování výjimek, když je připojen ladicí program. Tato technika umožňuje spouštět aplikace s ladicím programem a zastavit provádění, když dojde k výjimce.

Ve vašem kódu přidejte filtr výjimek, aby kód pro obnovení provádí pouze v případě, že není připojený ladicí program:

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

Po přidání tohoto v kódu, nastavujete ladicí program na přerušení na všechny neošetřené výjimky. Spuštění programu v ladicím programu a ladicí program přeruší vždy, když `PerformFailingOperation()` vyvolá `RecoverableException`.
Ladicí program přeruší programu, protože klauzule catch nebude provedeno z důvodu výjimky filtr vrátí hodnotu false.

## <a name="nameof-expressions"></a>`nameof` Výrazy

`nameof` Výraz vyhodnocen jako název symbolu. To je skvělý způsob, jak získat nástroje pracovat pokaždé, když budete potřebovat název proměnné, vlastnost nebo pole členů.

Jeden z nejčastěji používaných používá pro `nameof` je k poskytnutí názvu symbolu, která způsobila výjimku:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Další možností použití je s XAML na základě aplikace, které implementují `INotifyPropertyChanged` rozhraní:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

Výhodou použití `nameof` operátor přes konstantní řetězce je, že nástroje by rozuměla symbolu. Pokud používáte nástroje pro refaktoring Přejmenování symbolu, ji budou přejmenujte ji v `nameof` výrazu. Konstantní řetězce nemají tuto výhodu. Vyzkoušejte si to sami ve svém oblíbeném editoru: přejmenování proměnnou a všechny `nameof` výrazy budou aktualizovat také.

`nameof` Výraz vytvoří neúplný název svého argumentu (`LastName` v předchozích příkladech) i v případě, že používáte plně kvalifikovaný název argumentu:

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

To `nameof` výraz vytvoří `FirstName`, nikoli `UXComponents.ViewModel.FirstName`.

## <a name="await-in-catch-and-finally-blocks"></a>Operátor await v Catch a blocích Finally

C# 5 má několik omezení kde mohli byste umístit `await` výrazy.
Jedna z těchto byla odebrána v jazyce C# 6. Teď můžete použít `await` v `catch` nebo `finally` výrazy. 

Přidání await výrazy v catch a finally může zdát zkomplikovat ty zpracování bloky. Přidejme popisují, jak se zobrazuje příklad. V asynchronní metody, výrazu await v můžete klauzule finally.

Pomocí jazyka C# 6 může také čekat ve výrazech catch. To se nejčastěji používá v případě protokolování:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Podrobnosti implementace pro přidání `await` podporovala uvnitř `catch` a `finally` klauzule zajistí, že její chování je konzistentní s chování pro synchronní kód. Při spouštění kódu v `catch` nebo `finally` klauzule vyvolá výjimku, provádění hledá vhodný `catch` klauzule v další okolní bloku. Pokud se aktuální výjimku, tato výjimka bude ztracena. Stejné se stane s očekávané výrazy v `catch` a `finally` klauzulí: vhodný `catch` prohledána, a na aktuální výjimku, pokud existuje, dojde ke ztrátě.  

> [!NOTE]
> Toto chování je z důvodu se doporučuje pro zápis `catch` a `finally` klauzule pečlivě, aby nedošlo k zavedení nové výjimky.

## <a name="index-initializers"></a>Inicializátory indexů

*Inicializátory indexů* je jedním ze dvou funkcí, které usnadňují inicializátory kolekce konzistentnější s využitím indexu. V dřívějších verzích jazyka C#, můžete použít *inicializátory kolekce* pouze s kolekcemi styl sekvence, včetně <xref:System.Collections.Generic.Dictionary%602> přidáním závorek kolem páry klíč-hodnota:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

Teď je můžete využít s <xref:System.Collections.Generic.Dictionary%602> kolekce a podobné typy. Nová syntaxe podporuje přiřazení do kolekce pomocí indexu:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Tato funkce znamená, že asociativní kontejnery mohou být inicializovány pomocí syntaxe podobné co bylo nastavené pro kontejnery sekvence pro několik verzí.

## <a name="extension-add-methods-in-collection-initializers"></a>Rozšíření `Add` metody v inicializátory kolekce

Další funkce, která usnadňuje inicializace kolekce je schopnost používat *– metoda rozšíření* pro `Add` metody. Tato funkce byla přidána parita s jazykem Visual Basic. 

Tato funkce je nejužitečnější v případě, že máte vlastní třídu kolekce, která obsahuje metodu s jiným názvem sémanticky přidávat nové položky.

Představte si třeba kolekce studentů takto:

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

`Enroll` Metoda přidá student. Ale jeho není postupujte `Add` vzor.
V předchozích verzích jazyka C#, nelze používat inicializátory kolekce s `Enrollment` objektu:

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

Nyní můžete, ale pouze v případě, že vytvoření metody rozšíření, která mapuje `Add` k `Enroll`:

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

Co právě děláte pomocí této funkce je k mapování libovolné metody přidá položky do kolekce na metodu s názvem `Add` tak, že vytvoříte metody rozšíření.

## <a name="improved-overload-resolution"></a>Vylepšené přetížení

Tato funkce poslední je ten, který pravděpodobně nebude oznámení. Došlo k konstrukce předchozí verze kompilátoru jazyka C# může kde najdete některé volání metody zahrnující nejednoznačné výrazy lambda. Vezměte v úvahu tuto metodu:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

Voláním této metody pomocí syntaxe metody skupiny selže v dřívějších verzích jazyka C#:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
Kompilátor starší nelze rozlišit správně mezi `Task.Run(Action)` a `Task.Run(Func<Task>())`. V předchozích verzích je třeba použít výraz lambda jako argument:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

Určuje, který kompilátor jazyka C# 6 správně `Task.Run(Func<Task>())` je lepší volbou.

### <a name="deterministic-compiler-output"></a>Výstup kompilátoru deterministické

`-deterministic` Možnost instruuje kompilátor, aby vytvořit bajt po bajtu identické výstupního sestavení po sobě následujících souborů stejných zdrojových souborů.

Ve výchozím nastavení vytvoří každé kompilaci jedinečný výstup na každý kompilace. Kompilátor přidá časové razítko a identifikátor GUID vygenerovaný z náhodných čísel. Tuto možnost použijte, pokud chcete k porovnání pro bajtech výstupu k zajištění konzistence se v rámci sestavení.

Další informace najdete v tématu [– možnost kompilátoru deterministické](../language-reference/compiler-options/deterministic-compiler-option.md) článku.
