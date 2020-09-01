---
description: break – příkaz – reference jazyka C#
title: break – příkaz – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 7fd05889f684f7a2282de8222e1195898dead5b9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134741"
---
# <a name="break-c-reference"></a>break (Referenční dokumentace jazyka C#)

`break`Příkaz ukončí nejbližší ohraničující smyčku nebo příkaz [Switch](./switch.md) , ve kterém se zobrazí. Ovládací prvek je předán příkazu, který následuje ukončený příkaz, pokud existuje.

## <a name="example"></a>Příklad

V tomto příkladu podmíněný příkaz obsahuje čítač, který by měl počítat od 1 do 100; `break` příkaz však ukončí smyčku po 4 počtech.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Příklad

Tento příklad ukazuje použití `break` v příkazu [Switch](./switch.md) .

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Pokud jste zadali `4` , bude výstup:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a>Příklad

V tomto příkladu `break` je příkaz použit k přerušení vnitřní vnořené smyčky a vrátí řízení vnější smyčce. Řízení je vráceno _pouze_ ve vnořených smyčkách o jednu úroveň výš.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Příklad

V tomto příkladu `break` je příkaz použit pouze k přerušení aktuální větve během každé iterace smyčky. Samotný cyklus není ovlivněn instancemi `break` , které patří do vnořeného příkazu [Switch](./switch.md) .

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [přepnutí](./switch.md)
