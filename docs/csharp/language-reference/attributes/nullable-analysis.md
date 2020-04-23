---
title: 'C# Vyhrazené atributy: Statická analýza s možnou hodnotou Null'
ms.date: 04/14/2020
description: Tyto atributy jsou interpretovány kompilátorem poskytnout lepší statickou analýzu pro nullable a nenulelné typy odkazů.
ms.openlocfilehash: 33521133a6a01196e6e1ab9c3cdc191a24f1ecf3
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102707"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a>Vyhrazené atributy přispívají ke statické analýze nulového stavu kompilátoru.

V kontextu s možnou hodnotou null kompilátor provádí statickou analýzu kódu k určení stavu null všech proměnných typu odkazu:

- *not null*: Statická analýza zjistila, že proměnná je přiřazena k nenulové hodnotě.
- *možná null*: Statická analýza nemůže určit, že proměnné je přiřazena hodnota bez hodnoty null.

Můžete použít několik atributů, které poskytují informace kompilátoru o sémantiku vašich api. Tyto informace pomáhají kompilátoru provádět statickou analýzu a určit, kdy proměnná není null. Tento článek obsahuje stručný popis každého z těchto atributů a jak je používat. Všechny příklady předpokládají C# 8.0 nebo novější a kód je v kontextu s možnou hodnotou null.

Začněme se známým příkladem. Představte si, že vaše knihovna má následující rozhraní API pro načtení řetězce prostředků:

```csharp
bool TryGetMessage(string key, out string message)
```

Předchozí příklad následuje známý `Try*` vzor v rozhraní .NET. Existují dva referenční argumenty pro `key` toto `message` rozhraní API: a parametr. Toto rozhraní API má následující pravidla týkající se nullness těchto argumentů:

- Volající by neměli `null` projít jako `key`argument pro .
- Volající mohou předat proměnnou, `null` jejíž `message`hodnota je jako argument pro .
- Pokud `TryGetMessage` metoda `true`vrátí , `message` hodnota není null. Pokud je `false,` vrácená hodnota `message` hodnota (a její stav null) je null.

Pravidlo pro `key` může být vyjádřeno typem proměnné: `key` by měl být typ odkazu s možnou hodnotou null. Parametr `message` je složitější. Umožňuje `null` jako argument, ale zaručuje, že na `out` úspěch, že argument není null. Pro tyto scénáře potřebujete bohatší slovní zásobu k popisu očekávání.

Několik atributů byly přidány vyjádřit další informace o stavu null proměnných. Veškerý kód, který jste napsali před c# 8 představil null reference typy byl *null nevšímavý*. To znamená, že všechny proměnné typu odkazu může být null, ale null kontroly nejsou vyžadovány. Jakmile váš kód je *null,,,* tato pravidla změnit. Referenční typy by `null` nikdy měla být hodnota a nullable `null` typy odkazů musí být zkontrolovány proti před tím, než je odkazováno.

Pravidla pro vaše rozhraní API jsou pravděpodobně složitější, `TryGetValue` jak jste viděli u scénáře rozhraní API. Mnoho vašich api mají složitější pravidla pro proměnné může `null`nebo nemůže být . V těchto případech použijete k vyjádření těchto pravidel jeden z následujících atributů:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Vstupní argument, který nelze upustit, může mít hodnotu null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Vrácená hodnota, jejíž nenulovatelná hodnota může být null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Vrácená hodnota s možnou hodnotou null nikdy nebude null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Vstupní argument, který nelze utnou, `bool` může mít hodnotu null, pokud metoda vrátí zadanou hodnotu.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Vstupní argument s možnou hodnotou null `bool` nebude null, pokud metoda vrátí zadanou hodnotu.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Vrácená hodnota není null, pokud argument pro zadaný parametr není null.
- [DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Metoda nikdy vrátí. Jinými slovy vždy vyvolá výjimku.
- [DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): Tato metoda nikdy `bool` vrátí, pokud přidružený parametr má zadanou hodnotu.

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

Kontrast, který se `DisallowNull`scénáře pro použití : Tento atribut slouží k určení, že `null`vstupní proměnná typu odkazu s možnou hodnotou null by neměla být . Zvažte vlastnost, kde `null` je výchozí hodnota, ale klienti ji mohou nastavit pouze na hodnotu, která není null. Uvažujte následující kód:

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

V kontextu s možnou hodnotou `ReviewComment` `get` null může `null`přistupující odkaz vrátit výchozí hodnotu aplikace . Kompilátor varuje, že musí být kontrolovány před přístupem. Kromě toho varuje volající, že i když `null`by to mohlo být , `null`volající by nemělexplicitně nastavit na . Atribut `DisallowNull` také určuje *předběžnou podmínku*, nemá `get` vliv na přistupující ho. Atribut se `DisallowNull` používá, když sledujete tyto charakteristiky o:

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

Z důvodů uvedených v [obecných definicích a nullability](../../nullable-migration-strategies.md#generic-definitions-and-nullability) tato technika nefunguje s obecnými metodami. Můžete mít obecnou metodu, která následuje podobný vzor:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Nelze určit, že vrácená `T?`hodnota je . Metoda vrátí, `null` když není nalezena požadovaná položka. Vzhledem k tomu, `T?` že nelze deklarovat návratový typ, přidáte poznámku `MaybeNull` k metodě return:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Předchozí kód informuje volající, že smlouva znamená typ s nulou, ale vrácená hodnota *může* být ve skutečnosti null.  Použijte `MaybeNull` atribut, pokud by vaše rozhraní API mělo být typu s nulovým hodnotou, `null` obvykle parametr obecného typu, ale mohou existovat instance, kde by měl být vrácen.

Můžete také určit, že vrácená hodnota nebo `out` nebo `ref` argument není null, i když typ je typ odkazu s možnou hodnotou null. Zvažte metodu, která zajišťuje, že pole je dostatečně velké pro uložení několika prvků. Pokud vstupní argument nemá kapacitu, rutina by přidělit nové pole a zkopírovat všechny existující prvky do něj. Pokud je `null`vstupní argument , rutina by přidělit nové úložiště. Pokud je dostatečná kapacita, rutina nedělá nic:

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

Předchozí kód vyjadřuje existující smlouvy jasně: Volající můžete předat `null` proměnnou s hodnotou, ale vrácená hodnota je zaručeno, že nikdy být null. Atribut `NotNull` je nejužitečnější pro `ref` a `out` argumenty, kde `null` mohou být předány jako argument, ale tento argument je zaručeno, že není null, když metoda vrátí.

Můžete zadat bezpodmínečné postconditions pomocí následujících atributů:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Vrácená hodnota, jejíž nenulovatelná hodnota může být null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Vrácená hodnota s možnou hodnotou null nikdy nebude null.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Určete podmíněné `NotNullWhen`post-podmínky: , `MaybeNullWhen`a`NotNullIfNotNull`

Pravděpodobně jste obeznámeni `string` s <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>metodou . Tato metoda `true` vrátí, pokud je argument null nebo prázdný řetězec. Je to forma null-check: Volající nemusí null-zkontrolovat argument, pokud metoda `false`vrátí . Chcete-li metodu, jako je tato nullable aware, byste nastavit argument `NotNullWhen` na typ odkazu s hodnotou null a přidat atribut:

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

## <a name="verify-unreachable-code"></a>Ověření nedostupného kódu

Některé metody, obvykle pomocné shody nebo jiné metody nástroje, vždy ukončit vyvoláním výjimky. Nebo pomocník může vyvolat výjimku na základě hodnoty logického argumentu.

V prvním případě můžete přidat `DoesNotReturn` atribut do deklarace metody. Kompilátor vám pomůže třemi způsoby. Nejprve kompilátor vydá upozornění, pokud existuje cesta, kde může být metoda ukončena bez vyvolání výjimky. Za druhé, kompilátor označí jakýkoli kód po volání této `catch` metody jako *nedostupný*, dokud není zjištěna příslušná klauzule. Za třetí, nedostupný kód nebude mít vliv na žádné stavy null. Zvažte tuto metodu:

```csharp
[DoesNotReturn]
private void FailFast()
{
   throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   if (!isInitialized)
      FailFast();

   // unreachable code:
   this.field = containedField;
}
```

V druhém případě přidáte `DoesNotReturnIf` atribut do logického parametru metody. Předchozí příklad můžete upravit následujícím způsobem:

```csharp
private void FailFast([DoesNotReturnIf(false)]bool isValid)
{
   if (!isValid)
       throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   FailFast(isInitialized);

   // unreachable code when "isInitialized" is false:
   this.field = containedField;
}
```

## <a name="summary"></a>Souhrn

Přidání typů odkazů s možnou hodnotou null poskytuje počáteční slovní `null`zásobu k popisu očekávání api pro proměnné, které by mohly být . Další atributy poskytují bohatší slovní zásobu k popisu stavu null proměnných jako předpoklady a postconditions. Tyto atributy jasněji popisují vaše očekávání a poskytují lepší prostředí pro vývojáře, kteří používají vaše rozhraní API.

Při aktualizaci knihoven pro kontext s možnou hodnotou null přidejte tyto atributy, které uživatele vašich api navedou ke správnému použití. Tyto atributy vám pomohou plně popsat stav null vstupních argumentů a vrácených hodnot:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Vstupní argument, který nelze upustit, může mít hodnotu null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Vstupní argument s možnou hodnotou null by nikdy neměl mít hodnotu null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Vrácená hodnota, jejíž nenulovatelná hodnota může být null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Vrácená hodnota s možnou hodnotou null nikdy nebude null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Vstupní argument, který nelze utnou, `bool` může mít hodnotu null, pokud metoda vrátí zadanou hodnotu.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Vstupní argument s možnou hodnotou null `bool` nebude null, pokud metoda vrátí zadanou hodnotu.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Vrácená hodnota není null, pokud vstupní argument pro zadaný parametr není null.
- [DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Metoda nikdy vrátí. Jinými slovy vždy vyvolá výjimku.
- [DoesNotReturnIf](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute): Tato metoda nikdy `bool` vrátí, pokud přidružený parametr má zadanou hodnotu.
