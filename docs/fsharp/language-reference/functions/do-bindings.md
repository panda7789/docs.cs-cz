---
title: do – vazby
description: Zjistěte, jak F# "do" vazby se používá k provádění kódu bez definování funkce nebo hodnota.
ms.date: 05/16/2016
ms.openlocfilehash: d29f8557fda06097d2e85748ab6286f0415730b3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683376"
---
# <a name="do-bindings"></a>do – vazby

A `do` vazby se používá k provádění kódu bez definování funkce nebo hodnota. Také proveďte vazby může být použit ve třídách, naleznete v tématu [ `do` vazby ve třídách](../members/do-bindings-in-classes.md).

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Poznámky

Použití `do` vazby, pokud chcete spustit kód bez ohledu na jejich definici funkce nebo hodnota. Výraz v `do` vazby musí vracet `unit`. Kód v nejvyšší úrovni `do` vazby je proveden při inicializaci modulu. Klíčové slovo `do` je volitelný.

Atributy lze použít na nejvyšší úrovni `do` vazby. Například pokud program používá zprostředkovatele komunikace s objekty COM, můžete chtít použít `STAThread` atribut vašemu programu. Můžete to provést pomocí atributu na `do` vazbu, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](../index.md)
- [Funkce](index.md)