---
title: Typy s možnou hodnotou Null odkazů
description: Tento článek obsahuje přehled typů s povolenou hodnotou Null odkaz, přidá C# 8. Dozvíte se, jak tato funkce poskytuje zabezpečení proti výjimky odkaz s hodnotou null pro nové i stávající projekty.
ms.date: 02/19/2019
ms.openlocfilehash: f08e000edc29ed76c6539c27db005182396bfb5a
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56443163"
---
# <a name="nullable-reference-types"></a>Typy s možnou hodnotou Null odkazů

C#8.0 představuje **typy s možnou hodnotou Null odkazů** a **typy neumožňující hodnotu odkazu** , díky kterým můžete provádět příkazy důležité informace o vlastnostech pro proměnné typu odkazu:

- **Odkaz by neměl být null**. Pokud proměnné nejsou by měl mít hodnotu null, kompilátor vynucuje pravidla, která zajistí je bezpečné pokouší dereferencovat tyto proměnné, aniž byste nejdřív kontroluje se, že není null:
  - Proměnná musí být inicializován na hodnotu než null.
  - Proměnná může být nikdy přiřazena hodnota `null`.
- **Odkaz může mít hodnotu null**. Pokud proměnné může mít hodnotu null, vynucuje kompilátor různá pravidla k zajištění, že jste správně zkontrolovali pro odkaz s hodnotou null:
  - Proměnná může pouze lze přistoupit přes ukazatel po kompilátor může zaručit, že hodnota není null.
  - Tyto proměnné může být inicializovány s výchozím `null` hodnotu a může být přiřazena hodnota `null` v jiném kódu.

Tato nová funkce nabízí významné výhody přes zpracování referenčních proměnných v dřívějších verzích C# kde jsou záměr návrhu nelze z deklarace proměnné. Kompilátor neposkytli zabezpečení proti výjimky odkaz s hodnotou null pro typy odkazů:

- **Odkaz může mít hodnotu null**. Žádná upozornění jsou vydávány, pokud typ odkazu je inicializován na hodnotu null nebo později přiřazené na hodnotu null.
- **Odkaz se předpokládá, že nesmí být null**. Kompilátor nebude vydat upozornění při typy odkazů jsou přistoupit přes ukazatel. (S možnou hodnotou Null odkazy, kompilátor vyvolá upozornění pokaždé, když se přistoupit přes ukazatel proměnné, která může mít hodnotu null).

Přidání typy s možnou hodnotou Null odkazů můžete deklarovat máte v úmyslu jasněji. `null` Hodnota je správný způsob, jak reprezentaci, že proměnné neodkazuje na hodnotu. Nepoužívejte tuto funkci odebrat všechny `null` hodnoty z vašeho kódu. Místo toho by měla deklarovat vaším záměrem kompilátoru a jinými vývojáři, které čtou váš kód. Deklarací vaším záměrem, kompilátor vás informuje při psaní kódu, který je konzistentní s tohoto záměru.

A **typ s možnou hodnotou Null odkazu** je třeba poznamenat, pomocí stejné syntaxe jako [typy s možnou hodnotou](programming-guide/nullable-types/index.md): `?` se připojí k typu proměnné. Například následující deklaraci proměnné představuje proměnnou s s povolenou hodnotou Null řetězcem `name`:

```csharp
string? name;
```

Jakákoli proměnná kde `?` není připojen na typ je název **Null odkazový typ**. Když povolíte tuto funkci zahrnující všechny proměnné referenčního typu v existujícím kódu.

Kompilátor používá statickou analýzu k určení, zda se ví, že s možnou hodnotou Null odkaz hodnotu Null. Kompilátor vás upozorní, pokud je přístup přes ukazatel odkazu s možnou hodnotou Null při může mít hodnotu null. Toto chování můžete přepsat pomocí **striktní null operátor** (`!`) za název proměnné. Například, pokud víte, `name` proměnná není null, ale kompilátor vyvolá upozornění, můžete napsat následující kód k přepsání kompilátoru analýzy:

```csharp
name!.Length;
```

Si můžete přečíst podrobnosti o tomto operátoru v [koncept typy s možnou hodnotou Null odkazů](https://github.com/dotnet/csharplang/blob/master/proposals/nullable-reference-types-specification.md#the-null-forgiving-operator) specifikace návrhu na Githubu.

## <a name="nullability-of-types"></a>Možnost použití hodnoty Null z typů

Jakéhokoliv odkazového typu může mít jednu ze čtyř *nullabilities*, která popisuje po vygenerování upozornění:

- *Nemá*: Proměnné tohoto typu nelze přiřadit hodnotu Null. Proměnné tohoto typu není potřeba před dereferencováním být zaškrtnuto hodnotu null.
- *S povolenou hodnotou Null*: Na proměnné tohoto typu lze přiřadit hodnotu Null. Zrušení reference proměnné tohoto typu bez první zjišťování `null` způsobí, že upozornění.
- *Oblivious*: Toto je předběžnéC# 8 stavu. Proměnné tohoto typu lze přistoupit přes ukazatel nebo přiřazené bez upozornění.
- *Neznámý*: Obvykle se jedná pro parametry typu kde omezení Nemluvte kompilátor, že typ musí být *s možnou hodnotou Null* nebo *nonnullable*.

Možnost použití hodnoty Null typu v deklaraci proměnné je řízen *s možnou hodnotou Null kontextu* ve kterém je proměnná deklarována.

## <a name="nullable-contexts"></a>Kontexty s možnou hodnotou Null

S povolenou hodnotou Null kontexty povolit citlivé ovládací prvky jak kompilátor interpretuje proměnné typu odkazu. **Kontextu s možnou hodnotou Null anotace** z libovolného zdroje daného řádku je `enabled` nebo `disabled`. Si můžete představit předběžnéC# 8 kompilátoru jako kompilaci kódu jazyka `disabled` s možnou hodnotou Null kontextu: Jakéhokoliv odkazového typu může mít hodnotu null. **Kontextu s možnou hodnotou Null upozornění** může být nastavená na `enabled`, `disabled`, nebo `safeonly`. Kontext upozornění s možnou hodnotou Null určuje upozornění generovaný kompilátorem pomocí jeho analýzy toku.

Kontextové poznámky s možnou hodnotou Null a s povolenou hodnotou Null kontext upozornění můžete nastavit pro projekt používá `NullableContextOptions` element v vaše `csproj` souboru. Tento element lze konfigurovat, jak kompilátor interpretuje Null typy a jaké upozornění. Platná nastavení jsou:

- `enable`: Kontext s možnou hodnotou Null poznámky je **povolené**. S povolenou hodnotou Null kontext upozornění je **povolené**.
  - Proměnné typu odkazu, `string` jsou null.  Všechna upozornění možnosti použití hodnoty Null jsou povolené.
- `disable`: Kontext s možnou hodnotou Null poznámky je **zakázané**. S povolenou hodnotou Null kontext upozornění je **zakázané**.
  - Proměnné typu odkazu jsou oblivious, stejně jako dřívější verze C#. Všechna upozornění možnosti použití hodnoty Null jsou zakázané.
- `safeonly`: Kontext s možnou hodnotou Null poznámky je **povolené**. S povolenou hodnotou Null kontext upozornění je **safeonly**.
  - Proměnné typu odkazu jsou nemá. Všechna upozornění zabezpečení možnosti použití hodnoty Null jsou povolené.
- `warnings`: Kontext s možnou hodnotou Null poznámky je **zakázané**. S povolenou hodnotou Null kontext upozornění je **povolené**.
  - Proměnné typu odkazu jsou oblivious. Všechna upozornění možnosti použití hodnoty Null jsou povolené.
- `safeonlywarnings`: Kontext s možnou hodnotou Null poznámky je **zakázané**. S povolenou hodnotou Null kontext upozornění je **safeonly**.
  - Proměnné typu odkazu jsou oblivious. Všechna upozornění zabezpečení možnosti použití hodnoty Null jsou povolené.

Direktivy také můžete nastavit tyto stejné kontexty kdekoli ve vašem projektu:

- `#nullable enable`: Nastaví kontext poznámky s možnou hodnotou Null a s povolenou hodnotou Null kontext upozornění **povolené**.
- `#nullable disable`: Nastaví kontext poznámky s možnou hodnotou Null a s povolenou hodnotou Null kontext upozornění **zakázané**.
- `#nullable safeonly`: Nastavit kontext s možnou hodnotou Null poznámky na **povolené**a kontext upozornění pro **safeonly**.
- `#nullable restore`: Obnoví nastavení projektu kontext poznámky s možnou hodnotou Null a s povolenou hodnotou Null kontext upozornění.
- `#pragma warning disable nullable`: Nastavit kontext s možnou hodnotou Null upozornění na **zakázané**.
- `#pragma warning enable nullable`: Nastavit kontext s možnou hodnotou Null upozornění na **povolené**.
- `#pragma warning restore nullable`: Obnoví nastavení projektu s možnou hodnotou Null kontext upozornění.
- `#pragma warning safeonly nullable`: Nastaví kontext s možnou hodnotou Null upozornění na **safeonly**.

Anotace s možnou hodnotou Null výchozí a kontext upozornění jsou `disabled`. Toto rozhodnutí znamená, že váš stávající kód zkompiluje bez změny a generování všechna nová upozornění.

Rozdíly mezi `enabled` a `safeonly` s možnou hodnotou Null kontexty upozornění jsou upozornění pro přiřazení s možnou hodnotou Null odkaz na odkaz Null. Následující přiřazení vygeneruje upozornění v `enabled` upozornění kontextu, ale ne `safeonly` kontext upozornění. Ale druhý řádek, kde `s` se přistoupit přes ukazatel, vygeneruje upozornění v `safeonly` kontextu:

```csharp
string s = null; // warning when nullable warning context is enabled.
var txt = s.ToString(); // warning when nullable warnings context is safeonly, or enabled.
```

### <a name="nullable-annotation-context"></a>Kontextové poznámky s možnou hodnotou Null

Kompilátor používá následující pravidla v kontextu zakázáno s možnou hodnotou NULL Poznámky:

- Nelze deklarovat s možnou hodnotou Null reference v kontextu zakázáno.
- Všechny referenční proměnné může být přiřazen na hodnotu null.
- Žádná varování jsou generovány při dereferenci proměnné typu odkazu.
- Operátor striktní null nelze použít v kontextu zakázáno.

Chování je stejné jako v předchozích verzích C#.

Kompilátor používá následující pravidla v kontextu povolené poznámky s možnou hodnotou NULL:

- Všechny proměnné typu odkazu je **Null reference**.
- Null odkaz může být dereferencována bezpečně.
- Libovolný typ s možnou hodnotou Null reference (označeny `?` po typu v deklaraci proměnné) může mít hodnotu null. Statické analýzy určuje, pokud je hodnota známé být jiná než null, pokud je přistoupit přes ukazatel. V opačném případě kompilátor vás upozorní.
- Chcete-li deklarovat, že odkaz s možnou hodnotou Null není null můžete použít operátor striktní hodnotu null.

V kontextu povolené poznámky s možnou hodnotou Null `?` znak připojenou k odkazový typ deklaruje **typ s možnou hodnotou Null odkazu**. **Null promíjení operátor** (`!`) mohou být připojeny na výraz, chcete-li deklarovat, že výraz není null.

## <a name="nullable-warning-context"></a>S povolenou hodnotou Null kontext upozornění

Kontext upozornění s možnou hodnotou Null se liší od kontextu poznámky s možnou hodnotou Null. Upozornění je možné povolit i v případě, že nové poznámky jsou zakázané. Kompilátor používá k určení tok statické analýzy **stav s hodnotou null** veškerých odkazů. Stavu null je buď **není null** nebo **možná hodnota null,** při *s možnou hodnotou Null kontext upozornění* není **zakázané**. Pokud že přestoupíte odkaz, když kompilátor zjistil má **možná hodnota null,**, kompilátor zobrazí upozornění. Stav odkazu je **možná hodnota null,** Pokud kompilátor můžete určit jednu z dvě podmínky:

1. Proměnná byla jednoznačně přiřazena na nenulovou hodnotu.
1. Proměnné nebo výrazu po kontrole s hodnotou null před zrušením odkazu.

Kompilátor vygeneruje upozornění při každém přístupu přes ukazatel proměnné nebo výrazu v **možná hodnota null,** stavu s možnou hodnotou Null v kontextu upozornění `enabled` nebo `safeonly`. Kromě toho se generují upozornění při **možná hodnota null,** proměnné nebo výrazu je přiřazený k typu odkazu nemá v kontextu s možnou hodnotou Null anotace `enabled`.

## <a name="learn-more"></a>Víc se uč

- [Specifikace konceptu s možnou hodnotou Null reference](https://github.com/dotnet/csharplang/blob/master/proposals/nullable-reference-types-specification.md)
- [Úvod do kurzu odkazy s možnou hodnotou Null](tutorials/nullable-reference-types.md)
- [Migrovat existující kódové základny odkazy s možnou hodnotou Null](tutorials/upgrade-to-nullable-references.md)
