---
title: Upgrade polí API pro typy odkazů s možnou hodnotou null s atributy, které definují očekávání pro hodnoty null
description: Naučte se používat popisné atributy AllowNull, DisallowNull, MaybeNull, NotNull a další plně popsat stav null vašich api.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: a4b1f851bcbe27dd4884d45eb6d1209ab54271d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79170360"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Aktualizace knihoven za účelem použití typů odkazů s možnou hodnotou null a komunikace pravidel s možnou hodnotou null volajícím

Přidání [typů odkazů s možnou hodnotou](nullable-references.md) null `null` znamená, že můžete deklarovat, zda je hodnota povolena nebo očekávána pro každou proměnnou. Kromě toho `AllowNull`můžete použít řadu atributů: `DisallowNull` `MaybeNull`, `NotNull` `NotNullWhen`, `MaybeNullWhen`, `NotNullWhenNotNull` , a zcela popsat nulové stavy argumentů a vrácených hodnot. To poskytuje skvělé zkušenosti při psaní kódu. Upozornění se vám objeví, pokud může být `null`proměnná s možnou hodnotou null nastavena na hodnotu . Upozornění, pokud proměnná s možnou hodnotou null není před dereferenced. Aktualizace knihoven může nějakou dobu trvat, ale odměny stojí za to. Čím více informací, které poskytnete `null` kompilátoru o *tom, kdy* je hodnota povolena nebo zakázána, tím lepší upozornění uživatelé vašeho rozhraní API získají. Začněme se známým příkladem. Představte si, že vaše knihovna má následující rozhraní API pro načtení řetězce prostředků:

```csharp
bool TryGetMessage(string key, out string message)
```

Předchozí příklad následuje známý `Try*` vzor v rozhraní .NET. Existují dva referenční argumenty pro `key` toto `message` rozhraní API: a parametr. Toto rozhraní API má následující pravidla týkající se nullness těchto argumentů:

- Volající by neměli `null` projít jako `key`argument pro .
- Volající mohou předat proměnnou, `null` jejíž `message`hodnota je jako argument pro .
- Pokud `TryGetMessage` metoda `true`vrátí , `message` hodnota není null. Pokud je `false,` vrácená hodnota `message` hodnota (a její stav null) je null.

Pravidlo pro `key` může být zcela vyjádřeno `key` typem proměnné: by měl být typ odkazu s hodnotou nes hotelnou hodnotou null. Parametr `message` je složitější. Umožňuje `null` jako argument, ale zaručuje, že na `out` úspěch, že argument není null. Pro tyto scénáře potřebujete bohatší slovní zásobu k popisu očekávání.

Aktualizace knihovny pro odkazy s možnou `?` hodnotou null vyžaduje více než pokrokání na některé proměnné a názvy typů. Předchozí příklad ukazuje, že je třeba prozkoumat vaše api a zvážit vaše očekávání pro každý vstupní argument. Zvažte záruky pro vrácenou hodnotu a všechny `out` nebo `ref` argumenty na vrácení metody. Pak sdělte tato pravidla kompilátoru a kompilátor poskytne upozornění, když volající nedodržují tato pravidla.

Tahle práce chce čas. Začněme se strategiemi, aby vaše knihovna nebo aplikace byla upozorněna na nulu a zároveň vyvažovala další požadavky a dodávky. Uvidíte, jak vyvážit probíhající vývoj, který umožňuje typy odkazů s možnou hodnotou null. Dozvíte se výzvy pro definice obecných typů. Naučíte se použít atributy k popisu před a po podmínkách na jednotlivých api.

## <a name="choose-a-nullable-strategy"></a>Zvolte strategii, jejíž hodnotu lze zrušit

První volbou je, zda null typy odkazů by měly být zapnuty nebo vypnuty ve výchozím nastavení. Máte dvě strategie:

- Povolte typy odkazů s možnou hodnotou null pro celý projekt a zakažte je v kódu, který není připraven.
- Povolit pouze typy odkazů s možnou hodnotou null pro kód, který byl anotován pro typy odkazů s možnou hodnotou null.

První strategie funguje nejlépe, když přidáváte další funkce do knihovny při aktualizaci pro typy odkazů s možnou hodnotou null. Všechny nové vývoj je null,,,,,,,,,,,,,,,,,,,,, Při aktualizaci existujícího kódu povolíte v těchto třídách typy odkazů s možnou hodnotou null.

Po této první strategii postupujte takto:

1. Povolte typy s možnou hodnotou null pro celý projekt přidáním `<Nullable>enable</Nullable>` prvku do souborů *csproj.*
1. Přidejte `#nullable disable` pragma do každého zdrojového souboru v projektu.
1. Při práci na každém souboru odeberte pragmu a zřete všechna varování.

Tato první strategie má více práce předem přidat pragma do každého souboru. Výhodou je, že každý nový soubor kódu přidaný do projektu bude mít hodnotu null povolenou hodnotou. Všechny nové práce budou nullable vědomi; je třeba aktualizovat pouze existující kód.

Druhá strategie funguje lépe, pokud je knihovna obecně stabilní a hlavním zaměřením vývoje je přijmout typy odkazů s možnou hodnotou null. Při osazování polí API zapnete typy odkazů s možnou hodnotou null. Po dokončení povolíte typy odkazů s možnou hodnotou null pro celý projekt.

V návaznosti na tuto druhou strategii postupujte takto:

1. Přidejte `#nullable enable` pragma do souboru, který chcete, aby null být vědomi.
1. Adresují všechna varování.
1. Pokračujte v těchto prvních dvou krocích, dokud neuvědomíte celou knihovnu, která by byla známa.
1. Povolte typy s možnou hodnotou null pro celý projekt přidáním `<Nullable>enable</Nullable>` prvku do souborů *csproj.*
1. Odstraňte `#nullable enable` pragmy, protože už nejsou potřeba.

Tato druhá strategie má méně práce předem. Kompromis je, že první úkol při vytváření nového souboru je přidat pragma a učinit ji nullable aware. Pokud všichni vývojáři ve vašem týmu zapomenout, že nový kód je nyní v nevyřízených položkách práce, aby všechny kód nullable aware.

Která z těchto strategií si vyberete, závisí na tom, kolik aktivního vývoje probíhá ve vašem projektu. Čím zralejší a stabilnější váš projekt, tím lepší je druhá strategie. Čím více funkcí se vyvíjí, tím lepší je první strategie.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Měla by zavést neplatné výstrahy narušující změny?

Před povolením typů odkazů s možnou hodnotou null jsou proměnné považovány za *netečné*. Jakmile povolíte typy odkazů s možnou hodnotou null, všechny tyto proměnné jsou *nenulové*. Kompilátor vydá upozornění, pokud tyto proměnné nejsou inicializovány na hodnoty bez nuly.

Dalším pravděpodobným zdrojem upozornění je vrácené hodnoty, pokud hodnota nebyla inicializována.

Prvním krokem při adresování upozornění kompilátoru je použití `?` anotací na parametr a návratové typy k označení, kdy argumenty nebo vrácené hodnoty mohou být nulové. Pokud referenční proměnné nesmí být null, původní deklarace je správná. Jak to uděláte, vaším cílem není jen opravit varování. Důležitější je, aby kompilátor pochopil váš záměr pro potenciální hodnoty null. Při zkoumání varování dosáhnete dalšího zásadního rozhodnutí pro vaši knihovnu. Chcete zvážit úpravu podpisů rozhraní API tak, aby jasněji sdělovaly záměr návrhu? Lepší podpis rozhraní `TryGetMessage` API pro dříve zkoumanou metodu může být:

```csharp
string? TryGetMessage(string key);
```

Vrácená hodnota označuje úspěch nebo neúspěch a nese hodnotu, pokud byla nalezena hodnota. V mnoha případech může změna podpisů rozhraní API zlepšit způsob, jakým komunikují hodnoty null.

Pro veřejné knihovny nebo knihovny s velkými uživatelskými základnami však můžete upřednostňovat nezavádět žádné změny podpisu rozhraní API. Pro tyto případy a další běžné vzory můžete atributy použít jasněji definovat, `null`kdy argument nebo vrácená hodnota může být . Bez ohledu na to, zda uvažujete o změně povrchu rozhraní API, pravděpodobně zjistíte, `null` že samotné poznámky typu nejsou dostatečné pro popis hodnot argumentů nebo vrácených hodnot. V těchto případech můžete atributy použít jasněji popsat rozhraní API.

## <a name="attributes-extend-type-annotations"></a>Atributy rozšiřují poznámky typu

Několik atributů byly přidány vyjádřit další informace o stavu null proměnných. Veškerý kód, který jste napsali před c# 8 představil null reference typy byl *null nevšímavý*. To znamená, že všechny proměnné typu odkazu může být null, ale null kontroly nejsou vyžadovány. Jakmile váš kód je *null,,,* tato pravidla změnit. Referenční typy by `null` nikdy měla být hodnota a nullable `null` typy odkazů musí být zkontrolovány proti před tím, než je odkazováno.

Pravidla pro vaše rozhraní API jsou pravděpodobně složitější, `TryGetValue` jak jste viděli u scénáře rozhraní API. Mnoho vašich api mají složitější pravidla pro proměnné může `null`nebo nemůže být . V těchto případech použijete k vyjádření těchto pravidel jeden z následujících atributů:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Vstupní argument, který nelze upustit, může mít hodnotu null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Vrácená hodnota, jejíž nenulovatelná hodnota může být null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Vrácená hodnota s možnou hodnotou null nikdy nebude null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Vstupní argument, který nelze utnou, `bool` může mít hodnotu null, pokud metoda vrátí zadanou hodnotu.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Vstupní argument s možnou hodnotou null `bool` nebude null, pokud metoda vrátí zadanou hodnotu.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Vrácená hodnota není null, pokud argument pro zadaný parametr není null.

Předchozí popisy jsou stručný odkaz na to, co každý atribut dělá. Každá následující část popisuje chování a význam důkladněji.

Přidání těchto atributů poskytuje kompilátoru další informace o pravidlech pro rozhraní API. Při volání kódu je kompilován v kontextu s povoleným hodnotou null, kompilátor bude varovat volající, když porušují tato pravidla. Tyto atributy neumožňují další kontroly implementace.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Určete předběžné `AllowNull` podmínky: a`DisallowNull`

Zvažte vlastnost pro čtení `null` a zápis, která se nikdy nevrátí, protože má přiměřenou výchozí hodnotu. Volající předat `null` nastavit přistupujícího pole při jeho nastavení na tuto výchozí hodnotu. Zvažte například systém zasílání zpráv, který požádá o název obrazovky v chatovací místnosti. Pokud není k dispozici žádný, systém generuje náhodný název:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Při kompilaci předchozíkód v nečitelný kontext, vše je v pořádku. Jakmile povolíte typy odkazů `ScreenName` s možnou hodnotou null, vlastnost se stane nenulelným odkazem. To je správné `get` pro přistupující `null`ho: nikdy se vrátí . Volající nemusí kontrolovat vrácenou vlastnost pro `null`. Ale nyní nastavení `null` vlastnosti generuje upozornění. Chcete-li i nadále podporovat tento typ <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> kódu, přidejte atribut do vlastnosti, jak je znázorněno v následujícím kódu:

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Možná budete muset `using` přidat <xref:System.Diagnostics.CodeAnalysis> direktivu pro použití tohoto a dalších atributů popsaných v tomto článku. Atribut je použit a vlastnost, `set` nikoli přistupující objekt. Atribut `AllowNull` určuje *předběžné podmínky*a vztahuje se pouze na vstupy. Přistupující `get` odkaz má vrácenou hodnotu, ale žádné vstupní argumenty. Proto `AllowNull` atribut platí pouze pro `set` přistupujícího pole.

Předchozí příklad ukazuje, co hledat při `AllowNull` přidávání atributu na argument:

1. Obecná smlouva pro tuto proměnnou je, `null`že by neměla být , takže chcete typ odkazu s nemožnou hodnotou null.
1. Existují scénáře pro vstupní proměnné `null`, i když nejsou nejběžnější použití.

Nejčastěji budete potřebovat tento atribut pro `in` `out`vlastnosti `ref` , nebo , a argumenty. Atribut `AllowNull` je nejlepší volbou, pokud je proměnná obvykle non-null, ale je třeba povolit `null` jako předběžnou podmínku.

Kontrast, který se `DisallowNull`scénáře pro použití : Tento atribut slouží k určení, `null`že vstupní proměnná typu null by neměla být . Zvažte vlastnost, kde `null` je výchozí hodnota, ale klienti ji mohou nastavit pouze na hodnotu, která není null. Uvažujte následující kód:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Předchozí kód je nejlepší způsob, jak vyjádřit `ReviewComment` svůj `null`návrh, který by `null`mohl být , ale nelze nastavit na . Jakmile je tento kód nullable vědomi, můžete vyjádřit tento <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>koncept jasněji volajícím pomocí :

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

V kontextu s možnou hodnotou `ReviewComment` `get` null může `null`přistupující odkaz vrátit výchozí hodnotu aplikace . Kompilátor varuje, že musí být kontrolovány před přístupem. Kromě toho varuje volající, že i když `null`by to mohlo být , `null`volající by nemělexplicitně nastavit na . Atribut `DisallowNull` také určuje *předběžnou podmínku*, nemá `get` vliv na přistupující ho. Atribut byste měli `DisallowNull` použít, pokud sledujete tyto charakteristiky:

1. Proměnná může `null` být v základních scénářích, často při první instanci.
1. Proměnná by neměla být `null`explicitně nastavena na .

Tyto situace jsou běžné v kódu, který byl původně *null nevšímavý*. Je možné, že vlastnosti objektu jsou nastaveny ve dvou odlišných inicializačních operacích. Je možné, že některé vlastnosti jsou nastaveny pouze po dokončení některé asynchronní práce.

`AllowNull` Atributy `DisallowNull` a umožňují určit, že předběžné podmínky na proměnné nemusí odpovídat poznámky s hodnotou null na tyto proměnné. Tyto poskytují další podrobnosti o charakteristikách rozhraní API. Tyto další informace pomáhají volajícím správně používat vaše rozhraní API. Nezapomeňte zadat předběžné podmínky pomocí následujících atributů:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Vstupní argument, který nelze upustit, může mít hodnotu null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Uveďte post-podmínky: `MaybeNull` a`NotNull`

Předpokládejme, že máte metodu s následujícím podpisem:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Pravděpodobně jste napsali metodu, `null` jako je tato, abyste se vrátili, když se nenašel hledaný název. Jasně `null` ukazuje, že záznam nebyl nalezen. V tomto příkladu byste pravděpodobně změnit `Customer` návratový typ z na `Customer?`. Deklarování vrácené hodnoty jako typu odkazu s možnou hodnotou null jasně určuje záměr tohoto rozhraní API.

Z důvodů uvedených v [obecných definicích a nullability](#generic-definitions-and-nullability) tato technika nefunguje s obecnými metodami. Můžete mít obecnou metodu, která následuje podobný vzor:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Nelze určit, že vrácená `T?`hodnota je . Metoda vrátí, `null` když není nalezena požadovaná položka. Vzhledem k tomu, `T?` že nelze deklarovat návratový typ, přidáte poznámku `MaybeNull` k metodě return:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Předchozí kód informuje volající, že smlouva znamená typ s nulou, ale vrácená hodnota *může* být ve skutečnosti null.  Použijte `MaybeNull` atribut, pokud by vaše rozhraní API mělo být typu s nulovým hodnotou, `null` obvykle parametr obecného typu, ale mohou existovat instance, kde by měl být vrácen.

Můžete také určit, že vrácená hodnota nebo `out` nebo `ref` argument není null, i když typ je typ s možnou hodnotou null. Zvažte metodu, která zajišťuje, že pole je dostatečně velké pro uložení několika prvků. Pokud vstupní argument nemá kapacitu, rutina by přidělit nové pole a zkopírovat všechny existující prvky do něj. Pokud je `null`vstupní argument , rutina by přidělit nové úložiště. Pokud je dostatečná kapacita, rutina nedělá nic:

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

Dalo by se volat tuto rutinu takto:

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

Po povolení typů odkazů null, chcete zajistit, že předchozí kód zkompiluje bez upozornění. Když metoda vrátí, `storage` argument je zaručeno, že není null. Je však přijatelné volat `EnsureCapacity` s nulovým odkazem. Můžete vytvořit `storage` typ odkazu s možnou `NotNull` hodnotou null a přidat do deklarace parametru podmínku post-condition:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

Předchozí kód vyjadřuje existující smlouvy velmi jasně: Volající můžete předat `null` proměnnou s hodnotou, ale vrácená hodnota je zaručeno, že nikdy být null. Atribut `NotNull` je nejužitečnější pro `ref` a `out` argumenty, kde `null` mohou být předány jako argument, ale tento argument je zaručeno, že není null, když metoda vrátí.

Můžete zadat bezpodmínečné postconditions pomocí následujících atributů:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Vrácená hodnota, jejíž nenulovatelná hodnota může být null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Vrácená hodnota s možnou hodnotou null nikdy nebude null.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Určete podmíněné `NotNullWhen`post-podmínky: , `MaybeNullWhen`a`NotNullIfNotNull`

Pravděpodobně jste obeznámeni `string` s <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>metodou . Tato metoda `true` vrátí, pokud je argument null nebo prázdný řetězec. Je to forma null-check: Volající nemusí null-zkontrolovat argument, pokud metoda `false`vrátí . Chcete-li metodu, jako je tato nullable aware, byste nastavit argument `NotNullWhen` na typ s hodnotou null a přidat atribut:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

To informuje kompilátor, že žádný kód, kde je `false` vrácená hodnota nemusí být null-kontrolovány. Přidání atributu informuje statické analýzy kompilátoru, který `IsNullOrEmpty` provádí potřebnou `false`kontrolu null: `null`když vrátí , vstupní argument není .

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

Metoda <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> bude uvedena v notaci, jak je uvedeno výše pro .NET Core 3.0. Můžete mít podobné metody v základu kódu, které kontrolují stav objektů pro nulové hodnoty. Kompilátor nerozpozná vlastní metody kontroly null a poznámky budete muset přidat sami. Když přidáte atribut, statická analýza kompilátoru ví, kdy byla ověřená proměnná zkontrolována.

Dalším použitím pro tyto `Try*` atributy je vzor. Postconditions pro `ref` `out` a proměnné jsou sdělovány prostřednictvím vrácená hodnota. Zvažte tuto metodu zobrazenou dříve:

```csharp
bool TryGetMessage(string key, out string message)
```

Předchozí metoda následuje za typickým idiomem .NET: `message` vrácená hodnota označuje, zda byla nastavena na nalezenou hodnotu nebo, pokud není nalezena žádná zpráva, na výchozí hodnotu. Pokud metoda `true`vrátí , `message` hodnota není null; jinak metoda nastaví `message` na null.

Můžete komunikovat, že idiom pomocí atributu. `NotNullWhen` Při aktualizaci podpisu pro typy `message` odkazů `string?` s možnou hodnotou null vytvořte atribut a přidejte:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

V předchozím příkladu `message` je známo, že hodnota `TryGetMessage` není `true`null při vrátí . Měli byste anotovat podobné metody v základu kódu stejným způsobem: argumenty mohou být `null`a je `true`známo, že nejsou null, když metoda vrátí .

Je tu ještě jeden poslední atribut, který můžete také potřebovat. Někdy stav null vrácené hodnoty závisí na stavu null jednoho nebo více vstupních argumentů. Tyto metody vrátí hodnotu bez hodnoty null vždy, `null`když určité vstupní argumenty nejsou . Chcete-li správně opatří tyto metody, použijte `NotNullIfNotNull` atribut. Zvažte následující metodu:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Pokud `url` argument není null, výstup není `null`. Po povolení odkazů s možnou hodnotou null bude tento podpis fungovat správně za předpokladu, že rozhraní API nikdy nepřijme nulový vstup. Však pokud vstup může být null, pak vrácená hodnota může být také null. Proto můžete změnit podpis na následující kód:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

To také funguje, ale často nutí `null` volající implementovat další kontroly. Smlouva je, že vrácená `null` hodnota by `url` být `null`pouze v případě, že vstupní argument je . Chcete-li vyjádřit tuto smlouvu, měli byste anotovat tuto metodu, jak je znázorněno v následujícím kódu:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

Vrácená hodnota a argument byly anotovány `?` s označením, `null`že buď může být . Atribut dále objasňuje, že vrácená hodnota `url` nebude null, `null`pokud argument není .

Podmíněné postconditions zadáte pomocí těchto atributů:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Vstupní argument, který nelze utnou, `bool` může mít hodnotu null, pokud metoda vrátí zadanou hodnotu.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Vstupní argument s možnou hodnotou null `bool` nebude null, pokud metoda vrátí zadanou hodnotu.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Vrácená hodnota není null, pokud vstupní argument pro zadaný parametr není null.

## <a name="generic-definitions-and-nullability"></a>Obecné definice a nullability

Správná komunikace nulového stavu obecných typů a obecných metod vyžaduje zvláštní péči. To vyplývá ze skutečnosti, že typ hodnoty s možnou hodnotou s hodnotou null a typ odkazu s možnou hodnotou s možnou hodnotou null se zásadně liší. Synonymum `int?` pro `Nullable<int>`, `string?` vzhledem k tomu, že je `string` s atributem přidaným kompilátorem. Výsledkem je, že kompilátor nemůže `T?` generovat správný `T` kód, aniž by věděl, zda je `class` nebo `struct`.

To neznamená, že nelze použít typ s hodnotou null (typ hodnoty nebo typ odkazu) jako argument typu pro uzavřený obecný typ. Oba `List<string?>` `List<int?>` a jsou platné instance `List<T>`.

Co to znamená, že nelze `T?` použít v deklaraci obecné třídy nebo metody bez omezení. Například <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> nebude změněn na návrat `T?`. Toto omezení můžete překonat `struct` přidáním omezení nebo. `class` S některou z těchto omezení kompilátor ví, `T` `T?`jak generovat kód pro oba a .

Můžete chtít omezit typy používané pro obecný typ argumentu, které mají být nenulové typy. Můžete to udělat přidáním `notnull` omezení pro tento argument typu. When that constraint is applied, the type argument must not be a nullable type.

## <a name="conclusions"></a>Závěry

Přidání typů odkazů s možnou hodnotou null poskytuje počáteční slovní `null`zásobu k popisu očekávání api pro proměnné, které by mohly být . Další atributy poskytují bohatší slovní zásobu k popisu stavu null proměnných jako předpoklady a postconditions. Tyto atributy jasněji popisují vaše očekávání a poskytují lepší prostředí pro vývojáře, kteří používají vaše rozhraní API.

Při aktualizaci knihoven pro kontext s možnou hodnotou null přidejte tyto atributy, které uživatele vašich api navedou ke správnému použití. Tyto atributy vám pomohou plně popsat stav null vstupních argumentů a vrácených hodnot:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Vstupní argument, který nelze upustit, může mít hodnotu null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Vrácená hodnota, jejíž nenulovatelná hodnota může být null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Vrácená hodnota s možnou hodnotou null nikdy nebude null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Vstupní argument, který nelze utnou, `bool` může mít hodnotu null, pokud metoda vrátí zadanou hodnotu.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Vstupní argument s možnou hodnotou null `bool` nebude null, pokud metoda vrátí zadanou hodnotu.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Vrácená hodnota není null, pokud vstupní argument pro zadaný parametr není null.
