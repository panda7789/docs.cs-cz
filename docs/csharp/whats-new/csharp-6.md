---
title: Co je nového v jazyce C# 6 – Průvodce v C#
description: Informace o nových funkcích v jazyce C# verze 6
ms.date: 12/12/2018
ms.openlocfilehash: 478fd512f6b6facfce6d7f70f9691ce15e418d6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706179"
---
# <a name="whats-new-in-c-6"></a>Co je nového v jazyce C# 6

C# 6.0 vydání obsahovala řadu funkcí, které zvyšují produktivitu pro vývojáře. Celkový efekt z těchto funkcí je, že napíšete stručnější kód, který je také lépe čitelný. Syntaxe obsahuje méně procedury pro mnoho běžných postupech. Je snazší zjistit záměr návrhu s méně procedury. Přečtěte si tyto funkce dobře, a budete produktivnější a napsat kód lépe čitelný. Více můžete soustředit na funkce než na konstrukce jazyka.

Zbývající část tohoto článku poskytuje přehled o každé z těchto funkcí s odkazem k prozkoumání jednotlivých funkcí. Můžete si taky prostudovat funkce [interaktivní zkoumání na C# 6](../tutorials/exploration/csharp-6.yml) v části kurzy.

## <a name="read-only-auto-properties"></a>Auto vlastnosti jen pro čtení

*Auto vlastnosti jen pro čtení* poskytují stručnější syntaxi, vytvořte neměnný typy. Deklarovat vlastnost automaticky s pouze přístupový objekt get:

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

Tato funkce umožňuje podporu opravdový jazyk pro vytváření typů neměnných a používá syntaxi automatickou vlastnost stručnějším a pohodlné.

Pokud přidáte tuto syntaxi neodebere dostupná metoda, je [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).

## <a name="auto-property-initializers"></a>Inicializátory automatickou vlastnost

*Inicializátory automatickou vlastnost* umožňuje deklarovat počáteční hodnotu pro automatickou vlastnost jako součást deklarace vlastností.

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` Člen je inicializovaný, ve kterém je deklarována. Který usnadňuje provedení inicializace přesně jednou. Inicializace je součástí deklaraci vlastnosti, což usnadňuje odpovídá přidělení úložiště pro veřejné rozhraní `Student` objekty.

## <a name="expression-bodied-function-members"></a>Členové tvoření výrazy – funkce

Mnoho členů, které napíšete jsou jednotlivé příkazy, které mohou být jednoho výrazy. Místo toho zapisovat na člena s výrazem v těle. Funguje to pro metody a vlastnosti jen pro čtení. Například přepsání `ToString()` často je vynikající kandidát:

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

Pro vlastnosti jen pro čtení můžete také použít tuto syntaxi:

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Změna existujícího člena pro člena vozidlo výrazu je [binární kompatibilní změnu](version-update-considerations.md#binary-compatible-changes).

## <a name="using-static"></a>Pomocí statické

*Pomocí statické* vylepšení umožňuje importovat statické metody jednu třídu. Můžete zadat třídu, kterou používáte:

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<xref:System.Math> Neobsahuje žádné metody instance. Můžete také použít `using static` importovat třídy statické metody pro třídu, která má statické a metody instance. Jedním z nejužitečnějších příkladů je <xref:System.String>:

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> Musíte použít plně kvalifikovaný název třídy, `System.String` v statický příkaz using.  Nelze použít `string` – klíčové slovo místo.

Při importu z `static using` , rozšiřující metody jsou pouze v oboru při volány pomocí syntaxe volání metody rozšíření. Proto nejsou v oboru při volá jako statická metoda. To se často zobrazí v dotazech LINQ. Vzor LINQ můžete importovat pomocí importu <xref:System.Linq.Enumerable>, nebo <xref:System.Linq.Queryable>.

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

Obvykle volání metody rozšíření používat výrazy typu invocation – metoda rozšíření. Přidání názvu třídy ve výjimečných případech, kde je volat pomocí volání statické metody řeší nejednoznačnost syntaxe.

`static using` Direktiva také importuje všechny vnořené typy. Můžete odkazovat na jakékoli vnořené typy bez kvalifikace.

## <a name="null-conditional-operators"></a>Podmíněné operátory s Null

*Null podmiňovací operátor* mnohem jednodušší a plynulé provede kontroly hodnoty null. Nahraďte přístup ke členu `.` s `?.`:

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

V předchozím příkladu je proměnná `first` je přiřazena `null` Pokud objekt osoba `null`. V opačném případě je přiřazena hodnota `FirstName` vlastnost. Co je nejdůležitější `?.` znamená, že negeneruje tento řádek kódu `NullReferenceException` Pokud `person` proměnná je `null`. Místo toho zkratům a vrátí `null`. Můžete také null podmíněný operátor pro přístup k poli nebo indexeru. Nahraďte `[]` s `?[]` ve výrazu indexu.

Vrátí následující výraz `string`bez ohledu hodnotu `person`. Tento konstruktor se často používají *nulové sloučení* operátor přiřazení výchozí hodnoty, pokud jedna z vlastností `null`. Pokud výraz zkratům, `null` vrácená hodnota je typu tak, aby odpovídaly úplného výrazu.

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

Můžete také použít `?.` podmíněně volat metody. Nejběžnější použití nástroje členské funkce s hodnotou null podmíněný operátor je pro bezpečné vyvolání delegátů (nebo obslužné rutiny událostí), které mohou být `null`.  Bude volání delegáta `Invoke` pomocí metody `?.` operátor pro přístup k členu. Můžete zobrazit příklad v [delegovat vzory](../delegates-patterns.md#handling-null-delegates) článku.

Pravidla `?.` operátor Ujistěte se, že levá strana operátoru je vyhodnocen pouze jednou. Umožňuje mnoho idiomy, včetně následující příklad pomocí obslužných rutin událostí:

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

Zajištění, že na levé straně je vyhodnocen pouze jednou můžete také použít libovolný výraz, včetně volání metod na levé straně `?.`

## <a name="string-interpolation"></a>Interpolace řetězců

S C# 6, nové [interpolace](../language-reference/tokens/interpolated.md) funkce umožňuje vložení výrazů do řetězce. Jednoduše začínat řetězec s `$`a používat výrazy mezi `{` a `}` místo řadové číslovky:

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

Tento příklad používá vlastnosti pro nahrazeny výrazy. Můžete použít libovolný výraz. Například může vypočítat průměr student získal na podnikové úrovni jako součást interpolace:

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

Naformátuje hodnotu pro předchozí řádek kódu `Grades.Average()` jako číslo s plovoucí desetinnou čárkou se dvěma desetinnými místy.

Často je potřeba formátovací řetězec vytvořený pomocí konkrétní jazykové verze. Použít skutečnost, že objekt vytvořený testovaným interpolace řetězců lze implicitně převést na <xref:System.FormattableString?displayProperty=nameWithType>. <xref:System.FormattableString> Instance obsahuje složeném formátovacím řetězci a výsledky vyhodnocování výrazů před převedením na řetězce. Použití <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metoda zadat jazykovou verzi, při formátování řetězce. Následující příklad vytvoří řetězec za použití němčina (de-DE) jazykovou verzi. (Ve výchozím nastavení, Německá jazyková verze používá znak "," jako oddělovač desetinných míst a "." znak jako tisíců oddělovač.)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

Začít s interpolace řetězců, přečtěte si článek [interpolace v C# ](../tutorials/exploration/interpolated-strings.yml) Interaktivní kurz, [interpolace řetězců](../language-reference/tokens/interpolated.md) článku a [interpolace v C# ](../tutorials/string-interpolation.md) kurzu.

## <a name="exception-filters"></a>Filtry výjimek

*Filtry výjimek* jsou klauzule, které určují, kdy by použít klauzuli catch. daný. Pokud výraz použitý pro filtr výjimek vyhodnocuje na `true`, klauzule catch provádí běžného zpracování při výskytu výjimky. Pokud je výraz vyhodnocen `false`, pak bude `catch` klauzule se přeskočí. Zjistit informace o výjimce k určení, zda je jedno použití `catch` klauzule může zpracovat výjimku:

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

## <a name="the-nameof-expression"></a>`nameof` Výraz

`nameof` Výraz vyhodnocen jako název symbolu. To je skvělý způsob, jak získat nástroje pracovat pokaždé, když budete potřebovat název proměnné, vlastnost nebo pole členů. Jeden z nejčastěji používaných používá pro `nameof` je k poskytnutí názvu symbolu, která způsobila výjimku:

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

Další možností použití je aplikace založené na XAML, které implementují `INotifyPropertyChanged` rozhraní:

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

## <a name="await-in-catch-and-finally-blocks"></a>Operátor await v Catch a blocích Finally

C# 5 má několik omezení kde mohli byste umístit `await` výrazy. S C# 6, můžete nyní použít `await` v `catch` nebo `finally` výrazy. To se nejčastěji používá v případě protokolování:

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

Podrobnosti implementace pro přidání `await` podporovala uvnitř `catch` a `finally` klauzule Ujistěte se, že její chování je konzistentní s chování pro synchronní kód. Při spouštění kódu v `catch` nebo `finally` klauzule vyvolá výjimku, provádění hledá vhodný `catch` klauzule v další okolní bloku. Pokud se aktuální výjimku, tato výjimka bude ztracena. Stejné se stane s očekávané výrazy v `catch` a `finally` klauzulí: vhodný `catch` prohledána, a na aktuální výjimku, pokud existuje, dojde ke ztrátě.  

> [!NOTE]
> Toto chování je z důvodu se doporučuje pro zápis `catch` a `finally` klauzule pečlivě, aby nedošlo k zavedení nové výjimky.

## <a name="initialize-associative-collections-using-indexers"></a>Inicializovat asociativní kolekce pomocí indexerů

*Inicializátory indexů* je jedním ze dvou funkcí, které usnadňují inicializátory kolekce konzistentnější s využitím indexu. V dřívějších verzích C#, můžete použít *inicializátory kolekce* s kolekcemi styl sekvence, včetně <xref:System.Collections.Generic.Dictionary%602>, tím, že přidáte počet závorek kolem klíč a páry hodnot:

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#CollectionInitializer)]

Můžete využít s <xref:System.Collections.Generic.Dictionary%602> kolekce a další typy, kde přístupný `Add` metoda přijímá více než jeden argument. Nová syntaxe podporuje přiřazení do kolekce pomocí indexu:

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

Tato funkce znamená, že asociativní kontejnery mohou být inicializovány pomocí syntaxe podobné co bylo nastavené pro kontejnery sekvence pro několik verzí.

## <a name="extension-add-methods-in-collection-initializers"></a>Rozšíření `Add` metody v inicializátory kolekce

Další funkce, která usnadňuje inicializace kolekce je schopnost používat *– metoda rozšíření* pro `Add` metody. Tato funkce byla přidána parita s jazykem Visual Basic. Tato funkce je nejužitečnější v případě, že máte vlastní třídu kolekce, která obsahuje metodu s jiným názvem sémanticky přidávat nové položky.

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
