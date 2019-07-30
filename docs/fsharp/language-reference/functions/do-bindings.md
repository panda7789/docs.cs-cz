---
title: do – vazby
description: Zjistěte, jak F# se vazba do používá ke spouštění kódu bez definování funkce nebo hodnoty.
ms.date: 05/16/2016
ms.openlocfilehash: f98f523296bfaceeda35d4861eafbfeaa5a60c32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630537"
---
# <a name="do-bindings"></a>do – vazby

`do` Vazba se používá ke spouštění kódu bez definování funkce nebo hodnoty. Vazby do třídy lze také použít ve třídách naleznete v tématu [ `do` Bindings in Classes](../members/do-bindings-in-classes.md).

## <a name="syntax"></a>Syntaxe

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a>Poznámky

`do` Použijte vazbu, pokud chcete spustit kód nezávisle na definici funkce nebo hodnoty. Výraz ve `do` vazbě musí vracet `unit`. Kód v vazbě nejvyšší úrovně `do` se spustí při inicializaci modulu. Klíčové slovo `do` je volitelné.

Atributy lze použít na vazbu nejvyšší úrovně `do` . Například pokud váš program používá zprostředkovatele komunikace s objekty COM, může být vhodné použít `STAThread` atribut pro váš program. Můžete to provést pomocí atributu u `do` vazby, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](../index.md)
- [Funkce](index.md)
