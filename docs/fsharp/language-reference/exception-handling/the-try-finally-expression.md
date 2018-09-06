---
title: 'Výjimky: Výraz try...finally (F#)'
description: "Zjistěte, jak F # ' try... finally \"výraz umožňuje spuštění kódu čištění i v případě, že blok kódu vyvolá výjimku."
ms.date: 05/16/2016
ms.openlocfilehash: 546a6b0619de6f51044600dc1ead73c6d5211299
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43803340"
---
# <a name="exceptions-the-tryfinally-expression"></a>Výjimky: Výraz try...finally

`try...finally` Výraz umožňuje spuštění kódu čištění i v případě, že blok kódu vyvolá výjimku.

## <a name="syntax"></a>Syntaxe

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Poznámky

`try...finally` Výraz lze použít ke spouštění kódu vytvořeného v *expression2* v předchozí syntaxi bez ohledu na to, zda je vygenerována výjimka při provádění *expression1*.

Typ *expression2* není přispívat k hodnotě celý výraz; typ vrácený při výjimce nedochází je poslední hodnotu v *expression1*. Pokud dojde k výjimce, není vrácena žádná hodnota a tok řízení přenosů na další odpovídající obslužnou rutinu výjimky v zásobníku volání. Pokud se nenajde žádná obslužná rutina výjimky, program se ukončí. Předtím, než kód v odpovídající obslužná rutina se spustí nebo ukončí program, kód `finally` větev provést.

Následující kód demonstruje použití `try...finally` výrazu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

Výstup do konzoly nástroje je následující.

```
Closing stream
Exception handled.
```

Jak je vidět z výstupu datového proudu se zavřel před vnější výjimka byla zpracována a soubor `test.txt` obsahuje text `test1`, která označuje, že byly vyrovnávací paměti vyprázdněných a zapíšou na disk i v případě, že přenést výjimku řízení na obslužnou rutinu vnější výjimky.

Všimněte si, že `try...with` konstruktor je samostatnou konstrukci z `try...finally` vytvořit. Proto pokud váš kód vyžaduje obě `with` bloku a `finally` bloku, budete muset vnořit dvě konstrukce, jako v následujícím příkladu kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

V rámci výrazech výpočtu, včetně výrazech pořadí a asynchronní pracovní postupy **try... finally** výrazy mohou mít vlastní implementaci. Další informace najdete v tématu [výrazech výpočtu](../computation-expressions.md).

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Výjimky: `try...with` výraz](the-try-with-expression.md)
