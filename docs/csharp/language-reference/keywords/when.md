---
title: Když (referenční dokumentace jazyka C#)
ms.date: 03/07/2017
f1_keywords:
- when_CSharpKeyword
- when
helpviewer_keywords:
- when keyword [C#]
ms.assetid: dd543335-ae37-48ac-9560-bd5f047b9aea
ms.openlocfilehash: 3168cf620eb3aaf206afbe5bc2efc297832503ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
 # <a name="when-c-reference"></a>Když (referenční dokumentace jazyka C#)

Můžete použít `when` kontextové klíčové slovo chcete zadat podmínku filtrování do dvou kontextů:

- V `catch` prohlášení o [try/catch –](try-catch.md) nebo [try/catch/finally –](try-catch-finally.md) bloku.
- V `case` popisek [přepínač](switch.md) příkaz.

## <a name="when-in-a-catch-statement"></a>`when` v `catch` – příkaz

Od verze jazyka C# 6, `When` mohou být používány `catch` lze zadat podmínku, která musí být splněny pro obslužnou rutinu pro konkrétní výjimky k provedení. Jeho syntaxe je:

```csharp
catch ExceptionType [e] when (expr)
```
kde *expr* je výraz, který se vyhodnotí jako logická hodnota. Vrátí-li `true`, zpracuje obslužná rutina výjimky; Pokud `false`, neexistuje. 

Následující příklad používá `when` – klíčové slovo k podmíněnému spuštění obslužné rutiny pro <xref:System.Net.Http.HttpRequestException> v závislosti na text zpráva o výjimce.

 [!code-csharp[when-with-catch](../../../../samples/snippets/csharp/language-reference/keywords/when/catch.cs)]  
  
## <a name="when-in-a-switch-statement"></a>`when` v `switch` – příkaz

Od verze jazyka C# 7.0, `case` popisky už musí být vzájemně vylučují a pořadí, v jakém `case` zobrazí popisky v `switch` příkaz můžete určit, které bloku přepínačů provede. `when` – Klíčové slovo lze použít k určení podmínku filtrování, který způsobuje její přidružené návěstí pravdivá pouze v případě, že podmínku filtrování platí taky. Jeho syntaxe je:

```csharp
case (expr) when (when-condition):
```
kde *expr* konstantní vzor nebo typ vzor, který je ve srovnání s výrazu shody a *podmínka v případě* je libovolný logický výraz. 

Následující příklad používá `when` – klíčové slovo chcete otestovat `Shape` objekty, které mají určitou oblast nula, také tak, aby testovací pro celou řadu `Shape` objekty, které mají určitou oblast, která je větší než nula. 

 [!code-csharp[when-with-case#1](../../../../samples/snippets/csharp/language-reference/keywords/when/when.cs#1)]  

## <a name="see-also"></a>Viz také 
  [Switch – příkaz](switch.md)  
  [try/catch – příkaz](try-catch.md)  
  [try/catch/finally – příkaz](try-catch-finally.md) 

