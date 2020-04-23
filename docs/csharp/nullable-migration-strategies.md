---
title: Aktualizace základu kódu pro použití typů odkazů s možnou hodnotou null
description: Zvolte nejlepší strategii pro upgrade základu kódu pro použití typů odkazů s možnou hodnotou null.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: b4a10863aea5c47b47c2a017afb20786b1e67528
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103525"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Aktualizace knihoven za účelem použití typů odkazů s možnou hodnotou null a komunikace pravidel s možnou hodnotou null volajícím

Přidání [typů odkazů s možnou hodnotou](nullable-references.md) null `null` znamená, že můžete deklarovat, zda je hodnota povolena nebo očekávána pro každou proměnnou. Kromě toho `AllowNull`můžete použít řadu atributů: `DisallowNull` `MaybeNull`, `NotNull` `NotNullWhen`, `MaybeNullWhen`, `NotNullIfNotNull` , a zcela popsat nulové stavy argumentů a vrácených hodnot. To poskytuje skvělé zkušenosti při psaní kódu. Upozornění se vám objeví, pokud může být `null`proměnná s možnou hodnotou null nastavena na hodnotu . Upozornění, pokud proměnná s možnou hodnotou null není před dereferenced. Aktualizace knihoven může nějakou dobu trvat, ale odměny stojí za to. Čím více informací, které poskytnete `null` kompilátoru o *tom, kdy* je hodnota povolena nebo zakázána, tím lepší upozornění uživatelé vašeho rozhraní API získají. Začněme se známým příkladem. Představte si, že vaše knihovna má následující rozhraní API pro načtení řetězce prostředků:

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

## <a name="choose-a-strategy-for-nullable-reference-types"></a>Zvolte strategii pro typy odkazů s možnou hodnotou null.

První volbou je, zda null typy odkazů by měly být zapnuty nebo vypnuty ve výchozím nastavení. Máte dvě strategie:

- Povolte typy odkazů s možnou hodnotou null pro celý projekt a zakažte je v kódu, který není připraven.
- Povolit pouze typy odkazů s možnou hodnotou null pro kód, který byl anotován pro typy odkazů s možnou hodnotou null.

První strategie funguje nejlépe, když přidáváte další funkce do knihovny při aktualizaci pro typy odkazů s možnou hodnotou null. Všechny nové vývoj je null,,,,,,,,,,,,,,,,,,,,, Při aktualizaci existujícího kódu povolíte v těchto třídách typy odkazů s možnou hodnotou null.

Po této první strategii postupujte takto:

1. Povolte typy odkazů s možnou `<Nullable>enable</Nullable>` hodnotou null pro celý projekt přidáním prvku do souborů *csproj.*
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

Pravidla pro vaše rozhraní API jsou pravděpodobně složitější, `TryGetValue` jak jste viděli u scénáře rozhraní API. Mnoho vašich api mají složitější pravidla pro proměnné může `null`nebo nemůže být . V těchto případech budete používat atributy k vyjádření těchto pravidel. Atributy, které popisují sémantiku rozhraní API, najdete v článku [o atributy, které mají vliv na analýzu, kterou lze udatnou hodnotu](./language-reference/attributes/nullable-analysis.md).

## <a name="generic-definitions-and-nullability"></a>Obecné definice a nullability

Správná komunikace nulového stavu obecných typů a obecných metod vyžaduje zvláštní péči. To vyplývá ze skutečnosti, že typ hodnoty s možnou hodnotou s hodnotou null a typ odkazu s možnou hodnotou s možnou hodnotou null se zásadně liší. Synonymum `int?` pro `Nullable<int>`, `string?` vzhledem k tomu, že je `string` s atributem přidaným kompilátorem. Výsledkem je, že kompilátor nemůže `T?` generovat správný `T` kód, aniž by věděl, zda je `class` nebo `struct`.

To neznamená, že nelze použít typ s hodnotou null (typ hodnoty nebo typ odkazu) jako argument typu pro uzavřený obecný typ. Oba `List<string?>` `List<int?>` a jsou platné instance `List<T>`.

Co to znamená, že nelze `T?` použít v deklaraci obecné třídy nebo metody bez omezení. Například <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> nebude změněn na návrat `T?`. Toto omezení můžete překonat `struct` přidáním omezení nebo. `class` S některou z těchto omezení kompilátor ví, `T` `T?`jak generovat kód pro oba a .

Můžete chtít omezit typy používané pro obecný typ argumentu, které mají být nenulové typy. Můžete to udělat přidáním `notnull` omezení pro tento argument typu. When that constraint is applied, the type argument must not be a nullable type.
