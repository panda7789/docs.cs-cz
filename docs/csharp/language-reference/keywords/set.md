---
description: Set – klíčové slovo – Referenční dokumentace jazyka C#
title: Set – klíčové slovo – Referenční dokumentace jazyka C#
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: ff0c99e5d4d6271351783befd6650d9a77f39886
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136912"
---
# <a name="set-c-reference"></a>set (Referenční dokumentace jazyka C#)

`set`Klíčové slovo definuje metodu *přistupujícího objektu* ve vlastnosti nebo indexeru, která přiřadí hodnotu vlastnosti nebo prvku indexeru. Další informace a příklady najdete v tématech [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md)a [indexery](../../programming-guide/indexers/index.md).

Následující příklad definuje jak `get` a `set` přístup k vlastnosti s názvem `Seconds` . K zálohování hodnoty vlastnosti používá soukromé pole s názvem `_seconds` .

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

`set`Přistupující objekt se často skládá z jediného příkazu, který přiřadí hodnotu, stejně jako v předchozím příkladu. Počínaje jazykem C# 7,0 můžete implementovat `set` přistupující objekt jako člena Expression-těle. Následující příklad implementuje jak `get` a `set` přistupující objekty jako členy Expression-těle.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
Pro jednoduché případy, kdy přístup k vlastnostem `get` a `set` přistupující objekty neprovádí žádnou jinou operaci než nastavení nebo načtení hodnoty v soukromém poli pro zálohování, můžete využít podporu kompilátoru C# pro automaticky implementované vlastnosti. Následující příklad implementuje `Hours` jako automaticky implementovanou vlastnost.

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Vlastnosti](../../programming-guide/classes-and-structs/properties.md)
