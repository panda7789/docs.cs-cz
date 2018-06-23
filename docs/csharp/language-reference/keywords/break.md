---
title: BREAK – příkaz (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 987ee1ca5601b3dd105412bf0fa18361c57a95fd
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36315235"
---
# <a name="break-c-reference"></a>break (Referenční dokumentace jazyka C#)

`break` Příkaz ukončí nejbližší nadřazených smyčky nebo [přepínač](../../../csharp/language-reference/keywords/switch.md) příkaz, ve kterém se zobrazí. Ovládací prvek předává do příkazu, který následuje ukončenou příkaz, pokud existuje.

## <a name="example"></a>Příklad

V tomto příkladu obsahuje příkaz podmíněného čítač, který by měl počítat od 1 do 100; ale `break` příkaz ukončí smyčky po 4 počty.

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a>Příklad

V tomto příkladu `break` se použije příkaz k přerušení mimo smyčky vnořené vnitřní a vnější smyčky vrácení řízení.

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a>Příklad

Tento příklad ukazuje použití `break` v [přepínač](../../../csharp/language-reference/keywords/switch.md) příkaz.

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

Pokud jste zadali `4`, bude výstup:

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
[Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
[switch](../../../csharp/language-reference/keywords/switch.md)  
[Jump – příkazy](../../../csharp/language-reference/keywords/jump-statements.md)  
[Příkazy iterace](../../../csharp/language-reference/keywords/iteration-statements.md)
