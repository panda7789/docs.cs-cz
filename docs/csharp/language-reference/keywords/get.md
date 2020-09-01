---
description: Reference Get-C#
title: Reference Get-C#
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 7e13dc3ed6577717c64b4e36000a9e090f7b4751
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139733"
---
# <a name="get-c-reference"></a>get (Referenční dokumentace jazyka C#)

`get`Klíčové slovo definuje metodu *přístupového objektu* ve vlastnosti nebo indexeru, který vrací hodnotu vlastnosti nebo prvek indexeru. Další informace najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md) a [indexery](../../programming-guide/indexers/index.md).  
  
Následující příklad definuje jak `get` a `set` přístup k vlastnosti s názvem `Seconds` . K zálohování hodnoty vlastnosti používá soukromé pole s názvem `_seconds` .  

 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
`get`Přistupující objekt se často skládá z jediného příkazu, který vrací hodnotu, stejně jako v předchozím příkladu. Počínaje jazykem C# 7,0 můžete implementovat `get` přistupující objekt jako člena Expression-těle. Následující příklad implementuje rozhraní `get` a `set` přístup jako členy Expression-těle.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]

Pro jednoduché případy, kdy přístup k vlastnostem `get` a `set` přistupující objekty neprovádí žádnou jinou operaci než nastavení nebo načtení hodnoty v soukromém poli pro zálohování, můžete využít podporu kompilátoru C# pro automaticky implementované vlastnosti. Následující příklad implementuje `Hours` jako automaticky implementovanou vlastnost.
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](./index.md)
- [Vlastnosti](../../programming-guide/classes-and-structs/properties.md)
