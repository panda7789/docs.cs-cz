---
title: Objektové výrazy
description: Další informace o použití F# objektové výrazy, když chcete se vyhnout zvláštní kód a režijní náklady na potřebné k vytvoření nového, s názvem typu.
ms.date: 05/16/2016
ms.openlocfilehash: cb15983543fde2459c589b3de2554575d73db686
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613918"
---
# <a name="object-expressions"></a>Objektové výrazy

*Objektu výraz* je výraz, který vytvoří novou instanci typu dynamicky generovaný anonymní objekt, který je založen na existující základní typ, rozhraní nebo sady rozhraní.

## <a name="syntax"></a>Syntaxe

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a>Poznámky

V předchozí syntaxi *typename* představuje existující typu třídy nebo rozhraní. *parametry typu* obsahuje popis parametrů, volitelné obecného typu. *Argumenty* se používají pouze pro typy tříd, které vyžadují parametry konstruktoru. *Definice členů* přepsání metody základní třídy nebo implementace abstraktní metody ze základní třídy nebo rozhraní.

Následující příklad ukazuje několik různých typů objektové výrazy.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a>Použitím objektových výrazů

Objektové výrazy používají, když chcete se vyhnout zvláštní kód a režijní náklady, který je potřeba vytvořit nový s názvem typu. Používáte-li minimalizovat počet typů, které jsou vytvořené v programu objektové výrazy, můžete snížit počet řádků kódu a zabránit zbytečným růst počtu typů. Místo vytváření mnoho typů pouze pro zpracování konkrétních situacích, můžete použít objektový výraz, který přizpůsobí existujícího typu nebo poskytuje ve vhodné implementaci rozhraní pro tento konkrétní případ po ruce.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)