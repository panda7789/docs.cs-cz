---
title: Set – klíčové slovo – Referenční dokumentace jazyka C#
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: cdd84c824cc4dc93f4433f07e9978d22cba3f245
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795063"
---
# <a name="set-c-reference"></a>set (Referenční dokumentace jazyka C#)

`set` Klíčové slovo definuje metodu *přistupujícího objektu* ve vlastnosti nebo indexeru, která přiřadí hodnotu vlastnosti nebo prvku indexeru. Další informace a příklady najdete v tématech [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md)a [indexery](../../programming-guide/indexers/index.md).

Následující příklad definuje jak `get` a `set` přístup k vlastnosti s názvem. `Seconds` K zálohování hodnoty vlastnosti používá soukromé `_seconds` pole s názvem.

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

`set` Přistupující objekt se často skládá z jediného příkazu, který přiřadí hodnotu, stejně jako v předchozím příkladu. Počínaje jazykem C# 7,0 můžete implementovat `set` přistupující objekt jako člena Expression-těle. Následující příklad implementuje jak `get` a `set` přistupující objekty jako členy Expression-těle.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
Pro jednoduché případy, kdy přístup k `get` vlastnostem `set` a přistupující objekty neprovádí žádnou jinou operaci než nastavení nebo načtení hodnoty v soukromém poli pro zálohování, můžete využít podporu kompilátoru C# pro automaticky implementované vlastnosti. Následující příklad implementuje `Hours` jako automaticky implementovanou vlastnost.

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Vlastnosti](../../programming-guide/classes-and-structs/properties.md)
