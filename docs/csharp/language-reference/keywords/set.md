---
title: nastavit klíčové slovo - C# Reference
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 0b293709abe64a0a82d8575f6793a07ca6c9533b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173494"
---
# <a name="set-c-reference"></a>set (Referenční dokumentace jazyka C#)

Klíčové `set` slovo definuje *přistupující* metodu ve vlastnosti nebo indexeru, který přiřadí hodnotu vlastnosti nebo prvku indexeru. Další informace a příklady naleznete [v tématu Vlastnosti](../../programming-guide/classes-and-structs/properties.md), [Automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md)a [Indexery](../../programming-guide/indexers/index.md).

Následující příklad definuje jak `get` a `set` a a přistupující objekt pro vlastnost s názvem `Seconds`. Používá soukromé pole `_seconds` s názvem zpět hodnotu vlastnosti.

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

Často přistupující `set` ho se skládá z jednoho příkazu, který přiřadí hodnotu, stejně jako v předchozím příkladu. Počínaje C# 7.0, můžete `set` implementovat přistupující objekt jako člen s výrazem. Následující příklad implementuje `get` a `set` přístupové prvky jako členy s výrazem.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
Pro jednoduché případy, ve `get` kterých vlastnosti a `set` přistupující objekty provádět žádné jiné operace než nastavení nebo načítání hodnoty v soukromém záložním poli, můžete využít podpory kompilátoru Jazyka C# pro automaticky implementované vlastnosti. Následující příklad implementuje `Hours` jako automaticky implementované vlastnosti.

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../../language-reference/index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Vlastnosti](../../programming-guide/classes-and-structs/properties.md)
