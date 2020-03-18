---
title: Co je nového v C# 6 - C# Průvodce
description: Naučte se nové funkce v C# verze 6
ms.date: 12/12/2018
ms.openlocfilehash: da40b4c9d4af0094fdd907c542e971ba55086e0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399390"
---
# <a name="whats-new-in-c-6"></a>Co je nového v C# 6

Verze 6.0 c# obsahuje mnoho funkcí, které zlepšují produktivitu pro vývojáře. Celkový efekt těchto funkcí je, že píšete stručnější kód, který je také čitelnější. Syntaxe obsahuje méně obřad u mnoha běžných postupů. Je snazší vidět záměr návrhu s menším obřadem. Naučte se tyto funkce dobře a budete produktivnější a napíšete čitelnější kód. Můžete se soustředit více na své funkce než na konstrukce jazyka.

Zbývající část tohoto článku obsahuje přehled každé z těchto funkcí s odkazem na prozkoumání jednotlivých funkcí. Můžete také prozkoumat funkce v [interaktivní průzkum na C# 6](../tutorials/exploration/csharp-6.yml) v části kurzy.

## <a name="read-only-auto-properties"></a>Automatické vlastnosti jen pro čtení

*Automatické vlastnosti jen pro čtení* poskytují stručnější syntaxi pro vytváření neměnných typů. Deklarace auto-vlastnost pouze získat přistupujícího objektu:

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

`FirstName` Vlastnosti `LastName` a lze nastavit pouze v těle konstruktoru stejné třídy:

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

Při pokusu o nastavení `LastName` `CS0200` v jiné metodě se vygeneruje chyba kompilace:

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

Tato funkce umožňuje skutečnou jazykovou podporu pro vytváření neměnných typů a používá stručnější a pohodlnější syntaxi automatické vlastnosti.

Pokud přidání této syntaxe neodebere přístupnou metodu, jedná se o [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).

## <a name="auto-property-initializers"></a>Inicializátory automatických vlastností

*Inicializátory automatických vlastností* umožňují deklarovat počáteční hodnotu pro automatickou vlastnost jako součást deklarace vlastnosti.

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

Člen `Grades` je inicializován tam, kde je deklarován. To usnadňuje provedení inicializace přesně jednou. Inicializace je součástí deklarace vlastnosti, což usnadňuje srovnávač přidělení úložiště s veřejným rozhraním pro `Student` objekty.

## <a name="expression-bodied-function-members"></a>Členy funkce s výrazným tělem

Mnoho členů, které píšete, jsou jednotlivé příkazy, které mohou být jednotlivé výrazy. Místo toho napište člen s výrazem. Funguje pro metody a vlastnosti jen pro čtení. Například přepsání `ToString()` je často velkým kandidátem:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Tuto syntaxi můžete také použít pro vlastnosti jen pro čtení:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Změna existujícího člena na člen s tělesnou dolinou výrazu je [binární kompatibilní změna](version-update-considerations.md#binary-compatible-changes).

## <a name="using-static"></a>použití statické

*Použití statické* vylepšení umožňuje importovat statické metody jedné třídy. Zadejte třídu, kterou používáte:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

Neobsahuje <xref:System.Math> žádné metody instance. Můžete také `using static` použít k importu statické metody třídy pro třídu, která má statické metody i metody instance. Jedním z nejužitečnějších <xref:System.String>příkladů je :

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Je nutné použít plně kvalifikovaný `System.String` název třídy, ve statické using příkazu.  Místo toho `string` nelze použít klíčové slovo.

Při importu `static using` z příkazu jsou metody rozšíření pouze v oboru, pokud jsou volány pomocí syntaxe vyvolání metody rozšíření. Nejsou v oboru při volání jako statická metoda. Často se zobrazí v dotazech LINQ. Vzorek LINQ můžete importovat <xref:System.Linq.Enumerable>importováním <xref:System.Linq.Queryable>nebo .

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Obvykle volání metody rozšíření pomocí výrazy vyvolání metody rozšíření. Přidání názvu třídy ve výjimečných případech, kdy je voláte pomocí syntaxe volání statické metody, řeší nejednoznačnost.

Směrnice `static using` také importuje všechny vnořené typy. Můžete odkazovat na všechny vnořené typy bez kvalifikace.

## <a name="null-conditional-operators"></a>Operátory s nulovým podmíněným podmínkou

Operátor *podmíněné null* umožňuje null kontroly mnohem jednodušší a plynulé. Nahraďte `.` přístup `?.`člena :

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

V předchozím příkladu je `first` proměnná `null` přiřazena, `null`pokud je objekt osoby . V opačném případě je přiřazena hodnota vlastnosti. `FirstName` A co je `?.` nejdůležitější, znamená, že tento `NullReferenceException` řádek `person` kódu `null`negeneruje, pokud je proměnná . Místo toho zkratuje a `null`vrací . Můžete také použít operátor podmíněné null pro přístup k poli nebo indexeru. Nahradit `[]` `?[]` ve výrazu indexu.

Následující výraz vrátí `string`hodnotu a , `person`bez ohledu na hodnotu . Často používáte tento konstrukt s *nulovou slučovací* operátor přiřadit `null`výchozí hodnoty, pokud je jedna z vlastností . Když se výraz zkratuje, `null` vrácená hodnota je zadántak, aby odpovídala úplnému výrazu.

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Můžete také `?.` použít k podmíněnému vyvolání metod. Nejběžnější použití členských funkcí s operátorem podmíněné null je bezpečně vyvolat delegáty `null`(nebo obslužné rutiny událostí), které mohou být .  Budete volat metodu delegáta `Invoke` pomocí `?.` operátoru pro přístup k členu. Příklad můžete vidět v článku [vzory delegáta.](../delegates-patterns.md#handling-null-delegates)

Pravidla `?.` provozovatele zajišťují, že levá strana obsluhy je vyhodnocena pouze jednou. Umožňuje mnoho idiomy, včetně následujícího příkladu pomocí obslužné rutiny událostí:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Zajištění, že levá strana je vyhodnocena pouze jednou, umožňuje použít libovolný výraz, včetně volání metod, na levé straně`?.`

## <a name="string-interpolation"></a>Interpolace řetězců

S C# 6 nový řetězec [interpolace](../language-reference/tokens/interpolated.md) funkce umožňuje vložit výrazy v řetězci. Jednoduše předmluva `$`řetězec s a `{` `}` používat výrazy mezi a místo řadových čísel:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Tento příklad používá vlastnosti pro nahrazené výrazy. Můžete použít libovolný výraz. Můžete například vypočítat bodový průměr hodnocení studenta jako součást interpolace:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Předchozí řádek kódu formátuje hodnotu `Grades.Average()` jako číslo s plovoucí desetinnou čárkou se dvěma desetinnými místy.

Často může být nutné formátovat řetězec vytvořený pomocí určité jazykové verze. Použijete skutečnost, že objekt vytvořený interpolací řetězce lze <xref:System.FormattableString?displayProperty=nameWithType>implicitně převést na . Instance <xref:System.FormattableString> obsahuje složený formátovací řetězec a výsledky vyhodnocení výrazů před jejich převodem na řetězce. Pomocí <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metody určete jazykovou verzi při formátování řetězce. Následující příklad vytvoří řetězec pomocí německé (de-DE) jazykové verze. (Ve výchozím nastavení používá německá jazyková verze znak ',' pro oddělovač desetinných míst a znak '.' jako oddělovač tisíců.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Chcete-li začít s interpolací řetězců, naleznete v interaktivním kurzu [String interpolace v c#](../tutorials/exploration/interpolated-strings.yml) [, článek interpolace řetězce](../language-reference/tokens/interpolated.md) a [interpolace řetězce v kurzu Jazyka C#.](../tutorials/string-interpolation.md)

## <a name="exception-filters"></a>Filtry výjimek

*Filtry výjimek* jsou klauzule, které určují, kdy by měla být použita daná klauzule catch. Pokud výraz použitý pro filtr výjimek vyhodnotí `true`, klauzule catch provede normální zpracování na výjimku. Pokud výraz vyhodnotí `false`do `catch` , pak je klauzule přeskočena. Jedním z použití je prozkoumat informace `catch` o výjimce k určení, zda klauzule může zpracovat výjimku:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>Výraz `nameof`

Název [výrazu](../language-reference/operators/nameof.md) vyhodnotí název symbolu. Je to skvělý způsob, jak získat nástroje pracovní kdykoli budete potřebovat název proměnné, vlastnost nebo členské pole. Jedním z nejběžnějších `nameof` použití pro je poskytnout název symbolu, který způsobil výjimku:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Další použití je s aplikacemi založenými `INotifyPropertyChanged` na XAML, které implementují rozhraní:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>Čekají v Catch a Finally bloky

C# 5 měl několik omezení kolem `await` místa, kde můžete umístit výrazy. S C# 6, nyní `await` `catch` můžete `finally` použít v nebo výrazy. To se nejčastěji používá se scénáři protokolování:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Podrobnosti implementace `await` pro `catch` přidání `finally` podpory uvnitř a klauzule zajistit, že chování je konzistentní s chováním pro synchronní kód. Při spuštění kódu `catch` v `finally` nebo klauzule vyvolá, `catch` spuštění hledá vhodnou klauzuli v dalším okolním bloku. Pokud byla aktuální výjimka, tato výjimka je ztracena. Totéž se děje s `catch` očekávanými výrazy a `finally` klauzulemi: je vyhledána vhodná `catch` a aktuální výjimka, pokud existuje, je ztracena.  

> [!NOTE]
> Toto chování je důvod, proč `catch` `finally` se doporučuje psát a klauzule pečlivě, aby se zabránilo zavedení nové výjimky.

## <a name="initialize-associative-collections-using-indexers"></a>Inicializovat asociativní kolekce pomocí indexerů

*Index Initializers* je jedním ze dvou funkcí, které kolekce inicializátory více konzistentní s využití indexu. V dřívějších verzích jazyka C# můžete použít *inicializátory kolekce* s kolekcemi stylů sekvence, včetně <xref:System.Collections.Generic.Dictionary%602>, přidáním závorek kolem párů klíčů a hodnot:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

Můžete je použít <xref:System.Collections.Generic.Dictionary%602> s kolekcemi a `Add` jinými typy, kde přístupná metoda přijímá více než jeden argument. Nová syntaxe podporuje přiřazení pomocí indexu do kolekce:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Tato funkce znamená, že asociativní kontejnery lze inicializovat pomocí syntaxe podobné tomu, co bylo na místě pro kontejnery sekvence pro několik verzí.

## <a name="extension-add-methods-in-collection-initializers"></a>Metody `Add` rozšíření v inicializátorech kolekce

Další funkce, která usnadňuje inicializaci kolekce je `Add` možnost použít *metodu rozšíření* pro metodu. Tato funkce byla přidána pro paritu s visual basicem. Funkce je nejužitečnější, pokud máte vlastní třídu kolekce, která má metodu s jiným názvem sémanticky přidat nové položky.

## <a name="improved-overload-resolution"></a>Vylepšené rozlišení přetížení

Tato poslední funkce je ta, kterou si pravděpodobně nevšimnete. Tam byly konstrukce, kde předchozí verze kompilátoru Jazyka C# může mít nalezeny některé volání metod zahrnující lambda výrazy nejednoznačné. Zvažte tuto metodu:

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

V dřívějších verzích jazyka C# by volání této metody pomocí syntaxe skupiny metody selhalo:

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]

Dřívější kompilátor nemohl správně `Task.Run(Action)` rozlišit mezi a `Task.Run(Func<Task>())`. V předchozích verzích byste museli použít výraz lambda jako argument:

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

Kompilátor Jazyka C# 6 `Task.Run(Func<Task>())` správně určuje, že je lepší volbou.

### <a name="deterministic-compiler-output"></a>Deterministický výstup kompilátoru

Tato `-deterministic` možnost instruuje kompilátor k vytvoření identického výstupního sestavení bajtu za bajt pro následné kompilace stejných zdrojových souborů.

Ve výchozím nastavení každá kompilace vytváří jedinečný výstup na každé kompilaci. Kompilátor přidá časové razítko a identifikátor GUID generovaný z náhodných čísel. Tuto možnost použijte, pokud chcete porovnat výstup bajt za bajt, abyste zajistili konzistenci mezi sestaveními.

Další informace naleznete v článku [možnosti determinismu -deterministický kompilátor.](../language-reference/compiler-options/deterministic-compiler-option.md)
