---
title: Odkazové typy s možnou hodnotou null
description: Tento článek obsahuje přehled typů odkazů s možnou hodnotou null, které byly přidány v c# 8.0. Dozvíte se, jak funkce poskytuje bezpečnost proti výjimky nulové odkaz pro nové a existující projekty.
ms.technology: csharp-null-safety
ms.date: 02/19/2019
ms.openlocfilehash: bb4c2b6951a38eeb705c7de50ef5d9645350e336
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399425"
---
# <a name="nullable-reference-types"></a>Odkazové typy s možnou hodnotou null

C# 8.0 zavádí **typy odkazů s možnou hodnotou null** a typy odkazů s **hodnotou neobsahující hodnotu null,** které umožňují provádět důležitá prohlášení o vlastnostech proměnných typu odkazu:

- **Odkaz nemá být null**. Pokud proměnné nemají být null, kompilátor vynucuje pravidla, která zajistí, že je bezpečné zrušit odkaz na tyto proměnné bez předchozí kontroly, že není null:
  - Proměnná musí být inicializována na hodnotu nenulové.
  - Proměnné nelze nikdy přiřadit `null`hodnotu .
- **Odkaz může být null**. Pokud proměnné může být null, kompilátor vynucuje různá pravidla, aby zajistily, že jste správně zkontrolovat pro odkaz null:
  - Proměnná může být odkazována pouze v případě, že kompilátor může zaručit, že hodnota není null.
  - Tyto proměnné mohou být inicializovány s `null` výchozí `null` hodnotou a mohou být přiřazeny hodnotu v jiném kódu.

Tato nová funkce poskytuje významné výhody oproti zpracování referenčních proměnných v dřívějších verzích jazyka C#, kde záměr návrhu nelze určit z deklarace proměnné. Kompilátor neposkytl bezpečnost proti výjimkám nulového odkazu pro typy odkazů:

- **Odkaz může být null**. Při inicializování typu odkazu na hodnotu null nebo null je mu později přiřazeno žádné upozornění.
- **Odkaz se předpokládá, že není null**. Kompilátor nevydává žádná upozornění, když jsou odkazovány typy odkazů. (S odkazy s možnou hodnotou null kompilátor vydá upozornění vždy, když dereference proměnnou, která může být null).

S přidáním typů odkazů s možnou hodnotou null můžete deklarovat svůj záměr jasněji. Hodnota `null` je správný způsob, jak reprezentovat, že proměnná neodkazuje na hodnotu. Nepoužívejte tuto funkci k `null` odebrání všech hodnot z kódu. Spíše byste měli deklarovat svůj záměr kompilátoru a dalším vývojářům, kteří čtou váš kód. Deklarováním záměru vás kompilátor informuje při psaní kódu, který není konzistentní s tímto záměrem.

**Typ odkazu s možnou hodnotou null** je zaznamenán pomocí stejné syntaxe jako typy hodnot s [možnou hodnotou null](language-reference/builtin-types/nullable-value-types.md): a `?` je připojen k typu proměnné. Například následující deklarace proměnné představuje proměnnou `name`řetězce s možnou hodnotou null:

```csharp
string? name;
```

Každá proměnná, `?` kde není připojen k názvu typu, je **typ odkazu s možnou hodnotou null**. To zahrnuje všechny proměnné typu odkazu v existujícím kódu, pokud jste tuto funkci povolili.

Kompilátor používá statickou analýzu k určení, pokud je známo, že odkaz s možnou hodnotou null není null. Kompilátor vás upozorní, pokud zrušíte odkaz na odkaz s možnou hodnotou null, pokud může být null. Toto chování můžete přepsat pomocí `!` [operátoru null-forgiving](language-reference/operators/null-forgiving.md) za názvem proměnné. Například pokud víte, `name` že proměnná není null, ale kompilátor vydá upozornění, můžete napsat následující kód přepsat analýzu kompilátoru:

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>Nullability typů

Libovolný typ odkazu může mít jednu ze čtyř *hodnot nullabilities*, která popisuje při generování upozornění:

- *Neplatné*: Null nelze přiřadit proměnné tohoto typu. Proměnné tohoto typu není nutné zkontrolovat null před dereferencing.
- *Null:* Null lze přiřadit proměnné tohoto typu. Odstranění odkazování proměnných tohoto typu bez `null` předchozí kontroly způsobí upozornění.
- *Nevšímavý*: Toto je stav před c# 8.0. Proměnné tohoto typu mohou být odkazované nebo přiřazeny bez upozornění.
- *Neznámý*: Toto je obecně pro parametry typu, kde omezení neříkají kompilátoru, že typ musí být *nullable* nebo *nenullable*.

Nullability typu v deklaraci proměnné je řízen *a nullable kontextu,* ve kterém je deklarována proměnná.

## <a name="nullable-contexts"></a>Kontexty s možnou hodnotou Null

Kontexty s hodnotou Null umožňují jemně odstupňovaný ovládací prvek pro způsob, jakým kompilátor interpretuje proměnné typu odkazu. **Kontext poznámky s možnou hodnotou null** pro daný zdrojový řádek je povolen nebo zakázán. Kompilátor před c# 8.0 si můžete myslet jako kompilaci veškerého kódu v zakázaném kontextu s možnou hodnotou null: libovolný typ odkazu může mít hodnotu null. **Kontext upozornění s možnou hodnotou null** může být také povolen nebo zakázán. Kontext upozornění s možnou hodnotou null určuje upozornění generovaná kompilátorem pomocí jeho analýzy toku.

Kontext poznámky s možnou hodnotou null a kontext upozornění, který lze použít pro projekt pomocí `Nullable` prvku v souboru *.csproj.* Tento prvek konfiguruje, jak kompilátor interpretuje nullability typů a jaká upozornění jsou generována. Platná nastavení jsou:

- `enable`: Kontext poznámky s možnou hodnotou null je **povolen**. Kontext upozornění s možnou hodnotou null je **povolen**.
  - Proměnné typu odkazu, `string` například, jsou nenulové.  Všechna upozornění na zrušení jsou povolena.
- `warnings`: Kontext poznámky s možnou hodnotou null je **zakázán**. Kontext upozornění s možnou hodnotou null je **povolen**.
  - Proměnné referenčního typu jsou nevšímavé. Všechna upozornění na zrušení jsou povolena.
- `annotations`: Kontext poznámky s možnou hodnotou null je **povolen**. Kontext upozornění s možnou hodnotou null je **zakázán**.
  - Proměnné typu odkazu, například řetězec, jsou nenulové. Všechna upozornění na zrušení platnosti jsou zakázána.
- `disable`: Kontext poznámky s možnou hodnotou null je **zakázán**. Kontext upozornění s možnou hodnotou null je **zakázán**.
  - Proměnné typu odkazu jsou nevšímavé, stejně jako předchozí verze jazyka C#. Všechna upozornění na zrušení platnosti jsou zakázána.

**Příklad**:

```xml
<Nullable>enable</Nullable>
```

Direktivy můžete také použít k nastavení stejných kontextů kdekoli v projektu:

- `#nullable enable`: Nastaví kontext poznámky s možnou hodnotou null a kontext upozornění, kterou lze zrušit, na **povolenou hodnotu**.
- `#nullable disable`: Nastaví kontext poznámky s možnou hodnotou null a kontext upozornění, kterou lze zrušit, na **hodnotu zakázáno**.
- `#nullable restore`: Obnoví kontext poznámky s možnou hodnotou null a kontext upozornění, kterou lze uznat s hod.
- `#nullable disable warnings`: Nastavte kontext upozornění s možnou hodnotou null na **hodnotu zakázáno**.
- `#nullable enable warnings`: Nastavte kontext upozornění s možnou hodnotou null na **povolenou hodnotu**.
- `#nullable restore warnings`: Obnoví kontext upozornění s možnou hodnotou null do nastavení projektu.
- `#nullable disable annotations`: Nastavte kontext poznámky s možnou hodnotou null na **hodnotu zakázáno**.
- `#nullable enable annotations`: Nastavte kontext poznámky s možnou hodnotou null na **povolenou hodnotu**.
- `#nullable restore annotations`: Obnoví kontext upozornění na kontext poznámky do nastavení projektu.

Ve výchozím nastavení jsou kontexty poznámk y s možnou hodnotou null a upozornění **zakázány**. To znamená, že váš existující kód se zkompiluje beze změn a bez generování nových upozornění.

## <a name="nullable-annotation-context"></a>Kontext poznámky s možnou hodnotou null

Kompilátor používá následující pravidla v kontextu anotace s možnou hodnotou null:

- V zakázaném kontextu nelze deklarovat odkazy s možnou hodnotou null.
- Všem referenčním proměnným může být přiřazena hodnota null.
- Při dereferencování proměnné typu odkazu nejsou generována žádná upozornění.
- Operátor odpouštějící null nelze použít v zakázaném kontextu.

Chování je stejné jako předchozí verze jazyka C#.

Kompilátor používá následující pravidla v povoleném kontextu poznámky s možnou hodnotou null:

- Jakákoli proměnná typu odkazu je odkaz, který **lze neutírovat hodnotu null**.
- Všechny odkazy, které nelze zrušit, mohou být bezpečně odkazovány.
- Jakýkoli typ odkazu s `?` možnou hodnotou null (poznamenal po typu v deklaraci proměnné) může být null. Statická analýza určuje, zda je hodnota známo, že není null, když je odkazována. Pokud ne, kompilátor vás upozorní.
- Operátor null-forgiving můžete použít k prohlášení, že odkaz s možnou hodnotou null není null.

V povoleném kontextu poznámky s `?` možnou hodnotou null znak připojený k typu odkazu deklaruje **typ odkazu s možnou hodnotou null**. `!` **Operátor null odpouštějící** může být připojen k výrazu deklarovat, že výraz není null.

## <a name="nullable-warning-context"></a>Kontext upozornění s možnou hodnotou Null

Kontext upozornění s možnou hodnotou null se liší od kontextu poznámky s možnou hodnotou null. Upozornění lze povolit i v případě, že jsou zakázány nové poznámky. Kompilátor používá statickou analýzu toku k určení **nulového stavu** libovolného odkazu. Stav null není **null** nebo **možná null,** pokud není **zakázán**kontext upozornění s *možnou hodnotou null* . Pokud zrušíte odkaz, když kompilátor zjistí, že je **možná null**, kompilátor vás upozorní. Stav odkazu je **možná null,** pokud kompilátor může určit jednu ze dvou podmínek:

1. Proměnná byla jednoznačně přiřazena k hodnotě nenulové hodnoty.
1. Proměnná nebo výraz byl zkontrolován proti null před de-referencing to.

Kompilátor generuje upozornění vždy, když dereference proměnné nebo výraz ve stavu **možná null,** když je povolen kontext upozornění s možnou hodnotou null. Kromě toho jsou generována upozornění, když je proměnná nebo výraz **možná null** přiřazen k neplatnému typu odkazu v povoleném kontextu poznámky s možnou hodnotou null.

## <a name="see-also"></a>Viz také

- [Návrh specifikace referenčních typů s možnou hodnotou null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [Úvodní kurz odkazů s nulovou hodnotou](tutorials/nullable-reference-types.md)
- [Migrace existujícího základu kódu na odkazy s hodnotou null](tutorials/upgrade-to-nullable-references.md)
