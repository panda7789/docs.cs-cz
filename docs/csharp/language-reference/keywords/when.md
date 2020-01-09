---
title: Když se odkazuje na C# kontextové klíčové slovo
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712829"
---
# <a name="when-c-reference"></a>When (C# odkaz)

Pomocí klíčového slova `when` kontextové můžete určit podmínku filtru ve dvou kontextech:

- V příkazu `catch` bloku [try/catch](try-catch.md) nebo [try/catch/finally](try-catch-finally.md) .
- V popisku `case` příkazu [Switch](switch.md) .

## <a name="when-in-a-catch-statement"></a>`when` v příkazu `catch`

Počínaje C# 6 `when` lze použít v příkazu `catch` k určení podmínky, která musí být pravdivá pro obslužnou rutinu pro spuštění konkrétní výjimky. Jeho syntaxe je:

```csharp
catch (ExceptionType [e]) when (expr)
```

kde *expr* je výraz, který je vyhodnocen jako logická hodnota. Pokud vrátí `true`, spustí se obslužná rutina výjimky; Pokud `false`, není.

Následující příklad používá klíčové slovo `when` k podmíněnému provedení obslužných rutin pro <xref:System.Net.Http.HttpRequestException> v závislosti na textu zprávy o výjimce.

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a>`when` v příkazu `switch`

Počínaje C# 7,0 `case` popisky již nemusejí být vzájemně exkluzivní a pořadí, ve kterém `case` popisky se zobrazí v příkazu `switch`, mohou určit, který blok přepínače se spustí. Klíčové slovo `when` lze použít k určení podmínky filtru, která způsobí, že popisek jeho přidruženého případu bude platit pouze v případě, že je podmínka filtru pravdivá. Jeho syntaxe je:

```csharp
case (expr) when (when-condition):
```

kde *expr* je konstanta vzoru nebo typu, která je porovnána s výrazem Match, a *Podmínka when* je libovolný logický výraz.

Následující příklad používá klíčové slovo `when` k otestování `Shape` objektů, které mají oblast nula, a také k otestování celé řady `Shape` objektů, které mají oblast větší než nula.

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a>Viz také:

- [příkaz switch](switch.md)
- [try/catch – příkaz](try-catch.md)
- [try/catch/finally – příkaz](try-catch-finally.md)
