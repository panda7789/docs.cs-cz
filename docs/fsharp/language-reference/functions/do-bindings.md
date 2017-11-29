---
title: "do – vazby (F#)"
description: "Zjistěte, jak F # \"do\" vazby se používá ke spouštění kódu bez definování funkce nebo hodnota."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4c1057a3-3aa1-4b64-b46a-25ffe33f0be9
ms.openlocfilehash: f2563d384b67c005c96c2ff487c786476d385e70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
[Referenční dokumentace jazyka F #](../index.md)

[Funkce](index.md)

