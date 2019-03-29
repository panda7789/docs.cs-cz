---
title: 'Explicitní pole: Val – klíčové slovo'
description: Další informace o F# klíčové slovo "val", které se používá k deklaraci umístění pro uložení hodnoty v typu třídy nebo struktury bez inicializace typu.
ms.date: 05/16/2016
ms.openlocfilehash: 6557514f13a9e86c7f367713775535db79e99a0c
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634008"
---
# <a name="explicit-fields-the-val-keyword"></a>Explicitní pole: Val – klíčové slovo

`val` – Klíčové slovo se používá k deklaraci umístění pro uložení hodnoty v typu třídy nebo struktury, bez jeho inicializaci. Umístění úložiště, které jsou deklarovány tímto způsobem se nazývají *explicitní pole*. Další používání `val` – klíčové slovo se používá současně se `member` – klíčové slovo Chcete-li deklarovat automaticky implementované vlastnosti. Další informace o automaticky implementovaných vlastností najdete v tématu [vlastnosti](properties.md).

## <a name="syntax"></a>Syntaxe

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a>Poznámky

Obvyklým způsobem k definování polí v typu třídy nebo struktury je použít `let` vazby. Ale `let` vazby musí být inicializované jako součást konstruktoru třídy, která není vždy možné, potřebná nebo žádoucí. Můžete použít `val` – klíčové slovo má pole, které není inicializován.

Explicitní pole může být statické nebo nestatické. *Modifikátor přístupu* může být `public`, `private`, nebo `internal`. Explicitní pole jsou ve výchozím nastavení veřejné. Tím se liší od `let` vazby ve třídách, které jsou vždycky privátní.

[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) atribut je požadován na explicitní pole v typy tříd, které mají primární konstruktor. Tento atribut určuje, že pole je inicializována na nulovou hodnotu. Typ pole musí podporovat inicializace nula. Typ podporuje inicializace nula, pokud jde o jeden z následujících akcí:

- Primitivní typ, který má hodnotu nula.

- Typ, který podporuje hodnotu null jako hodnotu Normální, neobvyklé hodnoty nebo jako reprezentace hodnoty. To zahrnuje třídy, řazených kolekcí členů, záznamy, funkce, rozhraní a referenční typy .NET, `unit` typ a typy rozlišených sjednocení.

- Typ hodnoty .NET.

- Struktura, jejíž všechna pole podporují výchozí nulovou hodnotu.

Například neměnné pole s názvem `someField` zkompiloval pomocným polem v rozhraní .NET reprezentaci s názvem `someField@`, a přístup k uložené hodnotě pomocí vlastnosti s názvem `someField`.

Proměnlivé pole je reprezentace .NET zkompilován pole .NET.

>[!WARNING]
>Obor názvů rozhraní .NET Framework `System.ComponentModel` obsahuje atribut, který má stejný název. Informace o tomto atributu naleznete v tématu `System.ComponentModel.DefaultValueAttribute`.

Následující kód ukazuje použití explicitní pole a pro porovnání, `let` vazby ve třídě, která má primární konstruktor. Všimněte si, že `let`-vázané pole `myInt1` je privátní. Když `let`-vázané pole `myInt1` se odkazuje z metody člen, identifikátoru samotného `this` se nevyžaduje. Když odkazujete na explicitní pole, ale `myInt2` a `myString`, identifikátoru samotného je povinný.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

Výstup je následující:

```
11 12 abc
30 def
```

Následující kód ukazuje použití explicitní pole ve třídě, která nemá primární konstruktor. V takovém případě `DefaultValue` atribut není povinný, ale musí se inicializovat všechna pole v konstruktorech, které jsou definovány pro typ.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

Výstup je `35 22`.

Následující kód ukazuje použití explicitní pole ve struktuře. Vzhledem k tomu, že struktura je hodnotový typ, má automaticky výchozí konstruktor, který nastaví hodnoty polí na nulu. Proto `DefaultValue` atribut se nevyžaduje.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

Výstup je `11 xyz`.

**Mějte na paměti,**, pokud se chystáte inicializace struktury s `mutable` pole bez `mutable` – klíčové slovo, přiřazení bude fungovat na kopii struktury, které budou okamžitě po přiřazení zahozeny. Proto nedojde ke změně struktury.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

Explicitní pole nejsou určené pro běžné použití. Obecně platí, pokud je to možné, abyste používali `let` vazby ve třídě místo explicitní pole. Explicitní pole jsou užitečné v některých případech interoperability, například když je třeba definovat strukturu, která se použije v vyvolání platformy volání nativního rozhraní API, nebo ve scénářích vzájemné spolupráce COM. Další informace najdete v tématu [externí funkce](../functions/external-functions.md). Další situace, ve kterém může být nutné explicitní pole je při práci s F# generátoru kódu, který generuje třídy bez primárního konstruktoru. Explicitní pole jsou také užitečné pro proměnné statická na úrovni vlákna nebo podobné konstrukce. Další informace naleznete v tématu `System.ThreadStaticAttribute`.

Když klíčová slova `member val` pohromadě v definici typu, je to definice automaticky implementované vlastnosti. Další informace najdete v tématu [vlastnosti](properties.md).

## <a name="see-also"></a>Viz také:

- [Vlastnosti](properties.md)
- [Členové](index.md)
- [`let` Vazby ve třídách](let-bindings-in-classes.md)
