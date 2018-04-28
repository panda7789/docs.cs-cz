---
title: Vazby let ve třídách (F#)
description: "Zjistěte, jak definovat privátním polím a privátní funkce pro třídy F # pomocí vazby, umožní' v definici třídy."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: c4511a541403dde517acaf902e86de8d48f13781
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="let-bindings-in-classes"></a>Vazby let ve třídách

Můžete definovat privátním polím a privátní funkce pro třídy F # pomocí `let` vazby v definici třídy.


## <a name="syntax"></a>Syntaxe

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>Poznámky
Předchozí syntaxe se zobrazí po deklaracích záhlaví a dědičnost třídy, ale před všechny definice člen. Syntaxe je stejná jako u `let` vazby mimo třídy, ale názvy definované v třídě mít obor, který je omezený na třídu. A `let` vazbou soukromé pole nebo funkce; ke zveřejňování dat nebo funkce deklarovat veřejně, vlastnost nebo metoda člen.

A `let` vazby, který není statický nazývá instance `let` vazby. Instance `let` vazby spuštění při vytvoření objektů. Statické `let` vazby jsou součástí statické inicializátoru pro třídu, která záruku, že se provést před prvním použití typu.

Kód v rámci instance `let` vazby můžete použít primární konstruktor parametry.

Atributy a usnadnění modifikátory nejsou povolené pro `let` vazby do ve třídách.

Následující příklady kódu ilustrují několik typů `let` vazby do ve třídách.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

Výstup je následující.

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>Alternativní způsoby, jak vytvořit pole
Můžete také `val` – klíčové slovo k vytvoření soukromé pole. Při použití `val` – klíčové slovo, pole není zadána hodnota, pokud objekt se vytvoří, ale místo toho se inicializuje výchozí hodnotu. Další informace najdete v tématu [explicitní pole: val – klíčové slovo](explicit-fields-the-val-keyword.md).

Můžete také definovat privátním polím v třídě pomocí definice člena a přidáním klíčové slovo `private` k definici. To může být užitečné, pokud očekáváte, chcete-li změnit usnadnění člena bez přepisování kódu. Další informace najdete v tématu [řízení přístupu](../access-control.md).

## <a name="see-also"></a>Viz také
[Členové](index.md)

[`do` Vazby do ve třídách](do-bindings-in-classes.md)

[`let` Vazby](../functions/let-bindings.md)
