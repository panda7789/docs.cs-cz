---
title: do – vazby (F#)
description: 'Zjistěte, jak F # "do" vazby se používá ke spouštění kódu bez definování funkce nebo hodnota.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4c63da0c5e2f4130d59f9efa6bc54a55e5fe9fd8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
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

