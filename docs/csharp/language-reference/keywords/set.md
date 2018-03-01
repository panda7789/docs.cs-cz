---
title: "set (Referenční dokumentace jazyka C#)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b810280724dcf608859bfa455947a75ce64b7abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="set-c-reference"></a>set (Referenční dokumentace jazyka C#)
`set` Definuje – klíčové slovo *přistupujícího objektu* metoda ve vlastnosti nebo indexer, který přiřazuje hodnotu pro vlastnost nebo indexer element. Další informace a příklady naleznete v tématu [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), a [indexery](../../../csharp/programming-guide/indexers/index.md).  
  
V následujícím příkladu definuje, jak `get` a `set` přistupující objekt pro vlastnost s názvem `Seconds`. Používá soukromé pole s názvem `_seconds` zálohovat hodnotu vlastnosti.  
 
 [!code-csharp[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

Často `set` přistupujícího objektu se skládá z jednoho příkazu, který vrátí hodnotu, stejně jako v předchozím příkladu. Od verze jazyka C# 7, můžete implementovat `set` přistupujícího objektu jako výraz vozidlo člena. Následující příklad implementuje i `get` a `set` přístupových objektů jako výraz vozidlo členy.

 [!code-csharp[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
Pro jednoduché případy, kdy vlastnost `get` a `set` přístupové objekty provádět žádné operace, než nastavení nebo načtení hodnotu v poli privátní zálohování, můžete využít výhod podpory kompilátoru C# pro automaticky implementované vlastnosti. Následující příklad implementuje `Hours` jako ve automaticky implementované vlastnosti. 
  
 [!code-csharp[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)
