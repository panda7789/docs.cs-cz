---
title: "Smyčky: Výraz while...do (F#)"
description: "V tématu jak při... provést výraz se používá k provádění iterativní provádění (opakování ve smyčce) zadaný testovací podmínku hodnotu true."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0416ffca-7ed9-4aff-9493-e001fdba8c9b
ms.openlocfilehash: 5f10fda84a5e748856eb7b2c63ad46cc1fba44bb
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="loops-whiledo-expression"></a>Smyčky: Výraz while...do

`while...do` Výraz se používá k provádění iterativní provádění (opakování ve smyčce) zadaný testovací podmínku hodnotu true.


## <a name="syntax"></a>Syntaxe

```fsharp
while test-expression do
    body-expression
```

## <a name="remarks"></a>Poznámky
*Testovací výraz* vyhodnotí; Pokud je `true`, *textu výraz* se spustí a testovací výraz vyhodnocen znovu. *Textu výraz* musí mít typ `unit`. Pokud je test výraz `false`, skončení iterací.

Následující příklad ukazuje použití `while...do` výraz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5301.fs)]

Výstup jako předchozí kód je proud náhodná čísla 1 až 20, poslední z nich je 10.

```
13 19 8 18 16 2 10
Found a 10!
```

>[!NOTE] 
Můžete použít `while...do` v pořadí výrazy a další výpočetní výrazy v takovém případě přizpůsobená verze `while...do` použit výraz. Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výpočetní výrazy](computation-expressions.md).


## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Smyčky: `for...in` výraz](loops-for-in-expression.md)

[Smyčky: `for...to` výraz](loops-for-to-expression.md)
