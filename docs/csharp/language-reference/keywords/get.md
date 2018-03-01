---
title: "get (Referenční dokumentace jazyka C#)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a2e8426e5c5be16be0114b5ccc66f30793ce7dda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="get-c-reference"></a>get (Referenční dokumentace jazyka C#)

`get` Definuje – klíčové slovo *přistupujícího objektu* metoda ve vlastnosti nebo indexer, který vrací hodnoty vlastnosti nebo indexer element. Další informace najdete v tématu [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) a [indexery](../../../csharp/programming-guide/indexers/index.md).  
  
V následujícím příkladu definuje, jak `get` a `set` přistupující objekt pro vlastnost s názvem `Seconds`. Používá soukromé pole s názvem `_seconds` zálohovat hodnotu vlastnosti.  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
Často `get` přistupujícího objektu se skládá z jednoho příkazu, který vrátí hodnotu, stejně jako v předchozím příkladu. Od verze jazyka C# 7, můžete implementovat `get` přistupujícího objektu jako výraz vozidlo člena. Následující příklad implementuje i `get` a `set` přistupujícího objektu jako výraz vozidlo členy.

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
Pro jednoduché případy, kdy vlastnost `get` a `set` přístupové objekty provádět žádné operace, než nastavení nebo načtení hodnotu v poli privátní zálohování, můžete využít výhod podpory kompilátoru C# pro automaticky implementované vlastnosti. Následující příklad implementuje `Hours` jako ve automaticky implementované vlastnosti. 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md) [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
