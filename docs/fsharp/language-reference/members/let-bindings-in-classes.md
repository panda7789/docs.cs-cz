---
title: Vazby let ve třídách (F#)
description: 'Zjistěte, jak definovat privátní pole a soukromé funkce pro třídy F # s použitím "let" vazby v definici třídy.'
ms.date: 05/16/2016
ms.openlocfilehash: 237eb98a57571a21c9187abf31f05160374cf4fc
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033217"
---
# <a name="let-bindings-in-classes"></a>Vazby let ve třídách

Můžete definovat privátní pole a soukromé funkce pro třídy F # s použitím `let` vazby v definici třídy.

## <a name="syntax"></a>Syntaxe

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Poznámky

Předchozí syntaxi se zobrazí po deklarace záhlaví a dědičnost tříd, ale před všechny definice členů. Syntaxe je stejně jako u `let` vazby mimo třídy, ale názvy definované ve třídě mají obor, který je omezená na třídu. A `let` vazbou soukromé pole nebo funkce; ke zveřejňování dat nebo funkce deklarovat veřejně, vlastnost nebo metodu member.

A `let` vazby, která není statická nazývá instance `let` vazby. Instance `let` vazby spustí, když jsou vytvořeny objekty. Statické `let` vazby jsou součástí statický inicializátor pro třídu, která je zaručeno, že ke spuštění před první typ slouží.

Kód v rámci instance `let` vazby můžete použít parametry primárního konstruktoru.

Atributy a modifikátory dostupnosti nejsou u povolené `let` vazby ve třídách.

Následující příklady kódu znázorňují několik typů `let` vazby ve třídách.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

Výstup je následující.

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Alternativní způsoby, jak vytvořit pole

Můžete také použít `val` – klíčové slovo vytvořit soukromé pole. Při použití `val` – klíčové slovo, pole není zadána hodnota, pokud objekt je vytvořen, ale místo toho se inicializuje s výchozí hodnotou. Další informace najdete v tématu [explicitní pole: val – klíčové slovo](explicit-fields-the-val-keyword.md).

Můžete také definovat privátní pole v třídě pomocí definice členské a přidáním klíčového slova `private` na definici. To může být užitečné, pokud očekáváte, změňte přístupnost člena bez přepsání kódu. Další informace najdete v tématu [řízení přístupu](../access-control.md).

## <a name="see-also"></a>Viz také:

- [Členové](index.md)
- [`do` Vazby ve třídách](do-bindings-in-classes.md)
- [`let` Vazby](../functions/let-bindings.md)
