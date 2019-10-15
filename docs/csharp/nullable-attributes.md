---
title: Upgradovat rozhraní API s atributy pro definování očekávání null
description: Tento článek vysvětluje podněty a techniky pro přidání popisných atributů k popisu nulového stavu argumentů a vrácených hodnot z rozhraní API.
ms.date: 07/31/2019
ms.openlocfilehash: c51ec81f77bb1d31168848d8d51e68a08965d42c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319071"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Aktualizace knihoven pro použití typů odkazů s možnou hodnotou null a sdělování pravidel s možnou hodnotou null volajícím

Přidání [odkazových typů s možnou hodnotou null](nullable-references.md) znamená, že můžete deklarovat, zda je hodnota `null` pro každou proměnnou povolená nebo očekávaná. Poskytuje skvělé prostředí při psaní kódu. Zobrazí se upozornění, pokud může být proměnná bez hodnoty null nastavena na `null`. Zobrazí se upozornění, pokud u proměnné s možnou hodnotou null není zkontrolována hodnota null před tím, než ji zrušíte. Aktualizace knihoven může chvíli trvat, ale výnosy je. Další informace, které do kompilátoru zadáte, *Pokud* je hodnota `null` povolená nebo zakázaná, budou se lépe zobrazovat uživatelé vašeho rozhraní API. Pojďme začít se známým příkladem. Představte si, že knihovna má následující rozhraní API k načtení řetězce prostředků:

```csharp
bool TryGetMessage(string key, out string message)
```

Předchozí příklad dodržuje známý vzor `Try*` v rozhraní .NET. Pro toto rozhraní API existují dva argumenty odkazů: `key` a parametr `message`. Toto rozhraní API má následující pravidla týkající se hodnoty null těchto argumentů:

- Volající by neměl předat `null` jako argument pro `key`.
- Volající mohou předat proměnnou, jejíž hodnota je `null` jako argument pro `message`.
- Pokud metoda `TryGetMessage` vrátí `true`, hodnota `message` není null. Pokud je vrácená hodnota `false,`, hodnota `message` (a její stav null) má hodnotu null.

Pravidlo pro `key` může být zcela vyjádřeno typem proměnné: `key` by měl být odkazový typ, který není null. Parametr `message` je složitější. Povoluje jako argument hodnotu `null`, ale garantuje, že při úspěchu není argument `out` null. V těchto scénářích potřebujete podrobnější slovník, který popisuje očekávání.

Aktualizace knihovny pro odkazy s možnou hodnotou null vyžaduje více než automatické postřikovače `?` u některých proměnných a názvů typů. Předchozí příklad ukazuje, že je nutné projít vaše rozhraní API a vzít v úvahu vaše očekávání pro každý vstupní argument. Vezměte v úvahu záruky pro vrácenou hodnotu a všechny argumenty `out` nebo `ref` na vrácení metody. Potom tyto pravidla sdělí kompilátoru a kompilátor poskytne upozornění, pokud se volajícím tyto pravidla neřídí.

Tato práce trvá určitou dobu. Pojďme začít s strategiemi, které vaší knihovně nebo aplikaci zohledňují hodnoty null, zatímco se vyrovnávají další požadavky a dodávky. Uvidíte, jak vyrovnávat průběžný vývoj a povolit typy odkazů s možnou hodnotou null. Seznámíte se s problémy s definicemi obecného typu. Dozvíte se, jak použít atributy k popisu před a po jednotlivých podmínkách rozhraní API.

## <a name="choose-a-nullable-strategy"></a>Výběr strategie s možnou hodnotou null

První volbou je, že ve výchozím nastavení by se měly zapnout nebo vypnout typy odkazů s možnou hodnotou null. Máte dvě strategie:

- Povolte typy odkazů s možnou hodnotou null pro celý projekt a zakažte ho v kódu, který není připravený.
- Povolit pouze typy odkazů s možnou hodnotou null pro kód, který je opatřen poznámkou pro typy s možnou hodnotou null

První strategie funguje nejlépe při přidávání dalších funkcí do knihovny při jejich aktualizaci na typy odkazů s možnou hodnotou null. Veškerý nový vývoj má na paměti s možnou hodnotou null. Při aktualizaci existujícího kódu povolíte v těchto třídách typy odkazů s možnou hodnotou null.

Po této první strategii provedete následující:

1. Povolit typy s možnou hodnotou null pro celý projekt přidáním prvku `<Nullable>enable</Nullable>` do souborů *csproj* . 
1. Přidejte direktivu pragma `#nullable disable` do každého zdrojového souboru v projektu. 
1. Při práci na jednotlivých souborech odeberte direktivu pragma a vyřešte všechna upozornění.

Tato první strategie obsahuje více než více práce pro přidání direktivy pragma do každého souboru. Výhodou je, že každý nový soubor kódu přidaný do projektu bude mít povolenou hodnotu null. Jakékoli nové práce budou mít na paměti nabývat hodnoty null; je nutné aktualizovat pouze existující kód.

Druhá strategie funguje lépe, pokud je knihovna obecně stabilní a hlavní fokus vývoje je přijmout typy odkazů s možnou hodnotou null. Při přidávání poznámek k rozhraním API můžete zapnout typy odkazů s možnou hodnotou null. Až budete hotovi, povolte v celém projektu typy odkazů s možnou hodnotou null.

Po této druhé strategii provedete následující:

1. Přidejte direktivu pragma `#nullable enable` do souboru, pro který chcete nastavit nepovolenou hodnotu null.
1. Vyřešte všechna upozornění.
1. Pokračujte v těchto prvních dvou krocích, dokud nebudete mít k celou knihovnu s podporou null.
1. Povolit typy s možnou hodnotou null pro celý projekt přidáním prvku `<Nullable>enable</Nullable>` do souborů *csproj* . 
1. Odeberte direktivy pragma `#nullable enable`, protože už nejsou potřeba.

Tato druhá strategie má méně práce předem. Kompromisy je, že první úkol při vytváření nového souboru je přidání direktivy pragma a zpřístupnění hodnoty null. Pokud se některý z vývojářů v týmu zapomene, je nový kód v nedokončené práci, aby se zajistilo, že bude mít veškerý kód na hodnotu null.

Které z těchto strategií vybíráte, závisí na tom, kolik aktivního vývoje se v projektu provádí. Tím se zlepší a stabilnější váš projekt, tím lepší je druhá strategie. Vyvíjejí se další funkce, což je lepší první strategie.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Má upozornění na hodnotu null zavést průlomové změny?

Než povolíte typy odkazů s možnou hodnotou null, jsou proměnné považovány za *Nullable oblivious*. Jakmile povolíte typy odkazů s možnou hodnotou null, všechny tyto proměnné nebudou *mít hodnotu null*. Kompilátor bude vydávat upozornění, pokud tyto proměnné nejsou inicializovány na hodnoty, které nejsou null.

Dalším pravděpodobným zdrojem upozornění je vrácení hodnot, pokud hodnota nebyla inicializována.

Prvním krokem při adresování upozornění kompilátoru je použití `?` anotace u parametrů a návratových typů, které označují, kdy argumenty nebo návratové hodnoty mohou být null. Pokud referenční proměnné nesmí mít hodnotu null, je původní deklarace správná. V takovém případě váš cíl nestačí jenom opravit upozornění. Důležitější je, že kompilátor porozuměl vašemu záměru pro potenciální hodnoty null. Při kontrole upozornění se dostanete k vašemu dalšímu hlavnímu rozhodnutí o vaší knihovně. Chcete zvážit úpravu signatur rozhraní API, abyste mohli snadněji sdělit záměr návrhu? Lepší signatura rozhraní API pro metodu `TryGetMessage` prošetřená výše může být:

```csharp
string? TryGetMessage(string key);
```

Vrácená hodnota označuje úspěch nebo neúspěch a přenese hodnotu, pokud byla hodnota nalezena. V mnoha případech může změna signatur rozhraní API zlepšit způsob, jakým komunikuje hodnoty null.

Pro veřejné knihovny nebo knihovny s velkými základy uživatelů ale můžete raději nezavádět změny signatur rozhraní API. Pro tyto případy a další běžné vzory můžete použít atributy pro snadnější definování, když argument nebo návratová hodnota může být `null`. Bez ohledu na to, zda zvažte změnu povrchu rozhraní API, pravděpodobně zjistíte, že tyto anotace typu nejsou dostačující pro popis hodnot `null` pro argumenty nebo návratové hodnoty. V těchto případech můžete použít atributy pro přehlednější Popis rozhraní API. 

## <a name="attributes-extend-type-annotations"></a>Atributy rozšiřuje anotace typu

Bylo přidáno několik atributů pro vyjádření dalších informací o stavu hodnoty null proměnných. Veškerý kód, který jste C# napsali před 8 představenými typy odkazů s možnou hodnotou null, byl *null oblivious* To znamená, že jakákoli proměnná typu odkazu může mít hodnotu null, ale kontroly hodnoty null nejsou požadovány. Jakmile kód bude *mít na paměti hodnotu s možnou hodnotou null*, změní se tato pravidla. Odkazové typy by nikdy neměly být hodnotou `null` a typy odkazů s možnou hodnotou null musí být před zpětným odkazem zkontrolovány na `null`.

Pravidla pro vaše rozhraní API jsou pravděpodobně složitější, jak jste viděli ve scénáři `TryGetValue` rozhraní API. Mnohé z vašich rozhraní API mají složitější pravidla, kdy proměnné můžou nebo nemůžou být `null`. V těchto případech použijete jeden z následujících atributů pro vyjádření těchto pravidel:

- [AllowNull má](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): vstupní argument, který nemůže mít hodnotu null, může mít hodnotu null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): návratová hodnota, která není null, může mít hodnotu null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): návratová hodnota s možnou hodnotou null nikdy nebude null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): vstupní argument, který nemůže mít hodnotu null, může mít hodnotu null, pokud metoda vrátí zadanou hodnotu `bool`.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): vstupní argument s možnou hodnotou null nebude mít hodnotu null, pokud metoda vrátí zadanou hodnotu `bool`.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): návratová hodnota není null, pokud argument pro zadaný parametr není null.

Předchozí popisy představují rychlý odkaz na to, co každý atribut dělá. Každá z následujících částí popisuje chování a lepší význam.

Přidáním těchto atributů poskytne kompilátor více informací o pravidlech pro vaše rozhraní API. Při volání kódu v kontextu s povolenou hodnotou null, kompilátor upozorní volající, když porušují tato pravidla. Tyto atributy neumožňují u implementace další kontroly.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Zadejte předpoklady: `AllowNull` a `DisallowNull`.

Zvažte vlastnost pro čtení a zápis, která nikdy nevrací `null`, protože má rozumnou výchozí hodnotu. Volající přecházejí `null` do přístupového objektu set při jeho nastavování na tuto výchozí hodnotu. Představte si třeba systém zasílání zpráv, který se zeptá na název obrazovky v chatovací místnosti. Pokud není k dispozici žádný, systém vygeneruje náhodný název:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Pokud kompilujete předchozí kód v oblivious kontextu s možnou hodnotou null, vše je dobré. Po povolení typů odkazů s možnou hodnotou null se vlastnost `ScreenName` stala odkazem, který neumožňuje hodnotu null. To je správné pro přístup `get`: nikdy nevrátí `null`. Volající nepotřebují kontrolovat vrácenou vlastnost pro `null`. Ale nyní nastavuje vlastnost na `null` vygeneruje upozornění. Aby bylo možné pokračovat v podpoře tohoto typu kódu, přidejte do vlastnosti atribut <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType>, jak je znázorněno v následujícím kódu: 

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Pro použití tohoto a dalších atributů, které jsou popsány v tomto článku, bude pravděpodobně nutné přidat direktivu `using` pro <xref:System.Diagnostics.CodeAnalysis>. Atribut se použije na vlastnost, nikoli přístupový objekt `set`. Atribut `AllowNull` určuje *předběžné podmínky*a vztahuje se pouze na vstupy. Přístupový objekt `get` má návratovou hodnotu, ale žádné vstupní argumenty. Proto atribut `AllowNull` platí pouze pro přístup k přístupovému objektu `set`.

Předchozí příklad ukazuje, co je třeba najít při přidávání atributu `AllowNull` v argumentu:

1. Obecnou smlouvou pro tuto proměnnou je, že by neměla být `null`, takže chcete typ odkazu, který nepovoluje hodnotu null.
1. Existují situace, kdy vstupní proměnná bude `null`, i když nejsou nejběžnějším využitím.

Nejčastěji budete potřebovat tento atribut pro vlastnosti nebo argumenty `in`, `out` a `ref`. Je-li proměnná obvykle nenulová, je nejlepší volbou atribut `AllowNull`, ale je třeba v předběžných podmínkách umožnit `null`.

Na rozdíl od scénářů použití `DisallowNull`: pomocí tohoto atributu určíte, že vstupní proměnná typu s možnou hodnotou null by neměla být `null`. Vezměte v úvahu vlastnost, kde `null` je výchozí hodnota, ale klienti ji můžou nastavit jenom na jinou hodnotu než null. Vezměte v úvahu následující kód:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Předchozí kód je nejlepším způsobem, jak vyjádřit návrh, že `ReviewComment` by mohlo být `null`, ale nelze je nastavit na `null`. Jakmile tento kód bude mít na paměti hodnotu s možnou hodnotou null, můžete tento koncept zřetelně vyjádřit volajícím pomocí <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:

```csharp
[DisallowNull] 
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

V kontextu s možnou hodnotou null může přístupový objekt `ReviewComment` `get` vrátit výchozí hodnotu `null`. Kompilátor upozorní, že před přístupem musí být zkontrolován. Kromě toho upozorňuje volající, že i když by to bylo `null`, volající by se neměli explicitně nastavit na `null`. Atribut `DisallowNull` také určuje *předběžnou podmínku*, nemá vliv na přistupující objekt `get`. Pokud si vyberete tyto vlastnosti, měli byste použít atribut `DisallowNull`:

1. Proměnná by mohla být `null` v základních scénářích, často při první instanci.
1. Proměnná by neměla být explicitně nastavená na `null`.

Tyto situace jsou běžné v kódu, který byl původně *null oblivious*. Je možné, že vlastnosti objektu jsou nastaveny ve dvou různých inicializačních operacích. Je možné, že některé vlastnosti jsou nastaveny až po dokončení některé asynchronní práce.

Atributy `AllowNull` a `DisallowNull` umožňují určit, že představy pro proměnné nemusí odpovídat na tyto proměnné anotace s možnou hodnotou null. Poskytují podrobnější informace o vlastnostech vašeho rozhraní API. Tyto další informace pomáhají volajícímu používat rozhraní API správně. Nezapomeňte zadat předpoklady pomocí následujících atributů:

- [AllowNull má](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): vstupní argument, který nemůže mít hodnotu null, může mít hodnotu null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Zadejte podmínky post-Conditions: `MaybeNull` a `NotNull`.

Předpokládejme, že máte metodu s následujícím podpisem:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Pravděpodobně jste napsali metodu, jako to, aby vracela `null`, když se hledané jméno nenašlo. @No__t-0 jasně označuje, že se záznam nenašel. V tomto příkladu jste pravděpodobně změnili návratový typ z `Customer` na `Customer?`. Deklarace návratové hodnoty jako typ odkazu s možnou hodnotou null určuje záměr tohoto rozhraní API jasně. 

Z důvodů uvedených v rámci [obecných definic a možností použití hodnoty null](#generic-definitions-and-nullability) , které technika nepracuje s obecnými metodami. Je možné, že budete mít obecnou metodu, která následuje podobný vzor:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Nelze určit, že návratová hodnota je `T?`. Metoda vrátí `null`, pokud se požadovaná položka nenajde. Vzhledem k tomu, že nemůžete deklarovat návratový typ `T?`, přidáte do metody návratovou poznámku `MaybeNull`:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Předchozí kód informuje volající, že kontrakt implikuje typ, který nemůže mít hodnotu null, ale vrácená hodnota *může* být null.  Použijte atribut `MaybeNull`, pokud by vaše rozhraní API mělo být typ, který není null, obvykle parametr obecného typu, ale může se jednat o instance, kde by se vrátila `null`.

Můžete také určit, že návratová hodnota nebo argument `out` nebo `ref` není null, přestože typ je typ s možnou hodnotou null. Vezměte v úvahu metodu, která zajistí, že je pole dostatečně velké pro udržení počtu prvků. Pokud vstupní argument nemá kapacitu, rutina přidělí nové pole a zkopíruje do něj všechny existující prvky. Pokud je vstupním argumentem `null`, rutina by přidělila nové úložiště. Pokud existuje dostatečná kapacita, rutina neprovede nic:

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

Tuto rutinu můžete zavolat následujícím způsobem:

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

Po povolení typů odkazů s hodnotou null Chcete zajistit, aby předchozí kód byl zkompilován bez upozornění. Když metoda vrátí hodnotu, argument `storage` zaručuje, že nesmí mít hodnotu null. Je však přijatelné volat `EnsureCapacity` s odkazem s hodnotou null. Můžete nastavit `storage` typ odkazu s možnou hodnotou null a přidat podmínku `NotNull` po deklaraci parametru:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

Předchozí kód vyjadřuje jednoznačně stávající kontrakt: volající mohou předat proměnnou s hodnotou `null`, ale návratová hodnota je zaručena, že nikdy nebude mít hodnotu null. Atribut `NotNull` je nejužitečnější pro argumenty `ref` a `out`, kde `null` může být předán jako argument, ale u tohoto argumentu je zaručeno, že nebude mít hodnotu null, pokud se metoda vrátí.

Nepodmíněné následné podmínky se zadává pomocí následujících atributů:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): návratová hodnota, která není null, může mít hodnotu null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): návratová hodnota s možnou hodnotou null nikdy nebude null.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Zadejte podmíněné podmínky odeslání: `NotNullWhen`, `MaybeNullWhen` a `NotNullIfNotNull`.

Pravděpodobně jste obeznámeni s metodou `string` <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>. Tato metoda vrací `true`, pokud má argument hodnotu null nebo prázdný řetězec. Jedná se o podobu hodnoty null-check: volající nemusí mít hodnotu null. Pokud metoda vrátí hodnotu `false`, zaškrtnete argument. Chcete-li vytvořit metodu, jako je tato vlastnost s možnou hodnotou null, nastavte argument na typ s možnou hodnotou null a přidejte atribut `NotNullWhen`:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

Informuje kompilátor o tom, že jakýkoli kód, kde je vrácená hodnota `false` nemusí být zaškrtnutou hodnotou null. Přidání atributu informuje o statické analýze kompilátoru, které `IsNullOrEmpty` provádí potřebnou kontrolu null: když vrátí `false`, vstupní argument není `null`.

```csharp
string? userInput = GetUserInput();
if (!(string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

Metoda <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> bude označena jako uvedená výše pro .NET Core 3,0. Můžete mít podobné metody v základu kódu, které kontrolují stav objektů pro hodnoty null. Kompilátor nerozpozná vlastní metody kontroly null a bude nutné poznámky přidat sami. Když přidáte atribut, statická analýza kompilátoru zná, když byla testovaná proměnná vrácena na hodnotu null.

Jiné použití pro tyto atributy je vzor @no__t 0. Následné podmínky pro proměnné `ref` a `out` jsou přenášeny prostřednictvím návratové hodnoty. Zvažte tuto metodu popsanou výše:

```csharp
bool TryGetMessage(string key, out string message)
```

Předchozí metoda dodržuje typické rozhraní .NET idiom: vrácená hodnota označuje, zda byl `message` nastaven na zjištěnou hodnotu, nebo pokud není nalezena žádná zpráva, na výchozí hodnotu. Pokud metoda vrátí hodnotu `true`, hodnota `message` není null; v opačném případě metoda nastaví `message` na hodnotu null.

Pomocí atributu `NotNullWhen` můžete komunikovat s tímto idiom. Když aktualizujete podpis pro typy odkazů s možnou hodnotou null, udělejte `message` a `string?` a přidejte atribut:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

V předchozím příkladu je hodnota `message` v případě, že `TryGetMessage` vrátí `true`, považována za null. Podobné metody v základu kódu je vhodné opatřit stejným způsobem: argumenty mohou být `null` a známé jako nenulové, pokud metoda vrátí `true`.

Je možné, že budete potřebovat i jeden konečný atribut. V některých případech je nulový stav návratové hodnoty závislý na nulovém stavu jednoho nebo více vstupních argumentů. Tyto metody vrátí hodnotu, která není null, pokud některé vstupní argumenty nejsou `null`. Chcete-li tyto metody správně opatřit poznámkami, použijte atribut `NotNullIfNotNull`. Vezměte v úvahu následující metodu:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Pokud argument `url` není null, výstup není `null`. Jakmile jsou povoleny odkazy s hodnotou null, tento podpis funguje správně, pokud rozhraní API nikdy nepřijímá vstup s hodnotou null. Pokud ale může mít vstup hodnotu null, může být návratová hodnota také null. Proto můžete změnit signaturu na následující kód:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

To funguje i v případě, že bude často vynutit, aby volající implementovali dodatečné kontroly `null`. Kontraktem je, že návratová hodnota `null` pouze v případě, že je vstupní argument `url` `null`. Pro vyjádření této smlouvy byste si tuto metodu měli opatřit poznámkami, jak je znázorněno v následujícím kódu:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

Pro návratovou hodnotu a argument byly oba poznámy s `?`, což značí, že by mohlo být `null`. Atribut dále upřesňuje, že návratová hodnota nebude null, pokud argument `url` není `null`.

Podmíněný následné podmínky můžete zadat pomocí těchto atributů:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): vstupní argument, který nemůže mít hodnotu null, může mít hodnotu null, pokud metoda vrátí zadanou hodnotu `bool`.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): vstupní argument s možnou hodnotou null nebude mít hodnotu null, pokud metoda vrátí zadanou hodnotu `bool`.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): návratová hodnota není null, pokud vstupní argument pro zadaný parametr není null.

## <a name="generic-definitions-and-nullability"></a>Obecné definice a možnost použití hodnoty null

Správně komunikující stav null obecných typů a obecné metody vyžadují zvláštní péči. To je fakt, že typ hodnoty s možnou hodnotou null a typ odkazu s možnou hodnotou null jsou zásadním rozdílem. @No__t-0 je synonymum pro `Nullable<int>`, zatímco `string?` je `string` s atributem přidaným kompilátorem. Výsledkem je, že kompilátor nemůže vygenerovat správný kód pro `T?` bez vědomí, zda `T` je `class` nebo `struct`. 

To neznamená, že nemůžete použít typ s povolenou hodnotou null (buď typ hodnoty, nebo odkazový typ) jako argument typu pro uzavřený obecný typ. @No__t-0 a `List<int?>` jsou platné instance `List<T>`. 

To znamená, že nemůžete použít `T?` v deklaraci obecné třídy nebo metody bez omezení. Například <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> se nezmění, aby vracel `T?`. Toto omezení můžete překonat přidáním omezení `struct` nebo `class`. U některého z těchto omezení kompilátor ví, jak generovat kód pro `T` i `T?`.

Můžete chtít omezit typy používané pro argument obecného typu, aby byly typy bez hodnoty null. To lze provést přidáním omezení `notnull` u tohoto argumentu typu. Při použití tohoto omezení nesmí argument type být typ s možnou hodnotou null.

## <a name="conclusions"></a>Závěry

Přidání typů odkazů s možnou hodnotou null poskytuje počáteční slovník pro popis očekávání vašich rozhraní API pro proměnné, které by mohly být `null`. Další atributy poskytují bohatší slovník popisující stav null proměnných jako předpoklady a následné podmínky. Tyto atributy podrobněji popisují vaše očekávání a poskytují lepší prostředí pro vývojáře pomocí vašich rozhraní API.

Když aktualizujete knihovny pro kontext s možnou hodnotou null, přidejte tyto atributy, aby uživatelé vašich rozhraní API měli k správné využití. Tyto atributy vám pomůžou plně popsat stav hodnoty null vstupních argumentů a vrácených hodnot:

- [AllowNull má](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): vstupní argument, který nemůže mít hodnotu null, může mít hodnotu null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): návratová hodnota, která není null, může mít hodnotu null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): návratová hodnota s možnou hodnotou null nikdy nebude null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): vstupní argument, který nemůže mít hodnotu null, může mít hodnotu null, pokud metoda vrátí zadanou hodnotu `bool`.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): vstupní argument s možnou hodnotou null nebude mít hodnotu null, pokud metoda vrátí zadanou hodnotu `bool`.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): návratová hodnota není null, pokud vstupní argument pro zadaný parametr není null.
