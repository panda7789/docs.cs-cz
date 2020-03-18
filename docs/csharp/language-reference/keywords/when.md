---
title: při kontextovém klíčovém slově – c# odkaz
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 6a61c42ba2d01e84ffae376bf95c99877437be85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712829"
---
# <a name="when-c-reference"></a>když (Odkaz jazyka C#)

Kontextové `when` klíčové slovo můžete použít k určení podmínky filtru ve dvou kontextech:

- V `catch` příkazu [try/catch](try-catch.md) nebo [try/catch/finally](try-catch-finally.md) block.
- V `case` popisku [příkazu switch.](switch.md)

## <a name="when-in-a-catch-statement"></a>`when`v `catch` prohlášení

Počínaje C# 6, `when` lze použít `catch` v příkazu k určení podmínky, která musí být true pro obslužnou rutinu pro konkrétní výjimku spustit. Jeho syntaxe je:

```csharp
catch (ExceptionType [e]) when (expr)
```

kde *expr* je výraz, který je vyhodnocen jako logická hodnota. Pokud vrátí `true`, obslužná rutina výjimky se spustí; pokud `false`tomu tak není.

Následující příklad používá `when` klíčové slovo podmíněně spustit <xref:System.Net.Http.HttpRequestException> obslužné rutiny pro v závislosti na textu zprávy o výjimce.

[!code-csharp[when-with-catch](~/samples/snippets/csharp/language-reference/keywords/when/catch.cs)]

## <a name="when-in-a-switch-statement"></a>`when`v `switch` prohlášení

Počínaje C# 7.0 `case` popisky již nemusí být vzájemně vylučovat a pořadí, ve kterém `case` popisky se zobrazí v příkazu `switch` můžete určit, který přepínač blok spustí. Klíčové `when` slovo lze použít k určení podmínky filtru, která způsobí, že jeho přidružený popisek případu bude pravdivý pouze v případě, že je splněna také podmínka filtru. Jeho syntaxe je:

```csharp
case (expr) when (when-condition):
```

kde *expr* je konstantní vzor nebo vzorek typu, který je porovnán s výrazem shody, a *když podmínka* je jakýkoli logický výraz.

Následující příklad používá `when` klíčové slovo `Shape` k testování objektů, které mají oblast nula, `Shape` stejně jako k testování různých objektů, které mají oblast větší než nula.

[!code-csharp[when-with-case#1](~/samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]

## <a name="see-also"></a>Viz také

- [příkaz switch](switch.md)
- [try/catch prohlášení](try-catch.md)
- [příkaz try/catch/finally](try-catch-finally.md)
