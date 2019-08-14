---
title: Co je nového v C# 6. C# příručce
description: Naučte se nové funkce C# ve verzi 6.
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971386"
---
# <a name="whats-new-in-c-6"></a>Co je nového v C# 6

Verze 6,0 C# obsahuje mnoho funkcí, které zlepšují produktivitu pro vývojáře. Celkový vliv těchto funkcí je, že píšete výstižnější kód, který je také čitelnější. Syntaxe obsahuje méně procedury pro mnoho běžných postupů. Je snazší, abyste viděli záměr návrhu s méně procedury. Seznamte se s těmito funkcemi dobře a budete produktivnější a zapište čitelnější kód. Můžete se soustředit na další funkce než v konstrukcích daného jazyka.

Zbývající část tohoto článku obsahuje přehled každé z těchto funkcí s odkazem na prozkoumání jednotlivých funkcí. V části kurzy můžete také prozkoumat funkce [interaktivního průzkumu na C# 6](../tutorials/exploration/csharp-6.yml) .

## <a name="read-only-auto-properties"></a>Automatické vlastnosti jen pro čtení

*Automatické vlastnosti jen pro čtení* poskytují stručnější syntaxi pro vytváření neměnných typů. Automatickou vlastnost deklarujete pouze pomocí přístupového objektu Get:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

Vlastnosti `FirstName` a`LastName` lze nastavit pouze v těle konstruktoru stejné třídy:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Pokus o nastavení `LastName` v jiné metodě `CS0200` generuje chybu kompilace:

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

Tato funkce umožňuje skutečnou podporu jazyka pro vytváření neměnných typů a používá stručnější a pohodlný syntax automatických vlastností.

Pokud přidání této syntaxe neodebere přístupnou metodu, jedná se o [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).

## <a name="auto-property-initializers"></a>Inicializátory automatickou vlastnost

*Inicializátory automatických vlastností* umožňují deklarovat počáteční hodnotu pro automatickou vlastnost v rámci deklarace vlastnosti.

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` Člen je inicializován, kde je deklarován. To usnadňuje provedení inicializace přesně jednou. Inicializace je součástí deklarace vlastnosti, což usnadňuje přidělení úložiště k veřejnému rozhraní pro `Student` objekty.

## <a name="expression-bodied-function-members"></a>Členové funkce Expression-těle

Mnoho členů, které napíšete, je jediné příkazy, které by mohly být jednotlivé výrazy. Místo toho zapište člen Expression-těle. Funguje pro metody a vlastnosti jen pro čtení. Například přepsání `ToString()` je často skvělým kandidátem:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Tuto syntaxi můžete použít také pro vlastnosti jen pro čtení:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Změna existujícího člena na člen Expression těle je [binární kompatibilní změna](version-update-considerations.md#binary-compatible-changes).

## <a name="using-static"></a>Použití static

*Použití statického* rozšíření umožňuje importovat statické metody jedné třídy. Určíte třídu, kterou používáte:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<xref:System.Math> Neobsahuje žádné metody instance. Můžete také použít `using static` k importu statických metod třídy, které mají jak statické, tak metody instance. Jedním z nejužitečnějších příkladů je <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> `System.String` V příkazu static using je nutné použít plně kvalifikovaný název třídy.  Místo toho se `string` klíčové slovo nedá použít.

Při importu z `static using` příkazu jsou metody rozšíření v oboru pouze při volání pomocí syntaxe volání metody rozšíření. Nejsou v oboru, který je volán jako statická metoda. Často se to zobrazí v dotazech LINQ. Můžete importovat vzor LINQ importem <xref:System.Linq.Enumerable>, nebo. <xref:System.Linq.Queryable>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Metody rozšíření se obvykle volají pomocí výrazů volání rozšiřujících metod. Přidání názvu třídy ve výjimečném případě, kdy je zavoláte pomocí syntaxe volání statické metody, řeší nejednoznačnost.

`static using` Direktiva také importuje všechny vnořené typy. Na všechny vnořené typy můžete odkazovat bez kvalifikace.

## <a name="null-conditional-operators"></a>Podmíněné operátory s hodnotou null

*Podmíněný operátor s hodnotou null* zpřístupňuje v hodnotě null kontroly mnohem jednodušší a kapalin. Nahraďte přístup `.` členů pomocí `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

V předchozím příkladu je proměnná `first` přiřazena `null` , pokud je `null`objekt Person. V opačném případě se mu přiřadí hodnota `FirstName` vlastnosti. Co je nejdůležitější `?.` , znamená to, že tento řádek kódu `NullReferenceException` negeneruje, pokud `person` je `null`proměnná. Místo toho se jedná o krátkodobé okruhy `null`a vrátí. Pro přístup k poli nebo indexeru můžete použít také podmíněný operátor s hodnotou null. Nahraďte `[]` výrazem vindexu.`?[]`

Následující výraz vrátí `string`, bez ohledu na `person`hodnotu. Tento konstruktor se často používá s operátorem sloučení s *hodnotou null* k přiřazení výchozích hodnot, pokud je `null`jedna z vlastností. Při krátkých okruhech výrazu je vrácená `null` hodnota zadána, aby odpovídala celému výrazu.

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Můžete také použít `?.` k podmíněnému vyvolání metod. Nejběžnějším použitím členských funkcí s podmíněným operátorem s hodnotou null je bezpečné vyvolání delegátů (nebo obslužných rutin událostí `null`), které mohou být.  `Invoke` Metodu delegáta zavoláte `?.` pomocí operátoru pro přístup ke členu. Příklad najdete v článku [vzory delegátů](../delegates-patterns.md#handling-null-delegates) .

Pravidla `?.` operátora zajišťují, že levá strana operátoru je vyhodnocena pouze jednou. Umožňuje mnoho idiomy, včetně následujícího příkladu, pomocí obslužných rutin událostí:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Zajistěte, aby byla levá strana vyhodnocována pouze jednou, a umožňuje použít libovolný výraz, včetně volání metody, na levé straně`?.`

## <a name="string-interpolation"></a>Interpolace řetězců

S C# 6, nová funkce [interpolace řetězce](../language-reference/tokens/interpolated.md) umožňuje vkládat výrazy do řetězce. Jednoduše se dotvářte do `$`řetězce a používejte výrazy `{` mezi `}` a místo pořadových čísel:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Tento příklad používá vlastnosti pro substituované výrazy. Můžete použít libovolný výraz. Jako součást interpolace můžete například vypočítat průměrnou hodnotu typu "Student 's".

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Předchozí řádek kódu formátuje hodnotu `Grades.Average()` jako číslo s plovoucí desetinnou čárkou se dvěma desetinnými místy.

Často může být nutné zformátovat řetězec vytvořený pomocí konkrétní jazykové verze. Můžete použít fakt, že objekt vytvořený pomocí interpolace řetězce lze implicitně převést na <xref:System.FormattableString?displayProperty=nameWithType>. <xref:System.FormattableString> Instance obsahuje složený řetězec formátu a výsledky vyhodnocení výrazů před jejich převodem na řetězce. <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> Použijte metodu k určení jazykové verze při formátování řetězce. Následující příklad vytvoří řetězec pomocí jazykové verze německé (de-DE-DE). (Ve výchozím nastavení německá jazyková verze používá znak "," pro oddělovač desetinných míst a znak "." jako oddělovač tisíců.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Chcete-li začít s interpolací řetězců, přečtěte si článek o [interpolaci řetězce C# v](../tutorials/exploration/interpolated-strings.yml) interaktivním kurzu, o [interpolaci řetězce](../language-reference/tokens/interpolated.md) a o [interpolaci řetězce v C# ](../tutorials/string-interpolation.md) kurzu.

## <a name="exception-filters"></a>Filtry výjimek

*Filtry výjimek* jsou klauzule, které určují, kdy se má daná klauzule catch použít. Pokud je výraz použitý pro filtr výjimek vyhodnocen `true`jako, klauzule catch provede své normální zpracování na výjimku. Pokud se výraz vyhodnotí `false`jako, `catch` pak se klauzule přeskočí. Jedním z nich je prozkoumávat informace o výjimce k určení, `catch` zda klauzule může zpracovat výjimku:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>`nameof` Výraz

Výraz [nameof](../language-reference/operators/nameof.md) se vyhodnocuje jako název symbolu. Je to skvělý způsob, jak získat nástroje, kdykoli potřebujete název proměnné, vlastnosti nebo pole členů. Jedním z nejběžnějších použití pro `nameof` je poskytnout název symbolu, který způsobil výjimku:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Jiné použití je v aplikacích založených na jazyce XAML, `INotifyPropertyChanged` které implementují rozhraní:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>Očekává se v blocích catch a finally.

C#5 bylo několik omezení, kde byste mohli umístit `await` výrazy. S C# 6 můžete teď použít `await` ve `catch` výrazech nebo `finally` . Nejčastěji se používá při protokolování scénářů:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Podrobnosti implementace pro přidání `await` podpory uvnitř `catch` klauzulí a `finally` zajišťují, že chování je konzistentní s chováním pro synchronní kód. Když kód spuštěný v `catch` klauzuli `finally` or vyvolá, vyhledá vhodnou `catch` klauzuli v dalším okolním bloku. Pokud byla zjištěna aktuální výjimka, dojde ke ztrátě této výjimky. Totéž se stane s očekávanými výrazy v `catch` klauzulích a `finally` : je `catch` prohledána vhodná a aktuální výjimka, pokud nějaká existuje.  

> [!NOTE]
> Toto chování je důvodem pro pečlivou psaní `catch` a `finally` klauzulí, aby nedocházelo k zavlečení nových výjimek.

## <a name="initialize-associative-collections-using-indexers"></a>Inicializace asociativních kolekcí pomocí indexerů

*Inicializátory indexu* jsou jednou ze dvou funkcí, které vytvářejí inicializátory kolekce více konzistentní s využitím indexu. V dřívějších verzích C#nástroje můžete použít inicializátory *kolekce* s kolekcemi stylu sekvence, včetně <xref:System.Collections.Generic.Dictionary%602>, přidáním složených závorek kolem párů klíč-hodnota:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

Můžete je použít s <xref:System.Collections.Generic.Dictionary%602> kolekcemi a jinými typy, kde přístupná `Add` Metoda akceptuje více než jeden argument. Nová syntaxe podporuje přiřazení pomocí indexu do kolekce:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Tato funkce znamená, že asociativní kontejnery lze inicializovat pomocí syntaxe podobně jako u kontejnerů sekvence pro několik verzí.

## <a name="extension-add-methods-in-collection-initializers"></a>Metody `Add` rozšíření v inicializátorech kolekcí

Další funkcí, která usnadňuje inicializaci kolekce, je možnost použít *metodu rozšíření* pro `Add` metodu. Tato funkce byla přidána pro paritu s Visual Basic. Tato funkce je nejužitečnější, když máte vlastní třídu kolekce, která má metodu s jiným názvem pro sémantické přidání nových položek.

## <a name="improved-overload-resolution"></a>Vylepšené rozlišení přetížení

Tato poslední funkce je ta, kterou si pravděpodobně nevšimnete. Byly zjištěny konstrukce, kde předchozí verze C# kompilátoru mohla najít některá volání metod zahrnující výrazy lambda nejednoznačná. Zvažte tuto metodu:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

V dřívějších verzích systému C#volání této metody pomocí syntaxe skupiny metod selže:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

Předchozí kompilátor nemůže správně rozlišovat mezi `Task.Run(Action)` a. `Task.Run(Func<Task>())` V předchozích verzích byste měli použít výraz lambda jako argument:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

C# 6 kompilátor správně určí, že `Task.Run(Func<Task>())` je lepší volbou.

### <a name="deterministic-compiler-output"></a>Deterministický výstup kompilátoru

`-deterministic` Možnost instruuje kompilátor, aby vytvořil stejné výstupní sestavení typu Byte-Byte pro následná kompilace stejných zdrojových souborů.

Ve výchozím nastavení každá kompilace vytvoří jedinečný výstup v každé kompilaci. Kompilátor přidá časové razítko a identifikátor GUID vygenerovaný z náhodných čísel. Tuto možnost použijete, pokud chcete porovnat výstup bajtů za bajt, aby se zajistila konzistence napříč sestaveními.

Další informace naleznete v článku o [Možnosti deterministického kompilátoru](../language-reference/compiler-options/deterministic-compiler-option.md) .
