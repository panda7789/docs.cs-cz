---
title: Vazby let ve třídách
description: Naučte se definovat soukromá pole a soukromé funkce pro F# třídy pomocí vazeb let v definici třídy.
ms.date: 05/16/2016
ms.openlocfilehash: 1366ab8f1f4f606fe5947a8fc4df10de49346b3e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216527"
---
# <a name="let-bindings-in-classes"></a>Vazby let ve třídách

Můžete definovat soukromá pole a soukromé funkce pro F# třídy pomocí `let` vazeb v definici třídy.

## <a name="syntax"></a>Syntaxe

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Poznámky

Předchozí syntaxe se zobrazí za záhlavím třídy a deklaracemi dědičnosti, ale před jakýmikoli definicemi členů. Syntaxe je stejná jako u `let` vazeb mimo třídy, ale názvy definované ve třídě mají obor, který je omezen na třídu. `let` Vazba vytvoří soukromé pole nebo funkci; k veřejnému vystavení dat nebo funkcí, deklaraci vlastnosti nebo metody člena.

Vazba, která není statická, se nazývá vazba instance `let`. `let` Vazby `let` instance jsou spouštěny při vytváření objektů. Statické `let` vazby jsou součástí statického inicializátoru pro třídu, která je zaručena k provedení před prvním použitím typu.

Kód v rámci vazeb `let` instance může používat parametry primárního konstruktoru.

Atributy a Modifikátory dostupnosti nejsou u `let` vazeb ve třídách povoleny.

Následující příklady kódu ilustrují několik typů `let` vazeb ve třídách.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

Výstup je následující.

```console
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Alternativní způsoby vytváření polí

`val` Klíčové slovo můžete také použít k vytvoření soukromého pole. Při použití `val` klíčového slova není pole při vytvoření objektu přidělena hodnota, ale místo toho je inicializována s výchozí hodnotou. Další informace najdete v tématu [explicitní pole: Klíčové slovo](explicit-fields-the-val-keyword.md)Val

Můžete také definovat soukromá pole ve třídě pomocí definice člena a přidat klíčové slovo `private` do definice. To může být užitečné, pokud očekáváte, že změníte přístupnost člena, aniž byste museli přepisovat kód. Další informace najdete v tématu [Access Control](../access-control.md).

## <a name="see-also"></a>Viz také:

- [Členové](index.md)
- [`do`Vazby ve třídách](do-bindings-in-classes.md)
- [`let`Vazeb](../functions/let-bindings.md)
