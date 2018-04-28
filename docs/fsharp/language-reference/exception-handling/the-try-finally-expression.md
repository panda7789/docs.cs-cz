---
title: 'Výjimky: Výraz try...finally (F#)'
description: "Zjistěte, jak F # ' try... finally' výrazu umožňuje spuštění kódu čištění i v případě, že blok kódu vyvolá výjimku."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 588e4edb4d25c6d25ef103ba724613db997f68d7
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="exceptions-the-tryfinally-expression"></a>Výjimky: Výraz try...finally

`try...finally` Výrazu umožňuje spuštění kódu čištění i v případě, že blok kódu vyvolá výjimku.


## <a name="syntax"></a>Syntaxe

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Poznámky
`try...finally` Výraz můžete použít ke spouštění kódu vytvořeného v *Výraz2* v předchozí syntaxi bez ohledu na to, jestli se vygeneruje výjimku během provádění *expression1*.

Typ *Výraz2* není podílet se na hodnotu celého výrazu; typ vrácený při výjimku nedojde je poslední hodnotu v *expression1*. Pokud dojde k výjimce, je vrácena žádná hodnota a toku řízení přenese na další obslužná rutina odpovídající výjimky zásobníkem volání. Pokud je nalezena žádná obslužná rutina výjimky, program se ukončí. Před kód v odpovídající obslužná rutina se spustí nebo ukončí program, kód `finally` větev se spustí.

Následující kód ukazuje použití `try...finally` výraz.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

Výstup do konzoly nástroje je následující.

```
Closing stream
Exception handled.
```

Jak je vidět z výstupu datového proudu se zavřel před vnější výjimka bylo zpracováno a soubor `test.txt` obsahuje text `test1`, která označuje, že vyrovnávací paměti byly vyprázdněny a zapsat na disk, i když přenést výjimka řízení na obslužnou rutinu vnější výjimka.

Všimněte si, že `try...with` konstrukce je samostatný konstrukce z `try...finally` vytvořit. Proto pokud kódu vyžaduje, aby obě `with` bloku a `finally` bloku, budete muset vnořit dvě konstrukce, jako v následujícím příkladu kódu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

V kontextu výpočetní výrazy, včetně sekvenční výrazy a asynchronní pracovní postupy, **try... finally** výrazy může mít vlastní implementaci. Další informace najdete v tématu [výpočetní výrazy](../computation-expressions.md).


## <a name="see-also"></a>Viz také
[Zpracování výjimek](index.md)

[Výjimky: `try...with` výraz](the-try-with-expression.md)
