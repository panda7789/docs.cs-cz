---
title: Aktualizace základu kódu pro použití typů odkazů s možnou hodnotou null
description: Vyberte si nejlepší strategii pro upgrade základu kódu pro použití typů odkazů s možnou hodnotou null.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 5909eb9ffe1f5398fc2eb74848b82f8fe9516548
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975331"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Aktualizace knihoven pro použití typů odkazů s možnou hodnotou null a sdělování pravidel s možnou hodnotou null volajícím

Přidání [odkazových typů s možnou hodnotou null](nullable-references.md) znamená, že můžete deklarovat `null` , zda je nebo není hodnota pro každou proměnnou povolena nebo očekávána. Kromě toho můžete použít několik `AllowNull`atributů:, `DisallowNull`, `MaybeNull`, `NotNull`, `NotNullWhen`, `MaybeNullWhen`a `NotNullIfNotNull` k úplnému popisu stavů null argumentů a vrácených hodnot. Poskytuje skvělé prostředí při psaní kódu. Zobrazí se upozornění, pokud může být proměnná bez hodnoty null nastavena na `null`. Zobrazí se upozornění, pokud u proměnné s možnou hodnotou null není zkontrolována hodnota null před tím, než ji zrušíte. Aktualizace knihoven může chvíli trvat, ale výnosy je. Další informace, které pro kompilátor poskytnete, *Pokud* je `null` hodnota povolená nebo zakázaná, budou se vám lépe zobrazovat uživatelé vašeho rozhraní API. Pojďme začít se známým příkladem. Představte si, že knihovna má následující rozhraní API k načtení řetězce prostředků:

```csharp
bool TryGetMessage(string key, out string message)
```

Předchozí příklad se řídí známým `Try*` vzorem v rozhraní .NET. Pro toto rozhraní API existují dva argumenty odkazů: `key` a `message` parametr. Toto rozhraní API má následující pravidla týkající se hodnoty null těchto argumentů:

- Volající by neměli předat `null` jako argument pro `key`.
- Volající mohou předat proměnnou, jejíž hodnota je `null` jako argument pro. `message`
- Pokud `TryGetMessage` metoda vrátí `true`hodnotu, hodnota `message` není null. Pokud je návratovou hodnotou `false,` hodnota `message` (a její stav null), má hodnotu null.

Pravidlo pro `key` může být zcela vyjádřeno typem proměnné: `key` typ odkazu, který neumožňuje hodnotu null. `message` Parametr je složitější. To umožňuje `null` jako argument, ale zaručuje, že po úspěšném dokončení tento `out` argument nemá hodnotu null. V těchto scénářích potřebujete podrobnější slovník, který popisuje očekávání.

Aktualizace knihovny pro odkazy s možnou hodnotou null vyžaduje více `?` než automatické automatických zadávání u některých proměnných a názvů typů. Předchozí příklad ukazuje, že je nutné projít vaše rozhraní API a vzít v úvahu vaše očekávání pro každý vstupní argument. Vezměte v úvahu záruky pro vrácenou hodnotu a jakékoli `out` argumenty `ref` nebo argumentů, které vrátí metoda. Potom tyto pravidla sdělí kompilátoru a kompilátor poskytne upozornění, pokud se volajícím tyto pravidla neřídí.

Tato práce trvá určitou dobu. Pojďme začít s strategiemi, které vaší knihovně nebo aplikaci zohledňují hodnoty null, zatímco se vyrovnávají další požadavky a dodávky. Uvidíte, jak vyrovnávat průběžný vývoj a povolit typy odkazů s možnou hodnotou null. Seznámíte se s problémy s definicemi obecného typu. Dozvíte se, jak použít atributy k popisu před a po jednotlivých podmínkách rozhraní API.

## <a name="choose-a-strategy-for-nullable-reference-types"></a>Zvolit strategii pro typy odkazů s možnou hodnotou null

První volbou je, že ve výchozím nastavení by se měly zapnout nebo vypnout typy odkazů s možnou hodnotou null. Máte dvě strategie:

- Povolte typy odkazů s možnou hodnotou null pro celý projekt a zakažte ho v kódu, který není připravený.
- Povolit pouze typy odkazů s možnou hodnotou null pro kód, který je opatřen poznámkou pro typy s možnou hodnotou null

První strategie funguje nejlépe při přidávání dalších funkcí do knihovny při jejich aktualizaci na typy odkazů s možnou hodnotou null. Veškerý nový vývoj má na paměti s možnou hodnotou null. Při aktualizaci existujícího kódu povolíte v těchto třídách typy odkazů s možnou hodnotou null.

Po této první strategii provedete následující:

1. Povolte typy odkazů s možnou hodnotou null pro celý projekt `<Nullable>enable</Nullable>` přidáním elementu do souborů *csproj* .
1. Přidejte `#nullable disable` direktivu pragma do každého zdrojového souboru v projektu.
1. Při práci na jednotlivých souborech odeberte direktivu pragma a vyřešte všechna upozornění.

Tato první strategie obsahuje více než více práce pro přidání direktivy pragma do každého souboru. Výhodou je, že každý nový soubor kódu přidaný do projektu bude mít povolenou hodnotu null. Jakékoli nové práce budou mít na paměti nabývat hodnoty null; je nutné aktualizovat pouze existující kód.

Druhá strategie funguje lépe, pokud je knihovna obecně stabilní a hlavní fokus vývoje je přijmout typy odkazů s možnou hodnotou null. Při přidávání poznámek k rozhraním API můžete zapnout typy odkazů s možnou hodnotou null. Až budete hotovi, povolte v celém projektu typy odkazů s možnou hodnotou null.

Po této druhé strategii provedete následující:

1. Přidejte `#nullable enable` direktivu pragma do souboru, pro který chcete nastavit nepovolenou hodnotu s podporou.
1. Vyřešte všechna upozornění.
1. Pokračujte v těchto prvních dvou krocích, dokud nebudete mít k celou knihovnu s podporou null.
1. Povolit typy s možnou hodnotou null pro celý projekt `<Nullable>enable</Nullable>` přidáním elementu do souborů *csproj* .
1. Odeberte `#nullable enable` direktivy pragma, protože už nejsou potřeba.

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

Bylo přidáno několik atributů pro vyjádření dalších informací o stavu hodnoty null proměnných. Veškerý kód, který jste napsali předtím, než C# 8 zavádí odkazy s možnou hodnotou null, byl *null oblivious* To znamená, že jakákoli proměnná typu odkazu může mít hodnotu null, ale kontroly hodnoty null nejsou požadovány. Jakmile kód bude *mít na paměti hodnotu s možnou hodnotou null*, změní se tato pravidla. Odkazové typy by nikdy neměly `null` být hodnotou a pro typy odkazů s možnou hodnotou `null` null musí být před zpětným odkazem zkontrolovány.

Pravidla pro vaše rozhraní API jsou pravděpodobně složitější, jak jste viděli ve scénáři `TryGetValue` rozhraní API. Mnohé z vašich rozhraní API mají složitější pravidla, kdy proměnné můžou nebo nemůžou `null`být. V těchto případech použijete atributy k vyjádření těchto pravidel. Atributy, které popisují sémantiku vašeho rozhraní API, najdete v článku o [atributech, které mají vliv na analýzu s možnou hodnotou null](./language-reference/attributes/nullable-analysis.md).

## <a name="generic-definitions-and-nullability"></a>Obecné definice a možnost použití hodnoty null

Správně komunikující stav null obecných typů a obecné metody vyžadují zvláštní péči. To je fakt, že typ hodnoty s možnou hodnotou null a typ odkazu s možnou hodnotou null jsou zásadním rozdílem. `int?` Je synonymum pro `Nullable<int>`, zatímco `string?` je `string` atributem přidaným kompilátorem. Výsledkem je, že kompilátor nemůže generovat správný `T?` kód bez vědomí, zda `T` je `class` nebo. `struct`

To neznamená, že nemůžete použít typ s povolenou hodnotou null (buď typ hodnoty, nebo odkazový typ) jako argument typu pro uzavřený obecný typ. `List<string?>` A `List<int?>` jsou platné instance `List<T>`.

To znamená, že nemůžete použít `T?` v deklaraci obecné třídy nebo metody bez omezení. Například se nemění, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> aby vracel. `T?` Toto omezení můžete překonat přidáním omezení `struct` nebo. `class` U některého z těchto omezení kompilátor ví, jak generovat kód pro i `T` `T?`.

Můžete chtít omezit typy používané pro argument obecného typu, aby byly typy bez hodnoty null. To lze provést přidáním `notnull` omezení na tento argument typu. Při použití tohoto omezení nesmí argument type být typ s možnou hodnotou null.

## <a name="late-initialized-properties-data-transfer-objects-and-nullability"></a>Opožděné inicializace vlastností, Přenos dat objektů a možnosti použití hodnoty null

Vzhledem k tomu, že hodnota null vlastností, které jsou zpožděně inicializovány, což znamená, že je nastavena po konstrukci, může vyžadovat zvláštní pozornost, aby vaše třída nadále správně nevyjádřila původní záměr návrhu.

Typy, které obsahují zpožděné vlastnosti, jako je například Přenos dat objektů (DTO), jsou často vytvořeny pomocí externí knihovny, jako je například ORM databáze (objektová relační Mapovač), deserializátor nebo některá jiná komponenta, která automaticky vyplní vlastnosti z jiného zdroje.

Před povolením typů odkazů s možnou hodnotou null, které představují studenta, zvažte následující třídu DTO:

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string VehicleRegistration { get; set; }
}
```

Záměr návrhu (uvedený v tomto `Required` případě atributem) naznačuje, že v tomto systému jsou vlastnosti `FirstName` a `LastName` **povinné**, a proto není null.

`VehicleRegistration` Vlastnost není **povinná**, takže může mít hodnotu null.

Pokud povolíte typy odkazů s možnou hodnotou null, chcete určit, které vlastnosti mohou být s možnou hodnotou null, v souladu s původním záměrem:

```csharp
class Student
{
    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

Pro tento DTO je ``VehicleRegistration``jedinou vlastností, která může být null.

Kompilátor však vyvolává `CS8618` upozornění pro `FirstName` a `LastName`, což značí, že vlastnosti, které neumožňují hodnotu null, nejsou inicializovány.

Existují tři možnosti, které jsou k dispozici pro vyřešení upozornění kompilátoru způsobem, který zachovává původní záměr. Kterákoli z těchto možností je platná. měli byste zvolit ten, který nejlépe vyhovuje vašemu stylu kódování a požadavkům na návrh.

### <a name="initialize-in-the-constructor"></a>Inicializovat v konstruktoru

Ideální způsob, jak vyřešit neinicializovaná upozornění, je inicializovat vlastnosti v konstruktoru:

```csharp
class Student
{
    public Student(string firstName, string lastName)
    {
        FirstName = firstName;
        LastName = lastName;
    }

    [Required]
    public string FirstName { get; set; }

    [Required]
    public string LastName { get; set; }

    public string? VehicleRegistration { get; set; }
}
```

Tento přístup funguje pouze v případě, že knihovna, kterou použijete k vytvoření instance třídy, podporuje předávání parametrů v konstruktoru.

Kromě toho knihovna může podporovat předávání *některých* vlastností v konstruktoru, ale ne všechny.
Například EF Core podporuje [vazbu konstruktoru](/ef/core/modeling/constructors) pro normální vlastnosti sloupce, ale ne navigační vlastnosti.

Podívejte se na dokumentaci knihovny, která vytváří instanci vaší třídy, abyste pochopili rozsah, ve kterém podporuje vazby konstruktoru.

### <a name="property-with-nullable-backing-field"></a>Vlastnost s polem, které je k hodnotou null

Pokud vazba konstruktoru nebude pro vás fungovat, jedním ze způsobů, jak se tomuto problému vypořádat, je mít vlastnost nepovolující hodnotu null s polem, které je k dispozici s možnou hodnotou null:

```csharp
private string? _firstName;

[Required]
public string FirstName
{
    set => _firstName = value;
    get => _firstName
           ?? throw new InvalidOperationException("Uninitialized " + nameof(FirstName))
}
```

V tomto scénáři, pokud je `FirstName` vlastnost k dispozici před inicializací, kód vyvolá výjimku `InvalidOperationException`, protože kontrakt rozhraní API byl nesprávně použit.

Při použití zálohovaných polí byste měli zvážit, že některé knihovny můžou mít zvláštní předpoklady. EF Core například může být nutné nakonfigurovat pro správné použití polí pro [zálohování](/ef/core/modeling/backing-field) .

### <a name="initialize-the-property-to-null"></a>Inicializovat vlastnost na hodnotu null

Jako terser alternativa k použití pole, které je null, nebo v případě, že knihovna, která vytváří instanci vaší třídy, není kompatibilní s tímto přístupem, můžete jednoduše inicializovat `null` vlastnost přímo s použitím operátoru null-striktní (`!`):

```csharp
[Required]
public string FirstName { get; set; } = null!;

[Required]
public string LastName { get; set; } = null!;

public string? VehicleRegistration { get; set; }
```

Nebudete nikdy sledovat skutečnou hodnotu null za běhu s výjimkou důsledků programátorské chyby, a to tak, že přístup k vlastnosti před jejich správnou inicializací.

## <a name="see-also"></a>Viz také

- [Migrace existujícího základu kódu na odkazy s možnou hodnotou null](tutorials/upgrade-to-nullable-references.md)
- [Práce s typy odkazů s možnou hodnotou null v EF Core](/ef/core/miscellaneous/nullable-reference-types)
