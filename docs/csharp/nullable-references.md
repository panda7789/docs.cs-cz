---
title: Odkazové typy s možnou hodnotou null
description: Tento článek poskytuje přehled typů odkazů s možnou hodnotou null přidaných v C# 8. Dozvíte se, jak funkce poskytuje zabezpečení proti výjimkám odkazů s hodnotou null pro nové a existující projekty.
ms.date: 02/19/2019
ms.openlocfilehash: 7ca3ebc413fbe335f79d415249b952132c38f552
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214396"
---
# <a name="nullable-reference-types"></a>Odkazové typy s možnou hodnotou null

C#8,0 zavádí **typy odkazů s možnou hodnotou null** a typy odkazů, které neumožňují **hodnotu null** , které umožňují provádět důležité příkazy týkající se vlastností proměnných referenčního typu:

- **Odkaz by neměl mít hodnotu null**. V případě, že proměnné nemají být null, kompilátor vynutila pravidla, která zajistí, že je možné je bezpečně odkázat na tyto proměnné bez toho, aby nejprve kontrolovaly, zda není null:
  - Proměnná musí být inicializována na hodnotu, která není null.
  - Proměnné nemůže být nikdy přiřazena hodnota `null`.
- **Odkaz může mít hodnotu null**. Pokud proměnné mohou mít hodnotu null, kompilátor vynutil různá pravidla, aby bylo zajištěno, že jste správně kontrolovali odkaz s hodnotou null:
  - Proměnná se může odkázat pouze v případě, že kompilátor může zaručit, že hodnota není null.
  - Tyto proměnné mohou být inicializovány s výchozí `null` hodnotou a může být přiřazena hodnota `null` v jiném kódu.

Tato nová funkce poskytuje významné výhody pro zpracování referenčních proměnných v dřívějších verzích, C# kde nelze určit záměr návrhu z deklarace proměnné. Kompilátor neposkytl bezpečnost proti výjimkám odkazů s hodnotou null pro typy odkazů:

- **Odkaz může mít hodnotu null**. Nejsou vydávána žádná upozornění, pokud je typ odkazu inicializován na hodnotu null nebo je později přiřazen k hodnotě null.
- **Předpokládá**se, že odkaz nebude null. Kompilátor nevydá žádná upozornění, pokud jsou odkazy na typy odkazů. (S odkazy s možnou hodnotou null vyvolá kompilátor upozornění vždy, když zrušíte odkaz na proměnnou, která může být null).

S přidáním odkazových typů s možnou hodnotou null můžete deklarovat svůj záměr zřetelněji. `null` Hodnota je správný způsob, jak vyjádřit, že proměnná neodkazuje na hodnotu. Tuto funkci nepoužívejte k odebrání všech `null` hodnot z kódu. Místo toho byste měli deklarovat svůj záměr kompilátoru a dalším vývojářům, kteří si přečtou váš kód. Tím, že deklarujete svůj záměr, kompilátor vás informuje při psaní kódu, který není v souladu s tímto záměrem.

**Typ odkazu s možnou hodnotou null** je zaznamenán pomocí stejné syntaxe jako [typy hodnot s možnou hodnotou null](programming-guide/nullable-types/index.md): a `?` je připojen k typu proměnné. Například následující deklarace proměnné představuje proměnnou `name`řetězce s možnou hodnotou null:

```csharp
string? name;
```

Jakákoli proměnná, ve `?` které není připojen k názvu typu, je **odkazový typ, který nepovoluje hodnotu null**. Který zahrnuje všechny proměnné referenčního typu v existujícím kódu, když jste povolili tuto funkci.

Kompilátor používá statickou analýzu k určení, zda odkaz s možnou hodnotou null je znám jako jiný než null. Kompilátor vás upozorní, pokud zrušíte odkaz na odkaz s možnou hodnotou null, pokud může mít hodnotu null. Toto chování můžete přepsat pomocí **operátoru null-striktní** (`!`) za názvem proměnné. Například pokud víte, že `name` proměnná není null, ale kompilátor vydá upozornění, můžete napsat následující kód pro přepsání analýzy kompilátoru:

```csharp
name!.Length;
```

Podrobnosti o tomto operátoru si můžete přečíst v článku návrh specifikace [typů odkazů s možnou hodnotou null](../../_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) na GitHubu.

## <a name="nullability-of-types"></a>Hodnota null typů

Jakýkoli typ odkazu může mít jednu ze čtyř *nullabilities*, která popisuje, kdy se generují upozornění:

- Nemožnost *null*: Proměnné tohoto typu nelze přiřadit hodnotu null. Proměnné tohoto typu nemusejí být před zrušením odkazu zkontrolovány hodnotou null.
- *Nullable*: Proměnné tohoto typu mohou být přiřazeny hodnoty null. Přesměrování proměnných tohoto typu bez prvotní kontroly `null` způsobí upozornění.
- *Oblivious*: Toto je starší nežC# 8 stavů. Proměnné tohoto typu se dají odkázat nebo se jim přiřazují bez upozornění.
- *Neznámý*: To je všeobecně u parametrů typu, kde omezení neříká kompilátoru, že typ musí mít *hodnotu null nebo nemůže* být *null*.

Hodnota null typu v deklaraci proměnné je řízena *kontextem s možnou hodnotou null* , ve kterém je proměnná deklarována.

## <a name="nullable-contexts"></a>Kontexty s možnou hodnotou null

Kontexty s možnou hodnotou null umožňují detailní kontrolu způsobu, jakým kompilátor interpretuje proměnné referenčního typu. **Kontext poznámky s možnou hodnotou null** pro daný řádek `enabled` zdroje `disabled`je nebo. Představte si předC# 8 kompilátorem, když zkompilujete veškerý kód v kontextu `disabled` s možnou hodnotou null: Libovolný odkazový typ může mít hodnotu null. **Kontext upozornění s možnou hodnotou null** může `enabled` být `disabled`nastaven na nebo. Kontext upozornění s možnou hodnotou null určuje upozornění vygenerovaná kompilátorem pomocí analýzy toku.

Kontext anotace s možnou hodnotou null a kontext s možnou hodnotou null lze `Nullable` nastavit pro projekt `csproj` pomocí elementu v souboru. Tento prvek konfiguruje způsob, jakým kompilátor interpretuje hodnotu null typů a jaká upozornění jsou vygenerována. Platná nastavení jsou:

- `enable`: Kontext anotace s možnou hodnotou null je **povolen**. Výstražný kontext s možnou hodnotou null je **povolen**.
  - Proměnné typu odkazu, `string` například, nejsou null.  Jsou povolena všechna upozornění na možnost použití hodnoty null.
- `warnings`: Kontext anotace s možnou hodnotou null je **zakázán**. Výstražný kontext s možnou hodnotou null je **povolen**.
  - Proměnné typu odkazu jsou oblivious. Jsou povolena všechna upozornění na možnost použití hodnoty null.
- `annotations`: Kontext anotace s možnou hodnotou null je **povolen**. Výstražný kontext s možnou hodnotou null je **zakázán**.
  - Proměnné typu odkazu jsou oblivious. Jsou povolena všechna upozornění na možnost použití hodnoty null.
- `disable`: Kontext anotace s možnou hodnotou null je **zakázán**. Výstražný kontext s možnou hodnotou null je **zakázán**.
  - Proměnné typu odkazu jsou oblivious, stejně jako starší verze C#. Všechna upozornění na možnost použití hodnoty null jsou zakázána.

> [!IMPORTANT]
> Element se dřív jmenoval `NullableContextOptions`. `Nullable` Přejmenování se dodává se sadou Visual Studio 2019, 16,2-P1. Tato změna nemá .NET Core SDK 3.0.100-preview5-011568. Pokud používáte .NET Core CLI, budete ho muset použít `NullableContextOptions` , až bude k dispozici další verze Preview.

Můžete také použít direktivy pro nastavení stejných kontextů kdekoli v projektu:

- `#nullable enable`: Nastaví kontext anotace s možnou hodnotou null a kontext s možnou hodnotou null na **povoleno**.
- `#nullable disable`: Nastaví kontext poznámky s možnou hodnotou null a kontext s možnou hodnotou null na **disabled**.
- `#nullable restore`: Obnoví kontext anotace s možnou hodnotou null a kontext s možnou hodnotou null na nastavení projektu.
- `#pragma warning disable nullable`: Nastavte výstražný kontext s možnou hodnotou null na **disabled**.
- `#pragma warning enable nullable`: Nastavte výstražný kontext s možnou hodnotou null na **povoleno**.
- `#pragma warning restore nullable`: Obnoví kontext upozornění s možnou hodnotou null na nastavení projektu.

Výchozí anotace s možnou hodnotou null a `disabled`kontexty upozornění jsou. Toto rozhodnutí znamená, že váš stávající kód se zkompiluje beze změn a bez generování nových upozornění.

## <a name="nullable-annotation-context"></a>Kontext anotace s možnou hodnotou null

Kompilátor používá následující pravidla v neaktivním kontextu anotace s možnou hodnotou null:

- V zakázaném kontextu nemůžete deklarovat odkazy s možnou hodnotou null.
- Všem referenčním proměnným může být přiřazena hodnota null.
- Při zpětném odkazování na proměnnou typu odkazu se negenerují žádná upozornění.
- Operátor null-striktní se nedá použít v zakázaném kontextu.

Chování je stejné jako u předchozích verzí C#.

Kompilátor používá následující pravidla v povoleném kontextu anotace s možnou hodnotou null:

- Jakákoli proměnná typu odkazu je odkaz, který **nepovoluje hodnotu null**.
- Všechny odkazy, které neumožňují hodnotu null, lze bezpečně odkázat.
- Jakýkoli typ odkazu s `?` možnou hodnotou null (zaznamenáno po typu v deklaraci proměnné) může mít hodnotu null. Statická analýza určuje, zda je hodnota při odkazování na hodnotu nenulová. V takovém případě vás kompilátor upozorní.
- Operátor null-striktní můžete použít k deklaraci, že odkaz s možnou hodnotou null není null.

V povoleném kontextu `?` anotace s možnou hodnotou null znak připojený k typu odkazu deklaruje **typ odkazu s možnou hodnotou null**. **Operátor null forgiveness** (`!`) se může připojit k výrazu, který deklaruje, že výraz není null.

## <a name="nullable-warning-context"></a>Výstražný kontext s možnou hodnotou null

Výstražný kontext s možnou hodnotou null je odlišný od kontextu anotace s možnou hodnotou null. Upozornění je možné povolit i v případě, že jsou nové poznámky zakázané. Kompilátor používá analýzu statického toku k určení **nulového stavu** jakéhokoli odkazu. Stav null není null nebo **může** **mít hodnotu null** , pokud není **zakázán** *kontext s možnou hodnotou* null. Pokud odkázali odkaz na odkaz, pokud kompilátor určil, že je **pravděpodobně null**, kompilátor vás na vás upozorní. Stav odkazu je **pravděpodobně null** , pokud kompilátor nemůže určit jednu ze dvou podmínek:

1. Proměnná byla jednoznačně přiřazena k hodnotě, která není null.
1. Proměnná nebo výraz byly zkontrolovány proti hodnotě null před odkazem na ni.

Kompilátor generuje upozornění pokaždé, když zrušíte odkaz na proměnnou nebo výraz v možném stavu s možnou hodnotou **null** , `enabled`Pokud je kontext upozornění na hodnotu null. Kromě toho jsou generována upozornění, když je **pravděpodobně null** proměnná nebo výraz přiřazen k neprázdnému typu odkazu, když je `enabled`kontext poznámky s možnou hodnotou null.

## <a name="learn-more"></a>Víc se uč

- [Koncept referenční specifikace s možnou hodnotou null](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Kurz úvodu k odkazům s možnou hodnotou null](tutorials/nullable-reference-types.md)
- [Migrace existujícího základu kódu na odkazy s možnou hodnotou null](tutorials/upgrade-to-nullable-references.md)
