---
title: 'Výjimky: Výraz try...finally'
description: Podívejte se, F# jak se "Try... finally ' Expression umožňuje spustit čistý kód, i když blok kódu vyvolá výjimku.
ms.date: 05/16/2016
ms.openlocfilehash: 0ddb64ac13b307404864ec5b54f26fd8a7a3d7d8
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082996"
---
# <a name="exceptions-the-tryfinally-expression"></a>Výjimky: Výraz try...finally

`try...finally` Výraz umožňuje spustit čistý kód i v případě, že blok kódu vyvolá výjimku.

## <a name="syntax"></a>Syntaxe

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Poznámky

Výraz lze použít ke spuštění kódu v příkazu *Výraz2* v předchozí syntaxi bez ohledu na to, zda je výjimka generována během provádění *Výraz1.* `try...finally`

Typ *Výraz2* nepřispívá k hodnotě celého výrazu; typ vrácený při výskytu výjimky je poslední hodnota v *Výraz1*. Pokud dojde k výjimce, není vrácena žádná hodnota a tok řízení přenáší do další shodné výjimky obslužné rutiny v zásobníku volání. Pokud není nalezena žádná obslužná rutina výjimky, program skončí. Předtím, než je proveden kód v rámci vyhovující obslužné rutiny nebo program skončí, je spuštěn kód `finally` ve větvi.

Následující kód demonstruje použití `try...finally` výrazu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

Výstup do konzoly je následující.

```console
Closing stream
Exception handled.
```

Jak vidíte z výstupu, datový proud byl ukončen před tím, než byla zpracována vnější výjimka, a soubor `test.txt` obsahuje text `test1`, který označuje, že byly vyrovnávací paměti vyprázdněny a zapsány na disk, i když byla výjimka převedena. řízení vnější obslužné rutiny výjimky.

Všimněte si, `try...with` že konstrukce je samostatná konstrukce `try...finally` ze konstrukce. Proto pokud váš kód vyžaduje `with` blok `finally` i blok, je nutné vnořit dvě konstrukce, jako v následujícím příkladu kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

V kontextu výrazů výpočtu, včetně sekvenčních výrazů a asynchronních pracovních postupů, **zkuste... výrazy finally** mohou mít vlastní implementaci. Další informace najdete v tématu [výrazy výpočtu](../computation-expressions.md).

## <a name="see-also"></a>Viz také:

- [Zpracování výjimek](index.md)
- [Výjimky: `try...with` Výraz](the-try-with-expression.md)
