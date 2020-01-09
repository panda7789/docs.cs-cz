---
title: příkaz break – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713755"
---
# <a name="break-c-reference"></a>break (Referenční dokumentace jazyka C#)

Příkaz `break` ukončí nejbližší ohraničující smyčku nebo příkaz [Switch](./switch.md) , ve kterém se zobrazí. Ovládací prvek je předán příkazu, který následuje ukončený příkaz, pokud existuje.

## <a name="example"></a>Příklad

V tomto příkladu podmíněný příkaz obsahuje čítač, který by měl počítat od 1 do 100; příkaz `break` však ukončí smyčku po 4 počtech.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Příklad

Tento příklad ukazuje použití `break` v příkazu [Switch](./switch.md) .

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Pokud jste zadali `4`, výstup by byl:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a>Příklad

V tomto příkladu je příkaz `break` použit k přerušení vnitřní vnořené smyčky a vrátí řízení vnější smyčce. Řízení je vráceno _pouze_ ve vnořených smyčkách o jednu úroveň výš.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Příklad

V tomto příkladu je příkaz `break` použit pouze k přerušení aktuální větve během každé iterace smyčky. Samotný cyklus není ovlivněn instancemi `break`, které patří do vnořeného příkazu [Switch](./switch.md) .

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [switch](./switch.md)
