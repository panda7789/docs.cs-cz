---
title: do – vazby (F#)
description: 'Zjistěte, jak F # "do" vazby se používá ke spouštění kódu bez definování funkce nebo hodnota.'
ms.date: 05/16/2016
ms.openlocfilehash: 6fd084090a204beab0da1c2deb5b5ae2a86281c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="do-bindings"></a>do – vazby

A `do` vazby se používá ke spouštění kódu bez definování funkce nebo hodnota. Proveďte vazby může být také používány třídy, najdete v části [ `do` vazby do ve třídách](../members/do-bindings-in-classes.md).


## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Poznámky
Použití `do` vazby, pokud chcete spustit kód s nezávisle na definici funkce nebo hodnota. Výraz v `do` vazby musí vracet `unit`. Kód nejvyšší úrovni `do` vazba se spustí při inicializaci modulu. Klíčové slovo `do` je volitelný.

Atributy lze použít jako nejvyšší úrovni `do` vazby. Například pokud váš program používá zprostředkovatel komunikace s objekty COM, můžete chtít použít `STAThread` atribut vašeho programu. Můžete to provést pomocí atributu na `do` vazby, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](../index.md)

[Funkce](index.md)

