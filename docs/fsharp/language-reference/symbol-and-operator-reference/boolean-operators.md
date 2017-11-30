---
title: "Logické operátory (F#)"
description: "Další informace o logické operátory, které jsou k dispozici v programovací jazyk F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f79370b8-4bc2-4704-b514-d392c80942bd
ms.openlocfilehash: 63588f2e371bf2c0f15de0b8a26a46be82f832c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="boolean-operators"></a>Logické operátory

Toto téma popisuje podporu logické operátory v jazyce F #.


## <a name="summary-of-boolean-operators"></a>Souhrn logické operátory
Následující tabulka shrnuje logické operátory, které jsou k dispozici v jazyce F #. Je jediným typem podporuje tyto operátory `bool` typu.

|Operátor|Popis|
|--------|-----------|
|`not`|Logická negace|
|<code>&#124;&#124;</code>|Logická hodnota nebo|
|`&&`|Logická hodnota a|

Logická hodnota a a nebo operátory provést *krátká smyčka – vyhodnocení*, to znamená, že vyhodnocování výrazu na pravé straně operátoru jenom v případě, že je nutné určit celkový výsledek výrazu. Druhý výraz `&&` operátor vyhodnotí pouze v případě, že první vyhodnocen jako `true`; druhý výraz `||` operátor vyhodnotí pouze v případě, že první vyhodnocen jako `false`.

## <a name="see-also"></a>Viz také
[Bitové operátory](bitwise-operators.md)

[Aritmetické operátory](arithmetic-operators.md)

[Operátor referenční dokumentace symbolů a](index.md)
