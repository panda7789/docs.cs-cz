---
title: Když (referenční dokumentace jazyka C#)
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: a71cbdce256b1c1bd5d101d66f216fb229d70adf
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43859192"
---
 # <a name="when-c-reference"></a>Když (referenční dokumentace jazyka C#)

Můžete použít `when` kontextové klíčové slovo k určení podmínky filtru ve dvou kontextů:

- V `catch` příkazem [bloku try/catch](try-catch.md) nebo [konstrukce try/catch/finally](try-catch-finally.md) bloku.
- V `case` popisek [přepnout](switch.md) příkazu.

## <a name="when-in-a-catch-statement"></a>`when` v `catch` – příkaz

Od verze C# 6, `When` lze použít v `catch` příkaz a zadejte podmínku, která musí mít hodnotu true pro obslužnou rutinu pro určité výjimky k provedení. Syntaxe je:

```csharp
catch ExceptionType [e] when (expr)
```
kde *expr* je výraz, který se vyhodnocuje na logickou hodnotu. Vrátí-li `true`, spustí obslužnou rutinu výjimky; Pokud `false`, tomu tak není. 

V následujícím příkladu `when` – klíčové slovo k podmíněnému spuštění obslužné rutiny pro <xref:System.Net.Http.HttpRequestException> v závislosti na text zpráva o výjimce.

 [!code-csharp[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a>`when` v `switch` – příkaz

Od verze C# 7.0, `case` popisky už musí být vzájemně vylučují a pořadí, ve kterém `case` popisků se zobrazí v `switch` příkazu můžete určit, které blok switch spustí. `when` – Klíčové slovo lze použít k určení podmínky filtru, který způsobí, že jeho přidružené popisek případu na hodnotu true pouze v případě, že podmínka platí to i naopak. Syntaxe je:

```csharp
case (expr) when (when-condition):
```
kde *expr* je konstantní vzorek nebo vzor typu, který je ve srovnání s výrazu shody a *podmínka v případě* je libovolný výraz Boolean. 

V následujícím příkladu `when` – klíčové slovo pro testování `Shape` objekty, které mají určitou oblast nula, stejně jako test pro širokou škálu `Shape` objekty, které mají větší než nula oblasti. 

 [!code-csharp[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a>Viz také:

- [Switch – příkaz](switch.md)  
- [try/catch – příkaz](try-catch.md)  
- [konstrukce try/catch/finally – příkaz](try-catch-finally.md) 
