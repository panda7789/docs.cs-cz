---
title: Odkazové typy s možnou hodnotou null
description: Tento článek poskytuje přehled typů odkazů s možnou hodnotou null přidaných v C# 8,0. Dozvíte se, jak funkce poskytuje zabezpečení proti výjimkám odkazů s hodnotou null pro nové a existující projekty.
ms.technology: csharp-null-safety
ms.date: 04/21/2020
ms.openlocfilehash: 6d068760805a21e41712a4f70735bef41ce2052f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446669"
---
# <a name="nullable-reference-types"></a>Odkazové typy s možnou hodnotou null

C# 8,0 zavádí **typy odkazů s možnou hodnotou null** a odkazy, které neumožňují **hodnotu null** , které umožňují provádět důležité příkazy týkající se vlastností proměnných referenčního typu:

- **Odkaz by neměl mít hodnotu null**. V případě, že proměnné nemají být null, kompilátor vynutila pravidla, která zajistí, aby bylo možné je bezpečně odkázat na tyto proměnné bez toho, aby nejprve kontrolovaly, zda není null:
  - Proměnná musí být inicializována na hodnotu, která není null.
  - Proměnné nemůže být nikdy přiřazena hodnota `null` .
- **Odkaz může mít hodnotu null**. Pokud proměnné mohou mít hodnotu null, kompilátor vynutil různá pravidla, aby bylo zajištěno, že jste správně kontrolovali odkaz s hodnotou null:
  - Proměnná se může odkázat pouze v případě, že kompilátor může zaručit, že hodnota není null.
  - Tyto proměnné mohou být inicializovány s výchozí `null` hodnotou a může být přiřazena hodnota `null` v jiném kódu.

Tato nová funkce poskytuje významné výhody pro zpracování referenčních proměnných v dřívějších verzích jazyka C#, kde nelze určit záměr návrhu z deklarace proměnné. Kompilátor neposkytl bezpečnost proti výjimkám odkazů s hodnotou null pro typy odkazů:

- **Odkaz může mít hodnotu null**. Kompilátor nevydá upozornění, je-li typ odkazu inicializován na hodnotu null nebo je později přiřazen k hodnotě null. Kompilátor vystaví upozornění, když jsou tyto proměnné předané bez kontrol hodnot null.
- **Předpokládá**se, že odkaz nebude null. Kompilátor nevydá žádná upozornění, pokud jsou odkazy na typy odkazů. Pokud je proměnná nastavena na výraz, který může mít hodnotu null, vyvolá kompilátor upozornění.

Tato upozornění jsou generována v době kompilace. Kompilátor nepřidá žádné kontroly null ani jiné konstruktory runtime v kontextu s možnou hodnotou null. V době běhu je odkaz s možnou hodnotou null a odkazem, který nepovoluje hodnotu null, ekvivalentní.

S přidáním odkazových typů s možnou hodnotou null můžete deklarovat svůj záměr zřetelněji. `null`Hodnota je správný způsob, jak vyjádřit, že proměnná neodkazuje na hodnotu. Tuto funkci nepoužívejte k odebrání všech `null` hodnot z kódu. Místo toho byste měli deklarovat svůj záměr kompilátoru a dalším vývojářům, kteří si přečtou váš kód. Tím, že deklarujete svůj záměr, kompilátor vás informuje při psaní kódu, který není v souladu s tímto záměrem.

**Typ odkazu s možnou hodnotou null** je zaznamenán pomocí stejné syntaxe jako [typy hodnot s možnou hodnotou null](language-reference/builtin-types/nullable-value-types.md): a `?` je připojen k typu proměnné. Například následující deklarace proměnné představuje proměnnou řetězce s možnou hodnotou null `name` :

```csharp
string? name;
```

Jakákoli proměnná, ve které `?` není připojen k názvu typu, je **odkazový typ, který nepovoluje hodnotu null**. Který zahrnuje všechny proměnné referenčního typu v existujícím kódu, když jste povolili tuto funkci.

Kompilátor používá statickou analýzu k určení, zda odkaz s možnou hodnotou null je znám jako jiný než null. Kompilátor vás upozorní, pokud zrušíte odkaz na odkaz s možnou hodnotou null, pokud může mít hodnotu null. Toto chování můžete přepsat pomocí [operátoru null-striktní](language-reference/operators/null-forgiving.md) `!` za názvem proměnné. Například pokud víte, že `name` proměnná není null, ale kompilátor vydá upozornění, můžete napsat následující kód pro přepsání analýzy kompilátoru:

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>Hodnota null typů

Jakýkoli typ odkazu může mít jednu ze čtyř *nullabilities*, která popisuje, kdy se generují upozornění:

- Nelze zadat *hodnotu null*: proměnné tohoto typu nemohou být přiřazeny hodnoty null. Proměnné tohoto typu nemusejí být před zrušením odkazu zkontrolovány hodnotou null.
- *Nullable*: proměnné tohoto typu mohou být přiřazeny hodnoty null. Přesměrování proměnných tohoto typu bez prvotní kontroly `null` způsobí upozornění.
- *Oblivious*: oblivious je stav pre-C # 8,0. Proměnné tohoto typu se dají odkázat nebo se jim přiřazují bez upozornění.
- *Neznámé*: neznámý je všeobecně pro parametry typu, kde omezení neříká kompilátoru, že typ musí mít *hodnotu null nebo nemůže* být *null*.

Hodnota null typu v deklaraci proměnné je řízena *kontextem s možnou hodnotou null* , ve kterém je proměnná deklarována.

## <a name="nullable-contexts"></a>Kontexty s možnou hodnotou null

Kontexty s možnou hodnotou null umožňují detailní kontrolu způsobu, jakým kompilátor interpretuje proměnné referenčního typu. **Kontext poznámky s možnou hodnotou null** pro daný řádek zdroje je buď povolen, nebo zakázán. Kompilátor pre-C # 8,0 si můžete představit jako zkompilování veškerého kódu v zakázaném kontextu s možnou hodnotou null: jakýkoli odkazový typ může mít hodnotu null. **Kontext upozornění s možnou hodnotou null** může být taky povolený nebo zakázaný. Kontext upozornění s možnou hodnotou null určuje upozornění vygenerovaná kompilátorem pomocí analýzy toku.

Kontext anotace s možnou hodnotou null a kontext s možnou hodnotou null lze nastavit pro projekt pomocí `Nullable` elementu v souboru *. csproj* . Tento prvek konfiguruje způsob, jakým kompilátor interpretuje hodnotu null typů a jaká upozornění jsou vygenerována. Platná nastavení jsou:

- `enable`: Kontext anotace s možnou hodnotou null je **povolen**. Výstražný kontext s možnou hodnotou null je **povolen**.
  - Proměnné typu odkazu, `string` například, nejsou null.  Jsou povolena všechna upozornění na možnost použití hodnoty null.
- `warnings`: Kontext anotace s možnou hodnotou null je **zakázán**. Výstražný kontext s možnou hodnotou null je **povolen**.
  - Proměnné typu odkazu jsou oblivious. Jsou povolena všechna upozornění na možnost použití hodnoty null.
- `annotations`: Kontext anotace s možnou hodnotou null je **povolen**. Výstražný kontext s možnou hodnotou null je **zakázán**.
  - Proměnné typu odkazu, například řetězec, nesmí být null. Všechna upozornění na možnost použití hodnoty null jsou zakázána.
- `disable`: Kontext anotace s možnou hodnotou null je **zakázán**. Výstražný kontext s možnou hodnotou null je **zakázán**.
  - Proměnné typu odkazu jsou oblivious, stejně jako dřívější verze jazyka C#. Všechna upozornění na možnost použití hodnoty null jsou zakázána.

**Příklad**:

```xml
<Nullable>enable</Nullable>
```

Můžete také použít direktivy pro nastavení stejných kontextů kdekoli v projektu:

- `#nullable enable`: Nastaví kontext anotace s možnou hodnotou null a kontext s možnou hodnotou null na **povoleno**.
- `#nullable disable`: Nastaví kontext anotace s možnou hodnotou null a kontext s možnou hodnotou null na **disabled**.
- `#nullable restore`: Obnoví kontext anotace s možnou hodnotou null a kontext s možnou hodnotou null na nastavení projektu.
- `#nullable disable warnings`: Nastavte výstražný kontext s možnou hodnotou null na **disabled**.
- `#nullable enable warnings`: Nastavte kontext varování s možnou hodnotou null na **Enabled**.
- `#nullable restore warnings`: Obnoví kontext upozornění s možnou hodnotou null na nastavení projektu.
- `#nullable disable annotations`: Nastavte kontext anotace s možnou hodnotou null na **disabled**.
- `#nullable enable annotations`: Nastavte kontext anotace s možnou hodnotou null na **Enabled**.
- `#nullable restore annotations`: Obnoví kontext upozornění poznámky na nastavení projektu.

Ve výchozím nastavení jsou anotace a kontexty s možnou hodnotou null **zakázané**, včetně nových projektů. To znamená, že váš stávající kód se zkompiluje beze změn a bez generování nových upozornění.

Tyto možnosti poskytují dvě různé strategie [Aktualizace existujícího základu kódu](nullable-migration-strategies.md) pro použití typů odkazů s možnou hodnotou null.

## <a name="nullable-annotation-context"></a>Kontext anotace s možnou hodnotou null

Kompilátor používá následující pravidla v neaktivním kontextu anotace s možnou hodnotou null:

- V zakázaném kontextu nemůžete deklarovat odkazy s možnou hodnotou null.
- Všem referenčním proměnným může být přiřazena hodnota null.
- Při zpětném odkazování na proměnnou typu odkazu se negenerují žádná upozornění.
- Operátor null-striktní se nedá použít v zakázaném kontextu.

Chování je stejné jako u předchozích verzí jazyka C#.

Kompilátor používá následující pravidla v povoleném kontextu anotace s možnou hodnotou null:

- Jakákoli proměnná typu odkazu je odkaz, který **nepovoluje hodnotu null**.
- Všechny odkazy, které neumožňují hodnotu null, lze bezpečně odkázat.
- Jakýkoli typ odkazu s možnou hodnotou null (zaznamenáno `?` po typu v deklaraci proměnné) může mít hodnotu null. Statická analýza určuje, zda je hodnota v případě, že je hodnota nenulová, známa jako jiná než null. V takovém případě vás kompilátor upozorní.
- Operátor null-striktní můžete použít k deklaraci, že odkaz s možnou hodnotou null není null.

V povoleném kontextu anotace s možnou hodnotou null `?` znak připojený k typu odkazu deklaruje **typ odkazu s možnou hodnotou null**. **Operátor null-striktní** `!` může být přidán k výrazu, který deklaruje, že výraz nemá hodnotu null.

## <a name="nullable-warning-context"></a>Výstražný kontext s možnou hodnotou null

Výstražný kontext s možnou hodnotou null je odlišný od kontextu anotace s možnou hodnotou null. Upozornění je možné povolit i v případě, že jsou nové poznámky zakázané. Kompilátor používá analýzu statického toku k určení **nulového stavu** jakéhokoli odkazu. Stav null není null nebo **může** **mít hodnotu null** , pokud není **zakázán** *kontext s možnou hodnotou* null. Pokud odkázali odkaz na odkaz, pokud kompilátor určil, že je **pravděpodobně null**, kompilátor vás na vás upozorní. Stav odkazu je **pravděpodobně null** , pokud kompilátor nemůže určit jednu ze dvou podmínek:

1. Proměnná byla jednoznačně přiřazena k hodnotě, která není null.
1. Proměnná nebo výraz byly zkontrolovány proti hodnotě null před odkazem na ni.

Kompilátor generuje upozornění při odkázání na proměnnou nebo výraz, který je **pravděpodobně null** v kontextu upozornění s možnou hodnotou null. Kromě toho kompilátor generuje upozornění, když je v povoleném kontextu anotace s možnou hodnotou null přiřazen nehodnotový typ odkazu, který je **pravděpodobně** null.

## <a name="attributes-describe-apis"></a>Atributy popisují rozhraní API

Přidáte do rozhraní API atributy, které poskytují kompilátor, další informace o tom, kdy argumenty nebo návratové hodnoty mohou nebo nemůžou být null. Další informace o těchto atributech najdete v našem článku v referenční příručce k jazykům, které se vztahují na [atributy s možnou hodnotou null](language-reference/attributes/nullable-analysis.md). Tyto atributy se přidávají do knihoven .NET přes aktuální a nadcházející vydání. Nejdřív se aktualizují nejčastěji používaná rozhraní API.

## <a name="see-also"></a>Viz také

- [Koncept specifikace typů odkazů s možnou hodnotou null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Kurz úvodu k odkazům s možnou hodnotou null](tutorials/nullable-reference-types.md)
- [Migrace existujícího základu kódu na odkazy s možnou hodnotou null](tutorials/upgrade-to-nullable-references.md)
- [-Nullable (možnost kompilátoru C#)](language-reference/compiler-options/nullable-compiler-option.md)
