---
title: nastavit odkaz na C# klíčové slovo
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 97b0dbf8716edc4cd465eb5ac693efa0ecaa498b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713076"
---
# <a name="set-c-reference"></a>set (Referenční dokumentace jazyka C#)

Klíčové slovo `set` definuje metodu *přistupujícího objektu* ve vlastnosti nebo indexeru, která přiřadí hodnotu vlastnosti nebo prvku indexeru. Další informace a příklady najdete v tématech [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md)a [indexery](../../programming-guide/indexers/index.md).

Následující příklad definuje `get` a přístupový objekt `set` pro vlastnost s názvem `Seconds`. Pro zálohu hodnoty vlastnosti používá soukromé pole s názvem `_seconds`.

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

Přístupový objekt `set` se často skládá z jediného příkazu, který přiřadí hodnotu, stejně jako v předchozím příkladu. Počínaje C# 7,0 můžete implementovat přistupující objekt `set` jako člena Expression-těle. Následující příklad implementuje `get` a přístupové objekty `set` jako členy Expression-těle.

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
Pro jednoduché případy, kdy `get` a přistupující objekty `set` neprovádí žádnou jinou operaci než nastavení nebo načtení hodnoty v soukromém poli pro zálohování, můžete využít podporu C# kompilátoru pro automaticky implementované vlastnosti. Následující příklad implementuje `Hours` jako automaticky implementovanou vlastnost. 

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../../language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Vlastnosti](../../programming-guide/classes-and-structs/properties.md)
