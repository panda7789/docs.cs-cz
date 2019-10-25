---
title: Odkazové typy s možnou hodnotou null
description: Tento článek poskytuje přehled typů odkazů s možnou hodnotou null přidaných v C# 8,0. Dozvíte se, jak funkce poskytuje zabezpečení proti výjimkám odkazů s hodnotou null pro nové a existující projekty.
ms.date: 02/19/2019
ms.openlocfilehash: 2c2148b3ae50ce6c00e523390ea02686d9106b8b
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846763"
---
# <a name="nullable-reference-types"></a>Odkazové typy s možnou hodnotou null

C#8,0 zavádí **typy odkazů s možnou hodnotou null** a typy odkazů, které neumožňují **hodnotu null** , které umožňují provádět důležité příkazy týkající se vlastností proměnných referenčního typu:

- **Odkaz by neměl mít hodnotu null**. V případě, že proměnné nemají být null, kompilátor vynutila pravidla, která zajistí, že je možné je bezpečně odkázat na tyto proměnné bez toho, aby nejprve kontrolovaly, zda není null:
  - Proměnná musí být inicializována na hodnotu, která není null.
  - Proměnné nemůže být nikdy přiřazena hodnota `null`.
- **Odkaz může mít hodnotu null**. Pokud proměnné mohou mít hodnotu null, kompilátor vynutil různá pravidla, aby bylo zajištěno, že jste správně kontrolovali odkaz s hodnotou null:
  - Proměnná se může odkázat pouze v případě, že kompilátor může zaručit, že hodnota není null.
  - Tyto proměnné mohou být inicializovány s výchozí hodnotou `null` a může být přiřazena hodnota `null` v jiném kódu.

Tato nová funkce poskytuje významné výhody pro zpracování referenčních proměnných v dřívějších verzích, C# kde nelze určit záměr návrhu z deklarace proměnné. Kompilátor neposkytl bezpečnost proti výjimkám odkazů s hodnotou null pro typy odkazů:

- **Odkaz může mít hodnotu null**. Nejsou vydávána žádná upozornění, pokud je typ odkazu inicializován na hodnotu null nebo je později přiřazen k hodnotě null.
- **Předpokládá**se, že odkaz nebude null. Kompilátor nevydá žádná upozornění, pokud jsou odkazy na typy odkazů. (S odkazy s možnou hodnotou null vyvolá kompilátor upozornění vždy, když zrušíte odkaz na proměnnou, která může být null).

S přidáním odkazových typů s možnou hodnotou null můžete deklarovat svůj záměr zřetelněji. Hodnota `null` představuje správný způsob, jak vyjádřit, že proměnná neodkazuje na hodnotu. Tuto funkci nepoužívejte k odebrání všech hodnot `null` z kódu. Místo toho byste měli deklarovat svůj záměr kompilátoru a dalším vývojářům, kteří si přečtou váš kód. Tím, že deklarujete svůj záměr, kompilátor vás informuje při psaní kódu, který není v souladu s tímto záměrem.

**Typ odkazu s možnou hodnotou null** je zaznamenán pomocí stejné syntaxe jako [typy hodnot s možnou hodnotou null](programming-guide/nullable-types/index.md): `?` je připojen k typu proměnné. Například následující deklarace proměnné představuje řetězcovou proměnnou s možnou hodnotou null `name`:

```csharp
string? name;
```

Jakákoli proměnná, kde `?` není připojená k názvu typu, je **odkazový typ, který nepovoluje hodnotu null**. Který zahrnuje všechny proměnné referenčního typu v existujícím kódu, když jste povolili tuto funkci.

Kompilátor používá statickou analýzu k určení, zda odkaz s možnou hodnotou null je znám jako jiný než null. Kompilátor vás upozorní, pokud zrušíte odkaz na odkaz s možnou hodnotou null, pokud může mít hodnotu null. Toto chování můžete přepsat pomocí [operátoru null-striktní](language-reference/operators/null-forgiving.md) `!` za názvem proměnné. Pokud například víte, že proměnná `name` není null, ale kompilátor vydá upozornění, můžete napsat následující kód pro přepsání analýzy kompilátoru:

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>Hodnota null typů

Jakýkoli typ odkazu může mít jednu ze čtyř *nullabilities*, která popisuje, kdy se generují upozornění:

- Nelze zadat *hodnotu null*: proměnné tohoto typu nemohou být přiřazeny hodnoty null. Proměnné tohoto typu nemusejí být před zrušením odkazu zkontrolovány hodnotou null.
- *Nullable*: proměnné tohoto typu mohou být přiřazeny hodnoty null. Přesměrování proměnných tohoto typu bez prvotní kontroly `null` způsobí upozornění.
- *Oblivious*: Jedná se o stavC# 8,0. Proměnné tohoto typu se dají odkázat nebo se jim přiřazují bez upozornění.
- *Neznámé*: to je všeobecně u parametrů typu, kde omezení neříká kompilátoru, že typ musí mít *hodnotu null nebo nemůže* být *null*.

Hodnota null typu v deklaraci proměnné je řízena *kontextem s možnou hodnotou null* , ve kterém je proměnná deklarována.

## <a name="nullable-contexts"></a>Kontexty s možnou hodnotou null

Kontexty s možnou hodnotou null umožňují detailní kontrolu způsobu, jakým kompilátor interpretuje proměnné referenčního typu. **Kontext poznámky s možnou hodnotou null** pro daný řádek zdroje je buď povolen, nebo zakázán. Můžete si představit kompilátor předC# 8,0, protože kompilujete veškerý kód v zakázaném kontextu s možnou hodnotou null: jakýkoli odkazový typ může mít hodnotu null. **Kontext upozornění s možnou hodnotou null** může být taky povolený nebo zakázaný. Kontext upozornění s možnou hodnotou null určuje upozornění vygenerovaná kompilátorem pomocí analýzy toku.

Kontext anotace s možnou hodnotou null a kontext s možnou hodnotou null lze nastavit pro projekt pomocí elementu `Nullable` v souboru *. csproj* . Tento prvek konfiguruje způsob, jakým kompilátor interpretuje hodnotu null typů a jaká upozornění jsou vygenerována. Platná nastavení jsou:

- `enable`: kontext anotace s možnou hodnotou null je **povolen**. Výstražný kontext s možnou hodnotou null je **povolen**.
  - Proměnné typu odkazu, `string` například nemohou mít hodnotu null.  Jsou povolena všechna upozornění na možnost použití hodnoty null.
- `warnings`: kontext anotace s možnou hodnotou null je **zakázán**. Výstražný kontext s možnou hodnotou null je **povolen**.
  - Proměnné typu odkazu jsou oblivious. Jsou povolena všechna upozornění na možnost použití hodnoty null.
- `annotations`: kontext anotace s možnou hodnotou null je **povolen**. Výstražný kontext s možnou hodnotou null je **zakázán**.
  - Proměnné typu odkazu, například řetězec, nesmí být null. Všechna upozornění na možnost použití hodnoty null jsou zakázána.
- `disable`: kontext anotace s možnou hodnotou null je **zakázán**. Výstražný kontext s možnou hodnotou null je **zakázán**.
  - Proměnné typu odkazu jsou oblivious, stejně jako starší verze C#. Všechna upozornění na možnost použití hodnoty null jsou zakázána.

Můžete také použít direktivy pro nastavení stejných kontextů kdekoli v projektu:

- `#nullable enable`: nastavuje kontext anotace s možnou hodnotou null a kontext s možnou hodnotou null na **povolenou**.
- `#nullable disable`: nastavuje kontext anotace s možnou hodnotou null a kontext s možnou hodnotou null na **disabled**.
- `#nullable restore`: obnoví kontext anotace s možnou hodnotou null a kontext s možnou hodnotou null na nastavení projektu.
- `#nullable disable warnings`: nastavte výstražný kontext s možnou hodnotou null na **disabled**.
- `#nullable enable warnings`: nastavte kontext varování s možnou hodnotou null na **povoleno**.
- `#nullable restore warnings`: obnoví kontext upozornění s možnou hodnotou null na nastavení projektu.
- `#nullable disable annotations`: nastavte kontext anotace s možnou hodnotou null na **disabled**.
- `#nullable enable annotations`: nastavte kontext anotace s možnou hodnotou null na **Enabled**.
- `#nullable restore annotations`: obnoví kontext upozornění poznámky na nastavení projektu.

Ve výchozím nastavení jsou poznámky s možnou hodnotou null a kontexty upozornění **zakázané**. To znamená, že váš stávající kód se zkompiluje beze změn a bez generování nových upozornění.

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
- Jakýkoli typ odkazu s možnou hodnotou null (popsaný `?` po typu v deklaraci proměnné) může mít hodnotu null. Statická analýza určuje, zda je hodnota při odkazování na hodnotu nenulová. V takovém případě vás kompilátor upozorní.
- Operátor null-striktní můžete použít k deklaraci, že odkaz s možnou hodnotou null není null.

V povoleném kontextu anotace s možnou hodnotou null je znak `?` připojený k typu odkazu deklaruje **typ odkazu s možnou hodnotou null**. **Operátor null-striktní** `!` lze připojit k výrazu, který deklaruje, že výraz nemá hodnotu null.

## <a name="nullable-warning-context"></a>Výstražný kontext s možnou hodnotou null

Výstražný kontext s možnou hodnotou null je odlišný od kontextu anotace s možnou hodnotou null. Upozornění je možné povolit i v případě, že jsou nové poznámky zakázané. Kompilátor používá analýzu statického toku k určení **nulového stavu** jakéhokoli odkazu. Stav null není null nebo **může** **mít hodnotu null** , pokud není **zakázán** *kontext s možnou hodnotou* null. Pokud odkázali odkaz na odkaz, pokud kompilátor určil, že je **pravděpodobně null**, kompilátor vás na vás upozorní. Stav odkazu je **pravděpodobně null** , pokud kompilátor nemůže určit jednu ze dvou podmínek:

1. Proměnná byla jednoznačně přiřazena k hodnotě, která není null.
1. Proměnná nebo výraz byly zkontrolovány proti hodnotě null před odkazem na ni.

Kompilátor generuje upozornění pokaždé, když zrušíte odkaz na proměnnou nebo výraz v možném stavu s možnou hodnotou **null** , pokud je povolený kontext upozornění na hodnotu null. Kromě toho se generují upozornění, když je **pravděpodobně null** proměnná nebo výraz přiřazen k neprázdnému typu odkazu v povoleném kontextu s možnou hodnotou null.

## <a name="see-also"></a>Viz také:

- [Koncept specifikace typů odkazů s možnou hodnotou null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Kurz úvodu k odkazům s možnou hodnotou null](tutorials/nullable-reference-types.md)
- [Migrace existujícího základu kódu na odkazy s možnou hodnotou null](tutorials/upgrade-to-nullable-references.md)
