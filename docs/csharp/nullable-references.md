---
title: Typy s možnou hodnotou Null odkazů
description: Tento článek obsahuje přehled typů s povolenou hodnotou Null odkaz, přidá C# 8. Dozvíte se, jak tato funkce poskytuje zabezpečení proti výjimky odkaz s hodnotou null pro nové i stávající projekty.
ms.date: 12/03/2018
ms.openlocfilehash: f18fc9dbce2f934b216b3eb0b80658fec6b44c46
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53156486"
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

## <a name="nullable-contexts"></a>Kontexty s možnou hodnotou Null

S povolenou hodnotou Null kontexty povolit citlivé ovládací prvky jak kompilátor interpretuje proměnné typu odkazu. S povolenou hodnotou Null kontext kterýkoli řádek v daného zdroje je `enabled` nebo `disabled`. Si můžete představit předběžnéC# 8 kompilátoru jako kompilaci kódu jazyka `disabled` s možnou hodnotou Null kontextu: Jakéhokoliv odkazového typu může mít hodnotu null. Upozornění se negenerují, pokud jsou přistoupit přes ukazatel proměnné typu odkazu.

Kontext s možnou hodnotou Null se provádí pomocí nové direktivy pragma:

- `#nullable enable` Nastaví kontext s možnou hodnotou Null povolena.
- `#nullable disable` Nastaví kontext s možnou hodnotou Null na hodnotu zakázáno.

Výchozí kontext s možnou hodnotou null je `disabled`. Toto rozhodnutí znamená, že váš stávající kód zkompiluje bez změny a generování všechna nová upozornění.

Kompilátor používá následující pravidla v rámci zakázáno s možnou hodnotou NULL:

- Nelze deklarovat s možnou hodnotou Null reference v kontextu zakázáno.
- Všechny referenční proměnné může být přiřazen na hodnotu null.
- Žádná varování jsou generovány při dereferenci proměnné typu odkazu.
- Operátor striktní null nelze použít v kontextu zakázáno.

Chování je stejné jako v předchozích verzích C#.

Kompilátor používá následující pravidla v kontextu povoleno s možnou hodnotou NULL:

- Všechny proměnné typu odkazu je **Null reference**.
- Null odkaz může být dereferencována bezpečně.
- Libovolný typ s možnou hodnotou Null reference (označeny `?` po typu v deklaraci proměnné) může mít hodnotu null. Statické analýzy určuje, pokud je hodnota známé být jiná než null, pokud je přistoupit přes ukazatel. V opačném případě kompilátor vás upozorní.
- Chcete-li deklarovat, že odkaz s možnou hodnotou Null není null můžete použít operátor striktní hodnotu null.

Bohatší gramatika je navržená pro kontext s možnou hodnotou Null a bude v budoucím verzím Preview k dispozici. Další informace o kontextu s možnou hodnotou Null, najdete v článku [specifikace odkazu s možnou hodnotou Null](https://github.com/dotnet/csharplang/blob/master/proposals/nullable-reference-types-specification.md#nullable-contexts) koncept.

## <a name="null-states-of-nullable-references"></a>Null stavy odkazů s možnou hodnotou Null

Kompilátor používá k určení statické analýzy **stav s hodnotou null** jakékoli odkazu s možnou hodnotou Null. Stavu null je buď **není null** nebo **možná hodnota null,**. Pokud že přestoupíte odkazu s možnou hodnotou Null při kompilátor zjistil má **možná hodnota null,**, kompilátor zobrazí upozornění. Stav odkazu s možnou hodnotou null je **možná hodnota null,** Pokud kompilátor můžete určit jednu z dvě podmínky:

1. Proměnná byla jednoznačně přiřazena na nenulovou hodnotu.
1. Proměnné s hodnotou null byl vrácen před zrušením odkazu.

Kompilátor vynucuje, aby Null odkazy mohou být nikdy nastaveno na hodnotu null. Je třeba je inicializovat na nenulovou hodnotu. Pokud to neuděláte, kompilátor vás upozorní, že Null reference nebyl inicializován. Kompilátor také vás upozorní, kdykoli přiřadit Null odkaz na odkaz s možnou hodnotou Null **může mít hodnotu null**. To znamená, že Null odkaz na odkaz s možnou hodnotou Null můžete přiřadit pouze, pokud je tento odkaz s možnou hodnotou Null **není null**.

## <a name="learn-more"></a>Víc se uč

- [Specifikace konceptu s možnou hodnotou Null reference](https://github.com/dotnet/csharplang/blob/master/proposals/nullable-reference-types-specification.md)
- [Úvod do kurzu odkazy s možnou hodnotou Null](tutorials/nullable-reference-types.md)
