---
title: příkaz break - odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713755"
---
# <a name="break-c-reference"></a>break (Referenční dokumentace jazyka C#)

Příkaz `break` ukončí nejbližší ohraničující smyčky nebo [switch](./switch.md) příkaz, ve kterém se zobrazí. Ovládací prvek je předán příkazu, který následuje za ukončené prohlášení, pokud existuje.

## <a name="example"></a>Příklad

V tomto příkladu podmíněné prohlášení obsahuje čítač, který má počítat od 1 do 100; však `break` příkaz ukončí smyčky po 4 počítá.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Příklad

Tento příklad ukazuje použití `break` v [příkazu switch.](./switch.md)

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Pokud jste `4`zadali , výstup by byl:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a>Příklad

V tomto příkladu `break` se příkaz používá k přerušení vnitřní vnořené smyčky a vrácení ovládacího prvku do vnější smyčky. Ovládací prvek je _vrácena pouze_ o jednu úroveň výš v vnořené smyčky.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Příklad

V tomto příkladu `break` se příkaz používá pouze k přerušení aktuální větve během každé iterace smyčky. Samotná smyčka není ovlivněna `break` instancemi, které patří do vnořeného [příkazu switch.](./switch.md)

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](./index.md)
- [Přepnout](./switch.md)
