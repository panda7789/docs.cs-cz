---
title: When – kontextové klíčové slovo – Reference jazyka C#
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 2b041ca3a821f45dd63ce3f6bee7a920eb495651
ms.sourcegitcommit: 32f0d6f4c01ddc6ca78767c3a30e3305f8cd032c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2020
ms.locfileid: "87426992"
---
# <a name="when-c-reference"></a>When (Referenční dokumentace jazyka C#)

Pomocí `when` klíčového slova kontext můžete určit podmínku filtru v následujících kontextech:

- V `catch` příkazu pro blok [try/catch](try-catch.md) nebo [try/catch/finally](try-catch-finally.md) .
- V `case` popisku příkazu [Switch](switch.md) .
- Ve [ `switch` výrazu](../operators/switch-expression.md).

## <a name="when-in-a-catch-statement"></a>`when`v `catch` příkazu

Počínaje jazykem C# 6 `when` lze použít v `catch` příkazu k určení podmínky, která musí být pravdivá pro obslužnou rutinu pro spuštění konkrétní výjimky. Jeho syntaxe je:

```csharp
catch (ExceptionType [e]) when (expr)
```

kde *expr* je výraz, který je vyhodnocen jako logická hodnota. Pokud se vrátí `true` , spustí se obslužná rutina výjimky, pokud `false` není.

Následující příklad používá `when` klíčové slovo k podmíněnému provedení obslužných rutin pro <xref:System.Net.Http.HttpRequestException> v závislosti na textu zprávy o výjimce.

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a>`when`v `switch` příkazu

Počínaje jazykem C# 7,0 `case` popisky již nemusejí být vzájemně exkluzivní a pořadí, ve kterém `case` se popisky zobrazí v `switch` příkazu, mohou určit, který blok přepínače se spustí. `when`Klíčové slovo lze použít k určení podmínky filtru, která způsobí, že popisek jeho přidruženého případu bude platit pouze v případě, že je podmínka filtru pravdivá. Jeho syntaxe je:

```csharp
case (expr) when (when-condition):
```

kde *expr* je konstanta vzoru nebo typu, která je porovnána s výrazem Match, a *Podmínka when* je libovolný logický výraz.

Následující příklad používá `when` klíčové slovo pro otestování `Shape` objektů, které mají oblast nula, a také pro testování nejrůznějších `Shape` objektů, které mají oblast větší než nula.

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a>Viz také:

- [switch – příkaz](switch.md)
- [try/catch – příkaz](try-catch.md)
- [try/catch/finally – příkaz](try-catch-finally.md)
