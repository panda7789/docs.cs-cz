---
title: příkaz break – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 77d18d12cd0fabb26906a5b58dc3939da6214a29
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602244"
---
# <a name="break-c-reference"></a>break (Referenční dokumentace jazyka C#)

Příkaz ukončí nejbližší ohraničující smyčku nebo příkaz switch, ve kterém se zobrazí. [](./switch.md) `break` Ovládací prvek je předán příkazu, který následuje ukončený příkaz, pokud existuje.

## <a name="example"></a>Příklad

V tomto příkladu podmíněný příkaz obsahuje čítač, který by měl počítat od 1 do 100; `break` příkaz však ukončí smyčku po 4 počtech.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Příklad

V tomto příkladu `break` je příkaz použit k přerušení vnitřní vnořené smyčky a vrátí řízení vnější smyčce.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Příklad

Tento příklad ukazuje použití `break` v příkazu [Switch](./switch.md) .

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Pokud jste zadali `4`, bude výstup:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [switch](./switch.md)
