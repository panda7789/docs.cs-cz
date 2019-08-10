---
title: Upgradovat rozhraní API s atributy pro definování očekávání null
description: Tento článek vysvětluje podněty a techniky pro přidání popisných atributů k popisu nulového stavu argumentů a vrácených hodnot z rozhraní API.
ms.date: 07/31/2019
ms.openlocfilehash: eebd3d190b8c93833de6e1c1f1594c1c1f56e14e
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868887"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Aktualizace knihoven pro použití typů odkazů s možnou hodnotou null a sdělování pravidel s možnou hodnotou null volajícím

Přidání odkazových [typů s možnou hodnotou null](nullable-references.md) znamená, že můžete deklarovat `null` , zda je nebo není hodnota pro každou proměnnou povolena nebo očekávána. Poskytuje skvělé prostředí při psaní kódu. Zobrazí se upozornění, pokud může být proměnná bez hodnoty null nastavena na `null`. Zobrazí se upozornění, pokud u proměnné s možnou hodnotou null není zkontrolována hodnota null před tím, než ji zrušíte. Aktualizace knihoven může chvíli trvat, ale výnosy je. Další informace, které pro kompilátor poskytnete, *Pokud* `null` je hodnota povolená nebo zakázaná, budou se vám lépe zobrazovat uživatelé vašeho rozhraní API. Pojďme začít se známým příkladem. Představte si, že knihovna má následující rozhraní API k načtení řetězce prostředků:

```csharp
bool TryGetMessage(string key, out string message)
```

Předchozí příklad se řídí známým `Try*` vzorem v rozhraní .NET. Pro toto rozhraní API existují dva argumenty odkazů: `key` `message` a parametr. Toto rozhraní API má následující pravidla týkající se hodnoty null těchto argumentů:

- Volající by neměli předat `null` jako argument pro. `key`
- Volající mohou předat proměnnou, jejíž hodnota je `null` jako argument pro. `message`
- Pokud metoda vrátí `true`hodnotu, hodnota `message` není null. `TryGetMessage` Pokud je návratovou hodnotou `false,` `message` hodnota (a její stav null), má hodnotu null.

Pravidlo pro `key` může být zcela vyjádřeno typem proměnné: `key` typ odkazu, který neumožňuje hodnotu null. `message` Parametr je složitější. To umožňuje `null` jako argument, ale zaručuje, že po úspěšném dokončení tento `out` argument nemá hodnotu null. V těchto scénářích potřebujete podrobnější slovník, který popisuje očekávání.

Aktualizace knihovny pro odkazy s možnou hodnotou null vyžaduje více `?` než automatické automatických zadávání u některých proměnných a názvů typů. Předchozí příklad ukazuje, že je nutné projít vaše rozhraní API a vzít v úvahu vaše očekávání pro každý vstupní argument. Vezměte v úvahu záruky pro vrácenou hodnotu a jakékoli `out` argumenty `ref` nebo argumentů, které vrátí metoda. Potom tyto pravidla sdělí kompilátoru a kompilátor poskytne upozornění, pokud se volajícím tyto pravidla neřídí.

Tato práce trvá určitou dobu. Pojďme začít s strategiemi, které vaší knihovně nebo aplikaci zohledňují hodnoty null, zatímco se vyrovnávají další požadavky a dodávky. Uvidíte, jak vyrovnávat průběžný vývoj a povolit typy odkazů s možnou hodnotou null. Seznámíte se s problémy s definicemi obecného typu. Dozvíte se, jak použít atributy k popisu před a po jednotlivých podmínkách rozhraní API.

## <a name="choose-a-nullable-strategy"></a>Výběr strategie s možnou hodnotou null

První volbou je, že ve výchozím nastavení by se měly zapnout nebo vypnout typy odkazů s možnou hodnotou null. Máte dvě strategie:

- Povolte typy odkazů s možnou hodnotou null pro celý projekt a zakažte ho v kódu, který není připravený.
- Povolit pouze typy odkazů s možnou hodnotou null pro kód, který je opatřen poznámkou pro typy s možnou hodnotou null

První strategie funguje nejlépe při přidávání dalších funkcí do knihovny při jejich aktualizaci na typy odkazů s možnou hodnotou null. Veškerý nový vývoj má na paměti s možnou hodnotou null. Při aktualizaci existujícího kódu povolíte v těchto třídách typy odkazů s možnou hodnotou null.

Po této první strategii provedete následující:

1. Povolit typy s možnou hodnotou null pro celý projekt `<Nullable>enable</Nullable>` přidáním elementu do souborů *csproj* . 
1. `#nullable disable` Přidejte direktivu pragma do každého zdrojového souboru v projektu. 
1. Při práci na jednotlivých souborech odeberte direktivu pragma a vyřešte všechna upozornění.

Tato první strategie obsahuje více než více práce pro přidání direktivy pragma do každého souboru. Výhodou je, že každý nový soubor kódu přidaný do projektu bude mít povolenou hodnotu null. Jakékoli nové práce budou mít na paměti nabývat hodnoty null; je nutné aktualizovat pouze existující kód.

Druhá strategie funguje lépe, pokud je knihovna obecně stabilní a hlavní fokus vývoje je přijmout typy odkazů s možnou hodnotou null. Při přidávání poznámek k rozhraním API můžete zapnout typy odkazů s možnou hodnotou null. Až budete hotovi, povolte v celém projektu typy odkazů s možnou hodnotou null.

Po této druhé strategii provedete následující:

1. `#nullable enable` Přidejte direktivu pragma do souboru, pro který chcete nastavit nepovolenou hodnotu s podporou.
1. Vyřešte všechna upozornění.
1. Pokračujte v těchto prvních dvou krocích, dokud nebudete mít k celou knihovnu s podporou null.
1. Povolit typy s možnou hodnotou null pro celý projekt `<Nullable>enable</Nullable>` přidáním elementu do souborů *csproj* . 
1. `#nullable enable` Odeberte direktivy pragma, protože už nejsou potřeba.

Tato druhá strategie má méně práce předem. Kompromisy je, že první úkol při vytváření nového souboru je přidání direktivy pragma a zpřístupnění hodnoty null. Pokud se některý z vývojářů v týmu zapomene, je nový kód v nedokončené práci, aby se zajistilo, že bude mít veškerý kód na hodnotu null.

Které z těchto strategií vybíráte, závisí na tom, kolik aktivního vývoje se v projektu provádí. Tím se zlepší a stabilnější váš projekt, tím lepší je druhá strategie. Vyvíjejí se další funkce, což je lepší první strategie.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Má upozornění na hodnotu null zavést průlomové změny?

Než povolíte typy odkazů s možnou hodnotou null, jsou proměnné považovány za *Nullable oblivious*. Jakmile povolíte typy odkazů s možnou hodnotou null, všechny tyto proměnné nebudou *mít hodnotu null*. Kompilátor bude vydávat upozornění, pokud tyto proměnné nejsou inicializovány na hodnoty, které nejsou null.

Dalším pravděpodobným zdrojem upozornění je vrácení hodnot, pokud hodnota nebyla inicializována.

Prvním krokem při adresování upozornění kompilátoru je použití `?` poznámek na parametrech a návratových typech k označení, že argumenty nebo návratové hodnoty mohou být null. Pokud referenční proměnné nesmí mít hodnotu null, je původní deklarace správná. V takovém případě váš cíl nestačí jenom opravit upozornění. Důležitější je, že kompilátor porozuměl vašemu záměru pro potenciální hodnoty null. Při kontrole upozornění se dostanete k vašemu dalšímu hlavnímu rozhodnutí o vaší knihovně. Chcete zvážit úpravu signatur rozhraní API, abyste mohli snadněji sdělit záměr návrhu? Lepší signatura rozhraní API pro `TryGetMessage` dříve zkoumané metody může být:

```csharp
string? TryGetMessage(string key);
```

Vrácená hodnota označuje úspěch nebo neúspěch a přenese hodnotu, pokud byla hodnota nalezena. V mnoha případech může změna signatur rozhraní API zlepšit způsob, jakým komunikuje hodnoty null.

Pro veřejné knihovny nebo knihovny s velkými základy uživatelů ale můžete raději nezavádět změny signatur rozhraní API. Pro tyto případy a další běžné vzory můžete použít atributy pro přesnější definování v případě, že argument nebo návratová hodnota může být `null`. Bez ohledu na to, zda zvažte změnu povrchu rozhraní API, pravděpodobně zjistíte, že tyto anotace typu nejsou dostačující pro `null` popis hodnot argumentů nebo vrácených hodnot. V těchto případech můžete použít atributy pro přehlednější Popis rozhraní API. 

## <a name="attributes-extend-type-annotations"></a>Atributy rozšiřuje anotace typu

Bylo přidáno několik atributů pro vyjádření dalších informací o stavu hodnoty null proměnných. Veškerý kód, který jste C# napsali před 8 představenými typy odkazů s možnou hodnotou null, byl *null oblivious* To znamená, že jakákoli proměnná typu odkazu může mít hodnotu null, ale kontroly hodnoty null nejsou požadovány. Jakmile kód bude *mít na paměti hodnotu s možnou hodnotou null*, změní se tato pravidla. Odkazové typy by nikdy neměly `null` být hodnotou a pro typy odkazů s možnou hodnotou `null` null musí být před zpětným odkazem zkontrolovány.

Pravidla pro vaše rozhraní API jsou pravděpodobně složitější, jak jste viděli `TryGetValue` ve scénáři rozhraní API. Mnohé z vašich rozhraní API mají složitější pravidla, kdy proměnné můžou nebo nemůžou `null`být. V těchto případech použijete jeden z následujících atributů pro vyjádření těchto pravidel:

- [AllowNull má](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Vstupní argument, který nemůže mít hodnotu null, může mít hodnotu null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Návratová hodnota, která není null, může mít hodnotu null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Návratová hodnota s možnou hodnotou null nikdy nebude null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Pokud vrácená hodnota splňuje podmínku `ref` , může být hodnota null neboargumentunull.`out`
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Pokud vrácená hodnota `ref` splňuje podmínku, nemůže být hodnota null neboargumentunull.`out`
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Návratová hodnota není null, pokud vstupní argument pro zadaný parametr není null.

Předchozí popisy představují rychlý odkaz na to, co každý atribut dělá. Každá z následujících částí popisuje chování a lepší význam.

Přidáním těchto atributů poskytne kompilátor více informací o pravidlech pro vaše rozhraní API. Při volání kódu v kontextu s povolenou hodnotou null, kompilátor upozorní volající, když porušují tato pravidla. Tyto atributy neumožňují u implementace další kontroly.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Zadat předběžné podmínky: `AllowNull` a`DisallowNull`

Zvažte vlastnost pro čtení a zápis, která se `null` nikdy nevrátí, protože má rozumnou výchozí hodnotu. Volající přecházejí `null` do přístupového objektu set při jeho nastavení na tuto výchozí hodnotu. Představte si třeba systém zasílání zpráv, který se zeptá na název obrazovky v chatovací místnosti. Pokud není k dispozici žádný, systém vygeneruje náhodný název:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Pokud kompilujete předchozí kód v oblivious kontextu s možnou hodnotou null, vše je dobré. Po povolení typů `ScreenName` odkazů s možnou hodnotou null se vlastnost zobrazí jako odkaz bez hodnoty null. To je správné pro `get` přistupující objekt: nikdy se nevrátí. `null` Volající nepotřebují kontrolovat vrácenou vlastnost pro `null`. Ale teď vlastnost nastavíme tak `null` , aby vygenerovala upozornění. Aby bylo možné pokračovat v podpoře tohoto typu kódu, přidejte <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> atribut do vlastnosti, jak je znázorněno v následujícím kódu: 

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

`using` Pro<xref:System.Diagnostics.CodeAnalysis> použití tohoto a dalších atributů, které jsou popsány v tomto článku, bude pravděpodobně nutné přidat direktivu. Atribut se aplikuje na vlastnost, nikoli na `set` přistupující objekt. Atribut určuje *předběžné podmínky*a vztahuje se pouze na vstupy. `AllowNull` `get` Přistupující objekt má návratovou hodnotu, ale žádné vstupní argumenty. Proto se `set` atribut vztahuje pouze na přístup. `AllowNull`

Předchozí příklad ukazuje, co je třeba najít při přidávání `AllowNull` atributu v argumentu:

1. Obecnou smlouvou pro tuto proměnnou je, že by `null`neměla být, takže chcete typ odkazu, který nepovoluje hodnotu null.
1. Existují scénáře, které mají být `null`vstupní proměnné, i když nejsou nejběžnějším využitím.

Nejčastěji budete potřebovat tento atribut pro vlastnosti, nebo `in` `out`a `ref` argumenty. Atribut je nejlepší volbou v případě, že proměnná obvykle není null, ale je nutné `null` ji použít jako předběžnou podmínku. `AllowNull`

Na rozdíl od scénářů použití `DisallowNull`: Pomocí tohoto atributu určíte, že vstupní proměnná typu s možnou hodnotou null by `null`neměla být. Vezměte v úvahu vlastnost `null` , kde je výchozí hodnota, ale klienti ji můžou nastavit jenom na jinou hodnotu než null. Vezměte v úvahu následující kód:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Předchozí kód je nejlepším způsobem, jak vyjádřit návrh, který `ReviewComment` může být `null`, ale nelze jej nastavit na `null`. Jakmile tento kód bude mít na paměti hodnotu s možnou hodnotou null, můžete tento koncept srozumitelně <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>vyjádřit volajícím pomocí:

```csharp
[DisallowNull] 
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

V kontextu `ReviewComment` `null`s možnou hodnotou null může přístupovýobjektvrátitvýchozíhodnotu.`get` Kompilátor upozorní, že před přístupem musí být zkontrolován. Kromě toho upozorňuje volající, že i když to může být `null`, volající by se neměli explicitně nastavit na. `null` Atribut také určuje předběžnou *podmínku*, nemá vliv na `get` přistupující objekt. `DisallowNull` Tento `DisallowNull` atribut byste měli použít, pokud máte pozor na tyto charakteristiky:

1. Tato proměnná může být `null` v základních scénářích, často při první instanci.
1. Proměnná by neměla být explicitně nastavena na `null`.

Tyto situace jsou běžné v kódu, který byl původně *null oblivious*. Je možné, že vlastnosti objektu jsou nastaveny ve dvou různých inicializačních operacích. Je možné, že některé vlastnosti jsou nastaveny až po dokončení některé asynchronní práce.

Atributy `AllowNull` a`DisallowNull` umožňují určit, že představy pro proměnné nemusí odpovídat na tyto proměnné anotace s možnou hodnotou null. Poskytují podrobnější informace o vlastnostech vašeho rozhraní API. Tyto další informace pomáhají volajícímu používat rozhraní API správně. Nezapomeňte zadat předpoklady pomocí následujících atributů:

- [AllowNull má](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Vstupní argument, který nemůže mít hodnotu null, může mít hodnotu null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Zadat podmínky odeslání: `MaybeNull` a`NotNull`

Předpokládejme, že máte metodu s následujícím podpisem:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Pravděpodobně jste napsali metodu, která by měla vrátit `null` , když se hledané jméno nenašlo. `null` Jasně indikuje, že se záznam nenašel. V tomto příkladu jste pravděpodobně změnili návratový typ z `Customer` na. `Customer?` Deklarace návratové hodnoty jako typ odkazu s možnou hodnotou null určuje záměr tohoto rozhraní API jasně. 

Z důvodů uvedených v rámci [obecných definic a možností použití hodnoty null](#generic-definitions-and-nullability) , které technika nepracuje s obecnými metodami. Je možné, že budete mít obecnou metodu, která následuje podobný vzor:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Nemůžete určit, že návratová `T?`hodnota je. Metoda vrátí `null` , když není nalezena požadovaná položka. Vzhledem k tomu, že `T?` nelze deklarovat návratový typ, `MaybeNull` přidejte anotaci do metody Return:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Předchozí kód informuje volající, že kontrakt implikuje typ, který nemůže mít hodnotu null, ale vrácená hodnota *může* být null.  Použijte atribut, pokud by vaše rozhraní API mělo být typu, který nemůže mít hodnotu null, obvykle parametr obecného typu, ale mohou nastat `null` instance, kde by bylo vráceno. `MaybeNull`

Můžete také určit, že návratová hodnota nebo `out` argument nebo `ref` nemá hodnotu null, přestože typ je typ s možnou hodnotou null. Vezměte v úvahu metodu, která zajistí, že je pole dostatečně velké pro udržení počtu prvků. Pokud vstupní argument nemá kapacitu, rutina přidělí nové pole a zkopíruje do něj všechny existující prvky. Pokud je `null`vstupním argumentem, rutina přidělí nové úložiště. Pokud existuje dostatečná kapacita, rutina neprovede nic:

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

Po povolení typů odkazů s hodnotou null Chcete zajistit, aby předchozí kód byl zkompilován bez upozornění. Když metoda vrátí hodnotu, `storage` argument by neměl mít hodnotu null. Je však přijatelné volat `EnsureCapacity` s odkazem s hodnotou null. Můžete vytvořit `storage` typ odkazu s možnou hodnotou null a `NotNull` přidat podmínku post-Condition do deklarace parametru:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

Předchozí kód jednoznačně vyjadřuje stávající kontrakt: Volající mohou předat proměnnou s `null` hodnotou, ale návratovou hodnotou je zaručeno, že nikdy nebude mít hodnotu null. Atribut je nejužitečnější pro `ref` argumenty `out` a, `null` které mohou být předány jako argument, ale u tohoto argumentu je zaručeno, že není null, pokud se metoda vrátí. `NotNull`

Nepodmíněné následné podmínky se zadává pomocí následujících atributů:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Návratová hodnota, která není null, může mít hodnotu null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Návratová hodnota s možnou hodnotou null nikdy nebude null.

## <a name="specify-conditional-post-conditions-notnullwhen-and-maybenullwhen"></a>Zadejte podmíněné podmínky odeslání: `NotNullWhen` a`MaybeNullWhen`

Pravděpodobně jste obeznámeni s `string` metodou. <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> Tato metoda vrátí `true` , když argument není null, a ne prázdný řetězec. Jedná se o podobu kontroly hodnoty null: Volající nemusí mít hodnotu null – Pokud se metoda vrátí `false`, zaškrtnete argument. Chcete-li vytvořit metodu, jako je tato vlastnost s možnou hodnotou null, nastavte argument na typ s možnou hodnotou null a přidejte `NotNullWhen` atribut:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

To informuje kompilátor, že jakýkoliv kód, ve kterém není `false` vrácená hodnota, nesmí být zkontrolován hodnotou null. Přidání atributu informuje o statické analýze kompilátoru, která `IsNullOrEmpty` provede nezbytnou kontrolu null: když se vrátí `false`, vstupní argument `null`není.

```csharp
string? userInput = GetUserInput();
if (!(string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> Metoda bude opatřena poznámkami, jak je uvedeno výše pro .NET Core 3,0. Můžete mít podobné metody v základu kódu, které kontrolují stav objektů pro hodnoty null. Kompilátor nerozpozná vlastní metody kontroly null a bude nutné poznámky přidat sami. Když přidáte atribut, statická analýza kompilátoru zná, když byla testovaná proměnná vrácena na hodnotu null.

Jiné použití pro tyto atributy je `Try*` vzor. Následné podmínky pro `ref` proměnné a `out` jsou přenášeny prostřednictvím návratové hodnoty. Zvažte tuto metodu popsanou výše:

```csharp
bool TryGetMessage(string key, out string message)
```

Předchozí metoda dodržuje typické rozhraní .NET idiom: vrácená hodnota označuje, zda `message` byla nastavena na nalezenou hodnotu, nebo pokud není nalezena žádná zpráva, na výchozí hodnotu. Pokud metoda vrátí `true` `message` hodnotu, hodnota není null; v opačném případě je metoda nastavena `message` na hodnotu null.

Pomocí `NotNullWhen` atributu můžete komunikovat s tímto idiom. Když aktualizujete podpis pro typy odkazů s možnou hodnotou `message` null `string?` , udělejte a přidejte atribut:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

V předchozím příkladu `message` je hodnota při `TryGetMessage` návratu `true`známa, že není null. Stejné metody v základu kódu byste měli opatřit poznámkami stejným způsobem: argumenty mohou být `null`a při návratu `true`metody se označují jako nenulové.

Je možné, že budete potřebovat i jeden konečný atribut. V některých případech je nulový stav návratové hodnoty závislý na nulovém stavu jednoho nebo více vstupních argumentů. Tyto metody vrátí hodnotu, která není null vždy, když některé vstupní argumenty `null`nejsou. Chcete-li tyto metody správně opatřit poznámkami, `NotNullIfNotNull` použijte atribut. Vezměte v úvahu následující metodu:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Pokud argument není null, výstup není `null`. `url` Jakmile jsou povoleny odkazy s hodnotou null, tento podpis funguje správně, pokud rozhraní API nikdy nepřijímá vstup s hodnotou null. Pokud ale může mít vstup hodnotu null, může být návratová hodnota také null. Proto můžete změnit signaturu na následující kód:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

To funguje i v případě, že bude často vynutit, aby `null` volající implementovali další kontroly. Kontraktem je, že návratová hodnota by `null` byla pouze v případě, `url` že `null`je vstupní argument. Pro vyjádření této smlouvy byste si tuto metodu měli opatřit poznámkami, jak je znázorněno v následujícím kódu:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

U návratové hodnoty a argumentu byly oba poznámy s `?` označením, že by `null`mohlo být jedna z nich. Atribut dále upřesňuje, že návratová hodnota nebude mít hodnotu null, `url` Pokud argument `null`není.

Podmíněný následné podmínky můžete zadat pomocí těchto atributů:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Pokud vrácená hodnota splňuje podmínku `ref` , může být hodnota null neboargumentunull.`out`
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Pokud vrácená hodnota `ref` splňuje podmínku, nemůže být hodnota null neboargumentunull.`out`
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Návratová hodnota není null, pokud vstupní argument pro zadaný parametr není null.

## <a name="generic-definitions-and-nullability"></a>Obecné definice a možnost použití hodnoty null

Správně komunikující stav null obecných typů a obecné metody vyžadují zvláštní péči. To je fakt, že typ hodnoty s možnou hodnotou null a typ odkazu s možnou hodnotou null jsou zásadním rozdílem. Je synonymum pro `Nullable<int>`, zatímco `string?` je `string` atributem přidaným kompilátorem. `int?` Výsledkem je, že kompilátor nemůže generovat správný `T?` kód bez vědomí, zda `T` je `class` nebo `struct`. 

To neznamená, že nemůžete použít typ s povolenou hodnotou null (buď typ hodnoty, nebo odkazový typ) jako argument typu pro uzavřený obecný typ. `List<string?>` A`List<int?>`jsouplatné instance .`List<T>` 

To znamená, že nemůžete použít `T?` v deklaraci obecné třídy nebo metody bez omezení. Například se nemění, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> aby vracel. `T?` Toto omezení můžete překonat přidáním `struct` omezení nebo. `class` U některého z těchto omezení kompilátor ví, jak generovat kód pro i `T`. `T?`

Můžete chtít omezit typy používané pro argument obecného typu, aby byly typy bez hodnoty null. To lze provést přidáním `notnull` omezení na tento argument typu. Při použití tohoto omezení nesmí argument type být typ s možnou hodnotou null.

## <a name="conclusions"></a>Závěry

Přidání typů odkazů s možnou hodnotou null poskytuje počáteční slovní přehled pro popis očekávání vašich rozhraní API pro `null`proměnné, které by mohly být. Další atributy poskytují bohatší slovník popisující stav null proměnných jako předpoklady a následné podmínky. Tyto atributy podrobněji popisují vaše očekávání a poskytují lepší prostředí pro vývojáře pomocí vašich rozhraní API.

Když aktualizujete knihovny pro kontext s možnou hodnotou null, přidejte tyto atributy, aby uživatelé vašich rozhraní API měli k správné využití. Tyto atributy vám pomůžou plně popsat stav hodnoty null vstupních argumentů a vrácených hodnot:

- [AllowNull má](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Vstupní argument, který nemůže mít hodnotu null, může mít hodnotu null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Návratová hodnota, která není null, může mít hodnotu null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Návratová hodnota s možnou hodnotou null nikdy nebude null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Pokud vrácená hodnota splňuje podmínku `ref` , může být hodnota null neboargumentunull.`out`
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Pokud vrácená hodnota `ref` splňuje podmínku, nemůže být hodnota null neboargumentunull.`out`
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Návratová hodnota není null, pokud vstupní argument pro zadaný parametr není null.
